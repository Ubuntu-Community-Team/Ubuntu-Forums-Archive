---
title: "Did a Firefox 3.0b + Flash workaround ever surface?"
date: 2008-05-08
forum: General Help
---

### Post by Zorael on 2008-05-08
I've been running firefox-2 up until now, staying with it to keep my lovely addons, but now their developers all seem to have released new versions, so I upgraded and I basically like it. But, as with many others, flash doesn't work properly. The browser window itself doesn't crash, it just doesn't (always) display the flash content.


Did a workaround ever surface for this?

---

### Post by randcoop on 2008-05-08
Perhaps you can be more specific about the problem you're having with Flash.  I use Firefox 3.0b5 with Kubuntu Hardy and Flash 9.124 and I haven't experienced any circumstances where it didn't work.  It may be that the site you're trying to view is poorly constructed.

---

### Post by Zorael on 2008-05-08
Naturally.

While I wouldn't like to call it exclusively, it is mostly an issue with Youtube. Opening up any given video, there is a large chance of it not playing, instead ending up with a gray box where the player should be. I attached a screenshot of what it looks like; the terminal open contains the output from firefox-3.0.

I *am* running an x86_64 installation. If you can't relate to the issue at all, perhaps this is solely an 64-bit issue?

```
zorael@sunspire:~$ uname -a
Linux sunspire 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
zorael@sunspire:~$ apt-cache policy flashplugin-nonfree
flashplugin-nonfree:
  Installed: 9.0.124.0ubuntu2
  Candidate: 9.0.124.0ubuntu2
  Version table:
 *** 9.0.124.0ubuntu2 0
        500 http://se.archive.ubuntu.com hardy/multiverse Packages
        100 /var/lib/dpkg/status
```

---

### Post by hunteramor on 2008-05-09
I am experiencing the same issue, and no it's not a 64-bit issue. Problem popped up immediately after upgrading to hardy (and therefore firefox 3.0b)

---

### Post by artir on 2008-05-09
In launchpad a workaround was posted, it works 50% of times, but its something XD. I made a HOWTO HERE: [http://ubuntuforums.org/showthread.php?t=768448](http://ubuntuforums.org/showthread.php?t=768448)

---

### Post by hunteramor on 2008-05-09
problem was solved by installing the package libflashsupport and restarting firefox - that easy!

---

### Post by descentspb on 2008-05-09
In x64, i've made my Firefox and Opera work flawlessly with latest flash and Java just with changing the x64 versions of them to x32 and manually installing flash and java into the corresponding plugin directories of the browsers.

---

### Post by Zorael on 2008-05-11
> **descentspb said:**
> In x64, i've made my Firefox and Opera work flawlessly with latest flash and Java just with changing the x64 versions of them to x32 and manually installing flash and java into the corresponding plugin directories of the browsers.
Could you perhaps go into detail on how to install a 32-bit FF3 onto an x86_64 platform? Is it merely a matter of grabbing the 32-bit .deb and installing, then making appropriate symlinks?

---

### Post by stoffe on 2008-05-11
> **hunteramor said:**
> problem was solved by installing the package libflashsupport and restarting firefox - that easy!

It also results in crashes for a large percentage of users, you could at least mention that... it's the reason libflashsupport was removed, after all: crashes are worse than no sound. It works for some, but it seems not even the majority(?). That includes compiling it yourself (it's the exact same).

Other workarounds include removing pulseaudio completely, using Firefox 2 or using one of the competitors instead, but those have horrible quality.

The real solution is to fix the instability in libflashsupport, but it's very silent on that front. It's the single point of failure.

---

### Post by ubuntu-freak on 2008-05-11
No one in my sticky complained of crashes after installing libflashsupport. Firefox crashed a few times before I installed libflashsupport, though.
 
Nathan 
 
P.S. If anyone still has problems, try this command:
 
**sudo apt-get purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install flashplugin-nonfree libflashsupport**
 
Restart Firefox. Added libflashsupport incase anyone missed it.

---

### Post by Zorael on 2008-05-11
> **reassuringlyoffensive said:**
> P.S. If anyone still has problems, try this command:
 
**sudo apt-get purge flashplugin-nonfree gnash gnash-common swfdec-mozilla && sudo apt-get install flashplugin-nonfree libflashsupport**
 
Restart Firefox. Added libflashsupport incase anyone missed it.
As my previous posts should suggest, I had FF3 working with pulse sound, but with embedded flash often needing a page refresh (or two, or five) to show - up until a point where they all go grey and I need to restart Firefox to get them back.

