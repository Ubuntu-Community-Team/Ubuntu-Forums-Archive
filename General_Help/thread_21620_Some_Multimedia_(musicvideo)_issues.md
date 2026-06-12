---
title: "Some Multimedia (music/video) issues"
date: 2005-03-23
forum: General Help
---

### Post by Steel3 on 2005-03-23
Hey all,

Wasn't really sure where to put this; I apologize if this is not the appropriate forum.

Anyway, I've recently installed the preview version of Hoary (fresh install) and everything seems to be working very well, with the exception of audio/video playback.  Everything (regarding media playback) worked perfectly in Warty, so I'm probably forgetting something stupid.

Upon installing the gstreamer0.8-plugins, rythmbox could play mp3 files but nothing else bundled in the install was able to.  I added the debian-marillat repositories from ftp.nerim.net and installed the w32codecs, got a message that the package was not authenticated.  I also got the following messages when I tried to update the repositories.

W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Re was able to.  lease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907

Anyway, I installed beep-media-player and xmms, and both crashed when I tried to play an mp3 file.  After that, I removed w32codecs.

Afterwards I installed VLC and xine-ui.  Both can play a few different video files, but neither plays back any audio.  VLC gives this error message in the terminal when I try to open a file:

[00000271] mpeg_audio decoder: MPGA channels:2 samplerate:22050 bitrate:48
[00000274] oss audio output error: cannot open audio device (/dev/dsp)
[00000274] main audio output error: couldn't find a filter for the conversion
[00000274] main audio output error: couldn't set an output pipeline

I'm sort of in over my head, so any help would be appreciated.  I hope some of these issues are resolved/simplified when Hoary comes out.  Thanks in advance! :)

---

### Post by Steel3 on 2005-03-23
I've been able to resolve some of this by switching the output plugins for some of the programs to eSound.  Hopefully doing this by default is something that they'll rectify in the official release.

---

### Post by cutOff on 2005-03-23
Regarding GPG error, 
have you seen this [thread](http://www.ubuntuforums.org/showthread.php?t=20839&highlight=gpg)??

---

### Post by Steel3 on 2005-03-23
[QUOTE=cutOff]Regarding GPG error, 
have you seen this [thread](http://www.ubuntuforums.org/showthread.php?t=20839&highlight=gpg)??[/QUOTE]

Thanks, I didn't know that :)

Anyway, my problem was rectified by configuring esd to release the soundcard whenever it wasn't in use (they don't do this by default for some reason because everything in ubuntu main uses esd) as detailed on the [Ubuntu Wiki](https://www.ubuntulinux.org/wiki/RestrictedFormats).  Go figure.

---

