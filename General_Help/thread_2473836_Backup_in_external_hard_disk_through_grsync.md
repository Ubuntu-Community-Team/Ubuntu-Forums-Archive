---
title: "Backup in external hard disk through grsync"
date: 2022-04-15
forum: General Help
---

### Post by AnupamMitra on 2022-04-15
Off and on I create backup in external hard disk through Grsync. It was beautiful but today it was not so. While taking back up I got error message. The outcome is given below.
```

**** default - Fri Apr 15 13:35:52 2022

** Launching BEFORE command:

Error launching command!

** Launching RSYNC command:
pkexec rsync -r -t -v --progress --modify-window=1 -b -s /home/anupam/Documents /media/anupam/be907917-d62d-4c12-b3c7-1116436ed54f

sending incremental file list
Documents/PDF Scanner-14_04_2022-10_52_28.pdf
     15,338,308 100%  442.32MB/s    0:00:00 (xfr#1, ir-chk=1068/1085)
rsync: mkstemp "/media/anupam/be907917-d62d-4c12-b3c7-1116436ed54f/Documents/.PDF Scanner-14_04_2022-10_52_28.pdf.iQ9AFz" failed: Read-only file system (30)
Documents/SERVICES CHARGES_CONSOLIDATED_la2021207.pdf
rsync: mkstemp "/media/anupam/be907917-d62d-4c12-b3c7-1116436ed54f/Documents/.SERVICES CHARGES_CONSOLIDATED_la2021207.pdf.Z4IG3x" failed: Read-only file system (30)

        117,497 100%    3.30MB/s    0:00:00 (xfr#2, ir-chk=1066/1085)
Documents/BEFI/expiring_domain_list.csv
             60 100%    1.72kB/s    0:00:00 (xfr#3, ir-chk=1048/1213)
Documents/BOOKS/Bhago+Nahi+Duniya+Ko+Badalo.pdf
     15,773,704 100%  179.08MB/s    0:00:00 (xfr#4, ir-chk=1150/4618)
Documents/FLASH DRIVE/LIST OF STRIKE/LIST OF STRIKES_FINAL.docx
         17,678 100%  203.10kB/s    0:00:00 (xfr#5, ir-chk=1012/4816)
Documents/FLASH DRIVE/LIST OF STRIKE/LIST OF STRIKES_FINAL.pdf
         32,768  27%  376.47kB/s    0:00:00  
        118,777 100%    1.33MB/s    0:00:00 (xfr#6, ir-chk=1011/4816)
rsync: mkstemp "/media/anupam/be907917-d62d-4c12-b3c7-1116436ed54f/Documents/BOOKS/.Bhago+Nahi+Duniya+Ko+Badalo.pdf.ExIV0y" failed: Read-only file system (30)
Documents/LIST OF STRIKE/LIST OF STRIKES_FINAL.docx
rsync: mkstemp "/media/anupam/be907917-d62d-4c12-b3c7-1116436ed54f/Documents/FLASH DRIVE/LIST OF STRIKE/.LIST OF STRIKES_FINAL.docx.i3aFpz" failed: Read-only file system (30)

         17,678 100%  200.74kB/s    0:00:00  
         17,678 100%  200.74kB/s    0:00:00 (xfr#7, ir-chk=1081/5166)
rsync: mkstemp "/media/anupam/be907917-d62d-4c12-b3c7-1116436ed54f/Documents/LIST OF STRIKE/.LIST OF STRIKES_FINAL.pdf.QIjvdx" failed: Read-only file system (30)
Documents/LIST OF STRIKE/LIST OF STRIKES_FINAL.pdf
rsync: mkstemp "/media/anupam/be907917-d62d-4c12-b3c7-1116436ed54f/Documents/P.N.B.E.F.I/.LIST OF STRIKES_FINAL.docx.xdxVvx" failed: Read-only file system (30)

         32,768  27%  372.09kB/s    0:00:00  
rsync: mkstemp "/media/anupam/be907917-d62d-4c12-b3c7-1116436ed54f/Documents/P.N.B.E.F.I/6TH CONFERENCE/.LIST OF STRIKES_FINAL.pdf.ASBCvz" failed: Read-only file system (30)
skipping non-regular file "Documents/P.N.B.E.F.I/Link to DRAFT LETTER.docx"
        118,777 100%    1.32MB/s    0:00:00 (xfr#8, ir-chk=1080/5166)
Documents/P.N.B.E.F.I/LIST OF STRIKES_FINAL.docx
         17,678 100%  198.43kB/s    0:00:00 (xfr#9, ir-chk=1111/5286)
Documents/P.N.B.E.F.I/LIST OF STRIKES_FINAL.pdf
        118,777 100%    1.29MB/s    0:00:00 (xfr#10, ir-chk=1110/5286)
Documents/P.N.B.E.F.I/6TH CONFERENCE/LIST OF STRIKES_FINAL.pdf

         32,768  27%  359.55kB/s    0:00:00  
        118,777 100%    1.27MB/s    0:00:00 (xfr#11, ir-chk=1089/5382)
*** Skipping any contents from this failed directory ***
Documents/P.N.B.E.F.I/CIRCULAR/CIRCULAR 2022/Cir. 9.docx
rsync: recv_generator: mkdir "/media/anupam/be907917-d62d-4c12-b3c7-1116436ed54f/Documents/P.N.B.S.U/Domestic Enquiry/RATUL_ANKITA_JAYANTA_BARDHAMAN" failed: Read-only file system (30)

         32,768  66%  340.43kB/s    0:00:00  
         49,236 100%  511.51kB/s    0:00:00 (xfr#12, ir-chk=1008/6311)
rsync: recv_generator: mkdir "/media/anupam/be907917-d62d-4c12-b3c7-1116436ed54f/Documents/P.N.B.S.U/Domestic Enquiry/SOURAV PAUL" failed: Read-only file system (30)
Documents/P.N.B.E.F.I/CIRCULAR/CIRCULAR 2022/Cir. 9.pdf
*** Skipping any contents from this failed directory ***

         32,768  28%  340.43kB/s    0:00:00  
        113,594 100%    1.14MB/s    0:00:00 (xfr#13, ir-chk=1007/6311)
rsync: mkstemp "/media/anupam/be907917-d62d-4c12-b3c7-1116436ed54f/Documents/P.N.B.E.F.I/TU CLASS_SERVICE RULES/.LIST OF STRIKES_FINAL.pdf.u0xCAB" failed: Read-only file system (30)
Documents/P.N.B.E.F.I/TU CLASS_SERVICE RULES/LIST OF STRIKES_FINAL.docx

         17,678 100%  174.38kB/s    0:00:00  
         17,678 100%  174.38kB/s    0:00:00 (xfr#14, ir-chk=1022/6545)
rsync: mkstemp "/media/anupam/be907917-d62d-4c12-b3c7-1116436ed54f/Documents/P.N.B.S.U/SERVICE CONDITIONS OF PNB WORKMEN/NEW EDITION/.PREFACE_FINAL.docx.uyYllB" failed: Read-only file system (30)
Documents/P.N.B.E.F.I/TU CLASS_SERVICE RULES/LIST OF STRIKES_FINAL.pdf
        118,777 100%    1.13MB/s    0:00:00 (xfr#15, ir-chk=1021/6545)
Documents/P.N.B.S.U/24th Conference/
Documents/P.N.B.S.U/Domestic Enquiry/RATUL_ANKITA_JAYANTA_BARDHAMAN/
Documents/P.N.B.S.U/Domestic Enquiry/SOURAV PAUL/
rsync: mkstemp "/media/anupam/be907917-d62d-4c12-b3c7-1116436ed54f/Documents/SELF/BIDYUT/.Delivery Challan, NBA.doc.uibG0y" failed: Read-only file system (30)
Documents/P.N.B.S.U/SERVICE CONDITIONS OF PNB WORKMEN/NEW EDITION/PREFACE_FINAL.docx
rsync: mkstemp "/media/anupam/be907917-d62d-4c12-b3c7-1116436ed54f/Documents/SELF/BIDYUT/.Delivery Challan_2_ NBA.doc.7cCJFx" failed: Read-only file system (30)

         32,768  82%  299.07kB/s    0:00:00  
         39,813 100%  363.36kB/s    0:00:00 (xfr#16, ir-chk=1008/7584)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1207) [sender=3.1.3]
Documents/P.N.B.S.U/SERVICE CONDITIONS OF PNB WORKMEN/SERVICE CONDITIONS_3RD EDITION/
Documents/SELF/BIDYUT/Delivery Challan, NBA.doc
         43,008 100%  355.93kB/s    0:00:00 (xfr#17, to-chk=471/9462)
Documents/SELF/BIDYUT/Delivery Challan_2_ NBA.doc
         30,720 100%  254.24kB/s    0:00:00 (xfr#18, to-chk=470/9462)
Documents/SELF/GENERAL STRIKE/LIST OF STRIKES_FINAL.docx
         17,678 100%  146.30kB/s    0:00:00 (xfr#19, to-chk=412/9462)
Documents/SELF/GENERAL STRIKE/LIST OF STRIKES_FINAL.pdf
        118,777 100%  982.99kB/s    0:00:00 (xfr#20, to-chk=411/9462)

sent 32,598,257 bytes  received 5,688 bytes  65,207,890.00 bytes/sec
total size is 9,460,522,930  speedup is 290.16
Rsync process exit status: 23

```
I never experienced such difficulties. I do not know how to resolve it. Need help.

