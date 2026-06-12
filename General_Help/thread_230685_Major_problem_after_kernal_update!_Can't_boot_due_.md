---
title: "Major problem after kernal update! Can't boot due to BIOS HDD size limitation."
date: 2006-08-06
forum: General Help
---

### Post by KillrBuckeye on 2006-08-06
I have been running Ubuntu 6.10 on an old PIII rig for about a month now.  I recently upgraded the hard drive to a 250 GB Western Digital and started using it as a home file server.  Everything was working great (2 weeks) until I applied the updates and a new kernal image was downloaded.  Upon the reboot, I was greeted with an error message about failure to load the kernal image because the BIOS couldn't read past XXX cylinder on the hard drive, followed by the Grub boot menu.  When I selected the new kernal image from the boot menu, I got the same message.  However, I was able to select the old kernal image and it booted fine.

However, upon the next reboot I was greeted by the Grub command prompt. :(  I tried to access the Grub boot menu on the hard drive as follows:

```
grub> configfile (hd0,0)/boot/grub/menu.lst
```

I got the following error message:
```
Error 18:  Selected cylinder exceeds maximum supported by BIOS
```

Great... just great.  I booted from the LiveCD, but I don't know what to do.  Any suggestions?

BTW, upgrading the BIOS seems to be out of the question.  This mobo (Asus CUV-NT) is from an old HP, and it already has the latest BIOS from the HP website.  Support for larger HDDs was never added.  :rolleyes:

---

### Post by Ocxic on 2006-08-06
I would suggest makin a /boot partition (100-200MB) at the beginging of your hard drive then the problem wont be a problem. I'm pretty sure you can just copy the folder to the new partiton.

---

### Post by KillrBuckeye on 2006-08-06
Yeah, I think that would work.  However, my current boot partition is already at the beginning of the disk, so how could I create a new partition without wiping out the existing one?

---

### Post by vijirajan on 2006-08-06
You need a tool like PartitionMagic or System Rescue CD ([http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)) to do that.

---

### Post by vijirajan on 2006-08-06
You could try GParted too.

---

### Post by KillrBuckeye on 2006-08-06
Okay I moved the root partition to the end of the disk and created a boot partition in its original location at the beginning of the disk. Now Grub is able to load the kernal image, however it fails when attempting to mount the file system. I'm not sure what I'm supposed to do at this point. There must be something I need to change in the /boot folder to direct the OS to the new location of the root partition. I don't think it can even find fstab since it resides on the root partition, which has changed locations.

---

### Post by vijirajan on 2006-08-06
Can you paste the error message in this thread? Also check the root entry in /boot/grub/menu.lst. Make sure it points to the right partition (since you moved the partition, the parition number might have changed).

---

### Post by vijirajan on 2006-08-06
This is what my kernel entry in /boot/grub/menu.lst looks like:

title           Ubuntu, kernel 2.6.15-26-686
root            [COLOR="Red"](hd0,4)[/COLOR]
kernel          /boot/vmlinuz-2.6.15-26-686 root=[COLOR="Red"]/dev/sda5[/COLOR] ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-686
savedefault
boot


Make sure the red colored entries are specified correctly in your case. Root entry should point to the partition that will be mounted as "/". Assuming you have only 2 partitions it will be something like [COLOR="Red"]root (hd0, 1)[/COLOR] and the kernel entry will be something like [COLOR="Red"]root=/dev/sda2 or /dev/hda2[/COLOR].

Hope this helps!

---

### Post by KillrBuckeye on 2006-08-06
I changed the menu.lst entry to point to the proper root partition, and now it will boot up fine if I use the LiveCD and choose the "boot from first hard disk" option.  However, if I just try to boot from the hard drive directly, I get the following error:

DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

I'm thinking I may need to reinstall grub in my /boot partition, then rewrite it to the boot sector.

---

### Post by vijirajan on 2006-08-06
Sounds like you have to reinstall GRUB. You can do that with Dapper LiveCD or from within Dapper.

Here is an example:

```

> grub
> root (hd0,0)
> setup (hd0)
> quit

```

---

### Post by KillrBuckeye on 2006-08-06
I don't know what's going on, but it won't let me do that. :(  It says that (hd0,0) doesn't exist.  Right now I am REALLY confused.  Why can I boot off the HDD if I do it through the LiveCD, but can't just boot straight off the drive.  It doesn't make sense to me.

---

### Post by vijirajan on 2006-08-06
Sorry that should actually be [COLOR="Red"]root (hd0,1)[/COLOR] not (hd0,0)

---

### Post by KillrBuckeye on 2006-08-06
Please clear up a point of confusion for me.  The kernal image should reside in the /boot partition, correct?  However, the root file system should be the partition I moved to the end of the drive, which is now /dev/hdb4, right?  Shouldn't one entry in menu.lst point to hd0,0, and the other point to /dev/hdb4?

---

### Post by KillrBuckeye on 2006-08-06
This makes no sense. If I boot from a Grub floppy, I can specify the menu.lst file at "(hd0,0)/grub/menu.lst" and it boots fine. If I boot from the LiveCD, I can tell it to boot from the hard drive and Grub starts just fine. However, if I simply boot from the hard drive, I still get the DISK BOOT FAILURE error. Could you please walk me through the process of reinstalling Grub to make sure that I'm not doing anything wrong? I basically booted, went to the boot partition (mounted at /boot), then installed Grub via "grub-install /dev/hdb1" . I then re-wrote Grub to the MBR by starting grub and typing:

> root (hd0,0)
> setup (hd0)

Everything reports out okay. Am I missing something? Is my MBR screwed up somehow?

---

### Post by vijirajan on 2006-08-06
Let me get some information here before we try to fix the issue. Can you let me know how many hard disks you have and the list of partitions in each of these hard disks?

---

### Post by vijirajan on 2006-08-06
Also let me know if you get GRUB menu at all when you boot the system. If you don't then it means MBR is not installed correctly.

---

### Post by louieb on 2006-08-06
since you now have a seperate boot partition all paths are relative to that partition. I am set up in a simular way. here is my entry for ubuntu.

```
title		Ubuntu, kernel 2.6.15-26-386
                root (hd0,0)
                kernel /vmlinuz-2.6.15-26-386 root=/dev/hda3 ro quiet splash
                initrd /initrd.img-2.6.15-26-386
                savedefault
                boot

```   
note the path for the kernnel and initrd. This machine has the following partitions on hda.
1 boot
2 swap
3 ubuntu
4 fendora.
Hope this helps

---

### Post by vijirajan on 2006-08-06
Let me walk thru the steps of installing GRUB:

Let us assume the following setup for this example:

You have a hard disk with three partitions.

Partition 1 contains /data,
Partition 2 contains /boot,
Partition 3 contains /.

Here are the steps to install GRUB:

1) Install GRUB to MBR. This is done by going into GRUB and executing the following commands:

