---
title: "boot/hard drive crash"
date: 2007-05-23
forum: General Help
---

### Post by ngdias on 2007-05-23
Today I had a serious crash. The computer was installing those latest updates while i had thunderbird and firefox open. Sudently the windows turn grey and the computer gets somewhat irresponsive. After a bit the firefox window disappeared, then the thunderbird as well and finally the top and bottom desktop bars also disappeared. I had only the update window and the desktop image when i decided to hit the reset button.

After that Ubuntu never loaded again. I also have a windows partition and that was unaffected - its the one i'm using now. I use a software to read ext2 in windows and when i click my two ext3 drives (one is for the Ubuntu OS and the other for /home) it says they are not formatted and asks if i want to format them. Once only I was able to browse the Ubuntu system partition, but after restarting it became unreadable again.

I took some pictures of the boot messages. It says something about 'recovering journal'. In the end it shows the same block of messages and repeats them over and over every few seconds.

 Maybe someone can figure out whats wrong by looking at them. I'm not sure if this was caused by the updates or was a random disk crash caused by other reasons. Any help on *at least* recovering the data is appreciated.

[IMG]http://i192.photobucket.com/albums/z183/ngdias/IMG_1090-2.jpg[/IMG]

[IMG]http://i192.photobucket.com/albums/z183/ngdias/IMG_1091.jpg[/IMG]

[IMG]http://i192.photobucket.com/albums/z183/ngdias/IMG_1092.jpg[/IMG]

[IMG]http://i192.photobucket.com/albums/z183/ngdias/IMG_1095.jpg[/IMG]

[IMG]http://i192.photobucket.com/albums/z183/ngdias/IMG_1100.jpg[/IMG]

[IMG]http://i192.photobucket.com/albums/z183/ngdias/IMG_1101.jpg[/IMG]

[IMG]http://i192.photobucket.com/albums/z183/ngdias/IMG_1095-1.jpg[/IMG]

[IMG]http://i192.photobucket.com/albums/z183/ngdias/IMG_1100-1.jpg[/IMG]

---

### Post by ngdias on 2007-05-23
Can anyone please help?

---

### Post by cyrusrayne on 2007-05-24
If you can, I would strongly recommend getting a hard drive recovery tool such as spinrite.  If you can get one that supports the Linux file system you should be able to recover the partition.

---

### Post by ngdias on 2007-05-24
Spinrite costs money. I tried a few applications under windows - R-Linux for example is free and allows me to list the partition contents and recover files. Other demo applications also list correctly the contents of the partition.

I tried Test Disk 6.6 which also detects everything (it scans superblocks ? and tells me i have 10 in my offending partition) and shows folders and files.

However, I can't find an application that tells me _what's wrong_ with the disk... Or offer an option to repair it. The data was not lost, its all there, I can see it with recovery software. What do I have to do to make available again, in the normal way?

---

### Post by psusi on 2007-05-24
Oh my, it looks like your hard disk is dieing.  Boot from the livecd and try the following:

```

sudo apt-get install smartmontools
sudo smartctl -a /dev/sda

```

---

### Post by ngdias on 2007-05-24
```
ubuntu@ubuntu:~$ sudo smartctl -a /dev/sda
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Short INQUIRY response, skip product id
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
ubuntu@ubuntu:~$ 
```

I previousely ran the windows-based Maxtor drive utilities and all tests available (including SMART) said the disk was OK.

I also did another thing with Test Disk, I asked it to determine the partition table based on reading the whole disk (instead of just reading that info from the usual source). It said my disk was too small and there was definitely a problem with sda4 and suggested formatting it to solve the problem.

Is there a way to get rid of the ext3 data and make it just ext2. Maybe that could help...

---

### Post by psusi on 2007-05-24
Hrm.... weird... looks like your disk doesn't support SMART.  In that case, try sudo dd if=/dev/sda of=/dev/null.  This will take some time as it tries to read the entire disk.  See if it works or errors out.

---

### Post by ngdias on 2007-05-25
After 3 days going about with several boot CDs, several attempts to run fsck and windows-based utilities, I got it working again. What I did:

1. Loaded the Ubuntu live cd
2. At the terminal, typed:

```
sudo fsck.ext3 -fv dev/sda4
```

3. Said yes to a correction to the superblock once and yes to several corrections for empty blocks/sectors/whatever.

I don't know if all the previous tries and twinkering had any impact on this result.

I have to note that previous attempts to run this command resulted in a message "recovering journal' and after a while several I/O errors. The computer had to be shutdown at the power button to be able try and load either Windows or the messed up Ubuntu installed on the HD (hitting reset made the system not 'see' any boot sector in the HD).

Ah - my disc is a 250 Gb, SATA, 1 yr old, Maxtor drive. It *must* support SMART...

---

### Post by psusi on 2007-05-26
Hrm... then you should be able to get smartctl working.  You certainly should run several tests to determine the state of the media as bad sectors usually mean the disk is on its way out.  Wouldn't want to trust any data on that disk.

---

### Post by ngdias on 2007-05-26
Here is the result of the command you sugested, now that my sda4 ir working properly again (I'm wrting this post using my Ubuntu instalation):

```
sudo smartctl -a /dev/sda
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Device: ATA      Maxtor 6L250S0   Version: BACE
Serial number: L59CRL8G            
Device type: disk
Local Time is: Sat May 26 20:14:09 2007 WEST
Device does not support SMART

Error Counter logging not supported

[GLTSD (Global Logging Target Save Disable) set. Enable Save with '-S on']
Device does not support Self Test logging

```

For a few years now, all hard drives come with SMART... as far as I know. I don't know why SMART functions are not being detected in Ubuntu, as they certainly are under Windows.

Mine in particular can be analysed with an application provided by Maxtor. I did all tests available in that application during this crisis (under Windows) and it didn't find any problems - either with SMART reports or sector scans. The extended test for example took quite a while as it scaned the entire drive. Like I said no errors were reported.

I'm guessing the partition got corrupted some how - maybe in the journal or superblock - and that was causing all the trouble.

I'm not that convinced the disk is about to die. Either way, I have updated backups.

---

