---
title: "Can't install vlc on ubuntu 12.04"
date: 2015-03-28
forum: General Help
---

### Post by Ralph L on 2015-03-28
I got a new Canon sx280hs camera and recorded some 1080p 60 frame/sec video.  When I play it on Totem, it plays but with very jerky motion and the cpu is maxed out.  I thought I would try installing vlc, but I got the following error message:
```
ralph@Lat1:~$ sudo apt-get install vlc
[sudo] password for ralph: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: vlc-nox (= 2.1.2-2.1~precise3) but it is not going to be installed
       Recommends: vlc-plugin-notify (= 2.1.2-2.1~precise3) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 2.1.2-2.1~precise3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```
vlc-nox is listed in Synaptic as 2.1.2-2.1~precise3, just what is being ask for, but won't be installed.  Same for vlc-plugin-notify and vlc-plugin-pulse.

I don't know what packages are broken, nor what to do to fix it.  Anybody have any ideas??

Also, in case vlc is also slow like Totem, does anybody know of other players that might be faster, and allow me to play 1080p smoothly on my old Intel® Pentium(R) M  2.13GHz processor.

---

### Post by gifford on 2015-03-28
Do you have synaptic package manager installed? If not, install and then go to to sections, custom filters. There you will see broken, highlight that and it will list the broken packages. Click on the edit menu
and you will see the option to "Fix Broken Packages". Click on the option and you should be good to go.

---

### Post by Ralph L on 2015-03-28
Synaptic shows no broken packages.  See attachment.

---

### Post by mc4man on 2015-03-28
You have previously added a ppa that has been deleted, - djcj test
So your best bet is to open Software sources & remove that ppa if still listed.  Then run this to ck. for & remove any vlc packages from that ppa that may be installed.

```
 sudo apt-get purge vlc-data
``` 
After that  update your sources & install the 12.04 ubuntu version. 

IF curious about that ppa & whether any packages are installed from it then prior to the above  open synaptic > Origin, click on any entry on left that shows djcj

If you really wanted to install that dead ppa's  vlc then the last packages built could still be available to download & manually install. You'd need to get all the required packages, put in a folder, cd to the folder in a terminal & install with dpkg (sudo dpkg -i  *.deb) probably about 7 packages needed at a min..
[https://launchpad.net/~djcj/+archive/ubuntu/test-deletedppa/+build/5564501](https://launchpad.net/~djcj/+archive/ubuntu/test-deletedppa/+build/5564501)
[https://launchpad.net/~djcj/+archive/ubuntu/test-deletedppa/+build/5564500](https://launchpad.net/~djcj/+archive/ubuntu/test-deletedppa/+build/5564500)

---

### Post by Ralph L on 2015-03-29
Thank you for the response and for pointing out how Synaptic can be used.  I didn't know about that use.  Anyway, it appears that the vlc stuff came from ppa:garhuy/precise.  I installed that when I was installing wine to get cdemu, so that I could fake having a Windows game cd (Bicycle Bridge) in the cd drive, but have it on the hard drive.  How do I keep the cdemu stuff and get rid of the vlc stuff?

---

### Post by mc4man on 2015-03-29
> **Ralph L said:**
> Thank you for the response and for pointing out how Synaptic can be used.  I didn't know about that use.  Anyway, it appears that the vlc stuff came from ppa:garhuy/precise.  I installed that when I was installing wine to get cdemu, so that I could fake having a Windows game cd (Bicycle Bridge) in the cd drive, but have it on the hard drive.  How do I keep the cdemu stuff and get rid of the vlc stuff?
I see that ppa copied over the djcj packages & it is still an active ppa. So you should be able to install that version of vlc assuming the ppa is still enabled in your sources.
To try that go - 
sudo apt-get purge vlc-data
sudo apt-get update
sudo apt-get install vlc

Otherwise just disable the ppa in Software Sources, then run the 3 above commands. That will install the 12.04 Ubuntu vlc version. 
At this point you really don't need that ppa enabled as no updates to anything in it  are likely to happen.

---

### Post by Ralph L on 2015-04-01
I followed your instructions for the disabling of ppa:garhuy/precise, and installing vlc.  Thank you.  It runs very well.  However, it did not run any faster the Totem.  So unless I can find a faster video player, I will not be able to use the full 1080p 60 frame per second feature of my camera.  My cpu just isn't fast enough.

Thank you again for all your help.

---

### Post by nerdtron on 2015-04-01
Don't lose hope, If you have a good graphics card, it can help on your playback with VLC. Have you tried enabling hardware acceleration on the video settings of VLC?

And another player you might want to try is SMplayer, it's a little clunky but uses less CPU resources when it plays video during my testing.

---

### Post by Ralph L on 2015-04-02
Nerdtron
I don't really know how to set hardware acceleration on vlc.  I did try Tool>Preferences>Input&Codecs>Use GPU accelerated decoding.  It didn't help, but was this the setting you had in mind?  I haven't had a chance to try SMplayer yet, but I will.

Thanks,

---

### Post by Ralph L on 2015-04-04
Nerdtron,

Thanks for pointing me to SMplayer.  I installed it and it is indeed faster than either VLC or Totem.  It ran the 1920x1080p 60 frames per second fairly smoothly.  Neither VLC nor Totem could do that.  In fact VLC is the slowest, Totem next, and SMplayer the fastest.  However, it is still not quite fast enough.  When I look at the SMplayer log I see error messages that say ```
Too many video packets in the buffer: (461 in 33618040 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
```
Do you know of ways to speed up SMplayer?  I tried Option>Preferences>Performance>Hardware decoding: Auto, but it didn't seem to make much difference.  I also tried Options>Preferences>Performance>H.264 Loop Filtering: Skip only on HD videos and also no noticeable difference.  Any thoughts???

Thanks again.

---

