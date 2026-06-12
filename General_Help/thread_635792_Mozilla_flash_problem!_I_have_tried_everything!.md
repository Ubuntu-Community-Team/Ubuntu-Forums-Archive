---
title: "Mozilla flash problem! I have tried everything!"
date: 2007-12-09
forum: General Help
---

### Post by tenchu77491 on 2007-12-09
**Ubuntu 7.10** AMD64

Ok, when trying to install the flash plug in I always get this error in the terminal,

md5sum mismatch install_flash_player-9_linux.tar.gz
The flash plugin is NOT installed.

I searched the net and I found a topic similar, and I tried everything in it, 
[https://answers.launchpad.net/ubuntu/+question/10061](https://answers.launchpad.net/ubuntu/+question/10061)

I have tried installing it from Automatix, from Mozilla itself, Synoptic,  and manually installing it.... I think I could manually install it but the site was listing what to do and it said to copy the flashplayer.xpt from the tar and there was no flashplayer.xpt in it.... I looked everywhere for it...

How the heck can I get my flash back!? I had it on my previous install, but not after this clean install of Ubuntu 7.10.

As far as my repositories go... I have everything checked and as many sources as I can get... I doubt that is the problem since I can download it. <-- I do not have the cdrom checked for a source.

---

### Post by tenchu77491 on 2007-12-09
OMG I am going to shoot myself.

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=634756](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=634756)

I downloaded the 32bit .deb from that link, and I force installed it on my 64bit system and it worked...

God I fought this for a day.  SOLVED

Anyone with this problem see the above link.

Man this is just my luck, sign up, post a big problem that frustrated me for a day and then solve it myself in 10 minutes.

---

### Post by daradib on 2007-12-09
See [http://ubuntuforums.org/showthread.php?p=3923465](http://ubuntuforums.org/showthread.php?p=3923465)

You can install a 64-bit package (force installation of a 32-bit package on 64-bit Ubuntu not necessary).

---

### Post by stevecaldwell on 2007-12-13
I had the same problem with my son's computer that I recently upgraded from Ubuntu 7.04 to Ubuntu 7.10 (32 bit x386 versions) in early December 2007.

This problem wasn't present when I updated my laptop from 7.04 to 7.10 in early November 2007.

Both Automatix and the Synaptic package manager didn't work.  I installed the flash player manually on my son's computer after downloading it from Adobe's web site.

I'm sure there was a smarter way to fix this but my kludgy work-around was to manually install Adobe's plugin for all three user accounts on my son's computer and then turn off the administrative rights for the two non-administrator accounts after installing the plugin.

After doing this, both YouTube and Google Video work as advertised on my son's computer.

I think this is a package manager problem and not an Automatix problem.

---

### Post by daradib on 2007-12-13
If you see the [thread]("http://ubuntuforums.org/showthread.php?t=636397"), I explain the problem in depth and the fix which has been uploaded to the proposed repository.

---