---

### Post by Holger_Gehrke on 2022-04-15
The important part of all this output is
> 
Read-only file system

If a file system was not unmounted cleanly or if the OS encountered errors while reading from or writing to a file system it will set this file system to be read only. To get the file system back into a usable state you need to unmount it and do a file system check. From the command line the commands to do this are 'udiskctl unmount' or 'umount' for unmounting and 'fsck' for checking. You can also do it from the GUI using gparted.

Holger

---

### Post by SeijiSensei on 2022-04-15
You can also force a disk check at boot this way:
```
sudo touch /forcefsck
```
This will force a check of the disk on which / is mounted.

You can't check a disk while it is mounted. You can boot from an Ubuntu installation medium and run something like "sudo fsck /dev/sda1" that way, but it's generally easier to create the forcefsck file and reboot.

---

### Post by TheFu on 2022-04-15
> **SeijiSensei said:**
> You can also force a disk check at boot this way:
```
sudo touch /forcefsck
```
This will force a check of the disk on which / is mounted.

You can't check a disk while it is mounted. You can boot from an Ubuntu installation medium and run something like "sudo fsck /dev/sda1" that way, but it's generally easier to create the forcefsck file and reboot.


SeijiSensei, the /forcefsck method was dropped when systemd took over in 2016 and I know it wasn't working in 2020.  Did they finally add it back? It was so useful.   The last comment here: [https://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/](https://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/) says how to accomplish this on systemd controlled systems. It is ugly in comparison, sadly requires modifying the grub.cfg file and running update-grub.  Then to stop it, the reverse needs to be done.  
Or grub boot options can be ended before the OS is booted by pressing 'e' when the kernel we want to boot is selected in the grub menu.  
Or going into the grub advanced options, then choosing a "recovery" kernel. When the menu for options is displayed, choose Check All File systems.
The problem with all of these methods is that most require console access, which is hard for hobbyist providing remote support.  Companies that don't always include an IPMI connection ($300+) into a network console switch for their servers are also screwed.

