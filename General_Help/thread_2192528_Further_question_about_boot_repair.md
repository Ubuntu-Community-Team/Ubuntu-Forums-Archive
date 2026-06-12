---
title: "Further question about boot repair"
date: 2013-12-08
forum: General Help
---

### Post by zeynel2 on 2013-12-08
After I upgraded from 10.04 to next version I was unable to boot, I get the black screen. I ran the boot repair but it did not solve the problem
. I was told to ask the question here. This is the url from boot repair: [http://paste.ubuntu.com/6541631/](http://paste.ubuntu.com/6541631/). 
Thanks for the help.

---

### Post by oldfred on 2013-12-08
You may have video driver issues.
But I do not know ATI/AMD video as I have nVidia.

Have you tried nomodeset?
       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


 Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)


[LIST]
[*]Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1
[*]nVidia: nomodeset
[*]Generic: xforcevesa or nouveau.modeset=0
[*]Radeon: radeon.modeset=0
[/LIST]

 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

---

### Post by Bucky Ball on 2013-12-08
Well, it looks ok to me, but I'm no expert. Do you get to the screen which gives you a selection of kernels to boot (before the login screen)?

---

### Post by Bucky Ball on 2013-12-08
> **oldfred said:**
> You may have video driver issues.
But I do not know ATI/AMD video as I have nVidia.

Have you tried nomodeset?
       

Exactly. Ninja'd. My very next thought. ;)

---

### Post by zeynel2 on 2013-12-08
Yes, i get that screen with kernels to boot

---

### Post by zeynel2 on 2013-12-08
Where do I set nomodeset? In grub? I am ppsting these from my phone so sorry for asking for details...

---

### Post by zeynel2 on 2013-12-08
Ok, I changed GRUB with nomodeset (I put it before "splash...") but now it stopped loading on ubuntu screen. What am I doing wrong?

---

### Post by oldfred on 2013-12-08
Remove quiet splash and you will see all the booting process. So you may see where it stops, usually error message that is important is not last entry but a few before that. Or it may need an additional boot parameter.

And you can try the other options to nomodeset to see if they work any better.

---

### Post by zeynel2 on 2013-12-08
Ok, I removed quick splash. I see that it stopped at

* Checking battery ... [ok]

Then it went to Ubuntu 12.10 b tty1 screen. What can I do here?

---

### Post by oldfred on 2013-12-08
It seems to almost always stop at checking battery, but it is what errors it may have posted a few lines before that.

---

### Post by zeynel2 on 2013-12-08
Is there a way to go page by page so that i can see the errors?

---

### Post by oldfred on 2013-12-08
I never use less or more which may be better, but do use cat.
But you have to get to a terminal in your install or mount it from live installer so then path would include the additional mount in the path.

cat /var/log/dmesg

From live installer change example with sda2 to your drive & partition.
/mnt already exists, so it should work
  sudo mount /dev/sda2 /mnt
cat /mnt/var/log/dmesg

---

### Post by zeynel2 on 2013-12-08
@oldfred: Thanks for this reply; but I am a little confused since I am just a beginner. What do you want me to do? I can get to a screen that says "tty1" or something like that and I can login into that and it shows the command line, can I work there?

If not can you please clarify what I need to do with the live installer. I assume that's the original dvd and I will boot from it and choose "try ubuntu without installing" and after that...? Thanks.

---

### Post by oldfred on 2013-12-08
If you can get to command line in a working system then copy & paste first command. If not copy & paste each of the second two commands into a terminal.

If you can get to a terminal, can you boot recovery mode or the second entry in grub menu?

---

### Post by zeynel2 on 2013-12-08
I tried this [COLOR=#000000]cat /var/log/dmesg in command line after logging in with DVD but I got "No such file or directory". What am I doing wrong? [/COLOR]

---

### Post by zeynel2 on 2013-12-08
Yes, second entry in grub is "Advanced options for ubuntu" when I go there I see ubuntu, with Linux 3.8.0-33-generic (recovery mode). When I ran this recovery mode, I see a bunch things scroll down and it goes to another screen with recovery menu? What can I do here?

---

### Post by oldfred on 2013-12-08
It gives you a chance to go to terminal with Internet. To try to boot normally and all the other options.
Often if you can get to a terminal you then can do updates to fix whatever issue you may have.

See if you can get to terminal and login.

I normally post these if you have to chroot. In terminal in your install you normally need sudo.

 #if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
apt-get -f install
dpkg --configure -a

---

### Post by zeynel2 on 2013-12-13
@oldfred: Thanks for these instructions but they did not work for me, I still get the black screen after I see the ubuntu screen.

I tried to login with an earlier version in grub (Ubuntu, with Linux 3.8.0-33-generic) but that same thing happened.

Luckily, in this other thread [http://ubuntuforums.org/showthread.php?t=2193227](http://ubuntuforums.org/showthread.php?t=2193227) ian-weissler helped me to backup, so data is backed up now.

What do you advise that I try next?

When I replace quiet splash with nomodeset in grub, this is what happens: after some data scrolls down, I get to the screen 

Ubuntu 13.10 b tty1
b login:

and I am able to login (and this is how I was able to back up to Dropbox)

What should I do next? Should I forget about fixing this and try a new clean install?

---

### Post by zeynel2 on 2013-12-13
@oldfred: Thank you very much. I tried the instructions again and this time worked and I was able to login. I am closing the thread. Thanks again for the help.

---

### Post by oldfred on 2013-12-13
Glad you got it working. :)

---

