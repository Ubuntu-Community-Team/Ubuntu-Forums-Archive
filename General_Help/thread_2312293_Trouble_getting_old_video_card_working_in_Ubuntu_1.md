---
title: "Trouble getting old video card working in Ubuntu 15.10"
date: 2016-02-03
forum: General Help
---

### Post by pappo2 on 2016-02-03
I have an old mobo (ASUS P4P800) I was going to use to make a home server for my docs n pictures.
It has an old NVidia FX5200 graphics card.
I loaded Ubuntu 15.10 on it with no problems, but the desktop is like in slow motion.
I used "top" to  monitor the processes and compiz is using as much as 90% of the CPU at times.

I used apt-get to load the current nvidia driver (nvidia-352).  It installed ok, but when I reset and tried to login, it kept failing back to the login screen.
I then went to nvidia driver website and loaded their recommended driver for a FX5200 GPU.  Tried to run the file (NVIDIA-Linux-x86-173.14.39-pkg1.run) and it failed saying the kernel was wrong.

Any ideas ?

Maybe I should try a light weight desktop environment.  Does anyone have a recommendation ?

ps.  I booted up initially using Puppy Linux, which worked great, but I am a long time Ubuntu user and could not get used to not having apt-get for package upgrades

---

### Post by Vladlenin5000 on 2016-02-03
If the recommended driver is 173 then that's the one you should have installed in the first place via "additional drivers".

What you can do now is remove/purge all nvidia drivers already installed and start over.
At the login screen press CTRL+ALT+F1. This will give you a "text mode", i.e., no GUI. Then
```
sudo apt-get purge nvidia*
```
Reboot.
```
sudo reboot
```

At this point it should be back with the open source *nouveau* driver you had with the standard installation. Now go to System Settings > Software Properties > Additional drivers (tab). Select and apply the recommended one which will be, unsurprisingly, the 173 version.
(The one you installed no longer supports your ancient card)

---

### Post by pappo2 on 2016-02-03
Galiza - Thank you for the quick response.  
The additional drivers tab did not show the 173 version.  Only thing it returned was "Using Processor microcode firmware for the Intel CPUs from intel-microcode (proprietary)
I tried adding the ubuntu-x-swat repository, but when I ran apt-get update, the link to launchpad said it could not be found, however when I use my browser and go to [https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/x-updates), I can see it just fine.

I downloaded the 173 driver from NVidia  ( NVIDIA-Linux-x86-173.14.39-pkg1.run )  however, when I tried to install it, I got errors that I need to remove nouveau.  I purged all nvidia and nouveau packages, and ran sudo update-initramfs -u[COLOR=#111111][FONT=Ubuntu] so the initramfs can be purged of nouveau.  I was following some comments at this location:  [/FONT][/COLOR]http://askubuntu.com/questions/112302/how-do-i-disable-the-nouveau-kernel-driver[COLOR=#111111][FONT=Ubuntu]
It still fails.[/FONT][/COLOR]

---

### Post by Vladlenin5000 on 2016-02-03
Using a PPA would be my next suggestion. I don't know why it's failing to find it though. Have you done
```
sudo apt-add-repository **ppa:ubuntu-x-swat/x-updates**
```
If so, it should work and after apt-get update it should now show the 173 driver in the same additional drivers dialog.

(EDIT) - ****Ignore the previous paragraph****
The X-Swat repo is for Ubuntu releases up to **14.04** only! That's why it's giving that error... Please read the next post.

In almost all usage scenarios we strongly recommend against using the nvidia script and it shouldn't be necessary to remove nouveau as it is usually blacklisted by the installation of proprietary drivers the Ubuntu way so the users aren't required to perform further actions. You **need ***nouveau* as a fall-back driver should something happen to the other proprietary ones.
Always prefer the nvidia drivers already available in the official repos for your Ubuntu release.
Add and use a PPA if - and only if - the required driver version isn't available in the official repos.

---

### Post by Vladlenin5000 on 2016-02-03
Please read [http://ubuntuforums.org/showthread.php?t=2293379](http://ubuntuforums.org/showthread.php?t=2293379)

Bottom line: You're out of luck. It's *nouveau* or nothing.
If it performs poorly in your system then perhaps a lighter DE like the ones in Xubuntu or Lubuntu will give you better results (while still using *nouveau*).

---

