---
title: "mplayer broken?"
date: 2005-04-06
forum: General Help
---

### Post by b7j0c on 2005-04-06
The following packages have unmet dependencies:
  mplayer-nogui: Depends: libfontconfig1 (>= 2.3.0) but 2.2.3-4ubuntu7 is to be installed
                 Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
E: Broken packages


i can't seem to get this to go away, a little afraid of tinkering further.

---

### Post by lorap on 2005-04-06
hi friend!
i propose you to install XMMS and VLC players both together,one to listen to mp3 and another one to watch mp4 files.
VLC renders mp3 files also but XMMS is cute looking one.
pavel

---

### Post by b7j0c on 2005-04-06
thanks! vlan looks good. although if anyone has an explanation as to why mplayer is broken i would also apprecaiate that.

---

### Post by maqi on 2005-04-06
Mplayer isn't "broken" as such.

Mplayer is not an ubuntu package - it is from the marillat repository. It is a CVS version of mplayer also-so likely very recent. It has been built against more recent versions of those libs than we have available in hoary. 

Ubuntu did not break mplayer - it is not part of ubuntu so ubuntu maintainers/developers have nothing to do with it. The maintainer did not break mplayer - it works fine on a system with all the dependencies in place. It's just that the maintainer is not building his package with ubuntu compatibility in mind.

And - come to think of it, the maintainer may well be at the mercy of the developers to some extent also.

Your options? Wait for ubuntu to catch up (and it may not), try and get those libraries from elsewhere (eg, debian unstable - but you risk breaking your system), or get mplayer from the mplayer website and build it yourself.


Cheers,
maqi

---

### Post by emperor on 2005-04-06
or install xine now!

If you haven't done so already, enable DMA on your DVD drive. 
Info concerning how to do this is posted on the forums (search).

---

### Post by NeoChaosX on 2005-04-06
Do a Force Version in synaptic. There are builds of MPlayer in the hoary repositories, it's just that the Marillat builds have a higher version number (and thus are the default to be installed when you select the mplayer package) and depend on libaries that aren't in Hoary, but in Debian. Just select a version that has 'ubuntu' in the version number, and it'll install just fine.

---

### Post by b7j0c on 2005-04-06
thanks everyone - i understand now that mplayer is in a non-supported repo and i will have to wait for it to be fixed. sorry if i had known it had come from the marillat repo i would have not asked.

also thanks for the note about dma with the dvd drive

thanks everyone, you are very helpful

---

