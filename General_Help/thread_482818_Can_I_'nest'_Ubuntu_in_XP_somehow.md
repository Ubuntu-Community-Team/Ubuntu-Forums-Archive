---
title: "Can I 'nest' Ubuntu in XP somehow?"
date: 2007-06-24
forum: General Help
---

### Post by darkone465 on 2007-06-24
New forum member here...looking for creative solutions.

I use a Fiesty Live CD at my girlfriend's house, because I love Ubuntu and don't want to be bothered with XPs crappy limitations.  My girlfriend is a lovely gal, but she's a control freak when it comes to her possessions, so adding a second hard drive for dual boot or repartitioning / reinstalling on her existing XP system isn't an option (yet).

Though, I'm not a n00b, I'm certainly not a guru either when it comes to linux.  I guess I'm somewhere in the middle.  What I'd love to do (maybe you know a better solution) is:

Create a swapfile on the XP partition to give this Live CD some badly needed breathing room.  She's got a Gb of ram, but we all know what that's worth after it's loaded with a ramdisk and a couple running apps.  Would love some advice or links to be able to do this correctly.  Found [this walkthrough online]("http://www.netadmintools.com/art1.html"), but using dd anywhere on an NTFS partition makes me nervous.  Should I be?  I'm assuming dd wants a more linux-friendly filesystem to work with, but maybe it's not a big issue.

Another thought I had was creating a file-based volume (like truecrypt, though it doesn't need to be encrypted), then somehow shift the entire running system onto it...or better yet, be a sneaky ******* and install ubuntu on it behind my girlfriend's back and then chrooting to it each time after initially booting from the Live CD.  Is there a way to create a file-based volume without using trypecrypt?  I've heard installing it can be tricky in Ubuntu and keep in mind I'm working entirely within a Live CD environment with no swap (yet).  Can this even be done?

Another option is possibly utilizing a usb drive somehow.

So basically, I'd like to use Ubuntu on her computer without messing with her XP install or multi-booting, but the Live CD limits me in terms of memory usage, no swap, can't install additional apps, etc. (though, I do install frozen bubble into the ramdisk anyway...heh heh)

Thanks for reading this!  :popcorn:

---

### Post by Rui Pais on 2007-06-24
Hi, you can try [Wubi]("http://wubi-installer.org/").

[FAQ here]("http://wubi-installer.org/faq.php").

Check it's forum section  [here]("http://ubuntuforums.org/forumdisplay.php?f=234").

---

### Post by doctapeppa on 2007-06-24
Ubuntu runs terribly slow from the Live Cd, plus your changes are not permanent. Have you tried using another distro such as Knoppix or Puppy linux? I run Puppy linux from a USB stick on my work computer and I love it. It's fast, and all of my changes get written right to my memory stick.

---

### Post by bikeboy on 2007-06-24
Perhaps virtualisation would be the answer. Virtualbox seems popular these days. You install the program on XP and create a 'virtual machine' of Ubuntu. Then you can load the Ubuntu VM from within XP whenever you want, it's like a program rather than a dual boot.
[http://en.wikipedia.org/wiki/Virtualbox](http://en.wikipedia.org/wiki/Virtualbox)
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by darkone465 on 2007-06-24
Thanks for the advice.  I will experiment with each option and see which one works best for me.

---

