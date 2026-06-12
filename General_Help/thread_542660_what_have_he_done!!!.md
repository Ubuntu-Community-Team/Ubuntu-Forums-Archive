---
title: "what have he done!!!"
date: 2007-09-04
forum: General Help
---

### Post by samee on 2007-09-04
i was told that the best way to remove Ubuntu was to format the ubuntu partitions and restart the computer and vista should load. but as it seems i cannot even boot my computer up any more.

the computers HDD is formatted to to parts 3 parts now:
1 vista partition
1 data storage partition
and another partition where its just lying there as it was the Ubuntu partition and he also has combined them to 1 partition to form a total of three partition on my hdd

when ever i try to boot up the computer it says 
 searching for boot record from floppy...NOT FOUND
 searching for boot record from IDE-0... OK
Loading GRUB V1.5 

when it gets to loading GRUB it keeps restarting it self and is getting quite annoying.
 
i dont want to reformat the hdd because i have vital data on it. and any other suggestions on what i should do please reply ASAP. thanks in advance.

---

### Post by tonym on 2007-09-04
Looks like Grub is installed on the MBR and is trying to access the partition you scrubbed.  If you are only going to use Vista you need to boot from the Vista CD and rewrite the MBR.

---

### Post by samee on 2007-09-04
how do I rewrite the MBR?

---

### Post by expatCM on 2007-09-04
but quite why anyone would run Vista instead of Ubuntu is a bit beyond me

---

### Post by Steve1961 on 2007-09-04
> **samee said:**
> how do I rewrite the MBR?

Boot from the vista DVD/CD and enter the option that takes you to the where you can repair an existing installation.  Open the comand line interface (there's an icon for this) and type:

bootrec /fixmbr

---

### Post by samee on 2007-09-04
i have booted from the vista cd and click repair after doing so i was given lots of options like:

startup repair
system restore
memory diagnostics
command prompt

i click *command prompt as Steve1961 as requested me to do so*and typed "bootrec /fixmbr" and said the command has completed successfully. and to see if the changes have taken effect i restarted the pc and would not boot.

i then reinserted the cd and clicked "startup repair" but did not show my OS i then click next and it started to reapir and the results are as follows:

Diagnostics repair information

startup repair diagnostics and repair log 
-------------------------------------------------------------
numbers of repairs: 1

sessions details
-------------------------------------------------------------
systemdisk= \Device\harddisk0
windows recovery=
autoChk Run= 0 
Number of root causes= 1

Test performed
---------------------------------------
Name: check for updates
result: completed successfully. errorcode= 0X0
time taken= 0ms

test performed
---------------------------------------------------------
Name: system disk test
result: completed successfully. errorcode= 0X0
time taken= 16ms

test performed
---------------------------------------------------------
Name: disk meta test
result: completed successfully. errorcode= 0X0
time taken= 0ms

root cause found:
--------------------------------------------------------
the partition table does not have a valid system parition

Repair: partition table repair
result: completed successfully. errorcode= 0X0
time taken= 181406ms

-----------------------------------------------------
-----------------------------------------------------

---

### Post by Steve1961 on 2007-09-04
OK, boot the vista cd again and go to the command prompt.  Try these commands:

bootrec /fixmbr
bootrec /fixboot
bootrec /RebuildBcd

---

### Post by samee on 2007-09-04
i have tried the following commands
bootrec /fixmbr
bootrec /fixboot
bootrec /RebuildBcd

and results are as follows:

test with bootrec /fixmbr = the command has completed successfully
test with bootrec /fixboot = element not found
tets with bootrec /RebuildBcd = scanning all disks for windows installation. 
please wait, sine this may take a while...
successfult scanned windows installations.
total identified windows installations: 0 

the operation completed successfully.

---

### Post by Steve1961 on 2007-09-04
Looks like the vista partition is well and truly screwed.  Can you boot with a live cd to access the vista partition and drag any important files of it onto a usb key/hard drive?  If so, my advice would be to do that then reinstall vista.

---

### Post by cunninghamja on 2007-10-09
I hope I am not too late. I just had this type of problem when I installed Grub with opensuse 10.3. My system is a Toshiba A215 S4767. I got things working again when I slowed down to think about it. Toshiba has a hidden partition for its own file. Well long story short, the partition table from the opensuse install was broke. I booted the Vista disc, went to the command prompt, ran diskpart, made the toshiba partition inactive, made the vista partition 'active', then I did the bootrec /fixmbr bootrec /fixboot. All is now working. If I am too late, maybe this will help someone later before they think their system is hosed. I will still try a dual boot with Gutsy when it comes out. Vista is Ok, but it seems everything has to be done the hard way. M$ really worked on this one.

---

### Post by diordna on 2008-03-25
> **cunninghamja said:**
> I hope I am not too late. I just had this type of problem when I installed Grub with opensuse 10.3. My system is a Toshiba A215 S4767. I got things working again when I slowed down to think about it. Toshiba has a hidden partition for its own file. Well long story short, the partition table from the opensuse install was broke. I booted the Vista disc, went to the command prompt, ran diskpart, made the toshiba partition inactive, made the vista partition 'active', then I did the bootrec /fixmbr bootrec /fixboot. All is now working. If I am too late, maybe this will help someone later before they think their system is hosed. I will still try a dual boot with Gutsy when it comes out. Vista is Ok, but it seems everything has to be done the hard way. M$ really worked on this one.

NICE !


diskpart ! da solution :)

Thank you !

---

