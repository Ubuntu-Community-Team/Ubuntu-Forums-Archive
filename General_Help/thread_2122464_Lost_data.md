---
title: "Lost data"
date: 2013-03-05
forum: General Help
---

### Post by ThulasiS on 2013-03-05
Hi All
"For Every Problem there will be a Solution" (Hoping So)
I am very new to Linux but know very few commands and regular user of Windows. Since my windows making some troubles in booting from last two months and for my research purpose I require linux to run some software, I decided to install Ubuntu 12.10 (Latest available Version). Yesterday I installed it by replacing Windows where I thought It'll format only C drive like during installation of Windows. Later I understood that was my misunderstanding. Now I was unable to find the drivers like in Windows and unable to see my Data in other drives like D and E. How can I get it back and How can I see drivers like in windows. Please help me in getting my Files back if possible. I am losing my one year Research data. Please help me if you can.

Thank you

- Tulasi

---

### Post by varunendra on 2013-03-05
Welcome to the forums ThulasiS,

First of all, avoid using that drive to avoid further damage to the data.
Follow this guide and let us know if you are having any problem in understanding or following it : [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by grahammechanical on 2013-03-05
I am assuming that "drivers" = Drives. Yes? In Windows hard disk drives and partitions on those drives are labelled C:, D:, E: and so on. But in Linux drives and partitions are labelled  sda1, sda2, sda3, and so on. Sata Drive A = sda. The first partition on the first hard drive = sda1. The second partition on the first hard drive = sda2. And so on. Second hard drive = sdb. Third hard drive = sdc. And so on.

Open the File Manager (called Nautilus). It is called the Home Folder in the Launcher (panel on the left of the screen). In File Manager there is a panel on the left and a heading called Devices. Those partitions or drives that you call D and E will be listed there. They may be called Volumes or File Systems. 

Regards.

---

### Post by raja.genupula on 2013-03-05
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by ThulasiS on 2013-03-05
Ya exactly.It is a Machine..Nice quote

---

### Post by Tiles on 2013-03-05
Okay, I just did the same as this topic writer, and having the same problem.
grahammechanical : I tried looking at your opinion, but didn't work.
I did try to boot with my windows DVD to check my HDD. but the result was shocking that I saw most of my hard in 1 partition and only 4 gbs is the other partition "both were full"

---

### Post by Tiles on 2013-03-05
Any help around? this is confusing !!

---

### Post by varunendra on 2013-03-05
> **Tiles said:**
> Any help around? this is confusing !!

Follow the link in my previous post.

---

### Post by Tiles on 2013-03-05
Been doing that for a while, I can't launch the program, no clue why !!

---

### Post by Tiles on 2013-03-05
Still can't run it, I click on Testdisk_Static, but nothing !!

---

### Post by varunendra on 2013-03-05
It is a commandline program that needs to be run from terminal. Also, it is not already installed by default, so you need to install it first. It is very small and can be easily installed and run from the live session (running off a live cd/dvd/usb)

While in Ubuntu, make sure you are connected to internet. Then open a terminal (ctrl + alt + T) and run the following commands -
*(Please note that **sudo** will not ask for password if you are running a live session. In installed one, it will ask for password. You won't see anything on the screen while typing the password. Just type the one you use for login and press Enter)*

```
sudo apt-get update
sudo apt-get install testdisk
```

Let the installation finish. Then run -
```
sudo testdisk
```

Then proceed from the step with "[Log Creation]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Log_creation")" screenshot on the page I linked to.

It is not very uncommon for new users to get confused with that tutorial. So feel free to ask here wherever you are having problem with it.

---

### Post by Tiles on 2013-03-05
I did all that, after the deep search it showed me all the partitions, but when I pressed "Enter" it said no data to recover and I went back to main menu, does that mean it's unrecoverable or I just need to do deep search again ?

---

### Post by varunendra on 2013-03-05
Can you post an screenshot where it showed all the partitions after deep search ? Listing of partitions means testdisk found them and can recover them.

As mentioned on the guide page, you can highlight a partition and press **p** to see the folders/subfolders/files in it to verify if it is the correct partition. Once you are satisfied, you may return on the partition listing screen by pressing **q**, then use **Left/Right** arrow keys to change the partition type from **D** (deleted) to **P** (primary) or **L** (logical) as applicable. Then press '**Enter**' _in the last_ to save the changes.

But if you are confused with that screen, it would help a lot if you could post a screenshot, or at least copy-paste the whole content of the screen here.

If you copy-paste, make sure to use 'Code' tags to post it (see the example link in my signature to see how to use code tags).

---

### Post by Tiles on 2013-03-05
> **varunendra said:**
> Can you post an screenshot where it showed all the partitions after deep search ? Listing of partitions means testdisk found them and can recover them.

As mentioned on the guide page, you can highlight a partition and press **p** to see the folders/subfolders/files in it to verify if it is the correct partition. Once you are satisfied, you may return on the partition listing screen by pressing **q**, then use **Left/Right** arrow keys to change the partition type from **D** (deleted) to **P** (primary) or **L** (logical) as applicable. Then press '**Enter**' _in the last_ to save the changes.

But if you are confused with that screen, it would help a lot if you could post a screenshot, or at least copy-paste the whole content of the screen here.

If you copy-paste, make sure to use 'Code' tags to post it (see the example link in my signature to see how to use code tags).

Allright, thanks for the help Varun, I got my data back, I don't think I lost anything too, just minor stuff, no big deal.
It turned that you need to be caution when you install Ubuntu, don't know if it's a bug in the install or something, but it's solved, thanks :D

---

### Post by varunendra on 2013-03-05
Great job! And you're always welcome :)

By the way, partitioning is something that always needs extreme caution, regardless of the tool or OS in use.

Let's hope the OP is also as lucky as you :).

---

### Post by ThulasiS on 2013-03-06
Hi Varun
What are the requirements to start testdisk? 
I understood how to do from the link you sent. But from where I have to start like Pendrive or I have install in current OS? I didn't understand and I am confusing.
I am scared if I do something wrong I may not able to recover data. Plz help me

---

### Post by varunendra on 2013-03-06
It is installed like a normal application on the running OS (it also has a Windows version). See post #11

Recommended way is to install it on a live session running off a live cd or usb. Then run it from there as mentioned in post #11 above.

If you are recovering partitions, you will be working only on the drive which lost the partitions. But if you are recovering individual files from it (without recovering partitions), then it is strongly recommended to use a different drive as the destination for the recovered files to avoid chances of overwriting (thus permanently losing files)..

In your case, all you need is recovering partitions. So I recommend you create an Ubuntu live (persistent) usb > Boot from it > Install testdisk on it > run it and follow the Step-by-Step guide to recover your partitions.

Post back if you get stuck at some stage.

---

### Post by ThulasiS on 2013-03-06
Hi
It was giving a message unable to locate package testdisk.
What to do?

---

### Post by ThulasiS on 2013-03-06
Hi all
It was giving a message unable to locate package testdisk. After Upadte and giving the second command sudo install testdisk
What to do? i am scared

---

### Post by varunendra on 2013-03-06
Which version of Ubuntu are you using ? It is available in repositories of 12.04.

In **Software Center > Edit > Software Sources**, make sure the "**universe**" repository is enabled (has a tick mark in the checkbox).

Also make sure you are connected to internet while running the update and install commands.

Alternatively, you may download it from its homepage here : [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

Choose the Linux version suitable to your version of Ubuntu (i386 means 32 bit, x86_64 is for 64 bit kernel). But installing from repositories is much easier.

If unsure, please post back output of :
```
uname -mr
```
in a terminal.


**[COLOR="#B22222"]EDIT:[/COLOR]**
Like I mentioned in my PM reply, here is a link to System Rescue CD which includes TestDisk among many other useful tools -

Homepage and description, guides etc. : [http://www.sysresccd.org/SystemRescueCd_Homepage](http://www.sysresccd.org/SystemRescueCd_Homepage)
Download page : [http://sourceforge.net/projects/systemrescuecd/](http://sourceforge.net/projects/systemrescuecd/)

---

### Post by ThulasiS on 2013-03-06
Hi varun
I am using Ubuntu 12.10. I can download it but I don't know how to install it after downloading. Tell me please if you know that alternative way.
I'll try again by Updating

---

### Post by varunendra on 2013-03-06
Installing from repositories is the best and recommended way.

If downloading about 350MB and burning a cd is not a problem for you, then using System Rescue CD is the next best option as it already has testdisk installed. I have provided its link in my previous post.

Downloading the source from the home page and installing from it may get stuck in some dependency issues. So I'd recommend it as the last option. I will have to download and install it myself to tell you how to do it :)

---

### Post by ThulasiS on 2013-03-06
I think it is better to download the 350 Mb. Because the same msg again I got. Some index files failed to download. Why it is happening to me again and again? Net connection is also goo in our lab. I already downloaded Ubuntu rescue CD. Can I use it? Okay I'll download systemRescueCd.
I understood one thing Ubuntu is for professionals but not for me. I thought Ubuntu became user friendly by now but not true. Why So many people prefer Windows Now I understood.
Thanks for your help

---

### Post by varunendra on 2013-03-06
> **ThulasiS said:**
> I think it is better to download the 350 Mb. Because the same msg again I got. Some index files failed to download. Why it is happening to me again and again? Net connection is also goo in our lab. I already downloaded Ubuntu rescue CD. Can I use it? Okay I'll download systemRescueCd.
I understood one thing Ubuntu is for professionals but not for me. I thought Ubuntu became user friendly by now but not true. Why So many people prefer Windows Now I understood.
Thanks for your help
Partitioning is always a risky operation and needs extreme caution. The risks are same regardless of which OS you are using. Contrary to the impression you got, I find the linux tools for this job more friendly, mature, capable and easy to use than most of the other commercial software out there.

Also, the term "user-friendly" is very misleading. We tend to define 'familiar' as 'friendly'. I began with Windows, kept using it for about 7 years. I switched to Ubuntu less than an year ago and now find it much more friendly and comfortable than Windows. I can say without hesitation that I never felt half as comfortable with windows as I am now with Ubuntu. It's all about knowing your way around :)

Probably a good read for you when you are relaxed and have some time : [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

[COLOR="#808080"]/me gets down the soapbox.[/COLOR]

---

### Post by Tiles on 2013-03-06
Well, after using windows for long time, Linux isn't bad actually, it's just more advanced than windows, that's all. Plus people here give you help faster than I expected, which is far better :D

---

### Post by ThulasiS on 2013-03-07
Hi Varun
I used Live CD ubuntu rescue remix 12.04. It was showing all the files and partitions. I am following the steps which were given for testdisk. working good but after showing data I was unable to back up them. How can I do? It was showing no back up selected like something it was showing. What to do? How to save that data? It was showing all files after pressing p. Frm then I was unable to proceed. Help me in this regard.

---

### Post by Tiles on 2013-03-07
> **varunendra said:**
> Can you post an screenshot where it showed all the partitions after deep search ? Listing of partitions means testdisk found them and can recover them.

As mentioned on the guide page, you can highlight a partition and press **p** to see the folders/subfolders/files in it to verify if it is the correct partition. Once you are satisfied, you may return on the partition listing screen by pressing **q**, then use **Left/Right** arrow keys to change the partition type from **D** (deleted) to **P** (primary) or **L** (logical) as applicable. Then press '**Enter**' _in the last_ to save the changes.

But if you are confused with that screen, it would help a lot if you could post a screenshot, or at least copy-paste the whole content of the screen here.

If you copy-paste, make sure to use 'Code' tags to post it (see the example link in my signature to see how to use code tags).

This is the answer as I suppose :)

---

### Post by varunendra on 2013-03-07
That's a good news. But you still need to be careful until you get all the desired files copied to a different drive. And what do you mean by this -
> I used Live CD ubuntu rescue remix 12.04. It was showing all the files and partitions.
Were the files visible in normal file browser of Ubuntu or in the testdisk window??

If they were visible in the normal browser, then it means they are already there in good shape and you don't need any recovery *[COLOR="#808080"](it also means that this whole thread is a result of a misunderstanding, that grahammechanical pointed out in post #3)[/COLOR]*. Just copy them to an external drive to be extra safe, and ignore what I am going to suggest next, it won't be needed.

But if you mean the files were visible in the testdisk window, then -

..follow the steps in post #13 to restore the partition structure. Once the partition(s) is/are back, you should get all your files back as they were before. The detailed steps are on the same page under "Deeper Search" heading : [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#A_partition_is_still_missing:_Deeper_Search](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#A_partition_is_still_missing:_Deeper_Search)

However, if restoring partition(s) doesn't restore files back, then we will need to manually recover files using the same testdisk program. But first try restoring partitions and let me know if the problem is solved.

**PS:**
In order to change the partition type from 'D' to 'P' or 'L', you need to correctly identify its type. If you don't remember or can't identify by their looks, this page will help you identifying the correct partition type : [http://www.cgsecurity.org/wiki/Partition_recognition_primary_and_logicalhttp://www.cgsecurity.org/wiki/Partition_recognition_primary_and_logical](http://www.cgsecurity.org/wiki/Partition_recognition_primary_and_logicalhttp://www.cgsecurity.org/wiki/Partition_recognition_primary_and_logical)

**PPS:**
Beaten by Tiles while I was creating my post :)

Thanks Tiles! Yes, that was post #13 I was referring to.

---

### Post by ThulasiS on 2013-03-07
I saw those files when I used Testdisk only. I went thoroughly step by step and finally it showed P HPFS - NTFS some numbers  [Drive name(that was I have given earlier in windows like materials)] and showed other two also but nothing with * mark for booting instead it showed D Linux---- something numbers. I was interested in using testdisk it was really simple and amazing. but what I did is I selected the require drives by tapping right/left n  I didn't select Linux. And I entered write but after rebooting *It showed error unknown file system grub recovery> then I *struck there. What to do? What the mistake I did? But I am sure that I can recover data without anyone (except with your help) help.Help me friend. Again am I require install any OS? I think I missed OS selection. 
P HPFS - NTFS means? Files already there in HDD or to be recover?
This I don't know.
I am some what happy, I am Playing with system without any Harm (I thought so)
So help me at this point.

---

### Post by black veils on 2013-03-07
boot the ubuntu live disc again and open a file manager. you will see the Windows partition/drive in the left pane, click on it to mount, see if you can find your files and copy them to another usb stick or online service etc.

---

### Post by Tiles on 2013-03-07
Well it happened with me as well, I had to re install Ubuntu again, but use the live disk and check if your HDD files are there.
NTFS refers to "New Technology File System", hope that did answer you.

---

### Post by varunendra on 2013-03-07
Haha.. finally we are making some good progress here. Everything you described is normal and in a positive direction.

Let me address your points one-by-one -
> **ThulasiS said:**
> ..and finally it showed P HPFS - NTFS some numbers  [Drive name(that was I have given earlier in windows like materials)]
NTFS is the filesystem used by windows. If testdisk can see it, it can also recover it which I think you have already done now :)

> and showed other two also but nothing with * mark for booting instead it showed D Linux---- something numbers.
* mark means bootable partition, which can be only one per drive. So that is normal.
**D Linux** means "Linux" partition which was **D**eleted (or crashed/corrupt whatever).
Numbers indicate location and size of the listed partitions (in terms of CHS = Cylinder, Head, Sector).

Just for your information - If the number of starting Cylinder of a partition is smaller than that of ending Cylinder of the previous one, it means they are overlapping, which further means at least one of them is a wrong entry and needs to be corrected or dropped.

> I was interested in using testdisk it was really simple and amazing.
..no doubt it is :)

> after rebooting *It showed error unknown file system grub recovery> then I *struck there.
..Again, perfectly normal.
You had already started installing Ubuntu (or maybe even almost finished it) when you lost your partition. So the MBR (Master Boot Record) of the drive was overwritten by GRUB which is Ubuntu's boot loader. But now there is no Ubuntu there to complete the booting. Hence the grub prompt. It does not mean that there is anything wrong with the partitions you recovered. They must be there.

> Again am I require install any OS? I think I missed OS selection.
Yes. You do need an OS to access the partiton(s)/files in it.
But DON't attempt to install one on that drive yet !
Just boot with your Ubuntu live CD, make sure the partitions and the files in it are normally accessible.

Then copy ALL the files to an external drive > run GParted > delete all the partitions in the defective drive AFTER saving your files on a different drive > recreate new, healthy partitions > Install the OS of your choice.

If reinstalling Ubuntu, just select the existing partition for installation by choosing "Do something else" option to go to manual selection menu.
Start a new thread if you need help with that.


> P HPFS - NTFS means? Files already there in HDD or to be recover?
P means Primary partition
HPFS - NTFS means the filesystem is NTFS (or HPFS, but in your case it is NTFS)
If you can see the files normally in the live session of the Ubuntu live cd, then they are recovered and now you should copy them to a different drive, as this one may have errors on it.

However, if the files (or the whole partition) is not visible in the file browser, then we still need to recover them. No problem!

So the bottomline is -
Boot again with the live cd and see if you can access and copy files somewhere else.
If not, just post back the result of -
```
sudo fdisk -l
```
..from the live session.

---

### Post by ThulasiS on 2013-03-07
I can boot the live disc again but it is asking only commands. I dnt knw all commands. It is Ubuntu rescue remix 12.04. WHEN I boot with live CD it was showing only one small terminal where I am entering commands. Please help me open a file manager. Mine is Huge data around 200 GB. I dnt have any external hard disk also. How to copy files? Here Net connection is so bad..even i think online services also cannot open for this huge data.
Okay I'll copy only important files. Please tell me how to copy files from testdisk terminal.

---

### Post by ThulasiS on 2013-03-07
Hi Varun 
Thank you. 
How to copy files? O don't have external Hard Disk. K but I'll try to get one from some friend otherwise I'll use pendrives.
That code is for what?
live CD is showing only one terminal for commands nothing else it was showing. I dont know commands to copy files
Thank you in advance

---

### Post by varunendra on 2013-03-07
I'm not familiar with the rescue remix, but from what I have read about it, it should be no different from the normal cd - meaning you should be able to boot into a gui interface.

Regardless, post back the output of -
```
sudo fdisk -l
```
while the drive in question is connected.

If there is a second drive connected (internally or externally), also post the output of-
```
df -h
```

---

### Post by ThulasiS on 2013-03-07
Hey Tiles
Files are there in the HDD. I checked twice. It took 4hrs for both times to analyze. Anyway I'll analyze again not a matter for me. Did you copy your files to any external HD before reinstalling Ubuntu? If so tell me also how to copy files.
Small commands are really interesting. 
Thank you

---

### Post by ThulasiS on 2013-03-07
Hi Varun
The output of the codes what you asked are here
```
sudo fdisk -l
Disk /dev/sda :500GB, 5000....bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinder of 16065*512 = 8225280bytes
Device Boot Start End Blocks Id System
/dev/sda1  5100 23711 190297957  7 HPFS/NTFS
/dev/sda2 23712 42323 149492857 7 HPFS/NTFS
/dev/sda3 42324 60800 149408470 7 HPFS/NTFS
Warning: unable to open /dev/sr0 read write (Read only file system)
Error: /dev/sr) :Unrecognized disk label
```

df -h output
showing the details of my Pendrive like used data, free data etc..

So now what I have to do?
I kept for analysis deeper search using testdisk

Thank you.

---

### Post by ThulasiS on 2013-03-07
Hi Black veils
I can boot the live disc again but it is asking only commands. I dnt knw  all commands. It is Ubuntu rescue remix 12.04. WHEN I boot with live CD  it was showing only one small terminal where I am entering commands.  Please help me open a file manager. Mine is Huge data around 200 GB. I  dnt have any external hard disk also. How to copy files? Here Net  connection is so bad..even i think online services also cannot open for  this huge data.
Okay I'll copy only important files. Please tell me how to copy files from testdisk terminal.

Thank you

---

### Post by ThulasiS on 2013-03-07
Hi All

Using testdisk to recover data is good experience.
Still some doubts.
P means primary partition
L for Logic
what is the difference between two?
Please tell me:mad:

---

### Post by Tiles on 2013-03-07
L = Logic Partition, that's used to store data on, and isn't used to boot from to any OS.
P = Primary Partition, that's a partition used to boot from to OS you have.

As I understood, your all data were wiped out after installing Ubuntu, so I think the partition which had Windows is formatted. To get your other partitions back you need to make them "L" since they're used to store data on em not to boot from.

I actually didn't transfer any of my data outside of the HDD, all I did was being caution at formatting the old "C" partition which was used to have windows and setup Ubuntu on it. Hope that helped.

---

### Post by black veils on 2013-03-07
> **ThulasiS said:**
> Hi Black veils
I can boot the live disc again but it is asking only commands. I dnt knw  all commands. It is Ubuntu rescue remix 12.04. WHEN I boot with live CD  it was showing only one small terminal where I am entering commands.  Please help me open a file manager. Mine is Huge data around 200 GB. I  dnt have any external hard disk also. How to copy files? Here Net  connection is so bad..even i think online services also cannot open for  this huge data.
Okay I'll copy only important files. Please tell me how to copy files from testdisk terminal.

Thank you

i dont know what to say other than create another bootable disc/usb stick which has a GUI, not just commands. it would be a lot easier, then you can open a file manager and copy the files you need out of the 200gb.

---

### Post by ThulasiS on 2013-03-08
Okay I'll also do the same today. 
I'll make them L and I'll proceed further like Installing the other OS. Hope that will help me

---

### Post by varunendra on 2013-03-08
> **ThulasiS said:**
> 
Still some doubts.
P means primary partition
L for Logic
what is the difference between two?

> **Tiles said:**
> L = Logic Partition, that's used to store data on, and **isn't used to boot from to any OS**.
P = Primary Partition, that's a partition used to boot from to OS you have.
Some correction to above explanation -
Logical drives CAN be used to boot OS. It's just windows that prefers to be on a primary partition, and windows Vista onwards don't boot at all from a logical partition. I have personally booted XP from a logical partition, however, the boot files (ntldr, ntdetect.com, boot.ini) were located on the primary partition.

OS like Ubuntu have no problems booting from logical partitions.

More on Primary vs. Logical partitions : [http://en.wikipedia.org/wiki/Disk_partitioning#PC_partition_types](http://en.wikipedia.org/wiki/Disk_partitioning#PC_partition_types)
In essence, logical partitions are just a workaround to the partition no. limitation of traditional Master Boot Record (MBR).

> **Tiles said:**
> To get your other partitions back you need to make them "L" since they're used to store data on em not to boot from.
Not necessarily.
XP and previous versions of Windows tend to create one primary and rest logical partitions.
Vista and later tend to create upto four partitons as primary (four is limit of primary partitions), then convert them to '[dynamic]("http://msdn.microsoft.com/en-us/library/windows/desktop/aa363785(v=vs.85).aspx#dynamic_disks")' as subsequent ones are added.

So the partitions may or may not be logical ones. Besides, out target is to recover files. So we should refrain from messing with partitions unless necessary.

> **Tiles said:**
> I actually didn't transfer any of my data outside of the HDD, all I did was being caution at formatting the old "C" partition which was used to have windows and setup Ubuntu on it. Hope that helped.
Can be done if there is no other choice. But I have experienced issues with partition tables recovered with testdisk in the past. Although Ubuntu (9.10 it was) installed fine and was working fine, but gparted always flagged the drive as 'Unknown' type :). Whether it was some bug in gparted or the partition table wasn't clean - I'm not sure. But I have experienced this more than once and so prefer to start fresh after moving all the data to a different drive.
But like I said - it Can be done if there is no other choice.

> **ThulasiS said:**
> Okay I'll also do the same today. 
I'll make them L and I'll proceed further like Installing the other OS. Hope that will help me
Please don't mess with partitions unless necessary. First confirm whether the files are accessible or not. You haven't attempted so yet.

Creating a fresh live cd which has GUI is a good idea, although not necessary to copy the files. Some of the ways you can choose from -

1)
**Where are you posting from? If it is a different desktop PC, you can internally connect the drive in it to access the files using its running OS.**

However, if that is a laptop and you don't have an option to connect it via usb, then we can use either commands or a fresh live cd/usb with gui, but you still need a spare drive to transfer files if you want to be extra sure (again, it's not necessary as Tiles mentioned).

