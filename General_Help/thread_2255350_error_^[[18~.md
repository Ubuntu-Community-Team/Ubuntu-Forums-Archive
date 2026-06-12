---
title: "error ^[[18~"
date: 2014-12-04
forum: General Help
---

### Post by briar rabbit on 2014-12-04
Hello,

I have 10.04 lucid linux WHICH I LIKE.

Out of the blue I get the following error when I started my computer this morning: ^[[18~

This code filed the screen top to bottom side to side.  I had no control so I waited a short while and did a hard shut-down.

I will post more information as I get it - or perhaps someone is familiar with this problem.

Thanks.

---

### Post by grahammechanical on 2014-12-04
It could be some keyboard keys being held down or shorting with dust and stuff. Unplug the keyboard and see if it still happens.

By the way, you might also like this and end up with a supported OS.

[https://ubuntu-mate.org/](https://ubuntu-mate.org/)

Regards.

---

### Post by briar rabbit on 2014-12-04
thanks [**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323") 

this is a laptop.  I will try to write out some of what the screen has done.  It may take a while.  Was not planning on spending the day with my computer in this condition.

---

### Post by briar rabbit on 2014-12-04
When I start the laptop I do get the "ubuntu" logo screen but it never finishes.
When I click the "Esc" button I get the following on the screen.
I have retyped it here line for line.
===================
init: mounted-dev main process (351) terminated with status 127
mountall: Event failed
fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 257864/5857280 files, 21006256/23416832 blocks
* Starting: AppArmor profiles         ls: error while loading shared libraries: libattr.so.1: cannot open shared object file: No such file or directory
/sbin/apparmor_parser: cannot use or update cache, disable, or force-complain via stdin
[OK]
* setting sensors limits      [OK]
Speech-dispatcher configured for user sessions
Starting the Windind daemon windind =long space= /usr/sbin/winbind: error while loading shared libraries: libattr.so.1: cannot open shared object file: No such file or directory
[fail]
=================
then a repeat plus other stuff checking printer, pulse audio and battery which are all OK

and the curser at the bottom flashing

I do hope someone is familiar with this library problem and can help.  thanks

---

### Post by mörgæs on 2014-12-04
I don't think you will get much response. Most people here do not bother dealing with unsupported software.

[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

---

### Post by briar rabbit on 2014-12-04
thank you morgaes

As much as I hate to waste so much time and resources to replacing everything I own every few years I will do just that until I end the present work I must do using computers.

If you do not mind can you tell me if the latest hot flash bling bling OS I can find to put on this antique 2007 machine will enable me to get at the files that I am unable to excess do to my LIBRARY problem?

thank you - really

---

### Post by Impavidus on 2014-12-04
I have an even more antique computer (circa 2005) that still happily runs Xubuntu 14.04. But without details I can't say whether your's will run it too.

I don't know about your problem, but it's possible that because of some upgrade to the library that particular library file was removed, but a deamon relying in that library file, by belonging to a desktop package, was not upgraded and therefore broke. Unsupported releases like 13.10 are just insecure, partially supported releases like 10.04 can break at any moment due to upgrades of server packages

---

### Post by mörgæs on 2014-12-04
Please see the link in my signature.

---

### Post by briar rabbit on 2014-12-07
To those few smart people out there who still have the time to help with an un-supported OS - thank you.

I have down loaded the latest LTS (1 GB and it took hours) - don't know what to do with it yet, that is later.

As for my "libattr" problem.
I took the original Ubuntu 10.04 CD and ran it in the laptop. This allows me access to some files which I copied onto an external HD.  My problem is many of the things I would like to get are either "input/output errors" or I get the following; "Error while copying."
"The folder " ... cannot be handled because you do not have permission to read it."

How can I get "permission" to open (aka "read") files so I can copy them?

thanks again

---

### Post by JKyleOKC on 2014-12-07
> **briar rabbit said:**
> My problem is many of the things I would like to get are either "input/output errors" or I get the following; "Error while copying."
"The folder " ... cannot be handled because you do not have permission to read it."

How can I get "permission" to open (aka "read") files so I can copy them?
Those files that are giving you "input/output error" message are probably simply lost; this is most likely caused by a hardware error that the system cannot overcome.

Those that complain about permission, though, **might** be opened if you prefix the copy command with "sudo " on the same line (assuming you are using the command line; "gksudo nautilus" from a command line to launch the GUI with superuser privileges if using the GUI). The superuser has total permission everywhere, which means it can wipe out the files as easily as it can copy them, so be **very** careful.

There's a package called "testdisk" that includes a program "photorec" that can **sometimes** recover files from damaged hardware, and it can be installed when running from a live CD/USB. However my results with it have been less than 50% successful and it takes literally many hours to run...

---

### Post by briar rabbit on 2014-12-07
Hello Jim

Thanks for the help.

I guess I will need it spelled out for me.

I typed into the terminal "sudo" with several variations of differing file names and simply "sudo nautilus".

What happens is; nothing or "command not found".

OR; I get the 'desktop' at '/root' 'location unknown'.  But I can tell that this 'desktop' I am getting is on the CD because it has nothing in it.  Maneuvering around through the 'desktop' nautilus takes me to many places but nothing on the "96 GB Filesystem" I am trying to get at.

Thanks for all the help.  Not in a rush but would like to salvage what I can.

---

### Post by briar rabbit on 2014-12-15
"sudo nautilus"  superuser for the whole dang machine.

I typed in "sudo nautilus" and am immediately (without delay) taken to a new screen that has one thing on it; a desktop folder icon. I explore this for a while then go to "Places" click on the home file system and go through the whole routine as before - nothing has changed.

So, every once in a while I try the laptop again.  It broke itself maybe it will fix itself.  I also tried the "sudo nautilus" again.

Another effort with "sudo nautilus" yielded different(?) results:

ubuntu@ubuntu:~$ sudo nautilus
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

So, if there are any "administrators" out there with the time to help a no longer supported OS, G-R-E-A-T.

---

### Post by JKyleOKC on 2014-12-15
> **briar rabbit said:**
> I typed in "sudo nautilus" and am immediately (without delay) taken to a new screen that has one thing on it; a desktop folder icon. 
```
Please ask your system administrator to enable user sharing.

```
So, if there are any "administrators" out there with the time to help a no longer supported OS, G-R-E-A-T.Unfortunately I can't help much, since among other things I've not used Nautilus for many years and when I did it was on a Mandrake 8.1 system.

However I can tell you that you, yourself, are the system administrator in question. So long as you are in Nautilus, or a command line shell either, that was launched via "sudo" then you have full administrator privileges.

The inability to do much probably stems from the fact that booting from USB or CD/DVD creates a "ramdisk" that's entirely in memory and has no initial access to the hard disk that you are trying to reach. You have to mount that hard disk first; using Nautilus to do so is as simple as locating its icon to the left of the main window and double-clicking it, or so I've been told. However doing this seems to require that the "usershare" utility be available, and it appears to be missing for your case!

After reviewing the thread, it seems to me that some of the suggestions by others may have led you into a dead-end alleyway. Few of us remember all the details of changes made in the past four years, unfortunately. This line from your second post appears to be the crux of the matter, though: ```
init: mounted-dev main process (351) terminated with status 127
```That means that a most critical part of the boot process failed, and everything subsequent to that point isn't really reliable information.

I think I may still be able to help you recover your data, at least, but I can't tell yet whether recovery of the entire system will be possible. It may be best if you tell me exactly what is the minimum result you need; I understand that a total recovery would be desirable, but that might not be possible. My initial guess as to a reason for that "init" failure would be a hardware problem and these frequently are not curable.

As for the age of your machine being a problem, there are several sides to that. Other Linux distributions exist, and some are designed specifically for older machines. It may be necessary to download one of them and use it during the recovery effort. We'll see, as we go along...

---

### Post by matt_symes on 2014-12-15
Hi. 

Is the hard drive the original drive that came with the laptop ?

I would run a SMART test on the drive and see what that returns.

Boot into the 10.04 live ISO and run SMART test.

Kind regards

---

### Post by briar rabbit on 2014-12-15
I read these last two responses and something clicked  - in my head ??

So, I just tried 'it' again.  With the live CD in I clicked on 'my computer'.  This showed all the 'file systems' connected; the home file system, the live CD and the external drive.  I right clicked the 'home file system' and clicked 'open with other application' and then 'use a custom command'.  Now I entered in the field with "sudo nautilus" and walla I am in the home file as administrator ... except.   I know I am in as administrator because the files and folders that before had a large "X" on them and would not let me in, now I saw no "X" and I could get in a view them.  Great except ... I still do not have permission to copy (handle) the files.  So, I am happy I can view some of what I am missing - all is not lost.

(note; before what I was doing was going to "Applications > Accessories > Terminal and doing the sudo from there. And that way I could not even access the files.

Thanks Jim, I was able to retrieve my unique documents, there were not very many (12 I really wanted, because I occasionally copy my files, eventually I will learn enough about 'backup' programs to do that).  What I would really like to do now is get a couple months worth of internet gleanings that I had not been copying (backing up) off the crashed HD and onto an external drive..  It seems interesting that the docs I created, I could copy onto an external drive while the internet screen shots and pdf's are protected, oh well.

Matt, I love my Ubuntu - I really do. But, it is still a computer and I do not see were to run a "SMART" test.  However, I will say this much.  I bought the laptop used and I did a diagnostic on it then and found (if I remember correctly) there were 5 sectors on the HD and 2 of them were bad.  OK, so that said I have been looking at getting a 120 or 128 gb ssd and an external caddy.  This way I could go back to using the laptop and still (hopefully) be able to get things off of the crashed harddrive.

Thanks a bunch. Though I can not get the files copied, due to your input I can now look at those file and I will be making sure what I do and do not have  - which is better than I was doing.

---

### Post by matt_symes on 2014-12-15
Hi

Boot into the live cd and connect to the Internet.

Open a terminal and type

```
sudo apt-get install smartmontools
```

then type

```
sudo smartctl -t long /dev/sda
```

Make sure sda above is correct and is your hard drive. Wait for it to finish. It will display a finishing time and it may take over an hour.

when finished type

```
sudo smartctl -a /dev/sda
```

post the results back here.

This does assume the drive has SMART and it's enabled.

Kind regards

---

### Post by briar rabbit on 2014-12-20
I have been trying to get here for 2 1/2 days.  I login in fine but the second page I go to takes away my login status.  I had to do the login twice this morning to get to here but that was only after threatening to ask a question on 'ask ubuntu dot com'.
My SSD should be in today's mail.  My plan is to put the crashed HD in a caddy and be able to read it without permission issues merely because it will be connected via USB.  I will be busy putting 14.04 on the 160GB SSD first and then the proprietaries for video, etc.  

So ... hey matt, I suppose I do not have SMART and or it enabled.

TERMINAL 1
==========
ubuntu@ubuntu:~$ sudo apt-get install smartmontools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bsd-mailx postfix
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin
  resolvconf postfix-cdb
Recommended packages:
  mailx mailutils
The following NEW packages will be installed:
  bsd-mailx postfix smartmontools
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,808kB of archives.
After this operation, 4,395kB of additional disk space will be used.
Do you want to continue [Y/n]? 
===
Do you want to continue [Y/n]? Y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main postfix 2.7.0-1 [1,321kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main bsd-mailx 8.1.2-0.20090911cvs-2ubuntu1 [155kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main smartmontools 5.38-3ubuntu3 [332kB]
Fetched 1,808kB in 5s (301kB/s)       
Preconfiguring packages ...
=====================
THEN THIS BLOCKED THE TERMINAL
===
Postfix Configuration

Please select the mail server configuration type that best meets your needs.

No configuration:
  Should be chosen to leave the current configuration unchanged.
Internet site:
  Mail is sent and received directly using SMTP.
Internet with smarthost:
  Mail is received directly using SMTP or by running a utility such as fetchmail. Outgoing mail is sent using a smarthost.
Satellite system:
  All mail is sent to another machine, called a 'smarthost', for delivery.
Local only:
  The only delivered mail is the mail for local users. There is no network.

                            <Ok>                                      


SO I TRIED IN A SECOND TERMINAL
======================
ubuntu@ubuntu:~$ sudo apt-get install smartmontools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bsd-mailx postfix
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin
  resolvconf postfix-cdb
Recommended packages:
  mailx mailutils
The following NEW packages will be installed:
  bsd-mailx postfix smartmontools
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
ubuntu@ubuntu:~$ 
===
ubuntu@ubuntu:~$ sudo smartctl -t long /dev/sda
sudo: smartctl: command not found
ubuntu@ubuntu:~$

---

### Post by JKyleOKC on 2014-12-20
A couple points of caution and comment...

First, to get here as quickly as possible, use this link: [http://ubuntuforums.org/subscription.php](http://ubuntuforums.org/subscription.php)
It will take you to your own subscription page if you are already logged in, or to the login page if you are not already into the forums. If you do have to log in after using it, use it again after you're in, and you will go straight to your subscribed-thread list. I normally do not ever log out from these forums, just close Firefox when I'm done for a while. If I'm away for 24 hours, the system automatically logs me out and I have to log in again. If the time is shorter, I pop right back to my subscription list. (We're automatically subscribed to each thread in which we participate, and can subscribe to others if we so desire, using the thread tools at the top of the page.)

Second, and more importantly, trying to do the same job from more than one terminal window open at the same time is a recipe for (additional) disaster. That "Could not get lock" error indicates that the system is preventing you from creating a huge mess. It will go away once the first attempt is resolved.

The "freeze" of the first attempt **appears** to be that the installation routines are waiting for you to choose one of the configuration options. I believe that the one you need at this time is "Local only" which will install postfix as a server to pass mail between processes on only the one machine, with no network connection at all aside from the "loopback" interface. The configuration can always be changed later if need be. Once you've selected the option, installation should proceed. To make the selection, simply highlight it on the list and double-click (if I remember accurately -- it's been a few years since I last installed postfix and my memory ain't what it once was). You may have to hit Enter after making the selection, which is what the OK at the bottom is telling you.

Hope this helps!

---

### Post by briar rabbit on 2014-12-21
Hey Jim

I replaced my 100GB HDD (crashed with libattr.so.1 error) with a 160GB SSD.  I put the HDD in a caddy and connected to the USB everything is as I left it before the library crash.

As I look at the filesystem and the properties in the folder "lib" on the laptop (crashed and now in a caddy), the desktop (working) and the 160GB SSD (now in the laptop) this is what I find:

"lib" folder laptop; 7949 files
"lib" folder desktop; 39702 files
"lib" folder 160gb ssd; 4423 files

Since the "libattr.so.1" is missing from the laptop I am thinking I can just cut and paste a copy from the desktop into the "lib" folder that is missing it.

My question is are these types of files copyable? 

I am going to wait until I have copied the whole laptop harddrive onto an external HD before I try (just in case).

---

### Post by JKyleOKC on 2014-12-22
Sorry to be a bit slow. Yes, almost ANY type of file is copyable (except for those in the /proc directory, which are not really files at all but rather a fiction to simplify dealing with information actually stored all over RAM; one of these is actually the entire RAM space masquerading as a file). However it's best to make very certain that the source is at exactly the same version as was the one it's replacing. Some of the info kept by "dpkg" will, I believe, give you that information about the needs of the destination, as well as the status of the source. However, not having had need to do such things myself, I'm not sure exactly where the information can be found.

EDIT: Rather than copy-and-paste, I would use either the "cp" command direct, or the sneakernet approach, via a USB pen drive. Copy and paste has always worked for me in the past, but I've seen enough problems reported by others to be mistrustful of it for such critical tasks.

---

### Post by briar rabbit on 2014-12-22
Well, things not so good.

I do not see a "path" to type into the command line to copy "libattr.so.1" from one filesystems "/lib" into the other filestystems "/lib".  Right clicking properties only gives location as "/lib".

So, with both "/lib" folder's on the desktop I tried to copy and paste the "libattr.so.1" file from one to the other - permission denied.  I tried again logged in as 'sudo' as before no difference.

I was able to 'copy to' desktop but, I could not do anything with it once it got there.

If there is something you would like me to try let me know.  Otherwise, I'm ready to call it.

---

