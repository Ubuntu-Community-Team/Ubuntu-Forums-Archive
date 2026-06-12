---
title: "ubuntu drive &amp; folder files system"
date: 2013-10-22
forum: General Help
---

### Post by adi06 on 2013-10-22
Hi all, Some noob questions plz.
Coming from windows, i know my drive names and folder in C:/
But in ubuntu i see the following 3 type of folders. 
The places directory is preety explainatery,

**1)** In Drives section, "*Computer*" Is this the c drive/windows drive equalant? am i getting it right?
Also what other folder i should be familiar with?

In Gparted you can isee i have 1st C drive for windows 7, 2nd ext4 for ubuntu root  / 
3rd swap 2gb, and 4rth data drive ntfs

while installing ubuntu, i wanted to make a structure like 10GB for ubuntu OS which i mounted at root /
2GB swap, 8.9 GB Data, which i mounted at home.
[B]
2) [/B]Did i went okay? but i also see NTFS partinion in Devices section, so did i needed ext4 partition or i could have used my Data drives.
**3)** How do i rename my ext4 8.9 GB volume?

**3)** I see unmount option on drives except for windows 7 drive when i right click, what does that mean? i can remove them? and why is such option available, and what if i accidently unmount a drive and want to remount?
**4)** Thunderbird, if i receive emails, i have to open the app and wait few seconds, then the app reloads and shows new emails and a pop on top right corner., is this normal behavior? can it work like google talk? if not, what can i use?
**5)** Is google talk available to use in ubuntu? for audio and tet chat and email notifications works well,

**6)** For got to add an image, In system setting > online accounts. What is purpose of that? how do i use it? i added my gmail and facebok and flickr ids but nothing happend, nor i found any guide or infor, about hw that system works.
[B]
7) [/B]What about hardware drivers? things looks good everything is working, but do i need to install some latest driver or, all work out of box? i.e my default intel HD-2000 VGA of i3-2100 cpu, and inboard sound and lan.
And i am looking forward for a nvidia 3d card, will i be needing any 3rd part driver or the nvidia provides a driver for linux? asking just to be future safe :)

***8)** i tried to copy a package file from ntfs drive to 8.9GB ext4 but paste is disabled, also new folder option is disabled, why this drive is not access able?

****9)** I tried to diasable guest login by editing and saving some config file thoru a post guide, after that ubuntu boot and after the loading dots, screen gets turn off/black.
I re-installed ubuntu and all softs again :mad:

*****10)** how can i backup all installed apps and dependencies as an image/repository, so i can use them to install without internet(for faster working system), i.e in case i mess up ubuntu again.

If any other, things you might want to add for me as tip, tricks, plz do include them. 
Thanks in anticipation :KS



[IMG]http://img580.imageshack.us/img580/311/i98l.png[/IMG]

---

### Post by Bashing-om on 2013-10-22
adi06; Hi !

A  lot of uncertainty on you part is understandable with a lot of questions. I will try and address what I can of them.

Partitions: -> Windows designations of "drive" is actually "partitions" on a single physical device. Thus Windows c/drive is but a single partition on a single hard drive that ubuntu designates as sda1, in this case.
ubuntu renders that representation correctly as:
sda = the first hard drive
sda1 = the first hard drive and the first partition(1) primary, here a Windows ntfs partition;
sda2 = 1st HD, 2nd partition, here Window's 7 ntfs partition;
sda3 = 1st HD, 3rd primary partition; ntfs data partition -> that may be configured to share between both operating systems !
Then sda4 - this is an extended partition, that contains within it a number of "logical: partitions ->
sda5 = 1st HD, 5th partition (logical) is the swap partition, similar to use as Windows swap page;
sda7 = 1st HD, 7th parttion (logical) is the ubuntu operating system "/" ext4
------------
sdb - if you had a 2nd hard drive (b)
sdc - if you had a 3rd hard drive (c)

So, you are configured properly, 4 primary partitions ( the extended partition counts as a primary partition in which any number of "logical" partitions may be made, space permitting). But, you do not have a separate home, your '"/home" is contained with in the root (/) directory. No biggy as of this time. But if you use ubuntu, you will find that 10 gigs is too tight for a full featured installation to allow operating head room. I often see 30 gigs recommended.

