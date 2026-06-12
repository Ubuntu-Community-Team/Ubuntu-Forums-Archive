---
title: "Unable to delete files"
date: 2024-12-07
forum: General Help
---

### Post by ewm on 2024-12-07
I recently had to move my Home directory partition to make space for a bigger boot partition. Everything seems to have worked fine but when I run Lucky Backup simulation I get several errors  saying that file structures needs cleaning. The files in question are all in ./local/Trash. I have run fsck and e2fsck and both show file system is clean. I have tried deleting these files i.e moving them to trash but all that happens is that the file reappears with a new name e.g delete file xyz results in a file xyz.1 appearing.
I have a backup of the file system pre partition move but am reluctant to use this before resolving the problem. If I restore my backup will the files I cannot delete still be in the ./local/Trash folder? I also have tried sudo trash-empty but files are still there.
I suppose I could copy all the good files onto another drive then format the /home partition and then copy them back but I am hoping there is a quicker way.
All topics I have found on the web relating to this problem say use fsck but this does not work in my case. Any advice would be appreciated.
using ubuntu 24.04.

---

### Post by yancek on 2024-12-07
> I have tried deleting these files i.e moving them to trash but all that  happens is that the file reappears with a new name e.g delete file xyz  results in a file xyz.1 appearing. 

That is expected behavior.  Sending a file to the user .local/Trash directory again is not the same as deleting them.  If you actually want to delete them you can either use the rm (remove) command in a terminal or highlight the selected file and hold down the Shift + Delete keys and you will be prompted to delete or not delete them.

---

### Post by TheFu on 2024-12-07
Don't use a GUI program to delete them.

