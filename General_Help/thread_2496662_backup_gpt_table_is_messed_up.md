---
title: "backup gpt table is messed up"
date: 2024-04-07
forum: General Help
---

### Post by jgw on 2024-04-07
I started my machine and "backup gpt table is" messed up I think.  It was too fast to really read and then it said that it would use something else to put something into.  So, should I do something to the gtp table or just leave everything the way it is and forget it until there is another problem?

Thank you................

---

### Post by oldfred on 2024-04-07
Best to check.

Use gdisk and verify partitions are correct with p, or v to review issues,  and use w to write the partition table. If not correct just use q to quit. That should update primary, backup & protective MBR. Details:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html) & 

[https://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table/386802#386802](https://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table/386802#386802)
[http://askubuntu.com/questions/446991/gparted-claims-whole-hard-drive-is-unallocated-and-gives-warning-about-gpt-table](http://askubuntu.com/questions/446991/gparted-claims-whole-hard-drive-is-unallocated-and-gives-warning-about-gpt-table)

Change to your drive if not sda.
sudo gdisk /dev/sda
Command (? for help):

---

### Post by jgw on 2024-04-07
I here what it looked like{\```
sudo gdisk /dev/sda
[sudo] password for greg: 
GPT fdisk (gdisk) version 1.0.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Command (? for help): i
Partition number (1-2): 1-2
Partition GUID code: C12A7328-F81F-11D2-BA4B-00A0C93EC93B (EFI system partition)
Partition unique GUID: 268A9422-22A2-4F62-87E0-D14CD63524E0
First sector: 2048 (at 1024.0 KiB)
Last sector: 1050623 (at 513.0 MiB)
Partition size: 1048576 sectors (512.0 MiB)
Attribute flags: 0000000000000000
Partition name: 'EFI System Partition'


```
My sda disk is a 1tb sd disk

Thoughts?

---

### Post by oldfred on 2024-04-07
Please use Code Tags, Easy to add with Forum's Go Advanced Editor & # icon.

You only showed info on one partition, your ESP. 

Do you have good backups of data?
And backup of partition table structure?

It at least did not seem to show error on loading gpt data.

If you do x for experts menu & v for verify does it show anything.
q to exit, or w to write changes.

---

### Post by jgw on 2024-04-08
It keeps telling me that: The backup GPT table is corrupt, but the primary appears OK, so that will be used.

Code Tags, Easy to add with Forum's Go Advanced Editor & # icon  (don't know what this means)

Here is a report on the computer (1tb sd)
```
sudo parted -l
Model: ATA SanDisk SDSSDH31 (scsi)
Disk /dev/sda: 1024GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  538MB   537MB   fat32        EFI System Partition  boot, esp
 2      538MB   1024GB  1024GB  ext4[/HTML]


Boy! I apologize.  I know, exactly what you are talking about - now.  I realize that you may be old but, obviously, more lucky than I who is officially demented.  Anyway.........   (I think this may also be in the report below which I probably should have sent off to the pastebin - sorry)

This is a report on my 'computer' 4tb:
[HTML]Model: ATA HITACHI HUS72404 (scsi)
Disk /dev/sdb: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  4001GB  4001GB  ext4


Model: ATA TOSHIBA MG03ACA4 (scsi)
Disk /dev/sdc: 4001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  4001GB  4001GB  ext4


Error: The backup GPT table is corrupt, but the primary appears OK, so that will
be used.
OK/Cancel? OK                                                             
Model: General UDisk (scsi)
Disk /dev/sdd: 2097GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2097GB  2097GB  fat32              msftdata


Model: VendorC ProductCode (scsi)
Disk /dev/sde: 31.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  31.5GB  31.5GB  primary  fat32        lba

and here is another:
 sudo parted -l
Model: ATA SanDisk SDSSDH31 (scsi)
Disk /dev/sda: 1024GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  538MB   537MB   fat32        EFI System Partition  boot, esp
 2      538MB   1024GB  1024GB  ext4


Model: ATA HITACHI HUS72404 (scsi)
Disk /dev/sdb: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  4001GB  4001GB  ext4


Model: ATA TOSHIBA MG03ACA4 (scsi)
Disk /dev/sdc: 4001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  4001GB  4001GB  ext4


Error: The backup GPT table is corrupt, but the primary appears OK, so that will
be used.
OK/Cancel? OK                                                             
Model: General UDisk (scsi)
Disk /dev/sdd: 2097GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2097GB  2097GB  fat32              msftdata


Model: VendorC ProductCode (scsi)
Disk /dev/sde: 31.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  31.5GB  31.5GB  primary  fat32        lba
```

---

### Post by oldfred on 2024-04-08
Please go back and add code tags.
While I can do it, you need to know how.
Can you not click on the larger Go Advanced box at bottom for a post?
How to use Code tags, # in Forum's advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)
[https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)



gdisk will only show partition(s) based on which ever partition table seems correct.
You have to tell it to write the partition table to get it updated/corrected.
Refer back to instructions in gdisk repair link above.

---

### Post by jgw on 2024-04-09
I added 2 code tags so the two I had are highlighted.  First I deleted the thing to be tagged.  Then I set the code-tag thing and then I inserted the thing I just deleted.  It looks right to me.  What did I do wrong?

---

### Post by oldfred on 2024-04-09
Code tags not HTML code. Or # icon in Advanced.
Often if using Quick Reply which only has quote tags I use those & edit to be code.
If using Quick Reply then[noparse] ```
 at the beginning and 
``` at the end. [/noparse]

---

### Post by jgw on 2024-04-09
Sorry, I screwed up.  Couldn't find the code but went back and found that it was really the #. 

I went to the one that I screwed up but fixing it now is a bit of a problem.  I guess I could edit it, save the pertinent parts, and then delete everything there are start over. 

Do you want me to do that?

---

### Post by oldfred on 2024-04-09
It took me all of a few seconds to change HTML to code.

Back to gpt issue.
Have you done a write w to update gpt partition table with gdisk.
Review gdisk instructions, again.
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
More repair info  use p, v & w to write the partition table. If not correct just use q to quit. :

---

### Post by jgw on 2024-04-10
Here is what system-info had to say on EUFI (Have no idea if its interesting at all):
Current boot mode:   UEFI Firmware mode
   --- SecureBoot Status from 'mokutil':
SecureBoot disabled
Platform is in Setup Mode

There is a lot of reading on what you sent so I will be a while until I return.  

Thank you..................

---

### Post by oldfred on 2024-04-10
You are using UEFI with UEFI Secure boot off.
That is what I use, although some like Secure Boot on and maybe in future I will turn it on.

---

### Post by jgw on 2024-04-11
Do I have to do anything to my UEFI?

then there is GTP.  Apparently I should, first, run "gdisk /dev/sda1"   Which is my 1tb ssd 
That, in theory will tell me what, exactly is wrong which, in turn, will hopefully point me to the next thing to do

Thoughts?

---

### Post by oldfred on 2024-04-11
Its this to see gpt partitions:
sudo gdisk -l /dev/sda

While most tools are partition based, gpt is for the entire drive.

And you run commands per this:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

Use ? to see commands & link for explanations:

```
[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo gdisk /dev/sda [/COLOR]
[sudo] password for fred:  
GPT fdisk (gdisk) version 1.0.8 

Partition table scan: 
  MBR: protective 
  BSD: not present 
  APM: not present 
  GPT: present 

Found valid GPT with protective MBR; using GPT. 

Command (? for help): 


[/FONT]
```

---

### Post by jgw on 2024-04-11
Not sure what to do next.
Tried this (got me nothing):
sudo gdisk ? /dev/sda
GPT fdisk (gdisk) version 1.0.8

Usage: gdisk [-l] device_file

I suspect the one with all the options comes from recovery & transformation menu but not sure.  This stuff makes me VERY careful.  How, for instance, do I get some kind of check which tells me what is wrong and where.  

Thank you..............

---

### Post by oldfred on 2024-04-11
> sudo gdisk ? /dev/sda
Did you actually type ? in command, or typo on post?

---

### Post by jgw on 2024-04-12
Nope the question mark is what I put there.  In theory I think it was supposed to do something.  I also tried -? and got nothing.  

Interesting, I think?

---

### Post by oldfred on 2024-04-12
The question mark is not in the gdisk command, but once in gdisk you can use it to see list of valid commands. ? is not a valid command.
You can use -l that is el, not 1 or cap I as valid command to list partitions.
sudo gdisk -l /dev/sda

```
[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo gdisk /dev/sda [/COLOR]
[sudo] password for fred:  
GPT fdisk (gdisk) version 1.0.8 

Partition table scan: 
  MBR: protective 
  BSD: not present 
  APM: not present 
  GPT: present 

Found valid GPT with protective MBR; using GPT. 

Command[COLOR=#ff0000] (? for help):[/COLOR]  
[/FONT]
```

---

### Post by jgw on 2024-04-22
As far as i can tell I am no longer getting any problems so, it may have cleaned itself up.  I am going to leave it alone unless it comes back and then I will whine.  

On the other hand I have a brand new one now.  When I goto ebay, and choose anything, it goes to another page and then starts blinking and blinking and blinking.  Only seems to happen with ebay.  This one is pretty strange, even mysterious.

---

### Post by oldfred on 2024-04-22
If this issue is solved best to change status to solved. You can do that from first post editing and then at top menu.

And if new issue start a new thread.

---

