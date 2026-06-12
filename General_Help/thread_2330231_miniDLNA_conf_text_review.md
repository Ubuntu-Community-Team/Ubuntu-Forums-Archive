---
title: "miniDLNA conf text review"
date: 2016-07-09
forum: General Help
---

### Post by SciGuy1872 on 2016-07-09
I have used miniDLNA before--I was wondering if someone could review this text for a second and see if they can spot my mistake?  I have commented out the eth0 and I haven't had to use the line before. 

```
# This is the configuration file for the MiniDLNA daemon, a DLNA/UPnP-AV media# server.
#
# Unless otherwise noted, the commented out options show their default value.
#
# On Debian, you can also refer to the minidlna.conf(5) man page for
# documentation about this file.


# Specify the user name or uid to run as.
user=anthony




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
#   * "PV" for pictures and video (eg. media_dir=PV,/var/lib/minidlna/digital_camera)
media_dir=A,/home/anthony/Music
media_dir=P,/home/anthony/Pictures
media_dir=V,/home/anthony/Videos


# Set this to merge all media_dir base contents into the root container
# (The default is no.)
#merge_media_dirs=no


# Path to the directory that should hold the database and album art cache.
#db_dir=/var/cache/minidlna


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
#   * Or, you can specify the ObjectID of your desired root container
#     (eg. 1$F for Music/Playlists)
# If you specify "B" and the client device is audio-only then "Music/Folders"
# will be used as root.
root_container=/home/anthony


# Network interface(s) to bind to (e.g. eth0), comma delimited.
# This option can be specified more than once.
#network_interface=eth0


# Port number for HTTP traffic (descriptions, SOAP, media transfer).
# This option is mandatory (or it must be specified on the command-line using
# "-p").
port=8200


# URL presented to clients (e.g. http://example.com:80).
#presentation_url=/


# Name that the DLNA server presents to clients.
# Defaults to "hostname: username".
friendly_name=Anthony's miniDLNA


# Serial number the server reports to clients.
# Defaults to 00000000.
serial=681019810597110


# Model name the server reports to clients.
#model_name=Windows Media Connect compatible (MiniDLNA)


# Model number the server reports to clients.
# Defaults to the version number of minidlna.
#model_number=


# Automatic discovery of new files in the media_dir directory.
#inotify=yes


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
```

Thanks for your help.

---

### Post by ajgreeny on 2016-07-09
Why do you think it is a mistake?  Is your minidlna not serving media to any clients or causing you problems of some kind?

This is what is in mine which works fine without me having made any changes, ie, that is what the file contained before I edited it to add my media folders.
```
# Network interface(s) to bind to (e.g. eth0), comma delimited.
# This option can be specified more than once.
#network_interface=
```
I have eth0 only on my system, no wifi at all, but I do not know what is needed if you have both, though it would seem to suggest that both can be added.

Perhaps if you have only one connection it is found automatically with no further action on your part; if you have both eth0 and wlan0 it may be necessary to specify which should be used.

---

### Post by SciGuy1872 on 2016-07-09
The minidlna is not found by my xbox one--how can I get the original file?; I will make backup files from now on.  I tried to remove and install through the terminal, but the file remained with my edits.  I only have eth0.

Thanks for the reply.

---

### Post by Nutria on 2016-07-09
> **SciGuy1872 said:**
> The minidlna is not found by my xbox one--how can I get the original file?; I will make backup files from now on.  I tried to remove and install through the terminal, but the file remained with my edits.  I only have eth0.

Thanks for the reply.

Have you looked in /var/log/minidlna.log?  (I prefer explicitly setting the db and log locations.)
```
db_dir=/var/cache/minidlna
log_dir=/var/log
```

Here's what my whole config file looks like:
```
$ grep -v "#" /etc/minidlna.conf | grep -v '^$'
media_dir=/Data/share/video
media_dir=/Data/share/music
db_dir=/var/cache/minidlna
log_dir=/var/log
network_interface=**[COLOR="#FF0000"]enp5s0 <<< Because of changes to Linux kernel[/COLOR]**
port=8200
friendly_name=Johnson Media Player
serial=681019810597110
model_number=
inotify=yes
album_art_names=Cover.jpg/cover.jpg/AlbumArtSmall.jpg/albumartsmall.jpg
album_art_names=AlbumArt.jpg/albumart.jpg/Album.jpg/album.jpg
album_art_names=Folder.jpg/folder.jpg/Thumb.jpg/thumb.jpg
strict_dlna=no
```