2)
If you are planning to install Ubuntu again, I recommend 12.04 64 bit (if supported by your system) as it is an LTS, and also recommend to download it via torrent to ensure integrity of the downloaded iso : [http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)

You may also choose from [Xubuntu]("http://xubuntu.org/getxubuntu/") or [Lubuntu]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu") for a lightweight alternate.

Download any of them > burn a fresh live cd > boot with it to transfer your file > use the same disk to install.

3)
If you just need a live cd for copying files and want it to be as small in size as possible, then Slitaz is a good choice. Just under 35 MB in size with a nice gui : [http://www.slitaz.org/en/get/#stable](http://www.slitaz.org/en/get/#stable)

4)
And last :P you can even use the currently available commandline to copy the files. Let me know if you want to try that, and if you do, please also post output of -
```
mount
```

---

### Post by ThulasiS on 2013-03-08
Hi Varun :p
Thank you for your suggestions.

I am daily posting all these from my lab system which has net connection.
Before doing all these I recovered my data using the testdisk by running from live CD.
I recovered almost all files without big loss. I found my HDD partition by following the simple changes that analysis.
What I did is I run the testdisk from Terminal in ubuntu rescue Remix 12.04
Followed the tips from cgsecurity website the link which you were given.
After Deeper Search I found all partition in D (Deleted State). I selected all drives 
(Simple math I followed to identify cylinder numbers, like 0 to something for 1st drive and for other drives the cylinder no.s which I were posted earlier) 
making P (In my PC in first partition it self all drives in P state only, Varun you are Correct)
Then I hit the write tab and then rebooted.

