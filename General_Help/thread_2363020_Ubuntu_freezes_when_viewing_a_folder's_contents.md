---
title: "Ubuntu freezes when viewing a folder's contents"
date: 2017-06-05
forum: General Help
---

### Post by aiesileum on 2017-06-05
Hello everyone,

I'm posting here because some Google searching only returned results related to trying "freezes when trying to copy a large file" - which isn't the issue that I'm having.

When I was making backups of my music files yesterday, the process froze my compute at one point - with one exception: the mouse. Googling on a laptop while it was frozen, I came across an askubuntu answer that said that the mouse being able to move is deceptive: the OS (Ubuntu 16.04, recently used sudo apt-get update && upgrade) is simply frozen.

Thinking it might be related to a specific folder, I rebooted (via holding down the power button until shutdown, then restarting the computer), navigated tot he last folder that was in process, and tried copying it again. Again, it froze.

I rebooted again, and this time opened the folder to sort through the files list to see if anything would tip me off to a problem. Mysteriously, the OS froze while simply looking through the file list. None of the files are large files (all are under 10MB). All of them are music files. 

The only thing that I noticed was that some of the files didn't have icon (instead, they displayed the "clock"/"in processing" preview icon).

Does anyone have an idea as to what's going on? I'm currently using the computer that's been freezing, so it seems to work fine if I'm not viewing folder contents. The "Files" browser About shows version 3.14.3.

I'm going to try turning off previews in Nautilus and see if that changes anything.

---

### Post by LastDino on 2017-06-05
Its usually the number of files rather than size that can make it complicated and lengthy process. As I imagine you might have many Music files, have you tried using command prompt approach to copy?

 Also, bit info about hardware would help, along with exact OS version (you did mention 16.04 but that was in Ubuntu answer post quote)

---

### Post by aiesileum on 2017-06-05
The sub-folder has 109 files. I just rebooted after attempting the "no Preview" thing. I'm able to view the files list now, but attempting to copy files from that folder still causes a system freeze, so I think it has something to do with trying to "read" a specific file. Is there a tool that I can use to check for files that would cause this, or Solid State Drive areas that are broken? (due to corruption, etc?)


**Edit @ xx::44** -> There's a file listed as 57kb on my external drive and 1.9mb on my SSD. Attempting to copy that specific file from the SSD to the external HDD causes a freeze. Now I'm interested in knowing what the reason might be.



lsb_release -a results


LSB Version:    core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

---

### Post by LastDino on 2017-06-05
That is odd behavior for file, is it music file or something else? 

you can check it by doing following,

Here first browse to the file location from your terminal, type ```
ls -l
``` then type ```
file filenamewithextensionasshowninls
```

example
```

owl@owl-Lenovo-E40-80:~$ ls -l
total 44
drwxr-xr-x 4 owl owl 4096 Jun  5 15:55 Desktop
drwxr-xr-x 2 owl owl 4096 May 19 04:43 Documents
drwxr-xr-x 3 owl owl 4096 Jun  5 16:52 Downloads
-rwxrwxr-x 1 owl owl   61 May 22 17:33 hello.sh
drwxr-xr-x 2 owl owl 4096 May 19 04:43 Music
drwxr-xr-x 2 owl owl 4096 Jun  5 18:31 Pictures
drwxr-xr-x 2 owl owl 4096 May 19 04:43 Public
drwxrwxr-x 3 owl owl 4096 May 24 00:22 R
drwxr-xr-x 2 owl owl 4096 May 19 04:43 Templates
drwxr-xr-x 2 owl owl 4096 May 23 17:06 Videos
drwxrwxr-x 7 owl owl 4096 May 20 13:05 VirtualBox VMs
owl@owl-Lenovo-E40-80:~$ file hello.sh
hello.sh: Bourne-Again shell script, ASCII text executable


```


Lets see where this goes

---

### Post by aiesileum on 2017-06-05
This resulted in the OS freezing upon entering the command. I left it alone for 20 minutes and came back to find it still frozen.

Two hours ago I tried running badblocks to see what would come up. The OS also eventually froze in that scenario, and I left it alone for 40 minutes after that. My badblocks.txt didn't have any content after reboot.

I'm going to try it again and leave the System Monitor running on the "Processes" tab. Maybe I'll get lucky and the chart will give some kind of hint pre-freeze.


**Edit**: No hints whatsoever. CPU core usage stayed at 2% 4% 12.6% and 7.8% from terminal open to freeze. RAM use stayed at 1GB out of 3.8 GB. No blip occurred that would change the chart.

---

### Post by LastDino on 2017-06-05
ls is one of the most basic Linux commands and hardly requires any system effort. 

I'm starting to wonder if this is something to do with the corrupt file fragments and probable problem with SSD. 

Try with SMART and see if it reports any error. If it doesn't try updating firmwares (of SSD) and at last resort go with format of OS if it is on SSD and SSD.

---

### Post by Bashing-om on 2017-06-05
aiesileum; Hi !

Might be of interest here to know that the file system is consistent .
From a liveDVD(USB) - so the file system is NOT mounted - run a file system check:
```

sudo parted -l
sudo e2fsck -C0 -p -f -v /dev/sda1

```
replace "sda1" with the target partition as indicated from the parted output .

Then we can continue to examine the file(s) and find the root cause .

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by aiesileum on 2017-06-07
Last night I tried running a SMART test while logged in, and then tried badblocks and e2fsck from a LiveCD, and all of those processes resulted in freezing up. If I ignored the SSD and used the LiveCD for everything, I had no issues. I'm currently using an old HDD with 16.04 installed on it (last night), and I'm having no issues. 

I just tried to access the SSD to grab files from it, but after I enter the encryption password, I get an Operation canceled message, and then the SSD disappears from lsblk and fdisk -l.

**Edit**: Also, the icons for the SSD (120GB, 511MB) look different. [https://drive.google.com/open?id=0BymMsA6ul0r6VEluX0gzQTBfeGc](https://drive.google.com/open?id=0BymMsA6ul0r6VEluX0gzQTBfeGc)

Disk /dev/sdd: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x7ea260f8

Device     Boot   Start       End   Sectors   Size Id Type
/dev/sdd1  *       2048    999423    997376   487M 83 Linux
/dev/sdd2       1001470 234440703 233439234 111.3G  5 Extended
/dev/sdd5       1001472 234440703 233439232 111.3G 83 Linux

---

### Post by LastDino on 2017-06-07
It seems that you might be soon running into mishap with that SSD (if already haven't). I fear it can die any time. If under warranty, check with the vendor.

---

### Post by aiesileum on 2017-06-07
Another attempt just got "Error unlocking /dev/sdd5: Command-line `cryptsetup luksOpen "/dev/sdd5" "luks-b21eb60b-6535-4329-a81a-02b4adfac38b" ' exited with non-zero exit status 1:"

I think it's dead, Jim.

---

### Post by LastDino on 2017-06-07
Just in case I would check with the other computer with different OS as well.

---

### Post by Bashing-om on 2017-06-07
aiesileum; Well - not -

Additional thoughts :
I too had issues getting a SSD functional on old hardware . All happy at this time.
What I had to do was enable AHCI in bios - ATA and write errors !; and
I also have a nvidia card that I have to run the proprietary graphic's driver with - else the system experiences unexplained freeze incidents .on the SSD - hard drive installs have no problems with the nouveau/mesa drivers . imagine that .

[INDENT][INDENT]maybe this
[INDENT][INDENT][INDENT]might be that
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

