---
title: "Tired of Reinstalling Ubuntu - How Backup the whole system"
date: 2014-12-28
forum: General Help
---

### Post by DiogoSaraiva on 2014-12-28
Hi,
Hi have a new computer since about 2 weeks ago, and already reinstaled Ubuntu more than 3 times, because I install something wrong or bad, or edit wrong configuration files, etc... you maybe know what I'm telling.... So I'm tired of reinstalling....
So how can I backup my entire system?

I have a Ubuntu 14.04.1 64 bits with LVM.... and I already tried the program Back in Time... but give me errors... setting permissions I guesss, even if i open "Back in time (root)" (I installed the gnome version, but I have the default desktop: unity i guess...)

I tried learn how do LVM snapshots, I read various articles about this but I not understand: 

Here:
[http://www.tecmint.com/take-snapshot-of-logical-volume-and-restore-in-lvm/](http://www.tecmint.com/take-snapshot-of-logical-volume-and-restore-in-lvm/)
in step 1, when i issue the command "sudo vgs" shows me that i have only one named ubuntu-vg and no free space 


here:
[http://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html](http://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html)
is the same, it say "we now want to use the extra space in the 'ops' volume group" but where is my extra space???

Thanks in Advance...

---

### Post by agillator on 2014-12-28
I have never tried it before but I suppose most any backup program would work. Personally I use rsnapshot. Whether that would give you the same LVM errors or not I don't know. However, my guess is that backing up 'the whole system' may be an exercise in futility. Grub, for example, would not be able to boot unless a restored system were EXACTLY the same, same partitioning, same file locations, same everything. I suspect many parts of the system would run into the same problem. Any miniscule difference would cause a failure. In addition, I would be surprised if attemtping to restore from a backup would not take longer than simply reinstalling. Backing up configuration files makes some sense, if they are good in the first place. I have had the same frustrations with installation but found the best solution is to keep notes and learn from my mistakes so I don't make them again, learning to make a clean installation.

---

### Post by Mark Phelps on 2014-12-28
I regularly make full system backups using Clonezilla -- and the total time to do the backup, plus the time taken to verify the integrity of the backup, is under 5 minutes!  You'd be hard pressed to install or reinstall Ubuntu, together with apps, in less time than that.

---

### Post by sammiev on 2014-12-28
+1 to Clonezilla, I use it often.

---

### Post by DiogoSaraiva on 2014-12-29
+1 to Clonezilla, I tried it... I loved it...
I see this tutorial: [https://www.youtube.com/watch?v=gJKv6NSKMAU](https://www.youtube.com/watch?v=gJKv6NSKMAU) 
but unfortunately I was not able to boot the live USB Flash drive... gives me a error, like that usb flash drive isn't bootable I guess, or incorrect filesystem, don't remember...
I had to burn into a DVD RW (in that moment I had only 2 rewritable DVDs, no normal DVDs...)
[B]Other question:
[/B]Can I burn images like Gparted live or Clonezilla in CDs... I use Infrarecorder but If you know other software particularly that works on Ubuntu or Macintosh, tell me please... I say this, because I look into DVD and neither 1 cm / 0,40 inches from the beginning /center part of the DVD was burned... If you understand me....

Thanks in advance

---

### Post by sudodus on 2014-12-29
I have no problems booting ***Clonezilla*** live from either of CD/DVD/USB (pendrive). I install it to CD/DVD with ***k3b*** and to USB with ***mkusb***.

If you want help to boot from USB, please specify your computer (or motherboard if home-built)

- Brand name and model

See more details at [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

-o-

It is possible but much more difficult to make a multiboot USB pendrive. On the other hand, you can store the iso file in a hard disk drive, and ***use the USB pendrive as a temporary drive***. You copy/clone/flash an iso file to a pendrive in 30 seconds to 4 minutes depending on the size of the iso file and the write speed of the pendrive.

I think it is even harder (I have never done it) to use a CD/DVD as a multiboot device unless you get an iso file that is already an image of a multiboot device.

---

### Post by DiogoSaraiva on 2014-12-29
My PC is a Mini PC: Giada A51B-BP001 with 4GB Ram and 120GB SSD

Thanks

---

### Post by sudodus on 2014-12-29
That computer is (rather) new and has no built-in CD/DVD according to [http://www.giadapc.com/products/minipc/slim%20series/A51B.html](http://www.giadapc.com/products/minipc/slim%20series/A51B.html)

- Did you boot via an external DVD drive connected via USB? 
- Did you try all USB ports (not only the USB 3 port)?

Maybe you made a bad USB boot drive.

- Did you try the USB pendrive in another computer (only try 'live', do not install)?
- What tool did you use?
- Which version of Ubuntu did you install?

I think it can boot from USB if you set the BIOS/UEFI correctly or via a  hotkey (maybe you can find out which hotkey to use from a manual for  the computer). The computer is advertized to run linux, and I think the  intention is to install it via USB.

---

### Post by DiogoSaraiva on 2014-12-30
- Did you boot via an external DVD drive connected via USB? yes connected on usb 2.0
- Did you try all USB ports (not only the USB 3 port)? no i tried only the USB 3.0 port (more accessible) 
I used Tuxboot on Ubuntu...

ahh, and I reeintalled again because I was not able to resize the main partition to make another one called BACKUPS I guess because it is LVM...

Thank you very much for your help and see you soon...
and happy new year

My version of ubuntu:  Ubuntu Desktop 14.04.1 LTS 64 bits

---

### Post by sudodus on 2014-12-30
I don't know about Tuxboot, but the alternatives in [https://help.ubuntu.com/community/In...n/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick") should wor&#7729;, for example ***mkusb*** to make a good USB boot drive with either of

- Ubuntu Desktop 14.04.1 LTS 64 bits
- Clonezilla (I prefer the current stable version).

The gparted iso file should work too, but I have not tried it.

-o-

If you want a multiboot USB pendrive you can try the alternatives found searching the internet for ***linux multiboot***, for example

[YUMI: http://www.pendrivelinux.com/yumi-multiboot-usb-creator/]("http://www.pendrivelinux.com/yumi-multiboot-usb-creator/")
[Multisystem: http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/]("http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/")

---

### Post by DiogoSaraiva on 2014-12-30
ok, I will try,
thank you very much

---

### Post by verachen on 2015-01-13
Yes,you can backup the entire system if your computer has something wrong, you can boot it from the system backup image. You can use the windows built-in backup tool, or search in Google to find some useful backup software to do this task. In some review websites, such as: [http://pc-backup-review.toptenreviews.com/](http://pc-backup-review.toptenreviews.com/) there are some top software, maybe can help you. Once i used aomei backupper for [system backup]("http://www.backup-utility.com/features/system-backup.html"), which is in the top 10. You can use it to backup files, folders, partitions, disk and system. If you need to restore your computer, the backup image is very important. Besides, you also can use it to create a bootable media to boot computer system.Hope you like it and help you.

---

### Post by Z80A on 2015-01-13
I spotted this one in another discussion (in some signature line); [B]Redo Backup and Recovery.
[/B][INDENT][URL="http://redobackup.org/"]
http://redobackup.org/[/URL]
[/INDENT]

I haven't tried it out yet, but intend to do so. Sounds good:[INDENT][I][B]
Easy Backup, Recovery & Bare Metal Restore[/B]

**Redo Backup and Recovery** is so simple that anyone can use it. It is the easiest, most complete disaster recovery solution available. It allows bare-metal restore. **Bare metal restore** is not only the best solution for hardware failure, it is also the ultimate antivirus: Even if your hard drive melts or gets completely erased by a virus, you can have a completely-functional system back up and running in as little as 10 minutes.

All your documents and settings will be restored to the exact same state they were in when the last snapshot was taken. **Redo Backup and Recovery** is a live CD, so it does not matter if you use Windows or Linux. You can use the same tool to backup and restore every machine. And because it is open source released under the GPL, it is **completely free** for personal and commercial use.[/I]
[/INDENT]

---

### Post by Augusta51 on 2015-01-17
If you want to backup your whole System then try [CloudBacko Pro]("http://www.cloudbacko.com/"). Now I am using this software to backup my databases, server, virual machine etc. It is easy and reliable to use. Once you try this software.

---

### Post by trag on 2015-01-20
Create restore points and clone your drive using Timeshift

---

