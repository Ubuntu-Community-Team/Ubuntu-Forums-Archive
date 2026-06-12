---
title: "How to access/backup a GPT HDD on *buntu?"
date: 2014-07-04
forum: General Help
---

### Post by amjjawad on 2014-07-04
Hi there,

Not sure if I chose the best 'Title' that describe what I need here.

On my left, there is a Dell Inspiron 15R (Core i7 and 4GB RAM) which has Windows 8 and the secure boot thing of course. HDD is using [GPT]("http://en.wikipedia.org/wiki/GUID_Partition_Table") NOT [MBR]("http://en.wikipedia.org/wiki/Master_boot_record").

The HDD is failing and my neighbour gave me the laptop to rescue the data and was [interested to try GNU/Linux]("https://wiki.ubuntu.com/StartUbuntu") after I explained to them some advantages.

I have a Desktop PC that I use to backup files from Laptops.
I take the HDD out, connect it to my PC which has both IDE and SATA and I do the backup usually by using Lubuntu 14.04 LTS LiveUSB.

I have tried several times to access the files but it does not allow me to get in. It gives a long error message that I didn't actually save. What I understood from that message is as long as the HDD is using GPT instead of MBR, I can't access/mount that the normal way.

Any idea how can I access that to save the data? they really need that. I'm not sure if I can do anything to the hard drive like install GNU/Linux or not[1]? but what I need now is to access the data using *buntu LiveUSB (Lubuntu 14.04 LTS)?

The machine I'm using to backup the files is not the same laptop but different machine. Either way, I can't access/mount the partition of the dying HDD.

Thank you!



[1] *I have managed to [breathe new life into an old Dell machine]("https://wiki.ubuntu.com/StartUbuntu/Activities/ConvertCompetition#Competition") (Centrino) by using Xubuntu 14.04 LTS and that machine had a bad HDD. What I did is I excluded the first 20GB of the HDD and it is working now like a Charm.*

---

### Post by sudodus on 2014-07-04
Do you want to backup the whole (as much as possible) of the failing HDD? In that case, use ***ddrescue***. After installation, read the info page

```
info ddrescue
```

which is very good (better than the man page)

If you want to save only some files, it should be possible to mount a partition with the mount command

```
sudo mount /dev/sdxy /mnt
```

and save some files.

But if the drive is failing, it may get worse rapidly, so I recommend ddrescue at once. Of course, you need at least one spare drive of at least the same size as the failing drive. And you should write the log file to a third drive, for example the one you are booting from.

---

### Post by amjjawad on 2014-07-04
Hello my friend and thanks for your reply :)

In fact, I just need to save 'User' folder from Windows 8 as they don't care about the rest. At least, this is what the father told me. The laptop for my neighbour's son and he has school projects, etc. They do need that badly. I know it is Summer now but they need that :)

Thanks!

P.S.
I will try what you suggested and I do hope it will work :)
Will report back ;)

---

### Post by sudodus on 2014-07-04
If you can't mount it, maybe it was not unmounted correctly or maybe Windows was hibernated or semi-hibernated, not shut down completely. Then it is hard for Linux to mount and read. You may need to boot into Windows and shut it down completely.

Windows 8 hibernates by default, a method to make it boot faster. It can be hard to disable it completely, but I managed to do it this way (more than a year ago, before 8.1, I hope the method is still valid).

