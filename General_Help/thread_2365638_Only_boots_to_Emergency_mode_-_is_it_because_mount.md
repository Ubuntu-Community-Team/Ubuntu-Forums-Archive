---
title: "Only boots to Emergency mode - is it because mount -a can't run?"
date: 2017-07-08
forum: General Help
---

### Post by cable_guy on 2017-07-08
Hi,

My Ubuntu won't boot, it only goes to Emergency mode.  One change I've made since it was rock solid is disconnecting one of my USB drives which is referenced in /etc/fstab, so will definitely be affecting mount -a.

I noticed during boot it stalls on "starting show plymouth boot screen" then goes to emergency mode, I can see red lines for the USB disk being missing, but red lines for other stuff I don't understand.  I really can't debug the emergency log as it's only on my console and I don't know how I would be able to export them.

on previous installs I've had (kodibuntu) when this has happened it's given me a friendly message on boot whereby I can choose to ignore the mounting, but not on this install

---

### Post by #&amp;thj^% on 2017-07-08
> **cable_guy said:**
> Hi,

My Ubuntu won't boot, it only goes to Emergency mode.  One change I've made since it was rock solid is disconnecting one of my USB drives which is referenced in /etc/fstab, so will definitely be affecting mount -a.

I noticed during boot it stalls on "starting show plymouth boot screen" then goes to emergency mode, I can see red lines for the USB disk being missing, but red lines for other stuff I don't understand.  I really can't debug the emergency log as it's only on my console and I don't know how I would be able to export them.

on previous installs I've had (kodibuntu) when this has happened it's given me a friendly message on boot whereby I can choose to ignore the mounting, but not on this install

Is this a UEFI bios system ?
Also lets see if anything is sticking out in grub.
```
 nano /etc/default/grub
```
paste back here....this might be a slow process...but needs to be done.

---

### Post by Bucky Ball on 2017-07-08
Are you using Ubuntu or an official flavour of it or Kodibuntu?

Open a terminal, open this file:

```
sudo nano /etc/fstab
```

Look for the line that relates to the USB drive and put a '#' in front of it. This means the system will ignore that line (you could delete but you may want to add that USB drive back, if not, delete the line completely).

Reboot. Any different? If you have different errors, or less, let us know.

---

### Post by deadflowr on 2017-07-08
> **1fallen said:**
> Is this a UEFI bios system ?
Also lets see if anything is sticking out in grub.
```
 nano /etc/default grub
```
paste back here....this might be a slow process...but needs to be done.

It should be
```
nano /etc/default/grub
```

But yes, compare the fstab to the partitions you have connected to the machine 
(and those partitions not connected to the machine)

Use 
```
sudo blkid
```
to get the UUIDs of the partitions so you can do a comparison to the entries in the fstab file.

---

### Post by efflandt on 2017-07-09
Actually if you just want to look at the file you could use```
less /etc/default/grub
```If you actually wanted to change anything in it you would use```
sudo nano /etc/default/grub
sudo update-grub
```Unless in root console in recovery mode and partition has been remounted from read-only to read-write (in which case sudo would not be required).

---

### Post by cable_guy on 2017-07-10
Thanks for the replies, I ended up waiting and attaching the drive as I Was right, it booted.  Bit annoying that it's so dependent on fstab.

---

### Post by yancek on 2017-07-10
The fstab file will mount or try to mount any partition listed there so if you have a drive partition which is not always going to be connected, remove or comment out the entry in fstab.  That's the way it's designed to work.

---

### Post by Bucky Ball on 2017-07-11
> **yancek said:**
> The fstab file will mount or try to mount any partition listed there so if you have a drive partition which is not always going to be connected, remove or comment out the entry in fstab.  That's the way it's designed to work.

As instructed in post #3. You haven't done it?

---

