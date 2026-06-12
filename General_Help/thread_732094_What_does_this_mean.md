---
title: "What does this mean?"
date: 2008-03-22
forum: General Help
---

### Post by Derek Chai on 2008-03-22
ata3.00:exception Emask 0x0 sact 0x0 serr 0x0 action 0x2 frozen
ata3.00 cmd c8/00:08:00:00:00/00:00:00:00:00:00/c0 tag 0dma 4096 in
ata3.00 status:{DRDY}

What does it mean...

I'll get the live CD thing that pops up too that's from my installation of wubi. When I try to boot it up from grub.

---

### Post by Gen2ly on 2008-03-22
Well ata is a hard disk.  I don't see anyting that looks like an error msg though.  I'm not familiar using wubi, tried using the regular ubuntu LiveCD?

---

### Post by keratos on 2008-03-22
> **Dirk.R.Gently said:**
> Well ata is a hard disk.  I don't see anyting that looks like an error msg though.  I'm not familiar using wubi, tried using the regular ubuntu LiveCD?

"*Dont see any errors *"     cough ... Are you looking at the same thread as me?

Derek: 
The PCI bus is throwing errors. Try, if you know how, adding the "noacpi=true" to the kernel boot command "Boot:" at boot time. If you are using grub then press "e" to edit the boot line with the word "kernel=" on it.

---

### Post by Derek Chai on 2008-03-22
Can you explain how to do the noapi? Sorry I don't know which files etc.

---

### Post by keratos on 2008-03-23
do you boot using LiLO or GRUB

Does "LiLo" appear when you power up or does "Boot:" appear ?

---

### Post by Derek Chai on 2008-03-23
wait I think it's neither
[http://youtube.com/watch?v=XZI_htOeqEQ](http://youtube.com/watch?v=XZI_htOeqEQ)

Check the boot thing that's the whole boot.

---

### Post by keratos on 2008-03-24
sorry, i block flash and scripts. personal preference.

you will need to tell me what boot loader you installed.

---

### Post by Derek Chai on 2008-03-24
I have a NTLDR boot loader according to HP live help.

---

### Post by Derek Chai on 2008-03-24
If you mean for ubuntu at the ESC for different settings or whatever it's called I think that is grub but when I choose ubuntu it's the one I listed above.

---

### Post by keratos on 2008-03-24
> **Derek Chai said:**
> I have a NTLDR boot loader according to HP live help.

Well, you have either:

a) installed the linux boot loaders (either LiLo or GRUB) into a partition rather than a disk MBR
b) you have not updated the BIOS to make sure the disk you installed linux on is being booted first.
c) aborted the linux install process or it failed.

I don't think there can be any doubt of the above , if NTLDR is running.

---

### Post by Derek Chai on 2008-03-24
Does Wubi install anything? Live CD doesn't even run for me. So I had to use wubi. What should I do edit the wubi menu lst?

---

### Post by keratos on 2008-03-25
I have no experience with "wubi"

Did you download the "Alternate install live CD" and use that. It is not a graphical GUI and live CD so if you require a live CD, knoppix is very good. If however you want to install ubuntu, use an ubuntu CD.

---

### Post by Derek Chai on 2008-03-26
I'll try it can you link me to the 8.04 one?

---

### Post by keratos on 2008-03-26
[http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=i386&mirror=http%3A%2F%2Fmirror.ox.ac.uk%2Fsites%2Freleases.ubuntu.com%2Freleases%2F&debug=&download-button=&alternatecd=alternate](http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=i386&mirror=http%3A%2F%2Fmirror.ox.ac.uk%2Fsites%2Freleases.ubuntu.com%2Freleases%2F&debug=&download-button=&alternatecd=alternate)

Hardy (v8.x) is UNSTABLE and should not be used if you dont know what you are doing.

Use 7.10 as per link.

No disrespect, but dont use v8.

---

### Post by Derek Chai on 2008-03-27
It partions my HD for me right?

---

### Post by keratos on 2008-03-27
its the same as hardy in that respect.

---

