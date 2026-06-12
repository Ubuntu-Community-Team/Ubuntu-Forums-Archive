---
title: "Help, grub is driving me crazy"
date: 2008-02-22
forum: General Help
---

### Post by noobuntoo on 2008-02-22
hi all.

 I had a hard drive die recently and had to get a new one. After installing it my grub became all confused and i have a suspicion its pointing in the wrong direction now. Here's how my setup looks like.

I have 2 hard drives.

One is an IDE drive that has windows on it

The second is a SATA drive with ubuntu 7.04 on it.

Now grub did previously work fine, but when i replaced the first hard drive with windows on it, it became confused. The drive was replaced with another IDE drive and windows reinstalled on it from scratch fine. I used supergrub disc to install grub again and it wont work now. I really dont want to have to delete anything on my other hard disk.

Here's what i can gather from using livecd.

On my second drive in /boot/grub/ i can see device.map. It reads...

(hd0)	/dev/hdc
(hd1)	/dev/sda

Not so sure if this is correct.

If i go half way through an ubuntu install, it tells me that my first hard drive is...

/dev/sda
partition located at /dev/sda1
mountable at /media/sda1

and my second hd is

/dev/sdb1
mountable at /media/sdb1
with a swap partition at /dev/sdb5

as for my menu.lst, it reads...

title		Ubuntu, kernel 2.6.20-16-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=038ee942-163d-4b41-9b87-78b255de873c ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-386
savedefault

title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

I get a feeling that grub is pointed to the wrong location now that i installed a new drive, but i'm unsure what to change. Whenever i try to install grub again, if its wrong i end up going through the whole fixmbr stuff just to get windows to work again and its really a pain. Can someone tell me what i need to change to make my grub correct? Thanks in advance.

---

### Post by mahuyar on 2008-02-23
Let's try installing GRUB the manual way.  Boot into your live-cd.  Fire up a terminal.  

1)  ```
 sudo grub 
``` to get into grub config env (or whatever you wanna call it).

2)  Tell GRUB your boot device ( /dev/sda in your case):
```
 device (hd0) /dev/sda 
```

3)  And your boot partition:
```
 root (hd0,0) 
```

I think some explanation of what's going on should help you better here.  We're assuming that your /boot directory is in the first partion of /dev/sda.  The "0" after the comma means first partition of /dev/sda (GRUB starts counting from 0), and "hd0", I believe, is just a variable/pointer that we've defined in step 2 (I'm not entirely sure here though).

4)  ```
 setup (hd0) 
```
5)  ```
 quit 
```

We'll now run ```
 sudo update-grub 
```

Look out for any error messeages and ... post back your results.  Good Luck!

---

### Post by zxscooby on 2008-02-23
whenever i see someone who is confused about grub i point them to this
site [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
I found it very informative

---

### Post by noobuntoo on 2008-02-26
Thanks for the help. I'm finally getting around to doing this.

Are there no changes to device.map that i have to do? Or is this done when i install grub automatically?

---

### Post by mahuyar on 2008-02-27
> **noobuntoo said:**
> Thanks for the help. I'm finally getting around to doing this.

Are there no changes to device.map that i have to do? Or is this done when i install grub automatically?

As far as I've tried to setup GRUB on a couple of machines, I didn't have to touch device.map.  And I'm not exactly sure what device.map does.

---

### Post by noobuntoo on 2008-02-27
just wanted to say thanks a lot. You guys are lifesavers. i figured it out.

After reading about grub at that link that was posted i figured out i actually did have to edit device.map because with the new hard drive it was wrong.

I booted with a livecd, edited the device.map so it read 

hd0 /dev/sda
hd1 /dev/sdb

then i ran grub to install it, except i put

root (hd1,0)

when i reached that step.

Now everything is back to normal. phewwww :)

---

