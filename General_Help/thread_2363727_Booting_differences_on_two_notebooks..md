---
title: "Booting differences on two notebooks."
date: 2017-06-13
forum: General Help
---

### Post by northlynx on 2017-06-13
Hello. I am new to linux and just installed Lubuntu on two old Laptops of mine: 

A 2008 Thinkpad R61 with C2D T7100 CPU + 2GB memory and a 2011 HP630 with Celeron 800 CPU and 2GB memory. 

Now I noticed, that the R61 takes considerably longer to boot up even though I installed an SSD (benched it with 270 MB/s read speed). While the HP has a slightly faster CPU its only got a mechanical HDD with 80 MB/s. 

Now I noticed during boot up both show a different screen: 

Lenovo: 
[[IMG]https://abload.de/thumb/img_20170613_18560569disc7.jpg[/IMG]]("http://abload.de/image.php?img=img_20170613_18560569disc7.jpg")

HP: 
[[IMG]https://abload.de/thumb/img_20170613_193758364ssk7.jpg[/IMG]]("http://abload.de/image.php?img=img_20170613_193758364ssk7.jpg")

As you can see the Lenovo only shows the first row, while the HP shows a lot more and it only shows this screen for about two seconds, while the lenovo has it for like 10 seconds. Also shut down with the HP is almost instantly, while with the Lenovo it shows this screen again and takes 5 - 10 seconds longer to shut down. 


All hardware and programs work flawlessly on both machines and with Lubuntu they feel very fast and responsive, the Lenovo is faster though, when it comes to launching programs, due to its SSD. If only the Boot Up was fast as well. :(

I already reinstalled Lubuntu on the Lenovo with the same result. Is this normal behavior or is something not right? pls help

---

### Post by oldfred on 2017-06-14
What video card/chip in each system?

If only Ubuntu installed, you normally do not get grub menu.
But with BIOS install you can hold shift key from BIOS until menu appears.

And on linux line is quiet splash boot parameters, those normally hide all the lines you see when booting. Did you remove quiet splash?

Post this as it is where setting is, or to test you can manually edit grub as you boot.
 sudo nano /etc/default/grub
[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)
GRUB_CMD_LINUX


[LIST]
[*]Entries on this  are added to the end of the 'linux' command  (GRUB legacy's "kernel" ) for both normal and recovery modes. It is used to pass options to the kernel.
[/LIST]
 GRUB_CMD_LINUX_DEFAULT="quiet splash"

[LIST]
[*]This  imports any entries to the end of the 'linux'  (GRUB legacy's "kernel" ). The entries are appended to the end of the normal mode only.
[/LIST]
     o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash".

---