Anyway, I purged flashplugin-nonfree, libflashsupport, gnash* and swfdec-mozilla, and went through library directories with locate and tried to catch any leftovers. Then I reinstalled only flashplugin-nonfree and libflashsupport. At this point, I still have sketchy flash where content is only played perhaps one time out of four (up until it breaks), but now I also have no sound. :> Obviously I had done something before that escapes me now.

Opening up the pulseaudio manager and checking the Clients tab, there is an entry flashing *furiously*. It's hard to read what it's flashing between, but one of the states seem to say 'ALSA plugin (npviewer.bin)' and the other 'Native client (UNIX socket client)'.

Some random info:
```
zorael@sunspire:~$ uname -a
Linux sunspire 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 _**x86_64**_ GNU/Linux


zorael@sunspire:~$ apt-cache policy firefox flashplugin-nonfree libflashsupport libflash-mozplugin
firefox:
  Installed: (none)
  Candidate: 3.0~b5+nobinonly-0ubuntu3
  Version table:
     3.0~b5+nobinonly-0ubuntu3 0
        500 http://se.archive.ubuntu.com hardy/main Packages
flashplugin-nonfree:
  Installed: 9.0.124.0ubuntu2
  Candidate: 9.0.124.0ubuntu2
  Version table:
 *** 9.0.124.0ubuntu2 0
        500 http://se.archive.ubuntu.com hardy/multiverse Packages
        100 /var/lib/dpkg/status
libflashsupport:
  Installed: 1.9-0ubuntu1
  Candidate: 1.9-0ubuntu1
  Version table:
 *** 1.9-0ubuntu1 0
        500 http://se.archive.ubuntu.com hardy/universe Packages
        100 /var/lib/dpkg/status
libflash-mozplugin:
  Installed: (none)
  Candidate: 0.4.13-9ubuntu1
  Version table:
     0.4.13-9ubuntu1 0
        500 http://se.archive.ubuntu.com hardy/universe Packages

zorael@sunspire:~$ locate libflashsupport
/usr/lib/libflashsupport.la
/usr/lib/libflashsupport.so
/usr/share/doc/libflashsupport
/usr/share/doc/libflashsupport/changelog.Debian.gz
/usr/share/doc/libflashsupport/copyright
/usr/share/lintian/overrides/libflashsupport
/var/cache/apt/archives/libflashsupport_1.9-0ubuntu1_amd64.deb
/var/lib/dpkg/info/libflashsupport.list
/var/lib/dpkg/info/libflashsupport.md5sums
/var/lib/dpkg/info/libflashsupport.postinst
```

What should I do to troubleshoot? Do note that this is on an x86_64 system, so perhaps exta symlinks need to be made?

---

