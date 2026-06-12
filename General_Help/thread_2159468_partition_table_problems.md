---
title: "partition table problems"
date: 2013-07-03
forum: General Help
---

### Post by sid0972 on 2013-07-03
i was installing a flavor of ubuntu in my laptop, when i encountered a problem

"Partition table entries are not in order".
I have read solutions to this online but they were completely out of my grasp, i understood nothing, at all.

Can anyone please tell me the steps, what do i have to do to solve this?

i have highlighted the lines relevant to my hard disk
EDIT: dont know how the image got inverted!!!
[ATTACH=CONFIG]244362[/ATTACH]

---

### Post by sudodus on 2013-07-03
> **sid0972 said:**
> 
"Partition table entries are not in order".

That is a comment, not an error message. So you can continue to have the partitions like that unless there is some real problem.

---

### Post by sid0972 on 2013-07-03
the problem is i am trying to install it and i cant see the partition i created for installation, in fact i cannot see any partition there
all i can see is hard disk as a single entity, no partitions in it..........

---

### Post by sid0972 on 2013-07-03
EDIT
i can not see the partitions During Installation
other then that i can see the drives in the file manager normally

---

### Post by sudodus on 2013-07-03
> **sid0972 said:**
> the problem is i am trying to install it and i cant see the partition i created for installation, in fact i cannot see any partition there
all i can see is hard disk as a single entity, no partitions in it..........

There is one drive /dev/sda of 160 GB with 3 primary partitions, /dev/sda1 /dev/sda2 /dev/sda3.

There is one extended partition, /dev/sda4.

And inside the extended partition there are 3 logical partitions /dev/sda5, /dev/sda6, /dev/sda7.

And then there is one drive /dev/sdb of 16 GB, I guess your USB boot pendrive, or is it the target drive, where you want to install Ubuntu?

If you want to install Ubuntu into the hard disk drive, you need to
 
1. reformat one of the primary partitions or
2. reformat one of the logical partitions or
3. shrink one of the logical partitions to create space for Ubuntu

Or are you trying a wubi install? This will install Ubuntu into a file (with Ubuntu's file system inside, so you won't notice any extra partition).

So please describe what you have done, and what you want.
- Do you want only Ubuntu or install it alongside Windows?
- Which version (12.04 LTS or ...) and flavour (standard Ubuntu or some flavour Lubuntu, Xubuntu or Kubuntu ...)

It also helps give relevant advice, if you describe your computer: cpu, ram, graphics chip/card

---

### Post by Mark Phelps on 2013-07-03
With all these NTFS partitions, you must be running Windows at present.  What version are you running?

IF it's Win7, go into the Disk Management utility and see what it reports about the partitions.  Make sure they are all Basic volumes, not Dynamic disks.

---

### Post by sid0972 on 2013-07-04
> **sudodus said:**
> There is one drive /dev/sda of 160 GB with 3 primary partitions, /dev/sda1 /dev/sda2 /dev/sda3.

There is one extended partition, /dev/sda4.

And inside the extended partition there are 3 logical partitions /dev/sda5, /dev/sda6, /dev/sda7.

And then there is one drive /dev/sdb of 16 GB, I guess your USB boot pendrive, or is it the target drive, where you want to install Ubuntu?

If you want to install Ubuntu into the hard disk drive, you need to
 
1. reformat one of the primary partitions or
2. reformat one of the logical partitions or
3. shrink one of the logical partitions to create space for Ubuntu

Or are you trying a wubi install? This will install Ubuntu into a file (with Ubuntu's file system inside, so you won't notice any extra partition).

So please describe what you have done, and what you want.
- Do you want only Ubuntu or install it alongside Windows?
- Which version (12.04 LTS or ...) and flavour (standard Ubuntu or some flavour Lubuntu, Xubuntu or Kubuntu ...)

It also helps give relevant advice, if you describe your computer: cpu, ram, graphics chip/card

