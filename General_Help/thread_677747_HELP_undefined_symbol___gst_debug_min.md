---
title: "HELP: undefined symbol: __gst_debug_min"
date: 2008-01-25
forum: General Help
---

### Post by jwhitmore on 2008-01-25
I'm sure this can't be that difficult but I can't seem to get my sound issues resolved. I'm using " Ubuntu 7.10 - the Gutsy Gibbon" and have been for a while and have been ignoring the issues I have with music until this morning.

I can play MP3's using Audacity but Rhythmbox won't even import any files. When I try and import a file into Rhythmbox I get the error:

[I]/usr/lib/rhythmbox/rhythmbox-metadata: symbol lookup error: /usr/lib/rhythmbox/rhythmbox-metadata: undefined symbol: __gst_debug_min
process 11622: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 3247.
This is normally a bug in some application using the D-Bus library.
Segmentation fault (core dumped)[/I]


I've checked through the codecs mentioned in:

[https://help.ubuntu.com/community/RestrictedFormats/MP3#head-70c871ec4e080cee979d182af025821416454c5b](https://help.ubuntu.com/community/RestrictedFormats/MP3#head-70c871ec4e080cee979d182af025821416454c5b)

and I have all the codecs installed. I found a forums page ([http://ubuntuforums.org/showthread.php?t=188956](http://ubuntuforums.org/showthread.php?t=188956)) that stated 

"You have to change the output plugin in gstreamer-properties to OSS. It seems to be a problem of alsa or the alsa plugin of gstreamer."

But when I try to run gstreamer-properties I get the same error:

[I]gstreamer-properties: symbol lookup error: gstreamer-properties: undefined symbol: __gst_debug_min
[/I]

I hope that I've not missed something obvious! I tried a lot of searches but I may very well be searching for the wrong thing.

I hope that somebody can help.

---

