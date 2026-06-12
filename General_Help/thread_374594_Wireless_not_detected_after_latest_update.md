---
title: "Wireless not detected after latest update"
date: 2007-03-02
forum: General Help
---

### Post by OrganicPanda on 2007-03-02
Hey I just had a pile of 104 updates so i thought what the heck, what harm could it do lol

when the system came back up because a restart was need wlassistant is telling me i have no usable wireless devices, which is a lie.

i don't know where to start troubleshooting this, any help?

Thanks,
Panda

---

### Post by orb9220 on 2007-03-02
Well for me the issue of was working and not now always had to do with the /etc/network/interfaces file. For some reason I would have to edit it with comment symbol all lines except the first lines auto lo like this:

> auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


#iface ath0 inet dhcp
#wireless-essid [www.xxx.net](www.xxx.net)

#iface ath0 inet dhcp
#wireless-essid [www.xxxxx.net](www.xxxxx.net)

And reboot to get my nm-applet working again.
Hope this helps

---

### Post by OrganicPanda on 2007-03-03
Hey thanks for the reply, sadly it didn't work - my interfaces file looks like:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto ath0
iface ath0 inet dhcp

```

and when I run wlassstant from the command line I get:
```

Loaded application options.
DHCP Client: dhclient
All executables found.
iwconfig_status: /sbin/iwconfig
==>stderr: lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

No wireless interfaces found. Exiting.
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Application options saved.
Kernel socket closed.

