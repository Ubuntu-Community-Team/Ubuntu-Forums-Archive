---
title: "reclaim partition space"
date: 2014-09-27
forum: General Help
---

### Post by markk2 on 2014-09-27
Hi;
   I installed a version of ubuntu on my laptop . Do not know which one . Problem is that it did not work out so well . I noticed while installing it that a disclaimer was made that the partition it was making could not be undone . Well I thought for sure partition magic could do the trick but no . I wanted back my 30GB of space . PM can not even find it . Is there any way to recover that space ?
 I also tried to install mint 17 in the partition . How ever mint did not show the partition either . 

thanks

---

### Post by westie457 on 2014-09-27
Hi, do you have Windows on your computer and did you install  using a file called 'wubi.exe'?

---

### Post by markk2 on 2014-09-27
I have winxp . I installed with a cd . Not sure which version . got several of them . Deleted the ubunto file from HD . Now the partition does not even show up. Nothing real important since I have a lot of HD space available to install linux in but I jsut thought maybe I could install it in the ubunto partition if I could find it .

---

### Post by westie457 on 2014-09-27
> **markk2 said:**
> I have winxp . I installed with a cd . Not sure which version . got several of them . [COLOR=#ff0000]Deleted the ubunto file from HD . Now the partition does not even show up[/COLOR]. Nothing real important since I have a lot of HD space available to install linux in but I jsut thought maybe I could install it in the ubunto partition if I could find it .

|I will try to explain this as simply as possible even though by the time I finish everything will be as clear as mud.

When Ubuntu is installed using wubi.exe it is installed to an area of the Windows C:\ drive as a very large file (in your case a 30GB one) and not to a partition. This very large file acts like Ubuntu is on a partition and Windows cannot see what is inside this file. The usual way to remove a Wubi installation is via the Add/Remove Programs in Windows Control Panel. Just deleting the Ubuntu file causes quite a few more headaches.

One way to fix this is to boot the CD into 'Try' mode and install Boot Repair to repair the Windows boot files and enable you to start again with minimal fuss.

Boot Repair is here [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You will want to use the 2nd option

While you have the live Desktop running start Gparted, This will show all of the partitions on your drive (probably only one, taking up the whole of the drive.
If anything different take a screen-shot of Gparted and post it here so we can check on ways to recover.

---

### Post by markk2 on 2014-09-27
i will give that a try . 
edit : I forgot to add in that i do not have any problems booting up windows .  Just trying to figure out where that ubuntu was installed at . I think I made a partition to put it in . I thought it said " that this action can not be undone " 
Anyway I will boot from a cd and see what comes up

---

### Post by markk2 on 2014-09-27
I booted up ubuntu 8.10 intrepid . Not the version I used before but it worked any way . I went to " places " and it showed all three of the partitions . The one in question a 31GB  can not be accessed . It shows an error  " cannot mount volume. The volume uses the ext4 file system which is not supported by your system "

maybe I will try to boot with the cd I used the first time if I can figure out what it was . tried 2 that would not read and one that I thought was it but kept hanging up .

---

### Post by markk2 on 2014-09-27
got another quick question for you . Is ubunto as secure as linux mint ? I kind of liked that 8.1 intrepid .

---

### Post by yancek on 2014-09-27
> I booted up ubuntu 8.10 intrepid 

Take a look at the site below which gives the support ending dates for different releases of Ubuntu and you will see that it has not been supported for over 4 years.  What that means is you will not be able to get any security updates or download and install software in the usual manner.  It also shows which releases are still supported.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Posting some information on your hardware might help someone to make a useful suggestion.  As far as Mint, it is based on Ubuntu so there are not that many major differences but there are enough.  As far as security, the systems would be similar.

I'm not sure from your posts if you are using a "wubi" install which is installing Ubuntu inside windows as a program and not on a separate partition.  If so, you should know that wubi is no longer supported by Ubuntu.

If you can boot the Ubuntu CD/DVD, open a terminal and type the following command and post the output which will give info on drives/partition:  sudo fdisk -l(Lower Case Letter L in the command)

---

### Post by Impavidus on 2014-09-28
Support for ext4 first came in Ubuntu 9.04. Your live disk is just too old. Don't use old and unsupported releases, except in an emergency.

The results from the Boot-Info script from Boot-Repair could help us understand what's going on on your computer.

---

### Post by markk2 on 2014-09-28
okay thanks for the help . I installed from a cd ( I have 4 different cd's ) but the only one that seems to be working now is the 8.1 . the others will not read and one stalls . I also installed in the 31 gb partition which I made just for the ubuntu . Windows in in a different partition. When i made the partition Ubuntu gave a warning that the partition could not be undone . 
 
 The thing is I was wanting to use that 31 gb of space to to install mint 17 . How ever if Ubuntu is as secure as linux as far as hackers and virus I would not mind going with a new version of Ubuntu . Do you think a new Ubuntu could access that ext4 partition ?
 If so what is the best version of ubuntu and where do i get it ?

---

### Post by markk2 on 2014-09-28
[COLOR=#222222][FONT=Times New Roman]okay thanks for the help . I installed from a cd ( I have 4 different cd's ) but the only one that seems to be working now is the 8.1 . the others will not read and one stalls . I also installed in the 31 gb partition which I made just for the ubuntu . Windows in in a different partition. When i made the partition Ubuntu gave a warning that the partition could not be undone . 
 
 The thing is I was wanting to use that 31 gb of space to to install mint 17 . How ever if Ubuntu is as secure as linux as far as hackers and virus I would not mind going with a new version of Ubuntu . Do you think a new Ubuntu could access that ext4 partition ?
 If so what is the best version of ubuntu and where do i get it ? [/FONT][/COLOR]

---

### Post by yancek on 2014-09-28
The Ubuntu site below lists the minimum hardware requirements for Ubuntu so check that and compare it to your actual hardware.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

> [COLOR=#222222][FONT=Times New Roman]When i made the partition Ubuntu gave a warning that the partition could not be undone . [/FONT][/COLOR]

Can't speak to that as in the years I have been using Linux I have never seen anything like that.
The two releases of Ubuntu currently supported are 12.04 and 14.04 and their default filesystem is ext4.

You can download 14.04 at the site below.  You will probably need to use the 32bit version if your computer is old enough that it came with xp. 

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

You can download 12.04 at the site below, probably need the Intelx86 version.

[http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)

---

### Post by mcduck on 2014-09-29
> **markk2 said:**
> When i made the partition Ubuntu gave a warning that the partition could not be undone . 
 

The warning is trying to tell you that if, during the partitioning, you do something like deleting an existing partition, any files you had on that partition are gone and can't be recovered. The partitions themselves can of course always be edited and removed. It's just their *contents* that can't be recovered (At least in any easy way) if you delete a partition or something goes wrong during the partitioning process.

> **markk2 said:**
> How ever if Ubuntu is as secure as linux as far as hackers and virus I would not mind going with a new version of Ubuntu .
Ubuntu *is* a Linux distribution, just like Mint is. Actually Mint is based on Ubuntu, so there really shouldn't be much of a difference security-wise between the two. As far as I know much of the core packages in Mint come straight from Ubuntu's software repositories, and it's only the user interface side where they have made changes...

---

### Post by markk2 on 2014-09-29
> **yancek said:**
> The Ubuntu site below lists the minimum hardware requirements for Ubuntu so check that and compare it to your actual hardware.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)



Can't speak to that as in the years I have been using Linux I have never seen anything like that.
The two releases of Ubuntu currently supported are 12.04 and 14.04 and their default filesystem is ext4.

You can download 14.04 at the site below.  You will probably need to use the 32bit version if your computer is old enough that it came with xp. 

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

You can download 12.04 at the site below, probably need the Intelx86 version.


[http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)

Cool . that should do the trick . the ext4 file system was what i could  not access with anything I could find . thank you for the links . Ubunto seems so much easier to use than linux . Linix seems to be something for people with a lot of programming experience . Takes too much know how jsut to do a simple thing like install a program .

---

### Post by markk2 on 2014-09-29
> **mcduck said:**
> The warning is trying to tell you that if, during the partitioning, you do something like deleting an existing partition, any files you had on that partition are gone and can't be recovered. The partitions themselves can of course always be edited and removed. It's just their *contents* that can't be recovered (At least in any easy way) if you delete a partition or something goes wrong during the partitioning process.


Ubuntu *is* a Linux distribution, just like Mint is. Actually Mint is based on Ubuntu, so there really shouldn't be much of a difference security-wise between the two. As far as I know much of the core packages in Mint come straight from Ubuntu's software repositories, and it's only the user interface side where they have made changes...

thanks for the info . I was using the linux because of security concerns with windows . Have not had any problems in all the years I used XP but linux does not get all them virus ' so i thought be better for my banking and online buying . But if I can instal ubunto in that partition again that would be great .

---

