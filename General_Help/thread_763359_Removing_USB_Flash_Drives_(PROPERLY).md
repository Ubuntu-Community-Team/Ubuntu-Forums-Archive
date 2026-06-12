---
title: "Removing USB Flash Drives (PROPERLY)"
date: 2008-04-22
forum: General Help
---

### Post by Jebtrix on 2008-04-22
I looked through previous posts but none cover exactly what I want to know. I use USB sticks alot and they get detected and work just fine. I've had many sticks go bad over the years so this question is part paranoia now that im wielding my shiny new 32GB shizstik and I don't wanna f00bar it up [-o<

If I *properly* remove a USB device in winblowz, the USB stick activity light turns off, which with my experience is the safest and keeps Murphy's Law from happening. However in Ubuntu when I unmount the USB drive the activity light still lit up. Is there a more definitive removal of a USB device? Eject command? 

Sux being a n00b... TIA.

---

### Post by jen1963 on 2008-04-22
> **Jebtrix said:**
> I looked through previous posts but none cover exactly what I want to know. I use USB sticks alot and they get detected and work just fine. I've had many sticks go bad over the years so this question is part paranoia now that im wielding my shiny new 32GB shizstik and I don't wanna f00bar it up [-o<

If I *properly* remove a USB device in winblowz, the USB stick activity light turns off, which with my experience is the safest and keeps Murphy's Law from happening. However in Ubuntu when I unmount the USB drive the activity light still lit up. Is there a more definitive removal of a USB device? Eject command? 

Sux being a n00b... TIA.
I use those sticks myself and never had any problem with data corruption as long ***_as the drive is unmounted properly_***.
Had the same good luck with external Western Digital USB hard drives too.

---

### Post by Bubba64 on 2008-04-23
If you screw up the stick you can use gparted to repartition. I also found a trick on the forum to delete stuff off of the thumb drive highlight the package you want removed and hit shift-delete. If you click on computer in places it will tell if the USB needs to be mounted by right clicking on the icon, to confirm you have unmounted it.

---

### Post by lauriejb on 2008-04-23
I'm a definite tyro in this world but one thing I have found is that you MUST clear the trash can before taking the stick out.  The capacity seems not to restore properly if this is not done.  It might also help to wait if the stick is a big capacity one.

---

### Post by Bubba64 on 2008-04-23
> **lauriejb said:**
> I'm a definite tyro in this world but one thing I have found is that you MUST clear the trash can before taking the stick out.  The capacity seems not to restore properly if this is not done.  It might also help to wait if the stick is a big capacity one.

I removed the trash with the shift-delete and just remove everything that way. I was having problems getting the trash to empty due to a built in program that was MS based for compressing info.

---

### Post by oralalikaroaku on 2008-09-17
I followed the instruction to unmount the flash disk by right-clicking the mouse, sometimes tells me it's now safe to remove flash but sometime not... Im on ubuntu 8.4 dell inspiron.

Newbie

---

### Post by clearnitesky on 2008-11-22
Currently this is the only solution to the problem, it does work well though.

   1. Safely eject from Konqueror/Nautilus
   2. Enter root via su command
   3. sdparm –command=sync /dev/sdc
   4. sdparm –command=stop /dev/sdc

(obviously, you need to substitute "/dev/sdc" for the location of your drive, for me this was "/dev/disk/by-label/ext_drive", but I'm using Debian, so it could be different for you)

---

### Post by Jebtrix on 2009-01-06
I tried sdparm commands but all I get is 
"Unexpected extra argument: /dev/disk/by-label/USBSTICK"

I read another post about the same error message when dealing with an actual hard drive but the solution didn't work for this :frown:

---

### Post by Nico0020 on 2009-01-06
I've always wanted a way to properly unmount USB devices.  All my USB drives and such never have their activity light turn off but yet say it is safe to remove.  This should be addressed in future versions of ubuntu.

---

### Post by Jebtrix on 2009-01-06
Thats the un-nerving part. I've already dismounted the USB stick in nautilus and have the light go out. Rarely but it has happened. 

Just a small update since starting this thread I did actually end up whacking my 32GB stick (thank god for lifetime warranty :D ). I'm not blaming it on Ubuntu but its not confidence inspiring.

---

### Post by dcstar on 2009-01-06
> **Nico0020 said:**
> I've always wanted a way to properly unmount USB devices.  All my USB drives and such never have their activity light turn off but yet say it is safe to remove.  This should be addressed in future versions of ubuntu.

The "light" is just the USB device being connected to an active USB port - the USB device itself has no idea if the filesystem is mounted or unmounted.

If the USB device itself is somehow caching data before it writes it, then there is a risk of data corruption if the device is removed before the cache is emptied (the O/S "thinks" it is safe, but actually it is not - yet).

Using the unmount/eject in Linux should be safe as long as you wait a few seconds before pulling the connection.

---

