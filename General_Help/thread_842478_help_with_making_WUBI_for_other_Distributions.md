---
title: "help with making WUBI for other Distributions"
date: 2008-06-27
forum: General Help
---

### Post by mohit99 on 2008-06-27
Hi,

First of all I would like to congratulate Agostino Russo and the entire Wubi team for this wonderful software, it really makes Ubuntu Installation very very easy!

I am trying to compile WUBI for BOSSLinux (I use it at home along with Ubuntu 8.04), its a debian based distro a lot like Ubuntu but with built in Indian Languages support (and a few other extras targetting the Indian Linux User). I have read [http://ubuntuforums.org/showthread.php?t=701219](http://ubuntuforums.org/showthread.php?t=701219) , where the thread reached a dead end because the Kernel version in the current release was said to be too old for WUBI to work. I am going to try and remaster the ISO  to a newer kernel and then try WUBI, i have a few doubts:

1.Unlike Ubuntu, BOSS doesn't use a Live-cum-Install cd, the live and the install CDs are different. Would i have to create a Live-cum-Install CD and then make WUBI or will it work on the install CD itself? (BOSS uses Debian installer)

2. What version of the Linux Kernel would WUBI work best with? I plan to download the vanilla kernel from kernel.org, compile it to remaster the ISO.

Any help would be greatly appreciated :)

thanks

---

### Post by ago on 2008-06-27
Hi at the moment, wubi requires quite a few changes upstream. They are all in Ubuntu, so it is fairly easy to use Wubi with any Ubuntu derived distro, but those changes have not yet been ported to Debian. Hence making non Ubuntu distros is far tougher since you either need to merge the required changes upstream, or replace swap all the files on the fly.

See the WubiGuide for more info

---

### Post by Dicinox on 2008-06-27
There's something like wubi for Debian, [http://goodbye-microsoft.com/](http://goodbye-microsoft.com/)

I did not prove it, but for the screenshots it lokks like Wubi... and the function its the same

---

### Post by rawlwear on 2008-06-28
> **Dicinox said:**
> There's something like wubi for Debian, [http://goodbye-microsoft.com/](http://goodbye-microsoft.com/)

I did not prove it, but for the screenshots it lokks like Wubi... and the function its the same

thanks for that i'm downloading now and goin got test it out, if you find anymore please post

---

### Post by mohit99 on 2008-06-28
Thanks a lot for the quick reply *ago*. I'll try and read up on this.
And thanks *Dicinox*, i didnt know about the Debian Installer.

---

### Post by minhmeoke on 2008-06-29
> There's something like wubi for Debian, [http://goodbye-microsoft.com/](http://goodbye-microsoft.com/)

I did not prove it, but for the screenshots it lokks like Wubi... and the function its the same 

The Debian-Installer is somewhat different from Wubi, since it installs to a separate dedicated partition, rather than loopmounted files within Windows like Wubi. If you want something like the Debian-Installer for your distro, I recommend you contact tuxcantfly, the developer of UNetbootin, [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) and ask him to add support for your distro.

---

### Post by ago on 2008-06-30
netinstallation (such as instlux, debian win32-loader and unetbootin) will be easier since they only require an hd-media like initrd but no other change to the distro. Those are standard installations though, requiring dedicated partition, the biggest advantage being that they do not require a physical CD. Installing inside a file (loop-installations) is more involved. As mentioned that is fully supported for any Ubuntu derivative since all the changes are now upstream, but we haven't merged the changes into Debian yet.

---

### Post by mohit99 on 2008-07-03
hi all, thanks for helping out, does win32-loader also have an offline version that works off a CD like wubi does? Where i come from Broadband internet with unlimited bandwidth is still expensive. i am trying to read up as much as i can on this guys, i will post back on any real progress i make :) thanks again for helping out.

---

### Post by ago on 2008-07-04
The best bet is to pre-download the ISO and use the hd-media initrd. That should also work with a CD or be modified to do so. Note though that it will not be possible to resize the partition hosting the ISO.

---

### Post by mohit99 on 2008-07-14
Hi,

Iam looking for documentation on Lupin, how do i build Lupin?

thanks

---