```

>grub
>root (hd0,1) // this is the partition that contains /boot, if you are not sure execute the following command

grub> find /boot/grub/stage1 // this command will list the partitions that have /boot/grub/stage1 (in your case it will contain only one partition). Specify the resulting partition in the root command above

>setup (hd0)
>quit

```

2) Install GRUB to the /boot partition (You did this already)

3) Make sure the /boot/grub/menu.lst contain the proper root entry

For the above example it would be like the following:

```

title Ubuntu, kernel 2.6.15-26-686
root (hd0,1)
kernel /boot/vmlinuz-2.6.15-26-686 root=/dev/sda3 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-686
savedefault
boot

```

Note that root entry and kernel entries specify different partitions. Root entry specifies the partition that contains /boot where as root parameter of kernel entry specifies the root ("/") partition.

Hope this helps!

---

### Post by KillrBuckeye on 2006-08-06
Thanks for all of your help.  Unfortunately, I'm at a loss here guys.  I have checked and rechecked everything, and I can't find the problem.  As I mentioned, Grub works fine as long as it is started from the floppy or from the LiveCD.  It loads the menu from the menu.lst file on my /boot partition and I can boot up just fine from there.  I even went so far as to wipe the boot sector of the hard drive with a DOS floppy (FDISK /MBR), then rewrite Grub to it via "setup (hd0)" using a bootable Grub floppy.  What else can I do?  :(  I'm beginning to think that the MBR is screwed up somehow.  All I did was copy a partition, delete the old one, and create a new one... maybe something got screwed up then.

PS:  I have only one hard disk, which is /dev/hdb (it's primary slave).  There are 4 partitions.

hdb1 = boot
hdb2 = swap
hdb3 = large storage
hdb4 = Ubuntu root

Grub and the kernal images are on hdb1, and I have my menu.lst kernal entries pointing toward hdb4.  It works great as long as I actually make it to the menu...

---

### Post by vijirajan on 2006-08-06
One last thing you might want to try is to make sure your BIOS is set to boot from your primary slave hard disk by default.

---

### Post by KillrBuckeye on 2006-08-06
Thanks, I tried disabling all boot devices except the one hard drive and got the same error.  I'm completely out of ideas now.  I can continue booting using a Grub floppy, but I'm quite upset that my 2-week-old hard drive seems to have a damaged boot sector now.  If that's the case, I blame GParted, because it was fine before I used that program to change the partitions.  Does anyone know if there's a way I can verify that the boot sector is indeed messed up, or how I could go about repairing it?

---

### Post by KillrBuckeye on 2006-08-07
One more thing.  I found a way to read information from the MBR at the command line.  The information that is returned is mostly garbled (I think that's normal), but I believe there is critical information within some of the strings.  Right after the word "GRUB", I see a "Geom^ Hard^ Disk^ Read^ Error^".  A bit further down, I see "Loading stage1.5" followed by "Geom^ Read^ Error^".  I have attached some of the output below (note strings in bold letters).  

I would really appreciate it if someone with a working Grub in the MBR could paste similar information in this thread to see if those errors are normal (I seriously doubt it).  The command I used to write this information to a file called "strings.txt." is as follows:

```
sudo dd if=/dev/hdb bs=1024 count=1 >strings.txt
```

The contents of the file are shown below:
```
ëH<90>Ð¼^@|ûP^GP^_ü¾^[|¿^[^FPW¹å^Aó¤Ë¾¾^G±^D8,| u^U<83>Æ^PâõÍ^X<8b>^T<8b>î<83>Æ^PIt^V8,tö¾^P^G^C^Bÿ^@^@ ^A^@^@^@^@^Bú<90><90>öÂ<80>u^B²<80>êY|^@^@1À<8e>Ø<8e>Ð¼^@ û @|<ÿt^B<88>ÂR¾^?}è4^AöÂ<80>tT´A»ªUÍ^SZRrI<81>ûUªuC A|<84>Àu^E<83>á^At7f<8b>L^P¾^E|ÆDÿ^Af<8b>^^D|Ç^D^P^@ÇD^B^A^@f<89>\^HÇD^F^@pf1À<89>D^Df<89>D^L´BÍ^Sr^E»^@pë}´^HÍ^Ss
öÂ<80>^O<84>ê^@é<8d>^@¾^E|ÆDÿ^@f1À<88>ð@f<89>D^D1Ò<88>ÊÁâ^B<88>è<88>ô@<89>D^H1À<88>ÐÀè^Bf<89>^Df¡D|f1Òf÷4<88>T
f1Òf÷t^D<88>T^K<89>D^L;D^H}<<8a>T^MÀâ^F<8a>L
þÁ^HÑ<8a>l^LZ<8a>t^K»^@p<8e>Ã1Û¸^A^BÍ^Sr*<8c>Ã<8e>^FH|`^^¹^@^A<8e>Û1ö1ÿüó¥^_aÿ&B|¾<85>}è@^@ë^N¾<8a>}è8^@ë^F¾<94>}è0^@¾<99>}è*^@ëþ**GRUB** **^@Geom^@Hard Disk^@Read^@** Error^@»^A^@´^NÍ^P¬<^@uôÃ^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^A^A^@<83>þ?2?^@^@^@4<80>^L^@^@^@Áÿ^Eþÿÿ½<8a>¶^A^QÛ^S^@^@þÿÿ<83>þÿÿÎeÊ^A<98>åi^X^@þÿÿ<83>þÿÿfK4^Z>^Y§^AUªRV¾^C!è*^A^¿ø!f<8b>-<83>}^D^@^O<84>Ê^@<80>|ÿ^@t>f<8b>^]f1À°^?9E^D^?^C<8b>E^D)E^Df^A^EÇ^D^P^@<89>D^Bf<89>\^HÇD^F^@pPf1À<89>D^Df<89>D^L´BÍ^S^O<82><9f>^@»^@pëVf<8b>^Ef1Òf÷4<88>T
f1Òf÷t^D<88>T^K<89>D^L;D^H}t<8b>^D*D
9E^D^?^C<8b>E^D)E^Df^A^E<8a>T^MÀâ^F<8a>L
þÁ^HÑ<8a>l^LZR<8a>t^KP»^@p<8e>Ã1Û´^BÍ^SrF<8c>Ã<8e>E^FXÁà^E^AE^F`^^Áà^D<89>Á1ÿ1ö<8e>Ûüó¤^_¾^T!è`^@a<83>}^D^@^O<85><ÿ<83>ï^Hé.ÿ¾^V!èK^@Zê^@"^@^@¾^Y!è?^@ë^F¾^^!è7^@¾#!è1^@ëþLoading **stage1.5**^@.^@^M
^**@Geom^@Read^@ Error**^@»^A^@´^NÍ^PF<8a>^D<^@uòÃ^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^B^@^@^@^N^@ ^B


