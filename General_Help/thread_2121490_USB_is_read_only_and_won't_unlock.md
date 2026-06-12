---
title: "USB is read only and won't unlock"
date: 2013-03-02
forum: General Help
---

### Post by ShadowGuardian on 2013-03-02
i have a kingston datatravaler 32gb.  I got it a week ago so its brand new.

 i partitioned 10.5gb to ext4 with 3.5gb swap.  then installed ubuntu 12.10. it worked great. partitioned the other "half" the same way and tried to install fedora (which i havent used much) it said install failed.  after that it said the half i partitioned for fedora was unallocated when using minitool partitioner.  and the usb has gone read only.  it mounted in ubuntu at first but now it wont mount (something about bad superblock).

 i have tried: gparted, testdisk, disk utility, partitioners in windows 7. 

 I just want to wipe it clean and take back to default so i can try again (install fedora first this time, then ubuntu)

sorry for the choppy sentences but i really want some help.  I am new to the forum as well.

p.s.  i hate windows

---

### Post by zero2xiii on 2013-03-02
Hay,

You can try writing zero to the drive and try to repartition it.

```
sudo dd if=/dev/zero of=/dev*/usb_drive *bs=512
```

See "man dd" for details on the above syntax.
"of=" is the path to the device eg
/dev/sdb
NOT
/dev/sdb5

Good luck

---

### Post by ShadowGuardian on 2013-03-02
I believe i have already tried dd but i will try again.  I dont see a r/o switch on the casing either just so you know.  Its like the ubuntu that i installed on it has "locked" itself up.  It wont partition at all.  everything just says: You do not have permission.  Also, if i try to mount it, it says:

Error mounting: mount: block device /dev/sdb1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

The drive could be defective but i doubt it.

Is there any programs that just overide permissions?

Thanks for the help so far.

---

### Post by ShadowGuardian on 2013-03-02
Just tried dd, then repartition with disk utility. no go.   it says:

Error modifying partition: helper exited with exit code 1: In part_change_partition: device_file=/dev/sdb, start=1048576, new_start=1048576, new_size=11262754816, type=0x0c
Entering MS-DOS parser (offset=0, size=31347965952)
MSDOS_MAGIC found
looking at part 0 (offset 1048576, size 11262754816, type 0x83)
new part entry
looking at part 1 (offset 11264850944, size 20081280000, type 0x0f)
Entering MS-DOS extended parser (offset=11264850944, size=20081280000)
readfrom = 11264850944
No MSDOS_MAGIC found
Exiting MS-DOS extended parser
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 0
Warning: Unable to open /dev/sdb read-write (Read-only file system).  /dev/sdb has been opened read-only.
got it
Warning: Unable to open /dev/sdb read-write (Read-only file system).  /dev/sdb has been opened read-only.
Error: Invalid partition table on /dev/sdb -- wrong signature d569.
ped_disk_new() failed

thanks anyway

---

### Post by xp15 on 2013-03-03
I remember something similar happend to me, but I don't remember well what I've done.
If you are getting into nautilus with sudo-in the terminal:

 sudo nautilus

