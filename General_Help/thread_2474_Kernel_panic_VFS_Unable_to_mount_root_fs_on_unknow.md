---
title: "Kernel panic: VFS: Unable to mount root fs on unknown-block (9.0)"
date: 2004-10-28
forum: General Help
---

### Post by uggeli on 2004-10-28
Well this is problem what friend of mine face to when she was trying  warty-release-live-i386. She asked me to post her problem here, so I try to write things as well as I can.

---------------
Computer:
---------------
Motherboard: Intel D845GRGR ATX 478
Processor: Intel Celeron 1.7 GHz
Memory: 256 MB DDR 266MHz
Grafic-card: nVidia GeForce MX400/TV 64 MB
Harddrive: Maxtor 540X 5400rpm 40GB
CD-RW: LG GCE825B
---------------
Those were information I got about computer after askin few question


After booting computer when live-cd was inserted in cd-drive, ubuntu first started to boot and after it was loading for a while, error message came to screen.

---------------
Error message:
---------------
audit (1098837639.4294966438:0): initialized

Welcome to the MORPHIX live CD!

Found SCSI device (s) handled by aha 152x.ko.
Found SCSI device (s) handled by  atp870u.ko.
Found SCSI device (s) handled by megaraid.ko.
Found SCSI device (s) handled by  a100u2w.ko.

Accessing MORPHIX CDROM at/dev/hdc...

Enabling DMA acceleration for hda [Maxtor4D040H2]

Enabling DMA acceleration for hdb [ST36531A]
 
Enabling DMA acceleration for hdc [HL-DT-ST GCE-8525B]


Warning: unable to Find base module!

Cat:/MorphixCD/etc/id.so.cache:No such file or directory

Setting paths.../linuxrc:543/bin/cp:not found

/linuxrc:543 test:  not found
/linuxrc:543 rm:    not found
/linuxrc:543 awk:   not found	
/linuxrc:543 echo:  not found
/linuxrc:543 expr:  not found
/linuxrc:543 test:  not found
/linuxrc:543 mkdir: not found 
/linuxrc:543 test:  not found
/linuxrc:543 echo:  not found
/linuxrc:543 mkdir: not found 

/linuxrc 543 cannot create/var/run/utmp:Directory nonexistent

VFS: Cannot open root device "<NULL<" or unknown-block (9,0)

Please append a correct "root"=boot option

Kernel panic: VFS: Unable to mount root fs on unknown-block (9.0)
---------------

So what excatly went wrong for her? And most importantly question, are those problems caused by hardware and if so, is it possible to install ubuntu on harddrive on that machine or will there be problems allso then?

Thanks for all possibles answers.

---

### Post by uggeli on 2004-10-31
Well no-one haven't answer anything atleast not yet, so I was thinking it's probably good idea to say one thing which I forgot in my first post. ISO image was tested and md5sum was ok, and it was burned twice to cd-rw and once to cd-r and everytime result was same as mentioned on first post.

---

### Post by critter42 on 2005-01-03
[QUOTE=uggeli]Well no-one haven't answer anything atleast not yet, so I was thinking it's probably good idea to say one thing which I forgot in my first post. ISO image was tested and md5sum was ok, and it was burned twice to cd-rw and once to cd-r and everytime result was same as mentioned on first post.[/QUOTE]
 I got the same issue on a Dell Latitude CPi D266XT.  I tried expert mode, but still got the same error.  Tried with Knoppix, and it hung trying to find the knoppix cd on /dev/scd0.  I ran it with the noscsi and nodma cheatcodes and it booted fine.

What would be the options in Ubuntu LiveCD/Gnoppix that would allow me to do the same thing?

---

### Post by critter42 on 2005-01-03
[QUOTE=critter42]I got the same issue on a Dell Latitude CPi D266XT.  I tried expert mode, but still got the same error.  Tried with Knoppix, and it hung trying to find the knoppix cd on /dev/scd0.  I ran it with the noscsi and nodma cheatcodes and it booted fine.

What would be the options in Ubuntu LiveCD/Gnoppix that would allow me to do the same thing?[/QUOTE]

D'oh! just figured it out (I didn't realize that the line at the bottom was editable :) )...added the noscsi and nodma codes and it booted fine!

Try that and see if it fixes the issue like it did for me!

---

### Post by nyrblue35 on 2005-02-09
thanks critter42. this worked on my lattitude C600 too as well!   :-P

---

### Post by stereovision on 2005-05-18
- i am having the exact same problem on a IBM TP 600E.  I type 'vmlinuz noscsi nodma' at the boot prompt but im still getting the same end result. Anyone have any idea as to why?

---

