---
title: "partitions"
date: 2015-12-02
forum: General Help
---

### Post by cmcanulty on 2015-12-02
I am trying to repartition from the live usb and have an issue. I've done this a lot and never an issue before. See attached screenshot. I want to have 35GB as /, 4Gb as swap, and the rest as /Home. But it won't let me move  /home to right 12 GB so I can add 12GB to /. I think the issue is somehow /sda2 is an extended partition which wasn't what I wanted. I need to preserve the files in /home which is backed up but still don't want to reinstall it.Please advise.

---

### Post by cmcanulty on 2015-12-02
I am trying to repartition from the live usb and have an issue. I've done this a lot and never an issue before. See attached screenshot. I want to have 35GB as /, 4Gb as swap, and the rest as /Home. But it won't let me move  /home to right 12 GB so I can add 12GB to /. I think the issue is somehow /sda2 is an extended partition which wasn't what I wanted. I need to preserve the files in /home which is backed up but still don't want to reinstall it.Please advise.

[ATTACH=CONFIG]265900[/ATTACH]

---

### Post by yancek on 2015-12-02
> But it won't let me move  /home to right 12 GB so I can add 12GB to /

Well, what exactly happens when you try to do this?  Any error messages.  You have very little data on it but if you want to do this, you first unmount sda5 and when you go to the resize option you should see an option asking how much space you want before the partition.  Indicate 12GB which will need to move all the data in the partition so it will take a while.  You would need to do the same with the Extended partition.  This should give you 112GB of unallocated space before the Extended partition which you an use to expand sda1.  Since you are moving data and any time you are modifying partitions, it is pretty risky so you may lose some data.  Having a backup is great but you never know what will happen. Also, I've never done this myself but it seems logical from my understanding of partitioning.

Have you reviewed the GParted Manual on resizing?

  [http://gparted.org/display-doc.php%3Fname%3Dhelp-manual#gparted-advanced-partition-actions](http://gparted.org/display-doc.php%3Fname%3Dhelp-manual#gparted-advanced-partition-actions)

---

### Post by grahammechanical on 2015-12-02
The partitions sda1, sda2 & sda5 all have a key icon against them. They are locked and in that state cannot be resized. Have these partitions been mounted? If gparted is run from a live session then only swap should have the key icon. If swap was in the extended partition (which it is not) then the extended partition would also have the key icon and set swap to swap off would remove the key icons. Which is not the solution in your case.

You need to remove the key icons from sd1, sda2 & sda5.

Regards.

---

### Post by cmcanulty on 2015-12-02
the partitions were in use in the screenhot but when I was using the live usb they weren't mounted. The issue is how to deal with the extended partition to make it smaller.It doesn't behave like an ordinary partition where I could slide the left arrow to the right to make /home 12GB smller, the drag / to to the right to ake up the extra 12GB. Is there a way to convert the extended partition to a normal partition?

---

### Post by yancek on 2015-12-02
The Extended partition can't be changed until you change the logical partition within it.  Did you do that?  You might try a google to see about changing a logical to a primary which you could do as you have only three primaries.  Then you won't need the Extended.  Never done it myself so won't offer any advice.

---

### Post by oldfred on 2015-12-02
Make sure you have good backups. Any partition change has risk. Biggest is user gets impatient and stops system in the middle and then system is totally corrupted. Or power failure in middle of a partition move. Then recovery from backup is only recourse.

You have to resize the logical partitions inside the extended first. Then move logical right to make unallocated at start of extended. Then you can move start of extended to in effect move unallocated out of extended partition. Think of it as the old slide puzzle where you have to  move pieces around to get what you want.

You can relatively easily convert /home to a primary partition, but still have to resize and move right with gparted. Use fixparts and it can let you select partition type changes.
 [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by cmcanulty on 2015-12-03
OK thanks I will try that

---

### Post by cmcanulty on 2015-12-03
OK I installed fixparts and am trying the l option to change the extended sda2 to logical and I get this error, the tutorial says  "To use FixParts, you must launch it and pass it a device filename, as in:
# fixparts /dev/sdc" see the screenshot in previous post for my partitions. What am I doing wrong?The tutorial doesn't say it must be run from live usb maybe it does have to?


```
librarian@dell:~$ sudo fixparts /dev/sda2 -l
[sudo] password for librarian: 
FixParts 0.8.8
Usage: fixparts device_filename
librarian@dell:~$
```

---

### Post by oldfred on 2015-12-03
I would expect you have to run from live installer, so partitions are unmounted. But do not know for sure as it is just editing partition table. Changes to partition table could cause issues with running system depending on changes.

But instructions to not show a -l parameter.

---

### Post by cmcanulty on 2015-12-03
am I misunderstanding the tutorial? Here is the section I was trying to follow

> 
Use the r option to turn a partition into a primary partition, l (that's a letter L, not a digit 1) to turn it into a logical partition

---

### Post by oldfred on 2015-12-04
Those commands are once you have run fixparts.

sudo fixparts /dev/sda

run p command first, then ? to see list of commands
MBR command (? for help):

Only if you save with w command will changes be updated. use q if you get lost and just want to quit without changes.

---

### Post by cmcanulty on 2015-12-04
OK here is the output, do I just from there type 

```
/dev/sda2 -i
```

or

```
sudo fixparts /dev/sda2 -l
```

output

```
librarian@dell:~$ sudo fixparts /dev/sda
[sudo] password for librarian: 
FixParts 0.8.8

Loading MBR data from /dev/sda

Warning: 0xEE partition doesn't start on sector 1. This can cause problems
in some OSes.

MBR command (? for help): 

```

---

### Post by oldfred on 2015-12-04
And this is what you get when running fixparts. 
I now wants its commands, use ? to see commands:

MBR command (? for help):

---

### Post by cmcanulty on 2015-12-04
sorry by I am missing something here. I tried to set sda2 to logical and just get the options 

```
librarian@dell:~$ sudo fixparts /dev/sda
[sudo] password for librarian: 
FixParts 0.8.8

Loading MBR data from /dev/sda

Warning: 0xEE partition doesn't start on sector 1. This can cause problems
in some OSes.

MBR command (? for help): /dev/sda2 -l
a	toggle the active/boot flag
c	recompute all CHS values
l	set partition as logical
o	omit partition
p	print the MBR partition table
q	quit without saving changes
r	set partition as primary
s	sort MBR partitions
t	change partition type code
w	write the MBR partition table to disk and exit

MBR command (? for help): /dev/sda2 l
a	toggle the active/boot flag
c	recompute all CHS values
l	set partition as logical
o	omit partition
p	print the MBR partition table
q	quit without saving changes
r	set partition as primary
s	sort MBR partitions
t	change partition type code
w	write the MBR partition table to disk and exit

MBR command (? for help): 

```

---

### Post by yancek on 2015-12-04
> sorry by I am missing something here. I tried to set sda2 to logical and just get the options 


Why?  That won't work or help your problem at all because in order for a logical partition to exist, it must be inside an Extended partition and sda2 is the Extended partition.  There is nothing on sda2 and the partition you need to first modify is sda5 where your data actually exists.  You should be either trying to change sda5 to a primary or moving everything to the right to create room outside the Extended partition so you will have unallocated space on which to extend the / partition.

---

### Post by oldfred on 2015-12-04
Once you are inside fixparts, you do not use Linux device settings but just the partition number.

Not sure if you say l then it will ask which and reply 2 or vice-versa. What happens if you just type l as it is one of the listed commands.
Instructions are not totally clear. But you are using fixparts, not Linux.

All my currently mounted drives are gpt, so I cannot easily test myself.

---

