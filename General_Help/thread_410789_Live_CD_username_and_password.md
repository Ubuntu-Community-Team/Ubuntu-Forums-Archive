---
title: "Live CD username and password"
date: 2007-04-16
forum: General Help
---

### Post by Knitter on 2007-04-16
Hi,
I think this question shold have been asked before but I can't narrow down the search to find anything useful.
I've been remastering the Ubuntu CD this way:

sudo /etc/init.d/networking restart
sudo cp /etc/resolv.conf edit/etc/
sudo cp /etc/X11/xorg.conf edit/etc/X11/
sudo chroot edit
mount -o none /proc
mount -o none /sys
export HOME=/etc/skel/
cd /dev/
MAKEDEV generic
/etc/init.d/dbus start
/etc/init.d/gdm start

The problem is that I'm now faced with the GDM login screen and I don't know the username nor the password to login in my system.

Is there any place where I can find this information? or any information regarding the Ubuntu Live CD?

Thanks,

Knitter

---

### Post by beerorkid on 2007-04-16
I would try ubuntu or user

username: ubuntu
passwd: ubuntu

username: user
passwd: user

possibly guest.  Pretty sure it is ubuntu though.

---

### Post by Knitter on 2007-04-16
Thanks but I had already tried that. Both actualy :)

I'll revert to changing the system in console mode... but there are things I must do inside gnome, or that I only know how to do inside gnome.
Is there any place I can find more information?

Is there another way to "get to feel" the GNOME system in my chroot environment? One that relies on the fact that I'm root to the choort environment or that does not require authentication?

---

### Post by artinla on 2007-04-16
You need more RAM.

I was presented with the same screen until I put at least 512 meg of RAM in the machine.  The problem then went away.  I think the initrd gets borked somehow with remastering programs such as reconstructor.

I was able to put together a bootable live DVD of edgy which included a local repo of all the updates using reconstructor and the falcon repository creator.  The disk works perfectly.

Good luck

Art

---

### Post by Knitter on 2007-04-16
512 RAM you say... hum... strange. My specs:
Core 2 Duo @ something
1 GB RAM
2 GB SWAP
260 GB HDD
Ubuntu 7.04 beta SO.

I'm trying to remaster the same SO, Ubuntu 7.04 beta. I don't use reconstructor. All the commands I type are in single user mode.

If the problem is RAM, there is nothig I can do about it. But I have remastered KNOPPIX with a P3 and 128MB of RAM within the GNOME environment.

Any more thoughts?

---

### Post by artinla on 2007-04-16
Sorry, I misunderstood your predicament.  I thought your remastered disk was presenting you with the login screen, not a chroot environment.  Your problem may still be RAM, but your situation is different than mine. 

In my case, when booting up under the remastered live DVD I would get an authentication window that only occurred when running less than 512 meg of RAM.  It related to the number of upgraded packages and new programs that I had added to the disk.  (My remastered disk is over 3 gigs)

I don't know the answer to your problem, but suggest that you consider reconstructor.  It is a great program and I have had good success with it.  If you still run into trouble, PM me and I will be glad to assist.

Good luck,

Art

---

