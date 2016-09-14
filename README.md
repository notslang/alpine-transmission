# alpine-transmission

The Transmission torrent server in an Alpine Docker container.

## usage

Create local directories for Transmission to mount:

```bash
mkdir -p ~/transmission/{downloads,incomplete,resume,torrents}
```

Run the container:

```bash
docker run -d --name transmission \
-p 9091:9091 \
-p 51413:51413 \
-v ~/transmission/downloads:/downloads \
-v ~/transmission/incomplete:/incomplete \
-v ~/transmission/resume:/resume \
-v ~/transmission/torrents:/torrents \
slang800/alpine-transmission \
--username "admin" \
--password "password"
```

## volumes

volume      | contents
----------- | --------------------------------------------------------------------------------
/blocklists | Configuration directory for blocklists. Use `--blocklist` to enable this.
/downloads  | Main directory for downloaded torrents.
/incomplete | Directory for unfinished downloads. Pass `--no-incomplete-dir` to disable this.
/resume     | Resume files, to keep torrents through a restart.
/torrents   | Place where uploaded torrent files are put.
/watch      | Directory to watch for new torrent files. Pass `--no-watch-dir` to disable this.
