---
title: "Can I mount a flashdrive to /cdrom/"
date: 2008-05-27
forum: General Help
---

### Post by mishathegoat on 2008-05-27
Hi everyone!

I installed a form of Xubuntu from my Flashdrive (because my EeePc has no CDROM drive). Now I'm trying to install build-essential and it's asking me for a Cd? What can I do? Can I mount the LiveCD-Flashdrive to /cdrom/?

---

### Post by werries on 2008-05-27
either you can redirect it to the file on the flashdrive...orrr... to mount it, it should be just
```
sudo mount /dev/sdx /cdrom
```

where x is your flash drive's label.
if you dont know what it is, run 
```
sudo fdisk -l
```
and find the correct one.

---

### Post by mishathegoat on 2008-05-27
The command completed successfully but I go to /cdrom and there's nothing there.. I suppose I could download the Xubuntu iso and just mount that

---

### Post by pointone on 2008-05-27
Do you have Internet access? If so, edit /etc/apt/sources.list and comment out the CDROM source; build-essential's dependencies will then be downloaded from the Internet.

---

### Post by superyounan1 on 2008-05-27
> **pointone said:**
> Do you have Internet access? If so, edit /etc/apt/sources.list and comment out the CDROM source; build-essential's dependencies will then be downloaded from the Internet.

that would work if you have internet access (as mentioned). your idea to mount your flash drive to the /media/cdrom directory would work too i think if you need to install from the flash drive

If you need to do it the second way, post the output for these:

```

mount

```
and 
```

df -v

```

while your flash drive is plugged in. if its not clear which device in /dev belongs to the flash drive though, post the output of those commands before and after plugging in your flash drive

---

