---
title: "New ISOs are good!!!! All testers on board!"
date: 2008-02-21
forum: General Help
---

### Post by ago on 2008-02-21
We finally seem to have good 8.04 ISOs with all features and patches in! No tricks and workarounds should be required!

Grab the ISO here: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
Wubi here: [http://wubi-installer.org/devel/minefield/](http://wubi-installer.org/devel/minefield/)   (rev 431+)
Put both in the same folder and run wubi.exe

Once Alpha5 is out that can also be used. If you have old ISOs delete them to make sure the new ones are used.

If you have troubles:

1) run chckfs /f in a dos box within the drive where you installed wubi
2) after selecting wubi press esc at the countdown and try the other boot options
3) ask in this forum, possibly attaching the relevant log (even better if you select verbose mode at boot):

* Windows logs are in your temp folder (type %temp% in windows explorer) and in /ubuntu/*.log.
* Boot logs are /casper.log + /tmp/*log. They are relevant in case you cate a busybox prompt after rebooting.
* Ubiquity logs are /var/log/syslog + /var/log/installer/*. They are relevant for any issue during installation after rebooting.

---

### Post by ago on 2008-02-21
Message written using Wubi 8.04 rev431 :D

---

### Post by ago on 2008-02-21
And yes, Wubi is also in the new Live CD ISO. Try burning a CD and popping it in the tray... :D

---

### Post by ilych on 2008-02-21
I downloaded the new files and booted into Ubuntu, and it displayed "Installation failed" while it was checking partitions. It said that a log file was saved, but I can't seem to find it. Where should the log file be, and what could have gone wrong in the installation?

Thanks again for any help.

---

### Post by ago on 2008-02-22
Did you uninstall wubi first? 
Look into /ubuntu under windows for any zipped log file and attach it here

---

### Post by ilych on 2008-02-22
When the installation fails, it tells me that an error log as been produced at: /ubuntu/installation-logs.zip

But when I go back to Windows, I cannot find such a file (all system/hidden files are shown) in the directory. The only files that look like logs are "curl_log.txt" and "metadl_log.txt", both of which do not seem to contain any useful information.

Thanks again for any help.

---

### Post by ago on 2008-02-22
When you see the error message, press ctrl+alt+f2 to get a terminal
Then 

less /var/log/syslog

Go to the bottom to find relevant error info. The path in the algorithm that reports the errors is wrong so there will be no log.zip.

You can also use the command

grep -i -A 3 -B 3 'err\|fail' /var/log/syslog

---

### Post by ilych on 2008-02-22
I don't know how to see if something is an error or not. In any case, I tried to take a picture of lines where there was a "Warning" or some negatively charged word:

[lastpage.jpg]("http://www.thelittlerock.com/ubuntu/lastpage.jpg")
[lastpage2.jpg]("http://www.thelittlerock.com/ubuntu/lastpage2.jpg")
[error.jpg]("http://www.thelittlerock.com/ubuntu/error.jpg")
[error2.jpg]("http://www.thelittlerock.com/ubuntu/error2.jpg")
[error3.jpg]("http://www.thelittlerock.com/ubuntu/error3.jpg")
[error4.jpg]("http://www.thelittlerock.com/ubuntu/error4.jpg")
[error5.jpg]("http://www.thelittlerock.com/ubuntu/error5.jpg")
[error6.jpg]("http://www.thelittlerock.com/ubuntu/error6.jpg")
[error7.jpg]("http://www.thelittlerock.com/ubuntu/error7.jpg")

Thanks again for the help, ago. Let me know if the error wasn't captured in one of the above photos, so I can try again...

---

### Post by ago on 2008-02-22
From windows, edit 

/ubuntu/install/custom-installation/failure-command.sh

Replace "/varl/log" with "/var/log" throught the file

Reboot and select Ubuntu. Upon failure you should now have a zipped log in /ubuntu/.

Attach it here.

Thanks!

---

### Post by mikedep333 on 2008-02-22
> **ago said:**
> And yes, Wubi is also in the new Live CD ISO. Try burning a CD and popping it in the tray... :D

I absolutely hate burning CDs. Is it possible for me to extract wubi from the ISO image (to the same directory as the ISO image) and then run it? Would it use the ISO image this way?

---

### Post by evan d on 2008-02-22
> **mikedep333 said:**
> I absolutely hate burning CDs. Is it possible for me to extract wubi from the ISO image (to the same directory as the ISO image) and then run it? Would it use the ISO image this way?

[http://people.ubuntu.com/~evand/wubi/stable](http://people.ubuntu.com/~evand/wubi/stable)

Save it as wubi.exe and then run it.  It will download the ISO automatically.  What you suggest will also work, but this will be a bit easier if you don't have the tools to extract files from ISO images readily available.

---

### Post by ilych on 2008-02-22
Please find installation-logs.zip attached.

Thanks.

---

### Post by Derek Chai on 2008-02-22
Once I downloaded the iso do I put the file in c:/ubuntu/install?

---

### Post by ilych on 2008-02-22
> **Derek Chai said:**
> Once I downloaded the iso do I put the file in c:/ubuntu/install?

Place both the wubi installer and the ISO in the same folder and then run wubi.exe.

---

### Post by Derek Chai on 2008-02-22
So how would I dual boot this so I could switch to windows like like 20 seconds. and back

---

### Post by ilych on 2008-02-22
After you install Wubi, Ubuntu should show up in the boot options. Since you have to restart to go to the boot menu, I don't think you can switch back and forth within 20 seconds, if I understand you correctly.

---

### Post by Derek Chai on 2008-02-22
Thanks for your fast response. I've seen some google sites that have "hibernation" how is it possible to do that?

---

### Post by ago on 2008-02-22
> **ilych said:**
> Please find installation-logs.zip attached.

Thanks.

Do you have a directory C:/WINDOWS/system32/config/software (case sensitive!!!)

---

### Post by Derek Chai on 2008-02-22
I can't install it gives me all this stuff in grey on a black screen. 

I have rev431
and the iso you provided.

---

### Post by ago on 2008-02-22
what exactly do you see? 
try to press esc after selecting Ubuntu during the countdown and select one of the other options.

---

### Post by Derek Chai on 2008-02-22
I've tried the 1st and last option.

normal and vegto I think?
how long does it take i think i didnt let it finish

---

### Post by ilych on 2008-02-22
> **ago said:**
> Do you have a directory C:/WINDOWS/system32/config/software (case sensitive!!!)

No, I don't. The only folder under config is "systemprofile".

Thanks for your help.

---

### Post by evan d on 2008-02-23
> **ilych said:**
> No, I don't. The only folder under config is "systemprofile".

Thanks for your help.

It wont be a folder, it will be a file called software.

---

### Post by ilych on 2008-02-23
> **evan d said:**
> It wont be a folder, it will be a file called software.

Okay, I have the files "SYSTEM", "system.LOG", and "system.sav" but not "system" (case sensitive).

:(

---

### Post by lond on 2008-02-23
Hi!

I have this directories:

In  XP: C:/Windows/system32/config/software
in VISTA: C:/Windows/System32/config/SOFTWARE

// lond

---

### Post by ago on 2008-02-23
Evan, might be useful to make the paths case insensitive using find -iname or something similar.

As a workaround for the others, find the Migration-Assistant section in /ubuntu/install/custom-installation/preseed.cfg and comment it out (prepend # to each m-a line)

---

### Post by mikedep333 on 2008-02-23
Simply put, it works on my HP tx1000z laptop/tablet PC.

I had to select the acpi workarounds during the first boot, but then it worked.

Also, this time, unlike with alpha4, it automatically configured grub for the final/permanent booting to work off of the correct NTFS partition (hd0,4) instead of simply the 1st/windows NTFS partition (hd0,0).

So thanks alot and keep up the good work!

UPDATE: What's the difference between
[http://wubi-installer.org/devel/minefield/](http://wubi-installer.org/devel/minefield/)
and
[http://people.ubuntu.com/~evand/wubi/](http://people.ubuntu.com/~evand/wubi/)
?

---

### Post by ilych on 2008-02-23
> **ago said:**
> Evan, might be useful to make the paths case insensitive using find -iname or something similar.

As a workaround for the others, find the Migration-Assistant section in /ubuntu/install/custom-installation/preseed.cfg and comment it out (prepend # to each m-a line)

I commented out each m-a line, but the installation still fails. What else should I try? Thanks.

---

### Post by ago on 2008-02-23
> **mikedep333 said:**
> 
What's the difference between
[http://wubi-installer.org/devel/minefield/](http://wubi-installer.org/devel/minefield/)
and
[http://people.ubuntu.com/~evand/wubi/](http://people.ubuntu.com/~evand/wubi/)
?
Same file, one was compiled by myself, one by Evan, but using the same source code.

---

### Post by ago on 2008-02-23
> **ilych said:**
> I commented out each m-a line, but the installation still fails. What else should I try? Thanks.

Can you get me the log file?

---

### Post by Derek Chai on 2008-02-23
Yeah I've tried every single boot thiny from normal to veborse still it doesn't start.

---

### Post by ago on 2008-02-23
Try Ctrl+alt+f2 to get a shell, see in /var/log/syslog (bottom) for details on what is happening.

---

### Post by Derek Chai on 2008-02-23
Were is var log in the ubuntu folder?

Can you give me the .metalink file it's not downloading. I am trying a fresh install.

---

### Post by ago on 2008-02-23
syslog can be accessed from within Ubuntu, after you reboot.
The metalink files are here [http://wubi-installer.org/metalinks/8.04/](http://wubi-installer.org/metalinks/8.04/)
Save the relevant one under /ubuntu/install

---

### Post by Derek Chai on 2008-02-23
IM posting a youtube video of what is happening please stay tuned.

---

### Post by Derek Chai on 2008-02-23
[http://www.youtube.com/watch?v=XZI_htOeqEQ](http://www.youtube.com/watch?v=XZI_htOeqEQ)

---

### Post by ilych on 2008-02-23
> **ago said:**
> Can you get me the log file?

Attached, thanks.

---

### Post by evan d on 2008-02-24
> **ago said:**
> Evan, might be useful to make the paths case insensitive using find -iname or something similar.

It's written in C, making use of strcasecmp, so they are case insensitive.

Thanks for the suggestion all the same though.

---

### Post by evan d on 2008-02-24
> **ilych said:**
> Attached, thanks.

> 
Feb 23 14:15:29 ubuntu migration-assistant: info: setting ostype from: '/dev/sda1:Microsoft Windows XP Professional:Windows:chain'
Feb 23 14:15:29 ubuntu migration-assistant: info: got ostype of: 'windowsxp', mountpoint is: '/mnt/migrationassistant'
Feb 23 14:15:30 ubuntu ntfs-3g[12393]: Version 1.1120 
Feb 23 14:15:30 ubuntu ntfs-3g[12393]: Mounted /dev/sda1 (Read-Write, label "IBM_PRELOAD", NTFS 3.1) 
Feb 23 14:15:30 ubuntu ntfs-3g[12393]: Cmdline options: rw,umask=0022,nls=utf8 
Feb 23 14:15:30 ubuntu ntfs-3g[12393]: Mount options: rw,nls=utf8,silent,allow_other,nonempty,default_permissions,relatime,fsname=/dev/sda1,blkdev,blksize=4096 
Unable to open the registry file at '/mnt/migrationassistant/WINDOWS/system32/config/software'
2: No such file or directory
Unable to open the registry file at '/mnt/migrationassistant/WINDOWS/system32/config/software'
2: No such file or directory
Unable to open the registry file at '/mnt/migrationassistant/WINDOWS/system32/config/software'
2: No such file or directory
ma-search-users: Error.  Could not find ProfilesDirectory.
Feb 23 14:15:30 ubuntu ntfs-3g[12393]: Unmounting /dev/sda1 (IBM_PRELOAD) 
Feb 23 14:15:30 ubuntu ubiquity[8904]: migration-assistant: filtering out Microsoft Windows XP Professional (/dev/sda1) as it has no users


Looking at the logs, it's clear two things are happening:
[LIST=1]
[*]migration-assistant cannot find that file inside the registry access code, but was able to elsewhere.  Very odd, I'll look into this.
[*]The installer is calling failed_command because it needed to show a page of the UI, which we currently consider a failure.  I had intended to split failing out completely and showing a page of the UI into two separate commands at the end of the 7.10 cycle, but at that time it was too late for such a feature, and I have since forgotten.  I'll add it to my todo list.  The fact that it's trying to show the migration-assistant page when there are no users to import from is a bug in the m-a UI code that I've been meaning to get to for a while.  Now that we're in FF, I should be able to take care of that quickly as well.  Added to my todo.
[/LIST]

---

### Post by Derek Chai on 2008-02-24
did you watch my video yet???

---

### Post by ago on 2008-02-24
Derek, it would be more useful to see the boot in verbose mode. Press esc at the countdown and select verbose mode. If you get to a shell look at the logs under / and /tmp

---

### Post by ago on 2008-02-24
It might be that the kernel does not support your disk drive.

You can try to add "libata.noacpi=1" to /ubuntu/install/boot/grub/menu.lst (all lines that begin with "kernel"). Or simply wait.

---

### Post by switchfrenzy5 on 2008-02-24
> **evan d said:**
> Looking at the logs, it's clear two things are happening:
[LIST=1]
[*]migration-assistant cannot find that file inside the registry access code, but was able to elsewhere.  Very odd, I'll look into this.
[*]The installer is calling failed_command because it needed to show a page of the UI, which we currently consider a failure.  I had intended to split failing out completely and showing a page of the UI into two separate commands at the end of the 7.10 cycle, but at that time it was too late for such a feature, and I have since forgotten.  I'll add it to my todo list.  The fact that it's trying to show the migration-assistant page when there are no users to import from is a bug in the m-a UI code that I've been meaning to get to for a while.  Now that we're in FF, I should be able to take care of that quickly as well.  Added to my todo.
[/LIST]

Does this mean it won't be fixed until the final release? Thanks for your help Evan.

---

### Post by ilych on 2008-02-24
Thanks evan, I look forward to the next release.

---

### Post by lond on 2008-02-24
Hi!

After the installation is finish and i have done the reboot, i end up with this message...

sata-disk with vista, AMD Athlon64 X2 2.00GHz 1GB ram

---

### Post by ago on 2008-02-24
> **lond said:**
> Hi!

After the installation is finish and i have done the reboot, i end up with this message...

sata-disk with vista, AMD Athlon64 X2 2.00GHz 1GB ram
What is in the "root" line in /ubuntu/disks/boot/grub/menu.lst?
Might want to change that. What ISO did you use, is that the alpha5?

---

### Post by Derek Chai on 2008-02-24
[http://habboard.com/vids.php](http://habboard.com/vids.php)

Vid with veborse mode there.

---

### Post by lond on 2008-02-24
root		(hd4,0)/ubuntu/disks

I let the wubi-installer download it. rev431

// lond

---

### Post by Derek Chai on 2008-02-24
[http://habboard.com/vids.php](http://habboard.com/vids.php)

Blip and youtube there.

One thing tho. I tried every mode it does the same thing. Any good? I'm using a HP m7160n media center PC with 4GB ram.

---

### Post by ago on 2008-02-24
> **lond said:**
> root		(hd4,0)/ubuntu/disks

I let the wubi-installer download it. rev431

// lond

That means that it is looking in partition 5 of drive 1. Is this where you installed wubi? You can press esc at the countdown, then press "C", then use tab expansion to see what is visible.

---

### Post by ago on 2008-02-24
> **Derek Chai said:**
> [http://habboard.com/vids.php](http://habboard.com/vids.php)

Blip and youtube there.

One thing tho. I tried every mode it does the same thing. Any good? I'm using a HP m7160n media center PC with 4GB ram.

Darek thanks a lot for taking the time to do the videos. It looks to me like a kernel issue, not necessarily related to Wubi.

Could you please try to boot (and maybe install) off the Ubuntu CD and see if the same errors are there as well? In case you might file a bug for the kernel in launchpad.

---

### Post by Derek Chai on 2008-02-24
Wait if I boot off the CD how do I make it so it doesn't mess up my windows? Also which 8.04 or what? I have 7.10 CD's

---

### Post by ago on 2008-02-24
Booting off the CD is 100% safe, within the demo you can decide whether to install to a dedicated partition (in which case existing partitions will be resized and a new bootloader installed).That is optional of course.

---

### Post by Derek Chai on 2008-02-24
Wait which version and tell me in detail what I could do to do whatever you are talking about.. I am new to this.

---

### Post by mikedep333 on 2008-02-24
> **Derek Chai said:**
> Wait which version and tell me in detail what I could do to do whatever you are talking about.. I am new to this.

Just follow the guide here up** until it says installing**. If you get to the desktop, then it worked.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

For the CD to use, here is a link to all the CD images for hardy alpha5.
[http://cdimage.ubuntu.com/releases/8.04/alpha-5/](http://cdimage.ubuntu.com/releases/8.04/alpha-5/)
here is a direct link to the 32-bit CD image (which you should probably use):
[http://cdimage.ubuntu.com/releases/8.04/alpha-5/hardy-desktop-i386.iso](http://cdimage.ubuntu.com/releases/8.04/alpha-5/hardy-desktop-i386.iso)
and here is  a direct link to the 64-bit CD image (which you probably do not want to use):
[http://cdimage.ubuntu.com/releases/8.04/alpha-5/hardy-desktop-amd64.iso](http://cdimage.ubuntu.com/releases/8.04/alpha-5/hardy-desktop-amd64.iso)
Don't worry about messing up your system, that is only possible when you go to install, and you have to go well out of your way to install.

---

### Post by Derek Chai on 2008-02-24
I know how to install but how would I partion it and double boot without messing it up. I don't have any partioned things yet.

---

### Post by lond on 2008-02-25
> **ago said:**
> That means that it is looking in partition 5 of drive 1. Is this where you installed wubi? You can press esc at the countdown, then press "C", then use tab expansion to see what is visible.

My Wubi is installed on partition 1 on drive 5. If I try to switch the numbers then GRUB says that the partition does not exist. 

"C" or "c"? tab?

---

### Post by ago on 2008-02-25
> **lond said:**
> My Wubi is installed on partition 1 on drive 5. If I try to switch the numbers then GRUB says that the partition does not exist. 

"C" or "c"? tab?

Press esc at the countdown
Then press "c"

You should now be in a console environment (grub console)

Type

kernel (hd4,0)/[HIT TAB HERE]

The tab key basically list the available options/files given the partial command already typed. It is a trick to navigate in grub console. In partitcular you should see a kernel in 

kernel (hd4,0)/ubuntu/disks/boot/

---

### Post by ago on 2008-02-25
> **Derek Chai said:**
> I know how to install but how would I partion it and double boot without messing it up. I don't have any partioned things yet.

First see if the CD works. Then play with it and see if you like it. Then click on the installer icon in the desktop.

The installer will let you resize your windows partition and use the free space thus obtained. There is no need to use separate partitioning tools.

---

### Post by Dominator86 on 2008-02-25
Hello!

I can't get on cdimage.ubuntu.com.
Is it currently down?
Are there any mirrors?

---

### Post by ago on 2008-02-25
works for me:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by Dominator86 on 2008-02-25
Now works for me too :?

I hope this one works.
Last time I used wubi, the i386 version failed to install.
It seems that the amd64 version still has the usplash bug with gf8800 graphics cards.

---

### Post by ago on 2008-02-25
> **Dominator86 said:**
> Now works for me too :?

I hope this one works.
Last time I used wubi, the i386 version failed to install.
It seems that the amd64 version still has the usplash bug with gf8800 graphics cards.

You can disable usplash by hitting esc at boot (during countdown) and then select verbose mode.

---

### Post by lond on 2008-02-25
> **ago said:**
> kernel (hd4,0)/ubuntu/disks/boot/

The problem is that vista detecting the hard drives like this:
PM - Disk0
PS - Disk1
SM - Disk2
3M - Disk3
4M - Disk4 - Here is my C: and my Ubuntu install

My boot sequence is: 4M - PS - SM - 3M - PM

GRUB is detecting 4M as Hd0 and PM as Hd4

After the installation I booted in to vista and changed the menu.lst Hd4,0 to Hd0,0 and rebooted.

When I try to boot ubuntu in safe mode i get this system halt:

---

### Post by ago on 2008-02-25
It doesn't really matter how vista reads the partitions, what matters is how Grub4Dos sees them, and you can use the tab completion trick above to find out. Also you might want to try running chkdsk /r (from windows) within the drive hosting the ubuntu folder

---

### Post by lond on 2008-02-25
The Grub4Dos sees it as Hd0,0, at least it is there i found ubuntu :)

---

### Post by evan d on 2008-02-25
> **lond said:**
> When I try to boot ubuntu in safe mode i get this system halt:

Looks like ntfs-3g died.  Are you by any chance using the amd64 Ubuntu CD?

---

### Post by Dominator86 on 2008-02-25
Both versions, i386 and amd64, of the new Kubuntu ISO give me the following message shortly after the xserver is loaded:

> There was an error setting up inter-process communications for KDE.
Please check that the "dcopserver" program is running!

The system restarts when I click 'OK'.
I'm not able to switch to another console.

The previous ISOs didn't show this message, but the install failed:
The Hardy Live-CD booted well, then I clicked on 'Install' and ''Next', then the screen went black and the system restarted.

---

### Post by ago on 2008-02-25
> **Dominator86 said:**
> Both versions, i386 and amd64, of the new Kubuntu ISO give me the following message shortly after the xserver is loaded:



The system restarts when I click 'OK'.
I'm not able to switch to another console.

The previous ISOs didn't show this message, but the install failed:
The Hardy Live-CD booted well, then I clicked on 'Install' and ''Next', then the screen went black and the system restarted.

That is a known bug that affects kubuntu users (see the caveats in the hardy5 release note). You have 2 options: 

1) If you do NOT click ok the system should finish the installation anyway (even if you won't see a thing for 15 minutes) and reboot into an installed system

2) Use Ubuntu images and then install the kubuntu-desktop package

---

### Post by evan d on 2008-02-25
Or 3) Wait for tomorrow's daily live CD, as I've uploaded a new version of ubiquity that fixes this.

---

### Post by ago on 2008-02-25
> **ago said:**
> That means that it is looking in partition 5 of drive 1. Is this where you installed wubi? You can press esc at the countdown, then press "C", then use tab expansion to see what is visible.

I meant partition 1 of drive 5. Would be interesting to know why the target partition appered to grub as (4,0) during installation and (0,0) after installation...

---

### Post by switchfrenzy5 on 2008-02-25
Will my problem be fixed with tomorrow's release build with ubiquity and the migration assistant? You da man Evan.

---

### Post by lond on 2008-02-25
> **ago said:**
> I meant partition 1 of drive 5. Would be interesting to know why the target partition appered to grub as (4,0) during installation and (0,0) after installation...

I have installed 7.10 before with no problem :) :confused:

// lond

---

### Post by ago on 2008-02-25
> **lond said:**
> I have installed 7.10 before with no problem :) :confused:

// lond

The grub mechanism is a bit different in 8.04

---

### Post by Derek Chai on 2008-02-25
Ok I am testing. Burning it right now.

Should I uninstall wubi>

---

### Post by Derek Chai on 2008-02-25
Uninstalled wubi tried7.10 & 8.04 same errors as in video live mode won't starry

---

### Post by Derek Chai on 2008-02-25
Just searched HP m7160n lot's of problems won't work that's the problem  I think you guys need to fix.

---

### Post by evan d on 2008-02-26
> **switchfrenzy5 said:**
> Will my problem be fixed with tomorrow's release build with ubiquity and the migration assistant? You da man Evan.

No, not yet.

---

### Post by switchfrenzy5 on 2008-02-26
Evan, what is the best way to know when my problem will be fixed? I hate badgering you here on one specific thread.

---

### Post by evan d on 2008-02-26
> **switchfrenzy5 said:**
> Evan, what is the best way to know when my problem will be fixed? I hate badgering you here on one specific thread.

I just created a bug report to track the issue in.  Subscribe to it and it will automatically notify you via email when a fixed version of ubiquity has been uploaded.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/195905/+subscribe](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/195905/+subscribe)

The following day new CDs will be automatically made with the fixed version and put on [http://cdimage.ubuntu.com/daily-live/current](http://cdimage.ubuntu.com/daily-live/current)

---

### Post by ago on 2008-02-26
> **lond said:**
> The problem is that vista detecting the hard drives like this:
PM - Disk0
PS - Disk1
SM - Disk2
3M - Disk3
4M - Disk4 - Here is my C: and my Ubuntu install

My boot sequence is: 4M - PS - SM - 3M - PM

GRUB is detecting 4M as Hd0 and PM as Hd4

After the installation I booted in to vista and changed the menu.lst Hd4,0 to Hd0,0 and rebooted.

When I try to boot ubuntu in safe mode i get this system halt:

Can you pls tell me what the disk sequence looks like from inside Ubuntu?

You can use the grub command to find out

Can you please also post /boot/grub/device.map (commenting which device is which disk?)?

I am trying to understand if there is any difference in the way drives are ordered between Ubuntu's grub (inside Ubuntu) and grub4dos

---

### Post by lond on 2008-02-26
I will do that tomorrow after work.

// lond

---

### Post by Derek Chai on 2008-02-26
ubuntu don't work with windows media center edition

---

### Post by ago on 2008-02-26
Do you mean the Live CD or Wubi? The Live CD should work whatever OS you have installed (save hardware incompatibilities). If it's Wubi failing, what exactly is the problem?

---

### Post by Derek Chai on 2008-02-26
no no if you do a search on here the ubuntu forums search m7160n look at it ubuntu doesn't even work on my computer//

---

### Post by lond on 2008-02-27
From device.map
(fd0)	/dev/fd0
(hd0)	/dev/hda - PM
(hd1)	/dev/hdb - PS
(hd2)	/dev/hdc - SM
(hd3)	/dev/sda - sata1
(hd4)	/dev/sdb - sata2 - First boot disk, VISTA c:/ and wubi-ubuntu installed

grub4dos discovers hd4 as hd0

---

### Post by lond on 2008-02-28
After I have changed the Hd-settings in the menu.lst Ubuntu boot, but goes to a black screen. If I boot in safe mode I end up with this screen:

---

### Post by alzie on 2008-03-04
I downloaded and burned the iso last night (Mar 3)

The burning went uneventful (gnome baker) until the cd was finalizing then I got an error.  I decided to try the cd anyways.

Is there a trick to burn 703 MB on 700 MB cd?

In windows XP Pro I attempted to install wubi.  The installation went to the very end (99+%) before it stopped.  It complained that the cd was being accessed by another program.  I tried again, same result.

Rebooted to try the live cd.  I ran the check cd first, no issues, the cd is good.  I'm typing this from the live cd.  My only issue is my nvidia card is not detected (800x600 resolution 	:neutral: )

Network picked my windows network (2 computers) automatically,  that's never happened before :)

Granted I'm not taxing the system,  just looking around, my cpu is running at under 10 % and memory is under 50 % (Running live cd)

All in all I'm very pleased.  I will be trying to burn another iso to see if I can get wubi going.

AMD Athlon XP 2200+ with 768 MB ram Geforce 6200 nVidia card

---

### Post by ago on 2008-03-04
> **alzie said:**
> 
In windows XP Pro I attempted to install wubi.  The installation went to the very end (99+%) before it stopped.  It complained that the cd was being accessed by another program.  I tried again, same result.
might be becaused...

"The burning went uneventful (gnome baker) until the cd was finalizing then I got an error.  I decided to try the cd anyways."

Or because you had the windows explorer open.

Anyway you can use wubi directly with an ISO without any need to burn a CD. Just put wubi.exe and the ISO in the same folder.
Get wubi here: [http://wubi-installer.org/devel/minefield/](http://wubi-installer.org/devel/minefield/)

---

