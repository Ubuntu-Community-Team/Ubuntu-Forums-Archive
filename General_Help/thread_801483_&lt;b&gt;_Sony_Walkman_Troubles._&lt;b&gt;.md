---
title: "&lt;b&gt; Sony Walkman Troubles. &lt;b&gt;"
date: 2008-05-20
forum: General Help
---

### Post by JumpmanRugs on 2008-05-20
Hi Guys.

I have a Sony Walkman NWZ-S515.

I love it and think its great but since changing to ubuntu hardy heron from Vista I've experienced problems with it.

For instance, on Vista i could plug it in and transfer files and stuff over. Now i am unable to that as it just says 'Connecting' when i plug it in and no matter how long i leave it to connect, it never actually does so i am unable ot transfer files to and form my walkman. 

Can anybody please help me? It'd be greatly appreciated

Cheers****

---

### Post by TomGar on 2008-05-24
I had the same problem.
This thread gave me what I needed.
[http://ubuntuforums.org/showthread.php?t=790330](http://ubuntuforums.org/showthread.php?t=790330)

lsusb to see if it's connected
then sudo gparted to see where it's device name is (sdc in my case) 
then (just the once) sudo mkdir /media/nwz-s515 (to create the mount destination)
finally sudo mount -t vfat /dev/sdc /media/nwz-s515

and with luck you should have mounted the device.

Alternatively and much simpler try using amarok and connect as an mtp device!

Good luck

---

### Post by miluns on 2008-05-27
Hi,

I'm a little late to this thread, but here is a solution that worked for me. Hopefully it will help somebody else.

install pmount

sudo fdisk -l   to find out the location to mount ( /dev/sdb ) for me

right click applications > choose edit menus

click new item

name new item whatever you want (I used mount walkman)

put pmount /dev/<yourdevice> in the command line 

click ok

do the same thing for an unmount but use pumount /dev/<yourdevice> for the command

All that is left is to plug in your walkman and choose mount from the menu.


This is not a automatic mount, but it works for me,

Regards,

Mike

---