[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

---

### Post by amjjawad on 2014-07-04
> **sudodus said:**
> If you can't mount it, maybe it was not unmounted correctly or maybe Windows was hibernated or semi-hibernated, not shut down completely. Then it is hard for Linux to mount and read. You may need to boot into Windows and shut it down completely.

Windows 8 hibernates by default, a method to make it boot faster. It can be hard to disable it completely, but I managed to do it this way (more than a year ago, before 8.1, I hope the method is still valid).

[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

Here is the catch and I suspect this is the main issue I'm having right now. I can NOT access Windows 8. When I turn the machine ON, it gives me a dark grey screen and nothing happens after that.

I ran a diagnose test and everything is fine except the Hard Drive. Even SMART status is 'fail'.

---

### Post by sudodus on 2014-07-04
Do you think there is a logical error or a hardware error (bad sectors) on the drive?

If it is very important to save the data, I suggest ddrescue, and to try with ***Testdisk*** on the cloned copy, and if that does not work, try with ***PhotoRec***, to get at least the most important files (recognized by content and type).

Messing with Testdisk on the original drive is risky. Using these programs can be very time-consuming.

---

### Post by amjjawad on 2014-07-04
> **sudodus said:**
> Do you think there is a logical error or a hardware error (bad sectors) on the drive?

If it is very important to save the data, I suggest ddrescue, and to try with ***Testdisk*** on the cloned copy, and if that does not work, try with ***PhotoRec***, to get at least the most important files (recognized by content and type).

Messing with Testdisk on the original drive is risky. Using these programs can be very time-consuming.

It is very very weird/strange that at the very same time, I got 3 different machines and all have problems with the hard drive. I had two external HDDs too that another neighbours asked me to save/rescue so basically, I do have now 5 HDDs that need to be saved ... WOW!

I managed to fix 2 out of 5.

The one with this issue I explained on this thread is giving me: **This disk is likely to fail soon** message when I use Disk on Lubuntu (Menu > Accessories > Disk).

On the diagnose test on the Dell Laptop, it is also saying SMART failed.

I don't know yet if it is a hardware or software issue but from the fact we currently have, it seems hardware. Odd enough, the machine is NEW :/
I don't know what happened that suddenly I have two new different laptops and both with dying/dead HDD?!

The internal HDD of the laptop is Toshiba. Perhaps those guys need to put more efforts into this? why Dell and HP and the rest are using Toshiba HDDs instead of WD? I guess they're trying to reduce the cost or some kind of deal? no clue.

I will try my best firstly on the laptop itself. 

If that didn't work, I will disconnect the HDD and connect it to my Desktop PC.

If that didn't work either? well, not sure what else I can try?!

As for the rescue method is time-consuming? YES, tell me about it ... I do know exactly how painful that is ... I've been through this for months now with many failing HDDs.

---

### Post by stalkingwolf on 2014-07-04
have you tried booting the laptop directly from a live disk or usb drive?  I have not used win 8 so im not sure what suggestions to give. on older wim systems i have succesfully used the HDD regenerator in the hirens tools.  I have rregened the drive then booted it and copied the files to an external drive.

---

### Post by amjjawad on 2014-07-04
Hi,

This is what I have:


[ATTACH=CONFIG]254455[/ATTACH]

[ATTACH=CONFIG]254456[/ATTACH]

[ATTACH=CONFIG]254454[/ATTACH]

---

### Post by amjjawad on 2014-07-04
> **stalkingwolf said:**
> have you tried booting the laptop directly from a live disk or usb drive?  I have not used win 8 so im not sure what suggestions to give. on older wim systems i have succesfully used the HDD regenerator in the hirens tools.  I have rregened the drive then booted it and copied the files to an external drive.

Hi,

Indeed I have :)

GPT is not like MBR. GPT = GUID Partition Table = [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

With other machines and HDDs, I managed to access/mount the HDDs. The only case when I couldn't was when the HDD itself is dead and can't even be detected.

In this case with this Dell laptop, the machine still can 'read' or 'detect' the HDD.

It seems now because Windows wasn't shut down correctly (Hibernate), I can't access the HDD.

---

### Post by sudodus on 2014-07-04
The screenshots suggest that you mount the partitions read-only. Try that and maybe you can read (copy) the important files :-)

```
sudo mount -r /dev/sdxy /mnt
```

       From man mount:

```
-r, --read-only
              Mount the filesystem read-only. A synonym is -o ro.

              Note  that,  depending on the filesystem type, state and kernel behavior, the system may
              still write to the device. For example, Ext3 or ext4 will  replay  its  journal  if  the
              filesystem is dirty. To prevent this kind of write access, you may want to mount ext3 or
              ext4 filesystem with "ro,noload" mount options or set  the  block  device  to  read-only
              mode, see command blockdev(8).
```

or maybe you should try (It does not tell if it is relevant for NTFS)

```
sudo mount -o  ro,noload /dev/sdxy /mnt
```

---

### Post by amjjawad on 2014-07-12
> **sudodus said:**
> The screenshots suggest that you mount the partitions read-only. Try that and maybe you can read (copy) the important files :-)

```
sudo mount -r /dev/sdxy /mnt
```

       From man mount:

```
-r, --read-only
              Mount the filesystem read-only. A synonym is -o ro.

              Note  that,  depending on the filesystem type, state and kernel behavior, the system may
              still write to the device. For example, Ext3 or ext4 will  replay  its  journal  if  the
              filesystem is dirty. To prevent this kind of write access, you may want to mount ext3 or
              ext4 filesystem with "ro,noload" mount options or set  the  block  device  to  read-only
              mode, see command blockdev(8).
```




Hi,

I managed to mount it but when I'm trying to copy the content of 'Users' folder from the internal HDD to an external one, I'm getting many errors using Lubuntu 14.04 LiveUSB.

```
Error splicing file: input/output error
```

It says copying but during that, I'm getting these errors ...

---

### Post by sudodus on 2014-07-12
Something is wrong. I have not encountered the splicing file error before, and I don't know about it. I don't think it is due to the GPT partition table, rather that there is some error in the file system.

---

### Post by amjjawad on 2014-07-12
> **sudodus said:**
> Something is wrong. I have not encountered the splicing file error before, and I don't know about it. I don't think it is due to the GPT partition table, rather that there is some error in the file system.

Neither do I :(
I don't know what is going on ... it is copying the files but so many errors in the process and yes, all of them are the same:

```
filename.file-type : Error splicing file: input/output error
```

---

### Post by oldfred on 2014-07-12
I have been using gpt since version 10.10 and have had no issues. I do not think any issues you have are because of gpt partitioning but Windows hibernation and/or corruption. And from Linux it is difficult to mount a hibernated Windows system and you cannot run chkdsk to repair Windows file stuctures from Linux. 

Best to have a Windows repair flash drive.
       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

With gpt you should not dd copy a partition as partition table, backup partition table & partitions have internal data that must be in sync. It may be possible to fix gpt internal data with gdisk but better to dd image an entire drive if that is what you need to do.

---

