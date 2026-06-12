---
title: "Try Ubuntu option changes to full install"
date: 2019-07-16
forum: General Help
---

### Post by Gnusboy on 2019-07-16
Hey y'all

I'm trying to repair some issues with Ubuntu 16.04.1 LTS using the live DVD in the "Try mode" but hit a problem. I've been working to fix things after my system went bonkers. After regaining some  control over it I was close to fixing the problems. I needed to use  a clean version of 16.04 to finish things up.
I burned the live DVD and it booted just fine. The screen showed a choice between a trial version, or a full install. I chose the trial option, and the screen changed to show an a DVD icon labelled for an Install, and another file with some related Ubuntu programs. I clicked the install button, but that appeared to start a full install. There was nothing indicating that it was still in trial mode. 
The weird part was that it came to a page saying I had to change the partitions on my external HDD.I had set them basically equal in size and had a lot of data on both. I didn't think messing with them was what I should be doing at this point.
So with the choices being Quit, Back, or Install Now, I stopped to ask y'all the question: What the heck should I do now?

---

### Post by wildmanne39 on 2019-07-16
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by Impavidus on 2019-07-16
When you start the live disk, you can choose to start installation right away or try before install, which will give you a live session. There are some other options. You can also start the installer from the live session by clicking on "install", which is what you did. You were still running the live session. The installer runs in a live session. You can just quit it.

---

### Post by Gnusboy on 2019-07-16
Impavidus

Thanks. I've had so much trouble lately, I wasn't sure.

---

### Post by Gnusboy on 2019-07-16
wildmanne39

Sorry
I didn't know I'd messed with the colors. They don't show up on my side.

---

### Post by Gnusboy on 2019-07-17
I thought I'd gotten over the various system problems, but now I don't know. 
I started a live DVD session, but I got confused when the TRY install came to a point on my external drive and called on me to resize the partitions on my External Drive. 
I couldn't understand why the installation came up on the external drive instead of the main internal. The situation made it look like operation was required. 
As it didn't show that I was still in the TRY mode, I worried that I was in regular installation mode. I knew if I took a miss step I'd have much bigger problems.  
I started reading the tutorials and found that I could click through and go forward to next page. Unfortunately, That led a to a different problem.
To avoid the possibility of Ubuntu setting up on my external drive, I decided I should unmount the external drive and go from there. 
Using the GUI, I couldn't see which partition I needed to actually unmount and disconnect the external drive. Even using the terminal I wasn't sure of how to handle the task.

After a lot of time I decided to back out of the live DVD and then disconnect the drive, then start over.
I had a terminal  and a couple of other browser pages open. The system started getting very slow and then locked up entirely. During this, the internal hard drive was working continuously. 

Every time I tried to close a page to free up the system nothing worked and every click seemed to extend whatever process was in use.I waited several minutes for the system to recover, but it stayed locked with a dark screen. I finally did Ctl-Alt-Delete, but that made a much bigger problem. I was able to get the DVD out, but  as the system was rebooting 

There were about a hundred error messages similar to this: 

