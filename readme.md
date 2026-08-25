# Steganography

Hide a file in an image using LSB steganography with optional encryption.

## Demo

One of these two images carries a hidden, encrypted text file. Can you tell which one?

| `demo/original.png` | `demo/with_secret.png` |
|:---:|:---:|
| <img src="demo/original.png" alt="Original image" width="400"> | <img src="demo/with_secret.png" alt="Image with a hidden file" width="400"> |

The right one embeds [`demo/secret.txt`](demo/secret.txt), encrypted with a password, in the
least significant bits of the pixels:

```bash
# hide (crypt mode 1 = password)
$ python3 main.py hide demo/original.png demo/secret.txt -o demo/with_secret -c 1 -k "correct-horse-battery-staple"

# extract it back
$ python3 main.py unhide demo/with_secret.png -c 1 -k "correct-horse-battery-staple"
$ cat extracted_secret.txt
Rendez-vous samedi 21h, quai n°7.
Le mot de code est "girafe".
```

## Installation

```bash
$ pip install -r requirements.txt
```

## Help

```bash
$ python3 main.py hide -h
$ python3 main.py unhide -h
```