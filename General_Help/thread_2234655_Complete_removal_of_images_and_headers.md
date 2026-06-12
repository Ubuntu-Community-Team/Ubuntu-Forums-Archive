---
title: "Complete removal of images and headers"
date: 2014-07-15
forum: General Help
---

### Post by RedRat on 2014-07-15
I had a problem with grub and found out that I have been carrying around kernel images and headers going way back to whenever I first installed 12.04. I would like to get rid of most of them and only keep perhaps one to two current kernels for both 12.04 and 14.04. Really do not know how to do this. 

Bashing-om suggested using Synaptic, but do not see how to do that. Any ideas where these old kernels are stored? Can I simply find them and delete them?

---

### Post by Bashing-om on 2014-07-15
RedRat; Hi ! We meet again.

Your preference to remove kernels is synaptic ( wise choice ).
The command uname -a in a terminal will tell you which kernel you are running.- make sure that you do not remove this kernel...then:
Go to Synaptic Package Manager  select status on the left-lower  pane and select installed on the left-upper pane and search for linux-image.
 select the ones you want deleted. listed in the right-upperpane.
  and mark for complete removal.
Click the Apply button in the toolbar and then Apply in the summary window that pops up. Close Synaptic Package Manager.
Do not forget to let grub know what is going on: Terminal command:
```

sudo update-grub

```
  In addition to linux-image, also remove old versions of linux-headers and linux-restricted-modules (if you have them).

Boot into the alternate install and repeat the procedure. Nothing to it once ya done it a time or three.
see also:
[https://sites.google.com/site/easylinuxtipsproject/clean](https://sites.google.com/site/easylinuxtipsproject/clean) <-How to clean up Ubuntu

EDIT: My after thought for 14.04 ;
In release 14.04 the terminal command:
```

sudo apt-get autoremove

``` now also removes obsolete kernels !

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by tgalati4 on 2014-07-15
There is a kernel removal script floating around the forums.  You would have to search for it.  Synaptic is safer, but a little tedious.  Make a printout of /boot.  You can use tree piped to lp.  Use lpstat to get the name of your printer.

Open a terminal:

```
lpstat -a
cd /boot
tree | lp -d nameofyourprinterthatyougotfromlpstat
```

Keep the list handy and cross off the kernels that you delete from synaptic.  Don't delete too many.  Don't delete your current kernel.

The old GRUB (GRUB 1.0) had a configuration to keep X number of kernels.  I have no idea where that is stored in GRUB2.

---

### Post by timgood on 2014-07-17
Easiest way is to install Ubuntu Tweak from [http://ubuntu-tweak.com/downloads/](http://ubuntu-tweak.com/downloads/) which will give you an easy way to remove old kernels and maintain and clean your system. Hope this helps.

---

### Post by JKyleOKC on 2014-07-17
+1

It's by far the easiest way to keep a system clean.

---

### Post by sp40140 on 2014-07-17
-1 for Ubuntu Tweak to remove old kernels. 
Ubuntu Tweak is very good tool. But not reliable for removing old kernels. I have tried it. And would not recommend. However, you should install it because of other features it provides.

Cheers,

---

### Post by sammiev on 2014-07-17
> **Bashing-om said:**
> RedRat; Hi ! We meet again.

Your preference to remove kernels is synaptic ( wise choice ).
The command uname -a in a terminal will tell you which kernel you are running.- make sure that you do not remove this kernel...then:
Go to Synaptic Package Manager  select status on the left-lower  pane and select installed on the left-upper pane and search for linux-image.
 select the ones you want deleted. listed in the right-upperpane.
  and mark for complete removal.
Click the Apply button in the toolbar and then Apply in the summary window that pops up. Close Synaptic Package Manager.
Do not forget to let grub know what is going on: Terminal command:
```

sudo update-grub

```
  In addition to linux-image, also remove old versions of linux-headers and linux-restricted-modules (if you have them).

Boot into the alternate install and repeat the procedure. Nothing to it once ya done it a time or three.
see also:
[https://sites.google.com/site/easylinuxtipsproject/clean](https://sites.google.com/site/easylinuxtipsproject/clean) <-How to clean up Ubuntu

EDIT: My after thought for 14.04 ;
In release 14.04 the terminal command:
```

sudo apt-get autoremove

``` now also removes obsolete kernels !

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

+1 and a very good post.

---

### Post by bapoumba on 2014-07-17
> **tgalati4 said:**
> There is a kernel removal script floating around the forums.
[http://ubuntuforums.org/showthread.php?t=1658648](http://ubuntuforums.org/showthread.php?t=1658648)

---

### Post by timgood on 2014-07-18
> **sp40140 said:**
> -1 for Ubuntu Tweak to remove old kernels. 
Ubuntu Tweak is very good tool. But not reliable for removing old kernels. I have tried it. And would not recommend. However, you should install it because of other features it provides.

Cheers,

What problems have you had? I have never experienced any problems removing old kernels, and I have been using Ubuntu Tweak for years.

---

### Post by sp40140 on 2014-07-18
@timgood
tweak crashing everytime I try to remove old kernels. sometimes it breaks packages which screws with updates.
I am glade it works for you. It used to work for me as well but not since last two versions.
Also, I am not the only one. I found lots of ppl who ran into this (found them on google).
But let's not hijack this thread.
As long as RedHat finds the answer...

---

### Post by jaapz2 on 2014-07-26
Every now and then i run a cleanup in terminal. Below are the commands I use to do that.
Leave the most recent + the one before, that is a good practice from what I read on this subject.

uname -r *#determine which kernel is currently in use, to make sure you are running the latest and not removing an active one.*
dpkg --list | grep linux-image *#list all existing kernels on the system*
sudo apt-get purge linux-image-x.y.zz-aa-generic *#type the name of the kernel you want to remove, see the list you generated with the previous command for that*

sometimes the directory in which some of the kernel data resides is not automatically removed.
ls /lib/modules *#to find which kernels still have a folder there*
sudo rm -r /lib/modules/x.x.zz-aa-generic *# type the exact name of the folder to be removed. Don't delete the folders for the two kernels you have to keep!*
sudo autoremove
sudo autoclean
sudo update-grub *# this should run anyway as the last step of the purge-part, but it doesn hurt to do it anyway*

---

