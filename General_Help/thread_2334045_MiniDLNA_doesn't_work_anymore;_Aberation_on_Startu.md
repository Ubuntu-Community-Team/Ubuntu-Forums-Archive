---
title: "MiniDLNA doesn't work anymore; Aberation on Startup once; Re-install Necessary?"
date: 2016-08-15
forum: General Help
---

### Post by SciGuy1872 on 2016-08-15
Everything used to be fine, now the DLNA server does not provide anymore.  When starting the computer once, the lights on the keyboard all blinked consecutively and the computer never booted--should I just re-install Xenial?  Here's the miniDLNA conf file:

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
media_dir=A,/home/anthony/Music
media_dir=P,/home/anthony/Pictures
media_dir=V,/home/anthony/Videos


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
root_container=.


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


# Notify interval, in seconds.
#notify_interval=895


# Path to the MiniSSDPd socket, for MiniSSDPd support.
#minissdpdsocket=/run/minissdpd.sock
```

Thanks,
   Anthony

---

### Post by SeijiSensei on 2016-08-16
If the computer doesn't boot, I don't see how that's a minidlna problem.

Can you boot the machine from a CD/DVD or a USB pendrive?

---

### Post by SciGuy1872 on 2016-08-16
Thanks for the reply.  The one time with the aberation at startup was the only time it didn't boot (this happened about three days ago); I didn't try minidlna after successful boot, but now the server doesn't provide.  I'm afraid this machine has been hacked because the minidlna.conf had some text changes, besides the server not working now--if I change my sudo password, would the spies see what I changed my password to, or would it be secure?
  I added a firewall yesterday--that may have prevented the server from reaching my xbox; I'll turn the firewall off when testing for a working state when editing the conf file.  

Thanks again,
           Anthony

---

### Post by SeijiSensei on 2016-08-16
I don't see anything untoward in your minidlna.conf file.  

Being hacked is an very, very rare event.  Why do you think you have been "hacked?"

---

### Post by SciGuy1872 on 2016-08-16
The behavior of the computer when starting up or rebooting (it only happened two times)--the computer essentially freezes and the lights on the keyboard blink; I have to hold the power button until the machine turns off.  I had no problems with Xenial before.  Do you suggest I do anything?

Thanks for your time,
                           Anthony

---

### Post by ajgreeny on 2016-08-16
What were those changes in your minidlna.conf file?

Your version looks good to me as well; have you edited it back to original from those changes that you say were made?

---

### Post by SciGuy1872 on 2016-08-16
The changed minidlna.conf had a couple of lines at the very end that stated that the file was edited by someone "24 minutes ago".  When I discovered that entry that I didn't think should have been there, I erased that part, then saved.  Since I tried to use my tv to stream my music and the xbox reported that there was no server found, I jumped to reviewing the conf file, not the firewall, and that's when I found that part about the edit.  This is the current entry for the file:

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
media_dir=A,/home/anthony/Music
media_dir=P,/home/anthony/Pictures
media_dir=V,/home/anthony/Videos


# Path to the directory that should hold the database and album art cache.
db_dir=/var/cache/minidlna


# Path to the directory that should hold the log file.
log_dir=/var/log


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
root_container=.


# Network interface(s) to bind to (e.g. eth0), comma delimited.
# This option can be specified more than once.
#network_interface=eth0


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
#notify_interval=895


# Path to the MiniSSDPd socket, for MiniSSDPd support.
#minissdpdsocket=/run/minissdpd.sock
```

Thanks for your help,
                   Anthony

---

### Post by SciGuy1872 on 2016-08-17
Got it working!  First I turned off the Firewall, then ran the Purge command and deleted minidlna-original.conf, then rebooted and ran the install minidlna command; then I went to my tv and saw that the server was providing, but I still had to change the directories so they would be found.

Have a good day everyone,
                                Anthony

---

### Post by ajgreeny on 2016-08-17
Brilliant!

So it looks as if it was the firewall, not minidlna itself causing the problem for you.  Perhaps you just needed to open the minidlna port in the firewall.

---

### Post by SciGuy1872 on 2016-08-17
I don't think opening the ports were enough--I tried messing with the rules last night; it's running after the Purge reboot.  Oh well, I'm happy now.  If I changed my sudo password would hackers see a simple thing like that?--the password I have now is not that long.  The two problems when shutting down and booting give me pause--freezing up and the lights on the keyboard blinking.
Maybe I am a little bit foolish for not automatically thinking about the firewall--at least I solved my problem, for that I give myself at least some props. 
Thanks,
         Anthony

---