SQUASHFS ERROR - UNABLE TO READ fragment cache entry [ao7f484
SQUASHFS ERROR - UNABLE TO READ PAGE, block a07f484 size 4e46

Not all showed the same message, but the ones I read as it scrolled was close to that one.
I just did another reboot without the DVD. The system did not load and it displays the 
unexpected inconsistency error and needs to run fsck manually.

---

### Post by Gnusboy on 2019-07-19
I've come up with a different problem with the live session "Try Ubuntu" 
I can get through the first couple of screens, but the system keeps getting stuck on the resize partitions section. 

I disconnected the external drive to avoid mix ups, but I still have problem. During the install, I get past "install ubuntu alongside" the existing partitions. I didn't realize my HDD was so chopped up. These are the partitions my system is showing.

82.7 GB partition on /dev/sda 7 (ext 2)
73.4 GB partition on /dev/sda 8 (ext 4)
It also notes 5 smaller partitions on the next screen under installation type. I clicked through this section without change.

This chart also shows four different versions of Ubuntu in the system: (Ubuntu 11.10; 16.04 LTS; 12.04.5; 
and 14.04.5 LTS) 

The chart first shows /dev/sda,  
/dev/sda 1 (ext4) with sizes in MB and MB used  
/dev/sda 9 (ext4)
/dev/sda,7 (ext4)
/dev/sda 6 (ext4)
/dev/sda,8 (ext4)
/dev/sda 5 swap 5387 MB unknown

It lists the "Device for boot loader installation as:
/dev/sda  ATA WDC WD 6400 - Which is the size of my original hard drive.
I don't know how to properly resize a partition or which one to resize. 

At the bottom of the page it says "install now" "quit" or "go back."
If I hit the install now button and click through, the next screen shows "No root file system is defined. Please correct this from the partitioning menu" 
If I click through and do nothing, the next page locks up the entire system. I've tried this process again, 4 or 5 more times with the same result.
Can you help get me past this so I can actually get my system working.
I'd appreciate the help.
Thanks.

---

### Post by Gnusboy on 2019-07-20
> **Gnusboy said:**
> I've come up with a different problem with the live session "Try Ubuntu" 
I can get through the first couple of screens, but the system keeps getting stuck on the resize partitions section. 

I disconnected the external drive to avoid mix ups, but I still have problem. During the install, I get past "install ubuntu alongside" the existing partitions. I didn't realize my HDD was so chopped up. These are the partitions my system is showing.

82.7 GB partition on /dev/sda 7 (ext 2)
73.4 GB partition on /dev/sda 8 (ext 4)
It also notes 5 smaller partitions on the next screen under installation type. I clicked through this section without change.

This chart also shows four different versions of Ubuntu in the system: (Ubuntu 11.10; 16.04 LTS; 12.04.5; 
and 14.04.5 LTS) 

The chart first shows /dev/sda,  
/dev/sda 1 (ext4) with sizes in MB and MB used  
/dev/sda 9 (ext4)
/dev/sda,7 (ext4)
/dev/sda 6 (ext4)
/dev/sda,8 (ext4)
/dev/sda 5 swap 5387 MB unknown

It lists the "Device for boot loader installation as:
/dev/sda  ATA WDC WD 6400 - Which is the size of my original hard drive.
I don't know how to properly resize a partition or which one to resize. 

At the bottom of the page it says "install now" "quit" or "go back."
If I hit the install now button and click through, the next screen shows "No root file system is defined. Please correct this from the partitioning menu" 
If I click through and do nothing, the next page locks up the entire system. I've tried this process again, 4 or 5 more times with the same result.
Can you help get me past this so I can actually get my system working.
I'd appreciate the help.
Thanks.

I'm hoping someone can help me figure this out. I've on this problem for nearly 2 weeks. I can't find what I need in in Ubuntu tutorials or elsewhere.

---

### Post by Artim on 2019-07-20
You must have selected "Install Ubuntu" from the Live session (the "try").  No need to resize the boot partition, and you don't want to use the old unsupported versions of Ubuntu (11.10, 12.04).  An install of the new should *replace* all that old stuff, not run alongside it.

---

### Post by Impavidus on 2019-07-20
What is your goal? Do you want to cleanup the old, unsupported Ubuntu systems from your harddrive, do you want to fix your current 16.04 system, do you want a fresh install, just wiping everything that's there to get a fresh start? We can probably help you.

Do you have backups of all your important files on an external and now unplugged drive or in the cloud? In that case, nothing serious can go wrong. If not, create those backups now.

---

### Post by Gnusboy on 2019-07-20
I want to clean up my system so I can move up to the newer versions. I have gotten several error messages and I've been told not to upgrade with a broken system. If I had all of the backups 
I was supposed to have I'd do a wipe and install 18.04. Unfortunately, I don't think I have everything backed up. Deja Dup has not been my friend. When I started to do the original "no space left on device" repair, I found the storage location was completely full. There were 74 files of backups in a Deja Dup folder, but I could not get them open to check. I was able to free to free up enough space from the storage to get it working. I was trying to delete those excess backups when this current problem happened. 

I thought if I got 16.04 working properly I could fix the errors and  get some clean backups. So, that was my plan. Easy Peasy. 

 had been using 14.04 when I setup the 650 GB drive. It was fresh and clean and I divided it roughly in half. I kept the 14.04 on one partition and installed the 16.04 in the other side. 
I do recall seeing some extra options in Grub when it booted, but I rarely looked at them. The first line was 16.04 and and the next line was 14.04 and I wasn't overly curious. I'd boot into one 
or the the other as needed and it just worked. Every thing worked fine until recently. Maybe not perfectly, but it was acceptable at the time. 
All I can think of was the 11.10 and 12.04 were legacy’s left over and buried in the 14.04 version. Do old OS programs work like that? Is it possible that parts of the two became intermingled at 
some point and are the cause of my problems? Is it necessary to repair the 14.04 version or the 16.00 version first, or does it matter?

Can I make backups from within this Ubuntu trial? If so, I can copy  everything over and start over fresh. Would it help to nuke those older  versions - and should it be now, or after the upgrade to 18.00? 

Thanks
I

---

### Post by Artim on 2019-07-20
Are you able to access your Documents, Pictures, Music, etc. folders?  You can access them using a LiveUSB, then copy them over to another USB thumbdrive.  Things like Settings probably need to go away, since the current LTS version is quite different and the settings wouldn't carry over properly.  Find your browser bookmarks, e-mail account settings and store them on the same USB as your other backup stuff, then wipe the drive clean and do a fresh install of the current LTS.  You can create a separate **/home** partition and restore your backups there, but it might be easiest and simplest just to give Ubuntu the whole drive during installation and *then* restore your backed-up stuff.

---

### Post by Gnusboy on 2019-07-20
Hey Artim

I am working in the DVD live session now. It seems to function, but is quite slow for a 10 mbps connection. Getting to the files I need to transfer is a problem. 
All the folders show as empty and owned by Root. How do you change the owner from Root to me? Technically, I am Root, yes?

This is the the chart of my partitions. Which is the boot section? I'd like some help to resize the partitions, if I have to. 
 
I was able to attach this screenshot of some of the current  partitions. These look fractured and it could be difficult adjust  everything Ubuntu wants. Missteps while doing the changes could create bigger problems, yes? 
[IMG]file:///home/ubuntu/Pictures/Instlallion%20screenshot.png[/IMG]

However, everything that's supposed to be shown in the /home folder is either empty, or blocked by root. It's been so long since I needed root powers outside of "sudo" terminal commands, I can't remember the root password or how to access it.
 
If I can get into /home, I can hopefully do a good backup and delete those 74 needless backups. Or, if I can get past root to access and save all of the important stuff. I'm using a DVD with the live session now. All I have handy is a 4 GB USB - 
Wouldn't it be better to reconnect the external drive an copy the files to there.

---

### Post by Artim on 2019-07-20
Oh, my friend, your image link is to a file on your own computer, not to a site that hosts photos.  Try posting it to imgur or something and link us to that site.  Yes, you are root *on the LiveUSB*. The empty folders you are seeing are the ones on the LiveUSB, not the ones on your hard drive.  You have to go into the file manager and click into the hard drive and find *that* home folder.  Then copy that stuff onto a second USB drive while you are in the Live session.

---

### Post by Impavidus on 2019-07-21
I don't use Deja Dup. It may be an excellent tool, I don't know. I think it's important that backups are so simple that you can easily verify that all important files are indeed backed up and you can restore them using only simple tools.

Different Ubuntu releases on your hard drive don't affect each other (except in one way). All live in their own partition and never do anything to the partitions of the other Ubuntu systems. The only exception is the boot loader. Multiple Ubuntu systems can each try to be in control of your boot loader, but only one of them can be at the same time. But that's not your problem.

You can make backups from within your live session. It's one of the great things we can do in live sessions. Once you've got backups of all important files from the old Ubuntu systems, you can delete them.

Use the file manager in your live session. In the side panel you should see all partitions (at least, those containing a file system) of your internal hard drive. Their labels may not mean much to you. Click on such a partition to mount it, then you can browse the file system of that partition. Each of your installed Ubuntu systems has one, maybe you've got others. Find your documents and copy them to an external drive. Yes, you can reconnect your big external drive to store them there, just make sure you safely remove it and unplug it before you begin any partitioning or install Ubuntu. Use right click -> eject or right click -> remove or something like that before unplugging.

---

### Post by Gnusboy on 2019-07-22
Hey y'all

I'm getting an error message I've never seen before. I'll try to open a folder or a file and they show as empty even when I know there are files inside. When I check for documents and properties, under permissions is "Owner: User  #1000" At the bottom of the box is the notation of "You are not the owner, so you cannot change these permissions."

I  have never seen anything like this. This seems to be connected as root  - but there is no description on it. Just to make it more fun, there does not seem to be a coordinated scheme. 

One file opens without problem, but another file in the same folder will be locked by Owner #1000. Some documents have permission with full privileges to "create and delete" but have very little contents or are empty. 

I am also finding files and folders that are missing lots and lots of documents. I've spent years writing and editing documents, and those files appear to be gone. I can't say for sure - I have not checked all the other folders. In several instances, the files within are not formatted the same way I created them. They look  items like machine formatting, or something.

Just now, I found a documents folder that lists 648 items, but it totals 399.2 MB!
That could be accurate, but not in any document folder I have created. If they are lost in the ether - 

This can show up on current files or on things I've had for several years. It's just goofy.  Have anyone seen this and how do I make it go away?

Another thing: I tried to get Deja Dup running again, but it now says I am missing a component of the program. "Package name deja-dup-backend-gvfs could not be resolved." I've not found what that means. 
I am hoping all of this can be fixed. ... 

Thank you for any insight you can offer.

---

### Post by Impavidus on 2019-07-23
This isn't very productive. You may have file ownership messed up, or file system damage, or even a failing hard drive (I don't think that's the case, but I can't rule it out), or maybe you just misunderstand how the system works.

