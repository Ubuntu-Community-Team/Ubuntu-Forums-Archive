---
title: "Create .iso file from bootable cd."
date: 2007-02-10
forum: General Help
---

### Post by ghandi69_ on 2007-02-10
You There!!

I'm playing around with virtualbox and trying to install the copy of Vista my university gave me under a virtual machine.  However, VirtualBox does not detect my cdrom unless I unmount it first, but I would rather somehow be able to create an .iso file from my windows dvd.  Anyone know how to do this.  Linux has been rocking my world so much lately I wouldn't be suprised if it was just...

fiso -mk vista.iso media/cdrom

or something simple like that. .. "I made that up..."

---

### Post by ghandi69_ on 2007-02-10
ok... seems to not be easy to answer.. what about.. how would I go about unmounting my cdrom drive.. I've heard virtual box will then be able to recognize it.

---

### Post by igknighted on 2007-02-10
> **ghandi69_ said:**
> You There!!

I'm playing around with virtualbox and trying to install the copy of Vista my university gave me under a virtual machine.  However, VirtualBox does not detect my cdrom unless I unmount it first, but I would rather somehow be able to create an .iso file from my windows dvd.  Anyone know how to do this.  Linux has been rocking my world so much lately I wouldn't be suprised if it was just...

fiso -mk vista.iso media/cdrom

or something simple like that. .. "I made that up..."

I dont know the terminal commands to do that, but I believe k3b can do that?  i don't have it in front of me ATM, but I think it can.  Otherwise, try browsing Synaptic for an appropriate program.

---

### Post by koenn on 2007-02-10
your original "i made that up" command was quite close. 
try
```
 dd if=/dev/cdrom of=/visa.iso
```

This will be easier if you 'cd' into the destination directory first:, eg
```
cd /home/ghandi69_/images
```
because then that's where visa.iso will be created

---

### Post by ghandi69_ on 2007-02-10
That dd command was exactly what I was looking for!! Worked perfectly.... I now have Vista running successfully in Virtual Box!!  Maybe someday I'll eventually lose the noob tag.

Thanks for the help guys... 

note:: that dd worked pretty fast.. the vista dvd is almost 3 gigs.. it only took about 2 minutes to make it into a .iso

note::its pretty humorous I thought, but during most of the Vista install.. a message says "Windows will need to reboot several times in order to complete the installation" 

!!!  lol I was laughin when I read that.. sure enough.. it rebooted 3 times on its own before it could log me and and let me know about all the great features....

I'm not sure what I'm going to do with Vista now... but my only plans now are to use it to copy music with EAC (exact audio copy).. or at least until I get it running under wine... and also use it do run the occasionally necessary .exe downloading app or something like..

---