This should be safe for everyone to remove their trash from their HOME.
$ rm -rf  ~/.local/Trash/*

But ... Trash is stored by GUI file managers on a per-file system basis, so if you have other file systems and have been using a GUI to delete files, it is likely there is a /mnt/whatever/.Trash/ directory full of junk.  Every night, just before I do backups, I remove all trash from all partitions on my systems.  That means I have until midnight to retrieve any files from trash that I might need.  OTOH, I have daily backups, so if the files deleted are around for 30-60-90+ days, then they will be in a backup set and can be restored.  This assumes YOU have backups - automatic, weekly/daily, versioned, at least.

---

### Post by ewm on 2024-12-08
Thank you for the feed back. I tried $ rm -rf ~/.local/Trash/* and the files are still there. 
I then tried  "highlight the selected file and hold down the Shift + Delete keys " and I get this error -
Error when getting information for file &#8220;/home/me/.local/share/Trash/files/3175676598/MINS 59th AGM 2019.pdf&#8221;: Structure needs cleaning .
As I previously mentioned I have run fsck and e2fsck both of which report files clean.
I do a daily backup of the Home directory using Lucky Backup. I could of course exclude the Trash file in question but I am stumped as far as removing the problem files.

---

### Post by The Cog on 2024-12-08
Let's see exactly what files are in Trash, and which directory they're in. Please post the result of this command and its output:
**[FONT=Courier New][COLOR="#00007F"]find  ~/.local/share/Trash/ -ls[/COLOR][/FONT]**

I suspect they might be in expunged (a place for files that can't be deleted), and owned by root. If that's the case, using **[FONT=Courier New][COLOR="#00007F"]sudo rm ~/.local/share/Trash/expunged/*[/COLOR][/FONT]** should do the trick.

---

### Post by ewm on 2024-12-08
Ok First ran the following command with result as shown

sudo rm ~/.local/share/Trash/expunged/* 
rm: cannot remove '/home/eric/.local/share/Trash/expunged/*': No such file or directory

Result of listing filess
```
$ find ~/.local/share/Trash/ -ls
 13392254      4 drwx------   4 eric     eric         4096 Dec  8 10:30 /home/eric/.local/share/Trash/
 13369989      4 drwx------   2 eric     eric         4096 Dec  8 10:30 /home/eric/.local/share/Trash/info
 13369992      4 -rw-------   1 eric     eric           80 Dec  8 10:30 /home/eric/.local/share/Trash/info/AnyDesk.trashinfo
 13392256     12 drwx------  10 eric     eric        12288 Dec  8 10:30 /home/eric/.local/share/Trash/files
 37883836      4 drwx------   3 eric     eric         4096 Dec  7 12:20 /home/eric/.local/share/Trash/files/3962403877
 13117836      4 drwx------   3 eric     eric         4096 Dec  7 11:00 /home/eric/.local/share/Trash/files/3962403877/Old1
 13894014      4 drwx------   3 eric     eric         4096 Dec  7 11:00 /home/eric/.local/share/Trash/files/3962403877/Old1/.local
 13894015      4 drwx------   3 eric     eric         4096 Dec  7 11:00 /home/eric/.local/share/Trash/files/3962403877/Old1/.local/share
 13894516      4 drwx------   3 eric     eric         4096 Dec  7 11:00 /home/eric/.local/share/Trash/files/3962403877/Old1/.local/share/Trash
 13895472    144 drwx------   6 eric     eric       143360 Dec  7 12:58 /home/eric/.local/share/Trash/files/3962403877/Old1/.local/share/Trash/files
 14816085      4 drwx------   3 eric     eric         4096 Feb 11  2018 /home/eric/.local/share/Trash/files/3962403877/Old1/.local/share/Trash/files/.eteks
 14816086      4 drwx------   2 eric     eric         4096 Dec  7 11:00 /home/eric/.local/share/Trash/files/3962403877/Old1/.local/share/Trash/files/.eteks/sweethome3d

find: &#8216;/home/eric/.local/share/Trash/files/3962403877/Old1/.local/share/Trash/files/.eteks/sweethome3d/work&#8217;: Structure needs cleaning
 15215959      4 drwxrwxrwx   2 root     root         4096 Dec  7 11:00 /home/eric/.local/share/Trash/files/3962403877/Old1/.local/share/Trash/files/Manuals

find: &#8216;/home/eric/.local/share/Trash/files/3962403877/Old1/.local/share/Trash/files/Manuals/Mi_Phone_User_Guide_eng.pdf&#8217;: Structure needs cleaning
 15470027      4 drwx------   3 eric     eric         4096 Dec  7 11:00 /home/eric/.local/share/Trash/files/3962403877/Old1/.local/share/Trash/files/.npm

find: &#8216;/home/eric/.local/share/Trash/files/3962403877/Old1/.local/share/Trash/files/.npm/diff&#8217;: Structure needs cleaning
 15601045      4 drwx------   2 eric     eric         4096 Dec  7 11:00 /home/eric/.local/share/Trash/files/3962403877/Old1/.local/share/Trash/files/.npm/registry.npmjs.org

find: &#8216;/home/eric/.local/share/Trash/files/3962403877/Old1/.local/share/Trash/files/.npm/registry.npmjs.org/aws-sign2&#8217;: Structure needs cleaning
find: &#8216;/home/eric/.local/share/Trash/files/3962403877/Old1/.local/share/Trash/files/.npm/registry.npmjs.org/form-data&#8217;: Structure needs cleaning
find: &#8216;/home/eric/.local/share/Trash/files/3962403877/Old1/.local/share/Trash/files/.npm/object-assign&#8217;: Structure needs cleaning
find: &#8216;/home/eric/.local/share/Trash/files/3962403877/Old1/.local/share/Trash/files/.npm/util&#8217;: Structure needs cleaning
find: &#8216;/home/eric/.local/share/Trash/files/3962403877/Old1/.local/share/Trash/files/.npm/formatio&#8217;: Structure needs cleaning
find: &#8216;/home/eric/.local/share/Trash/files/3962403877/Old1/.local/share/Trash/files/.npm/timers-browserify&#8217;: Structure needs cleaning
 15732891      4 drwxrwxrwx   3 root     root         4096 Dec  7 11:00 /home/eric/.local/share/Trash/files/3962403877/Old1/.local/share/Trash/files/.mozillabackup
 15732894      4 drwx------   3 eric     eric         4096 Dec  7 11:00 /home/eric/.local/share/Trash/files/3962403877/Old1/.local/share/Trash/files/.mozillabackup/firefox
 15732903      4 drwx------   3 eric     eric         4096 Dec  7 11:00 /home/eric/.local/share/Trash/files/3962403877/Old1/.local/share/Trash/files/.mozillabackup/firefox/lmp24b0n.default-1465596900734-1501173239188
 20583370      4 drwx------   3 eric     eric         4096 Dec  7 11:00 /home/eric/.local/share/Trash/files/3962403877/Old1/.local/share/Trash/files/.mozillabackup/firefox/lmp24b0n.default-1465596900734-1501173239188/storage
 22289223     48 drwx------   2 eric     eric        45056 Dec  7 11:00 /home/eric/.local/share/Trash/files/3962403877/Old1/.local/share/Trash/files/.mozillabackup/firefox/lmp24b0n.default-1465596900734-1501173239188/storage/default

find: &#8216;/home/eric/.local/share/Trash/files/3962403877/Old1/.local/share/Trash/files/.mozillabackup/firefox/lmp24b0n.default-1465596900734-1501173239188/storage/default/https+++www.google.com^partitionKey=%28https%2Cloot.co.za%29&#8217;: Structure needs cleaning
 13108089      4 drwx------   2 eric     eric         4096 Dec  7 11:00 /home/eric/.local/share/Trash/files/2484184567

find: &#8216;/home/eric/.local/share/Trash/files/2484184567/Halloweenpeanuts.jpg&#8217;: Structure needs cleaning
 13107420     16 drwx------   2 eric     eric        16384 Dec  7 11:00 /home/eric/.local/share/Trash/files/3175676598

find: &#8216;/home/eric/.local/share/Trash/files/3175676598/MINS 59th AGM 2019.pdf&#8217;: Structure needs cleaning
 15597612      4 drwx------   3 eric     eric         4096 Dec  7 11:00 /home/eric/.local/share/Trash/files/2024626015
 15859854      4 drwx------   2 eric     eric         4096 Dec  7 11:00 /home/eric/.local/share/Trash/files/2024626015/Final\ Maps

find: &#8216;/home/eric/.local/share/Trash/files/2024626015/Final Maps/Aerial Views Artifacts&#8217;: Structure needs cleaning
 18748756      4 drwx------   2 eric     eric         4096 Dec  7 10:05 /home/eric/.local/share/Trash/files/3203557833

find: &#8216;/home/eric/.local/share/Trash/files/3203557833/661e5dcb-407d-85b2-4bc87274-4c1c1ee5.extra&#8217;: Structure needs cleaning
 13107637     12 drwx------   2 eric     eric        12288 Dec  7 11:00 /home/eric/.local/share/Trash/files/748432960


find: &#8216;/home/eric/.local/share/Trash/files/748432960/jeanacc.jpeg&#8217;: Structure needs cleaning
 15086550      4 drwx------   2 eric     eric         4096 Jun 22 09:17 /home/eric/.local/share/Trash/files/AnyDesk
 20054081      4 drwx------   2 eric     eric         4096 Dec  7 11:00 /home/eric/.local/share/Trash/files/305902959.2

find: &#8216;/home/eric/.local/share/Trash/files/305902959.2/nid response erf 3488.pdf&#8217;: Structure needs cleaning
eric@mycomputer:~$
```

---

### Post by TheFu on 2024-12-08
Looks like you need to boot from a flash drive with a Linux ISO and run **fsck** on all the Linux file systems in the box.  The same flash drive you used to install the OS with that ISO is fine.

File system errors never get better, only worse.

The other option is to wipe this file system/partition, reformat it, and restore from backups.  That assumes you keep /home in a separate file system from the OS, /.

---

### Post by ewm on 2024-12-08
Thanks again, I have already tried using live iso and tried several of the options but e2fsck says there are files with errors but does not fix them. If I run fsck it reports file system as clean. I guess I will have to go the format partition root. Yes my Home directory is on a separate partition from the OS. and I had made a backup before I did my partition resize. I will make another backup of the system as is on another drive just in case.

Thanks everybody for your advice.

---

### Post by TheFu on 2024-12-08
Be certain to run some SMART tests and the report before doing too much more.  Wouldn't be good to waste time on a failing HDD or SATA SSD.  If it is an NVMe SSD, use the nvme command with the smart-whatever option to get the information on failing areas.

---

### Post by oldfred on 2024-12-08
I am seeing this: drwx------
Try:
sudo chmod -R a+rwX [B][FONT=Courier New][COLOR=#00007F]~/.local/share/Trash
Never run on / folders particularly with -R which is recursive.

It looks like you have folders within folders.
[/COLOR][/FONT][/B]

---

### Post by yancek on 2024-12-08
From post 4 you show the below output which is incorrect and should be "/home/eric/.local/share/Trash/".  What happened when you highlighted a file and did Shift+Delete?

>  rm -rf ~/.local/Trash/* and the files are still there 

I don't know why you have a duplicate path or how that happened, shown below and referred to by oldfred.

> /home/eric/.local/share/Trash/files/3962403877/Old1/.local/share/Trash/files/.eteks/sweethome3d 

---

### Post by TheFu on 2024-12-08
> **yancek said:**
>  I don't know why you have a duplicate path or how that happened, shown below and referred to by oldfred.

I suspect the OP tried to use a GUI to delete the files again, causing a little recursion.  Most file managers have an "Empty Trash" - or some locally appropriate term, in the file manager to clean the trash bins.  Don't know if anyone already suggested using this or not.

---

### Post by The Cog on 2024-12-08
According to man e2fsck, you need to use a **-p** flag (for preen, apparently) in order to actually fix the problems found. The man page does say that repairing is optional.
sudo e2fsck -p /dev/whatever

---

### Post by ewm on 2024-12-08
Tried your suggestion and get this result
chmod: cannot access '/home/eric/.local/share/Trash/files/2484184567/Halloweenpeanuts.jpg': Structure needs cleaning

---

### Post by ewm on 2024-12-10
I have made a backup on another drive and excluded the udeletable files in the Trash will restore from this drive and hopefully the problem will be solved. Thanks again for all the suggestions.

---