I have a laptop running win 7, and wanted to install ubuntu 12.04 alongside win 7, so i created a partition for that.
I am not doing a wubi install.

Under win 7 i already had created a partition for ubuntu but when inside ubuntu installer it shows the hard disk as one unit and does not show the partitions 
In file manager it shows the partitions normally

PC specs: Intel atom processor, 1 GB RAM, integrated graphics, 160GB hdd, 

> **Mark Phelps said:**
> With all these NTFS partitions, you must be running Windows at present.  What version are you running?

IF it's Win7, go into the Disk Management utility and see what it reports about the partitions.  Make sure they are all Basic volumes, not Dynamic disks.

Yes i am running windows 7, version is "Starter Edition".
And yeah they are all basic and not dynamic.

---

### Post by sid0972 on 2013-07-04
i referred to this guide here

[http://gparted.sourceforge.net/h2-fix-msdos-pt.php](http://gparted.sourceforge.net/h2-fix-msdos-pt.php)

and i found i have overlapping partitions.

and upon running the command
```
[COLOR=#000000]$ [/COLOR]**sudo parted */dev/sda* unit s print**
```

i get the following result

```
[COLOR=#000000]Error: Can't have overlapping partitions.[/COLOR]
```[COLOR=#000000]

Problem is, i cannot completely understand the solution given there.
i understood the example, but the situation is different in my case, and i know not what is it.....

EDIT: Upon running gparted [GUI], i found my HDD doesnt have a partition table, and when i try to create one, it says "all the data on the hard disk will be erased.
[/COLOR]

---

### Post by sudodus on 2013-07-04
It seems you have real problems, not only what is reported by fdisk ("Partition table entries are not in order"). "Overlapping partitions" means that the partition table is bad and you have problems.

Many questions (to help us all understand the present situation)

- How did you create (try to create) the partition for Ubuntu: I understand you used Windows, so is one of the partitions seen in the attached picture in post #1 intended for Ubuntu? Which one?

- Can Windows still run in the computer?

- Do you have backup of Windows?

- Do you have backup of your personal files (documents, pictures ...)?

If  Windows still runs, but gparted doesn't understand the partition table, I think you might have dynamic partitions, as asked by *Mark Phelps*.

If Windows is borked, you need to restore your system

- from a backup copy
- trying with Testdisk or
- from a Windows install disk or Windows recovery system.

*Edit: Important:* ***If there are personal files without backup in the computer, you should try to recover them before doing anything else***, that might destroy them.

---

### Post by sid0972 on 2013-07-04
I create the partition uaing aomei partition editor under windows, but as of now I have deleted it.
So there are 4 partitions, c drive (windows), recovery, another 200mb partition and 87gb unallocated space.

I can run windows fine, I dont have any important data on it, I can format the whole hard drive if I absolutely have to but dont want to (its original windows).

I checked that its not dynamic, but I can check again, any different method in your mind?

I think if I can create the partition table or get it recognized i can install ubuntu in any partition i want? 
I saw in a post that if I import a txt file containing correct values it gets fixed? 
How can I do that?

---

### Post by sid0972 on 2013-07-04
Solved it! !!!!
I rebuilt the MBR and voila!
I was able to solve it.
thank you very much sudodus for taking time to addreas my problem you were very patient on this one.
Thank you again

---

### Post by sudodus on 2013-07-04
Congratulations :KS

I hope and think that you have a dual boot system now with Windows and Ubuntu.

Please describe which tool you used (and some more details) to solve the problem, because it will help other people with similar problems. And please mark this thread as solved. I think you should still use this workaround:

Open the first post for editing. Go advanced, and change the prefix to SOLVED.

---

### Post by sid0972 on 2013-07-04
I used aoemi partition editor in that we have an option of rebuilding the master boot record.
And yes now I have a dual boot system but I think I will install fedora too, have to get a hang of yum.
Thanks again.

---

