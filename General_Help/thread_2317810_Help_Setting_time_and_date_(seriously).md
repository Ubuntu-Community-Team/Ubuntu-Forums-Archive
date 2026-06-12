---
title: "Help: Setting time and date (seriously)"
date: 2016-03-20
forum: General Help
---

### Post by Hammi on 2016-03-20
Ok, I feel embarrassed. I have setup a number of Ubuntu machines since Ubuntu 7.04, and never came across this problem.

I am trying to set time and date on an Ubuntu machine. I noticed there is an issue after having setup an ntp server and asking my machines around to use it. It works well with all except one machine. That machine is 15s off. So after I struggeled with ntp, I fell back to the basics, I tried:

```
root@machine:/# date -s "2016-03-20 08:05:45"
Su 20 Mar 08:05:45 CET 2016
root@machine:/# date
Su 20 Mar 08:06:10 CET 2016
```

I appreciate the difference is not significant, and I may have needed second or two to type the second "date" command. But the point is: It does not work. I cannot change the time in the current system.

What could that be?

Thanks!

---

### Post by mörgæs on 2016-03-20
Using the root account is generally discouraged:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Hammi on 2016-03-20
I became "root" using ```
sudo su
```, just for testing a few things. The root account is still locked here - and the problem remains the same if I issue the command as a normal user.

---

### Post by sudodus on 2016-03-20
Can you try to figure out if the problem is with the computer (hardware, uefi/bios etc), or with the installed operating system?

What happens if you boot a live system (from a USB pendrive) in that machine? Will it still be stubborn and stick to its own time setting?

Is there some menu in the UEFI/BIOS system for date and time, where you can change this behaviour or at least set the time to be correct?

---

### Post by Hammi on 2016-03-21
Ok, so I did a couple of tests after preparding a USB live medium (gparted for this purpose).

In gparted, setting the date without sudo yields the same behavior as under Ubuntu, i.e.

```
user@debian:~$ date
Mo 21 Mar 07:46:21 CET 2016
user@debian:~$ date -s "2016-03-21 08:00:00"
Mo 21 Mar 08:00:00 CET 2016
user@debian:~$ date
Mo 21 Mar 07:47:01 CET 2016
```

With sudo, its working:

```
user@debian:~$ date
Mo 21 Mar 07:47:01 CET 2016
user@debian:~$ sudo date -s "2016-03-21 08:00:00"
Mo 21 Mar 08:00:00 CET 2016
user@debian:~$ date
Mo 21 Mar 08:00:07 CET 2016
```

So then I booted into Ubuntu 14.04.4 server again:

```
user@machine:~$ date
Mo 21 Mar 07:53:01 CET 2016
user@machine:~$ date -s "2016-03-21 07:51:00"
date: das Datum kann nicht gesetzt werden: Vorgang nicht zulässig [tranlsation: date cannot be set: operation not permitted]
Mo 21 Mar 07:51:00 CET 2016
user@machine:~$ sudo date -s "2016-03-21 07:51:00"
[sudo] password for user:
Mo 21 Mar 07:51:00 CET 2016
user@machine:~$ date
Mo 21 Mar 07:53:40 CET 2016
```

So as you can see, under Ubuntu I get an error, if I try it without sudo. With sudo, no error, but it's still not working.

I guess this test also clarifies that this should not be related to the BIOS, as it works from the live stick (which I booted with UEFI as well, by the way, just as Ubuntu).

Again, I'm lost...

---

### Post by sudodus on 2016-03-21
I agree, it depends on the operating system.

1. The next step would be to try with a live Ubuntu system, for example Ubuntu 14.04.4 LTS ***desktop*** (64-bit for UEFI, matching what you use in the server system).

If you want to download a smaller file and a lighter system, you can install the corresponding ***Lubuntu desktop iso file*** flash it into a USB pendrive and boot from it.

This test would indicate if the problem is with the Ubuntu system under the hood, or if something is damaged in your installed Ubuntu Server system.

2. The next step might be to install Ubuntu Server into [another] USB drive. It would probably be enough with a mini system without any particular services installed, only a basic text screen system. Can you manage the date in that system? See this link:

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

> 2. Install (a complete installed system) to a USB stick or pendrive and boot from it.

---

### Post by Hammi on 2016-03-25
Ok, that took a while. But finally I managed to install ubuntu onto a stick, and then managed to find a time slot where playing around with the server wouldn't annoy too many people. :D

ubuntu 14.04.4 server on the stick works.

```
user@ubuntu-mobile:~$ date
Fri Mar 25 08:06:21 CET 2016
user@ubuntu-mobile:~$ date -s "2016-03-25 08:39:00"
date: cannot set date: Operation not permitted
Fri Mar 25 08:39:00 CET 2016
user@ubuntu-mobile:~$ date
Fri Mar 25 08:07:12 CET 2016
user@ubuntu-mobile:~$ sudo date -s "2016-03-25 08:39:00"
[sudo] password for user:
Fri Mar 25 08:39:00 CET 2016
user@ubuntu-mobile:~$ date
Fri Mar 25 08:39:05 CET 2016

```

On the server itself, it's still not working:

```
root@machine:/home/user# date
Fri 25 Mar 08:47:55 CET 2016
root@machine:/home/user# date -s "2016-03-25 08:00:00"
Fri 25 Mar 08:00:00 CET 2016
root@machine:/home/user# date
Fri 25 Mar 08:48:27 CET 2016
```

---

### Post by sudodus on 2016-03-25
This indicates, that there is something in your installed system (the server itself), that borks the date setting.

Can you think of anything you have installed or tweaked, that might need and cause syncing with some other computer or something like that, or for some reason cannot allow changing the time? For example, I can imagine that book-keeping programs (for a company's economy) must not be back-dated in order to avoid manipulation (economic crime).

But it might be a bug too, maybe caused by a conflict with one of the installed program packages.

---

### Post by Hammi on 2016-03-25
The machine runs no applications as such. It serves as a host for VMs, and runs the data graves for the VMs (md raid for 2x boot SSDs, zfs across 8 HDDs). 

```
apt-get install smartmontools
add-apt-repository ppa:zfs-native/stable 
apt-get update 
apt-get install spl-dkms 
apt-get install zfs-dkms 
apt-get install ubuntu-zfs
apt-get install nfs-kernel-server
apt-get install samba-common samba
```

I also installed a minimal unity desktop for virt-manager.

```
apt-get install ubuntu-desktop --no-install-recommends 
apt-get install unity-lens-applications unity-lens-files 
apt-get install gnome-disk-utility gparted
```

And then a few tools like htop, mc, etc. I didn't keep track of everything, obviously.
If it helps, I could post the output of 

```
dpkg --get-selections | grep -v deinstall
```

One further question: My normal system boots via UEFI, the stick does not. Could that make a difference?

---

### Post by sudodus on 2016-03-25
I'm afraid that I don't understand what those program packages might do to the time settings. I think we can agree that some of them should be 'harmless' for example ubuntu-desktop, gparted, htop, mc. I have smartmontools and I don't have your problems.

I checked in a live UEFI system (with Ubuntu xenial beta 2 desktop) and I can change the clock like I can in BIOS mode.

***Anyone, who reads this thread, please chip in an help :-)***

---

### Post by 1clue on 2016-03-25
Do you have a service on a vm that might mess with the clock?

Traditionally the host runs ntp or simil.ar to keep the clock accurate and the virtualization software keeps the guest clocks synced. I can imagine a scenario where a guest fiddles with the clock thereby changing the host time. Not sure if it would work that way but worth a look.

---

