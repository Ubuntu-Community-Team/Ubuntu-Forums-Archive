---
title: "Blue Screen w/ black bottom"
date: 2007-05-09
forum: General Help
---

### Post by Lery on 2007-05-09
Just downloaded and installed this project.  Seems like a really cool idea.

I installed and it downloaded the iso.  Installed on to my C drive which is NTFS running Windows XP Pro.

That said, the install seemed to go fine.  I chose Ubuntu on the bootup.  Some things went by, a progress bar went by with copying some additional files.

Now I'm looking at a Blue Screen with a black bottom portion that looks like it has a cursor blinking.

I left this go for about 15 minutes.

Is there anything I should be doing?  Is there a problem?

---

### Post by ago on 2007-05-09
Probably not. Just wait.

See also [https://bugs.launchpad.net/lupin/+bug/113273](https://bugs.launchpad.net/lupin/+bug/113273)

Sometimes, when it takes over 30 mins, it might be due to a driver missing for your particular harddrive which forces Linux to use far slower I/O operations. You can also select smaller virtual disk when you install.

---

### Post by Lery on 2007-05-09
Ok, it's still going.  Not sure where you are speaking about the virtual disk size, but if for some reason this does not start working shortly I will try looking for in in the installation process.

---

### Post by jimbo99 on 2007-05-09
I have been trying this on a compaq r3000 laptop with a newly installed 60gig HDD with XP Home SP2 on it.  I have backed up the .iso file so I don't have to keep downloading it.

When I start I get the mp-bios bug error, but that's not the issue I'm  having.  What happens is that when it starts into ubuntu after a new install I get various messages and if I watch closely I see a message about /sys missing.  It also lists one or more other directories missing.

Then it proceeds to copy some files and then dumps me to a blue screen with black on the bottom.  I've let it run for some time, not a half hour.  During the time I waited there was no disk activity at all.

I looked at saw a preseed.cfg.template file but no preseed.cfg.  I then looked at the menu.lst file and unfortunately in Windows the carriage return/line feed isn't read properly.  Same for the logs.  Also the menu.lst is a rather sizable file with more than just a few entry for different boot types.

I'm going to go back and wipe and try one more time and let it sit for hours if necessary, but some explanation of why I am getting the blue screen of death with a black bottom without any sort of activity.

I could get quite a few people interested in Ubuntu if this were easily managed with this sort of set up.  Not to mention saving me a considerable amount of time setting it up for others.

Keep up the good work and please, this should not be happening.  I'd appreciate a quick fix so I can move on with testing.

---

### Post by Lery on 2007-05-09
If it helps my HD is a SATA drive.  Other than that all pretty much straight forward.

-Lery

---

### Post by ago on 2007-05-09
> **jimbo99 said:**
> What happens is that when it starts into ubuntu after a new install I get various messages and if I watch closely I see a message about /sys missing.  It also lists one or more other directories missing.
You can safely ignore those errors

> Then it proceeds to copy some files and then dumps me to a blue screen with black on the bottom.  I've let it run for some time, not a half hour.  During the time I waited there was no disk activity at all.
You should let it run a bit, particularly if your virtual disk size is fairly large (you select that from wubi>settings). Note that if you have interrupted the installer you have to reinstall. As mentioned, we may have missed a particular HD driver and that may actually slow down the installer to snail speed. Since you have a sata drive that might also be the case. You can press Alt+F4 to see what is happening. What is exactly the make and model of your HD?

> I looked at saw a preseed.cfg.template file but no preseed.cfg.
That is normal. Preseed gets deleted during installation for security reasons
 
> I then looked at the menu.lst file and unfortunately in Windows the carriage return/line feed isn't read properly.  Same for the logs.
You can use wordpad for that.
 
> I'm going to go back and wipe and try one more time and let it sit for hours if necessary, but some explanation of why I am getting the blue screen of death with a black bottom without any sort of activity.
See the above bug report

---

### Post by jimbo99 on 2007-05-09
AGO,

I'm already an Ubuntu user and have been using it for some time.  I have a very nice desktop setup.  I think what you guys are doing is fantastic.  So, even if I can't get t his particular incarnation working I have to say you are a decent guy to take the time to help so many of us.

I have chosen to set aside 20gigs, so yes it probably should take some time.  I was wondering why everything seems to be going so quickly.  What will get people scratching their heads is that the HDD appears to have no activity.

---

### Post by Lery on 2007-05-09
Ok great.  Alt-F4 was the trick to show me something.

Now here is what I have and it indeed seems to have just quit the installation process.

Back at 2:04 (it's now 3:34 p.m.), I have the following showing on the screen:

bio too big device loop6 (2 > 0)
EXT2-fs:  unable to read superblock
bio to big device loop6 (2 > 0)
EXT3-Fs:  unable to read superblock
bio to big device loop6 (8 > 0)
ReiserFS:  loop6:  warning: sh-2006: read_super_block: bread failed (dev loop6, block 2, size 4096)

some other trailing errors come along as well.

The hard drive is a Maxtor SATA 6Y120M0.

Other thoughts to get this going?

---

### Post by jimbo99 on 2007-05-09
I know this isn't on topic but I always recommend against Maxtor drives, due primarily to how often they fail and how poorly they treat customers on failures to rma'd failed drives.

---

### Post by jimbo99 on 2007-05-09
I also see things like that:

bio too big device loop6 (2 > 0)
EXT2-fs:  unable to read superblock
bio too big device loop6 (2 > 0)
EXT3-fs:  unable to read superblock

This is repeated for ReiserFS and FAT

Then it just sits there at bio too big device loop6 (8 > 0)

-Jim

P.S.  If I hit ctrl+c i get the following:
init:  Process '/usr/bin/tail -f /var/log/syslog' (pid 7861) exited.  Scheduling it for restart.

---

### Post by foxtrott on 2007-05-10
Hi,
I had tried to install wubi on my laptop (fujitsu siemens amilo)  but i have the bluescreen too after the first reboot.
So console mode > nano /var/log/syslog

I have an error at the level of the inode writing

the last lines of the log is:
date hour main-menu[4554]: (process:5665): 27/47
date hour main-menu[4554]: (proc

i tried to reinstall wubi or uninstall to reinstall it after, but i have always the same trouble.
Please help me!!!

Thanks

---

### Post by ago on 2007-05-10
It is formatting the virtual disk. We have no visual feedback in that stage (no progressbar) but that is normal. Depending on the size of your virtual disk and disk speed, it can take anything from 1 minute to 30 minutes. So just let it run. More than 30 min would probably indicate that we did not include a driver for your particular HD (usually that happens with some more esoteric Sata drives) and disk I/O is suboptimal (read very, very slow), therefore formatting takes forever.

---

### Post by foxtrott on 2007-05-10
Ok, thanks for answering, i retry now and i come back

---

### Post by RickyDo on 2007-05-10
I've been trying to install and I'm getting a similar error:

"bio too big device loop6 (8>0) " with a time stamp of 21:54.  

I finally stopped the install after 12 hours.  Am I out of luck or is there something I might change to get the install going again?

---

### Post by ago on 2007-05-10
Did you install on FAT? What size was assigned to the Virtuald disks? What size were actually the virtual disks? Do you have sata/raid?

PS you can also try to reinstall and remove home.virtual.disk before rebooting, that virtual disk is optional

---

### Post by foxtrott on 2007-05-10
> **ago said:**
> It is formatting the virtual disk. We have no visual feedback in that stage (no progressbar) but that is normal. Depending on the size of your virtual disk and disk speed, it can take anything from 1 minute to 30 minutes. So just let it run. More than 30 min would probably indicate that we did not include a driver for your particular HD (usually that happens with some more esoteric Sata drives) and disk I/O is suboptimal (read very, very slow), therefore formatting takes forever.


My screen is always blue, since more 1 hour :( 
My disk isn't a SATA.

I don't know what to do now  :confused:

---

### Post by ago on 2007-05-10
Try with small disk sizes.

Use 3-4 GB for system, 0.5 for home and 0.5 for swap.

See if that improves the situation.

---

### Post by foxtrott on 2007-05-10
is it normal that there is no activity on the disk when the virtual disk is formatting ??

---

### Post by ago on 2007-05-10
Probably not but you can check what processes are running by pressing alt+f2 and executing:

ps -ax

---

### Post by foxtrott on 2007-05-10
ps -ax
many process and the last :
7821    root   1092  D  mkfs.ext3 /dev/loop7

i think i'll give up.

---

### Post by ago on 2007-05-10
That means that it is formatting. What hd do you have?

---

### Post by foxtrott on 2007-05-10
the hard disk is a fujitsu MHT2040AT.
My laptop is a sh*t, euh excuse me, a Fujitsu siemens Amilo-EN Celeron 2.4 256Mo ram.
thanks for your help.

---

### Post by ago on 2007-05-10
not sure if there is hdparm in d-i, but try

hdparm -i /dev/hda

---

### Post by Lery on 2007-05-10
> **Lery said:**
> Ok great.  Alt-F4 was the trick to show me something.

Now here is what I have and it indeed seems to have just quit the installation process.

Back at 2:04 (it's now 3:34 p.m.), I have the following showing on the screen:

bio too big device loop6 (2 > 0)
EXT2-fs:  unable to read superblock
bio to big device loop6 (2 > 0)
EXT3-Fs:  unable to read superblock
bio to big device loop6 (8 > 0)
ReiserFS:  loop6:  warning: sh-2006: read_super_block: bread failed (dev loop6, block 2, size 4096)

some other trailing errors come along as well.

The hard drive is a Maxtor SATA 6Y120M0.

Other thoughts to get this going?

Still getting the above.  Any hope for me?

P.S.  I booted back into Windows and made the virtual disk a smaller size from the default.  Did not seem to help.

---

### Post by ago on 2007-05-10
remove home.virtual.disk before rebooting

---

### Post by Lery on 2007-05-10
> **ago said:**
> remove home.virtual.disk before rebooting

Ok I do not have a home.virtual.disk.  I have swap.virtual.disk and system.virtual.disk if that helps?

I would REALLY love to get this working.  I have been messing around with Ubuntu on a VMWare server instance for a few days now and reading up on it all.  I really like it and would love to take advantage of some of the things out there that I could take advantage of in a non-vm world.


-Lery

---

### Post by nickd4 on 2007-05-10
I get the same blue screen w/ black bottom only i was patient and let it go for 5 hours.. what i think is ample time... and it still didnt accomplish anything. what's going on!?

---

### Post by ago on 2007-05-10
Press alt+f2

then find out what is your hardisk id (usually either /dev/sda or /dev/hda):

cat /proc/mounts | grep host

then, assuming your disk is sda,  run

hdparm -i /dev/sda 

See whether the asterisk is on a udma setting or not.

---

### Post by Lery on 2007-05-10
> **ago said:**
> Press alt+f2

then find out what is your hardisk id (usually either /dev/sda or /dev/hda):

cat /proc/mounts | grep host

then, assuming your disk is sda,  run

hdparm -i /dev/sda 

See whether the asterisk is on a udma setting or not.

Ok, not sure what I am looking for here.  I did the commands listed.  It gave me some output.  The last part of the output says * signifies the current active mode.

However, I look through the output above, and I do not see anything with an * on it.

So what else should I be doing?

The output looks valid and good.  It even lists the model of my SATA HD, which is a Maxtor Model 6Y120M0

---

### Post by ago on 2007-05-11
This is my output of hdparm -i /dev/sda:

/dev/sda:

 Model=TOSHIBA MK4026GAX                       , FwRev=PA102D  , SerialNo=           X4E11068T
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=48
 BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=78140160
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6

 * signifies the current active mode



If you note I have udma5 enabled (it is prefixed with an asterisk). The fist command is only used to let you know the ID of your HD.

---

### Post by Lery on 2007-05-11
> **ago said:**
> This is my output of hdparm -i /dev/sda:

/dev/sda:

 Model=TOSHIBA MK4026GAX                       , FwRev=PA102D  , SerialNo=           X4E11068T
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=48
 BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=78140160
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6

 * signifies the current active mode



If you note I have udma5 enabled (it is prefixed with an asterisk). The fist command is only used to let you know the ID of your HD.

Allright here is my output for hdparm -i /dev/sda.  I have to of course manually type this out :)

/dev/sda:

Model=Maxtor 6Y120M0                                                                    ,FwRev=YAR51EW0, SerialNo=Y3KY9GXE
Config={ Fixed }
RawCSH=16383/16/63,  TrkSize=0,  SectSize=0,  ECCbytes=4
BuffType=DualPortCache, BuffSize=7936kB, MaxMultSect=16, MultSect=?16?
CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=240121728
IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
PIO modes:  pio0 pio1 pio2 pio3 pio4
DMA modes:  mdma0 mdma1 mdma2
UDMA modes:  udma0 udma1 udma2 udma3 udma4 udma5
AdvancedPM=yes:  disabled (255) WriteCache=enabled
Drive conforms to:  ATA/ATAPI-7  T13  1532D  revision  0:  ATA/ATAPI-1  ATA/ATAPI-2 ATA/ATAPI-3 
ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

*signifies the current active mode

So, hopefully that means something to you?  I can see the difference in mine and yours in that I do not have an asterik by anything.

So what's next?

---

### Post by ago on 2007-05-11
Dont you have an * in front of udma?

UDMA modes: udma0 udma1 udma2 udma3 udma4 ***udma5 **

---

### Post by Lery on 2007-05-11
> **ago said:**
> Dont you have an * in front of udma?

UDMA modes: udma0 udma1 udma2 udma3 udma4 ***udma5 **

Nope.  No asterick.

---

### Post by ago on 2007-05-11
hdparm -I /dev/hda

only report dma settings

---

### Post by Lery on 2007-05-11
> **ago said:**
> hdparm -I /dev/hda

only report dma settings

Here is what comes up when I do hdparm -I /dev/hda and just in case the formatting was wrong I also did hdparm -I /dev /hda

When I do the following:  hdparm -I /dev /hda:

HDIO_DRIVE_CMD(identify) failed:  Inappropiate ioctl for device
/hda:  No such file or directory

When I do the following:  hdparm -I /dev/hda:

/dev/hda:  No such file or directory

---

### Post by ago on 2007-05-11
I meant: hdparm -I /dev/sda

---

### Post by Lery on 2007-05-11
> **ago said:**
> I meant: hdparm -I /dev/sda

Ok I type that and it scrolls off the screen a little.  Anyway what specifically are you looking for?  The last statement says:

 Checksum:  correct

---

### Post by ago on 2007-05-11
I am looking for DMA settings to see whether it is active or not in your case.

---

### Post by Lery on 2007-05-11
> **ago said:**
> I am looking for DMA settings to see whether it is active or not in your case.

Ok is there a trick to scroll up to see some of the things that went by?  If it helps I did not notice anything there in the portion of the screen that I could see.

---

### Post by ago on 2007-05-11
Shift + PgUp

or you can write the output of the command to a file:

hdparm -I /dev/sda > hdinfo
cp hdinfo /host

Now you should see the file under C:

---

### Post by Lery on 2007-05-11
> **ago said:**
> Shift + PgUp

or you can write the output of the command to a file:

hdparm -I /dev/sda > hdinfo
cp hdinfo /host

Now you should see the file under C:

Allright.  I did the command you provided and did not see anything happen.  I checked the C drive and was not able to see any log file created recently.

Regardless I was able to shift PgUp and was able to see an * by udma6.

Doing the earlier commands udma6 was not displayed.

---

### Post by ago on 2007-05-11
Well that looks fine to me.

---

### Post by Lery on 2007-05-11
> **ago said:**
> Well that looks fine to me.

So back to the drawing board I guess?

---

### Post by ago on 2007-05-11
Make the virtual disks 4GB 0.5GB and 0.5GB. Use wubi minefield 0.6 and see how long it takes.

---

### Post by Lery on 2007-05-11
> **ago said:**
> Make the virtual disks 4GB 0.5GB and 0.5GB. Use wubi minefield 0.6 and see how long it takes.

When I click on settings in the installation program, to set what you have suggested:

I can only change System Size.  So I set that to 4gb.

Home Size is greyed out and I can not change it.

Swap Size, I put to 0.5.

You say to use wubi minefield 0.6?  What exactly is that and where?  

So I tried it with the settings chosen above.

To my shock it booted and installed!  I am now logged in to Ubuntu.

Now previously I did change the System size to 4gb, and tried but it failed.

So the only thing I can think of that did the trick was also setting the swap size to 0.5.  No clue what that means?

During boot up I got a failure next to something but it flies by to fast and then boots into Ubuntu.

Thank you so much for all the help and advice.  Now I can really start playing with this :)  Oh and learning it as well.

---

### Post by ago on 2007-05-11
> **Lery said:**
> Home Size is greyed out and I can not change it.
That is because you are in reinstallation mode. And when you reinstall you do not want to risk wiping out your data...

> You say to use wubi minefield 0.6?  What exactly is that and where?  
That will give you some visual feedback when virtual disks are formatted. And it will detect FAT filesystems and avoid having too large virtual disks there. [http://ubuntuforums.org/showthread.php?t=439597](http://ubuntuforums.org/showthread.php?t=439597)

> Now previously I did change the System size to 4gb, and tried but it failed.
It might be that you were using FAT and had one of the disks larger than 4GB?  Anyway I am glad it works.

---

### Post by foxtrott on 2007-05-12
Hi,
I tried all you said.
hdparm >> *udma5 >> so it should be ok

partitions sizes: 4gb /0.5Gb/0.5Gb >> so it should be ok

but i always have the blue screen (now with the last release,  there is a progression bar, it stops at 33% - formatting system.virtual.disk)
alt+f4>> main menu 4638: process 5749: 27/32

i despair :(

if someone have any suggestion, i take it.

Thanks

---