File system:
Everything is a file to ubuntu .. everything.. devices, hard drives usb sticks, monitors... everything is a file to ubuntu. At the top of this file structure is "/" the root directory - for the ubuntu operating system -  and it contains all the other directories (and files) and all is attached and incorporated under "/". All the system files, bin, boot, etc. lib, ect, ect ;This includes your "/home" directory, that will contain all your own personal stuff and config files fro the applications that you use.

Devices -> data:
As you only have the one single hard drive installed, I expect that "data" is actually "sda3" that yes, may be mounted for read/write access. And as in Windows, (UN)mount -eject-- when a task is completed. Remount is as you surmise, right click on the icon, and select mount. And you have access now to that attached file system. Same goes for the Window's partitions... but exercise extreme caution when mounting the Windows' operating system partitions from ubuntu .. you can unwittingly inflict damage to the Windows' operating system !


Your number 7) ubuntu is well supported - out of the box - with all hardware drivers. If it ain't broke, do not fix it ! If additional attention is required try and stay within the ububtu direct support system to find the solution; primarily the utility "Additional Hardware", next is supported PPA (personal Package Archive) and then if all else fails one may try and down load drivers from the manufacturer, perhaps compile from source, and install manually. Not to be contemplated by the unwary !

your number 8) item. the devices must be mounted before you can access the files thereon.

Your number 9), No way to tell what happened, editing only a guest .config file should not have effected your user files. Pleased you were able to (re)install and back up and running.

Your number 10) Backup procedures are as diverse as there are users, there are a number of backup utilities available in addition to what is provided in the install .. As you now know a (re)install is quick and painless .. I personally only make backups of my personal data and a few config files that would be a trial to rebuild. My personal experience with my knowledge and how I use my system, I can completely (re-)install from scratch and be back up fully at the point I was in 20 minutes. However, I have written scripts to backup those files, and scripts to restore them to the new install. That capability will come to you also if you want that ability. There is no direct need to backup system files, they are all available on the install.

The other questions I can not address as I have no experience with those applications.

Be patient, use your ubuntu operating system and in time all your questions will be answered.

Welcome again to what, in my opinion is ->
[INDENT][INDENT][INDENT]the greatest operating system the world has ever known
[/INDENT][/INDENT][/INDENT]

---

### Post by jamesisin on 2013-10-22
Welcome to Ubuntu.  Bashing-om's comment is pretty comprehensive.  If you still have questions, let us know and we'll work to fill in the gaps.

---

### Post by oldfred on 2013-10-22
To add a little.

Linux partitions have ownership & permissions. It is a multiuser system so you can set files with different owners and permissions. You probably have not given yourself ownership & permissions to use your ext4 data partition. That partition is not your /home as it is not mounted that way.
       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

    
You probably did not need a separate Linux data partition if using a NTFS data partition. I still have my NTFS shared data partition with my Firefox & Thunderbird profiles, so I can share with Windows & Linux. Then all bookmarks & emails are the same in both systems.
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

You have a little red icon next to your Windows 7. That says your system partition cannot be mounted. Does it need chkdsk or is it hibernated? Best not to hibernate when dual booting. And best not to write (read ok) into Windows system partition, but use shared NTFS data partition for read/write sharing.

Ubuntu has recent nVidia drivers in its repository. You may have to use nomodeset to boot, but then just install the nVidia drivers from within Ubuntu. Post back when that time comes, or search forum as there are many threads on that very issue.

---

### Post by adi06 on 2013-10-22
@bashing-Om you explanation of drives, i don't have much words to say how much i appreciate it. i'm a noob Computer science student, and one of my specialty was windows partitioning, But on linux, i was blank. but now i know a lot, with ur guide. Thanks a lot.
And your remaining points are awesome. thanks 
Only one thing from ur reply is left unresolved, **point 10** backup utility. you said fresh install is easy, i agree and that is what i'll do, takes me 8 mins.
but the apps i install takes 20+ mins, i.e, flash, gparted, gimp, codacks, vlc, skype, variety wall changer, kdenlive, etc..
If you can explain or forward me to some guide, so i can make:
**1)** A backup of the installed apps, and use them as a source to choose from in software center, (on non internet pc)
**2)** Make a script so install all the apps in the image created by step 1, so suo apt-run-script install_all_apps_in_script_source_is_img1