Also, I suspect the OP needs to run fsck on the target file system ... which seemed mounted under /media/....  That just requires NOT having the file system mounted which isn't usually too hard for non-/ partitions.

Or did I misread everything?

If this were not a read-only file system and the target was silently corrupt, then pushing a mirror copy like rsync does would very likely result in corrupted 'backups', this is 1 reason why we need to be doing **automatic**, daily, **versioned**, backups.  For a home system, daily may be too much and weekly would be fine. YMMV.  OTOH, it isn't like the daily versioned backups will be very large - or any smaller than the weekly versioned backups.  Versioned backups only require the changed data, so it really is a fairly small amount. For example, I do daily, versioned, backups for about 20 systems - excluding video media files.  The backups for all of those systems - at least 90 days, but many have 120-180 days, all fit on a single 1.5TB HDD.  A few times, I've needed to restore some data from almost 40 days prior when a DBMS was corrupted. That DBMS was only used for monthly financial reporting, which explains why nobody notice the problem earlier.

Anyway, rsync/grsync to about 80% of what we need in a backup tool.  But that extra 20% really isn't very hard to achieve with tools specifically designed for backups, not just mirroring.

---

### Post by AnupamMitra on 2022-04-16
[SIZE=2][FONT=Tahoma]I have never been in such a situation. Suddenly I observed that the main hard disk of my PC, which has a [/FONT][FONT=Tahoma]capacity [/FONT][FONT=Tahoma]of 1 TB, has only 61 GB of free space left in it, which is unbelievable. Since then [/FONT][FONT=Tahoma]I [/FONT][FONT=Tahoma]faced trouble while turning on the computer, [/FONT][FONT=Tahoma]booting hanged midway. Somehow once it could be started. [/FONT][FONT=Tahoma]I [/FONT][FONT=Tahoma]observed [/FONT][FONT=Tahoma]through [/FONT][FONT=Tahoma]Gparted [/FONT][FONT=Tahoma]that the color has changed to red. My knowledge is very limited. [/FONT][FONT=Tahoma]I became puzzled. I copied all my files in several USB drive and ultimately I[/FONT][FONT=Tahoma] was forced to reinstall Ubuntu. [/FONT]
[FONT=Tahoma]Thanks to [/FONT][FONT=Tahoma]all of you viz. [/FONT][FONT=Tahoma]**Holger_Gehrke**[/FONT]**[COLOR=#000000][FONT=Tahoma], [/FONT][/COLOR]****[COLOR=#000000][FONT=Tahoma]SeijiSensei, TheFu, [/FONT][/COLOR]**[COLOR=#000000][FONT=Tahoma][/FONT][/COLOR][COLOR=#000000][FONT=Tahoma]for your cooperation and [/FONT][/COLOR][FONT=Tahoma]for taking pains for me [/FONT][FONT=Tahoma]to sort [/FONT][FONT=Tahoma]out [/FONT][FONT=Tahoma]the[/FONT][FONT=Tahoma] problem. I hope, no one [/FONT][FONT=Tahoma]would [/FONT][FONT=Tahoma]misunderstand me.[/FONT][/SIZE]

---

### Post by TheFu on 2022-04-16
I have some computers that have only 16G-40G total storage available.  They work fine.  Limited space when more than 1G is available is seldom an issue. 
There are exceptions, but since you wiped the system, we'll never know the root cause.  It could easily be a failing HDD, so this issue will return soon.  
OTOH, if it gets a working system back, that's always a 'win' to me.  After spending more than 30 minutes on an issue like this, I'd probably wipe it, do a fresh install, and restore from my backups too.

Anyway, if this is solved, please help the community by clicking on the Thread Tools button and selecting "SOLVED".

---

### Post by AnupamMitra on 2022-04-18
> **TheFu said:**
> I have some computers that have only 16G-40G total storage available.  They work fine.  Limited space when more than 1G is available is seldom an issue. 
There are exceptions, but since you wiped the system, we'll never know the root cause.  It could easily be a failing HDD, so this issue will return soon.  
OTOH, if it gets a working system back, that's always a 'win' to me.  After spending more than 30 minutes on an issue like this, I'd probably wipe it, do a fresh install, and restore from my backups too.

Anyway, if this is solved, please help the community by clicking on the Thread Tools button and selecting "SOLVED".

One day ago you have predicted that "..... so this issue will return soon". I couldn't imagine that it will return so early. 

However, I mention the gist of the problem occurred since yesterday night. When I starts the computer I'm getting a message, the image of which I enclosed herewith. 

Furthermore, in my PC I'm having two HDD - one for UBUNTU and another is for Windows 10. I also use Ext2FSD software on Windows platform. Through this I'm able to enter in UBUNTU HDD. Today when UBUNTU is not booting properly and not opened, but through Ext2FSD I could enter to UBUNTU HDD and locate all my files/folders. 

I'm unable to understand what to do. Would you please throw some light and suggest ?

---

### Post by TheFu on 2022-04-18
The solution for a failing HDD is to replace the HDD.

---

### Post by AnupamMitra on 2022-04-20
> **TheFu said:**
> The solution for a failing HDD is to replace the HDD.

Do you really feel that HDD is the main cause for all these problems? Don't you feel that Ext2FSD has a role on this issue? Okay, then I have to arrange for a new HDD.

---

### Post by TheFu on 2022-04-20
> **AnupamMitra said:**
> Do you really feel that HDD is the main cause for all these problems? Don't you feel that Ext2FSD has a role on this issue? Okay, then I have to arrange for a new HDD.

I would check the drive S.M.A.R.T. data and hopefully get more information.  **smartctl** is the tool for that. I don't recall the name of the package, but it isn't the same.  There are lots of threads here about using smartctl.  It has 2 steps.

---

### Post by him610 on 2022-04-21
> smartctl is the tool for that
```

sudo apt install smartmontools

```

---

### Post by AnupamMitra on 2022-05-03
> **him610 said:**
> ```

sudo apt install smartmontools

```

Thanks for your cooperation. However, as advised, I have installed smartctl. But I can't locate or find it. How to use it? Would you please guide?

---

