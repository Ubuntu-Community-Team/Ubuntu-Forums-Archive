---
title: "MTP devices"
date: 2007-11-29
forum: General Help
---

### Post by discoade on 2007-11-29
Hi guys!

Im fairly new to ubuntu ver 7.10 (48 hrs)

Are MTP devices supported in this version i have a samsung k3 mp3 player and was wondering if i can use it in ubuntu of do i need to revert back to xp to make it work!](*,)  

if they are supported how do i set it up? TIA. :guitar:

---

### Post by nikoPSK on 2007-11-29
mtp? If you explaing i can help....

---

### Post by discoade on 2007-11-29
MTP  media transfer protocol  The new format for mp3 players and the like!

---

### Post by nikoPSK on 2007-11-29
should work wonderfully, just plug it in.

---

### Post by etnlIcarus on 2007-12-08
Having just bought a Samsung U3 player today, I can tell you MTP is supported - somewhat.

Amarok can manage MTP devices. Just go to Settings>Configure Amarok>Media Devices.

Choose, "Add Device...". Name it and set it to be handled with, "MTP Media Device".

Save and close preferences and go to the Devices tab. Choose MTP Media Device from the drop-down and connect.

Having played around with this today, I can tell you Amarok is finicky. Try to queue up too many files and Amarok will crash and you'll get some corrupted data on the device.



On the other hand, if you're like me and you want to be able to manage your files in a file-manager manner, the closest thing i've found so far is **Gnomad 2** (it's in the repos). Gnomad suffers from the same problem as Amarok: if you try to move too many files at once, it goofs up.

Another possibility is **gphotofs**, which supposedly supports MTP but I haven't tested it, nor am I sure how to configure it.

---

### Post by discoade on 2007-12-08
Yes ive got amarock and it detected my k3 and works just fine!

Are you sure the problem your having isnt connected to the music preview bug? ie disabling the music preview in your file browser?  causes file browser to freeze. its on these forum some ware!

Just a thought as mine is working fine now ive disabled it.

---

### Post by NullHead on 2007-12-08
rhythm box works too.. just install lib mtp 

```
sudo apt-get install libmtpv6 libmtp-dev
```

---

### Post by Cuppa-Chino on 2007-12-13
[I]how do I get to transfer video files onto an mtp device?

i have an iriver clix (mtp only version unfortunately) that can play videos, I can transfer audio files with amarok but how can I transfer video files?

any other tools but command line mtp-tools avail ? is there a help page for the mtp-tools somewhere?[/I]

SOLVED in Shell:

mtp-connect --sendfile /*video*/*directory*/*film.avi* [COLOR="Blue"]*Video*[/COLOR]

only question for me is whether there is a GUI application avail

---

