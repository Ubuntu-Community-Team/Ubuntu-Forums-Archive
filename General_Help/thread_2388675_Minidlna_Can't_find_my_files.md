---
title: "Minidlna Can't find my files"
date: 2018-04-06
forum: General Help
---

### Post by Hoopz on 2018-04-06
Can't seem to get minidlna working.  I have read quite a few posts on getting it working but can't figure it out.   If anyone could assist me in getting it working that would be awesome!  I have my minidlna.conf below

```
# This is the configuration file for the MiniDLNA daemon, a DLNA/UPnP-AV media
# server.
#
# Unless otherwise noted, the commented out options show their default value.
#
# On Debian, you can also refer to the minidlna.conf(5) man page for
# documentation about this file.

# Specify the user name or uid to run as.
#user=minidlna


# Path to the directory you want scanned for media files.
#
# This option can be specified more than once if you want multiple directories
# scanned.
#
# If you want to restrict a media_dir to a specific content type, you can
# prepend the directory name with a letter representing the type (A, P or V),
# followed by a comma, as so:
#   * "A" for audio    (eg. media_dir=A,/var/lib/minidlna/music)
#   * "P" for pictures (eg. media_dir=P,/var/lib/minidlna/pictures)
#   * "V" for video    (eg. media_dir=V,/var/lib/minidlna/videos)
media_dir=V,/home/hooadam/DLNA
media_dir=V,/home/hooadam/Videos
media_dir=P,/home/hooadam/Pictures

# Path to the directory that should hold the database and album art cache.
#db_dir=/home/hooadam/DLNA/db

# Path to the directory that should hold the log file.
#log_dir=/var/log

# Type and minimum level of importance of messages to be logged.
#
# The types are "artwork", "database", "general", "http", "inotify",
# "metadata", "scanner", "ssdp" and "tivo".
#
# The levels are "off", "fatal", "error", "warn", "info" or "debug".
# "off" turns of logging entirely, "fatal" is the highest level of importance
# and "debug" the lowest.
#
# The types are comma-separated, followed by an equal sign ("="), followed by a
# level that applies to the preceding types. This can be repeated, separating
# each of these constructs with a comma.
#
# The default is to log all types of messages at the "warn" level.
#log_level=general,artwork,database,inotify,scanner,metadata,http,ssdp,tivo=warn

# Use a different container as the root of the directory tree presented to
# clients. The possible values are:
#   * "." - standard container
#   * "B" - "Browse Directory"
#   * "M" - "Music"
#   * "P" - "Pictures"
#   * "V" - "Video"
# If you specify "B" and the client device is audio-only then "Music/Folders"
# will be used as root.
root_container=.V

# Network interface(s) to bind to (e.g. eth0), comma delimited.
# This option can be specified more than once.
network_interface=wlp3s0


# IPv4 address to listen on (e.g. 192.0.2.1/24).
# If omitted, the mask defaults to 24. The IPs are added to those determined
# from the network_interface option above.
# This option can be specified more than once.
# listening_ip=192.168.0.1/24

# Port number for HTTP traffic (descriptions, SOAP, media transfer).
# This option is mandatory (or it must be specified on the command-line using
# "-p").
port=8200

# URL presented to clients (e.g. http://example.com:80).
#presentation_url=/

# Name that the DLNA server presents to clients.
# Defaults to "hostname: username".
friendly_name=UBUNTU_DLNA

# Serial number the server reports to clients.
# Defaults to 00000000.
serial=681019810597110

# Model name the server reports to clients.
#model_name=Windows Media Connect compatible (MiniDLNA)

# Model number the server reports to clients.
# Defaults to the version number of minidlna.
#model_number=

# Automatic discovery of new files in the media_dir directory.
inotify=yes

# List of file names to look for when searching for album art.
# Names should be delimited with a forward slash ("/").
# This option can be specified more than once.
album_art_names=Cover.jpg/cover.jpg/AlbumArtSmall.jpg/albumartsmall.jpg
album_art_names=AlbumArt.jpg/albumart.jpg/Album.jpg/album.jpg
album_art_names=Folder.jpg/folder.jpg/Thumb.jpg/thumb.jpg

# Strictly adhere to DLNA standards.
# This allows server-side downscaling of very large JPEG images, which may
# decrease JPEG serving performance on (at least) Sony DLNA products.
#strict_dlna=no

# Support for streaming .jpg and .mp3 files to a TiVo supporting HMO.
#enable_tivo=no

# Notify interval, in seconds.
notify_interval=240

# Path to the MiniSSDPd socket, for MiniSSDPd support.
#minissdpdsocket=/run/minissdpd.sock
```

---

### Post by Hoopz on 2018-04-06
Here's my minidlna.log

```
[2018/04/05 23:11:45] minidlna.c:1047: warn: Starting MiniDLNA version 1.2.0.
[2018/04/05 23:11:45] minidlna.c:342: warn: Creating new database at /var/cache/minidlna/files.db
[2018/04/05 23:11:45] minidlna.c:1087: warn: HTTP listening on port 8200
[2018/04/05 23:11:45] playlist.c:125: warn: Parsing playlists...
[2018/04/05 23:11:45] playlist.c:259: warn: Finished parsing playlists.
[2018/04/05 23:12:19] upnphttp.c:1021: warn: /favicon.ico not found, responding ERROR 404
[2018/04/05 23:12:20] upnphttp.c:1021: warn: /favicon.ico not found, responding ERROR 404
[2018/04/05 23:12:20] upnphttp.c:1021: warn: /favicon.ico not found, responding ERROR 404
[2018/04/05 23:12:20] upnphttp.c:1021: warn: /favicon.ico not found, responding ERROR 404
[2018/04/05 23:12:21] upnphttp.c:1021: warn: /favicon.ico not found, responding ERROR 404
[2018/04/05 23:12:21] upnphttp.c:1021: warn: /favicon.ico not found, responding ERROR 404
[2018/04/05 23:12:21] upnphttp.c:1021: warn: /favicon.ico not found, responding ERROR 404
```

---

### Post by SeijiSensei on 2018-04-06
Try forcing it to rescan the directories.

```

sudo service minidlna stop
sudo rm -rf /var/cache/minidlna/*
sudo minidlnad -R -d
sudo service minidlna start

```

This deletes any stale index files in /var/cache/minidlna/ then forces a rescan ("-R") of the directories.  Running with the "-d" switch will display the results of the scan on the terminal.  You'll see the various files flash by on the screen along with large blocks of XML content.  When you no longer see either of those, hold down Ctrl and hit C to terminate the process.  Then start the daemon using "sudo service minidlna start".

Rescanning can take a while if you have large archives.

---

### Post by xwizard2 on 2018-04-06
Also, check as which user is minidlna running by default. It just may not have access to files in your home directory.

---

### Post by Hoopz on 2018-04-06
Thanks!  SeijiSensei that seems to have taken me one step closer because now the web interface shows I have some files now. However I try to find the video files on my phone using VLC it says empty still

MiniDLNA status
Media library
Audio files	0
Video files	4
Image files	14

---

### Post by Hoopz on 2018-04-06
Never mind it's working now  I reran your commands and waited longer on the sudo minidlnad -R -d now it's working.  Thanks!!

---