Are you able to do something with rightclick (Through the sudo nautilus' window) on the device > Properties? Can you free it from there?

---

### Post by carl4926 on 2013-03-03
I had similar once
I had to trash it, but it was only 8GB

Will Imagewriter write an image to it?

---

### Post by ShadowGuardian on 2013-03-03
universal installer failed to write ubuntu 12.10 to it, but unetbootin ran and appears to have "worked".  so i will give it a try, although my partitioner shows nothing has changed. i have been bouncing back between windows 7 and ubuntu to try and fix this thing.

---

### Post by sudodus on 2013-03-03
Maybe the drive is physically bad. You can check that with ***badblocks***. Learn how to run it in ```
man badblocks
```.

For example if your USB pendrive is recognized as /dev/sdx

```
sudo badblocks -n /dev/sdx
```

---

### Post by ShadowGuardian on 2013-03-03
tried badblocks, this is what it says:

shadowaviator@shadow-Aspire-7740:~$ sudo badblocks -n /dev/sdb
[sudo] password for shadowaviator: 
badblocks: Read-only file system while trying to open /dev/sdb
shadowaviator@shadow-Aspire-7740:~$

---

### Post by xp15 on 2013-03-03
I found a similaer thread, it may help: [http://ubuntuforums.org/showthread.php?t=859878](http://ubuntuforums.org/showthread.php?t=859878)
try the Unistalling U3, maybe you have it? or something similar?

---

### Post by dcstar on 2013-03-03
> **ShadowGuardian said:**
> i have a kingston datatravaler 32gb.  I got it a week ago so its brand new.
.........
 I just want to wipe it clean and take back to default so i can try again (install fedora first this time, then ubuntu)


Use **gparted** to write a new Partition Table.

---

### Post by ShadowGuardian on 2013-03-03
Gparted doesnt recognize the usb.  if i sudo it i can see Gparted trying, but the read-only error comes up.

I havent used gparted much, so you'll have to explain if i am not understanding something.

Thanks for the help, but i need to get to sleep.  SO WE WILL CONTINUE THIS ADVENTURE TOMORROW!

---

### Post by dcstar on 2013-03-03
> **ShadowGuardian said:**
> Gparted doesnt recognize the usb.  if i sudo it i can see Gparted trying, but the read-only error comes up.

I havent used gparted much, so you'll have to explain if i am not understanding something.


Device-Create Partition Table.

If you cannot see the device in gparted then you have a hardware problem.

Open a terminal, plug the device in and run the command "**dmesg**" after a few seconds and post the output.

---

### Post by scruffyeagle on 2013-03-03
I'm running Ubuntu v10.04, and have a similar problem - but, it's more than the flash drive.

I encountered it yesterday, upon opening a True Crypt FAT partition on a 8GB flash drive. I've used that partition many times; always, Read/Write. It opened w/o problem, except it was Read Only. No matter what I did, it wouldn't change permissions to allow writing to the drive. I figured it was probably some interaction between True Crypt & Ubuntu, but I'd get around to trying to figure it out later because it wasn't urgent.

But, today I did some major repartitioning on my 1TB external HD, and the problem is hitting there. I deleted 2 NTFS partitions (~5GB, ~400GB) and used the space to create (2) ~202GB NTFS partitions. One of those partitions is functioning properly - but, the other isn't. The OS allowed me to copy ~8GB of files to it. I then did a reboot on general principles, and when the OS was up again, the 1st partition was still Read/Write, but the 2nd partition was Read Only.  I've tried everything I can think of, but the OS won't allow the permissions being changed.

Both the flash drive & the external drive are going through USB ports on my Dell Inspiron 9400 laptop, so this jives w/ the OP's connection - but what I find strange is that (if I understood correctly) the original poster in this thread is running Ubuntu v12, whereas I'm running v10.

NOTE: I came back to edit this because I'd forgotten to mention this. I did another reboot after discovering the new 2nd partion was still being mounted Read Only - and, when the system was fully rebooted, I discovered that one of the other partitions I hadn't done anything at all with on that external HD was now mounted as Read Only too!!! CRAP!!! What's wrong with this?

Only 2 things come to mind about this. One, is that there may have been something updated recently, of a  file that's being supplied to both v12 & v10. The other, is that maybe some twisted creep has finally managed to make a virus that infects Linux.

Any thoughts about this, or suggestions?

---

### Post by sudodus on 2013-03-03
> **ShadowGuardian said:**
> tried badblocks, this is what it says:

shadowaviator@shadow-Aspire-7740:~$ sudo badblocks -n /dev/sdb
[sudo] password for shadowaviator: 
badblocks: Read-only file system while trying to open /dev/sdb
shadowaviator@shadow-Aspire-7740:~$

Yes, it could be a bug, but maybe we can try another thing before giving up:

Did you connect and unmount (not eject) the USB drive before the two crucial operations?

**[FONT=courier new]sudo dd ...[/FONT]** and [FONT=courier new]**sudo badblocks ...**[/FONT]

Try again to connect the USB drive and then
```
sudo umount /dev/sdb1
```
(if it is still mounting as /dev/sdb1)
and run the zeroising dd command and the badblock command again

---

### Post by zero2xiii on 2013-03-03
+1 for the dmesg output.

Might I suggest clearing it first.

Unplug the USB drive then:
```
sudo dmesg --clear
```
The plug the USB drive back in and run:
```
sudo dmesg
```
NOTE: Not sure if dmesg runs without sudo, my permissions are heavily modified on my system.
Please post the output of the second command here.

Further more +1 on the "did you unmount" post (#15)

:)

---

### Post by Sharpie1 on 2013-03-03
Sad to say, easiest thing is to put it in a PC, right click, "format"

Sharpie1

---

### Post by carl4926 on 2013-03-03
> **Sharpie1 said:**
> Sad to say, easiest thing is to put it in a PC, right click, "format"

Sharpie1
If you mean Windows PC

It won't work either

---

### Post by scruffyeagle on 2013-03-03
I have 3 OS's on my laptop (3 partitions). Ubuntu v10.04, Debian Squeeze, & Xubuntu v12.04. I ran a little test, involving the Xubuntu. I rebooted from Unbuntu into Xubuntu, and tested copying files from one of the other partitions into the 2nd new partition. It worked okay. I rebooted & did it again - no problem. That told me for sure, that there wasn't anything inherently wrong in the new 2nd partition. It also told me for sure, that Xubuntu as it was right then & there was managing the USB permissions properly. I then did the downloading of updates which the OS had been nagging me about (but, I'd been intentionally delaying). After a reboot, the problem involving Read Only was happening in Xubuntu also!

This pegs it. There's a bug in the updates that are being served. It's crippling the permissions of drives loaded via USB, and it's affecting both v10.04 & v12.04.

A little more info from one more test: Rebooting into Ubuntu v10 using a previous kernel (44) didn't fix it. So, whatever the problem is, it's lodged somewhere other than the current (45) kernel.


Any suggestions what can be done about this?

---

### Post by sudodus on 2013-03-03
> **scruffyeagle said:**
> ...

This pegs it. There's a bug in the updates that are being served. It's crippling the permissions of drives loaded via USB, and it's affecting both v10.04 & v12.04.

A little more info from one more test: Rebooting into Ubuntu v10 using a previous kernel (44) didn't fix it. So, whatever the problem is, it's lodged somewhere other than the current (45) kernel.


Any suggestions what can be done about this?

Great :KS It will be much easier to solve it, now that you have described these details. Do you know if someone has reported it as a bug in Launchpad?

---

### Post by ShadowGuardian on 2013-03-03
for those who wanted dmesg:
 403.888131] sd 6:0:0:0: [sdb]  Sense Key : Data Protect [current] 
[  403.888137] sd 6:0:0:0: [sdb]  Add. Sense: Write protected
[  403.888143] sd 6:0:0:0: [sdb] CDB: Write(10): 2a 00 00 00 08 00 00 00 08 00
[  403.888155] end_request: critical target error, dev sdb, sector 2048
[  403.888161] Buffer I/O error on device sdb1, logical block 0
[  403.888165] lost page write due to I/O error on sdb1
[  403.888189] EXT4-fs error (device sdb1): __ext4_get_inode_loc:3680: inode #8: block 705: comm mount: unable to read itable block
[  403.888232] EXT4-fs (sdb1): no journal found

This is the last few lines.

also, ubuntu says it cant mount it when i plug it in or click on it. So i assume it is unmounted

---

### Post by ShadowGuardian on 2013-03-03
tried the unmount thing and then dd and badblocks. NO GO

as regards to the update bug,  the usb does the same stubborn thing in windows 7.

I think i just need a program or something that overrides or ignores the "readonly" part.  I don't need any data off the drive, just want a fresh usb.

---

### Post by carl4926 on 2013-03-03
Do you tell us if imagewriter will write an image to it?

---

### Post by ShadowGuardian on 2013-03-04
@carl4926

Sorry, I was not very clear.  Universal usb installer said it could not write on the usb.  Unetbootin said it successfully wrote the live ubuntu 12.10 iso to it.  However, my partitioners show no change in the partitions and when i tried to boot from the usb it gives me an error message saying it could not boot. 

 Minitool Partition Wizard and Unetbootin both said they successfully changed the data on the usb (I tried to wipe it and repartition with Minitool).  

However when i apply changes and refresh minitool it shows the same old 10.5gb of ext4 and the rest unallocated (which i cant partition because it also says "readonly").

It seems the whole thing is locked up not just the ext4 partition.

Any more suggestions?

---

### Post by carl4926 on 2013-03-04
> [COLOR=#000000]Any more suggestions?[/COLOR]Only Google the problem
*unlock usb dongle*
Or some such subject

---

### Post by dcstar on 2013-03-04
> **ShadowGuardian said:**
> for those who wanted dmesg:
 403.888131] sd 6:0:0:0: [sdb]  Sense Key : Data Protect [current] 
[  403.888137] sd 6:0:0:0: [sdb]  Add. Sense: Write protected
[  403.888143] sd 6:0:0:0: [sdb] CDB: Write(10): 2a 00 00 00 08 00 00 00 08 00
[  403.888155] **end_request: critical target error, dev sdb, sector 2048**
[  403.888161] **Buffer I/O error on device sdb1, logical block 0**
[  403.888165] lost page write due to I/O error on sdb1
[  403.888189] EXT4-fs error (device sdb1): __ext4_get_inode_loc:3680: inode #8: block 705: comm mount: unable to read itable block
[  403.888232] EXT4-fs (sdb1): no journal found


Well, there is your answer.

You have a hardware problem, a broken/faulty device.

Bin it.

---

### Post by ShadowGuardian on 2013-03-04
Thanks for pointing the critical target error, but could you explain what it means exactly.  I know it could be a hardware problem.  But i would like to try everything first, even if it may be futile.  Is there a program that would ignore the read only part and the hardware error and try to format anyway?

Thanks for the replies and suggestions

---

### Post by sudodus on 2013-03-04
> **ShadowGuardian said:**
> Thanks for pointing the critical target error, but could you explain what it means exactly.  I know it could be a hardware problem.  But i would like to try everything first, even if it may be futile.  Is there a program that would ignore the read only part and the hardware error and try to format anyway?

Thanks for the replies and suggestions

You have tried such programs already (according to your replies in this thread), and they have failed.

Have you checked if there is a hardware switch, that makes the drive read-only?

---

### Post by ShadowGuardian on 2013-03-04
I cant see a switch anywhere.  I'm gonna have a computer tech look at it tomorrow.  Has anyone else had a usb they bought break  after a short amount of use?  I just got it off newegg.com two weeks ago (I actually got two 32gb usb drives).  I think i will get two 16gb ones for ubuntu and fedora (dual-booting is a little unstable).

Oh well, thanks for the replies, and if you think of something else or something that might randomly work please let me know.

P.S. If there was a switch, wouldn't it have denied me access from the beginning.  Why would it start now?

---

### Post by carl4926 on 2013-03-04
> [COLOR=#000000]Has anyone else had a usb they bought break after a short amount of use[/COLOR]Yes, I mentioned earlier a 8GB one

> [COLOR=#000000]P.S. If there was a switch, wouldn't it have denied me access from the beginning. Why would it start now?[/COLOR]You know what they say...... Stuff happens!

---

### Post by schragge on 2013-03-05
> **ShadowGuardian said:**
> for those who wanted dmesg:
 ```
403.888131] sd 6:0:0:0: [sdb]  Sense Key : Data Protect [current] 
[  403.888137] sd 6:0:0:0: [sdb]  Add. Sense: [COLOR=#ff0000]Write protected[/COLOR]
[  403.888143] sd 6:0:0:0: [sdb] CDB: Write(10): 2a 00 00 00 08 00 00 00 08 00
[  403.888155] end_request: critical target error, dev sdb, sector 2048
[  403.888161] Buffer I/O error on device sdb1, logical block 0
[  403.888165] lost page write due to I/O error on sdb1
[  403.888189] EXT4-fs error (device sdb1): __ext4_get_inode_loc:3680: inode #8: block 705: comm mount: unable to read itable block
[  403.888232] EXT4-fs (sdb1): no journal found
```
Hmm, maybe [this advice]("http://askubuntu.com/a/138051") will help:
```

sudo apt-get install hdparm
sudo hdparm -r0 /dev/sdb

```
Also, similar problems were previously [thread=1284222]reported[/thread] for JetFlash USB drives. Some succeeded by reformatting them with [JetFlash Online Recovery]("http://www.transcendusa.com/Products/online_recovery_2.asp"). Does Kingston offer some low-level format utility for your drive model? Perhaps, [this]("http://www.kingston.com/us/support/technical/downloads?product=dthx30&filename=kingston_format_utility")?

---

### Post by scruffyeagle on 2013-03-06
It seems as if the solution for the OP has been found... Still, I think I should mention that my problem solved itself. The partitions which had been Read Only have returned to being Read/Write - and, I have no idea why.

---

### Post by sudodus on 2013-03-06
> **scruffyeagle said:**
> It seems as if the solution for the OP has been found... Still, I think I should mention that my problem solved itself. The partitions which had been Read Only have returned to being Read/Write - and, I have no idea why.

So, at least in your case, scruffyeagle, let us think it was some obscure bug, that has been fixed after an update :-)

ShadowGuardian, have a last try with your pendrive!

First you should update your system
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

And then try with your pendrive again! If you had the same problem as scruffyeagle, it may work now. Otherwise we can be pretty sure it's a hardware problem, a broken/faulty device, as dcstar told us some posts ago.

---

### Post by scruffyeagle on 2013-03-06
> **sudodus said:**
> So, at least in your case, scruffyeagle, let us think it was some obscure bug, that has been fixed after an update :-)
...


Well, that's the thing... I hadn't allowed any updates to happen, while I was trying to figure out exactly what had gone wrong. I did notice one detail of similarity between my situation & the OP - we'd both used gparted right before the Read Only problem happened.

Instigated by this situation, I did a lot of study on mount & fstab recently. Perhaps it would be worth a try for the  OP to attempt a remount specifying -rw?

---

### Post by ShadowGuardian on 2013-03-08
My computer tech had my usb so i wasnt replying.  It is still not fixed.  BTW i used gparted after the problem.  Problem started after i tried installing fedora 18.  I think fedora tried to use ubuntu's swap partition.  The install failed, and when i tried to format everything and try again is when the readonly problem started.

I wont throw it away because i want to fix it even if i cant use it.  I will try your suggestions tomorrow.  @sudodus: do you think i need to update to 12.10, because i would rather keep LTS.

Please keep sending suggestions, and thanks for the replies so far.

---

### Post by carl4926 on 2013-03-08
> [COLOR=#000000]do you think i need to update to 12.10, because i would rather keep LTS.[/COLOR]
12.04 is just fine

---

### Post by sudodus on 2013-03-08
> **ShadowGuardian said:**
> My computer tech had my usb so i wasnt replying.  It is still not fixed.  BTW i used gparted after the problem.  Problem started after i tried installing fedora 18.  I think fedora tried to use ubuntu's swap partition.  The install failed, and when i tried to format everything and try again is when the readonly problem started.

We don't know why this happened, but it is unlikely, that fedora should have destroyed it. And swap partitions are re-useable, at least if they are not encrypted.
> 
I wont throw it away because i want to fix it even if i cant use it.  I will try your suggestions tomorrow.  @sudodus: do you think i need to update to 12.10, because i would rather keep LTS.

Please keep sending suggestions, and thanks for the replies so far.

Yes, keep it! In case it is a bug, maybe your system will manage to use the USB drive soon.

Finally, I do not think you need to upgrade to 12.10. ***Stay with 12.04 LTS, it is better debugged and more stable***. This problem with the USB drive is not an issue because of too new hardware for your version of the operating system.

---

### Post by ShadowGuardian on 2013-03-08
Good to see your online sudodus

---

### Post by ShadowGuardian on 2013-03-08
Anyway, i am gonna fight this stupid thing until i figure it out.  I am willing to try magnets :)

After the failed fedora install, minitool partitioner said ubuntu swap was gone.

I believe when i tried to reinstall ubuntu on it after the failure (to see if it would help) it would not recognize/mount the usb so i couldnt select it for the install.  My computer tech said try the fedora install and see what happens.  

I dont think its an update issue because the usb fights windows 7, too.  Just thought i would give you guys more info (I love these forums)

---

### Post by sudodus on 2013-03-08
If by any chance, something was written to parts of the flash memory outside what is normally available to the user, you can try to wipe the pendrive with DBAN
[URL="http://www.dban.org/"][COLOR=#ff0000]
[http://www.dban.org/](http://www.dban.org/)[/COLOR][/URL]

and after that try to create a partition table with partitions and file systems again.

---

### Post by ShadowGuardian on 2013-03-08
If I use Dban, can i put it on a usb using universal usb installer?l  Also, i havent had to create a partition TABLE before, is it difficult or can i just use minitool or Gparted?

This sounds like what I need, a COMPLETE clean of the drive.  I hope it works and thank you very much.

P.S. I will let you know how it goes.

---

### Post by sudodus on 2013-03-09
> **ShadowGuardian said:**
> If I use Dban, can i put it on a usb using universal usb installer?l

I think so, try it! Otherwise Unetbootin is good (there are versions for linux as well as Windows).
> 
Also, i havent had to create a partition TABLE before, is it difficult or can i just use minitool or Gparted?

I use gparted, I think it is easy to use. Select Device - Create Partition Table (and select MSDOS)
> 
This sounds like what I need, a COMPLETE clean of the drive.  I hope it works and thank you very much.

P.S. I will let you know how it goes.

Good luck :-)

---

### Post by ShadowGuardian on 2013-03-09
Do I need to pull my HDD before I try this?  Sounds like it could lead to alot of work.  I have install linux to USB before without unplugging my HDD, but I havent used DBAN before.

---

### Post by sudodus on 2013-03-09
> **ShadowGuardian said:**
> Do I need to pull my HDD before I try this?  Sounds like it could lead to alot of work.

No I think DBAN will ask which drive to wipe. It should not wipe directly. But if you want to be 100% sure, unplug the internal drive, or use this as an incentive to make a ***backup of your installed system***! With a good backup you can afford a mistake.
> 
  I have install linux to USB before without unplugging my HDD, but I havent used DBAN before.

An alternative is to do it in a desktop computer, where it is easy to unplug the internal drive, and it is easy to move the USB pendrive ;-)

---

### Post by sudodus on 2013-03-09
See this link, I don't think you will start wiping the drive by mistake

[[COLOR=#0000ff]http://www.ucd.ie/itservices/itsupport/itsecurity/securitytools/howtousedbantoremovethecontentsfromaharddisk/[/COLOR]]("http://www.ucd.ie/itservices/itsupport/itsecurity/securitytools/howtousedbantoremovethecontentsfromaharddisk/")

---

### Post by ShadowGuardian on 2013-03-09
I decided to test DBAN.  I put it on a usb and booted.  It shows three drives: my HDD, its own usb, and an unrecognized usb (the corrupt kingston).  I didnt try pressing any keys, since when i go to wipe it, I am gonna pull my HDD (just for safety).  The "arrow" next to the unrecognized one is different, but like i said i didn't try anything.  I am being very cautious.  

I am worried that it wont be able to wipe the usb, since it is unrecognized.

Just thought i'd post to see what you would say.  Can it still wipe an "unrecognized" usb?

---

### Post by ShadowGuardian on 2013-03-09
Sorry about the over eager post.  I pulled my HDD and tried to wipe the kingston usb.  But since it did not recognize it, it could not wipe it. It didnt even give me the option of wiping it.
DBAN HAS FAILED ME!  Good try though.

I might try hdparm, but if DBAN did not work then I doubt hdparm will.

---

### Post by sudodus on 2013-03-10
> **ShadowGuardian said:**
> Sorry about the over eager post.  I pulled my HDD and tried to wipe the kingston usb.  But since it did not recognize it, it could not wipe it. It didnt even give me the option of wiping it.
DBAN HAS FAILED ME!  Good try though.

I might try hdparm, but if DBAN did not work then I doubt hdparm will.

I think you have done what is possible now. There is something wrong with the hardware of that pendrive.

> **ShadowGuardian said:**
> i have a kingston datatravaler 32gb.  I got it a week ago so its brand new.

 i partitioned 10.5gb to ext4 with 3.5gb swap.  then installed ubuntu  12.10. it worked great. partitioned the other "half" the same way and  tried to install fedora (which i havent used much) it said install  failed.  after that it said the half i partitioned for fedora was  unallocated when using minitool partitioner.  and the usb has gone read  only.  it mounted in ubuntu at first but now it wont mount (something  about bad superblock)...

It is still new. I think this is typical for electronic devices. Either they break, when they are brand new, or they last for years (often until they are obsolete). In my country there should be a valid guarantee. I don't know about the consumer market laws in your country, but try to return it to the vendor and ask for a new one.

---

### Post by ShadowGuardian on 2013-03-10
I will hang on to it just in case, but i am ordering in two 16gb flashdrives.  I know i could dual boot a 32gb usb (since through this mess i have figured out how), but it will be more useful to have two usb drives.

So this is my plan: my other 32gb kingston is for storage, one of the 16gb ones will be for a custom pentesting/hacking system, the other 16gb one will be my computer tech bootable "toolbox" for cleaning, repairing, and rescuing data, the 8gb i have will be for distro testing and installation. (yes i bought a case for all these usb drives)

Anyway, thanks very much for your help.

---

### Post by sudodus on 2013-03-10
You are welcome :-)

Do you run a small company or are you 'only' helping family and friends?

---

### Post by schragge on 2013-03-10
@**ShadowGuardian**
Just curious, what was the result of trying *hdparm -r0*?

---

### Post by sudodus on 2013-03-10
Would you like to try another thing to save the pendrive? See this link

[[COLOR=#ff0000]http://ubuntuforums.org/showthread.php?t=2124232[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2124232")

---

### Post by mirearts KING SUNNY on 2013-03-10
Assuming you have GPARTED,

Go to the partitions tables, and select the USB partition and as you used an unsawp the swap partition.

Now open the disks utility and select the USB again, then select analyse/verify depending on the version. If you have any errors, try to delete all partition tables and create only 1 full with FAT32 file system and repeat the 2nd step.

If the error persist, you may have a faulty USB disk.

---

### Post by ShadowGuardian on 2013-03-10
I haven't tried the hdparm thing yet, but i will try after the gparted suggestion and windows utility suggestion. I hope they work.

Also, I don't run a company (at least not yet), but I help anyone who needs it.  That and I like to have tools.  I suppose you could say I would like to be a "Tony Stark" (IronMan) of computers, although I will try to develop a miniature fusion reactor and a suit to utilize it (I am not kidding, but it will be awhile).

Anyway, I will try the suggestions and let you guys know.  Thanks again.

---

### Post by ShadowGuardian on 2013-03-10
The SSS_MP thing is russian, but I found a download for english.  However, I apparently need to know the SSS of my usb.  How do I find out or will the latest SSS_MP thing work?

---

### Post by sudodus on 2013-03-10
> **ShadowGuardian said:**
> The SSS_MP thing is russian, but I found a download for english.  However, I apparently need to know the SSS of my usb.  How do I find out or will the latest SSS_MP thing work?
I have no idea. You have not much to lose, the USB drive is already bricked :P

But of course, you have to trust the guy who posted the link at the Ubuntu Forums.

---

### Post by ShadowGuardian on 2013-03-10
I guess its trial and error time.

---

### Post by vandorjw on 2013-03-10
```

$ sudo su

```
> 
> enter password


```

# blkid

```
> 
....
/dev/sdb1: LABEL="Steam-Data" UUID="4f789d43-816b-47de-a011-6a5f2fba943f" TYPE="ext4" PARTUUID="fc576711-24ca-4815-885e-2e045769a573" 
**/dev/sdd1: LABEL="datatravele" UUID="C4C4-6002" TYPE="vfat"** 


```

# gdisk /dev/sdd

```
(sdd because my datatraveler was on sdd1) <-- yours may/will be different
```

press o then y

```

> 
Command (? for help): o
This option deletes all partitions and creates a new protective MBR.
Proceed? (Y/N): y


```

press n then hit enter a few times

```
> 
Command (? for help): n
Partition number (1-128, default 1): 
First sector (34-7669790, default = 2048) or {+-}size{KMGTP}: 
Last sector (2048-7669790, default = 7669790) or {+-}size{KMGTP}: 
Current type is 'Linux filesystem'
Hex code or GUID (L to show codes, Enter = 8300): 
Changed type of partition to 'Linux filesystem'


```

press w then y

```

> 
Command (? for help): w
Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT) to /dev/sdd.
The operation has completed successfully.



Press ctrl+d when finished (to leave root)

Now, it still won't have a filesystem, but the partititions are set up, and the GPT table should have been recreated.
If this didn't work, the device is broken. I hope this does solve your problem.

To put a filesystem back on, use a tool like gparted.

---

### Post by dpharo on 2013-03-10
If you have a windows box (hate saying this), plug the jump drive in and in MY COMPUTER right click and select check for errors, make sure to allow to fix errors too. You should not lose any data, but anything can happen. This will take some time as the jump drive is huge. Good luck!

---

### Post by ShadowGuardian on 2013-03-12
Vandorjw suggestion results:

 gdisk /dev/sdb
GPT fdisk (gdisk) version 0.8.1

NOTE: Write test failed with error number 30. It will be impossible to save
changes to this disk's partition table!

EBR signature for logical partition invalid; read 0xD569, but should be 0xAA55
Error reading logical partitions! List may be truncated!
Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by typing 'q' if
you don't want to convert your MBR partitions to GPT format!
***************************************************************

Any ideas.  Not really sure what i am looking at.

---

### Post by ShadowGuardian on 2013-03-12
Went through vandorjw steps, but ended with:
Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT).
Unable to open device '/dev/sdb' for writing! Errno is 30! Aborting write!

Any ideas?

---

### Post by vandorjw on 2013-04-03
Sorry to get back to you 3 weeks later.

I have never been in your situation before so I won't be able to give you solid advice.
The problem is that your device is in READ-ONLY mode for some reason. I am trying to think of a situation right now when the root account would not have write permission. (You don't have SE-Linux enabled do you? Ubuntu doesn't even include that.)

Errno 30 is what told me the device is read only.
See this --> [http://www.barricane.com/c-error-codes-include-errno](http://www.barricane.com/c-error-codes-include-errno)

My only suggestion is to look for a physical button that made the device be read only.
Otherwise try to bring it back the store, or trash it. :(

---

### Post by schragge on 2013-04-04
I'm not sure a physical button is the only way to turn off the hardware read-only mode. See [post=12542306]my previous post[/post] in this thread.

---

### Post by necro99 on 2013-05-15
ok so I realize I've arrived quite late in this but I was digging for an answer to this exact issue when I ran across this thread. since then I believe I have found the answer. recently I installed pfsense, a FreeBSD based firewall/router, via a 32GB Lexar jumpdrive. after doing so my drive decided it was going to be read only and nothing I did seemed to work. I went through many of the same steps I see here and nothing worked. until, that is, I ran a Windoze program (yeah, yeah, whatever. I use what works for me under any given circumstance. no fanboi-ism here.) called "Hard Disk Low Level Format Tool". currently I am at about 60% of it being leveled. if youre interested the link is [http://www.fileguru.com/Hard-Disk-Low-Level-Format-Tool/download](http://www.fileguru.com/Hard-Disk-Low-Level-Format-Tool/download) , if not, suit yourself. just thought it might be helpful. :)

---

### Post by necro99 on 2013-05-15
quick update, it finished successfully and I was able to format it without a hitch.

now back to your regularly scheduled programming.

---