As u can see i joined ubuntu forum in 2009, that was the 1st time i installed ubuntu, 8.02 something. but bcoz of wireless adapter driver and many other issues was just not my cup of coffee. so i left, now 2013 and its way better then before. I totally want to migrate from windows to linux(Ubuntu i prefer).

On;y thing left is: **3)** VPN like hotspot, youtube is blocked in my country & i need it. as i'm a noob, some gui based or one time setting would be preferred. you can see my post about it, a guy suggested some but those didn't worked well.

**4)** where are the apps get installed, what is equivalent of program files in ubuntu, is it opt folder?
i have a execute able file for a text editor, sublime text 2, i was wondering where to put it. Also how can i make it default editor for all file type or when i click edit.
how do i replace it with gedit? bcoz its a standalone execute able, i don't have clue how i can do it.
*besides is it advisable to replace gedit with that editor? or should i use that only for my development/production time, which i mostly do simply by running from dash.*

@oldfred, your post is awesome, i used that information, 10 mins google search and i understood what u explained about user rights and ownership.
using that knowledge i am able to rename the drive and also changed the ownership from root to my logged in username. everything is beautiful now.
Now what is bothering me is, when i created the ext4 during installation of OS, then it i suppose by default assigned it to root user, but during installation, user have to create an account, which in my case was bsienn, so do i always have to get through the mess of assigning right back from root to bsienn?
i understand its only 1 time process mostly, during OS install which wont happen a lot, but it should have been obvious and by default the administrator user should have ownership of the created partition. IMO

here is the stuff i used, but not sure what they are.
gksu nautilus
Alt+F2

i know nautilus is the explorer for ubuntu
i know sudo, gksg is i guess same thing but whats the difference? i didn't had this on system, terminal gave me intrusction to download it, and i did sudo apt-install gksu
2ndly what is Alt+F2

3rdy, i tried to change permission of my windows 7 drive for root and owner from read & write to list only, but when i change the drop down, it get back to default read&write.
why is that? maybe bcoz thats my primary OS and linked with dual booting or something like that?
What i want is not access windows 7 drive in ubuntu for security reason. accidental read/write for all users.

i never use OS partition for storing data, so windows 7's my documents and pics/download folder are always empty, same goes for Ubuntu, i'll no use home directory for anything.

So i'm back on my 1st question, partition. as bashing-Om said, everything is in / root, than what is the purpose of the following pic, where i assigned the 8.9GB volume ext4 partition in /home and the ubuntu OS drive to /

and what about the other options in the pic?
[IMG]http://www.basicconfig.com/files/content/manual_partition_ubuntu06.preview.png[/IMG]

