# Share Note self-hosted PHP backend

- `/api/` is the API backend.
- `/public/` will be the location of uploaded files.

## Installation

### Server

1. Copy `./api/env.cfg.example` to `./api/env.cfg`, and update with your specific 
configuration as follows:

#### `uid` and `private_key`

You will need to generate a random 32 character alphanumeric string for each of
these, and set them in both `env.cfg` on the server, and in the `data.json` file
for Share Note plugin in your Obsidian plugins folder.

A quick way to generate these would be to use an MD5 hash of a string. 
[Here's an online tool](https://emn178.github.io/online-tools/md5.html) to do that.

You will need to set these the server `env.cfg`,

```
uid=8a307375635b44003b1f249ce4381f10
private_key=e28616cde774ed5199764d0b9b27768a
```

#### `upload_folder` 

This is the public HTML directory where your shared notes should be saved, example:

```
upload_folder=/var/www/public
```

#### `file_url_base`

The public URL to reach the above `upload_folder`, example:

```
file_url_base=http://localhost/public
```

#### `assets_webroot`

The public URL to reach the assets folder, usually this will be an `/assets` subfolder
of the above location. Example:

```
assets_webroot=http://localhost/public/assets
```

2. Point your API web root to the `./api/` folder in this repo.

3. Point your shared notes location web root to the `./public/` folder in this repo.

### Plugin

Edit the `data.json` file in your Obsidian Share Note plugin folder.

#### `uid` and `apiKey`

Update `uid` and `apiKey` to match the `uid` and `private_key` values from your server's `env.cfg`.

```json
  "uid": "8a307375635b44003b1f249ce4381f10",
  "apiKey": "e28616cde774ed5199764d0b9b27768a",
```

#### `server`

Set this to be the URL for your server's `./api/` folder:

```json
  "server": "http://localhost/api",
```