Also, is minidlna actually running?  lsof should show something like this?
```
# lsof | grep minidlna | grep -v REG
minidlnad 16851               minidlna  cwd       DIR                8,2     4096          2 /
minidlnad 16851               minidlna  rtd       DIR                8,2     4096          2 /
minidlnad 16851               minidlna    0u      CHR                1,3      0t0          6 /dev/null
minidlnad 16851               minidlna    1u      CHR                1,3      0t0          6 /dev/null
minidlnad 16851               minidlna    2u      CHR                1,3      0t0          6 /dev/null
minidlnad 16851               minidlna    3r      CHR                1,9      0t0         11 /dev/urandom
minidlnad 16851               minidlna    6u  netlink                         0t0      88362 ROUTE
minidlnad 16851               minidlna    7u     IPv4              88363      0t0        UDP 239.255.255.250:1900 
minidlnad 16851               minidlna    8r  a_inode               0,11        0       7041 inotify
minidlnad 16851               minidlna    9u     IPv4              88364      0t0        TCP *:8200 (LISTEN)
minidlnad 16851               minidlna   10u     IPv4             610068      0t0        UDP haggis.homelan:51494 
minidlnad 16851 16872         minidlna  cwd       DIR                8,2     4096          2 /
minidlnad 16851 16872         minidlna  rtd       DIR                8,2     4096          2 /
minidlnad 16851 16872         minidlna    0u      CHR                1,3      0t0          6 /dev/null
minidlnad 16851 16872         minidlna    1u      CHR                1,3      0t0          6 /dev/null
minidlnad 16851 16872         minidlna    2u      CHR                1,3      0t0          6 /dev/null
minidlnad 16851 16872         minidlna    3r      CHR                1,9      0t0         11 /dev/urandom
minidlnad 16851 16872         minidlna    6u  netlink                         0t0      88362 ROUTE
minidlnad 16851 16872         minidlna    7u     IPv4              88363      0t0        UDP 239.255.255.250:1900 
minidlnad 16851 16872         minidlna    8r  a_inode               0,11        0       7041 inotify
minidlnad 16851 16872         minidlna    9u     IPv4              88364      0t0        TCP *:8200 (LISTEN)
minidlnad 16851 16872         minidlna   10u     IPv4             610068      0t0        UDP haggis.homelan:51494 

```

---

### Post by deadflowr on 2016-07-09
If the naming scheme for the interface is that new fangled way then that's systemd.
To find the status of a service with systemd, use:
```
systemctl status service-name-here
```
in this case you can try:
```
systemctl status minidlna
```

It defaults to give a lot of info, but the important stuff is in the beginning, and you can simply hit q to exit.

---

### Post by ajgreeny on 2016-07-09
I have no idea how you can get the original file if you did not make a backup, but the unedited default that comes with the minidlna package is shown below.  You will, of course need to add back in your own media folders as you did before.  Did your minidlna server work before you made the edit you talk of, and why can you not edit the change back to the original?  Don't forget that you will have to edit the file as root with ```
sudo -H gedit /etc/minidlna.conf
``` in order to maske any edits stick.

I have no knowledge of x-box systems so can not say if that is a possible problem, but I see no reason why it should be.
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
media_dir=/var/lib/minidlna

# Path to the directory that should hold the database and album art cache.
#db_dir=/var/cache/minidlna

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
#root_container=.

# Network interface(s) to bind to (e.g. eth0), comma delimited.
# This option can be specified more than once.
#network_interface=

# IPv4 address to listen on (e.g. 192.0.2.1/24).
# If omitted, the mask defaults to 24. The IPs are added to those determined
# from the network_interface option above.
# This option can be specified more than once.
#listening_ip=

# Port number for HTTP traffic (descriptions, SOAP, media transfer).
# This option is mandatory (or it must be specified on the command-line using
# "-p").
port=8200

# URL presented to clients (e.g. http://example.com:80).
#presentation_url=/

# Name that the DLNA server presents to clients.
# Defaults to "hostname: username".
#friendly_name=

# Serial number the server reports to clients.
# Defaults to 00000000.
serial=681019810597110

# Model name the server reports to clients.
#model_name=Windows Media Connect compatible (MiniDLNA)

# Model number the server reports to clients.
# Defaults to the version number of minidlna.
#model_number=

# Automatic discovery of new files in the media_dir directory.
#inotify=yes

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
#notify_interval=895

# Path to the MiniSSDPd socket, for MiniSSDPd support.
#minissdpdsocket=/run/minissdpd.sock

```

---

### Post by SciGuy1872 on 2016-07-09
Thanks everyone--lesson learned: make backup files!  
Very grateful--Anthony

---

### Post by Nutria on 2016-07-09
> **SciGuy1872 said:**
> Thanks everyone--lesson learned: make backup files!  
Very grateful--Anthony

So... is minidlna actually running?  What does the log file say?

---

### Post by SciGuy1872 on 2016-07-09
There are no problems now--I am listening to music right now through my xbox and the tv; Thank you!

---

### Post by Nutria on 2016-07-09
> **SciGuy1872 said:**
> There are no problems now--I am listening to music right now through my xbox and the tv; Thank you!

What were the problem and solution?

---

### Post by SciGuy1872 on 2016-07-09
I guess there was some problem with the text in .conf, not sure what it was--it made sense to me; that's why I posted it.  The solution was to copy the text ajgreeny provided (making a backup).  :P, then edit the source directories.
Thanks for the help,
                       Anthony

---

