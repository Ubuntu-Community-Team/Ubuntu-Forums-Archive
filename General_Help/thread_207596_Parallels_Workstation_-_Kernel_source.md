---
title: "Parallels Workstation - Kernel source"
date: 2006-07-02
forum: General Help
---

### Post by welsh_spud on 2006-07-02
Hi

I am trying to install the [Parallels Worstation]("http://www.parallels.com/") trial on Dapper 6.06. The download is a .deb file (which is good) but once it is installed I have to run parallels-config which asks for the kernel source to be installed.

I have tried searching in synaptic for the kernel source, but I can't find anything that pleases Parallels.

My output for 'uname -r' is 2.6.15-23-386

Can someone help me find the package that this program wants installed? :)

---

### Post by mlind on 2006-07-02
You usually need just kernel-headers package, install linux-kernel-headers-386
if you are running 386 arch kernel.

If you really want the full kernel, install linux-image-386

---

### Post by FredB on 2006-07-03
Yes. In synaptic you have to choose the headers version which matches the kernel one.

In terminal : sudo apt-get install linux-kernel-headers-'uname -r' or something like this.

By the way, do a little sudo apt-get dist-upgrade, as your kernel is not the latest one :

```
$  uname -a
Linux fredo 2.6.15-25-386 #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006 i686 GNU/Linux
```

My 2 cents, of course ;)

Also, I tested Parallels, it is good, but not as VMWare Server ;)

---

### Post by az on 2006-07-03
No.  The package is linux-headers-386

Also, you will need build-essential.  All of those are on the cd.  Just put the cd back into your computer while you are at the ubuntu desktop.  The package manager will start and the packages on the cd will be recognised.


If you are online, nevermind - the packages are online.

---

### Post by mlind on 2006-07-03
[QUOTE=azz]No.  The package is linux-headers-386

Also, you will need build-essential.  All of those are on the cd.  Just put the cd back into your computer while you are at the ubuntu desktop.  The package manager will start and the packages on the cd will be recognised.


If you are online, nevermind - the packages are online.[/QUOTE]

oh my, that's the third time I suggested kernel-headers package instead..
You are right azz, thanks for correcting.

---

### Post by welsh_spud on 2006-07-03
Thanks everyone, I will try installing Parallels again later today with the kernel-headers, that is, once I fix GRUB - I had to install Windows on a small partition to get some work done, and in doing so wrote over GRUB.

If anyone is interested, [Gparted Live CD]("http://gparted.sourceforge.net/livecd.php") is a very good live CD for partioning \\:D/

---

### Post by buddhagui on 2006-07-12
Thank you very much for this post. I have been struggling to find the kernel-headers package. Now I think I got her running! Thanks,

Chris

---

