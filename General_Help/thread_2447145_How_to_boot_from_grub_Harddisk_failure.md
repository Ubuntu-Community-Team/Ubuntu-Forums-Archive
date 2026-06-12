---
title: "How to boot from grub? Harddisk failure?"
date: 2020-07-13
forum: General Help
---

### Post by s-ett on 2020-07-13
So, I have a laptop where I dualboot Xubuntu and Windows 10, but Xubuntu boots by default. But suddenly I get grub command line instead when I boot! I also see that if I boot Windows 10 instead, Windows is unable to shut down the computer, instead it seems to just reboot (so maybe this is a hardware issue?)

Using ls in GNU Grub 2.02 I see that I have hd0 and hd0,gpt1-7. And an error: failure reading sector 0x801 from `hd0'.

gpt 7 is lost+found and my home directory (my files are still there it seems) 
ext2 file system

gpt6 is /, the root
ext2

gpt1-5 is unknown. 
gpt1 gives the same error message again when using ls (hd0,gpt1), except it is sector 0x802

I was able to start loading the kernel, but then there was something with initframfs (if I remember correctly) I didn't understand

How do I fix this without breaking anything?

---

### Post by oldfred on 2020-07-13
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Did Windows do an update & both reset itself to first in boot order & turn fast start up back on.
Make sure fast start up is off.

Can you boot recovery mode from grub menu? Second entry.

Do you have good backups?
If not do that first.

---

### Post by s-ett on 2020-07-13
Ok, so I download and boot the Boot-Repair to get the report, but it won't autofix anything? Or do you mean a Xubuntu installation image? 

Not sure what happened. The problem seem to have started when suddenly Windows was booting. Not sure what caused that, I haven't been using Windows for a while. It's possible I hit a key that made it change to Windows during booting.


No idea how to boot recovery mode


Too long since I've done any backups. I suppose I can just boot from USB and backup first, but I'd ideally prefer to not do a clean install if possible

---

### Post by ajgreeny on 2020-07-13
If you still have the USB or DVD that you used to install the system boot to that, install the boot-repair package from the PPA, as mentioned by oldfred, and in my signature below and follow the instructions there to run the Boot-Info-Script.	

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and may tell us all that's needed to get you up and running again..

---

### Post by s-ett on 2020-07-13
Ok, and it doesn't matter if the USB files I'll be booting are from 2018?

---

### Post by oldfred on 2020-07-13
As long as it is a current version, like 18.04 LTS, but not 18.10 or other EoL versions.
Otherwise create a new flash drive from download of current ISO.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

But it sounds like Windows updates reset some things.
Windows also can update UEFI and that usually restores many UEFI settings to defaults. So also check those. I have to keep a list.

---

### Post by s-ett on 2020-07-14
[https://pastebin.com/DfybLg7m](https://pastebin.com/DfybLg7m)


Weird, it said I need to enable legacy mode, but both Windows and Xubuntu should be in UEFI mode. I did not notice any BIOS settings changing. The Ubuntutest boot option was just me trying to see if I could fix the problem

---

### Post by oldfred on 2020-07-14
Boot-Repair did not see your ESP - efi system partition, so that is why it suggested a BIOS/Legacy/CSM install of grub. Do not do that.

Your sda1 is not shown & files in it are not shown.
But UEFI shows boot entry for some ESP partition. 
Fstab shows sda1 as the ESP.
Fdisk shows from partition table that sda1 is/was ESP.

But no files nor internal info was shown for sda1, as if it had been erased, but partition table not updated?
Can you manually mount sda1 as FAT32/vfat and see files?

First try dosfsck. Must be unmounted when you run this.
sudo /sbin/fsck.vfat -V <the fat32 device>
sudo fsck.vfat -t -a /dev/sda1
man dosfsck

If we have to totally recreate the ESP, you then have to totally reinstall grub boot loader and Windows boot loader and delete old UEFI entries that have old GUID in them. UEFI uses GUID of ESP to know which partition to find the efi boot files.

---

### Post by s-ett on 2020-07-15
GParted showed reading errors from sda1 too. And said it has no file system.

Trying fsck.vfat -V I get 'Read 512 bytes at 0:Input/output error'

fsck.vfat -t -a -v gives the same

Is the partition totally broken?

---

### Post by s-ett on 2020-07-15
badblocks found 4 bad blocks on sda1, (4/0/0 errors)

Edit: I think it said 0 1 2 3

---

### Post by s-ett on 2020-07-15
And running sudo badblocks -v /dev/sda I got this.... so my harddisk is already ruined? 
> [SIZE=1]
[/SIZE][SIZE=3][SIZE=1]Checking blocks 0 to 976762583
Checking for bad blocks (read-only test): 1024
1025
1026
1027
476010632
476010633
476010634
476010635
481332520
481332521
481332522
481332523
481332964
481332965
481332966
481332967
514029876
514029877
514029878
514029879
519273124
519273125
519273126
519273127
done                                                 
Pass completed, 24 bad blocks found. (24/0/0 errors)[/SIZE]
[/SIZE]


---

### Post by oldfred on 2020-07-15
In Disks and icon in upper right corner is Smart Status.
What does that say about drive.

A few bad blocks is somewhat normal, but a increasing number is drive failure.

---

### Post by s-ett on 2020-07-15
It says: Disk is OK, 48 bad sectors. All SMART Attributes are marked as either old-age or pre-fail though, so I presume it won't be OK much longer. I'm running a self-test now just to see what it says.

I already backed up everything I think is important. But is there a way to see what files are potentially damaged?

Here's how it looks like[URL="https://i.imgur.com/nRhYJWn.png"]
https://i.imgur.com/nRhYJWn.png[/URL]




Finished the extended test now, and it said it failed

---

### Post by s-ett on 2020-07-20
Anyone knows?

---

### Post by dragonfly41 on 2020-07-21
Since I don't know the answer (some time since I experienced a bad HDD and I now use SSD) a simple google search found this ..

[https://superuser.com/questions/247419/how-to-quickly-get-a-list-of-files-that-have-bad-sectors-blocks-clusters-whate](https://superuser.com/questions/247419/how-to-quickly-get-a-list-of-files-that-have-bad-sectors-blocks-clusters-whate)

which refers to ddrescue to scan.

---

### Post by oldfred on 2020-07-21
TheFu posted this which explains some of HDD failure modes.
 What a Failing HDD looks like
[https://ubuntuforums.org/showthread.php?t=2446974](https://ubuntuforums.org/showthread.php?t=2446974)

---

### Post by s-ett on 2020-07-23
Since most of the errors were from the NTFS partition, I tried chkdsk with Windows first, here's the result
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]https://pastebin.com/p8pYwYyM
I'll keep trying to fix things, including the stuff you said. Or do you think I have to replace it anyway?
[/FONT]

---

### Post by oldfred on 2020-07-23
When a drive starts to look a bit flaky or is more than a few years old, I demote it to one of my backups.
I do not have the high end drives like TheFu discusses, just regular consumer grade. And even if a 5 yr warrantee, I often upgrade to a new drive. Lately been adding SSDs as my new faster replacements. 

Backups still important whether drive is old or new. 

With HDD, the deleted/changed data is often still there and recoverable with various tools. But SSDs run trim and that in effect housecleans all old data.

---