### Post by Zorael on 2008-05-11
Running [FONT="Courier New"]pulseaudio --log-level=3[/FONT] instead of daemonising, and then trying to watch a youtube clip, it outputs this.
```
...

I: client.c: Created 280 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 280 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [npviewer.bin]"
I: module-volume-restore.c: Restoring sink for <pulsecore/protocol-native.c$ALSA plug-in [npviewer.bin]>
I: module-volume-restore.c: Restoring volume for <pulsecore/protocol-native.c$ALSA plug-in [npviewer.bin]>
I: sink-input.c: Created input 278 "ALSA Playback" on alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0 with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: sink-input.c: Freeing output 278 "ALSA Playback"
I: client.c: Freed 280 "ALSA plug-in [npviewer.bin]"
I: protocol-native.c: connection died.
I: client.c: Created 281 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 281 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [npviewer.bin]"
I: module-volume-restore.c: Restoring sink for <pulsecore/protocol-native.c$ALSA plug-in [npviewer.bin]>
I: module-volume-restore.c: Restoring volume for <pulsecore/protocol-native.c$ALSA plug-in [npviewer.bin]>
I: sink-input.c: Created input 279 "ALSA Playback" on alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0 with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: sink-input.c: Freeing output 279 "ALSA Playback"
I: client.c: Freed 281 "ALSA plug-in [npviewer.bin]"
I: protocol-native.c: connection died.
I: client.c: Created 282 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 282 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [npviewer.bin]"
I: module-volume-restore.c: Restoring sink for <pulsecore/protocol-native.c$ALSA plug-in [npviewer.bin]>
I: module-volume-restore.c: Restoring volume for <pulsecore/protocol-native.c$ALSA plug-in [npviewer.bin]>
I: sink-input.c: Created input 280 "ALSA Playback" on alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0 with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: sink-input.c: Freeing output 280 "ALSA Playback"
I: client.c: Freed 282 "ALSA plug-in [npviewer.bin]"
I: protocol-native.c: connection died.
I: client.c: Created 283 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 283 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [npviewer.bin]"
I: module-volume-restore.c: Restoring sink for <pulsecore/protocol-native.c$ALSA plug-in [npviewer.bin]>
I: module-volume-restore.c: Restoring volume for <pulsecore/protocol-native.c$ALSA plug-in [npviewer.bin]>
I: sink-input.c: Created input 281 "ALSA Playback" on alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0 with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: sink-input.c: Freeing output 281 "ALSA Playback"
I: client.c: Freed 283 "ALSA plug-in [npviewer.bin]"
I: protocol-native.c: connection died.

...
```
Ad nauseam. This was with a libflashsupport compiled from git sources as per [http://www.pulseaudio.org/wiki/FlashPlayer9Solution](http://www.pulseaudio.org/wiki/FlashPlayer9Solution).

edit: Making it [FONT="Courier New"]--log-level=4[/FONT] (which is max) makes it this:
```
...

I: client.c: Created 314 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 314 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [npviewer.bin]"
I: module-volume-restore.c: Restoring sink for <pulsecore/protocol-native.c$ALSA plug-in [npviewer.bin]>
I: module-volume-restore.c: Restoring volume for <pulsecore/protocol-native.c$ALSA plug-in [npviewer.bin]>
I: sink-input.c: Created input 313 "ALSA Playback" on alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0 with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
D: memblockq.c: memblockq requested: maxlength=132300, tlength=88200, base=4, prebuf=84672, minreq=3528
D: memblockq.c: memblockq sanitized: maxlength=132300, tlength=88200, base=4, prebuf=84672, minreq=3528
I: sink-input.c: Freeing output 313 "ALSA Playback"
I: client.c: Freed 314 "ALSA plug-in [npviewer.bin]"
I: protocol-native.c: connection died.

...
```

---

### Post by ubuntu-freak on 2008-05-11
I forgot to put mozilla-plugin-gnash in the command (don't ask...), but it's there now.
 
Nathan

---

### Post by Zorael on 2008-05-11
It works **with and only with** the libflashsupport linked to at [http://ph.ubuntuforums.com/showpost.php?p=4350045](http://ph.ubuntuforums.com/showpost.php?p=4350045). The repo one doesn't, the git compiled one doesn't, the other random .deb I found while googling doesn't. Looking around, I had a copy of it in my semi-important-stuff-to be-organized directory, so it must obviously have been the key to my earlier success.

Perhaps successfully building it from a subversion snapshot would've done the trick, but it refused.
```
zorael@sunspire:/media/main/downloads/svnlibflash/src$ make
gcc -fPIC -shared -O2 -Wall -Werror  -lpthread -DLIBDIR=/usr/lib \
        -DALSA_INTERNAL  -DPULSEAUDIO -DLIBPULSEPATH='"/usr/lib/libpulse-simple.so.0"' -DESD -DLIBESDPATH='"/usr/lib/libesd.so.0"' \
        -DOSS -DOPENSSL -lssl  \
        flashsupport.c -o libflashsupport.so
cc1: warnings being treated as errors
flashsupport.c: In function &#8216;FPX_SoundOutput_Open&#8217;:
flashsupport.c:502: warning: cast from pointer to integer of different size
flashsupport.c:514: warning: cast from pointer to integer of different size
flashsupport.c:544: warning: cast from pointer to integer of different size
make: *** [libflashsupport.so] Error 1
```

So, now I'm back at square one. Flash is still sketchy. Once again audible, but still sketchy.

---

### Post by Zorael on 2008-05-12
It's obviously not a pulse issue, which leaves FF3 and nspluginwrapper. Wrapped flash works in other browsers, so it's likely something new in FF3 that the plugin doesn't handle well.


Related: [http://ubuntuforums.org/showthread.php?t=791127](http://ubuntuforums.org/showthread.php?t=791127)

I've found that I don't need a browser restart when it breaks completely (grey box, no right-click popup, as the earlier attached screenie shows); I just need to navigate away from any and all pages currently trying to display flash content. Of course, the next page I go to with flash content may break it again right away, but at least I don't have to restart the program.

I haven't been able to compile nspluginwrapper from source yet (about which I'll likely post a new thread), but I did try downgrading to the build Rashad Tatum posted over at [https://bugs.launchpad.net/nspluginwrapper/+bug/177856](https://bugs.launchpad.net/nspluginwrapper/+bug/177856). ([http://launchpadlibrarian.net/11224902/nspluginwrapper_0.9.91.5-1ubuntu2_amd64.deb](http://launchpadlibrarian.net/11224902/nspluginwrapper_0.9.91.5-1ubuntu2_amd64.deb)). No noticeable improvement.

---

### Post by hunteramor on 2008-05-12
i didn't mention crashes from libflashsupport because i didn't know, although i think i may have noticed them subsequently....

it has also only solved the problem about 50% of the time

---

