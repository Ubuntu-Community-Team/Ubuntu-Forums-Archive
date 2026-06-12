---
title: "Run On Second Drive"
date: 2013-01-11
forum: General Help
---

### Post by Mike Green9 on 2013-01-11
[FONT=Arial, sans-serif]Hi.[/FONT]
 

 [FONT=Arial, sans-serif]I have a dual boot (Windows 7 & Ubuntu 12.10) system, with 2 drives. The second drive (partitioned identical to the first) is used purely for backups. Ubuntu is on sda4 and sdb4. (Windows is on sda1 & sdb1.)[/FONT]
 

 [FONT=Arial, sans-serif]Under Windows, I used EasyBCD to set up a dual boot. When I installed Ubuntu, I told it to put its boot record alongside Ubuntu. So when I boot, I start with the Windows dual boot Menu, I select 'Ubuntu', and end up in the Ubuntu Boot  Menu (Grub2), and select 'Ubuntu'.[/FONT]
 

 [FONT=Arial, sans-serif]Periodically, under windows, I do an exact copy, Windows partition by Windows partition, to the second drive. [/FONT] 
 

 [FONT=Arial, sans-serif]As a test, I remove the first drive, boot off the second, and everything is fine. I would like to do the same for Ubuntu.[/FONT]
 

 [FONT=Arial, sans-serif]In Terminal, I:[/FONT]
 [FONT=Arial, sans-serif]	sudo dd if=/dev/sda4 of=/dev/sdb4 conv=noerror,sync bs=8192[/FONT]
 

 [FONT=Arial, sans-serif]Then I removed the first drive, and ran on the second. Windows works fine, but when I select 'Ubuntu' on the boot, I never get Grub2. I gather I am missing the Ubuntu boot record on the second drive. [/FONT] 
 

 [FONT=Arial, sans-serif]Question: I want to be able to run solely on the second drive should the first drive fail. How can I get Grub2 on the second drive?[/FONT]
 

 

 [FONT=Arial, sans-serif]Thanks,[/FONT]
 

 [FONT=Arial, sans-serif]M....[/FONT]

---

### Post by dcstar on 2013-01-11
> **Mike Green9 said:**
> 
..........
Question: I want to be able to run solely on the second drive should the first drive fail. How can I get Grub2 on the second drive?

[LIST=1]
[*]Stop wasting time on fancy fonts - it does nothing except annoy people using these forums.
[*]Boot off the second Ubuntu install, then: ```
sudo dpkg-reconfigure grub-pc
``` and select that drive to install the boot loader.
[/LIST]

---

### Post by oldfred on 2013-01-11
I do not really know EasyBCD, but it uses grub4dos and chainloads to Ubuntu's grub2. Then Ubuntu has to be installed to the PBR or partition boot sector.

Run the Boot-Info report and post the link to confirm where everything is installed. You can just run from your install if you want.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

Change to your Ubuntu partition, but this should be the PBR or partition boot sector.
       sudo dd if=/dev/sda1 bs=512 count=1 | hexdump -C

---

### Post by Mike Green9 on 2013-01-11
[FONT=Arial, sans-serif]Hi. 
[/FONT]


