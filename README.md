# Legacy Value Test Data

This repository contains test data for the json-based [ssb legacy data encodings](https://spec.scuttlebutt.nz/feed/datamodel.html).

The directory `syntax` contains data that is not valid [json](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf) at all.

The directory `surrogate` contains data that is syntactically valid but contains strings with [invalid](https://spec.scuttlebutt.nz/datamodel.html#json-transport-encoding) escaped surrogate code points.

The directory `duplicate` contains data that is syntactically valid but contains maps with duplicate keys.

The directory `number` contains numbers that are syntactically valid but round to a [forbidden value](https://spec.scuttlebutt.nz/datamodel.html#floats).

The directory `yay` contains four files for each piece of data:

- `foo` is a valid json transport encoding of a legacy value
- `foo.json_signing` is the signing encoding for this value
- `foo.length` is the length of the signing encoding (number of utf16 code units)
- `foo.sha256` is the sha256 hash fo the signing encoding (hashing only the less significant byte of the utf16 code units)

A conforming ssb implementation must reject the content of all files in the directories `syntax`, `surrogate`, `duplicate` and `number`, and it must produce the corect signing encoding, length and sha256 hash for all files in `yay`.