@[**[COLOR=#000000]jamesisin[/COLOR]**]("http://ubuntuforums.org/member.php?u=612780") Thanks for your support :)

---

### Post by oldfred on 2013-10-22
My first install of Redhat 5 back 15 years ago (not more current version), was more a server type install. And then you created partitions for just about every system folder. With servers often still done to provide for different requirements. But not needed for most desktops.

All these are really the same thing on Linux standard base or file structure.
 Explanation of file structure
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
[http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base)
[http://en.wikipedia.org/wiki/Unix_directory_structure](http://en.wikipedia.org/wiki/Unix_directory_structure)
Linux Standard Base details
[http://refspecs.linux-foundation.org/LSB_3.2.0/LSB-Core-generic/LSB-Core-generic/book1.html](http://refspecs.linux-foundation.org/LSB_3.2.0/LSB-Core-generic/LSB-Core-generic/book1.html)

      
 A master thread on learning/books/terminal/bash/Linux etc
Linux Command Line Learning Resources - cortman
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)
[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)

---

### Post by Petro Dawg on 2013-10-22
> **4)** where are the apps get installed, what is equivalent of program files in ubuntu, is it opt folder?

You might look [here]("http://www.tldp.org/LDP/intro-linux/html/sect_03_01.html") for some general information regarding the Linux file system.

As a "guideline" the following convention is used for file system organization, however, it is not set in stone...
[B]
Table 3-2. Subdirectories of the root directory[/B]

[TABLE="class: CALSTABLE"]
[TR]
[TH]Directory[/TH]
[TH]Content[/TH]
[/TR]
[TR]
[TD]/bin[/TD]
[TD]Common programs, shared by the system, the system administrator and the users.[/TD]
[/TR]
[TR]
[TD]/boot[/TD]
[TD]The startup files and the kernel, vmlinuz.  In some recent distributions also grub data.  Grub is the GRand Unified Boot loader and is an attempt to get rid of the many different boot-loaders we know today.[/TD]
[/TR]
[TR]
[TD]/dev[/TD]
[TD]Contains references to all the CPU peripheral hardware, which are represented as files with special properties.[/TD]
[/TR]
[TR]
[TD]/etc[/TD]
[TD]Most important system configuration files are in /etc, this directory contains data similar to those in the Control Panel in Windows[/TD]
[/TR]
[TR]
[TD]/home[/TD]
[TD]Home directories of the common users.[/TD]
[/TR]
[TR]
[TD]/initrd[/TD]
[TD](on some distributions) Information for booting.  Do not remove![/TD]
[/TR]
[TR]
[TD]/lib[/TD]
[TD]Library files, includes files for all kinds of programs needed by the system and the users.[/TD]
[/TR]
[TR]
[TD]/lost+found[/TD]
[TD]Every partition has a lost+found in its upper directory.  Files that were saved during failures are here.[/TD]
[/TR]
[TR]
[TD]/misc[/TD]
[TD]For miscellaneous purposes.[/TD]
[/TR]
[TR]
[TD]/mnt[/TD]
[TD]Standard mount point for external file systems, e.g. a CD-ROM or a digital camera.[/TD]
[/TR]
[TR]
[TD]/net[/TD]
[TD]Standard mount point for entire remote file systems[/TD]
[/TR]
[TR]
[TD]/opt[/TD]
[TD]Typically contains extra and third party software.[/TD]
[/TR]
[TR]
[TD]/proc[/TD]
[TD]A virtual file system containing information about system resources.  More information about the meaning of the files in proc is obtained by entering the command **man *proc*** in a terminal window.  The file proc.txt discusses the virtual file system in detail.[/TD]
[/TR]
[TR]
[TD]/root[/TD]
[TD]The  administrative user's home directory.  Mind the difference between /,  the root directory and /root, the home directory of the *root* user.[/TD]
[/TR]
[TR]
[TD]/sbin[/TD]
[TD]Programs for use by the system and the system administrator.[/TD]
[/TR]
[TR]
[TD]/tmp[/TD]
[TD]Temporary space for use by the system, cleaned upon reboot, so don't use this for saving any work![/TD]
[/TR]
[TR]
[TD]/usr[/TD]
[TD]Programs, libraries, documentation etc. for all user-related programs.[/TD]
[/TR]
[TR]
[TD]/var[/TD]
[TD]Storage  for all variable files and temporary files created by users, such as  log files, the mail queue, the print spooler area, space for temporary  storage of files downloaded from the Internet, or to keep an image of a  CD before burning it.[/TD]
[/TR]
[/TABLE]

---

### Post by Bashing-om on 2013-10-22
adi06; Hey,
Backups, here is one thought as the package manager in ubuntu is a wonder to behold and even greater to use:
How about a system generated file of all installed apps and a means to automatic-ly (re)install them ?
[http://ubuntuforums.org/showpost.php...75&postcount=5](http://ubuntuforums.org/showpost.php...75&postcount=5)
[http://kevin.vanzonneveld.net/techbl...selectupgrade/](http://kevin.vanzonneveld.net/techbl...selectupgrade/)

Basically:
From the old install
```

dpkg --get-selections > ~/my-packages

```
Save that file along with other data files you want restored.
In the new install:
```

sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

```

Making a back up script, I leave as an exercise for the student. Only you can know what and where your files are - I will provide you what I have if ya want, merely as a template/example . But I assure you, specific to what I have and do, not much use to you.

VPN I do not use, so know nothing about it..Tunneling can be done, ssh and such but is beyond my current experience to set it up, documentation abounds !

Now comes some confusion in respect to the root account. By default on ubuntu it does not exist (initially) What one has is the "sudo" mechanisum 
for administration of the system. The 1st user created at install may and does exercise administrative authority. Precede any command that requires that access   by the term -sudo- and provide authentication by entering your password (you set this at install ).


See this for an explanation of sudo/gksudo and the wherof/why !
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
[http://ubuntuforums.org/showthread.php?t=1841457&page=5](http://ubuntuforums.org/showthread.php?t=1841457&page=5)


NTFS access and permissions are set at the mount point:
see these most excellent tutorial/template:
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

> 
So i'm back on my 1st question, partition. as bashing-Om said, everything is in / root, that what is the purpose of the following pic, where i assigned the 8.9GB volume ext4 partition in /home

Can't say other than the change to the partition table was not "applied".. a quick way to see what is current on you system:
```

sudo fdisk -lu
sudo blkid
df -h

``` as you can tell I think more CLI that GUI !

[INDENT][INDENT]We will have you setting pretty, and glowing at your ubuntu ! - in no time
[/INDENT][/INDENT]

---

### Post by adi06 on 2013-10-22
[[IMG]http://ubuntuforums.org/customavatars/avatar1693421_3.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1693421") 				 				 					 						 	[**[COLOR=#000000]Petro Dawg[/COLOR]**]("http://ubuntuforums.org/member.php?u=1693421")
Superb details, thanks for it :)


> **Bashing-om said:**
> 
[INDENT][INDENT]We will have you setting pretty, and glowing at your ubuntu ! - in no time
[/INDENT]
[/INDENT]


hehehe, loved it!

Its 5am here and i am studying about linux from awesome fellows like u.
In single post i have got a lot of material to study, thanks for ur great time.
I'll keep reading it in morning, till then. Good night ^_^

---

### Post by jamesisin on 2013-10-22
New users may appreciate this brief guide I wrote outlining how I create new machines for people.

[http://jamesisin.com/a_high-tech_blech/index.php/2013/03/built-a-new-ubuntu-machine/](http://jamesisin.com/a_high-tech_blech/index.php/2013/03/built-a-new-ubuntu-machine/)

---

### Post by JKyleOKC on 2013-10-22
To answer your earlier question about the difference between sudo and gksu/gksudo: These three commands all do approximately the same thing, which is to allow execution of a single command with root privileges. The difference lies in what they do with the environment variables that are carried along behind the scehes. Basically, sudo is for use at the command line; the two "gk" variants are for use when the command being executed uses the GUI, such as "gusudo nautilus" -- using sudo for this can cause some hidden files to be written with root as their owner, which can then cause problems later such as an inability to boot!

As for where files get installed, they can be almost any place but the usual standard for all of the *buntu flavors is to put them in /usr/bin rather than in /bin (which one would expect to be the right place, from reading its definition). System administrative programs usually go into /usr/sbin; global configuration files go into /etc while user-specific configuration files usually go into your home directory as hidden files; having "." as the first character of the file name makes it hidden.

Hope this helps; you definitely seem to be picking it up quite rapidly!

---

### Post by adi06 on 2013-10-24
Thanks all for help, i learned a lot in 2 days, and i think i'm 20% filled with information out of 100% of linux word ^_^
When i'll read all the topics of this post i'll be upto 40%, hopefully will learn more from u ppl.
Will post back with more questions soon, after finishing with current info.

Greatly Thankful

---

### Post by 3rdalbum on 2013-10-24
I guess nobody else noticed, but you said that your 9 GiB ext 4 partition was mounted at /home - but the screenshot clearly shows that it's not. It's just an extra partition. If it was mounted as /home it would not appear in the sidebar as a hard disk. Looks like you made a mistake in the Ubuntu installer.

Anything that you save into /home will go into your 10 GiB / partition, not the 9 GiB partition.

If you still want the 9 GiB partition to be used as /home, you'll need to move everything out of your existing /home onto the 9 GiB partition, and then modify your /etc/fstab file to mount the partition at the location "/home".

When I say "out of your existing /home", I don't mean out of your personal home directory. I mean, in that screenshot you posted above, you'd double-click on the "home" icon in the main part of the window, do a Select All, and then cut and paste into the 9 GiB partition.

For new users I'd generally recommend using just one partition for the whole Ubuntu system, including /home. When newbies do their own partitioning they usually overestimate how much space they should use for / and swap, (I've seen 100 GiB and 14 GiB respectively... far too much) and then as a consequence their /home partition doesn't have enough room for all their files! Even though I'm not a new user, my server and laptop use one partition for Ubuntu, there's really very few downsides.

---

### Post by adi06 on 2013-10-26
> **3rdalbum said:**
> I guess nobody else noticed, but you said that your 9 GiB ext 4 partition was mounted at /home - but the screenshot clearly shows that it's not. It's just an extra partition. If it was mounted as /home it would not appear in the sidebar as a hard disk. Looks like you made a mistake in the Ubuntu installer.



Good catch, Bashing-Om did mentioned about that, and he said maybe something went wrong.
The partitioning process was fairly starlight forward.

I had 21GB free space, unpartitioned, which i made by shrinking my C drive.
i tried to make a primary 10 gb for root, after that the remaining free disk became unusable. so i had to delete the 10GB and make the 21GB logical/extended.
I made 10GB for ubuntu OS which i mounted at root /
2GB swap
8.9 GB Ubuntu drive, which i mounted at /home.
Then clicked install. and as u see the ubuntu drive is not mounted in /home.
i'll try ur suggestion and make it mount at /home.

I should have mentioned it when i was 1st told that the size is not sufficient.
I am only days old ubuntu user, and at most i'll test my php development using lampp.
and won't be installing other software or storing songs or any data on linux drives.
But if such usage will still cost the space some problem, then i'll make big partitions. But what could cost me space with my setup, if any?
Or will i'll be okay?

---

### Post by brian-9 on 2013-10-28
Hi you guys,  I dabble with Ubuntu long term, still not sure if worth it. I have the kind of partition problem as above. My "boot "  folder is full with updates and I do not know what to do about it. I can do one of two things - reboot and hope the "boot" folder problem disappears or sit down a week to read through the above and try to get  to the bottom of it.With the new salamander here I would like to re- format and start from scratch.
Can you quickly explainthis procedure.

Brian

---

### Post by adi06 on 2013-10-28
> **brian-9 said:**
> My "boot "  folder is full with updates and I do not know what to do about it. I can do one of two things - reboot and hope the "boot" folder **problem** disappears
Brian

Hi,

From you comment i do not understand what problem(s) you are having. Can you please eleborate more, so someone more knowledgeable then me can help u easily, and maybe if i could understand and help.
What do u mean by your boot folder is full of updates? what kind of updates and what of that?
And what problem you have with Boot Folder?

**Edit:**
oldfred to the rescue, hehe 
@brian-9 oldfred is right, and he will surly help u resolve ur issue, follow him as he suggested.

---

### Post by oldfred on 2013-10-28
@ brian-9
Please start a new thread and not hijack this one. 
Plus which issue are you interested in.  A full /boot or how to install and suggested partitioning. 
Post current partitioning with screen shot from gparted or 
sudo df -h
       sudo parted /dev/sda unit s print
    And if you cannot boot use live installer version.

---

### Post by Bashing-om on 2013-10-28
brian-9; Hi !

The answer is relative to what you presently have on your system that you may want to save and known plans for how you intend to use your system.

If sausy salamander is to be the only operating system installed and you want the install to be as simple as possible; then by all means a standard install allowing the install wizard to set up this standard install is all that is required.

Down load the .iso,
Verify the .iso (md5sum) ,
Burn the .iso as an image to DVD,
Set to boot the DVD device as 1st boot priority in bios,
Boot this liveDVD, depress shift key soon as bios screen clears ->language screen -> boot options screen -> choose "check disk",
Choose "try ubuntu" and test all hardware functions as expected,
Choose "install ubuntu" -> "erase disk and install ubuntu", answer the locale and user and password questions.
DONE

Else, you may consider cleaning up and - updating - your present install and doing the version upgrade online and the installer will do it's best to keep all the current configuration settings and user files.
Additional information from you will be required to render our advise. When you are ready to upgrade - Remember to;
a) disable 3rd party PPAs prior to upgrading
b) disable the screensaver
c) backup any important data, things can and have and do go wrong -> power failure or cats or dogs or children whatever interrupts  the update process. If this does happen, the better recourse is to try and recover from a liveDVD.

You will have to decide what route you want to employ as only you know your system, what data you have to backup (in any case, good backups are standard practice), how you use your system, and how you need the system set up.

Again, if you are happy with a standard install, and no data to backup -> standard install and be done with it !
I favor doing a clean install myself each time I upgrade to the next version. 

[INDENT][INDENT]it is all in what you want to do
[/INDENT][/INDENT]

---