[FONT=Arial, sans-serif]Thanks for the prompt responses.
[/FONT]
[FONT=Arial, sans-serif]
[/FONT]
[FONT=Arial, sans-serif]I started Boot Repair as suggested, and backed up as requested. I was afraid to do the recommended repair. I did do the Boot Info Summary if that helps:[/FONT]
   	 	 	 	 	 	   [FONT=Arial, sans-serif][COLOR=#0099ff]	[/COLOR][[COLOR=#0099ff]http://paste.ubuntu.com/152240[/COLOR]]("http://paste.ubuntu.com/1522406/")[/FONT]
  [FONT=Arial, sans-serif]
[/FONT]
[FONT=Arial, sans-serif]If you still suggest that I do the recommended repair, than I will. Please note that I'm booting off sda – and I want the repair to be made to sdb  (Ubuntu on sdb4).[/FONT]
 

 

 [FONT=Arial, sans-serif]I'm not sure what oldfred is referring to re fancy fonts. I prepare all my posts in libreoffice, then I cut and paste into the forum thread. I apologize if that causes a problem.[/FONT]
 

 [FONT=Arial, sans-serif]Thanks,[/FONT]
 

 [FONT=Arial, sans-serif]M...[/FONT]

---

### Post by oldfred on 2013-01-12
Script had trouble mounting several partitions on sdb. 

You also will have issues in trying to copy from sda to sdb. It seems like you are trying to manually do a RAID 1 configuration.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

But if you use dd to clone a drive, it has to be same size to same size and then both drives cannot be connected as the same UUIDs may both be used and data not consistent. 
If you just copy data to second drive it will not be bootable as first drive as UUIDs and grub & fstab will have incorrect entries. Not sure how Windows does it.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
    
Ways to fully backup Windows:
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

    
But my preference is to separate data from system. And have a system on every drive. So I would suggest Windows on one drive with separate data partition, Linux on other drive with separate data partition  (and or /home). Then backup regularly with rsync the data from one drive to the other (and DVDs or flash), but not attempt to backup system. If Ubuntu drive fails, you can fully reinstall in about an hour and reuse backup data or /home. Windows is not as easy to restore, but still probably better than trying to manage the changing drive issues.

In the old days when XP hard coded the drive in boot.ini and Ubuntu also used hard coded devices not UUID, your copy may have worked. But now both Windows & Ubuntu use unique partition IDs and then you start to have issues.

---

### Post by Mike Green9 on 2013-01-12
[FONT=Arial, sans-serif]Hi.[/FONT]
 

 [FONT=Arial, sans-serif]You have cleared up some of the confusion I have encountered: [/FONT] 
 

  [FONT=Arial, sans-serif]	On close inspection, I realize that some Partitions on the second drive have the same[/FONT]
[FONT=Arial, sans-serif]uuids as the 'parallel' Partitions on the first drive :o.[/FONT]
 

 [FONT=Arial, sans-serif]I read somewhere: 1 trillion UUIDs would have to be created every nanosecond for 10 billion years to get a duplicate. [/FONT] 
 

 [FONT=Arial, sans-serif]How is it that Ubuntu is giving the same uuids for different partitions on my own system, and how can I make them different :confused:??[/FONT]
 

 [FONT=Arial, sans-serif]Thanks,[/FONT]
 

 [FONT=Arial, sans-serif]M....[/FONT]

---

### Post by oldfred on 2013-01-12
If you used DD or gparted to copy the partition it is going to copy the UUID so it is identical. That is the only way grub & fstab will work with the clone. But you cannot then keep clone plugged in.

       Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX
if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid

---

### Post by Mike Green9 on 2013-01-12
Okay - dd copies uuid;s - that solves that mystery :).

What I have done a few hours ago is unplug the second drive (I also turned the drive OFF in the BIOS).

For now, I will run Ubuntu on ONE drive, and use sbackup to make pertinent data backups to one of the Windows partitions. That will work for me at this point.

Now my new problem - when I boot, well you guessed it, Ubuntu is hanging trying to mount the unplugged drive. 

Two more questions:

1. Why doesn't Ubuntu look at the BIOS for the drive setup?
2. What do I have to do to let Ubuntu know that there is only one drive?


Thanks again,

M...

---

### Post by oldfred on 2013-01-13
Perhaps with the changes to fstab or grub your have crossed/mixed which drive should be used. Double check fstab that you are only mounting UUIDs on the drive you have still installed and reinstall grub with Boot-Repair.
       # To clear cache and get new view:
sudo blkid -c /dev/null -o list
sudo cat /etc/fstab
    
BIOS only reports drive & size, and system parameters, but partition configuration is from operating system.

---

### Post by Mike Green9 on 2013-01-13
Thanks Oldfred.

I will try re-installing Grub (when I figure out how to do that :)).

While you are on  the line, what DIRs do you recommend to backup? Currently, I am backing up (sbackup):

/var
/home
/usr/local
/bin
/etc

& excluding
/tmp
/media
/var/spool
/var/tmp
/var/cache
/var/run


Using my second drive plugged in as the first and only drive, I did a Live CD fresh install. I then installed sbackup and Restored from yesterday (data from my up and running Ubuntu).

Mostly looks pretty good. However, I am missing some software I installed such as Jedit. And, I no longer have ALACarte in the dash (I can't remember what I did to get it there).

Of course the restored grub is looking for that darn second drive...

Thanks for hanging on.


M...

---

### Post by apollothethird on 2013-01-13
> **Mike Green9 said:**
> 
 [FONT=Arial, sans-serif]I'm not sure what oldfred is referring to re fancy fonts. I prepare all my posts in libreoffice, then I cut and paste into the forum thread. I apologize if that causes a problem.[/FONT]

Hi, Mike.  I often use Libreoffice for preparing my message.  To avoid the posting problem that you may experience, I always paste the text in to a text editor (gedit), then copy it from there to paste to the form.

The text editor doesn't retain the formating codes and the resulting text to the form is plan.

The other user is right about the annoyance of the havoc a word processor does to a form when trying to read messages.

Your spacing if off on the current one that I'm replying to.  Copying first to gedit then copying from there will avoid all the problems... even some you haven't gotten to yet.  There is lots of embedded codes in word processors.

> **Mike Green9 said:**
> Thanks Oldfred.

I will try re-installing Grub (when I figure out how to do that :)).