Finally I removed live CD and Inserted my Windows 7 DVD. I went for Installation, during installation it showed all my drives like those in previous state with details of memory.
I installed windows 7 and during installation it showed & fixed some errors in drive D.
Finally I got my Data Back for which I struggled these many days.
Now its the time to install Ubuntu 12.10 along side of windows.
My Simple experiment worked well (Before proceeding I thought so many times and finally I thought its just machine)
I am so excited and I tried to explain you all what I did. I hope you Understand this Long Post. 
The Bottom line of the Post is now I am a relaxed Guy and I my research on data recovery from a drive worked well for me.:guitar:
Thank you for all your support
Thank you, I personally owe so much to you all.):P

---

### Post by black veils on 2013-03-08
remember to backup your important files

---

### Post by ThulasiS on 2013-03-08
Thank you
For Sure I'll do..
Thank you so much

---

### Post by ThulasiS on 2013-03-08
Hi All

I successfully Recovered Data.
I want to make this thread as solved but
I was Unable to do even after seeing the posts related to make thread solved.
Because those options are not coming on my PC.
So please any form member make it solved.

Thank you and Thanks a lot...

---

### Post by varunendra on 2013-03-08
Thank you for the feedback. It helps a lot the other users who may come across this thread looking for solution with a similar problem.

Please follow the (See how) link in my signature to mark the thread as **[Solved]** now that it is. It makes the thread more useful for others.

For installation of Ubuntu, I always recommend to use gparted (included on the live cd/dvd) to create/format partitions. Don't rely on automatic selection of the installer as it is prone to such mistakes as you have suffered.

Start a new thread if you need help with that.

Thanks again, and good luck with the fresh installation :)

---

### Post by ThulasiS on 2013-03-09
HI All
I Recovered Data, even what ever the files I deleted earlier also. Thank to the software team who developed such a wonderful recovery software.

---

### Post by varunendra on 2013-03-09
> **ThulasiS said:**
> HI All
I Recovered Data, even what ever the files I deleted earlier also. Thank to the software team who developed such a wonderful recovery software.
I couldn't find an official link for feedback to the project, but if you can, you should consider some small donation to the project then:
[http://www.cgsecurity.org/wiki/Donation](http://www.cgsecurity.org/wiki/Donation)

Not an appeal though, only if you feel happy doing so :)

---