Let's get some real data. Install and run [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) in your live session, create a BootInfo summary and show us the link. Don't run the recommended repair; it may do more damage. Also check the health of your hard drive: [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools). Try the long test. Report the results and we may be able to show you more commands to get to the bottom of this.

---

### Post by Gnusboy on 2019-07-24
[FONT=Times New Roman][/FONT][COLOR=#000000][IMG]file:///home/ubuntu/Pictures/Instlallion%20screenshot.png[/IMG][/COLOR]
[SIZE=4][/SIZE]

---

### Post by Artim on 2019-07-24
Click on that link, Gnusboy... it's a link to a file on your own HDD.  Not visible to anyone else.

---

### Post by Gnusboy on 2019-07-25
Sorry for the delay. 

But I think I have a huge problem right now

I had mucho data toward fixing my system. But a little while ago My  system locked up and I had to do a reboot. Several window and the output  of 3 terminals went poof!
And it's not just that.I rebooted into the live disk,just like always. Now my system shows only 2 partitions. first Partition is 93 GB and is bootable. The second partition is empty! It is 0.0 KB unknown. It also shows Unallocated Space of 547 GB from the 650 GB hard drive.
It's also strange that when I ran it through GParted everything come up looking like always. I'm going to try and send you the output from both tests. 
The scariest thing that's happening for me is that when the system rebooted all the setting and preferences are wiped out. There is no formatting other than bare basics. Folders seem to be empty or gone.
None of the information and responses to the boot-repair are also out of sight. I did get a read out of the boot-repair test in the terminal. But it looks like it did not finish the task. It is just sitting 
at the last line without finishing the command. Seems odd to me. I'm not sure if I can send attachments of the hard drive tests. The tests don't allow for a select cut or copy, so I'm not sure I can figurer it out. If not I'll post them in plain text or on imgur or a similar hosting site. I'm not familar with those, but I'll figure it out.
he biggest thing for me right now is trying to fix my system from today's destruction.
I've neve faced anything like either in Linux or Windows I you know any tricks or tip, I'd welcome any input. I don't know if I should reboot into another live session or pull the disk and see if I can recover from there.

 





I did a lot of looking at how bad my system is becoming and I don't think it's pretty. I had a small problem with Boot-Repair, but I got it worked out. 
Apparently the terminal link it had a glitch and couldn't resolve. But I think I found the error. 
The bigger problem for me is that I had mucho data toward fixing my system. But a little while ago My system locked up and I had to do a reboot. Several window and the output of 3 terminals went poof! I'm going to recall what I can and do over what I can't.
I appreciate your patience and help.

---

### Post by Gnusboy on 2019-07-25
Sorry for the delay. 

But I think I have a huge problem right now

Just now wondered whether the live session will save me from this disaster

I had mucho data toward fixing my system. But a little while ago My  system locked up and I had to do a reboot. Several window and the output  of 3 terminals went poof!
And it's not just that.I rebooted into the live disk,just like always. Now my system shows only 2 partitions. first Partition is 93 GB and is bootable. The second partition is empty! It is 0.0 KB unknown. It also shows Unallocated Space of 547 GB from the 650 GB hard drive.
It's also strange that when I ran it through GParted everything come up looking like always. I'm going to try and send you the output from both tests. 
The scariest thing that's happening for me is that when the system rebooted all the setting and preferences are wiped out. There is no formatting other than bare basics. Folders seem to be empty or gone.
None of the information and responses to the boot-repair are also out of sight. I did get a read out of the boot-repair test in the terminal. But it looks like it did not finish the task. It is just sitting 
at the last line without finishing the command. Seems odd to me. I'm not sure if I can send attachments of the hard drive tests. If not I'll post them on imgur or a similar hosting site.

Terminal:

ubuntu@ubuntu:~$ boot-repair
boot-repair: command not found
ubuntu@ubuntu:~$ sudo boot-repair
sudo: boot-repair: command not found
ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair
 Simple tool to repair frequent boot problems.

Website: [https://sourceforge.net/p/boot-repair/home](https://sourceforge.net/p/boot-repair/home)
 More info: [https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair](https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmp26nil3lr/secring.gpg' created
gpg: keyring `/tmp/tmp26nil3lr/pubring.gpg' created
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp26nil3lr/trustdb.gpg: trustdb created
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
```

ubuntu@ubuntu:~$ sudo apt-get update
Ign:1 cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial InRelease
Hit:2 cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial Release
Get:4 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial InRelease [17.5 kB]
Get:5 http://security.ubuntu.com/ubuntu xenial-security InRelease [109 kB]     
Hit:6 http://archive.ubuntu.com/ubuntu xenial InRelease                        
Get:7 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]       
Get:8 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial/main amd64 Packages [1,876 B]
Get:9 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages [705 kB]
Get:10 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [999 kB]
Get:11 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en [280 kB]
Get:12 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [73.7 kB]
Get:13 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [73.2 kB]
Get:14 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 Packages [7,204 B]
Get:15 http://security.ubuntu.com/ubuntu xenial-security/restricted Translation-en [2,152 B]
Get:16 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 DEP-11 Metadata [200 B]
Get:17 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial/main Translation-en [2,036 B]
Get:18 http://archive.ubuntu.com/ubuntu xenial-updates/main Translation-en [393 kB]
Get:19 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [323 kB]
Get:20 http://archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [241 kB]
Get:21 http://archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 Packages [7,616 B]
Get:22 http://archive.ubuntu.com/ubuntu xenial-updates/restricted Translation-en [2,272 B]
Fetched 3,349 kB in 4s (798 kB/s)  
``` 

```
                               

** (appstreamcli:8130): CRITICAL **: Error while moving old database out of the way.
AppStream cache update failed.
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  boot-sav boot-sav-extra gawk glade2script libsigsegv2 pastebinit python-gi
Suggested packages:
  boot-info mdadm os-uninstaller gawk-doc python-gi-cairo
The following NEW packages will be installed:
  boot-repair boot-sav boot-sav-extra gawk glade2script libsigsegv2 pastebinit
  python-gi
0 upgraded, 8 newly installed, 0 to remove and 769 not upgraded.

```
```

Need to get 1,237 kB of archives.
After this operation, 5,221 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu xenial/main amd64 libsigsegv2 amd64 2.10-4 [14.1 kB]
Get:2 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial/main amd64 glade2script all 3.2.3~ppa4 [36.0 kB]
Get:3 http://archive.ubuntu.com/ubuntu xenial/main amd64 gawk amd64 1:4.1.3+dfsg-0.1 [398 kB]
Get:4 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial/main amd64 boot-sav all 4ppa65 [425 kB]
Get:5 http://archive.ubuntu.com/ubuntu xenial/main amd64 python-gi amd64 3.20.0-0ubuntu1 [194 kB]
Get:6 http://archive.ubuntu.com/ubuntu xenial/main amd64 pastebinit all 1.5-1 [14.6 kB]
Get:7 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial/main amd64 boot-repair all 4ppa65 [12.4 kB]
Get:8 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial/main amd64 boot-sav-extra all 4ppa65 [142 kB]
Fetched 1,237 kB in 3s (370 kB/s)  
```
```
     
Selecting previously unselected package libsigsegv2:amd64.
(Reading database ... 191931 files and directories currently installed.)
Preparing to unpack .../libsigsegv2_2.10-4_amd64.deb ...
Unpacking libsigsegv2:amd64 (2.10-4) ...
Setting up libsigsegv2:amd64 (2.10-4) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Selecting previously unselected package gawk.
(Reading database ... 191939 files and directories currently installed.)
Preparing to unpack .../gawk_1%3a4.1.3+dfsg-0.1_amd64.deb ...
Unpacking gawk (1:4.1.3+dfsg-0.1) ...
Selecting previously unselected package python-gi.
Preparing to unpack .../python-gi_3.20.0-0ubuntu1_amd64.deb ...
Unpacking python-gi (3.20.0-0ubuntu1) ...
Selecting previously unselected package glade2script.
Preparing to unpack .../glade2script_3.2.3~ppa4_all.deb ...
Unpacking glade2script (3.2.3~ppa4) ...
Selecting previously unselected package boot-sav.
Preparing to unpack .../boot-sav_4ppa65_all.deb ...
Unpacking boot-sav (4ppa65) ...
Selecting previously unselected package boot-repair.
Preparing to unpack .../boot-repair_4ppa65_all.deb ...
Unpacking boot-repair (4ppa65) ...
Selecting previously unselected package boot-sav-extra.
Preparing to unpack .../boot-sav-extra_4ppa65_all.deb ...
Unpacking boot-sav-extra (4ppa65) ...
Selecting previously unselected package pastebinit.
Preparing to unpack .../pastebinit_1.5-1_all.deb ...
Unpacking pastebinit (1.5-1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160701-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up gawk (1:4.1.3+dfsg-0.1) ...
Setting up python-gi (3.20.0-0ubuntu1) ...
Setting up glade2script (3.2.3~ppa4) ...
Setting up boot-sav (4ppa65) ...
Setting up boot-repair (4ppa65) ...
Setting up boot-sav-extra (4ppa65) ...
Setting up pastebinit (1.5-1) ...

```
--------------------------------------------------------------------------
It just ends here




I did a lot of looking at how bad my system is becoming and I don't think it's pretty. I had a small problem with Boot-Repair, but I got it worked out. 
Apparently the terminal link it had a glitch and couldn't resolve. But I think I found the error. 
The bigger problem for me is that I had mucho data toward fixing my system. But a little while ago My system locked up and I had to do a reboot. Several window and the output of 3 terminals went poof! I'm going to recall what I can and do over what I can't.
I appreciate your patience and help.

---

### Post by Gnusboy on 2019-07-25
Artim

Is this the link you shared?

[http://technophobeconfessions.wordpress.com/](http://technophobeconfessions.wordpress.com/)

---

### Post by deadflowr on 2019-07-25
> **Gnusboy said:**
> Artim

Is this the link you shared?

[http://technophobeconfessions.wordpress.com/](http://technophobeconfessions.wordpress.com/)

No.
It refers to the image you tried posting in post #18
The img tag only links images from image hosting sites.
To add an image from your computer use the Attachments function.

To use attachments you need to open the advanced editor,
(You can open the advanced editor either with Reply to Thread or the Go Advanced option.
The Quick Reply doesn't have the advanced settings.
In the Advanced editor the Attachments are the paperclip icon in the toolbar.
A popup window will show, then just click on the add files in the upper right corner and select Choose File, then navigate you home directory to where the file is and select it.
Then click on the upload button to upload the image.
The uploaded image will automatically be added to the queue for the post.
Then just click done in the bottom right corner of the popup to close.

---

### Post by Gnusboy on 2019-07-25
[ATTACH=CONFIG]283675[/ATTACH][ATTACH=CONFIG]283674[/ATTACH][ATTACH=CONFIG]283675[/ATTACH]

---

### Post by Gnusboy on 2019-07-25
I'm wondering if some of the problems I'm having can be helped by the live session. Yesterday my system locked up and I was forced to a reboot. When it came up, There were several new issues.
It stripped the formatting out the display. All I get is a rudimentary lines and boxes and the background color, on the pages of Firefox. 
The system partitions mostly gone.I started a live session, in part to clean up my system. After the reboot, it went from 7 partitions down to 1 working partition. Until a day or so ago, I had a 1 TB external HDD attached, but I removed it in case it would have affected some of the problems I'm trying to fix. Prior to the reboot there were five partitions on my 650 GB internal drive. but after there was only one working partition. There was also a second partition but it was completely empty, showing 0.0 kb on it. Oddly, there was another area, not exactly a partition, showing 547 GB of free space. This is approximately the available storage of 1/2 of the external HDD that I disconnected. I can't say what happened, but I've never seen it before. So far, no one I've talked to is familiar with it either.
There are a variety of other goofy stuff two, including a very slow cursor, that doesn't keep up with my slow typing speed. This seems to come and go on an irregular basis, but I'd like to know how to fix it.It appears there are a few other glitches, but these are the big ones.
I definitely appreciate all the help I've been given.
And I've learned more about Ubuntu than I knew. That is a positive education, if only my aged brain can remember it for the next crisis.

Thanks

---

### Post by Impavidus on 2019-07-26
When you reboot, all running applications are gone. That's normal. On a live system, all files are gone too. The rootsystem of a live system only exists in the computer's short-term memory (RAM). The hard drive shouldn't be affected though. If partitions suddenly disappear, you either deleted them somehow or the hard drive is dying. As it reports the result of the self test as failed, that is a possibility to consider. But we still don't have anything solid to go on.

Can you run these two commands while using your live system? Report the output.```
sudo parted -l
sudo df
```

---

### Post by Gnusboy on 2019-07-26
Impavidus

Here's the info.

Did you get the pictures I sent? Iwas trying to send a shot of the GParted view, but it just wouldn't copy. There's a lot of difference between
GParted and the Smart Monitor results.

ubuntu@ubuntu:~$ sudo parted -l 
Model: ATA WDC WD6400AAKS-0 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  93.4GB  93.4GB  primary   ext4            boot
 2      93.4GB  640GB   547GB   extended
 9      93.4GB  172GB   78.7GB  logical   ext4
 7      172GB   328GB   156GB   logical   ext2
 6      328GB   522GB   194GB   logical   ext4
 8      522GB   635GB   113GB   logical   ext4
 5      635GB   640GB   5388MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Model: Optiarc DVD RW AD-7240S (scsi)                                     
Disk /dev/sr0: 1513MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac
Disk Flags: 

Number  Start   End     Size    File system  Name   Flags
 1      2048B   6143B   4096B                Apple
 2      1499MB  1501MB  2425kB               EFI


Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
Error: /dev/sr1: unrecognised disk label
Model: Unknown (unknown)                                                  
Disk /dev/sr1: 101MB
Sector size (logical/physical): 2048B/2048B
Partition Table: unknown
Disk Flags: 

ubuntu@ubuntu:~$ sudo df
Filesystem     1K-blocks      Used Available Use% Mounted on
udev             1846560         0   1846560   0% /dev
tmpfs             378836     25176    353660   7% /run
/dev/sr0         1477840   1477840         0 100% /cdrom
/dev/loop0       1425792   1425792         0 100% /rofs
/cow             1894164   1888628      5536 100% /
tmpfs            1894164       476   1893688   1% /dev/shm
tmpfs               5120         8      5112   1% /run/lock
tmpfs            1894164         0   1894164   0% /sys/fs/cgroup
tmpfs            1894164       228   1893936   1% /tmp
tmpfs             378836        72    378764   1% /run/user/999
/dev/sda6      186096372 104190540  72429596  59% /media/ubuntu/77aacfae-f704-422a-82f5-047bb0dcb95f
/dev/sda8      108338136  55977116  46834700  55% /media/ubuntu/a2aad275-090f-490e-a903-e4b68f52eb19
ubuntu@ubuntu:~$ 


[ATTACH=CONFIG]283684[/ATTACH][ATTACH=CONFIG]283685[/ATTACH]

---

### Post by Impavidus on 2019-07-27
I can see the pictures you attached to posts #24 and #27

parted detects 5 partitions with a file system on your internal hard drive. I don't know why the disks tools doesn't see them, but in case of confusion it's best to trust the command line tools. There are 2 other partitions as well, one is a container for 5 partitions, 1 is a swap partition.

The goal is to find your files, so you can make a backup of them.

Now we'll identify which partition is which.
```
# We start with sda1
sudo mount -o ro -t ext4 /dev/sda1 /mnt
ls -l /mnt
ls -l /mnt/home
cat /mnt/etc/lsb-release
sudo umount /mnt

# Now sda6
sudo mount -o ro -t ext4 /dev/sda6 /mnt
ls -l /mnt
ls -l /mnt/home
cat /mnt/etc/lsb-release
sudo umount /mnt

# Now sda7
sudo mount -o ro -t ext2 /dev/sda7 /mnt
ls -l /mnt
ls -l /mnt/home
cat /mnt/etc/lsb-release
sudo umount /mnt

# Now sda8
sudo mount -o ro -t ext4 /dev/sda8 /mnt
ls -l /mnt
ls -l /mnt/home
cat /mnt/etc/lsb-release
sudo umount /mnt

# Now sda9
sudo mount -o ro -t ext4 /dev/sda9 /mnt
ls -l /mnt
ls -l /mnt/home
cat /mnt/etc/lsb-release
sudo umount /mnt
```
If any of the mount commands gives an error, skip to the next mount command. If the ls or cat commands give an error, just ignore it. If the umount command gives an error, something weird is going on, but I think it's still safe to continue.

As for hard drive status, it mentions test failed, but all parameters show as OK. I suspect the test didn't complete. Once you've got all your files backed up, you should wipe your hard drive and start fresh.

---

### Post by Gnusboy on 2019-07-27
This may post twice. Apologies


~$ 
ubuntu@ubuntu:~$ sudo mount -o ro -t ext4 /dev/sda9 /mnt
ubuntu@ubuntu:~$ ls -l /mnt
total 120
drwxr-xr-x   2 root root  4096 May 29 14:57 bin
drwxr-xr-x   3 root root  4096 May  2 11:54 boot
drwxr-xr-x   2 root root  4096 Feb  8  2017 cdrom
drwxr-xr-x   5 root root  4096 Jul 19  2016 dev
drwxr-xr-x 137 root root 12288 Jun 17 16:57 etc
drwxr-xr-x   3 root root  4096 Feb  8  2017 home
drwxr-xr-x   2 root root  4096 Jun 12 19:37 homebackup
lrwxrwxrwx   1 root root    32 Nov  9  2017 initrd.img -> boot/initrd.img-4.4.0-98-generic
lrwxrwxrwx   1 root root    32 Oct 11  2017 initrd.img.old -> boot/initrd.img-4.4.0-97-generic
drwxr-xr-x  22 root root  4096 Nov 23  2017 lib
drwxr-xr-x   2 root root  4096 Feb 21 15:46 lib64
drwx------  11 root root 16384 Feb  8  2017 lost+found
drwxr-xr-x   3 root root  4096 Feb  8  2017 media
drwxr-xr-x   2 root root  4096 Jul 19  2016 mnt
drwxr-xr-x   3 root root  4096 Feb 11  2017 opt
drwxr-xr-x   2 root root  4096 Apr 12  2016 proc
drwx------   8 root root  4096 Feb 18 14:17 root
drwxr-xr-x  12 root root  4096 Jul 19  2016 run
drwxr-xr-x   2 root root 12288 Jun  7 10:48 sbin
drwxr-xr-x  12 root root  4096 Dec 18  2018 snap
drwxr-xr-x   2 root root  4096 Jul 19  2016 srv
drwxr-xr-x   2 root root  4096 Feb  5  2016 sys
drwxrwxrwt  26 root root  4096 Jul  4 18:54 tmp
drwxr-xr-x  11 root root  4096 Jul 19  2016 usr
drwxr-xr-x  14 root root  4096 Jul 19  2016 var
lrwxrwxrwx   1 root root    29 Nov  9  2017 vmlinuz -> boot/vmlinuz-4.4.0-98-generic
lrwxrwxrwx   1 root root    29 Oct 11  2017 vmlinuz.old -> boot/vmlinuz-4.4.0-97-generic
ubuntu@ubuntu:~$ ls -l /mnt/home
total 148
drwxr-xr-x 38 1000 1000 147456 Jul  4 17:24 jess
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ cat /mnt/etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.6 LTS"
ubuntu@ubuntu:~$ sudo umount /mnt</pre>
bash: syntax error near unexpected token `newline'
ubuntu@ubuntu:~$ sudo umount /mnt</pre>
bash: syntax error near unexpected token `newline'
ubuntu@ubuntu:~$

---

### Post by Impavidus on 2019-07-28
Your /dev/sda9 partition is your 16.04 system and your home directory, which should contain all your files, is there too. I don't know what user ID your livedisk uses, it's not 1000, but that shouldn't be much of a problem.

Is your Ubuntu 16.04 system the place where you've got your files stored that you haven't backed up yet? Are they all somewhere in your home directory? Make sure your sda9 is mounted read-write```
sudo mount -t ext4 /dev/sda9 /mnt
```Previously, I asked you to mount read-only, as there were reasons to suspect filesystem damage, but that doesn't appear likely now.

Now, we don't want complications from running a file manager as root or making your backups in the terminal. It isn't hard, but I can't give you the full command without knowing where exactly your files are and where your backup drive is. So let's try a dirty trick. We'll chown your home directory to the live session user and use the file manager to copy everything to your backup drive. This is the command:```
sudo chown -R $USER /mnt/home/jess
```This will make it impossible to login when you boot your 16.04 system, but you're going to wipe that anyway. If you wish to reverse the above command, use```
sudo chown -R 1000 /mnt/home/jess
```
After that first chown command, you can use the file manager to copy the files you need from your home directory (which you can find at /mnt/home/jess) to your external backup drive.

Then check again if you've got backups of all your important files and know how to restore the backups.

BTW, in your last post you made an error in the umount command. For some reason a trailing html tag appeared.

---

### Post by Gnusboy on 2019-07-29
Well this has been a process.  I was so low on space that none of my programs would function or open. I started deleting every file I thought was deletable, only to find that everything I sent to trash went to a different place, so I had to do that all over again, item by item.
I was trying to use the terminal links you sent, but for some reason they didn't work for me. I tried to figure it out, I ran out of my time to do other things I'm behind on.
While I searched for things to get rid of, I noticed something I've never seen before. As I moved back and forth through the partitions looking for stuff to get rid of, when I changed from one to another the partitions suddenly disappeared from the screen sidebar. 
It it was a process to reinstate them, but I got it fixed. I've never seen that before.
Also, I keep finding out that most of the files I try to delete are root and that doesn't work. When I check a folder for properties, they appear to be empty. As far as I can tell, most of the ones I want to go have data, but no way to get rid of it.

This process would go faster if I could figure out a way to delete bigger files without screwing things up. I don't have a lot of extraneous programs, but I'm I can throw them out without problems.

---

### Post by Impavidus on 2019-07-30
I get the impression that you're running through fog. You try very hard to fix your problem, but you can't see where you're going and what lies around. Whenever I try to help you take a step towards solving the problem, you report a failure because of something completely unrelated. Now you report a full hard drive. You didn't mention that before.

To make it clear, you've got some problem with Ubuntu 16.04. You want to get 18.04 installed. You've some old systems on your hard drive that you want to get rid of (the old systems, not the drive). The solution is: Backup all important files, wipe the hard drive and install Ubuntu 18.04.

Don't try to fix your system, don't try to remove files from your internal hard drive, don't even boot your installed system. You're going to wipe it anyway.

What's the status of your backups? Use your live disk to create any backups you need. You can use some fancy backup tool or rsync or simply use the file manager to copy files to an external drive. I don't care how you do it. You may have to run your file manager with root permissions to access your files or first chown them using the terminal.

Whenever you run some commands, show the exact commands and the complete output. It's more helpful than "it didn't work."

Whenever you use the mount command to mount a partition, it no longer appears in the side panel of the file manager. That's normal. You can access the partition from the file manager by navigating to the directory used as its mountpoint. In the examples given, that's /mnt.

---

### Post by Gnusboy on 2019-08-01
[SIZE=1][FONT=times new roman]Impavidus,

Sorry to take so long getting back. Sometimes life slathers you in honey and stakes you down over an ant hill.

Please understand that I appreciate everything you are helping me with. I get that I've been a bit slow on the uptake. I'm juggling several balls - as, undoubtedly, are you. 

Part of my problem is that I don&#8217;t always know how to describe what I see. When I'm looking at things I don't fully understand it's hard for me to explain what I need.
As a result I use terms that are not accurate and it can lead to confusion. When I have a problem, I always try to work it out, but that can involve hours of 
looking for information and reading what to do and how to do it. 

Through the years, I've tried to fix problems on my own, but when it didn't immediately work or I couldn't figure it out, or ran out of time, I would usually drop the effort mid-job and leave it. Without a need to use it, I'd forget what I had learned. 

This is one reason why I appreciate your time and knowledge. I have learned more about Ubuntu in the last few days than I could by studying a manual.
 
My hard drive is not full - it's just stuck on "no space left on device."
This is probably sounds dumb as hell, but I don&#8217;t know how to get from the Firefox file manager to the /dev/sda9 file manager in the terminal. I spent a lot of time looking through terminal &#8220;help&#8221;
and &#8220;info&#8221; but could not find that answer &#8211; which is why I had
not done the backups.

Although I can&#8217;t get to files in the 113 GB volume, I can get access to the folders in other volumes and  have found most of my document files scattered through the other partitions. There are also several Deja Dup folders that I have not searched.
[/FONT]
[FONT=times new roman]
 [/FONT]
[FONT=times new roman]Unfortunately, I&#8217;m off the grid for the rest of the day. I apologize. If you are still will to help me, I&#8217;ll be free for the rest of the week.[/FONT]
[/SIZE][SIZE=5][FONT=times new roman][SIZE=1]Jess  [/SIZE]
[/FONT][/SIZE]

---

### Post by Impavidus on 2019-08-02
Take your time to find all files you want to secure. Do you need help to gain access to your 113GB partition (known as /dev/sda8)?

"No space left on device" means exactly what it says: the filesystem doesn't have enough capacity to store your file. This means that either the partition is full, or it has reached the limit on the number of files that can be stored there. The [s]fd[/s] df command can tell you:```
# How many bytes can we store?
df

# How many files can we store?
df -i

```Those commands will tell you the current usage of all currently mounted filesystems.

---

### Post by Gnusboy on 2019-08-02
Hello
Thanks for hanging on. Here is the results from df and df -i
If I understand this, it looks like
SDB 1 is using just 1% of available drive space. Is sdb1 the external drive?
SDA 9 is using 97% of available space which might account for the "No Space Left on device" error message. Is that right? To fix this I need to clear out some files to open it for use again.
I thought SDA 9 was the only partition mounted, but I looked up the DF cmd which says that all partitions shown are mounted. Is SDA 9 also the boot?

On the df -i view, SDA 9 is shown with  4808704  317780  4490924    7% /mnt, which is different from what is list above. I don't know the significance of that. See that output down page.

Another topic: Is there a way to tell what sda 9 coresponds with which partition? C*an *I see the files in a particular SDA? 

I just checked and it appears I have full sccess to the 194 GB partition. Multiple files, etc. Unfortunately, I did not write many current files to the partition. So, I'm out several documents - unless I have them in a different partiion 
or in a Deja Dup backup.


----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
As I search for the files to backup, I've been stopped by many different error messages. These are some of the ones I get. I have multiple /home directories in the separate partitions. I can access a few, but the others
are locked by  Root 
Some of the files I have looked for during the last fw days that were "root" seem to have been changed and assigned properities to me. Is this from chown I did yesterday?  Is there a way to change the root owned files to me?
Also, will you be online over the weekend in case I need some advice? Down want to bother you if you are relaxing.


Again, thanks


Error messages:

1) Unhandled error message: Error when getting information for file '/home/ubuntu/Documents': No such file or directory
Unable to find the requested file. Please check the spelling and try again.

2) /home/ubuntu You do not have the permissions necessary to view the contents of &#8220;ranhanrio&#8221;

3) LibreOffice could not save important internal information due to insufficient free disk space at the following location:
/home/ubuntu/.config/libreoffice/4/user/backup
You will not be able to continue working with LibreOffice without allocating more free disk space at that location.
Press the 'Retry' button after you have allocated more free disk space to retry saving the data.

4)Error saving the document SUNP0009:
There is no space left on device /home/ubuntu/Pictures/Wallpapers/SUNP0009.od

5) Libre Office 5.1.6.2. 
Error saving the document SUNP0009:
Object not accessible.
The object cannot be accessed due to insufficient user rights.
--------------------------------------------------------------------------------
DF and DF -i readouts.
```
**ubuntu@ubuntu:~$ df**
Filesystem     1K-blocks      Used Available Use% Mounted on
udev             1846560         0   1846560   0% /dev
tmpfs             378836     39436    339400  11% /run
/dev/sr0         1477840   1477840         0 100% /cdrom
/dev/loop0       1425792   1425792         0 100% /rofs
/cow             1894164   1894164         0 100% /
tmpfs            1894164    302264   1591900  16% /dev/shm
tmpfs               5120         4      5116   1% /run/lock
tmpfs            1894164         0   1894164   0% /sys/fs/cgroup
tmpfs            1894164    740908   1153256  40% /tmp
tmpfs             378836       104    378732   1% /run/user/999
/dev/sdb1         999320        60    999260   1% /media/ubuntu/897fbe47-71a3-4afa-9722-109fc80bc2a4
/dev/sda9       75540592  68952140   2728128  97% /mnt
/dev/sdb3      451348860  78109640 373239220  18% /media/ubuntu/205504c6-6bf7-4fc0-a732-4ea634c2d00a
/dev/sda8      108338136  55917732  46894084  55% /media/ubuntu/a2aad275-090f-490e-a903-e4b68f52eb19
/dev/sda1       89608576  13460184  71573460  16% /media/ubuntu/d936da7d-f118-4a64-87cb-ea8377a17d59
/dev/sdb2      524204856  81600108 442604748  16% /media/ubuntu/d60ed036-350a-4524-833e-c91e7dd76fc3
/dev/sda6      186096372 104190540  72429596  59% /media/ubuntu/77aacfae-f704-422a-82f5-047bb0dcb95f

```
```
**ubuntu@ubuntu:~$ df -i**

Filesystem       Inodes   IUsed    IFree IUse% Mounted on
udev             461640     598   461042    1% /dev
tmpfs            473541     866   472675    1% /run
/dev/sr0              0       0        0     - /cdrom
/dev/loop0       202955  202955        0  100% /rofs
/cow             473541   35926   437615    8% /
tmpfs            473541     181   473360    1% /dev/shm
tmpfs            473541       7   473534    1% /run/lock
tmpfs            473541      16   473525    1% /sys/fs/cgroup
tmpfs            473541   28658   444883    7% /tmp
tmpfs            73541      43   473498    1% /run/user/999
/dev/sdb1              131072      11   131061    1% /media/ubuntu/897fbe47-71a3-4afa-9722-109fc80bc2a4
/dev/sda9        4808704  317780  4490924    7% /mnt
/dev/sdb3             110240  110240        0  100% /media/ubuntu/205504c6-6bf7-4fc0-a732-4ea634c2d00a
/dev/sda8       6889472 1810915  5078557   27% /media/ubuntu/a2aad275-090f-490e-a903-e4b68f52eb19
/dev/sda1        5701632  534039  5167593   10% /media/ubuntu/d936da7d-f118-4a64-87cb-ea8377a17d59
/dev/sdb2        128000  128000              0  100% /media/ubuntu/d60ed036-350a-4524-833e-c91e7dd76fc3
/dev/sda6      11829248 1110512 10718736  10% /media/ubuntu/77aacfae-f704-422a-82f5-047bb0dcb95f
```

------------------------------------------------------------------------------------------------------------------------------------------

---

### Post by Impavidus on 2019-08-03
> **Gnusboy said:**
> Hello
Thanks for hanging on. Here is the results from df and df -i
If I understand this, it looks like
SDB 1 is using just 1% of available drive space. Is sdb1 the external drive?
From the output you pasted a week back in post #27, I know that your computer has one internal hard drive, /dev/sda. It has several partitions, /dev/sda1, /dev/sda6, /dev/sda7 etc. /dev/sdb is your external drive, /dev/sdb1 is the first partition of your external drive. Your external drive appears to have at least 3 partitions. /dev/sdb1 is fairly small at 1GB, /dev/sdb2 is about 520GB and /dev/sdb3 is about 450GB. All partitions on this external drive are mostly empty. However, /dev/sdb2 has 128,000 tiny files, so that it hits the limit on the number of files that can be stored there. You should be able to store a lot of stuff on /dev/sdb3.

> SDA 9 is using 97% of available space which might account for the "No Space Left on device" error message. Is that right? To fix this I need to clear out some files to open it for use again.
I thought SDA 9 was the only partition mounted, but I looked up the DF cmd which says that all partitions shown are mounted. Is SDA 9 also the boot?sda9 is the 79GB partition on your internal hard drive. It contains your Ubuntu 16.04 system. I assume that's the system that was in control of your booting process. The fact that it is full may very well explain the fact you had trouble with this system. Now, you have trouble with your Ubuntu 16.04 system, not fully diagnosed, your want to clean up the hard drive and get rid of the old Ubuntu systems and the space they take on the hard drive and you want to move on to Ubuntu 18.04, right? In that case, I suggest that you don't fix any of your problems, but just backup all your files, wipe the hard drive, repartition and install 18.04. Once we know your files are safe, it can be done in half an hour.

> On the df -i view, SDA 9 is shown with  4808704  317780  4490924    7% /mnt, which is different from what is list above. I don't know the significance of that. See that output down page.It means that sda9 can hold at most 4,808,704 files and currently uses 7% of that capacity.

> Another topic: Is there a way to tell what sda 9 coresponds with which partition? C*an *I see the files in a particular SDA? sda9 is partition 9 of your internal hard drive. As partition 2 is a container for other partitions and the partitions are out of order, that's the second partition. It has a size of 79GB. I can see that in the output you showed in past #27:```
Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  93.4GB  93.4GB  primary   ext4            boot
 2      93.4GB  640GB   547GB   extended
 9      93.4GB  172GB   78.7GB  logical   ext4
 7      172GB   328GB   156GB   logical   ext2
 6      328GB   522GB   194GB   logical   ext4
 8      522GB   635GB   113GB   logical   ext4
 5      635GB   640GB   5388MB  logical   linux-swap(v1)
```
There are basically two ways to mount a partition. You can use the mount command, as I showed in post #28. That will mount the partition at the directory given in the command, which in this case is /mnt. Alternatively, you can click on the partition in the file manager, which will mount it at /media/some_name/some_code. I prefer the mount command as it's more predictable and it's easier to tell in a forum post what commands you enter than what things you click.

> I just checked and it appears I have full sccess to the 194 GB partition. Multiple files, etc. Unfortunately, I did not write many current files to the partition. So, I'm out several documents - unless I have them in a different partiion 
or in a Deja Dup backup.That's sda6. Good, go on.

> As I search for the files to backup, I've been stopped by many different error messages. These are some of the ones I get. I have multiple /home directories in the separate partitions. I can access a few, but the others
are locked by  Root If your user ID in an installed system is different from your user ID (the numerical user ID, not the user name) in the live session, you can't access your home partition of the installed system. Normally the first user of an installed system gets user ID 1000, just as the user ID of the live session, but maybe something is wrong here. Either use the file manager in your live session with root permissions or change ownership of those files on the hard drive with chown. Note that this may make it impossible to log in to the installed system when you boot it, but that doesn't matter. You just want to get the files off, then wipe everything. Or you change ownership of the files back with chown, if you wish.

> Some of the files I have looked for during the last fw days that were "root" seem to have been changed and assigned properities to me. Is this from chown I did yesterday?  Is there a way to change the root owned files to me?A chown would normally do just that. You can chance ownership of all files in your home directory of whatever partition you want to the live session user with```
sudo chown /path/to/directory $USER

#For example
sudo chown /mnt/home/jess $USER
```

> Also, will you be online over the weekend in case I need some advice? Down want to bother you if you are relaxing.I'm here pretty much every day, but the time of day is variable. And I'm in Europe, so I may be in a different time zone.

> Error messages:

1) Unhandled error message: Error when getting information for file '/home/ubuntu/Documents': No such file or directory
Unable to find the requested file. Please check the spelling and try again.**Don't safe anything in /home/ubuntu/Documents while running a live session. /home/ubuntu is the home directory of the live session user. It's completely destroyed when you shutdown or reboot. Save your documents on your external drive.**

> 2) /home/ubuntu You do not have the permissions necessary to view the contents of “ranhanrio”Doesn't matter. Nothing interesting could be there.

> 3) LibreOffice could not save important internal information due to insufficient free disk space at the following location:
/home/ubuntu/.config/libreoffice/4/user/backup
You will not be able to continue working with LibreOffice without allocating more free disk space at that location.
Press the 'Retry' button after you have allocated more free disk space to retry saving the data.

4)Error saving the document SUNP0009:
There is no space left on device /home/ubuntu/Pictures/Wallpapers/SUNP0009.odThere is no disk space at these locations because there is no disk. /home/ubuntu is the home directory of user ubuntu, which is you when you're using the live disk. It doesn't have a file system on any hard drive, it exists purely in RAM. Maybe you're running out of RAM and therefore you can't save files. **Again, store your stuff that you don't want to loose on the external drive.**

---

### Post by oldfred on 2019-08-03
Please post using standard fonts & use code tags for longer terminal output to preserve formatting & make it easier to read.

       How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

The live installer in live mode is user 999, so has no direct user permissions for your internal installed system which is user 1000.

---

### Post by Gnusboy on 2019-08-03
I'm a bit confused. You specify "The fd command", but then go back to df  and df -i
Did I miss something or is it just a typo? 

Also: Where are you in Europe? I've been to a few places there.

---

### Post by Impavidus on 2019-08-04
> **Gnusboy said:**
> I'm a bit confused. You specify "The fd command", but then go back to df  and df -i
Did I miss something or is it just a typo? A typo. I fixed it (or are there more?). There is no fd command.

> Also: Where are you in Europe? I've been to a few places there.
My coordinates are at the top right of my post. That's in the Netherlands, close to the German border.

---

### Post by Gnusboy on 2019-08-04
I've been to several countries in Europe, but have missed the Netherlands. I used to have some friends in Amsterdam, but that was long ago.
I have been to France 4 times, Spain, Portugal, Italy, Austria, Czech Republic and England and Switzerland.
And a few places in South America.
With a bit more retirement I'd be living somewhere in Europe.

---

### Post by Gnusboy on 2019-08-15
Hello Impavidus
Are you doing well?

I have an issue I want to be sure of, if you don't mind.
When I installed the 650GB internal drive when I built the system. At the time I split the drive - more or less 50-50, with 16.04 on one partition and 14.04 on the other one. We primarily focused on the 16.04 because that's where the problems are. 
I'm pretty sure the 14.04 is OK, but I won't know for sure until I get a clean partition.
I understand I can clear the entire hard drive, but is there an option to clean just the 16.04 while keeping the 14.04 intact. 
Assuming for a minute, that the 14.04 is good on its own, do you think replacing the other with a 18.04, will cause hardware problems? 
Do you think both will stay in their own corrals and play nice? I haven't had any problems between 14.04 and 16.04 through the years. And I know that just wiping both partitions is the best solution - and I'll most likely erase everything and start from scratch. I'd like your opinion pro/con on the idea.

I'm pretty sure I have everything I need off of the Ubuntu 16.04 partition and I'm going to slick that side of the drive.
Then If I later find a need for that space, it will be available.

I've also seeing another oddity while removing files from the 16.04. Many files are "owned" by root, so cannot be changed. They don't seem to be operational or boot files, but some files show owned by root. Yet if I make a copy/paste of the file, it changes from locked to locked and I can edit it. Have you seen this before?
When we talked about the files that show "either 1000 or #1000" as the owner, I didn't look into the issue. There is also another tweak I don't understand. But some of those files marked as owned by "1000" or with a hash tag "#1000"
And some can be opened and can be edited, while others can. So far, I haven't figured out the difference between one with a # hashtag vs a file with just "1000"
Have you seen this before, know it's affect? It appears to be just one more goofy thing with my system, I'd like to figure it out.
Thanks

---

### Post by oldfred on 2019-08-15
Forget about 14.04 it is EoL - End of Life and will just give grief in trying to update it .

User 1000 is the first user, user 1001 is the second user, etc. Your login name is then associated with the number actually used in the file.

You should not have root as owner of your own files in /home. I have accidentially used sudo or downloaded a file & it then is owned by root so I change it. But all the system files are owned my various system utilities, many but not all are owned by root. Do not change any system files, or then you just might as well reinstall from scratch and restore your data & settings from backups.

---

### Post by Impavidus on 2019-08-16
As oldfred says.

User documents are supposed to be owned by your normal user account, not root. Maybe something went wrong once. If the files have been set as readable for all, you can still read them. If they're only readable for the owner, you can't. If you can read those root-owned files, you can make a copy and you'll own the copy.

Don't be pretty sure you've got all files you need backed up. Be absolutely sure. Doublecheck that all files you need are on your external backup drive, then unmount and unplug the drive.

---