While you are on  the line, what DIRs do you recommend to backup? Currently, I am backing up (sbackup):

/var
/home
/usr/local
/bin
/etc

& excluding
/tmp
/media
/var/spool
/var/tmp
/var/cache
/var/run


Using my second drive plugged in as the first and only drive, I did a Live CD fresh install. I then installed sbackup and Restored from yesterday (data from my up and running Ubuntu).


The only directories I'm concerned to be ensured backed up are the ones that have my data on it.  That would be /home and possibly /var/local.  I also put my programs in /var/opt.  I feel like most of the other directories can be restored with fresh installs.  I notice from your current message that you are familiar with fresh installations.

Of course if you're running web pages you should make sure your web directories are backed up, as well as the data for your mysql databases.

I have my virtual web pages in a directory, /home/web/site1, /home/web/site2, etc.

I often perform a fresh install of my personal computer, every time a new Ubuntu version is released.  It doesn't take me long to put my data in place on the new installation.

I upgrade my main server every couple of years.  Because of the experience in upgrading my personal computer the way I mentioned, when I need to change hardware or perform a fresh upgrade of one of my servers, I find it rather easy to do.

The key is having some systematic process for the way things are setup.

By the way, I didn't notice your Libreoffice formating codes in this current message.  Did you eliminate the step of using Libreoffice in the message preparation?

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by oldfred on 2013-01-13
I use rsync. And started with this:
       Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

    [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
backup the following:

   1. /home (Users' personal files and settings) including keys in ~/.gnupg
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script to generate the backup
5. list of installed applications 

       Other applications if data not separate
apache, any sqldb, tomcat, web folders, etc
Document system backup or for multiple install:
[http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm](http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm)

    Some folders to exclude from /home:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

       More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

       rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
#[http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4)
more scripts:
[http://ubuntuforums.org/showthread.php?t=1319155](http://ubuntuforums.org/showthread.php?t=1319155)

---

### Post by Mike Green9 on 2013-01-14
[QUOTE=......
By the way, I didn't notice your Libreoffice formating codes in this current message.  Did you eliminate the step of using Libreoffice in the message preparation?

-- L. James


Hi Mr. James.

Thanks for the info.

Yes I know about control characters in word processors like libre office - I just got careless and skipped the 'paste into a text editor' step. This is in fact what I did for my last post.


Thanks,


M....

---

### Post by Mike Green9 on 2013-01-14
Hi.

I am slooowly documenting a restore from a fresh install. Mostly appears to be okay. However, some programs like jedit do not appear to be there. 

If I look in etc, there is a '.jedit' folder. But I can't seem to invoke. I tried the Dash Home and enter jedit trick, but nothing happens. This is the same for other apps like xournal, bluefish, cream.... They appear on the Dash, but no response when I click on them. Also, the icons are funny - like a spring with cap.

What's worse is that I cant' seem to re-install, since Ubu thinks they are already there. 

So, what Directories did I forget to backup that prevent me from invoking what appears to be there?


Thanks,

M...

---

### Post by oldfred on 2013-01-14
When you backup /home it saves the configuration or data files each application installs in the user's /home. But if a new install the application is not reinstalled. As part of my resync script I run the dpkg to create a current list of my installed apps. Then it is easy to reinstall with all the apps I have added.

       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

---

### Post by Mike Green9 on 2013-01-18
Hi.

Thanks to your input, I have resolved this issue. 

Running solely on my second drive:
I did a fresh CD install
Re-installed all my apps
Restored data from:     home/mg/       & /etc/apt    (all my data files are on other partitions)
Some aesthetic fiddling


System works like a charm :D. All my custom setting are there. 

I will now unplug the second drive, and plug in the first. Running on my 'live' drive, I will repeat the process. I will log all changes, and do backups to USB as required. If the drive crashes, the second one is waiting in the wings.

It is too bad that there is no simple way to backup the apps - saving the hassle of re-installing them.  Or, ideally, a "dd" type backup that doesn't alter destination uuid's and allows the destination partition to be booted.

This has been a great learning process. I am an Ubuntu convert.

Thanks again for your help. I will mark the thread as 'solved'.



M....

---

### Post by oldfred on 2013-01-18
Glad you got it working. :)

Only if installing exactly the same Ubuntu version, and have not housecleaned out the debs.

       Location of downloaded debs
/var/cache/apt/archives/

            Offline Updates:
[http://keryxproject.org/](http://keryxproject.org/)
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
Download once for many machines
How To Install Apt-Cacher-NG in Ubuntu Linux
[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)

---