```

What's wrong here, what tools can I use to check my wireless adaptor is working?

---

### Post by OrganicPanda on 2007-03-04
Somebody please throw me a bone here, I need help

---

### Post by syruppie on 2007-03-04
I have the same problem!

I saw 76 updates were available last night and decided to update before I went to bed.  Today, I found wireless not working.

What's worse is that my only link to the internet is my atheros card (Dlink G650 vB4).  My laptop is fairly old and does not include ethernet.  This essentially bricked my laptop.. which was mostly used for the internet and email.

Is it possible to revert the atheros driver from the new linux-restricted thingamajik to the old one that came with the cd??  If so, how?

---

### Post by DagMan on 2007-03-05
Are these problems where there was a kernel update, and using the old kernel solves the problem?
for example, is there a directory in /lib/firmware that is a kernel version number but it is not the same as what you see when you type uname -r

Just a shot in the dark.

---

### Post by domzo on 2007-03-05
>  Are these problems where there was a kernel update, and using the old kernel solves the problem?

Yes, at least in my case - I had  this same problem yesterday after an update. Removing the new kernel solved it.

To check if this will solve the problem press escape (or f2? can't remember offhand) during boot to enter the options menu and select to boot from the older kernel (2.6.17-10 in my case).

If your wireless works again then you can remove the new (offending) kernel package "linux-image-2.6.17.11-generic" 

i.e: sudo apt-get remove linux-image-2.6.17-11-generic

Note, please be careful! Make sure you have booted using the old kernel (2.6.17-10) while you remove the new one (2.6.17-11). Check the version in use with "uname -r" as DagMan suggested.

---

### Post by Episcopus on 2007-03-05
Perfect advice, that solved the problem for me too.

---

### Post by DagMan on 2007-03-05
On my machine, I'm able to copy the old firmware directory to the name of the new kernel and it doesn't break anything, for example, and while in the kernel that is not working:
sudo cp -r /lib/firmware/Old-Kernel-Directory /lib/firmware/`uname -r`
substituting Old-Kernel-Directory with whatever is there.  I can then reboot into either kernel.

If you want to do it from the old kernel and then reboot into the new one it would look like this:
sudo cp -r /lib/firmware/`uname -r` /lib/firmware/NEW-kernel-name
and NEW-kernel-name can be sort of figured out if you look at the bottom section of /boot/grub/menu.lst

This works for me, but the advice comes without warranty.  I doubt it would hurt anything.

Good luck

---

### Post by syruppie on 2007-03-05
Thank you so much! The sudo apt-get remove thing worked perfectly for me.

However I did try to follow Dagman's post first.  Sorry, I'm a newb in linux and I have to ask.. is the lib/firmware directory similar to Window's /windows/system32/drivers directory?

was that copy command trying to copy the old drivers from the old kernel to the new kernel?

I ask because I tried the command except i used

sudo cp -r /lib/firmware/2.6.17-10-generic /lib/firmware/2.16.17-11-generic

(was booting from old kernel when I tried this)

It did not work.  I tried booting from 2.6.17-11 afterwards and it still gave me a no network devices found message from network manager.

---

### Post by Ryzzen on 2007-03-05
I have the exact same problem with mine. A few weeks ago I installed Ubuntu, got all the drivers, and downloaded all the updates (including the new kernel) without any problems. Then I had some issues installing Beryl and ended up ruining my OS. (oops) I was fairly busy the next few weeks, so I left it alone. At the time, I remember there being 137 new updates.

Yesterday, I decide to format and reinstall Ubuntu. I installed my wireless drivers (I have a Broadcom 43xx one, btw), and then downloaded the updates. Upon rebooting, my wireless was nonexistant. It showed up under Device Manager, but not under Networking. I noticed that under Device Manager it was no longer in its own category. It looked like it was in a subcategory of my Ethernet card. There were 138 new updates when I downloaded them.

I'm thinking that it may not be the new kernel, but a different update which caused the problem, since prior to a few days ago, it worked fine with the new kernel update. I haven't yet tried booting from the old kernel yet, but I will as soon as I get home. I'm also going to reinstall one more time, and look through the list of updates to see if I can find something wireless related...

If anyone finds out anything more about this issue, please post.

---

### Post by DagMan on 2007-03-05
> **syruppie said:**
> Thank you so much! The sudo apt-get remove thing worked perfectly for me.

However I did try to follow Dagman's post first.  Sorry, I'm a newb in linux and I have to ask.. is the lib/firmware directory similar to Window's /windows/system32/drivers directory?

was that copy command trying to copy the old drivers from the old kernel to the new kernel?

I ask because I tried the command except i used

sudo cp -r /lib/firmware/2.6.17-10-generic /lib/firmware/2.16.17-11-generic

(was booting from old kernel when I tried this)

It did not work.  I tried booting from 2.6.17-11 afterwards and it still gave me a no network devices found message from network manager.

Hi,
I don't know much about Windows to answer that part of the question.

If 2.16.17-11-generic is indeed the name of the new kernel, which you look to see by booting into it and typing uname -r, and the directory is named correctly... and it doesn't work, then it might be possible to compile the drivers and firmware for your wireless device.  If you know what your wireless device is then I'd suggest searching the forums and googling a bit and if you don't come up with anything that works or that you understand then making a new thread specific your device would be a good idea, I think people are overlooking this one more by now since there's also a lot of unanswered posts.

Good luck with it.

---

### Post by Episcopus on 2007-03-05
> **Ryzzen said:**
> I have the exact same problem with mine. A few weeks ago I installed Ubuntu, got all the drivers, and downloaded all the updates (including the new kernel) without any problems. Then I had some issues installing Beryl and ended up ruining my OS. (oops) I was fairly busy the next few weeks, so I left it alone. At the time, I remember there being 137 new updates.

Yesterday, I decide to format and reinstall Ubuntu. I installed my wireless drivers (I have a Broadcom 43xx one, btw), and then downloaded the updates. Upon rebooting, my wireless was nonexistant. It showed up under Device Manager, but not under Networking. I noticed that under Device Manager it was no longer in its own category. It looked like it was in a subcategory of my Ethernet card. There were 138 new updates when I downloaded them.

I'm thinking that it may not be the new kernel, but a different update which caused the problem, since prior to a few days ago, it worked fine with the new kernel update. I haven't yet tried booting from the old kernel yet, but I will as soon as I get home. I'm also going to reinstall one more time, and look through the list of updates to see if I can find something wireless related...

If anyone finds out anything more about this issue, please post.

I would be fairly certain it is the new kernel.  I had wireless, installed all 138 updates, then didn't have wireless.  I booted from the old kernel and had wireless, so I removed the new kernel and I still have wireless.  I didn't undo any of the other updates.

---

### Post by OrganicPanda on 2007-03-06
I can confirm, at least for me, that booting into the old kernel (10, not the new 11) makes everything work, I don't mind this - thanks for the help everybody

---

