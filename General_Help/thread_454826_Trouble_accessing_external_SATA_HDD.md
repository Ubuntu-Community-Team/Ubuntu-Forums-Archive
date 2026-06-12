---
title: "Trouble accessing external SATA HDD"
date: 2007-05-25
forum: General Help
---

### Post by John W on 2007-05-25
Hi all,

I'm fairly new to the Linux sceen, been using Ubuntu 6.06 LTS for about 6mos now with no complaints. I have a SATA drive from my previous windows install that has some files on it (specifically music files that were erased from my ipod the first time I used gtkpod) that I would like to get. I put it in an external SATA HD enclosure, plugged it in, turned it on, and it was not detected by Ubuntu.
 So here are my questions:

1) How do I get the external HD to be recognized?
2) Once recognized, will I be able to just go and get the files I want?
3) I would like to try out Feisty, can I load it on that drive and boot off it externally?

Thank you in advance for your time.

---

### Post by mbradlcu on 2007-05-27
is the sata drive connect via usb? if so then you may have to explicedly mount it here's an example but you're settings will most likely be a little different:
```
sudo mount -t ntfs /dev/sdd1 /mnt
```
then you're files will be readable at the /mnt directory.

as for question 3,, short answer is yes but it requires editing the grub boot configuration.. something I don't do much ; (

---

### Post by John W on 2007-06-06
Thanks for your reply and sorry it took so long to get back to you. I have the external drive connected via sata connector, so I don't know if that will make a difference in the mount command.

---