```

---

### Post by vijirajan on 2006-08-07
Those error messages are completely normal. What you are seeing is the program that GRUB installed to MBR. "^@Geom^@Read^@ Error^" is one of the possible error message that GRUB can display in case of an error. This does NOT mean that you have an error.

Before trying other options to fix your issue, lets take a step back and find out what has changed since it stopped working. In your first message in this thread you mentioned you had the new hard disk working for 2 weeks. Can you tell me what has changed in your system since then?

1) Were you running any other OSes in addition to Ubuntu at that time?
2) Did you have more than one hard disk installed at that time?
3) Where was the new hard disk installed? in Primary Master or Primary Slave?
4) Does your BIOS support booting from Primary Slave directly? If not, I would try moving your hard disk to the Primary Master slot if possible (this would require you fix menu.lst and rewrite GRUB to MBR).

---

### Post by Robor on 2006-08-07
I ran into this same error when I did a dist-upgrade from 5.04 to 6.06.  I tried several fixes and workarounds but none of them worked.  I did a fresh install of Ubuntu 6.06 only this time I made sure I created a /boot partition and put it at the front of the hard disk.  This of course broke my Windows bootup and I haven't been able to correct that yet.  

Upgrading shouldn't break things like this.  It's things like this that will likely turn my Ubuntu/XP Pro laptop into 100% Vista later this year.

---

### Post by KillrBuckeye on 2006-08-07
> **vijirajan said:**
> Those error messages are completely normal. 

...

Can you tell me what has changed in your system since then?

1) Were you running any other OSes in addition to Ubuntu at that time?
2) Did you have more than one hard disk installed at that time?
3) Where was the new hard disk installed? in Primary Master or Primary Slave?
4) Does your BIOS support booting from Primary Slave directly? If not, I would try moving your hard disk to the Primary Master slot if possible (this would require you fix menu.lst and rewrite GRUB to MBR).vijirajan, I believe you are right about the error messages being normal in the boot sector.  This leads me to believe that Grub is successfully writing to the MBR, but something in the MBR is still screwed up causing my BIOS to throw the disk error message when it is accessed.  I believe my only recourse at this point in time is to attempt to wipe the MBR clean and rewrite it by following a guide I found:
[http://neosmart.net/blog/archives/14]("http://neosmart.net/blog/archives/14")

I'll try to answer your questions as best I can.

1) This machine has always been running Ubuntu 6.10 only.
2) There has always been only one hard drive installed in the machine at any given time.
3) Both hard disks have always been installed in the primary slave position (except when I copied the contents of the old drive to the new drive using Acronis True Image drive-to-drive copy feature).
4) Yes, the BIOS supports booting from the primary slave, because it had been working fine like this until I encountered the problem with the updated kernal and messed with the partitions.  Further, as a test I swapped out the current HDD for the old one and it loaded Grub and booted just fine.

I believe I know when/where things went sour with my MBR.  When I first encountered the problem of Grub not being able to find the menu.lst file (since it was past cylinder 1024 on the HDD), I followed the advice of others to create a separate /boot partition at the beginning of the drive.  For this task I used GParted from the Ubuntu LiveCD, but things were a little messy because GParted doesn't let you move the beginning of a partition.  Initially, my drive was partitioned as follows:

- hdb1: ext3 Ubuntu root partition (included /boot and /home    
        directories)
- hdb2: Linux swap partition
- hdb3: Large ext3 partition for data storage (no system files 
        here)
- Unused space at the end

Since GParted wouldn't let me simply move hdb1 to create room at the beginning of the disk for another partition, I used the "Copy" feature to copy it to the end of the disk (in the unused space).  I now had 4 partitions on the disk.

Next, I deleted the hdb1 partition (original Ubuntu partition), and in its place created a ~500 MB ext3 partition for /boot.  After these changes were applied, my partitions were reported as follows:

- hdb1: Small ext3 partition for /boot    
- hdb2: Linux swap partition
- hdb3: Large ext3 partition for data storage (no system files 
        here)
- hdb4: Ubuntu root partition

Ever since these changes were applied, I have not been able to boot from the hard drive.  This leads me to believe that these operations screwed up the MBR somehow.  Maybe the partition table was written incorrectly or the new partition I created at the beginning of the disk blew away part of the MBR?  All I know is that every time I have used GParted to manipulate partitions, something has gone terribly wrong...

---

### Post by KillrBuckeye on 2006-08-08
UPDATE:

I gave up and wrote zeros to the drive, reinstalled Ubuntu, and I got the same DISK BOOT FAILURE. At this point I started suspecting a BIOS problem, so I attached the drive to another computer and tried booting from it. Sure enough, Grub loaded and it started booting with no problems!

I think I screwed up the BIOS when I tried to flash it with the HP utility, but I got a message saying that it couldn't proceed with the flash (can't remember the reason, something about a process being active?). Anyhow, I didn't think any harm was done to the BIOS, but ever since then I can't boot from my 250GB drive. Note that my old 16GB drive boots fine.

Okay, so what can I do now? Assuming the BIOS is now operating in some other mode (somebody mentioned CHS mode in another forum), is there anything I can do to work around this? Can I set the HDD parameters manually in the BIOS? I have no idea what any of these parameters mean. Any help would be appreciated.

---

