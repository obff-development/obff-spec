## Open Book File Format
v1.0

## Extension
obff uses `.obff` or `.obf` as file extension.

## File Header
| Format | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|-------:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| UTF-8 | O | B | F | F | 1 | 0 | . | . |
| Bytes | 4F | 42 | 46 | 46 | 32 | 30 | 00 | 00 |

## File Structure
`[FILE_HEADER][S_TITLE][S_DESC][S_COVER][S_PAGES][TITLE][DESC][COVER][PAGES]`

| BLOCK | Size | Description |
|------:|:-----|-------------|
|`FILE_HEADER`| 8 Bytes | File Header (also known as *magic bytes*) |
|`S_TITLE`| 4 Bytes | Size of title |
|`S_DESC`| 4 Bytes | Size of description |
|`S_COVER`| 4 Bytes | Size of cover |
|`S_PAGES`| 4 Bytes | Size of [Pages](#pages) |
|`S_COVER`| 4 Bytes | Size of cover |
|`TITLE`| nth Bytes | UTF-8 string as bytes |
|`DESC`| nth Bytes | UTF-8 string as bytes |
|`COVER`| nth Bytes | Image as raw bytes |
|`PAGES`| nth Bytes | twice gzip compressed [Pages](#pages) |


### Pages
Structure of the page block\
`[COUNT]<LIST:PAGE>`

| BLOCK | Size | Description |
|------:|:-----|-------------|
| `COUNT` | 4 Bytes | Count of pages |
| `LIST:PAGE` | nth Bytes | List of [Page](#page) |

#### Page
`[SIZE][IMAGE]`

| BLOCK | Size | Description |
|------:|:-----|-------------|
| `SIZE` | 4 Bytes | Size of image |
| `IMAGE` | nth Bytes | Image as raw bytes |
