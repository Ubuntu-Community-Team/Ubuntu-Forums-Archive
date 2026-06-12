---
title: "QuickStart: Back-up, Restore, &amp; Set-up Ubuntu Quickly and Easily"
date: 2007-11-14
forum: General Help
---

### Post by mdpalow on 2007-11-14
QUICKSTART has been moved. If you would like to download this program or discuss it more, please visit:

[http://quickstart.phpbb.net](http://quickstart.phpbb.net)   for the forum

[http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11)  for the thread to download QuickStart

********************************************************************************

Hi Everyone,

I've written an Ubuntu script to expedite some things I do on my computer. If interested, you're welcome to download and use it. I call it QuickStart 
(screen shots are attached below) and with it you can:


[COLOR="Red"]1. Install the proper DVD & Codecs files so you can play a DVD in your drive using Totem, etc. (works with 7.10 / 7.04 and 32-bit / 64-bit). [/COLOR]

2. Back-up Your /home folders  

3. Back-up Your / folders

4. Back-up Your Configuration files separately (fstab, device.map, mtab, menu.lst, and xorg.conf)

5. Create a Custom Back-up for selected folders

6. Create a Custom Scheduled (Recurring) Back-up (daily, weekly, or monthly). You decide the exact date and time

7. Create a Scheduled 1:1 Synchronized Back-Up of Selected Folders to Another Drive/Partition.

8. Restore Your System /home folders

9. Restore Your / folders

10. Restore Your configuration files

11. Install some common applications (aMSN, aMSN fix, Firestarter,  AllTray, and a few others). Nice when you're starting from scratch (clean install)

12. House Cleaning (delete unnecessary files throughout your computer). 

13. View or Edit Your Key Files (fstab, menu.lst, and xorg.conf).

[COLOR="Red"]14. Back-up Your Master Boot Record (MBR)[/COLOR].

[COLOR="Red"]15. Back-up Your Windows Partition (dual booters) While in Ubuntu[/COLOR].

16. Format Windows Partition in NTFS with gParted.

[COLOR="Red"]17. Restore Your Master Boot Record (MBR)[/COLOR].

[COLOR="Red"]18. Restore Your Windows Back-Up While in Ubuntu[/COLOR].

19. Download Updates/Upgrades with a click of the mouse.



**How to download and install QuickStart** (Please follow these instructions exactly as they are written) :

1. Left-click the Install_QuickStart.sh file below and save it to your [COLOR="Red"]DESKTOP[/COLOR]

2. RIGHT click the Install_QuickStart.sh file on your DESKTOP and select Properties, then select the Permissions tab at the top, and ensure the 'Execute' check-box is checked towards the bottom where it says 'Allow executing file as program'. Close window.

3. If you installed the Ubuntu 32-bit OS you can skip this step. If you installed the Ubuntu 64-bit OS, open a terminal window and copy/paste the following, so your system can run 32-bit applications: [COLOR="Red"]sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0[/COLOR]

4. Click or double-click the Install_QuickStart.sh file now located on your Desktop and select [COLOR="Red"]Run in Terminal[/COLOR]

You will now have a QuickStart icon in your menu ( Applications -> Accessories -> QuickStart ) 



[COLOR="Blue"]1.) Please post a message after downloading the program to bump it to the top for others to see in case they want it too.[/COLOR]

[COLOR="Blue"]2.) Probably a good idea to subscribe to this thread if you plan on using this program as some postings might be of interest to you.[/COLOR]

[COLOR="Blue"]3.) FYI: QuickStart is free to use, but the source is not open. If that's problematic for you, I recommend you don't download it.[/COLOR]
.

---

### Post by poudin on 2007-11-15
looks cool...i would try it if you made it available.

---

### Post by sloggerkhan on 2007-11-15
Hmm. It looks pretty straightforward.

---

### Post by Inxsible on 2007-11-15
Does it take a bit by bit image of the partition like partimage ?

or simply a copy of all the files?

---

### Post by gupta_sumesh63 on 2007-11-15
Very much interested.
Be kind enough to share it please.:guitar:

---

### Post by mdpalow on 2007-11-15
> **Inxsible said:**
> Does it take a bit by bit image of the partition like partimage ?

or simply a copy of all the files?

TAR copies files and is able to compress them, but it doesn't make an image.

---

### Post by llamakc on 2007-11-15
What option flags are you using with tar?

---

### Post by mdpalow on 2007-11-15
> **llamakc said:**
> What option flags are you using with tar?

I would post, but I have many '$ex' in the actual tar command, which are referenced elsewhere in the code and I don't want to paste all that here as it's pretty lengthy.

Also, depending on which option you select, the arguments/flags/parameters change and I'd have to post them all here as well.

I am keeping file permissions and restoring with same-ownership.

---

### Post by mdpalow on 2007-11-16
I'm looking to update this program with an additional feature that will allow you to only restore your desktop menu (the one that has your applications, places, and System). Does anyone know which file(s) contain the menu? If you do, please send full path.

I'm looking to do this 'cause last night, I saw a reason for just wanting to install this alone without the rest of the back-up and think I will add this to the program.

Based on what I've seen, I believe it's more than one file and more like three.

Thanks in advance...

---

### Post by poudin on 2007-11-16
Downloaded...very nice work...tried it and seems to work great

also compliments on the layout of the script...very easy to read and see breakdown...

keep up the good work!!!!!:):):)

---

### Post by mdpalow on 2007-11-16
> **poudin said:**
> Downloaded...very nice work...tried it and seems to work great

also compliments on the layout of the script...very easy to read and see breakdown...

keep up the good work!!!!!:):):)

Thanks Poudin. Your review is very much appreciated.

I've actually made an update/upgrade to uBackup!

Now it will, if you select the option, automatically install 12 of the most used applications one after another without ever having to go to Synaptic. Here's a short list of what can be installed:

Flash, aMSN, aMSN update/fix, gStreamer, K3B, Firestarter, AllTray, and a few others. 

I haven't decided if I want to upload this version for members/users yet; we'll see.

Thanks again....

.

---

### Post by mdpalow on 2007-11-17
I've added two nice features to uBackup!, which I believe will help a lot of users.

The two updates are as follows:

1. Option 14 - Installs most commonly used applications with one key stoke (see list below).

2. Option 15 - Installs the necessary DVD and Codecs files, so you can watch a DVD on your DVD player. If you're having difficulty playing DVDs - this 'should' finally do it for you...

Both options have been tested and work nicely. Performed a clean install with 7.10 (both 32 and 64 bit versions) and had no ability to watch a DVD on computer. Ran option 15 and DVD played directly after install.

Here's a list of the commonly used programs that will be installed:

1 -  All Tray                      - Allows you to minimize applications to system tray
2 -  aMSN                         - The Linux MSN Messenger clone
3 -  DeVeDe                     - Program that allows you to copy a DVD to disk
4 -  Firestarter                  - The GUI for your firewall
5 -  Flash Plugin                - Adobe Flash Player plugin installer
6 -  gParted                       - A partition editor
7 -  K3B                             - The Linux version of Nero 
8 -  Build Essential             - Essential tools for building Debian packages.
9 -  aMSN Fix                   - Gives aMSN a much cleaner look and better font usage

I understand this list might be viewed as 'subjective,' but for the most part, these files are commonly used by many and shouldn't create too much of a discussion. :)

Enjoy the upgrades!

..

---

### Post by mdpalow on 2007-11-18
One change to uBackup! :

uBackup!.Help file has been updated and included in new package.
No updates/changes to uBackup!

---

### Post by jryprt on 2007-11-18
Just used it worked great .
Thanks Great Job

---

### Post by Dumpy Dumpster on 2007-11-18
Woaaa there,son!!
I am 2 days into Ubuntu Fawn, and I logged onto_ Absolute Beginners_ to try to learn something!
I clicked on the link <uBackup!.tar.gz> and it came up - but not on desktop.  In fact I have no idea where it has gone.
Lots of people say - how simple - well I AM EVEN SIMPLER and cannot made head or tail of most of the following threads.
As an ex-Windows user, I am used to simple installations and downloads, but I am completely lost.
Words of 1/2 a syllable. please!   Perhaps I should have chosen SIMPLETON for a user name     Thanks.

---

### Post by mdpalow on 2007-11-18
Ok, just for you Dumpy,

I've updated the original post with the following:

(Right click on file and select SAVE LINK AS) Save it to your Desktop.

Let me know if that doesn't help you.

.

---

### Post by Dumpy Dumpster on 2007-11-18
Thank you, mdpalow, but not really!  I did this and it saved as <attachment.php> that a left click would not open.   This is all rather complicated and it seems to me that this OS is for experts and not novices!!
You must not forget that Windows for all it's faults, was VERY simple to use!

---

### Post by philinux on 2007-11-18
```
windows was simple to use
```

Only cos you've been using it a long time. :lolflag:

I've been using ubuntu since August and now it seems easier than windows. 

give it time.

The link just needs a left click not right.

---

### Post by jryprt on 2007-11-18
> **Dumpy Dumpster said:**
> Woaaa there,son!!
I am 2 days into Ubuntu Fawn, and I logged onto_ Absolute Beginners_ to try to learn something!
I clicked on the link <uBackup!.tar.gz> and it came up - but not on desktop.  In fact I have no idea where it has gone.
Lots of people say - how simple - well I AM EVEN SIMPLER and cannot made head or tail of most of the following threads.
As an ex-Windows user, I am used to simple installations and downloads, but I am completely lost.
Words of 1/2 a syllable. please!   Perhaps I should have chosen SIMPLETON for a user name     Thanks.

Click on it again the uBackup!.tar.gz & when it ask choose save to disk the go to 1st post and read it .

---

### Post by mdpalow on 2007-11-18
Yeah, what he said above. :)

Just go to the first post where the file is located.

Click on the file and save it to your Desktop.

Then read the instructions in the first post on how to install it.

You should know that unzipping a a program in Linux is no different than in Windows. Also, if you can select files in Windows and drag them to another folder then you shouldn't have any problems with this as it's the same thing.

Good luck and let us know how you come along. I'm watching this thread, so if you post a problem, I'll get it and respond.

...

---

### Post by coskierken on 2007-11-18
[FONT="Times New Roman"]I used the uBackup!.  I have used the functions of backup/restore for the system and home files, mounting, and drive info.  It worked perfectly.:)  I was having problems with the DVD playback under the Totem MoviePlayer with gstreamer,  Once I used the utility via uBackup! for installing the files needed, it works fantastic.:)  I, also, use the utility to install the comman apps, which were extremely useful.  I have since backed up my entire system for both installs of 32-bit and 64-bit.  I am currently using 64-bit.  I can do an install and restore in about 20 minutes.  A complete restore of XP takes me a few hours[/FONT].  :KS:KS:KS:KS:KS

---

### Post by gn2 on 2007-11-18
Here's another useful tool: [http://ubuntu-unleashed.blogspot.com/2007/09/remaster-and-clone-your-ubuntu-install.html](http://ubuntu-unleashed.blogspot.com/2007/09/remaster-and-clone-your-ubuntu-install.html)

---

### Post by ericartman on 2007-11-18
Really impressive, very easy and fast.  Now if you could just get my printer to install :lolflag:

Cart

---

### Post by tonymoloney on 2007-11-18
Hi there.
I came across this thread and it looked to be exactly what I want, so I downloaded the tar.gz to my desktop and tried to follow the instructions.
However, after right-clicking on the file and selecting "Extract Here", I fell in a hole.
I can't click on the uBackup! folder 'cos there is none!
All I have on my desktop are:
uBackup!.tar.gz
uBackup.help and
uBackup! (which isn't a folder, but a shell script)
I've used the search function to look for a uBackup! folder anywhere under / but can't find one.
I'm using Kubuntu - would that make a difference?

---

### Post by mdpalow on 2007-11-18
Hang on tonymoloney...

Let me test the process and see if I can figure out what's going on...

.

---

### Post by mdpalow on 2007-11-18
hmm, not sure why that was happening...

All you should have to do is click on the attached file (no right click) and save to your desktop. Then right click on uBackup!.tar.gz file and select EXTRACT HERE. Then just move the folder to - Example -  /home/Chris

<where Chris would be your name instead>

Go into the uBackup! folder you just moved and then click/double-click on the uBackup! file and select 'Run in Terminal'

Can you please reply with how these instructions worked for you, so we can tweak if necessary?

Thanks....

---

### Post by Dumpy Dumpster on 2007-11-19
Thanks to you all for your patience!
I see the thread has been moved from Absolute Beginners, which is where I belong!!   I will scrub this for the moment.

---

### Post by mdpalow on 2007-11-19
Hi Dumpy,

The post was actually moved because my post is providing help and not a request for help. Go figure...

If you want to click on my name above and send me a private message with your e-mail address, I'll send you the two files uncompressed - so you don't have to unzip them. 

If you know how to make a folder and know how to save an e-mail attachment, then you will be able to do this. :)

Everyone has to start somewhere, so don't get too frustrated. I'll help you if you want it. 

mdpalow

---

### Post by olivero1 on 2007-11-20
Just what I was looking for!

Thanks for this script - it will save me hours of custom settings if I ever need to reset the OS!

---

### Post by mdpalow on 2007-11-20
You're welcome olivero1. :)

To all those who have already download uBackup! - version 1.1 has just been uploaded to this posting. Please be sure to download it.

uBackup! Version 1.1

Only a minor change in presentation of Option 8. However, you are highly encouraged to download it because of the three restore options - this is the one that can have dire consequences if used incorrectly.


Changes:

Help File: Updated to be much more detailed with regard to how/when you should use option 8. 

Program: Set it to:

1. Halt

2. Remind you to have read and understood the function you are about to perform

3. Give you the menu option to:

       Read help file again
       Continue with Restore
       Exit to Main Menu

I realize this may seem as a non-vital update for some, but consider this scenario:

You download uBackup!, read the help file, and then make your back-ups. Then, two months from now something happens and you need to restore. 

Since you're about to restore anyway, you decide you're first going to change some partition settings because you didn't like your previous set-up.

Now you re-install Ubuntu and have a different 'fstab' configuration file. You've since forgotten how/when Option 8 should be used and proceed to restore your 'fstab' file to the way it was BEFORE you changed your set-up and now your system doesn't boot!

Had you been reminded of the proper use for Option 8 before you actually ran it, you might not have made this mistake.

Again, it's not a major update, but a simple reminder that will most likely cause you to read Option 8 in the help file and save some a lot of grief.

Just looking out for your best interest. :)

---

### Post by Dumpy Dumpster on 2007-11-20
Fellas,
If someone as new as Dumpy Dumpster can get it to work after some initial clumsiness on my part - it has got to be good!
Go for it NOW

---

### Post by ericartman on 2007-11-21
Question, how so I know which version I have? Checked help file, found nothing obvious. BTW this program rocks!

Cart.

---

### Post by mdpalow on 2007-11-21
thanks ericartman. :)

When you run the program, look in the top right corner of the Main menu. The version number is printed there.

---

### Post by ntu on 2007-11-21
Many thanks to mdpalow for this backup facility. I have just used it and now have 3 backup files on the desktop :).

---

### Post by mdpalow on 2007-11-21
> **ntu said:**
> Many thanks to mdpalow for this backup facility. I have just used it and now have 3 backup files on the desktop :).

You're welcome ntu.

If you have an extra hard drive, be sure to copy a set onto each drive just in case one of them should crash or have a problem. If the back-ups are small enough, copy them to a CD/DVD.

take care and thanks again...

---

### Post by ntu on 2007-11-21
> **mdpalow said:**
> 

If you have an extra hard drive, be sure to copy a set onto each drive just in case one of them should crash or have a problem. If the back-ups are small enough, copy them to a CD/DVD.


Thank you for your comments mdp. 

I have an internal 'storage' hdd for storing files on (fat32) and was wondering if I moved the 3 backup files to it, would I need to move them back to the desktop again to restore, or could I restore from the storage hdd? I am new to backing up proceedures.

---

### Post by mdpalow on 2007-11-21
> **ntu said:**
> Many thanks to mdpalow for this backup facility. I have just used it and now have 3 backup files on the desktop :).

> **ntu said:**
> Thank you for your comments mdp. 

I have an internal 'storage' hdd for storing files on (fat32) and was wondering if I moved the 3 backup files to it, would I need to move them back to the desktop again to restore, or could I restore from the storage hdd? I am new to backing up proceedures.

You can put the finished back-up files wherever you like. If/when it comes time to restore a back-up file, uBackup! will ask you where the file(s) is /are located. 

I only set it to put the files on your Desktop, so there would be no confusion as to where they are...

---

### Post by ntu on 2007-11-21
> **mdpalow said:**
> If/when it comes time to restore a back-up file, uBackup! will ask you where the file is located. 

I only set it to put the files on your Desktop, so there would be no confusion as to where they are...

Ah, thank you for this clarification.

I am still quite perplexed about restoring and which file to use to restore what.

In a worse case scenario whereby I have somehow formatted my hdd, what would be the restore procedure then? Assuming I still had the ubackup! files on my storage hdd.

Sorry if this question is rather over the top, but it would give peace of mind here if I knew how to recover from a major mistake.

---

### Post by mdpalow on 2007-11-21
> **ntu said:**
> 

I am still quite perplexed about restoring and which file to use to restore what.

In a worse case scenario whereby I have somehow formatted my hdd, what would be the restore procedure then? Assuming I still had the ubackup! files on my storage hdd.

Sorry if this question is rather over the top, but it would give peace of mind here if I knew how to recover from a major mistake.

Three files are created and placed on your Desktop after back-up. 

The system_backup_mm.dd.yyyy.tgz and the home_backup_mm.dd.yyyy.tgz files are the ones you would restore after Live CD install. uBackup! will ask you where the files are located (most people will not keep these back-up files on their Desktop). Simply put in the path for one of the files and it will restore. Then put the path in for the other file and let it restore. All done.. 

Just make sure you keep the three files and uBackup! somewhere safe; preferably a different drive. I like to keep all three files on two separate hard drives, since the chance of both drives having problems at the same time is not likely.

BTW, each of the restore options actually display text on the next screen telling you what to do and WHICH file it's wanting to use to restore. 

Did that help any?

Good luck.

---

### Post by ericartman on 2007-11-21
OK I just switched to 64 bit, just because, and the FIRST thing I did was run your program, it made my start up sooooo easy, a million thanks

Cart

---

### Post by ntu on 2007-11-21
> **mdpalow said:**
> Three files are created and placed on your Desktop after back-up. 

The system_backup_mm.dd.yyyy.tgz and the home_backup_mm.dd.yyyy.tgz files are the ones you would restore after Live CD install. uBackup! will ask you where the files are located (most people will not keep these back-up files on their Desktop). Simply put in the path for one of the files and it will restore. Then put the Andpath in for the other file and let it restore. All done.. 

Just make sure you keep the three files and uBackup! somewhere safe; preferably a different drive. I like to keep all three files on two separate hard drives, since the chance of both drives having problems at the same time is not likely.

BTW, each of the restore options actually display text on the next screen telling you what to do and WHICH file it's wanting to use to restore. 

Did that help any?

Good luck.

Thanks for this mpd. This is what I especially needed to know:

> The system_backup_mm.dd.yyyy.tgz and the home_backup_mm.dd.yyyy.tgz files are the ones you would restore after Live CD install. uBackup! will ask you where the files are located

Thank you.

And I now have all 3 backup files on 2 hdds. :)

---

### Post by ntu on 2007-11-22
> **mdpalow said:**
> 
The system_backup_mm.dd.yyyy.tgz and the home_backup_mm.dd.yyyy.tgz files are the ones you would restore after Live CD install. 

I am now wondering.....
In the above quote, does "Live CD install" mean:
1. putting the live/install cd in and booting to the live desktop? Or;
2. after reaching the live desktop, installing the system from the live/install cd?

---

### Post by mdpalow on 2007-11-22
> **ntu said:**
> I am now wondering.....
In the above quote, does "Live CD install" mean:
1. putting the live/install cd in and booting to the live desktop? Or;
2. after reaching the live desktop, installing the system from the live/install cd?

Sorry to get to this so late. I didn't get an alert for the previous post.

What I mean by this is:

If you needed to do a restore of your system, you would place the Live CD in your CD ROM and boot it up. When it comes up, you would then install Ubuntu. When finished, you would run uBackup! and run Option 6 to restore the system_backup_mm.dd.yyyy.tgz file. Then you would run Option 7 to restore the home_backup_mm.dd.yyyy.tgz file. Done! You may need to run Option 8 also, but you are alerted by the program to read the Help file for this option to see if you meet the requirements. Most people will probably not need to run Option 8. 

Now your system will be exactly like the day you backed it up. 

Hope this helps...

Please take some time to also read the help file. I think it will help you understand how uBackup! works.

---

### Post by mdpalow on 2007-11-22
> **ntu said:**
> 

Thank you.

And I now have all 3 backup files on 2 hdds. :)

Perfect! 

...and you're welcome. :)

---

### Post by mdpalow on 2007-11-22
Just a reminder to all. 

uBackup! is not JUST for a complete restore of your system; that's why I separated the back-up process into three (/, /home, and config) files.

If you were to mess something up in your / directories, then you can simply use Option 6 to restore /. 

If you messed something up in your /home directories, then you can simply use Option 7 to restore /home. 

If you messed up your menu.lst, xorg.conf, device.map, fstab, and/or mtab file(s), then you could simply use Option 8 to restore to restore these files.

I'm about to make an update (version 1.2) that will allow you to select an individual file or folder to restore. An example of how to use this would be:

You're running VMware or Virtualbox with windows xp and mess something up. If you're like me and have one of these running in your /home directory, that back-up file is about 5 gigs. Maybe you just want to restore the VMware directory and not the entire /home. You'll be able to just select the VMware directory for restore and be done.

By the way, uBackup! works VERY nicely with backing up VMware files. When I'm done restoring my back-up, my virtual windows runs perfectly every time. That means no re-installing windows, photoshop, and dreamweaver each time. That saves me ~ 1.5 hours in itself.

---

### Post by ntu on 2007-11-22
Thank you mdp. I will try to give you some peace now. You have well earnt it.

---

### Post by garry4o on 2007-11-22
Mike:

Really good job. A couple of things I noticed:

1) While in menu 2 (options 11-16), when entering 0, I stayed in menu 2 rather than returning to menu 1.

2) I quickly scanned the script, just as a learning experience. I noticed that the function declaration for function "option_11" was spelled as "opion_11", and would probably not call correctly.

I'm ready to try the actual backup and restore now. I've spent a long time looking for just this solution.

Thanks for the work

Garry

---

### Post by frodon on 2007-11-22
I always found tar commands too long for this kind of stuff, [partimage]("http://www.partimage.org/Main_Page") is for example way faster than this kind of solutions and i recommend it first as it is full featured, stable and reliable backup tool with an intuitive GUI.
As a comparison it takes me 10mins to backup my 6.4Go ubuntu partition (with normal compression) and 5 minutes to restore it.

This is a nice home made script to create backups but it is still less convenient than a solution like partimage which is a reference.

---

### Post by garry4o on 2007-11-22
Hi Mike again:

Error in my first post. I was in what ever the menu to edit/view menu.lst, etc, that I could not exit from (after viewing all three files, if that matters).

---

### Post by mdpalow on 2007-11-22
> **garry4o said:**
> Mike:

Really good job. A couple of things I noticed:

1) While in menu 2 (options 11-16), when entering 0, I stayed in menu 2 rather than returning to menu 1.

2) I quickly scanned the script, just as a learning experience. I noticed that the function declaration for function "option_11" was spelled as "opion_11", and would probably not call correctly.

I'm ready to try the actual backup and restore now. I've spent a long time looking for just this solution.

Thanks for the work

Garry

Thanks Gary. I made the fix and spelled it correctly now. :) Will upload now.

Not sure what you mean in number 1. In menu 2 there are two options. One option is to return to main menu (16) and the other is to exit uBackup! completely (0). Both work correctly. Am I missing something?

---

### Post by mdpalow on 2007-11-22
> **garry4o said:**
> Hi Mike again:

Error in my first post. I was in what ever the menu to edit/view menu.lst, etc, that I could not exit from (after viewing all three files, if that matters).

Hi again Gary.

Ok, I saw what you were talking about. I've updated the menu system to now allow you to get out to main menu again.

I also upgraded the menus a little as well.

Good timing actually since I also updated the help file with some FAQs and added text to explain a few more things.

Would appreciate it if you could try and reproduce the menu problem with option 12 again...

To all... this menu typo did/does not affect any back-ups you may have made. This is purely a menu problem.

Will upload files now and call this version 1.2 so everyone knows if they have a previous release.

---

### Post by toupeiro on 2007-11-22
I'm a user of sbackup, but I like the potential of your tool.  couple of questions:

1.  Can it be scheduled?
2.  Can it maintain a backup rotation?
3.  Does it keep a catalog?
4.  Can it do incremental/Differential backups?

---

### Post by mdpalow on 2007-11-22
> **frodon said:**
> I always found tar commands too long for this kind of stuff, [partimage]("http://www.partimage.org/Main_Page") is for example way faster than this kind of solutions and i recommend it first as it is full featured, stable and reliable backup tool with an intuitive GUI.
As a comparison it takes me 10mins to backup my 6.4Go ubuntu partition (with normal compression) and 5 minutes to restore it.

This is a nice home made script to create backups but it is still less convenient than a solution like partimage which is a reference.

I see this as being a viable option, but I can also foresee a scenario where boot-up problems will occur if/when users makes some changes to their system. That's why uBackup! is written to back-up a few critical config files separately. 

I personally would have suffered this problem had I used your suggestion and I have read where many others have done the exact same thing that would cause 'partimage' to be problematic for them as well.

Not trying to knock your suggestion in favor of mine; just thinking out-loud. In fact, I'm even going to look into your suggestion.

Also, please let's not debate in this thread as it will just clutter it up with _non-tar_ options, so please private message me if you or anyone would like to discuss further.  Thanks. :)

---

### Post by mdpalow on 2007-11-22
> **toupeiro said:**
> I'm a user of sbackup, but I like the potential of your tool.  couple of questions:

1.  Can it be scheduled?
2.  Can it maintain a backup rotation?
3.  Does it keep a catalog?
4.  Can it do incremental/Differential backups?

1. If you knew how to extract the commands I've implemented and knew enough about Linux, you could do it - but at this stage of development it doesn't. I am looking into adding this ability, but I have to do a little checking on something first.

2. No

3. No

4. Not yet, but it's something I'm looking at adding very soon as I think I may want this also.

---

### Post by delphiguy on 2007-11-22
This looks like a cool utility to have.  Gonna try this one out.

Thanks a lot dude.

---

### Post by mdpalow on 2007-11-22
If you wish to use uBackup! and are interested in automatic scheduling of back-ups, would you pls post here and let me know.

I can add a menu option to uBackup! that will create an automatic scheduling of back-ups on a daily, weekly, or monthly basis if it's wanted.

If so, I think it'll be a back-up that looks at your current archive to determine if there is anything new or different to add and if so; it will append to it.

Thanks...

---

### Post by ericartman on 2007-11-23
Scheduled and incremental would be outstanding, two thumbs up lol

Cart

---

### Post by mdpalow on 2007-11-23
> **ericartman said:**
> Scheduled and incremental would be outstanding, two thumbs up lol

Cart

Almost have it done. Should be ready to go in a couple/few days. uBackup! will now allow you to create daily, weekly, and monthly back-ups based on the hour/day/date you want automatically.

I first have to add the last part, which is incremental and then want to clean up some of the original code, and then finally update the .help file.

If you've downloaded uBackup! before or about to, recommend you consider subscribing to this thread, so you'll know if/when updates come out.

---

### Post by mdpalow on 2007-11-24
Hi everyone,

uBackup! 2.0 will now create scheduled back-ups, which you can have run daily, weekly, and monthly.

I've also reconfigured the menus to be a little more intuitive, so now - steps 1 of 3, 2 of 3, and 3 of 3 are related to 1, 2, and 3 on keyboard. I've moved a couple more things around in the menus, but nothing major.

I still need to update the help file with the new scheduled back-up option and then it should be done.

I'd like to have a few people test out the new function and also just give it a run through with the menus to make sure I didn't miss anything.

I've already tested the scheduled back-up option several times and it appears to work flawlessly, but it would be nice to have another user go over it as well.

If you're interested, please Private Message me so I can send it to you.

I'll upload it when everything is ready to go.

Thanks in advance ...

---

### Post by Eion on 2007-11-24
Thank you for this!  My DVD's are working now!

---

### Post by L.C.D. on 2007-11-25
Doesnt seem to work for me installing correct codecs to play DVDs.  VLC and ogle just close themselves if I try to play a DVD and totem asks if I have libdvdcss installed.  

I'm running 7.10 64bit and I used the correct option in the script but still no luck.

Also tried VLCs option of playing a directory which sometimes works but again, same problem as if i had just told it to play a disc

---

### Post by mikewhatever on 2007-11-25
> **L.C.D. said:**
> Doesnt seem to work for me installing correct codecs to play DVDs.  VLC and ogle just close themselves if I try to play a DVD and totem asks if I have libdvdcss installed.  

I'm running 7.10 64bit and I used the correct option in the script but still no luck.

Also tried VLCs option of playing a directory which sometimes works but again, same problem as if i had just told it to play a disc

Try [https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29%7C%28formats%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29%7C%28formats%29)

---

### Post by mdpalow on 2007-11-25
> **L.C.D. said:**
> Doesnt seem to work for me installing correct codecs to play DVDs.  VLC and ogle just close themselves if I try to play a DVD and totem asks if I have libdvdcss installed.  

I'm running 7.10 64bit and I used the correct option in the script but still no luck.

Also tried VLCs option of playing a directory which sometimes works but again, same problem as if i had just told it to play a disc

I've seen this happen before on a friend's computer. For him, it didn't have anything to do with his Codecs, but was related to his restricted driver manager / video card and some additional drivers he needed to load for his card.

He also was using the 7.10 64-bit at the time.

---

### Post by mdpalow on 2007-11-25
I've finished uBackup! 2.0 and uploaded it for anyone who would like to have it.

This version will now make it very easy for you to schedule a daily, weekly, or monthly back-up.

All you have to do is select when you want it to run and it will do the rest for you.

enjoy ...

---

### Post by ericartman on 2007-11-25
Outstanding! Works like a charm. Thank you very much, my life is much easier because of this, believe me. Think I'll go put it on the wifes computer. Should be called Newbie Swiss Army Knife lol.

Thanks again
Cart

---

### Post by mdpalow on 2007-11-25
Thanks Cart.. I'm glad it's working out for you.

Since uBackup! does more than just back-up a system, I could see a reason to change the name, but I haven't given it too much thought just yet.

However, if you or anyone else wants to suggest a name, I'll definitely consider changing it for the next version, which will have a GUI interface - so you can point and click. :)

---

### Post by mdpalow on 2007-11-25
Many thanks to CART for finding a bug in the menu options.

Apparently if you went into Option 8 and then exited back to Main menu (4), the option to then exit out of uBackup! (0) took you back to Option 8 instead of exiting.

Fixed and uploaded...

CART verifies the new scheduled back-up option is working for him....

---

### Post by ericartman on 2007-11-25
Hey what are friends for? Glad I could help.

Cart

---

### Post by mdpalow on 2007-11-27
Hi Everyone,

Had been told there was a problem with exiting a menu properly the other day. That was fixed and re-uploaded.

Had a feeling I better check the menus one more time just to make sure and I found two exit options that didn't take you to the following menu properly.

They are fixed now and uBackup! has been uploaded.

Please grab it if you're using uBackup!

---

### Post by mdpalow on 2007-11-28
Made some minor updates to uBackup! 2.0 and a nice update to the installer.

If you want to update, delete the uBackup! folder and the uBackup! file you currently have and download the new uBackup!.tar.gz and Install_uBackup!.sh files from the first post in this thread.

I think most users will find the update worth downloading. :) It only took me 2 days of mad searching for the proper file to create this update. 

Special thanks to 'geirha' for showing me where the file is, so I could finally get it to work the way I wanted.

I only wish 'ericartman' wasn't having problems running this with his Kubuntu because one of his comments to me is what inspired part of this update.

---

### Post by mdpalow on 2007-11-30
Last night, I was on the phone while removing something from Synaptic. I guess I wasn't paying attention because after telling Synaptic to remove a program, I saw it was removing a LOT more than I had intended. Turns out I had to use my uBackp! to restore my whole system.

After using the 'Restore /' and 'Restore /home' options I was checking everything out to make sure my restore was good and noticed my VMware wasn't booting Windows XP.

Had me stumped until today when I rebooted and it worked fine.

Reminder: Be sure to reboot your machine after a restore if you have VMware or Virtualbox installed.

I've updated uBackup! to provide a reminder of this and will upload it soon.

---

### Post by wislon32 on 2007-11-30
Thanks.  Saved lots of time trying to work out how to use tar.  I was looking for a backup utility.  This seems to work nicely .:KS

---

### Post by mdpalow on 2007-11-30
> **wislon32 said:**
> Thanks.  Saved lots of time trying to work out how to use tar.  I was looking for a backup utility.  This seems to work nicely .:KS

You're welcome wislon32. :)

That's exactly why I wrote it. After researching, for some time, how to properly do a back-up using tar, I learned it really takes three different types of tar entries, which as you may now know are pretty involved and even complex for some. A few weeks later I certainly wouldn't have remembered the proper commands. Granted, I could have copied the code to a document and saved that, but as my requirements grew for other nice-to-have terminal commands, it only made sense to put it into a script.

Be sure to subscribe to this thread if you continue to use uBackup! as there will be some updates in the near future, which I think you'll want.

---

### Post by billgoldberg on 2007-11-30
I got this and it seems to do his work.

A quick question.

Lets say, x breaks.

How would I restore it using your program?

The back-up (first option) is saved on external hard drive.

---

### Post by mdpalow on 2007-11-30
> **billgoldberg said:**
> I got this and it seems to do his work.

A quick question.

Lets say, x breaks.

How would I restore it using your program?

The back-up (first option) is saved on external hard drive.

Good question...

Ok, as you can see there are three back-up options - 1, 2, & 3. Do them all and save to your external drive.

Now let's say you mess something up in your /home directory.

Then run "Option 5: Restore /home"

You'll be asked where the back-up for that restore option is located. 

You would enter as an example:

/media/sdb1/home_backup_11.30.2007.tgz   <where the file name matches the back-up and the date you made it>

RESTORE Options 4,5, & 6 are used in reference to BACK-UP Options 1,2, & 3.

Also, if you enter Option 9 to go to the extended menu, you'll see option 16 (version 2.0), which will give you the help file. That should be of a lot of help to you as well.

Did that help?

---

### Post by Vadi on 2007-11-30
Have you thought of making this into a .deb?

Not for the simplicity of the install (it's easy already), but so that the program can spread to over sites and such.

---

### Post by Vadi on 2007-11-30
Actually I can't get it to install :/

> vadi@vadi-laptop:~/Downloads$ ./Install_uBackup!.sh
bash: !.sh: event not found
vadi@vadi-laptop:~/Downloads$ ./"Install_uBackup!.sh"
bash: !.sh": event not found
vadi@vadi-laptop:~/Downloads$ ./"Install_uBackup!".sh
bash: !".sh: event not found


---

### Post by mdpalow on 2007-11-30
> **Vadi said:**
> Have you thought of making this into a .deb?

Not for the simplicity of the install (it's easy already), but so that the program can spread to over sites and such.

Thanks for that Vadi...

You know... uBackup! was originally started by me just to have a simple and easy to use back-up script that I could use when I needed it. I then realized that as much as I like to reinstall my system, I might want to add another option that would add all the codecs and dvd files, so I could play my movies. Then it was something else and so on. I appreciate the thought, but to be honest - I couldn't even tell you if uBackup! is liked that much by those who downloaded it. Every once in a while I get a thank you from someone who seems to like it, but unless I got a lot more favorable responses - I'll probably just offer it up to anyone that wants it through the forum.

Also, I want to make a few more upgrades in the near future to make it even easier.

Like right now I'm experimenting (already have one module working) with the idea of having it still run in terminal, but when it comes time to entering the path of where the back-up file is located, a file manager will come up and you can click and point on the file you want to restore instead of having to try and figure out where the file is actually located and then typing it in.

Also, I'm looking into making it completely GUI, but need to learn a few things on that side first. When I do all that (in the next couple weeks hopefully) AND people are telling me they like it a lot - then I would look into making it widely available if possible.

---

### Post by mdpalow on 2007-11-30
> **Vadi said:**
> Actually I can't get it to install :/

You didn't follow the instructions on the original post where you downloaded the file. :)

Try it again using my install instructions and I think it'll work for you this time.

[http://ubuntuforums.org/showthread.php?t=613462]("http://ubuntuforums.org/showthread.php?t=613462")

---

### Post by Vadi on 2007-11-30
Yep got it working.

Though, I'd like better management of what can I backup. I store a lot of stuff in my /home - games, music, that I don't want to backup...

---

### Post by mdpalow on 2007-11-30
> **Vadi said:**
> Yep got it working.

Though, I'd like better management of what can I backup. I store a lot of stuff in my /home - games, music, that I don't want to backup...

Sounds to me like you might want to create a simple cron job that could be used in conjunction with a tar back-up.

uBackup! provides you a means of restoring your computer back to original and if you have the drive space you could team the two together to give you all that you want. That's what I do by the way. It's a little overkill, but I like to have many back-up options available to me.

PM me if you like and I can help you with that easy enough if you're interested.

...

---

### Post by Nelsinius on 2007-11-30
I downloaded the two files, followed the installation instructions and performed the first 3 (backup) steps without any difficulty. This is a very simple yet effective back-up solution. I also use the Apt-OnCD utility.

---

### Post by olivero1 on 2007-12-03
Just for the record - I think that a gui would be great! We do live in a "windows" world after all :)

I would also like to suggest to anyone who is using this script to suscribe to this thread. I have missed some of the updates and it is getting better all the time!

It has actually saved me since I was playing around and made some severe changes to my system and rather than fix them again I simply performed the backup - It works GREAT!

This is a program that just WORKS! It is now on my 1st to install list for friends and family!

Keep up the great work and I would be interested in being a beta tester for you, I have a spare "toy" pc that I can do whatever I want with and I can do some real damage on it if I need too :twisted:

---

### Post by ericartman on 2007-12-03
Yowza Yowza subscribe to the thread. This program rocks!! I've been fooling around installing Mint and Ultimate and I even got a 64 bit version to work and this program save me HOURS of time getting things up to speed. Thank You mdpalow!


Cart

---

### Post by mdpalow on 2007-12-03
thanks guys for the great comments. :) Nice of you to say...

Subscribing to this thread, if you want to continue using uBackup!, is good advice by olivero1 because he's right - I have made several updates and will continue to make them. In fact, I already have a couple, but just haven't uploaded yet....

Olivero1 - I'm gonna take you up on your offer one day to beta the GUI when it comes out. It's slow starting right now, but once I get going on it, I think it'll be done in a few days.

---

### Post by megamania on 2007-12-04
> **mdpalow said:**
> Also, I'm looking into making it completely GUI, but need to learn a few things on that side first. When I do all that (in the next couple weeks hopefully) AND people are telling me they like it a lot - then I would look into making it widely available if possible.
If I can give you my advice, keep it simple. :-) That's why your program is so appreciated, in my opinion. If you start adding tons of options and a fancy gui, it will end up being a *different* program. 
There are lots of backup programs out there. I think yours is nice because it's small, quick and easily customizable.

Gianfranco

---

### Post by mips on 2007-12-04
How would one tar.bz2 /home to:
1) A external drive
2) Another physical volume on another pc
3) A samba share

The current volume is full so tarring to it is not an option, it has to be a remote destination.

---

### Post by mdpalow on 2007-12-04
you would first 'cd' to the location you want the file to be stored.

then..

```
sudo tar cvpjf your_file_name_here.bz2 /home
```

Think that would do it, but bz2 is slower and I can't imagine it will compress that much more than regularly...

It was an option I was going to make when I first started uBackup!, but decided to leave it out at the time...

Hope that helps..

---

### Post by mips on 2007-12-04
Thanks, it does help.

I might just use gz wich is faster than bz2.

---

### Post by mdpalow on 2007-12-04
> **megamania said:**
> If I can give you my advice, keep it simple. :-) That's why your program is so appreciated, in my opinion. If you start adding tons of options and a fancy gui, it will end up being a *different* program. 
There are lots of backup programs out there. I think yours is nice because it's small, quick and easily customizable.

Gianfranco

Thanks Gian...

I think you make a good point; especially where you mention customizing it. That would not be an option for most if it was made to GUI.

I am torn between your logic and Olivero1's comment as they both are very valid.

We'll see where it takes us... :)

Thanks for weighing in.

---

### Post by ericartman on 2007-12-04
My 2cents,

A GUI would make it prettier but in reality it wouldn't improve the functionality of the program, as the program is just as simple as I could imagine to use.  

Cart

---

### Post by mdpalow on 2007-12-05
Hi Everyone,

Just a quick note to let you know uBackup! 2.1 is now uploaded if you would like it.

uBackup! 2.2 will be out sometime after I make changes to the scheduled back-up option where it will create your back-up even if your computer was turned off at the time you scheduled it. That's not to say it will happen while your computer is off, it just means your computer will know if it was off when you scheduled a back-up and make it the next time it is on.

I don't know that there are any other upgrades to be made after this as I can't think of anything else to add that will make your Ubuntu experience any easier.

If anyone has any ideas that I've overlooked, please feel free to post them and I'll look into it. Basically, I'm looking for any back-up ideas or anything to install that can be automated and save you time.

bfn...

---

### Post by olivero1 on 2007-12-05
After reading some wise comments about the gui - I thought about it for a minute and asked myself - would a gui add to the programs functionality?

I beleive it would not, it would be eye candy. So I ran the program again and imagnined I never used a back up program before...

The interface is easy, understandable and simple.

So as much as a "windows" user I am I can live without a gui :)

Great job on this script and keep it up!

Let me know if I can ever be of assistance for you in the future for any projects you dream up!

---

### Post by CliveM on 2007-12-05
The attachment uBackup!.tar.gz is not there.
Have you removed it for some reason?

---

### Post by mdpalow on 2007-12-05
Hi,

Yes, I did remove it. I thought I saw a menu issue and wanted to make sure it was ok, before any 2.1 downloads occurred. Turns out it wasn't an issue, but better safe than sorry.

I'll have it up again very shortly. I just like to look everything over one last time before uploading.

thanks

---

### Post by altonbr on 2007-12-05
I just noticed in your screenshot you're using MM-DD-YYYY for you filename.

You should consider using the ISO standard of YYYY-MM-DD.

Why? (1) It's an International standard for communication between countries and languages and (2) Because files will be sorted chronologically if they're first sorted by year, month then day.

Good luck if your project. Looks excellent!

---

### Post by mdpalow on 2007-12-05
Great suggestion; thanks.

I'll make that change right now while I'm reviewing everything.

---

### Post by mdpalow on 2007-12-05
Ok, uBackup! 2.1 is loaded again to the forum

[http://ubuntuforums.org/showthread.php?t=613462]("http://ubuntuforums.org/showthread.php?t=613462")

---

### Post by olivero1 on 2007-12-05
Just used Version 2.1, still rock solid!

Thanks A MILLION!

---

### Post by maruchan on 2007-12-05
Looks pretty cool - is there a way to exclude certain folders from the backup process? I'd like to backup /home but I don't want to backup one of the folders inside that, for example.

---

### Post by mdpalow on 2007-12-05
> **maruchan said:**
> Looks pretty cool - is there a way to exclude certain folders from the backup process? I'd like to backup /home but I don't want to backup one of the folders inside that, for example.

hold that thought.... I'll be back to you with an answer in a short while.

---

### Post by mdpalow on 2007-12-05
> **maruchan said:**
> Looks pretty cool - is there a way to exclude certain folders from the backup process? I'd like to backup /home but I don't want to backup one of the folders inside that, for example.

Great question Maruchan.

Actually, your question just motivated me to do something I should have done a long time ago. I too want to exclude a certain directory from my /home back-up 'cause it's just so large and doesn't change at all. Therefore, it's one folder I could back-up on its own.

Ok, the /home back-up now has an option to exclude a directory if you like. I may make it so you can add more than one exclusion, but I don't want to get carried away with that before thinking it through first.

The update, per Maruchan's question/hidden suggestion :), is now uploaded to the forum if you would like to download it.

[http://ubuntuforums.org/showthread.php?t=613462]("http://ubuntuforums.org/showthread.php?t=613462")

Sorry if you're getting tired of downloading updates, but I am trying to make uBackup! as good as it can be and I think this is certainly an option worth having. :)

As always, you comments are welcome.

---

### Post by shanerdaner on 2007-12-05
Hi 
So when i run this and do a full backup my ubuntu stays on?  I am doing it now as I type...  Just want to make sure.  this looks sweet.

---

### Post by mdpalow on 2007-12-05
> **shanerdaner said:**
> Hi 
So when i run this and do a full backup my ubuntu stays on?  I am doing it now as I type...  Just want to make sure.  this looks sweet.

Yep! That's the beauty of Linux :)

---

### Post by CliveM on 2007-12-05
Downloaded, installed & used.
I went looking for help in getting DVDs to play using Totem Movie Player. That now runs perfectly.
You make life a lot easier for a new Ubuntu user. 
Many thanks for your work.

---

### Post by mdpalow on 2007-12-05
> **CliveM said:**
> Downloaded, installed & used.
I went looking for help in getting DVDs to play using Totem Movie Player. That now runs perfectly.
You make life a lot easier for a new Ubuntu user. 
Many thanks for your work.

Now that's always nice to hear... You're welcome.

---

### Post by shanerdaner on 2007-12-05
I was curious if you could create a preferances so that someone could backup daily to an external drive without having to cut and paste it there?  thought I would ask..  unless I just missed it.  Great program!!

---

### Post by shanerdaner on 2007-12-05
> **mdpalow said:**
> Yep! That's the beauty of Linux :)
WOW!! thanks for making this!  you are very blessed with the gift of writing such a great tool as are all of the writers of ubuntu distro.  OT:  Any good linux substitutions for Publisher????  TIA  what r the steps when doing a restore?

---

### Post by mdpalow on 2007-12-05
> **shanerdaner said:**
> I was curious if you could create a preferances so that someone could backup daily to an external drive without having to cut and paste it there?  thought I would ask..  unless I just missed it.  Great program!!

Almost did that the other day.

The concern is... how many new users will have difficulty knowing where it is they actually want it to go?

Would users know, for instance, to enter:

/media/sdb2/Backups if they wanted it to go to the second Hard Drive and in a folder called Backups. I get it perfectly, but when you make something like this for everyone, you sometimes lose some of the functionality you would like to have...

Will give it some more thought..

thanks...

---

### Post by shanerdaner on 2007-12-05
> **mdpalow said:**
> Almost did that the other day.

The concern is... how many new users will have difficulty knowing where it is they actually want it to go?

Would users know, for instance, to enter:

/media/sdb2/Backups if they wanted it to go to the second Hard Drive and in a folder called Backups. I get it perfectly, but when you make something like this for everyone, you sometimes lose some of the functionality you would like to have...

Will give it some more thought..

thanks...
I would not know but is there a way to navigate through it like in openoffice?  were u select the drive?

thanks

Shane

---

### Post by mdpalow on 2007-12-05
> **shanerdaner said:**
> I would not know but is there a way to navigate through it like in openoffice?  were u select the drive?

thanks

Shane

Yes, there is a way using something called Zenity. In fact, I already wrote the script into uBackup! the other day, but didn't like how you were in a graphical mode half the time and in terminal the other half.

My decision was also based on something I once read in the forum from someone who said if you're gonna do a terminal script then keep it terminal. In other words, don't go back and forth between the two.

Will reconsider... looking now.

EDIT: hmm, just had an idea. I guess I could leave Desktop as the default location to place the file, but allow the user to enter a different location IF they are comfortable doing that.

---

### Post by shanerdaner on 2007-12-05
> **mdpalow said:**
> Yes, there is a way using something called Zenity. In fact, I already wrote the script into uBackup! the other day, but didn't like how you were in a graphical mode half the time and in terminal the other half.

My decision was also based on something I once read in the forum from someone who said if you're gonna do a terminal script then keep it terminal. In other words, don't go back and forth between the two.

Will reconsider... looking now.

EDIT: hmm, just had an idea. I guess I could leave Desktop as the default location to place the file, but allow the user to enter a different location IF they are comfortable doing that.

Awesome once again!!...thanks!!!

---

### Post by mdpalow on 2007-12-05
Can I get some of my 'old timers' (cart, olivero1, Gianfranco, etc.), to weigh-in on the idea of having a graphical (GUI) interface pop-up and ask you where you would like the back-up placed.

Currently, files are placed on the Desktop. This change would allow you to decide where you want to place the file by using your mouse to navigate your computer.

thanks for any comments...

---

### Post by shanerdaner on 2007-12-05
> **mdpalow said:**
> Can I get some of my 'old timers' (cart, olivero1, Gianfranco, etc.), to weigh-in on the idea of having a graphical (GUI) interface pop-up and ask you where you would like the back-up placed.

Currently, files are placed on the Desktop. This change would allow you to decide where you want to place the file by using your mouse to navigate your computer.

thanks for any comments...
:lolflag:
old timers!!!!!!

---

### Post by mdpalow on 2007-12-05
Old Timers as in those who have been using uBackup! a little while now and have been active in this thread.

I couldn't possibly know how old any of them actually are... :)

---

### Post by mdpalow on 2007-12-05
shanerdaner,

Private Message me your e-mail address and I'll send you a custom uBackup! that allows you to select a destination using a graphical interface.

...

---

### Post by shanerdaner on 2007-12-05
> **mdpalow said:**
> shanerdaner,

Private Message me your e-mail address and I'll send you a custom uBackup! that allows you to select a destination using a graphical interface.

...

ok thanks sent can't wait to get yr e-mail.

---

### Post by mdpalow on 2007-12-05
> **shanerdaner said:**
> ok thanks sent can't wait to get yr e-mail.

Ok, I e-mailed you a custom uBackup! .

Tell me if that works for you....

---

### Post by shanerdaner on 2007-12-05
> **mdpalow said:**
> Ok, I e-mailed you a custom uBackup! .

Tell me if that works for you....
where is the u backup folder?

---

### Post by mdpalow on 2007-12-05
> **shanerdaner said:**
> where is the u backup folder?

should be in     /home/your_name/uBackup!

---

### Post by shanerdaner on 2007-12-05
> **mdpalow said:**
> should be in     /home/your_name/uBackup!
I am getting an error 1 sec I type it here

---

### Post by shanerdaner on 2007-12-05
There was an error creating the child process for this terminal
when I try to run the knife

---

### Post by shanerdaner on 2007-12-06
> **shanerdaner said:**
> There was an error creating the child process for this terminal
when I try to run the knife
ok how do i remove the old one?  I launched this one like the other

---

### Post by mdpalow on 2007-12-06
drop it in your trash can or right click and then select "move to trash"

---

### Post by shanerdaner on 2007-12-06
> **mdpalow said:**
> drop it in your trash can or right click and then select "move to trash"
the knife doesnt work should i delete it?

---

### Post by shanerdaner on 2007-12-06
> **shanerdaner said:**
> the knife doesnt work should i delete it?
it said it may need my pw then a box came up that said choose a dest folder then I selected it now it is backing up.  how can i get the knife 2 work?  on my desktop

---

### Post by ericartman on 2007-12-06
Call me old timer if you want, been called a  LOT worse. Pop up sounds cool. I have been sending my backups to a Samba networked file anyway. Keep up the good work sir, love the desktop icon 

Cart

---

### Post by mdpalow on 2007-12-06
> **ericartman said:**
> Call me old timer if you want, been called a  LOT worse. Pop up sounds cool. I have been sending my backups to a Samba networked file anyway. Keep up the good work sir, love the desktop icon 

Cart

You can take credit for the icon. :)

When you told me that uBackup! is like a Swiss Army Knife of Ubuntu tools, I couldn't help but use that icon.

---

### Post by shanerdaner on 2007-12-06
> **mdpalow said:**
> You can take credit for the icon. :)

When you told me that uBackup! is like a Swiss Army Knife of Ubuntu tools, I couldn't help but use that icon.

how do I remove this ?  I want to revert to the original w/o the option to pick a drive..thanks


Shane

---

### Post by shanerdaner on 2007-12-06
> **shanerdaner said:**
> how do I remove this ?  I want to revert to the original w/o the option to pick a drive..thanks


Shane

I deleted the knife on my desktop and the ubackup folder from my home is that all there is to it?

---

### Post by mdpalow on 2007-12-06
Hi Everyone,

uBackup! now has a brother with a GUI for back-up and restore functions.

Would like to know if anyone wants to beta test it for me?

Cart, Olivero1 ???

It's not a beta test in the sense of will it work; I know it works. I'm looking for someone to test out the GUI part and tell me if they like it and if it is helpful..

If so, PM me your e-mail address and I'll send it to you.

Thanks

---

### Post by megamania on 2007-12-06
> **mdpalow said:**
> Can I get some of my 'old timers' (cart, olivero1, Gianfranco, etc.),
hmmm... old timer?  :-o

Ok, this is what I'd do:
- merge the two versions into one
- place a Want_Gui flag at the beginning of the script - it's up to you whether to ship it as Want_Gui = Yes or Want_Gui = No.

Users would just have to change that flag to use the mode they prefer.

or, second option:
- on the main menu, add a menu option working as a toggle (i.e. if I press "g" it toggles the Gui on and off)

This way you'd keep things simple and clean (one version) while giving people choice.

Gianfranco

---

### Post by Amstell on 2007-12-06
great program.....i really like codec installer....nice job.

thanks

---

### Post by mdpalow on 2007-12-06
> **megamania said:**
> hmmm... old timer?  :-o

Ok, this is what I'd do:
- merge the two versions into one
- place a Want_Gui flag at the beginning of the script - it's up to you whether to ship it as Want_Gui = Yes or Want_Gui = No.

Users would just have to change that flag to use the mode they prefer.

or, second option:
- on the main menu, add a menu option working as a toggle (i.e. if I press "g" it toggles the Gui on and off)

This way you'd keep things simple and clean (one version) while giving people choice.

Gianfranco

Hey Gian...,

Not sure what you're talking about. I was asking for someone to beta test the new GUI version. Which version they prefer is not an issue since right now it's two separate versions and it can be packaged that way...

However, there is good cause to move to the GUI version because it takes a lot of headache out of the coding and is much more friendly for new users. I'll have to do some thinking on that though.

Also, the whole program is not GUI; only small parts of it. The more difficult parts like selecting a path to the file you want to restore is now GUI. This way you can't mess up the path and then have to retype it all in again. Selecting a location to put your back-ups is GUI. Selecting a folder to exclude from your /home back-up is GUI.

If you want to test/see it, please let me know...

Thanks :)

---

### Post by mdpalow on 2007-12-06
> **Amstell said:**
> great program.....i really like codec installer....nice job.

thanks

Thanks Amstell :)

---

### Post by bazanime on 2007-12-08
Is there a way to uninstall the apps that ubackup put there?   i didnt realise it would put alot of "junk" in my app list. i just wanted Flash.
Add remove only shows very few of the apps.  can you write a script that undoes what its applied.

---

### Post by mdpalow on 2007-12-08
The uBackup! option you selected:

What would you like to do?

 1: Install Programs  <-------

 2: Exit to Menu

Think that is pretty clear, but nevermind. :)

The next version of uBackup! will give you a choice of what you want to install. I'm hoping to have it done by this weekend.

I've attached a small script for you to remove the applications you didn't want.

Be sure to set the permissions to  "allow executing file as program," so you can run it.

---

### Post by toupeiro on 2007-12-08
ok, so I ditched sbackup because recently I had to rebuild my machine, and I tried to restore back to the last full and drop on the incrementals, and every single full I had was corrupt.  It (being GNUtar based) apparently has trouble with tar files in excess of 4.0GB.  The fact that they were gzipped did not help any repair procedures  I get unexpected EOF on every single full.  I simply have a lot of data.
So now I am in the hunt for a new backup restore tool.  Preferrably one using bz2 compression so I can use bzip2recover on the compressed file to attempt to repair a broken backup.

Can your tool be configured to be smart enough to split a backup into multiple archives at say .. 3gb, so I don't risk corrupting my data? 


 If so, sign me up!

---

### Post by mdpalow on 2007-12-08
> **toupeiro said:**
> ok, so I ditched sbackup because recently I had to rebuild my machine, and I tried to restore back to the last full and drop on the incrementals, and every single full I had was corrupt.  It (being GNUtar based) apparently has trouble with tar files in excess of 4.0GB.  I get unexpected EOF on every single full.  I simply have a lot of data.

Can your tool be configured to be smart enough to split a backup into multiple archives at say .. 3gb, so I don't risk corrupting my data?  If so, sign me up!

I think you might want to "sign up" as it is right now. My home_backup file is 11+ gigs (VMware w/ Windows XP and apps) and compressed down to around 5 gigs and I've used it to restore my computer probably 15 times with perfect results every time.

Run it and see if you get the EOF error message. I don't think you will with uBackup!

good luck

---

### Post by bazanime on 2007-12-08
Thank you for the lil script, but i'd like to know how many times i have to click yes or no before its actually finaly finished all it needs to do.  
Will it remove only the app ubackup installed, or will it also take out apps that were there prior to installation?  I hope for the former.

Hopefully your new app will include more clearer steps aswell, instead of the lines of text that are quite confusing to the layman eyes.  Good luck with that.

update: it stopped at something about NTP and closed itself. Is that meant to happen?  I still see the apps in my panel. should i reboot or something?

---

### Post by mdpalow on 2007-12-08
It will only remove only the apps uBackup! installed.

Have you considered that the 'confusing lines' you mention are not uBackup!'s doing, but are instead the files your system is downloading from the repositories? The "Y" and "N" prompts are being generated by aptitude - not the uBackup! program.

Did you know that any program you have installed on your computer can easily be removed using Synaptic?

For instance, if you didn't want "firestarter" (the GUI for your firewall, then do a search for "firestarter" in Synaptic and then click on it to remove.

Next time, if you want to just install the flash plugin, you can enter:

```
sudo aptitude install flashplugin-non free
```

It's all pretty simple/clear once you know a little more about what's going on. Good luck with that...

---

### Post by bazanime on 2007-12-08
I was lead to ubackup via another thread as a solution to get flash working properly in firefox. The sudo solution did not work for me and neither did the others i have come across after trawling through the forum.

I know about Synaptic and how to uninstall apps as usual in ubuntu, but i wont be asking for help if i knew what exatly was being installed like firestarter. A little clarification would be helpful so i could remove them myself.

I'm not aware of how the scripts work, i'm no programmer, just a linux new user. The lines of text i see running before it gives me the option for "yes or no" i assumed is just the app running in the usual text mode that linux users seem to enjoy. Forgive my ignorance, i'm used to the "pacifier" screens that windows apps tend to have.

I'm not stupid and I'm not blaming your app for being crap, i'm just asking for assistance and maybe pointing out some UI flaws that may help you streamline the next version.  

Ubuntu and linux are getting more popular these days via Dell, Everex and Asus, there will be many more questions from layman users that are used to windows and osx, and most wont get the whole textual thing and terminal apps.

I dont mean any offense to you work, i'm just asking questions and seeking help from the author. Its pretty simple and clear once you know whats going on, and thats what i'm trying to find out.

---

### Post by mdpalow on 2007-12-08
See - that's where you're wrong.

You seem to be under the impression you can say something like "I'm not blaming your app for being crap," and then turn around and make a stupid comment like "I dont mean any offense to you work" and think you're covered.

Hmm, after being caught robbing a bank, you tell the police "I didn't mean any offense" and they're suppose to simply forget about it, right?

Hmm, "Please don't take this as being disrespectful towards you, but I think you're an idiot." 

< that is an example only. I'm not actually calling you an idiot.>

You see, it just doesn't go over well, does it?

No one said you were "stupid," but it's obvious you're still pretty new to this. When you're new to something and ask questions - all is fine and people love to help.

However, when you're new to something and immediately start blaming the application, without knowing better (ex: it was actually aptitude giving you all those confusing lines) then you come across as being a bit offensive and also like a paying customer who may have a right to expect something.

Couldn't tell you why the flash plugin didn't work for you. uBackup! has been tested on several different computers with both 32 and 64 bit OS's and it works fine every time. There is a known issue with flash plugin for 64-bit, but that's not uBackup! - that's a flash problem. There is a work-a-round that will be included in the next version. Are you using the 64-bit version?

You said: 

> I know about Synaptic and how to uninstall apps as usual in ubuntu, but i wont be asking for help if i knew what exatly was being installed like firestarter. A little clarification would be helpful so i could remove them myself.

When you selected Option 14, there's a list (see attached pic below) of what would be installed. That didn't help?

Ok, so now I see we're not using this forum as it's meant to be used, so I suggest we do one of two things:

1. You remove uBackup! from your computer and perhaps find something you like better.

2. Private message me with any questions, concerns, or suggestions you might have and maybe I can help you.

Your call.

good luck

---

### Post by r4wr on 2007-12-08
nice:popcorn:

---

### Post by mdpalow on 2007-12-08
> **r4wr said:**
> nice:popcorn:

:lolflag:

How funny... 

When I was writing my last reply, I was thinking how someone would probably be getting a kick out of this.

Only problem is I'm trying to get uBackup! 3.0 out this weekend and this is definitely slowing me down.

..

---

### Post by bazanime on 2007-12-08
Dude i'm not blaming the application.  I may have used the wrong choice of words, but dont take that as a snipe against the app.  I'm not looking for trouble here, i just wanted assistance and since youre here to ask then i thought i'd ask.

I know youre protective of your hard work and i would too, but dont take any slightly less positive comment as a complete insult. It wasnt intended that way. I'm not actually saying it bad or crap, those words were not meant literaly. I should have said "I'm not saying your app isnt good or working...", maybe that would have gone better.

I'm not looking for something better, or saying that your app is causing me problems. I just was confused and was asking for clarification on what was happening.

Yes, i glossed over the list. I thought it was a summary or the apps being installed. Sorry, i missed that.

The flash issues with me is that only youtube works and nothing else.  Gnash seems to garble things up and flash even after installed on its own, wont work.


Sorry i'm holding you back.  Your app is great and well done. I look forward to version 3.0 <that is not sarcasm, its genuine>


p.s. i dont want to seem like the party pooper here, so i want to make myself clear to others that read that i'm not against you or your app.  i will not be the pariah.  It was all just a misunderstanding of words, and knee jerk reactions.

---

### Post by mdpalow on 2007-12-08
I'm thinking there is a problem with the Macromedia site for downloading the flash plugin. I'm getting errors connecting and also an md5sum mismatch when uBackup! connects and gets anything. I will be watching Macromedia to see if it resolves.

...

---

### Post by shanerdaner on 2007-12-08
> **mdpalow said:**
> I'm thinking there is a problem with the Macromedia site for downloading the flash plugin. I'm getting errors connecting and also an md5sum mismatch when uBackup! connects and gets anything. I will be watching Macromedia to see if it resolves.

...

i CANNOT WAIT FOR 3.0!!!!!!!!!!!!!!!!!!!!!!!!!!!  KEEP UP THE GREAT WORK!!!!!!

---

### Post by mdpalow on 2007-12-08
k, I think it's confirmed there is a bug right now with adobe and downloading the flash plugin. When the update comes out, I will test uBackup! against it and make any changes necessary to make it transparent once again.

> This causes Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). See bug 173890. This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10.


I think I need to get back to coding now or 3.0 will never get finished.

...

---

### Post by olivero1 on 2007-12-08
bazanime,

Welcome to the world of Ubuntu.

I am sorry to hear the problems you are having with Ubackup! and I am glad that you have worked out the situation that has left you upset.

May I offer you a suggestion for the future posts?

Please only state the problem and what you would like to accomplish, you will be amazed at how responsive the Ubuntu crowd is!

We now have 2 pages of information that explains that the flash plug-ins has a bug and the proper people are aware of it and will hopefully be fixed soon!

I hope that you find this application useful and I hope that you continue to use Ubuntu and ask for help. Remember - we were all noobies at one time. I still am, but I am learning more every day!

Sorry to go off topic everyone.

I am so READY for 3.0!

---

### Post by ericartman on 2007-12-08
Can't wait for 3.0 myself.  

Cart

---

### Post by mdpalow on 2007-12-10
Hi Everyone,

uBackup! 3.0 is ready for testing if you want it now.

When I say testing, I'm not implying the program has a potential for serious problems as I've checked the back-up functions and they work fine. I'm talking more about testing the GUI interface, checking grammar, spelling, etc.

I spent some time tonight working out the flash issue with adobe and have a working solution, but decided to leave it out of 3.0 because my understanding is Ubuntu should be putting an update out any day now to resolve the bug. If I don't see it come out real soon or I get requests for it, I'll put it in.

I still want to update the help file with the new interface and changes that were made, so that will come when 3.0 is put on the forum for the taking.

Some of the changes to 3.0 are:

Now you can create all three back-ups (/, /home, and Config) at one time and leave the computer until they're done.

Changed device_backup to config_backup

Now you can select which applications you want to install. That just reminded me - I still need to add one application.

Now you can delete a scheduled back-up from the GUI and have none if you change your mind.

Now you can exclude a folder from your /home back-up IF you like

Now you can specify where you want the back-ups to be placed (networked drives as well)

Now you don't have to type the path to a back-up file anymore if you need/want to restore - file manager will allow you to select w/ mouse

See attached pics below.

If interested in testing it and providing input, please Private Message me with your e-mail address and I'll send it to you.

thanks

---

### Post by altonbr on 2007-12-10
I'm a little worried that this is starting to look like Automatix ([http://getautomatix.com/](http://getautomatix.com/)) with the program installs, now that it does more than just backups.

I DO NOT want to hinder progress of this piece of software, but I would like to hear it's goals!

Keep up the good work!

---

### Post by mdpalow on 2007-12-10
> **altonbr said:**
> I'm a little worried that this is starting to look like Automatix ([http://getautomatix.com/](http://getautomatix.com/)) with the program installs, now that it does more than just backups.

I DO NOT want to hinder progress of this piece of software, but I would like to hear it's goals!

Keep up the good work!

The goals are simple.

To provide me a tool that:

1. Helps me automate my back-up/restore or clean install

2. Helps a friend to automate his backup/restore or clean install

3. Help someone else IF they want my program.

Why does it 'worry' you if it looks like another program?

I probably should change the name from uBackup! to something else since it does more now, but I haven't - yet.

---

### Post by bw44 on 2007-12-10
> **frodon said:**
> I always found tar commands too long for this kind of stuff, [partimage]("http://www.partimage.org/Main_Page") is for example way faster than this kind of solutions and i recommend it first as it is full featured, stable and reliable backup tool with an intuitive GUI.
As a comparison it takes me 10mins to backup my 6.4Go ubuntu partition (with normal compression) and 5 minutes to restore it.

This is a nice home made script to create backups but it is still less convenient than a solution like partimage which is a reference.

Following your suggestion,  I tried out partimage and it's certainly a good tool (though it took me longer than 10 minutes, including the time to burn the images to CD).

One limitation of partimage is that it's only good for restoring to the same partition size and location, isn't it?

Couldn't  uBackup be used to restore stuff to a copy of Ubuntu installed to a different partition? This would be helpful  if you were moving your system  to a new computer, for example.

---

### Post by mdpalow on 2007-12-10
> **bw44 said:**
> Following your suggestion,  I tried out partimage and it's certainly a good tool (though it took me longer than 10 minutes, including the time to burn the images to CD).

One limitation of partimage is that it's only good for restoring to the same partition size and location, isn't it?

Couldn't  uBackup be used to restore stuff to a copy of Ubuntu installed to a different partition? This would be helpful  if you were moving your system  to a new computer, for example.

Yep, sure could. However, you might not want to restore the third and final file (config_backup_yyyy.mm.dd.tgz) as the xorg.conf and fstab would most likely not work on a different computer. However (again), you wouldn't need to 'cause a new installation on a different partition would already have a working fstab and xorg.conf file. At that point, what I would do if I wanted some unique xorg.conf (video/monitor) settings on the new computer is.... extract the xorg.conf file from the first computer to the desktop by itself and then pull out any unique stuff and enter it into the new xorg.conf file in/on the other computer/partition. 

Just to be clear and because I've actually done this already...  If you had a dual monitor setup in the original xorg.conf file and wanted the dual monitor setup on the new computer, you could simply copy out that part and put it in the xorg.config of the second computer. The only limitation would be if the second monitor didn't support the resolution/refresh rate of the first monitor. But, since setting up dual monitor is relatively simple, it might just be a better solution to do it on the 2nd computer from scratch. Bottom line - restoring all but config_backup should do the trick. :)

Make sense? :)

---

### Post by bw44 on 2007-12-10
Thanks for the clarification on not restoring the config_backup if moving to a different computer. Makes sense!  I hadn't thought about the problems of the xorg.conf file settings, but as you say, these would best be done manually.

---

### Post by mdpalow on 2007-12-10
> **bw44 said:**
> Thanks for the clarification on not restoring the config_backup if moving to a different computer. Makes sense!  I hadn't thought about the problems of the xorg.conf file settings, but as you say, these would best be done manually.

That's the EXACT reason I programmed uBackup! to back-up the config files separately.

If they were included with the the other back-up files, as many programs do, you would have serious problems after you restored the files to another computer OR even if you upgraded your computer with say... an additional hard drive or different video card and then performed a restore.

See... I did think through a lot of this stuff before actually writing the program... :)

take care..

---

### Post by mdpalow on 2007-12-10
Ok, 3.0 has been sent to several people for beta testing and I've gotten a couple great reviews, but I'll wait for a few more responses.

I've updated the help file and even decided to go ahead and code the flash plugin fix for 32 and 64-bit users. So, if you have Ubuntu 64, this should do it for you too. I figured it was harder to get the code in than take it out and since right now flash seems to be driving a lot of people crazy, I went ahead and added it.

The flash thing is confusing 'cause I see people saying it doesn't work with 64-bit OS's, but then others say it works out of the box. I don't know since I'm using 32-bit. If I find it's not necessary, I'll just take it out and redo the Main menu.

Once again, if you'd like to help beta test uBackup! 3.0, please PM with your e-mail address and I'll send it to you.

I'll be posting the files to the forum soon...

thanks...

---

### Post by evilc on 2007-12-10
This is nice and simple to use, ideal for all new users of linux. Keep up the good work, definitely easiest backup prog.

---

### Post by frodon on 2007-12-11
> **bw44 said:**
> One limitation of partimage is that it's only good for restoring to the same partition size and location, isn't it?No, there's not such limitation as far as i know, it's not an image like if you use a dd command (if i well understood) so you can restore it where you want, including on another partition. It is in general the first purpose of all image backup tools.

---

### Post by bw44 on 2007-12-11
> **frodon said:**
> No, there's not such limitation as far as i know, it's not an image like if you use a dd command (if i well understood) so you can restore it where you want, including on another partition. It is in general the first purpose of all image backup tools.

You may be right, but I got my impression from a comment on the partimage site [http://www.partimage.org/Partimage-manual_Usage:](http://www.partimage.org/Partimage-manual_Usage:)

> The partition to restore must have the same size as the saved partition. If the partition is smaller than the original one, the operation will fail. If it is bigger, space can be lost. You can read the FAQ of this handbook, for more details about this.
It would be a good idea to check the author's FAQ at [http://www.partimage.org/Partimage-FAQ](http://www.partimage.org/Partimage-FAQ) before relying on partimage to move/resize partitions.

But it's still a good tool - glad you brought it to my attention!

---

### Post by frodon on 2007-12-11
I'm scared you're right on this, i wasn't aware of this annoying limitation.

At my home i use norton ghost, i know it's a windows software but i have it for several years now and i found really convenient to backup my linux partition from another OS. Obviously the drawback is that it's a proprietary apps and not free.

---

### Post by bw44 on 2007-12-11
> **frodon said:**
> I'm scared you're right on this, i wasn't aware of this annoying limitation.

At my home i use norton ghost, i know it's a windows software but i have it for several years now and i found really convenient to backup my linux partition from another OS. Obviously the drawback is that it's a proprietary apps and not free.

I've heard ghost is great.  Too bad about partimage, but like the author said, maybe he or she will get around to including the move/resize function someday.

Cheers.

---

### Post by mdpalow on 2007-12-12
Just some news for anyone following this thread...

uBackup! 3.0 has a new name; it's now QuickStart 3.0

I think anyone familiar with what it does will know why that makes sense.

I'm hesitant to put it out just yet because of one option that allows Ubuntu 64-bit users to fix their flash problems. I've got it coded, but since I don't run 64-bit, I can't test it out.

I must admit, there seem to be a million! different solutions to fixing this problem and based on what I've read, I attempted to code the fix based on the best input I was able to find. I was able to test the function (code) on a 32-bit file and it worked, so I believe the code is right, but I don't actually know if the .deb file will work since I can't actually test it. If I were to guess on the probability of it working, I would give it a 80+% chance of success.

If anyone is a 64-bit user and their flash isn't working currently, then giving this a try wouldn't hurt. Please PM me your e-mail address if you fall into this category and would like to give it a shot.

I found some menu'ing issues just now, which I have fixed, so for those of you currently beta testing - clicking cancel in the SCHEDULED BACK-UP portion is now working properly.

Lastly, I recently thought of an issue that might warrant some further thought. Currently, 'QuickStart' creates your back-ups with a default name (example: system_backup_yyyy.mm.dd.tgz). Have any of you ever wanted to add some unique text to this name (example: system_backup_yyyy.mm.dd_64bit_experiment.tgz) to make it easier to know what a particular back-is unique for when you made it? I mean since we've switched from having to type in the path/file name, it really shouldn't matter how long it becomes, right?

thanks...

P.S. Now would be a really good time for a wish list if you think of something QuickStart should be able to do. Just remember, whatever it is should be something that is beneficial to the majority and not just something you would like.

---

### Post by altonbr on 2007-12-12
Wow. Keep up the good work! Can't wait until it's packaged by MOTU!

---

### Post by shanerdaner on 2007-12-12
this is the best BuU by far keep up the super work!!

---

### Post by mdpalow on 2007-12-12
Thanks Shanerdaner...

Ok, for everyone else.....

good news and some good news

Got word from a 64-bit user that QuickStart solved his Flash problem on first go around, so that's good news

and

I think QuickStart 3.0 is ready to go out if anyone wants it.

For those beta testers, please rid yourself of your copy and use this new one as it's much better...

I'm gonna try and package it up tonight and put it on the forum. If not tonight, it'll be on tomorrow.

bfn...

P.S.

thanks to olivero1, bw44, cart, shane, and anyone else I might have overlooked for taking a look at QuickStart and beta testing it.

---

### Post by shanerdaner on 2007-12-13
> **mdpalow said:**
> Thanks Shanerdaner...

Ok, for everyone else.....

good news and some good news

Got word from a 64-bit user that QuickStart solved his Flash problem on first go around, so that's good news

and

I think QuickStart 3.0 is ready to go out if anyone wants it.

For those beta testers, please rid yourself of your copy and use this new one as it's much better...

I'm gonna try and package it up tonight and put it on the forum. If not tonight, it'll be on tomorrow.

bfn...

P.S.

thanks to olivero1, bw44, cart, shane, and anyone else I might have overlooked for taking a look at QuickStart and beta testing it.

no problem love helping out!!

---

### Post by olivero1 on 2007-12-13
> **mdpalow said:**
> thanks to olivero1, bw44, cart, shane, and anyone else I might have overlooked for taking a look at QuickStart and beta testing it.

Glad to be of help! Keep up the good work!

---

### Post by mdpalow on 2007-12-13
Added some updates.

They're worth downloading QuickStart again.

Found a couple Menu errors where it didn't exit properly when 'Cancel' was selected; you had to click it twice. 

Added a few pop-up windows, so you know when some tasks are complete. 

Made some cosmetic changes; nothing major.

Won't be up'ing the version number for these minor changes.

Thanks...

---

### Post by bw44 on 2007-12-13
Just downloaded QuickStart 3.0 -- the E(mergency) R(escue) feature is great addition.
Many thanks!

---

### Post by toupeiro on 2007-12-13
> **mdpalow said:**
> Added some updates.

They're worth downloading QuickStart again.

Found a couple Menu errors where it didn't exit properly when 'Cancel' was selected; you had to click it twice. 

Added a few pop-up windows, so you know when some tasks are complete. 

Made some cosmetic changes; nothing major.

Won't be up'ing the version number for these minor changes.

Thanks...

Another recommendation:

setup a paypal for donations.  Your turnaround to feedback on this solution is ouutstanding.  You should give people benefitting from your work and like to contribute to independent development like this another way to show their appreciation and keep the good updates flowing back.

---

### Post by shanerdaner on 2007-12-13
> **toupeiro said:**
> Another recommendation:

setup a paypal for donations.  Your turnaround to feedback on this solution is ouutstanding.  You should give people benefitting from your work and like to contribute to independent development like this another way to show their appreciation and keep the good updates flowing back.

I AGREE!!!

---

### Post by mdpalow on 2007-12-13
LOL :)

If I thought more than a few people would actually make a small donation I might actually consider it. :)

Thanks guys... Very nice of you to say.

---

### Post by mdpalow on 2007-12-14
Hi Everyone,

I actually found a real bug in QuickStart tonight. Apparently, option 5 (Create a Custom Back-up) not only didn't work as it was intended, but the exiting for it was not working properly.

Anyway, the good news is... for everyone that has to download the update, you not only get a fix, but you get an upgrade along with it. :)

Now, instead of only being able to select one folder to back-up, you can select as many as you like for a truly customizable back-up.

fix/upgrade has already been uploaded. 

Enjoy...

---

### Post by bw44 on 2007-12-14
Sorry I didn't catch that problem -- I thought I had tested Option 5.  Being able to select multiple folders to back up is a good enhancement (I did notice that limitation, but didn't want to delay the release of 3.0 by requesting it!)

Cheers.

---

### Post by mdpalow on 2007-12-14
Hi Everyone,

Ok, without a doubt I think you all are going to like this.

After the last update, I realized these updates/upgrades are coming out often and causing everyone to have to continuously go to the site and reinstall.

So, what I did was upgraded QuickStart to have it's own, built-in update feature. It's now option 15 at the bottom. Just click it and QuickStart will go out and update itself for you. Nothing for you to have to do anymore. ;)

Go to the forum and download latest upgrade/update with this feature and it'll be the last time you have to do it.

Enjoy... 

P.S. Look at option 15 on the attached pic

---

### Post by bw44 on 2007-12-14
Hey, don't make it too easy ! ;)

---

### Post by mdpalow on 2007-12-14
New Updates for QuickStart...

Thanks to Olivero1 for his suggestion to create a wiki for the help file. I originally decided I wasn't going to use it, but after last night's update allowing you to auto-update, I decided to use the Wiki space for more than just the program updates.

Now the help file is also located on/in the Wiki, which you will be taken to when clicking on Option 14 for help. I will give access to Olivero1, if he's still interested in updating the help file, and a few others who might be interested in being a part of QuickStart.

Please select Option 15 and update to get the latest updates, which include the Wiki addition and more cosmetic changes.

The cosmetic changes will be coming frequently as there's a lot to change when going from terminal to GUI. I'm doing a little bit daily until it gets to where it needs to be, so please keep an eye on this thread for notification of updates.

Take care...

---

### Post by altonbr on 2007-12-14
You should make your own PPA in Launchpad for this so users don't have to update manually or via your new script :)

---

### Post by mdpalow on 2007-12-14
> **altonbr said:**
> You should make your own PPA in Launchpad for this so users don't have to update manually or via your new script :)

That's a great idea, but can you PM me some details/instructions/anything? Not up to speed on this...

Will be gone for the next hour, so if you respond - my reply will have to wait until then. :)

Thanks altonbr

---

### Post by altonbr on 2007-12-14
Posted here and PMed:

**Launchpad PPA Service**
Announcement: [http://www.ubuntu.com/news/launchpad-ppa](http://www.ubuntu.com/news/launchpad-ppa)
PPA list: [https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)
HOWTO: [https://help.launchpad.net/PPAQuickStart](https://help.launchpad.net/PPAQuickStart)

**Example repository I use for Pidgin:**
> deb [http://ppa.launchpad.net/bruce89/ubuntu](http://ppa.launchpad.net/bruce89/ubuntu) gutsy main

**MOTU**
Then, once you have the PPA setup and have reviews that everything is working great, I would get into contact with MOTU via '#ubuntu-motu' on 'irc.freenode.net'.

I'm not a software developer, but I know these are solid steps to follow.

**Website**
Then you can come to me if you need a website :)

---

### Post by chipwich on 2007-12-15
Wanted to add my thanks here for this very useful utility.  New to ubuntu, but got it installed and working perfectly.  Two thumbs up.

---

### Post by mdpalow on 2007-12-15
> **chipwich said:**
> Wanted to add my thanks here for this very useful utility.  New to ubuntu, but got it installed and working perfectly.  Two thumbs up.

Thanks Chipwich... glad it was able to help. :)

---

### Post by luckyrog on 2007-12-15
Nice one mdpalow!  Works like a charm - thank you. :)

---

### Post by mdpalow on 2007-12-16
> **luckyrog said:**
> Nice one mdpalow!  Works like a charm - thank you. :)

Thanks very much Luckyrog..

There's an update out there if you/anyone wants to select Option 15 to update your QuickStart...

---

### Post by davidwfox on 2007-12-16
It's rare that I work through 19 pages of postings but on this occasion I've done it and, apart from the inevitable knocker 80% of the way through, I'm seriously impressed. Mdpalow, you're a shining example of what makes Linux in general such an enjoyable computing experience for those of us who wish to do just a little more than simply running apps. Mind you, your obvious expertise turns me green with envy, but so be it ....

I do need your guidance however. I followed your instructions, to the point of having created the Swiss knife on the desktop. Clicking it, instead of bringing up the programme, brings up a blank terminal window with an error pop-up advising:
"There was an error creating the child process for this terminal"
Clicking OK leaves me with a blank terminal window.
What have I stuffed up??

---

### Post by mdpalow on 2007-12-16
Thanks for your comments davidwfox..

Let's see if we can figure this out...

Did you just download the two files from the first and original post?

What are you running?   Ubuntu 7.10?

thanks...


EDIT: Just ran a test on the original files in first post and all seems to be in order and the install works for me.

---

### Post by davidwfox on 2007-12-16
Yes to both questions

---

### Post by mdpalow on 2007-12-16
K, let's troubleshoot this through Private Message, so we don't send a dozen posts to anyone subscribes to this thread. 

Will send you a PM now...

---

### Post by Myglaren on 2007-12-16
Thanks for that, I started to try and install pitfdll.-0.8.2 and it got a bit too complex a bit too fast.  Your little widget worked perfectly and simply.  Great stuff.

I also have to add that the screen image is now exceptionaly superior to my Toshiba laptop that in theory should be better than this machine but - isn't!
It *is* running Vista currently though, so perhaps I shouldn't gripe too much.

---

### Post by Techwiz on 2007-12-16
I like it! I have been looking for a backup solution. Yours seems to work great! Just wondering if there's any way I can add the quickstart launcher to my mail menu with it's icon?

---

### Post by SonicSteve on 2007-12-16
> **mdpalow said:**
> Hi Everyone,          ------------------------------------------------------ [COLOR="Red"]QuickStart 3.0 (uploaded 14 Dec 2007)[/COLOR]

If you're interested in having this - I've written a menu-driven script called QuickStart that will allow you to:

[COLOR="Red"]1. Auto Install proper DVD & Codecs Files so you can Play a DVD in your drive using totem, etc. (works with 7.10 / 7.04 and 32-bit / 64-bit).

2. Auto Install Some Common Applications (aMSN, aMSN fix, Flash, Firestarter, Java, AllTray, and a few others) 

[SIZE="4"]**3. Automatically fixes Flash problems for 32/64-bit systems until fix comes out**[/SIZE].[/COLOR]



.

What exactly does it fix? What are referring to. I have a few glitches with flash on certain sites such as MLB.com NBA.com and a few others. Some of the flash menus don't display quite right. Is this the kind of "fix" you're talking about or...

---

### Post by mdpalow on 2007-12-16
wow! That's big... :)

Maybe I should re-write the original post. :)

The first "fix" refers to installing flash so it works. Right now, if you try to install Flash with synaptic or command line you'll get an error (read the terminal to see error).

The second "fix" refers to the update that has already been made for Ubuntu 8.04, but hasn't been sent to us to update our 7.10.

I went to MLB.com and watched a video and it worked well for me; sound included.

---

### Post by SonicSteve on 2007-12-16
> **mdpalow said:**
> wow! That's big... :)

Maybe I should re-write the original post. :)

The first "fix" refers to installing flash so it works. Right now, if you try to install Flash with synaptic or command line you'll get an error (read the terminal to see error).

The second "fix" refers to the update that has already been made for Ubuntu 8.04, but hasn't been sent to us to update our 7.10.

I went to MLB.com and watched a video and it worked well for me; sound included.

It was a bit big wasn't it? I should have previewed the post first:redface:
I set it to 4 instead of 5, it's not quite so obnoxious now. :)

---

### Post by mdpalow on 2007-12-16
I changed some wording on the original post and hope it's a bit more clear...

---

### Post by SonicSteve on 2007-12-16
One more question for now, :)
Will this work well with 7.04?

---

### Post by mdpalow on 2007-12-16
> **SonicSteve said:**
> One more question for now, :)
Will this work well with 7.04?

I haven't been able to test it on 7.04 because I don't have it. 

However, the concept of the fix should work on any Ubuntu OS since it's not actually OS specific, but 'Firefox' specific instead.

---

### Post by SonicSteve on 2007-12-16
I'll guinea pig it for you on my server, if flash breaks it won't matter since I don't use it for that anyway.

Edit****
The setup seemed to work well but...
When running the QuickStart file on the desktop I first had to edit the permissions tab to include "allow executing file as a program"
Then when it runs it says this;
"There was an error creating the child process for this terminal"

I don't know if you want to try and tackle this or not. If I'm missing something simple let me know.

---

### Post by mdpalow on 2007-12-16
> **SonicSteve said:**
> One more question for now, :)
Will this work well with 7.04?

Another thought... the fix QuickStart will make for this existing problem is not going to cause anything crazy to happen, so even if it didn't work, it's not like you're going to have a corrupted system and it's not going to boot. QuickStart is simply going to download the Flash plugin, untar it for you, strip a file from the download and put it in a firefox folder for you.

---

### Post by SonicSteve on 2007-12-16
The setup seemed to work well but...
When running the QuickStart file on the desktop I first had to edit the permissions tab to include "allow executing file as a program"
Then when it runs it says this;
"There was an error creating the child process for this terminal

EDIT***
I looked at the launcher and it was calling from /my home folder/QuickStart/QuickStart 
However there is nothing inside the QuickStart folder (it's empty) perhaps the setup didn't go so well?

---

### Post by Dragon43 on 2007-12-16
Just got through downloading and installing.
Elegant work **mdpalow**, thanks.....Will work with it soon, still getting 7.10 all organized.

Make more stuff to make it easy for us.... :D

---

### Post by mdpalow on 2007-12-16
> **SonicSteve said:**
> The setup seemed to work well but...
When running the QuickStart file on the desktop I first had to edit the permissions tab to include "allow executing file as a program"
Then when it runs it says this;
"There was an error creating the child process for this terminal

EDIT***
I looked at the launcher and it was calling from /my home folder/QuickStart/QuickStart 
However there is nothing inside the QuickStart folder (it's empty) perhaps the setup didn't go so well?

You're the 2nd person in two days with this problem. :(

I've just tested the download AGAIN and it works. I sent you a PM.. please read, so we can figure out what's going on with your system.

Another person downloaded QuickStart right after you and it worked for them, so I'm trying to look and see what the differences might be.

---

### Post by mdpalow on 2007-12-16
> **SonicSteve said:**
> The setup seemed to work well but...
When running the QuickStart file on the desktop I first had to edit the permissions tab to include "allow executing file as a program"
Then when it runs it says this;
"There was an error creating the child process for this terminal

EDIT***
I looked at the launcher and it was calling from /my home folder/QuickStart/QuickStart 
However there is nothing inside the QuickStart folder (it's empty) perhaps the setup didn't go so well?

After looking at your post again, I see that you posted '  /my home folder/QuickStart/QuickStart '   Just out of curiosity, do you have a path to your Documents folder (for example) that looks like '   /home/steve/Documents ' or is it something else? I'm assuming 'steve' is your logon name.

If not, can you post your path to the 'Documents' folder, so I can see what the path looks like?

Thanks...

---

### Post by CanonKen on 2007-12-16
I downloaded this about an hour ago and have tried it out and there was no problem at all for me, excellent work, much better than the rest I have tried, finally found the back-up program I was after.

Cheers

Edit - Can I now delete the 2 files I downloaded?

---

### Post by SonicSteve on 2007-12-16
OK then,
I didn't realize that I needed to download both files in the original post. I thought one was the program that I needed to compile (the tar.gz file) and the other an auto installer script. 
I was wrong.
[B]
Once I downloaded _both files_ onto my desktop[/B], and re-ran the setup it worked perfectly.
I ran the flash installer for 32bit OS's
 I then tested the [www.xbox.com](www.xbox.com) and the flash on the home page worked perfectly.

[B][SIZE="3"]Thanks mdpalow for your help. I'll get around to testing the other features of the QuickStart program and post the results as I do. 
[/SIZE][/B]
The only issue I saw was that the installer was caught in a loop, it would install correctly then try to install again. Once I ended the loop the program ran the way it was supposed to.

Just for the record of those who haven't read the entire thread I'm running 7.04.

---

### Post by mdpalow on 2007-12-16
SonicSteve

Glad we were able to fix the problem.

After speaking with you, I feel pretty confident the other person with the same problem also didn't download the 'QuickStart.tar.gz' file.

I updated the original post with a large, red reminder to download both files, so hopefully this recurring problem won't happen again. :)

by the way -  I added an Exit command to the installer, which shouldn't be required. Now it should not loop under any circumstances.

thanks very much...

---

### Post by mdpalow on 2007-12-17
> **CanonKen said:**
> I downloaded this about an hour ago and have tried it out and there was no problem at all for me, excellent work, much better than the rest I have tried, finally found the back-up program I was after.

Cheers

Edit - Can I now delete the 2 files I downloaded?

Thanks CanonKen :)  

yes, you can delete original downloaded files (Install_QuickStart.sh and QuickStart.tar.gz).

Sorry for late reply.. just saw this..

---

### Post by mdpalow on 2007-12-17
I recently had a suggestion made to me, which makes the 2nd time this has been brought up.

The suggestion was to allow for a back-up that did not use Tar, but instead was a direct copy of files and folders to another drive.

A while back, I had originally thought to add this to uBackup! (now QuickStart 3.0), but I never did because I wasn't sure if a lot of people had second hard drives. I've been doing it personally on my machine since the beginning, so I know the value of it. After the second request and thinking it through, I think there might be more people with 2nd hard drives then not.

For those without a second Hard Drive, they can always copy the folders to another partition on their one Hard Drive (if they've created one) or even create another folder within their /home directory and put the back-up there. I guess the options plentiful. 

I actually started on this last night and have half of it working now.

This will become a new option that will allow you to select folder(s) you want backed up, select a location to copy these folders to, and then select a time-frame for checking the original folder(s) against the copy and update IF there is a change. This is not a tar.gz file, but a straight 1:1 copy of the folder(s) IF a change is recognized between the two.

I have 6 folders updated every hour if the script sees a change was made in the original.

Thanks SonicSteve for the suggestion...

---

### Post by ntu on 2007-12-17
> **mdpalow said:**
> I recently had a suggestion made to me, which makes the 2nd time this has been brought up.

The suggestion was to allow for a back-up that did not use Tar, but instead was a direct copy of files and folders to another drive.

A while back, I had originally thought to add this to uBackup! (now QuickStart 3.0), but I never did because I wasn't sure if a lot of people had second hard drives. I've been doing it personally on my machine since the beginning, so I know the value of it. After the second request and thinking it through, I think there might be more people with 2nd hard drives then not.

For those without a second Hard Drive, they can always copy the folders to another partition on their one Hard Drive (if they've created one) or even create another folder within their /home directory and put the back-up there. I guess the options plentiful. 

I actually started on this last night and have half of it working now.

This will become a new option that will allow you to select folder(s) you want backed up, select a location to copy these folders to, and then select a time-frame for checking the original folder(s) against the copy and update IF there is a change. This is not a tar.gz file, but a straight 1:1 copy of the folder(s) IF a change is recognized between the two.

I have 6 folders updated every hour if the script sees a change was made in the original.

Thanks SonicSteve for the suggestion...

This sounds an option I would prefer - aren't some people difficult. With the present Quickstart I am unsure in what situations I would restore what backup folder. I would prefer to clone the whole Ubuntu hdd to another one (and update this on demand if possible) and then restore the whole lot back to the original hdd if something goes wrong.

I am rather an oldtimer and simplicity is the key here. 

Many thanks for what you have done mdp.

---

### Post by mdpalow on 2007-12-17
An interesting suggestion NTU.

In a sense you are cloning the hard drive to three back-up files. The only reason for three files as opposed to one is for reliability and saving time.

All you really have to know/remember is:

1. If you're editing your xorg.conf or fstab file and something goes wrong, you only have to restore config_backup_yyyy.mm.dd.tar.tgz

Most people would probably edit these files early on when setting up Ubuntu and then leave them alone. So, if you edit these files and something goes wrong, you know what to restore. Even later if you're editing these files and something goes wrong (you should know immediately or at the next boot-up), you'll know what the problem is.

2. If you haven't been editing the xorg.conf or fstab file and something goes wrong, you'll probably want to start with the restoring system_backup_yyyy.mm.dd.tar.tgz and reboot and see if all is good. If not, then move on to the home_backup_yyyy.mm.dd.tar.tgz file and you'll be surely fine then.

You or someone else reading this might be thinking if something goes wrong and you haven't backed up your /home folders in a while then what.

In about another hour or so, I'm about to upload the latest update to QuickStart that will allow you to synchronize folders you select to another hard drive hourly, daily, or weekly. So now, you can back-up your most treasured folders automatically and have a better restore solution. This will not be compressed Tar back-up, but instead a 1:1 initial copy and then based on your schedule, the folders you selected will be updated to match the original folders if a change is recognized. An example of the folders I use this option with are:

/home/me/

Documents
Photos
aMSN_Received_Files
vmware
Backups
QuickStart
.evolution (for my e-mail)
.mozilla (for my bookmarks and plugins)
.vmware (for my preferences file)

For me (I did this manually months ago), these folders are updated every hour if a change has been made to the original.  

Note: Updating every HOUR might not be the best option for everyone. Recommend you give your schedule some consideration and then select what is best for you. A Daily or Weekly might be preferable for most.

---

### Post by ntu on 2007-12-17
Thank you very much for this information mdp. This provides me with clear 'flow diagram' of what to do when/if something goes wrong.

---

### Post by mdpalow on 2007-12-18
Hi Everyone,

Please update to QuickStart 4.0

New option to synchronize and back-up selected folders (Option 7).

Several menu exiting fixes.

This is a highly encouraged update...

Enjoy..

---

### Post by Espreon on 2007-12-18
Interesting... I shall give it a go...

---

### Post by lenn-art on 2007-12-18
Wow ..! Thanks, +1 for this app!

 - edit:
i've problems to start the program from my bar. It's just starting with the commad "/home/lenn-art/QuickStart/QuickStart" but does not open a terminal? When i check the box 'run in terminal' i got only a terminal and nothing happens :(
 - edit2:
SOLVED: the commando should be > "/home/lenn-art/QuickStart/QuickStart" ./QuickStart and the terminal box should be checked on.

---

### Post by jamaas on 2007-12-18
Thanks, if we have not installed the previous version, is there somewhere we can go and download the most recent version, i.e. 4.0? Relative noob/intermediate here, thanks for all your hard work.

Jim


QUOTE=mdpalow;3971862]Hi Everyone,

Please update to QuickStart 4.0

New option to synchronize and back-up selected folders (Option 7).

Several menu exiting fixes.

This is a highly encouraged update...

Enjoy..[/QUOTE]

---

### Post by mdpalow on 2007-12-18
> **jamaas said:**
> Thanks, if we have not installed the previous version, is there somewhere we can go and download the most recent version, i.e. 4.0? Relative noob/intermediate here, thanks for all your hard work.

Jim


QUOTE=mdpalow;3971862]Hi Everyone,

Please update to QuickStart 4.0

New option to synchronize and back-up selected folders (Option 7).

Several menu exiting fixes.

This is a highly encouraged update...

Enjoy..[/QUOTE]

If you look at the bottom of QuickStart 3.0, you'll see Option 15. That's the update option. - just click that and press OK and it'll update on its own.

If you downloaded QuickStart from the original post just now, you already have QuickStart 4.0 and no further updates are available right now.

Did I answer your question?

Thanks :)

---

### Post by mdpalow on 2007-12-18
> **lenn-art said:**
> Wow ..! Thanks, +1 for this app!

 - edit:
i've problems to start the program from my bar. It's just starting with the commad "/home/lenn-art/QuickStart/QuickStart" but does not open a terminal? When i check the box 'run in terminal' i got only a terminal and nothing happens :(
 - edit2:
SOLVED: the commando should be  and the terminal box should be checked on.

Interesting... :)

I never even thought to do that. I just now dragged the QuickStart ICON from my desktop to my panel and it placed an icon there. When I clicked it, QuickStart loaded fine. I didn't have to do anything.

If you put it in your menu, you do have to select the option to run it in terminal.

---

### Post by mdpalow on 2007-12-18
Hi Everyone/Anyone,

I need some help making a decision.

Currently, QuickStart 4.0 will synchronize selected folders from the OS to a back-up drive or partition. As we may know by now, this can happen each hour, once a day, or once a week - depending on which schedule you select.

When the folders are synch'd, it simply looks for changes in the original folder compared to the synch'd folder and if there's a change then it copies the changed files over. This has the effect of overwriting your back-up file with the newly changed one.

However, I was considering changing the code to cause your synch'd files to have a '1up' name and give you the ability to save revisions of a file. Meaning, you write an important document (ex: important_document.doc) and it gets synch'd. Then you edit the document and instead of just overwriting it, it creates a document named 'important_document.doc ~1~'. The next time you edit said document and sync, it creates 'important_document.doc ~2~' and so on.

The dilemma is... Example: You have VMware installed so you can run Windows XP along with some must have programs. Regardless of whether you created a straight 8gig virtual drive or are allowing the virtual drive to expand as you add more windows programs, the XP virtual drive will at least be a few gigs in size. Now if you were to add a program after synch'ing -- the newly sync'd folders is now going to add this very large file as a revision. In essence, you now have, for example, - two, 3 gig files in the VMware folder; the original and the revision.

Granted:

1. You could not select a folder with such large files for sync'ing.

2. You could go into the sync'd folder and view hidden files and delete the one you don't need anymore.

3. You could go into the script, which QuickStart creates and remove the added code and remove this revision feature from that particular folder and then it would simply overwrite each time.

Personally, I'm thinking it might be a good option to add this revision feature and since sync'ing VMware doesn't work for some reason to begin with it wouldn't be an issue. The VMware example was just to give you an idea of what I meant when dealing with large files and the impact it might have. :)

Ok, so there's the dilemma. Do we add a '1up' revision capability, so we don't overwrite our files and then later find out the update we made was completely wrong, but now we can't get our previous work back and have to start over....

OR

Leave it out... ??

If your vote is to leave it out then please tell me why we shouldn't create revisions of our sync'd files.

thanks...

---

### Post by mdpalow on 2007-12-18
Please update your QuickStart.

When you schedule a back-up and/or synchronize folders, QuickStart will create a folder called 'Cron' in your home directory. If/when you delete a schedule, QuickStart will check for a script file it would have created for either option and if it doesn't see one or the other - it deletes the 'Cron' folder.

However, I was considering the possibility that you might, for some reason, have create a 'Cron' folder for something else you're doing and didn't want QuickStart to delete the folder just because it doesn't see any of its own files. I therefore changed the code to check for any other files that might exist first and if it's empty, then it can remove the folder it created.

Safety first.... :)

---

### Post by Greasyfingers on 2007-12-18
Thanks for this, mdpalow. I got uBackup! v 2.1 and see that you have since made great progress with it. It's not only a nice piece of kit, but it's great for beginners like me to work through the code and see just how a script all fits together.

One questions (I expect there'll be more) - I have a twin HDD setup, and I like the synchronize feature, but cp doesn't seem capable of deleting stuff on the backup which no longer exists on the source folder. Is this right? Inevitably, this means that the backup will just fill up and up with stuff that is no longer needed.

Also, some suggestions: Can it be made so that...
 i) ...you can synchronise more than one folder? As a dual-booter, I want to backup not only my /home folder but also the shared folder (I've figured out how to do this by modifying the folder_sync.sh file, but reckon it would be a good feature).
 ii) ...you can review exactly what you are synchronising and where?
 iii) ...there is a 'Synchronise Now' option, which overrides the schedule, or so that it doesn't have to be scheduled at all?
Also, any chance of some sort of progress bar, even one of those text-only ones in the terminal?

---

### Post by mdpalow on 2007-12-18
> **Greasyfingers said:**
> 

One questions (I expect there'll be more) - I have a twin HDD setup, and I like the synchronize feature, but cp doesn't seem capable of deleting stuff on the backup which no longer exists on the source folder. Is this right? Inevitably, this means that the backup will just fill up and up with stuff that is no longer needed.

Also, some suggestions: Can it be made so that...
 i) ...you can synchronise more than one folder? As a dual-booter, I want to backup not only my /home folder but also the shared folder (I've figured out how to do this by modifying the folder_sync.sh file, but reckon it would be a good feature).
 ii) ...you can review exactly what you are synchronising and where?
 iii) ...there is a 'Synchronise Now' option, which overrides the schedule, or so that it doesn't have to be scheduled at all?
Also, any chance of some sort of progress bar, even one of those text-only ones in the terminal?

Thanks greasyfingers :)

i) When you select folders to synchronize, you can select more than one and therefore don't need to edit the 'folder_sync.sh' file. Just hold down your CTRL key and select as many folders as you like; to include hidden (.xxxx) files.

ii) I thought to make it show you what you had selected, but I thought the pop-up window might not be able to handle it if someone were to select a lot of folders to back-up. I will look into this for you.

iii) lol. I was actually working on that right now when your message came in. :) The progress bar in Zenity isn't very good. I've experimented with it and it doesn't work when you have a variable; such as copying an unknown amount of files. If I knew, for instance, that I was going to make QuickStart perform a function that say... installed 10 files then it would work nicely because I know there are ten files and I could make the progress bar update every 10% or 1 file. However, since I could never know how many files will be copied in your sync schedule, I can't program it. I know it would be nice to have and I wanted to put it in myself, but for now I don't think it'll happen unless they update zenity.

---

### Post by Greasyfingers on 2007-12-18
[quote="mdpalow"]Just hold down your CTRL key and select as many folders as you like[/quote]I get it! Still need to figure out how to select just sub-folders, though.

[quote="mdpalow"]I know it would be nice to have and I wanted to put it in myself, but for now I don't think it'll happen unless they update zenity.[/quote] OK - it was just a minor detail.

Any idea for that problem with cp?

Thanks

---

### Post by mdpalow on 2007-12-18
> **Greasyfingers said:**
> I get it! Still need to figure out how to select just sub-folders, though.

 OK - it was just a minor detail.

Any idea for that problem with cp?

Thanks

I understand what you mean about deleting a file from the original folder and then having the back-up file still sitting in the synchronized folder taking up space, but I can't initially see why that might be considered a problem or bad thing. Believe me though... I get what you're saying.

Since I've been doing it manually for some time, I just go into the folder periodically and delete things I don't need anymore and since I don't do it that often, I guess I view it as a last chance to recover a file that I already deleted in the original folder and didn't back-up.

I'd have to give it more thought, but right now I think it doesn't sit right with me to write a script that goes through and deletes any files that exist in the sycn folder because it no longer exist in the orig folder. Seems a bit scary to just delete all those files with the click of a mouse without going through them one by one and making sure.

I have however just added the override feature where you can synchronize without having to wait for the scheduled sync to occur. Also, based on your first post, I've rewritten something to take in account when a user manually edits the sync file like you did. Must admit, didn't consider anyone would want to edit it, but now it's accounted for in the latest update when it comes out.

thanks....

---

### Post by mdpalow on 2007-12-18
Ok... so based on some good suggestions by Greasyfingers

I've added his suggestions and a couple of my own updates

Now you have the option to create your first sync after your schedule is created. Should have been there from the beginning.

There's now an option to override the schedule and sync when you want. Thanks Greasyfingers

Now you will be given a list of folders you selected, so you can take another look. Thanks Greasyfingers

and

Now QuickStart is able to clean up after itself better even when user edits sync file.

Thanks Greasyfingers for your suggestions.

I haven't heard from anyone about my dilemma I posted a few messages up. No one with an opinion?

thanks

update is uploaded to server so you can update QuickStart any time.

---

### Post by bw44 on 2007-12-18
> **mdpalow said:**
> ...
I haven't heard from anyone about my dilemma I posted a few messages up. No one with an opinion? ...

I've gotten a bit behind your updates to QuickStart, and haven't tried all the features you've introduced in the last few days.  The sync function is good, but when I'm asked to select the folders  to be sync-ed, zenity doesn't allow me to select any of  the hidden (.folder_name) folders I would most like to keep up to date, such as .mozillla and .mozilla-thunderbird. (Which I copy to my flash disk fairly regularly now.)   Did I miss something?  (The online help file is falling behind the pace of innovation!)  I'm not familiar with zenity -- can it be configured to display the hidden files and folders?

I'm also unclear about why exactly, I would choose to sync a folder rather than back it up. Is it because if I back up a folder every day (week, whatever), I will have to manually delete older versions of the backup as they start to accumulate and are no longer useful, but consuming space? Sync-ing folders (which I gather means updating the "backed up" version of the files in the folder, with only those files that have changed) used to be called "incremental" backup didn't it? Or is that something different? If you made the change you're considering, would I be keeping multiple versions of any file which has been updated more than once, but in the same folder with all the files that haven't changed? 

In your discussion with others, I got the impression you all have a requirement to back up huge file systems, but can't afford (or don't want to pay for) complete backups, when only a random selection of files are likely to have changed during the interval between backups (or syncs).   

I can see why some people might like to have multiple "generations" of certain files, but my own needs wouldn't dictate this enhancement.  I would only ask that the "sync-with-replacement" be retained as an option.  The problem with very large file sizes wouldn't affect me, since I would not be backing up (I mean "sync-ing") such files.

QuickStart is a great tool for comparative noobs (like me!), but it's obvious that more experienced users are finding new or potential applications for it as well.
I've been reading the chapter on "Backing Up and Restoring Files" in the _Ubuntu Linux Bible_ and before I can help you with _your_ dilemma I need to think through what _my_ backup requirements really are.  I'm a great believer in backup, but It's not true that "you can't have too much backup!" 

Can you recommend other discussions of the pedestrian backup requirements of ordinary users (as opposed to people maintaining, say, shared files in a multi-user network environment)?  As a long-time Windows user I had cobbled together a rough set of procedures using NTbackup and file copies  to: 1) insure I could re-build my system and recover it to the point of the last (yesterday's!) major software change; and 2)restore any highly active and important files I was using. 

Thanks for any suggestions.  (Oh, and what's the deal with the hidden folders?)

---

### Post by mdpalow on 2007-12-18
Wow bw44... I actually had to open another window to reply here just so I can go back and forth between the two. Copying your quote here would be too large. :)

First. Just press CTRL + H to show hidden files. Mine is showing hidden folders by default because I pressed CTRL + H once before.

Yes, in a sense it is an incremental back-up and one that you wouldn't have to untar if you needed it. With the tar back-up you have to restore the entire file where as with synching, you could essentially just copy the backed up files right out and paste them elsewhere. It's also a lot quicker since you're only updating changed files and even then just a select few folders.

Yes, you would have multiple versions of a file that changed if I made the update I was suggesting. However, you must consider how many files you update that often. The only file for me that is going crazy with increments is the QUICKSTART program!  LOL :)

hmm, no discussion about backing up huge system files or anything like that. Not sure what you mean. Just trying to avoid an issue where you change a file and then sync over it and then find out later you wish you hadn't made that change and want the old one back. If you did an hourly sync, you might not be able to get the old one back as it would have been overwritten already with the new change. Also, just wondering if someone has a huge file (gig(s)) they edit a lot, which means doing an incremental might have a big impact at some point.

"Can you recommend other discussions of the pedestrian backup requirements of ordinary users (as opposed to people maintaining, say, shared files in a multi-user network environment)?"

Not sure what you meant there. My example earlier of VMware and Windows XP is probably used by a majority of new users and was the only example I could think of to highlight my point about big files. I personally am not doing anything over shared networks or such. I made QuickStart to just back-up my computer like you. :)

Again, press CTRL + H to see hidden folders.

Thanks for your reply..

---

### Post by bw44 on 2007-12-18
Sorry about the ramble. (Like Pacal said "I apologize that this letter is so long, I didn't have time to make it short.")

At least one user mentioned wanting to back up to multiple hard disks, and your example of  "two, 3 gig files in the VMware folder; the original and the revision" made me think your proposed changes were addressing  the needs of power users.  The chapter in the book I mentioned is addressed to system administrators as much as individual users.

The whole point of my post was really a question to myself:  how can I make best use of QuickStart as it is, and do I need the facilities mdpalow is proposing? Sorry to take up your time.

Thanks for your (as always) thoughtful reply and for the tip about CTRL + H to get at the hidden folders.

Cheers.

P.S. Just tried the sync function -- it's great!

---

### Post by mdpalow on 2007-12-18
> **bw44 said:**
> 

At least one user mentioned wanting to back up to multiple hard disks, and your example of  "two, 3 gig files in the VMware folder; the original and the revision" made me think your proposed changes were addressing  the needs of power users.  The chapter in the book I mentioned is addressed to system administrators as much as individual users.


P.S. Just tried the sync function -- it's great!

Ok, I went back and saw that message. No, he was just talking about a separate partition he made with FAT32, which he uses to share files between Windows and Ubuntu depending on which OS he's in at the time. Since win can't read EXT3 there has to be a partition where both OS's can read and that's FAT32.

Glad you liked the Sync feature. I take it the CTRL + H worked for you? :)

[COLOR="Red"]HOWEVER, I just fixed a bug and a conceptual error and uploaded the update to the server, so pls update again.

bug was wrong path and concept error was I was creating sync in regular user mode, but if someone wants to sync system folders then they have to be SU, so had to change the command to sudo.

I personally don't use sync to sync system folders; just personal folders - so I didn't think to put sudo in front of the command.[/COLOR]

[COLOR="Red"]PLEASE UPDATE[/COLOR]

---

### Post by bw44 on 2007-12-18
> **mdpalow said:**
> ... I take it the CTRL + H worked for you? :) ... I personally don't use sync to sync system folders; just personal folders - so I didn't think to put sudo in front of the command.
Yes, CTRL+H works fine (any way to make it stick across sessions?)

I wouldn't know enough about system files to know what to sync! I guess the .mozilla folders could be considered "system," but I think you said you also sync them (or was it another user? -- anyway, someone mentioned them.)

I updated QuickStart and set up my sync schedule for .mozilla , .mozilla-thunderbird, QuickStart(!), and one personal folder to be sync-ed to a destination folder on my Kingston memory stick.  There was a message in the terminal window that this operation  might require my sudo password, but I wasn't asked to enter it.  Then the following messages appeared on the terminal:```
cp: cannot create symbolic link `/media/KINGSTON/daily_backups/.mozilla/firefox/naokggc0.default/lock': Operation not permitted
cp: cannot create symbolic link `/media/KINGSTON/daily_backups/.mozilla-thunderbird/ifc91egv.default/lock': Operation not permitted
```

I did a quick check of files in the destination folders and the sync seems to have worked, but the destination folders are one item short. I have no idea what the above messages mean.  Are they anything to worry about?

---

### Post by bw44 on 2007-12-19
Oops! I just requested "Synchronize Now (Don't Wait for Schedule)". This terminal output doesn't look good ```
 Select a schedule for the folders you will be synchronizing or select
 'Delete My Current Sync Schedule' to delete a previously created synchroni-
 zation schedule. 

 Hourly - Your back-up folders will be compared against your original folders
 each hour. If there is a change to the original folders, the back-up folders 
 will be updated.

 Daily  - Same as above, but updated only once a day.

 Weekly - Same as above, but updated weekly. 

[sudo] password for bob:
cp: failed to preserve ownership for `/media/KINGSTON/daily_backups/.mozilla/firefox/naokggc0.default/cookies.txt': Operation not permitted
cp: failed to preserve ownership for `/media/KINGSTON/daily_backups/.mozilla/firefox/naokggc0.default/Cache/730D5609d01': Operation not permitted
cp: failed to preserve ownership for `/media/KINGSTON/daily_backups/.mozilla/firefox/naokggc0.default/Cache/730D560Ed01': Operation not permitted
cp: failed to preserve ownership for `/media/KINGSTON/daily_backups/.mozilla/firefox/naokggc0.default/Cache/5247B0E0d01': Operation not permitted

[and so on and on]

cp: failed to preserve ownership for `/media/KINGSTON/daily_backups/.mozilla-thunderbird': Operation not permitted
cp: failed to preserve ownership for `/media/KINGSTON/daily_backups/journals': Operation not permitted
cp: failed to preserve ownership for `/media/KINGSTON/daily_backups/QuickStart/QuickStart.desktop': Operation not permitted
cp: failed to preserve ownership for `/media/KINGSTON/daily_backups/QuickStart': Operation not permitted

 Welcome to QuickStart 4.0

 Please keep this terminal window in view (upper left-hand corner) as
 important messages and requests will be passed to you here.

 Select an option and press OK to begin
```

Help!:(

P.S.  I changed the destination folder to my Fat32 partition in case the problem was with my memory stick. But the same or similar messages appeared, most having to do with cp: failed  to preserve (something or other).  Again, the files appear to be there and accessible.

---

### Post by mdpalow on 2007-12-19
Hey bw44,

Sorry to get to this so late, but I didn't see it.

I think the reason you're getting these errors is because both locations you're trying to 'cp' to are FAT32 drives. Even the Kingston should be a FAT32, similar to a USB Flash drive.

FAT32 drives can not handle Linux file permissions.

Do you have a hard drive that is formatted EXT3 (Ubuntu/Linux recommended)? That should work for you.

Let me know.....

P.S. I would imagine the files are copied, just without the permissions/ownership..etc...

P.P.S. I will probably need to put something in QuickStart that says not to save to a FAT32 drive...

---

### Post by mdpalow on 2007-12-19
> **bw44 said:**
> Yes, CTRL+H works fine (any way to make it stick across sessions?)

I updated QuickStart and set up my sync schedule for .mozilla , .mozilla-thunderbird, QuickStart(!), and one personal folder to be sync-ed to a destination folder on my Kingston memory stick.  There was a message in the terminal window that this operation  might require my sudo password, but I wasn't asked to enter it.  Then the following messages appeared on the terminal:```
cp: cannot create symbolic link `/media/KINGSTON/daily_backups/.mozilla/firefox/naokggc0.default/lock': Operation not permitted
cp: cannot create symbolic link `/media/KINGSTON/daily_backups/.mozilla-thunderbird/ifc91egv.default/lock': Operation not permitted
```

I did a quick check of files in the destination folders and the sync seems to have worked, but the destination folders are one item short. I have no idea what the above messages mean.  Are they anything to worry about?

If you were to open a terminal window and try to copy a folder that included a symbolic link, it simply wouldn't do it and you'd never know it. However, when you run a script that copies a folder that includes a symbolic link, which it can't do - it spits out an error. I've uploaded an update to QuickStart just now that should fix the issues you've been experiencing.

Try it all again to a non-fat32 drive and see if you still get errors. I'm thinking once you update QuickStart and run again you won't have any errors.

thanks..

---

### Post by altonbr on 2007-12-19
So I was looking through your code and I didn't notice a license. Make sure to license your code eh!?

GPLv2, GPLv3, Apache, Mozilla, whatever!

---

### Post by altonbr on 2007-12-19
Oh and might I advise you to use this:
```
PASSWORD=`zenity --title='Password' --text='Please enter your password' --entry`
echo $PASSWORD | sudo -S aptitude install zenity | zenity --text-info
```
for asking the user's password and displaying output.

This will remove the use of the terminal almost altogether.

---

### Post by bazanime on 2007-12-19
Nice nice nice!!! A big visual improvement.  Good work.

---

### Post by zchenyu on 2007-12-22
Wow, this successfully installed Flash on my 64 bit Ubuntu! I've been trying for days to get Flash working while this program finished it in a matter of minutes!

Thank you!

PS. Flash hangs FireFox when entering/exiting a page with Flash in it

---

### Post by ubukool on 2007-12-23
mdpalow,

Thanks very much for this.  I've tried Time Vault which seems great for  taking snapshots of individual files which change, but it's much less clear how to make a whole system backup; your system, on the other hand, is very easy to use to make backup files.

I notice there is no help file with the latest version (there was when it was 'Ubackup!') so is the restore completely automated with the menu options - there's really no need to manually restore any directories?

Also, I tried double clicking on the Tar backup file for /home and file roller says that it can't open the archive because "archive type not supported".  Any idea why?

Many thanks for all your work! :)

---

### Post by altonbr on 2007-12-24
Just giving you a shout out on Christmas that this is a wonderful program!

---

### Post by mdpalow on 2007-12-25
> **ubukool said:**
> mdpalow,

Thanks very much for this.  I've tried Time Vault which seems great for  taking snapshots of individual files which change, but it's much less clear how to make a whole system backup; your system, on the other hand, is very easy to use to make backup files.

I notice there is no help file with the latest version (there was when it was 'Ubackup!') so is the restore completely automated with the menu options - there's really no need to manually restore any directories?

Also, I tried double clicking on the Tar backup file for /home and file roller says that it can't open the archive because "archive type not supported".  Any idea why?

Many thanks for all your work! :)

Hi Ubukool,

Sorry to get back to you so late.

The help file is now a wiki that is built into the program. Look at the bottom of the main menu. You may need to update, since I don't know which version you have. 

We're up to QuickStart 5.0 as of today since I added some updates to help clean out my computer periodically. 

I must admit, the help wiki is not up to date though, but to answer your question - - when restoring, you simply have to select the back-up file you want to restore and that's it. In most cases, that will be both the home_backup_yyyy.mm.dd.tgz and the system_backup_yyyy.mm.dd.tgz files. Bottom line... no, you don't restore any individual folders/directories when restoring; just all of it. :)

I will be working on the help wiki to catch up with all the updates.

Not sure why you can't see the home_backup file after backing up. I'm using the .gz standard and it seems to work for everyone else, plus the four computers I test on. If you'd like to send me a Private Message with all the details of what you're doing, maybe we can figure it out.

I'll keep an eye out for your PM.

...

---

### Post by mdpalow on 2007-12-25
Just a quick message to everyone.

I've put a little 'stocking stuffer' for those of you using QuickStart. It's called QuickStart 5.0.

I've been looking into the process of cleaning up my computer from unnecessary files. I've found a few places where files are stored, which you can delete in order to make more room on your hard drive. I found over 350 megs of stuff that could be removed. I imagine many of you will have much more as I don't really load much onto my computer. This 'House Cleaning' utility is now added to QuickStart 5.0.

Hope you enjoy your gift and Happy Holidays...

---

### Post by mdpalow on 2007-12-25
Please hold up on the update.... if you haven't already... just found a bug that needs fixing first for the new version...

will be fixed soon.

---

### Post by mdpalow on 2007-12-25
Ok... fixed.

forgot to change the inner menus to call the main menu correctly when exiting with the new format.

Did a find so I could manually replace and should have gotten them all.

If you already updated before this message, you'll have to do it again.

thanks...

---

### Post by jkzubu on 2007-12-25
mdpalow-

I love your program and have been using it since uBackup.  I just upgraded to QuickStart (yesterday on my P3 and this AM on my AMD64x2) and ran the backups.  I am currently running Gutsy on both.  You mention that there is a bug.  I am just wondering if this bug will affect my backups from yesterday and/or earlier this morning? ---Edit--- I see from your post that this answer is likely to be that the backup files I made are just fine.

Also:
1.  One thing I really like about the uBackup version was seeing the backup files get rattled through the terminal window while in process. I ran the backups on my P3 machine yesterday and this view was active.

I ran the QS 5 this AM on my AMD machine and this view was replaced with small graphical window.  Is it still possible, with QS 5 on the AMD, to see the terminal window view during backup?  I like to see the files and their loactaions during the backup process.

2.  Are all of the Medibuntu (multimedia codecs) installed in option 12? Or are just DVD codecs installed?

3.  I may downgrade my older P3 machine to 6.10 LTS.  I am just cruious to know if the QS 5 backup files will 'restore' to 6.10.  I have read the through this thread and I see you have tested it with Feisty and Gutsy.

4.  I notice that the QS 5 icon seems to be tied to the desktop.  While I am able to delete it, it it always comes back when I launch the program.  I would like to keep the icon either in my AWN, in a panel, or in a menu.  How can I keep the icon off the desktop?

Thank you for the great work.

Jim K.

---

### Post by mdpalow on 2007-12-25
> **jkzubu said:**
> mdpalow-

I love your program and have been using it since uBackup.  I just upgraded to QuickStart (yesterday on my P3 and this AM on my AMD64x2) and ran the backups.  You mention that there is a bug.  I am just wondering if this bug will affect my backups from yesterday and/or earlier this morning?

Also:
1.  One thing I really like about the uBackup version was seeing the backup files get rattled through the terminal window while in process. I ran the backups on my P3 machine yesterday and this view was active.

I ran the QS 5 this AM on my AMD machine and this view was replaced with small graphical window.  Is it still possible, with QS 5 on the AMD, to see the terminal window view during backup?  I like to see the files and their loactaions during the backup process.

2.  Are all of the Medibuntu (multimedia codecs) installed in option 12? Or are just DVD codecs installed?

3.  I may downgrade my older P3 machine to 6.10 LTS.  I am just cruious to know if the QS 5 backup files will 'restore' to 6.10.  I have read the through this thread and I see you have tested it with Feisty and Gutsy.

Thank you for the great work.

Jim K.

Hi Jim and thanks.

1. The bug was only a problem when you Canceled an option. It wouldn't go back to the main menu. Please download again, so it runs properly. There would be no problem with your back-up as that command has remained the same since the beginning when it was uBackup! 1.0.

2. Unfortunately, the terminal window to see the back-up " MAY " be gone forever. Actually, I like seeing the files processed too and it was the main reason for holding off going to full GUI for a while. I was able to get the gui to show the files being processed, but zenity works on the popup message principle. Meaning you have to close a window before it will continue. The files being processed were in a popup window and wouldn't continue on to the next back-up (if you selected to do all three at once for example) until you clicked OK. If you wanted to leave while backing up, it would never finish.

IFFFFF, I could pipe the backup to a gnome-terminal I would be glad to show the terminal for back-ups, but I couldn't get it to work. I will keep trying and ask a friend for some help to see if I can get it right. :)

3. Everything required by the MEDIBUNTU is installed; not just the codecs.

4. I personally haven't tested it on Feisty, but other users have. I may be misunderstanding your question, so I'll answer both ways.

If you were downgrading, you wouldn't want to restore your files as this would simply put 7.10 back on. 

However, I think you mean will back-up and restore using QuickStart 5.0 work on Feisty. Assuming all the folders are named the same and the directory structure is the same it will work as expected. 

You could always run another test for us as it would only take about 15 minutes to test. Of course if it didn't work, you would have to reinstall one more time and that would take another 15 minutes. :)

My instinct tells me there weren't changes to the directory structure in the two versions and it will work for you.

Hope I answered your questions.

Happy Holidays ...

---

### Post by CanonKen on 2007-12-25
I've just downloaded the latest version but it won't bring the terminal up now for some reason

Edit - ignor me, just tread the posts above :)

---

### Post by mdpalow on 2007-12-25
> **CanonKen said:**
> I've just downloaded the latest version but it won't bring the terminal up now for some reason

Hi CanonKen...

The new version is completely GUI now like a regular program. All messages are now passed to you in a graphical window instead of both a graphical and terminal window that sits in the back..

---

### Post by jkzubu on 2007-12-25
Thanks md-

I did have a question #4 that I edited in during the interim (about the icon).  Perhaps you could just review that question.

Yeah, I am wondering about the downgrade part.  I am currently running Gutsy on the older P3.  I am thinking about downgrading to 6.10 LTS, and upgrading to the 2008 LTS when it becomes released.  Your answer makes sense, and if I do the downgrade, I'll just go from scratch.  I just use the P3 machine for hacking around.  Thanks.

Jim K.

---

### Post by mdpalow on 2007-12-25
> 4. I notice that the QS 5 icon seems to be tied to the desktop. While I am able to delete it, it it always comes back when I launch the program. I would like to keep the icon either in my AWN, in a panel, or in a menu. How can I keep the icon off the desktop?

Sorry I missed that...

I don't know what you mean by the icon is tied to the Desktop. The icon is simply a file that is linked to the program and launches it. If you delete it (icon), it does not come back when you run the program - or at least it shouldn't.

The icon is however re-created for you every time you upgrade just to give an indication of how to run the program for new users, but you can delete it or drag it to your panel. There's also a copy of the icon in your QuickStart folder just in case you delete it and want to bring it back at a later time.

I did however delete mine and ran the program again from the folder and no new icon was re-created.

Could you Private Message me the steps you're taking to cause this to happen for you because I'm not seeing it happen here?

thanks...

---

### Post by altonbr on 2007-12-25
I think the file should lay in /usr/share/applications and tell the application to be installed in System Tools via the .desktop file.

That way the user can add it to his or her desktop or panel by choice, but it stays in the Applications menu by default as per most graphical Ubuntu programs.

> [Desktop Entry]
Encoding=UTF-8
Version=5.0
Name=QuickStart 5
Comment=Backup your computer!
Exec=/home/$USER/QuickStart/QuickStart
Terminal=false
Type=Application
Icon=/usr/share/icons/gnome/scalable/categories/applications-utilities.svg
**Categories=Application;System;**

---

### Post by mdpalow on 2007-12-25
It's a good suggestion altonbr. II've been a little leery of putting QuickStart anywhere but on the Desktop in favor of:

1. Making it easy to find immediately after downloading/installing.

2. Letting the user decide what they want to do with the icon.

However, if I were to get some feed-back that said "make the install put the icon in the menu" then I would re-write the update function to put it there, but until then... I didn't want to impose. :)

All I do is open my MAIN MENU option in SYSTEM -> PREFERENCES -> MAIN MENU and drag the icon where I like it.

Like I said though... If users prefer the icon placed in the Menu somewhere, we can do it. Just tell me where you think it's best placed and we'll move it.

"Whatever the users want........... mostly anyways." :) lol

---

### Post by mdpalow on 2007-12-26
Hi Everyone,

Please update your QuickStart...

I had to install Java tonight for a program I wanted to run and was immediately reminded of a quirk in the install process for java. Maybe not a real quirk, but something to cause a bug with the new version of QuickStart.

I've made the fix, so please update as this is an important one. Not updating will cause your Java package to not install completely and then you have to do the " sudo dpkg --configure -a" command in the terminal, etc., etc..

I've actually had to make it so a terminal window is opened up, so the Java license can be read and agreed to, which is a terminal window written script.

thanks...

---

### Post by altonbr on 2007-12-26
See, wouldn't this be easier if it was in a repository? Possibly a Launchpad PPA? :P

I'll see if I can work out the details and get one set up for you :D

---

### Post by garret on 2007-12-26
[http://restore-backup.com](http://restore-backup.com) is worth a look too. GPL based project.

---

### Post by money2themax on 2007-12-26
this rocks this is going to be shared with my friends

---

### Post by Barrius on 2007-12-26
mdpalow, downloaded/installed per instruction without problems on AMD64 Gutsy.  When attempting to execute the Quickstarter icon I receive "Ther was an error launching the application.  Details: Failed to execute child process "/home/barrius/QuickStart/QuickStart" (No such file or directory)"

I've deleted the Quickstart directory, downloaded the script and re-ran with the same results.  Any suggestions?

---

### Post by mdpalow on 2007-12-26
> **Barrius said:**
> mdpalow, downloaded/installed per instruction without problems on AMD64 Gutsy.  When attempting to execute the Quickstarter icon I receive "Ther was an error launching the application.  Details: Failed to execute child process "/home/barrius/QuickStart/QuickStart" (No such file or directory)"

I've deleted the Quickstart directory, downloaded the script and re-ran with the same results.  Any suggestions?

I sent you a private message just checking to make sure you did everything right, but I just tested everything from downloading the Install_QuickStart.sh file to running the program and it seems to be all in order.

I see someone else downloaded just before you and it worked for them. Anyone else experiencing any problems I should know about?

Thanks..

---

### Post by mdpalow on 2007-12-27
Just an update for 64-bit users...

Barrius' comments got me thinking that his 64-bit OS might be the reason why it's not working for him. I loaded the 64-bit version a short while ago to test and sure enough QuickStart didn't run.

So, I opened a terminal window and entered:   [COLOR="Red"]sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0[/COLOR]

to load the files necessary to run 32-bit apps and it worked straight away.

---

### Post by OffHand on 2007-12-28
I have made two backups using your application but if I manually try to extract them it bombs out with an error message. Check attachment for output. Help appreciated  :)

Edit: The error was caused because Fat32 cannot handle files larger than 4 GB.

---

### Post by mdpalow on 2007-12-28
Hi Offhand,

I just ran two back-ups using Option 1 - one on /home and the other on the configuration files. I then did an EXTRACT HERE on both .gz files and it worked fine. I then clicked into each .gz file and selected an individual file for extraction to the desktop and it worked fine.

Am I doing the same thing as you're attempting or no? If not, pls let me know exactly what you're doing, so I can try and recreate it.

---

### Post by altonbr on 2007-12-28
> **OffHand said:**
> I have made two backups using your application but if I manually try to extract them it bombs out with an error message. Check attachment for output. Help appreciated  :)

I don't think 'tar' can follow symbolic links...

---

### Post by mdpalow on 2007-12-28
> **altonbr said:**
> I don't think 'tar' can follow symbolic links...

Thanks altonbr... we're resolving this now over chat. He's trying to save to a FAT32 drive. I just tested to my drive and it worked, so either his drive might be bad or it's like you said about symbolic links; we'll see soon hopefully.

Right now we're trying to back-up to his Desktop instead.

thanks again...

EDIT: It just occurred to me that I have at least one symbolic link (on my desktop) right now and it works when I back-up my /home.

---

### Post by mdpalow on 2007-12-28
I think the problem is the fat32 file size limit. If I remember right, you can't write files larger than 4 gigs and his /home back-up is slightly over 4 gigs.

...

---

### Post by OffHand on 2007-12-28
The error happened because Fat32 cannot handle files larger than 4 GB. Problem solved  :)

---

### Post by mdpalow on 2007-12-28
Ok, as we can see the problem was due to a large back-up file that was being written to a file system (FAT32) that couldn't handle file sizes larger than 4 gigs.

Backing up to FAT32 is still possible as long as any ONE file isn't larger than 4 gigs.

I went ahead and updated the pop-up window just before you select your destination to mention this fact as a reminder, so it hopefully doesn't happen to someone else.

...

---

### Post by altonbr on 2007-12-28
> **OffHand said:**
> The error happened because Fat32 cannot handle files larger than 4 GB. Problem solved  :)

> **http://en.wikipedia.org/wiki/Fat32]Max file size 	4 GiB &#8722 said:**
> 

Yikes! Damn Windows 95 file system!

[QUOTE=mdpalow;4030019]Thanks altonbr... we're resolving this now over chat. He's trying to save to a FAT32 drive. I just tested to my drive and it worked, so either his drive might be bad or it's like you said about symbolic links; we'll see soon hopefully.

Right now we're trying to back-up to his Desktop instead.

thanks again...

EDIT: It just occurred to me that I have at least one symbolic link (on my desktop) right now and it works when I back-up my /home.

I still think you need to add the '-h' flag for following symbolic links with tar

[QUOTE='man tar'] -h, --dereference
don&#8217;t dump symlinks; dump the files they point to
[/QUOTE]

Might be wrong on that one.

---

### Post by mdpalow on 2007-12-28
I don't know. Right now to me... it doesn't make sense to change anything because the symbolic link is copied and when you restore it, it still points to the original file. Also, the file it's linked to is not copied unless you selected that folder for back-up as well. 

Seems right, am I missing something?

thanks...

---

### Post by OffHand on 2007-12-28
> **mdpalow said:**
> I don't know. Right now to me... it doesn't make sense to change anything because the symbolic link is copied and when you restore it, it still points to the original file. Also, the file it's linked to is not copied unless you selected that folder for back-up as well. 

Seems right, am I missing something?

thanks...

One question: If you restore your home folder using your app does it replace the current home folder or does it ask you to overwrite or skip the file?

---

### Post by mdpalow on 2007-12-28
> **OffHand said:**
> One question: If you restore your home folder using your app does it replace the current home folder or does it ask you to overwrite or skip the file?

A restore will make the directory if it's not there. Otherwise, the files located in the back-up would overwrite the files with the same name in current folder.

So, if you had in a folder called test and files inside were 1.txt, 2.txt, and 3.txt. Then you backed it up. Then tomorrow you added 4.txt and 5.txt. Then you restored the backup, it would overwrite 1.txt, 2.txt, and 3.txt, but it wouldn't do anything to 4.txt and 5.txt.

It will only overwrite same name files and leave everything else there.

That's why tar isn't the best solution for restoring a system if you're one who likes a really clean system with no extra files sitting on the drive. Well, let me rephrase that. Tar is great for this as well, but if you want a really clean system, you would want to load the Live CD and format the partitions and start with a fresh install and then restore your tar backup. Then it would be really clean... as long as your back-up was made before you started adding all sorts of things you now don't want now. :)

and.... no, it won't ask you about overwriting. It just does it.

Did that make any sense? ;)

---

### Post by OffHand on 2007-12-28
It does... thanks.

---

### Post by altonbr on 2007-12-28
> **mdpalow said:**
> A restore will make the directory if it's not there. Otherwise, the files located in the back-up would overwrite the files with the same name in current folder.

So, if you had in a folder called test and files inside were 1.txt, 2.txt, and 3.txt. Then you backed it up. Then tomorrow you added 4.txt and 5.txt. Then you restored the backup, it would overwrite 1.txt, 2.txt, and 3.txt, but it wouldn't do anything to 4.txt and 5.txt.

It will only overwrite same name files and leave everything else there.

In that case, you should probably look at using ```
rsync -avrz --delete source/ destination/
```

Why? Because what happens if you have 1.txt, 2.txt and 3.txt and then the next day you add 4.txt and 5.txt (as you've said), but then DELETE 1.txt? Does 1.txt get deleted? 'rsync --delete' takes care of that for you.

---

### Post by mdpalow on 2007-12-28
I don't think that was his concern B. rsync is another animal all together.

---

### Post by duce2k on 2007-12-29
Installed quick start using the instructions in the link, does it need a password however?

---

### Post by mdpalow on 2007-12-29
> **duce2k said:**
> Installed quick start using the instructions in the link, does it need a password however?

yes, when you install it, but only to clean up the install. The program is actually already installed and read to go.

The only time you have to use a password in QuickStart is when you are doing something that needs to access your system files or when installing applications, etc... That's normal though as you would have to do it in a terminal window as well.

Did I answer your question?

thanks...

---

### Post by money2themax on 2007-12-29
mket the back up go to a HDD formatted ext3 or NTFS those can handle large files up to 2TB if i'm not mistaken

---

### Post by mdpalow on 2007-12-31
Hi Everyone,

New update available if you want it....

Recently I've had a couple of Private Messages sent to me concerning:

1. Back-up over 4gigs not writing to FAT32 file system.

2. Back-up didn't work when user entered '/' in the description.

The first issue was a limitation in FAT32, which we know - and the second issus is because you can't put '/' in a file name.

I updated QuickStart to remind users of the FAT32 limitation if they were thinking about saving directly to a FAT32 partition and I updated QuickStart to not allow users to enter potentially bad descriptions that would cause QuickStart not to work.

Also, for those of you who love the terminal window when doing a back-up, you'll be happy to know it's back. I have to admit, I missed it too. Also, while doing a recent back-up, I didn't have the terminal window showing me the files being backed up and didn't like the fact I didn't know what was going on until the back-up had finished. I think there might be more out there who feel the same way.

If you don't care to watch the files being backed up, you can simply close the terminal window and leave the progress bar running.

The way it works is... for each back-up you're doing (ex: /, /home, and Configuration files) a separate window will pop up. Now you can review the back-up in the previous window while the files are scrolling up in the next window. When finished, close out the first one and review the second when it's finished.

bye for now...

---

### Post by Casual Fan on 2007-12-31
many thanks!  will give it a whirl...

---

### Post by shanerdaner on 2008-01-01
> **mdpalow said:**
> Hi Everyone,

New update available if you want it....

Recently I've had a couple of Private Messages sent to me concerning:

1. Back-up over 4gigs not writing to FAT32 file system.

2. Back-up didn't work when user entered '/' in the description.

The first issue was a limitation in FAT32, which we know - and the second issus is because you can't put '/' in a file name.

I updated QuickStart to remind users of the FAT32 limitation if they were thinking about saving directly to a FAT32 partition and I updated QuickStart to not allow users to enter potentially bad descriptions that would cause QuickStart not to work.

Also, for those of you who love the terminal window when doing a back-up, you'll be happy to know it's back. I have to admit, I missed it too. Also, while doing a recent back-up, I didn't have the terminal window showing me the files being backed up and didn't like the fact I didn't know what was going on until the back-up had finished. I think there might be more out there who feel the same way.

If you don't care to watch the files being backed up, you can simply close the terminal window and leave the progress bar running.

The way it works is... for each back-up you're doing (ex: /, /home, and Configuration files) a separate window will pop up. Now you can review the back-up in the previous window while the files are scrolling up in the next window. When finished, close out the first one and review the second when it's finished.

bye for now...

Send me the next beta to test when you are ready and HAPPY NEW YEAR!!!

---

### Post by verb3k on 2008-01-01
mdpalow, please provide the source code, I am interested in learning from you, that's the spirit of open source!

---

### Post by Goomacher on 2008-01-03
I am new to Ubuntu.  Unfortunately for me, I had to do a bunch of searches post readings to find all the info that this one app provides.  I used one of the earlier versions and everything I needed worked.  I just came back and downloaded the newest version and I'm even more impressed.  I especially like the option to not install certain apps.  Thank you very much for your efforts.  You have saved me an incredible amount of time and energy.

---

### Post by NullHead on 2008-01-03
Great work! I will try it out soon. Keep up the good work! :popcorn:

---

### Post by Barrius on 2008-01-03
> **mdpalow said:**
> Just an update for 64-bit users...

Barrius' comments got me thinking that his 64-bit OS might be the reason why it's not working for him. I loaded the 64-bit version a short while ago to test and sure enough QuickStart didn't run.

So, I opened a terminal window and entered:   [COLOR="Red"]sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0[/COLOR]

to load the files necessary to run 32-bit apps and it worked straight away.

mdpalow, the sudo apt-get command to install the missing files worked perfect.   Many thanks -preparing to try it out!

---

### Post by Arcuru on 2008-01-06
This helped fix some DVD playback and flash issues for me.  Very easy to use, I definitely recommend it.

---

### Post by NorthernSuze on 2008-01-06
Thanks for quick simple solution for back-up.  Sure beats all the dithering about   tar options and which ones to use and what if I use the wrong ones!!!  <grin>  With a good copy (or two) of backups I will have more confidence to learn and explore Ubuntu.
Suzanne in northern BC Canada

---

### Post by mdpalow on 2008-01-08
Hi Everyone,

Just an update for anyone watching this thread.

Last week I had a need to install Windows and do a dual-boot. That install got me thinking again about how much I hate installing Windows because of the length of time it takes.

So, I've updated QuickStart with another module that will now:

Back-up your Master Boot Record (MBR)
Back-up (Clone) your Windows Partition
Restore your MBR
Restore your Windows partition.

I've already written the code and got it in QuickStart. It's tested and works wonderfully. I was able to delete my Windows partition and restore it from Ubuntu in less than 5 minutes. Granted I hadn't loaded all the Windows updates or any additional programs, so it was quick, but it ran beautifully after re-booting and the GRUB menu is intact allowing you to boot into Ubuntu or Windows.

I've been cleaning up code again, so it might be a day or two before I actually upload QuickStart 6.0 because I want to run tests on everything else again.

Initial tests have been perfect so far with no problems, but I'll still check some more.

bye for now...

---

### Post by Aaronought on 2008-01-08
Thank you very much for this program it worked like a charm.

i have used the:

"install the DVD and codec files"
"install flash plugin 32/64-bit"
"install JAVA 6"

parts and all worked wonderfully.

Thanks again pal

Aaron.

---

### Post by mdpalow on 2008-01-10
Anyone out there want to take a crack at QuickStart 6.0 before I actually put it up on the server?

I'm really interested in hearing from anyone that's a dual-booter (Windows & Ubuntu 7.10).

Send me a Private Message (with your e-mail address) if you're interested.

Thanks...

---

### Post by brucewagner on 2008-01-10
MDPALOW....   Wow wow wow. 

I just discovered this thread. It appears to be a dream come true. Quite literally. 

First, I hope you won't mind me saying that you're an angel for recognizing this obvious need, then creating the solution and sharing it.  That's the spirit of Ubuntu at work. Love it!  Thank You so Much!!!

Second, it might have taken me so long to find it due to the title of the thread. I wasn't really looking for a Backup solution at the moment (much less a "new" one), so I may have overlooked it more than once.   I know that, for you, this apparently grew of of your need to backup & restore your systems. That's wonderful. However, for me. (and I suspect MANY others), it comes from a desire to simply do an initial install of an Ubuntu system where everything works!   I'm referring to us Brand New Day One Users who don't have the slightest clue why our youtube videos won't play, and the normal websites we frequent which use Java aplets won't run, and our movies as AVI files won't play, and our DVDs won't play. 

MOST brand new users probably just blame Ubuntu and say things like, "Ubuntu is not ready for prime time.", etc.  (That includes the Tech writers for the New York Times & Wall Steeet Journal & USA Today)  A minority of us brand new users will have the determination to preserve and scour these forums for answers.  Then, we find answers. Many answers. Too many answers.  Many conflicting stories. And we have to wonder to ourselves, "Am I doing more harm than good to my system, trying all these fixes that end up not working?"   If they're nervous about it, like me, and really really want it to be stable and "right"... they may end up doing a fresh install again and again, after every failed attempt to solve these flash/java/DVD problems...   

So, for me to notice it, the title of the thread could have been, "How to Get a Fresh Install of Ubuntu that Works"

Now, a couple of Questions:  

(1)     WHY aren't these functions built-in to Ubuntu?

       (a)  I understand the legal issues with DVD decryption, but a simple application that installs this stuff with a suitable legal warning splash-screen should be sufficient.

       (b)  I know there's some issue with Adobe/Ubuntu installing the wrong code for flashplugin, but that seems like it should warrent an almost emergency fix to correct that.

       (c)  And what's this about some programs that need to be installed in order for the 64-bit Ubuntu to be able to run 32-bit apps!?!   That's the first I've heard of that!   That may explain some of the problems I had when I had the AMD64 version of Gutsy installed --- before I finally scrapped that and did a fresh install of the i386 version, in hopes that it might work better on these issues.  WHY aren't those programs installed --- by default --- on the 64-bit version of Ubuntu!?  Please tell me that there's some REALLY valid reason for Ubuntu to omit those programs from their 64-bit base install....  Yes?

       (d)  The backup interface you've created is just the icing on the cake. Everyone needs that too!  I can't think of a single reason that that functionality isn't already included in Ubuntu "out of the box".  TAR is the major standard for backup in the Linux world, no?  Why on earth would there not be a GUI backup utility based on TAR --- like the one you've created here --- built-in to the standard Ubuntu install....?

(2)     What can you do to submit / suggest that this functionality be included in the standard Ubuntu install "out of the box"...?     What can we, the user community, do to request this?  Assist in this?

---

### Post by OffHand on 2008-01-10
> **brucewagner said:**
> MDPALOW....   Wow wow wow. 

I just discovered this thread. It appears to be a dream come true. Quite literally. 

First, I hope you won't mind me saying that you're an angel for recognizing this obvious need, then creating the solution and sharing it.  That's the spirit of Ubuntu at work. Love it!  Thank You so Much!!!

Second, it might have taken me so long to find it due to the title of the thread. I wasn't really looking for a Backup solution at the moment (much less a "new" one), so I may have overlooked it more than once.   I know that, for you, this apparently grew of of your need to backup & restore your systems. That's wonderful. However, for me. (and I suspect MANY others), it comes from a desire to simply do an initial install of an Ubuntu system where everything works!   I'm referring to us Brand New Day One Users who don't have the slightest clue why our youtube videos won't play, and the normal websites we frequent which use Java aplets won't run, and our movies as AVI files won't play, and our DVDs won't play. 

MOST brand new users probably just blame Ubuntu and say things like, "Ubuntu is not ready for prime time.", etc.  (That includes the Tech writers for the New York Times & Wall Steeet Journal & USA Today)  A minority of us brand new users will have the determination to preserve and scour these forums for answers.  Then, we find answers. Many answers. Too many answers.  Many conflicting stories. And we have to wonder to ourselves, "Am I doing more harm than good to my system, trying all these fixes that end up not working?"   If they're nervous about it, like me, and really really want it to be stable and "right"... they may end up doing a fresh install again and again, after every failed attempt to solve these flash/java/DVD problems...   

So, for me to notice it, the title of the thread could have been, "How to Get a Fresh Install of Ubuntu that Works"

Now, a couple of Questios:  

(1)     WHY aren't these functions built-in to Ubuntu?

       (a)  I understand the legal issues with DVD decryption, but a simple application that installs this stuff with a suitable legal warning splash-screen should be sufficient.

       (b)  I know there's some issue with Adobe/Ubuntu installing the wrong code for flashplugin, but that seems like it should warrent an almost emergency fix to correct that.

       (c)  And what's this about some programs that need to be installed in order for the 64-bit Ubuntu to be able to run 32-bit apps!?!   That's the first I've heard of that!   That may explain some of the problems I had when I had the AMD64 version of Gutsy installed --- before I finally scrapped that and did a fresh install of the i386 version, in hopes that it might work better on these issues.  WHY aren't those programs installed --- by default --- on the 64-bit version of Ubuntu!?  Please tell me that there's some REALLY valid reason for Ubuntu to omit those programs from their 64-bit base install....  Yes?

       (d)  The backup interface you've created is just the icing on the cake. Everyone needs that too!  I can't think of a single reason that that functionality isn't already included in Ubuntu "out of the box".  TAR is the major standard for backup in the Linux world, no?  Why on earth would there not be a GUI backup utility based on TAR --- like the one you've created here --- built-in to the standard Ubuntu install....?

(2)     What can you do to submit / suggest that this functionality be included in the stadard Ubuntu install "out of the box"...?     What can we, the user community, do to request this?  Assist in this?

1 a + b) You can install them through Synaptic or with apt-get.
c) 32 bit apps need 32 libraries

---

### Post by brucewagner on 2008-01-10
> **OffHand said:**
> 1 a + b) You can install them through Synaptic or with apt-get.

Not unless I know how to do that.   And how would I know how to do that?

I think you missed the part about me being one of the millions of "brand new day one" users...

Every time I've tried to install them through Synaptic, and every time I've followed posted directions with Terminal commands, it does not work.

> **OffHand said:**
> c) 32 bit apps need 32 libraries

That makes perfect sense.  Except, the question was:  "WHY aren't those programs installed --- by default --- on the 64-bit version of Ubuntu!?"

---

### Post by OffHand on 2008-01-10
Because not all 64 bit users need 32 bit apps.

---

### Post by OffHand on 2008-01-10
> **brucewagner said:**
> Not unless I know how to do that.   And how would I know how to do that?

I think you missed the part about me being one of the millions of "brand new day one" users...

Every time I've tried to install them through Synaptic, and every time I've followed posted directions with Terminal commands, it does not work.

Hmmm fair enough. Most guides on these forums are pretty well written with new users in mind and if something is not clear there usually is someone to help out. Did you ask for help with the issues you had?

P.S. They are not enabled by default for legal reasons (addition to my answer to question 1a). Thank your government for that.

---

### Post by mdpalow on 2008-01-10
Hi Bruce,

I'm following your thread and will answer shortly. I'm currently trying to get through some e-mails and preparing QuickStart 6.0 for some people who have kindly offered to beta test the new release for me.

Thank you for your initial post and kind words. I can't remember all of your original post, but the parts I do remember, I agree with you.

Offhand is right about the 32/64-bit thing, but I'm in agreement with you. It really wouldn't hurt to add a few files to the 64-bit OS to make it more transparent when running 32-bit apps. In fact, I thought 64-bit was always downward compatible with 32-bit apps, but was wrong. I then had to research it to make it possible for 64-bit users to use.

I'll post again shortly about another point you made that I think you hit the target as well, but first I need to prep 6.0.

Again, if anyone else want to give 6.0 a go, pls private message me your e-mail address, so I can send you the install file. Beta testing 6.0 is not dangerous as some might think. Beta testing is, as always, more of a test to make sure the install works properly and the menu options are working correctly.

Yes, you can beta test the Windows partition cloning, but I've already tested it on another computer and it didn't NUKE anything, so I don't foresee any problems with respect to that. :) In fact, as I mentioned in an earlier post a couple/few days ago, it worked rather nicely.

Sometimes I load files to allow QuickStart to do a task, but forget to place them in the code. So even though it works on my machine, if I forgot to put the files in the code for install - it won't work on your machine. That's the kind of stuff I'm looking to beta.

Thanks....

---

### Post by commonplace on 2008-01-10
Just downloaded it. Thanks!

/Kevin

---

### Post by bw44 on 2008-01-11
mdpalow:

A question regarding the "Synchronize Selected Folders" option.  You explained before why we're prevented from writing the synchronized backup to NTFS or Fat32 partitions or devices -- because file permissions aren't preserved.

If I make a tar archive of a synchronized backup and copy ** it** to an NTFS or Fat32 partition will the permissions be correctly preserved if I later restore the archive to my Ubuntu partition?

Thanks.

PS.  Good to see so many new users are discovering QuickStart!

---

### Post by mdpalow on 2008-01-11
In a word.... yes. :)

---

### Post by bw44 on 2008-01-11
> **mdpalow said:**
> In a word.... yes. :)

Just what I hoped to hear! :guitar:

---

### Post by mdpalow on 2008-01-11
bw44...

Think it might be time to trim your whiskers...


;)

---

### Post by Amstell on 2008-01-11
I love this.  Use it all the time for people I am install ubuntu on. 

Thanks again man.  Keep it up.

Cheers

---

### Post by nyk52687 on 2008-01-11
Great program! Keep up the good work.

Had a small problem installing Flash on a fresh install of 7.10 x64 and just wanted to point it out in case anyone else ran into the same problem.

QuickStart v5 appeared to install the x64 Flash fine (no errors) however when checking Flash sites in Firefox (such as youtube.com), the Flash didn't work. Turns out I didn't have all the required dependencies for the Flash plugin to work. My system was missing the nspluginwrapper package. Upon installing this and reinstalling Flash from QuickStart, it worked like a charm.

Just wanted to put that out there in case anyone else is having problems.

Thanks,
Chris

---

### Post by mdpalow on 2008-01-11
my understanding was the nspluginwrapper was installed by default on 7.10 64-bit.

So, just to confirm I understand you correctly, you only had to install nspluginwrapper and then it worked.

I assume the code was:

sudo apt-get install nspluginwrapper

Please confirm for me and I'll update QuickStart.

Thanks... :)

---

### Post by money2themax on 2008-01-11
i honestly think that this program should come preinstalled on ubuntu and all of it's variation and debain and all it's variations

[yes i know ubuntu is a variation of debain]

:guitar:

---

### Post by crgutierrez on 2008-01-11
Got it
looks great
working fine for 32 bit
wil try 64 bit later
MUCHAS GRACIAS!!!!!!!!!!!!!!!!!

---

### Post by allforcarrie on 2008-01-11
Nice!!!

---

### Post by luke16 on 2008-01-12
This looks like a nice little backup program. I had to abandon sbackup because it was incredibly slow for some reason. I'm going to have to try this when I have time.

Can this do backups over networks such as ssh? Over windows network "smb"? Is anything excluded from full backups (/boot/ and /proc/ etc.)?

---

### Post by nyk52687 on 2008-01-12
Yup, thats correct mdpalow. There were also 3-4 dependencies for nspluginwrapper, but I was prompted automatically to install them.

Chris

---

### Post by mdpalow on 2008-01-12
> **luke16 said:**
> This looks like a nice little backup program. I had to abandon sbackup because it was incredibly slow for some reason. I'm going to have to try this when I have time.

Can this do backups over networks such as ssh? Over windows network "smb"? Is anything excluded from full backups (/boot/ and /proc/ etc.)?

Had someone test it on a Network and it worked, but have not done it myself. You should try it and let us know. :)

Also, yes - the typical folders/directories (mnt, proc, sys, trash, etc, etc) are excluded from the back-up.

---

### Post by mdpalow on 2008-01-12
> **nyk52687 said:**
> Yup, thats correct mdpalow. There were also 3-4 dependencies for nspluginwrapper, but I was prompted automatically to install them.

Chris

One more verification...

you only used:

```
sudo apt-get install nspluginwrapper 
```

and never typed in anything like below:

```
nspluginwrapper -i /home/YOURUSERNAME/.mozilla/plugins/libflashplayer.so
```

---

### Post by nyk52687 on 2008-01-12
Correct, I only used the apt-get line.

Chris

---

### Post by Polygon on 2008-01-12
nice program, i would seriously consider trying to get it in the ubuntu repos for hardy

---

### Post by altonbr on 2008-01-12
> **luke16 said:**
> This looks like a nice little backup program. I had to abandon sbackup because it was incredibly slow for some reason. I'm going to have to try this when I have time.

Can this do backups over networks such as ssh? Over windows network "smb"? Is anything excluded from full backups (/boot/ and /proc/ etc.)?

Don't forget mdpalow, I can help you get this to work via SSH (the dump especially, but you could even run this program remotely), especially for daily or weekly backups, fully encrypted, whether over LAN or WAN.

---

### Post by reubeni on 2008-01-12
Tried the ubackup today  all worked accept the backup option 1 it just hung my system even stopped the clock from running strange had to reboot to get anywhere anyone else have this problem?
All the other options worked fine using gutsy .:confused:

---

### Post by ugm6hr on 2008-01-12
Just downloaded and installed Quickstart 5.0.

Not used it yet - but wanted to say it looks very slick, and the options seem easy to understand.

Quite like the easy access to xorg etc... maybe worth considering offering the option to backup these files prior to editing (simple cp file.bkp to same directory would suffice).

I would also prefer it to appear in my Applications -> System Tools or System -> Administration menu system (cos I like my desktop clean), but that's no big deal...

Thanks for the hard work - if only I'd seen it when I first installed Gutsy!

---

### Post by mdpalow on 2008-01-12
> **ugm6hr said:**
> Just downloaded and installed Quickstart 5.0.

Not used it yet - but wanted to say it looks very slick, and the options seem easy to understand.

Quite like the easy access to xorg etc... maybe worth considering offering the option to backup these files prior to editing (simple cp file.bkp to same directory would suffice).

I would also prefer it to appear in my Applications -> System Tools or System -> Administration menu system (cos I like my desktop clean), but that's no big deal...

Thanks for the hard work - if only I'd seen it when I first installed Gutsy!


Thanks for your coments

The configuration files you're speaking of are backed-up to your desktop before you actually get to the editing part. Only when you're VIEWING any of the three files it doesn't back-up the file. Try it again and select the EDIT option and you'll have a copy placed on your desktop. :)

QuickStart 6.0 is about to be released as soon as I can get resolution on one issue. Not sure if it's a bug (works fine on my system) or if the beta tester has something wrong with their system and that's why it's not working as expected for them. In version 6.0 the icon has been moved from the Desktop to the main menu as you asked for...

However, I'm putting it in the APPLICATIONS -> ACCESSORIES menu because SYSTEM TOOLS is not turned on by default if I remember correctly. If I don't remember correctly, would someone please let me know as then I wouldn't have a problem with putting it there instead. I just don't want it in a menu that is not turned on by default and then have someone not be able to find it because they don't know to turn it on in the menu.

---

### Post by ugm6hr on 2008-01-12
Just tried to EDIT - and yes - my mistake - it does backup to Desktop.  Sorry...

And - you are right - System Tools only appeared in my menu after I installed a couple of programs.  Accessories seems like a sensible place for it to go to...

Thanks again :)

---

### Post by alnhntr29 on 2008-01-12
very cool, works flawlessly on freespire 2.0. About time somebody did this for linux. Thank You very much

---

### Post by mdpalow on 2008-01-12
> **alnhntr29 said:**
> very cool, works flawlessly on freespire 2.0. About time somebody did this for linux. Thank You very much

Very cool. Thanks...

---

### Post by DoctorMO on 2008-01-13
Programmers Error, This package fails to abide by one of the programming tennants for tools: "Do one thing only and one thing well."

Why is there a backup solution blended into a replacement for mediubuntu or one of the other "Install my codecs" apps? I fail to see how it makes sense to have these even in the same package.

---

### Post by mdpalow on 2008-01-13
> **DoctorMO said:**
> Programmers Error, This package fails to abide by one of the programming tennants for tools: "Do one thing only and one thing well."

Why is there a backup solution blended into a replacement for mediubuntu or one of the other "Install my codecs" apps? I fail to see how it makes sense to have these even in the same package.

[-o<

"Lord, please keep one arm around my shoulder, and one hand over my mouth."

---

### Post by mewzicman on 2008-01-13
Same problem here.  Tried it twice now and it does the same thing each time

---

### Post by mewzicman on 2008-01-13
> **reubeni said:**
> Tried the ubackup today  all worked accept the backup option 1 it just hung my system even stopped the clock from running strange had to reboot to get anywhere anyone else have this problem?
All the other options worked fine using gutsy .:confused:

Sorry, forgot the quote in the first message
Same problem here.  All options work except backup

---

### Post by corn13read on 2008-01-13
I think that this should be included in every ubuntu distro! This is a great app and just what ububntu needs for all of the newbs that are coming aboard that give up on it because they can't even get DVD's to play...

Great app great job! I do think that the addition of backup to remote location and choose method (ssh, ftp) would be great additions. I also think that adding the winehq repository and installing wine would also be really good maybe even associating with .exe files. There is also another top ten app or two that is needed besides wine. nautilus-image-converter and compizconfig-settings-manager.

---

### Post by money2themax on 2008-01-13
> **corn13read said:**
> I think that this should be included in every ubuntu distro! This is a great app and just what ububntu needs for all of the newbs that are coming aboard that give up on it because they can't even get DVD's to play...

Great app great job! I do think that the addition of backup to remote location and choose method (ssh, ftp) would be great additions. I also think that adding the winehq repository and installing wine would also be really good maybe even associating with .exe files. There is also another top ten app or two that is needed besides wine. nautilus-image-converter and compizconfig-settings-manager.
1 small problem in the US it's illigal to have a linux distro that can play DVD for what i've heard

---

### Post by corn13read on 2008-01-13
One more thing that is definately needed for first time ubuntu users is menu item for installing smb support and smbpasswd -a you can call it "simple file sharing"

---

### Post by corn13read on 2008-01-13
> **money2themax said:**
> 1 small problem in the US it's illigal to have a linux distro that can play DVD for what i've heard

I'd like to see someone try to prosecute a linux user for watching dvd's on his laptop... Besides we're not all in the us... :)

---

### Post by ugm6hr on 2008-01-13
> **money2themax said:**
> 1 small problem in the US it's illigal to have a linux distro that can play DVD for what i've heard

This program does not include the codecs - merely downloads them *if requested*.  Therefore, including this program is not an issue - it is up to the users to install the codecs, just as it is at present (with Synaptic etc).

I would agree that if you are looking for ideas to improve things as a Quickstart engine (rather than backup) - things to sort:
Windows Wireless Drviers / ndiswrapper (maybe just install ndis-gtk, altho it doesn't work that well)
Graphics cards (ATI / Nvidia drivers can be automated with Envy: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html))

Not complaining though!

---

### Post by reubeni on 2008-01-13
> **mewzicman said:**
> Sorry, forgot the quote in the first message
Same problem here.  All options work except backup

Yep tried it about 6 times with different options no compiz,no external drives or dongles and the program froze the system for hours the nearest I got to any joy was a 5hr stint of very slow activity and then I killed the system and went to bed that was after I killed conky.
It appears that the program hits the cpu so hard it can only process 1 file at a time 100% cpu usage 1g of swap  file and so little HD activity you could count the cycles very strange since what is supposed to be backed up is to and from the HD perplexed :confused:

---

### Post by mdpalow on 2008-01-13
> **corn13read said:**
> I think that this should be included in every ubuntu distro! This is a great app and just what ububntu needs for all of the newbs that are coming aboard that give up on it because they can't even get DVD's to play...

Great app great job! I do think that the addition of backup to remote location and choose method (ssh, ftp) would be great additions. I also think that adding the winehq repository and installing wine would also be really good maybe even associating with .exe files. There is also another top ten app or two that is needed besides wine. nautilus-image-converter and compizconfig-settings-manager.

Thanks for that. I had actually told myself some time ago that I need to add 'compizconfig-manager' because I kept forgetting the name. I will add it now...

---

### Post by alnhntr29 on 2008-01-13
I have a question, maybe you can answer it. I am running freespire 2.0. I have always had problems with getting a dvd to play, no matter what distro I have used. I used the install feature of quick start to install totem and the codecs. I was able to play burnt movies, but not store bought. What do I need to have to play encrypted dvd's?
Thanks in advance for your help.

---

### Post by mdpalow on 2008-01-13
Hi Everyone,

QuickStart 6.0 has been put on the server, so if you decide to update you'll now also be able to back-up/restore your MBR and Windows partition if you're dual-booting.

Also, for those who already have 6.0, please update QuickStart as I went to back-up my system today and realized it was also backing up my Windows partition back-up I had made the other day. Not cool to have a 10 gig back-up within a back-up! :) lol

I didn't think to add the windows_backup.img exclusion to the original back-up code. It's added now...

---

### Post by brucewagner on 2008-01-13
> **mdpalow said:**
> I just don't want it in a menu that is not turned on by default and then have someone not be able to find it because they don't know to turn it on in the menu.

Mdpalow, this is an example of the brilliance of your attention to detail which we all so appreciate.   

Some programmers have the technical know-how, and some can relate to the total newbie user.   But to be able to do BOTH --- as you can --- is a rare and precious talent.

Thanks so much for sharing your talent with the world!

And, yes, by all means....  Let's see if we can get QuickStart added to the Ubuntu repos for Hardy...    Who knows how to go about doing that?   It should be included in the Applications-->Add/Remove too.

---

### Post by OffHand on 2008-01-13
> **mdpalow said:**
> 
However, I'm putting it in the APPLICATIONS -> ACCESSORIES menu because SYSTEM TOOLS is not turned on by default if I remember correctly. If I don't remember correctly, would someone please let me know as then I wouldn't have a problem with putting it there instead. I just don't want it in a menu that is not turned on by default and then have someone not be able to find it because they don't know to turn it on in the menu.

I think that if you insert a menu item it will show up by itself. (If you uncheck all items the menu item will disappear. )

---

### Post by MaxVK on 2008-01-13
EEP! Something seems to be wrong!

I used the settings to back up my system, watched as a terminal type window opened and the names of the files being backed up began to scroll in it. I watched for a while and then went and watched the TV. When I came back the Quickstart window was on top, so I closed it, expecting the terminal window to close as well, but it didn't.

In fact its still there (45 mins and counting) with the last file showing as '/etc/hosts', and its still using CPU time etc.

Just in case anyone reads this in the meantime - Should I close this window? What else is there to do?

---

### Post by mdpalow on 2008-01-13
>  Originally Posted by reubeni
Tried the ubackup today all worked accept the backup option 1 it just hung my system even stopped the clock from running strange had to reboot to get anywhere anyone else have this problem?
All the other options worked fine using gutsy .

> **mewzicman said:**
> Sorry, forgot the quote in the first message
Same problem here.  All options work except backup

After trouble-shooting, we believe there may be a problem with the file system (i.e. corrupt perhaps). Running a simple tar command in a terminal produced problems that should not have occurred.

If anyone else has problems backing up their computer using Option 1 in QuickStart, please private message me and we can run some tests to see what the problem might be.

Thanks..

---

### Post by altonbr on 2008-01-13
> **alnhntr29 said:**
> I have a question, maybe you can answer it. I am running freespire 2.0. I have always had problems with getting a dvd to play, no matter what distro I have used. I used the install feature of quick start to install totem and the codecs. I was able to play burnt movies, but not store bought. What do I need to have to play encrypted dvd's?
Thanks in advance for your help.

Run this:
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo aptitude install libdvdcss2
```

It installs the Ubuntu **Gutsy** repositories for [Medibuntu](http://medibuntu.org/), updates your repositories and then installs **libdvdcss2**.

You might also want to look at the package **ubuntu-restricted-extras**.

---

### Post by mdpalow on 2008-01-13
> **MaxVK said:**
> EEP! Something seems to be wrong!

I used the settings to back up my system, watched as a terminal type window opened and the names of the files being backed up began to scroll in it. I watched for a while and then went and watched the TV. When I came back the Quickstart window was on top, so I closed it, expecting the terminal window to close as well, but it didn't.

In fact its still there (45 mins and counting) with the last file showing as '/etc/hosts', and its still using CPU time etc.

Just in case anyone reads this in the meantime - Should I close this window? What else is there to do?

LOL :)  ](*,)

Max... I really wish I had seen this message before spending all this time trying to figure out what's going on with your back-up. 

I'll repeat this again for everyone to see as this is not the first time this has appeared.

The Terminal windows that appear while doing a back-up are simply for you to be able to review the back-up once it has finished. They do not go away by default. If you don't care to review anything, you can close them at any time during or after the backup.

Unfortunately, I have not found a way to be able to put a short message in there, at the end, that says finished.

I will have to update the help wiki with this info - not that anyone probably reads it! lol

Max, thanks for being detailed in your post. It makes trouble-shooting a lot easier. Yes, you can close it. :)

---

### Post by mdpalow on 2008-01-13
> **altonbr said:**
> Run this:
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo aptitude install libdvdcss2
```

It installs the Ubuntu **Gutsy** repositories for [Medibuntu](http://medibuntu.org/), updates your repositories and then installs **libdvdcss2**.


QuickStart already does this for you ...

---

### Post by altonbr on 2008-01-13
> **mdpalow said:**
> QuickStart already does this for you ...

Just more of an advertisement for ya then ;)

I was merely answering that gentleman's question.

---

### Post by mdpalow on 2008-01-13
no problem... I'm having problems with my Internet today and trying to write short/quick messages before I lose connection again.

---

### Post by Polygon on 2008-01-14
im trying a backup now, will tell how it goes :D

---

### Post by caughran on 2008-01-14
Having a lot of trouble with this. It installs, creates a menu item, but the permissions are not there:
```
Failed to execute child process "/home/jim/QuckStart/QuickStart" (Permission denied)
```

I went to the QS folder and overdid permissions:
jim@JIMJANET:~/QuickStart$ ls -l
```
total 96
-rwxrwxrwx 1 jim jim 83072 2008-01-13 23:31 QuickStart
-rwxrwxrwx 1 jim jim   257 2008-01-14 11:00 QuickStart.desktop
-rwxrwxrwx 1 jim jim   947 2008-01-13 23:31 READ_ME

```

No better. 

Worse, some other things don't work which worked before:
```
jim@JIMJANET:~/Desktop$ ./runQuackle.sh
bash: ./runQuackle.sh: /bin/sh: bad interpreter: Permission denied

jim@JIMJANET:~/Desktop$ ./zyzzyva-1.desktop
bash: ./zyzzyva-1.desktop: Permission denied
```

Those things work, however, by clicking on them, which QS doesn't.

I discovered that the /usr/share/applications QS desktop item didn't have execute permissions, but adding them did not help.

What did I screw up?

---

### Post by mdpalow on 2008-01-14
Seems there's a few more people recently experiencing problems with QuickStart then in past releases. It got me thinking perhaps something might have been changed in the code and is causing these problems.

So here's what I did:

1. I just finished formatting my laptop hard drive.

2. re-installed Ubuntu 7.10 / 32-bit clean w/ Live CD

3. Came to this thread and downloaded the Install_QuickStart.sh file

4. Ran the install file

5. Selected the QuickStart icon from the menu

6. QuickStart loaded fine

7. Selected 'Create a Back-Up'

8. Selected all three boxes/back-ups and ran it

For those of you who know how QuickStart works - All three back-ups are now sitting on my desktop and are accessible. Meaning... it worked fine.

I did not install anything to Ubuntu. I literally ran QuickStart after rebooting Ubuntu. I didn't even install updates or restricted drivers.

I also ran:

Option 13 (Install Java 6) just to further test other options.. and:

1. Terminal window appeared as expected

2. I entered my password

3. QuickStart began downloading and installing Java

4. Java is loaded and icon is sitting in my menu

So, I guess bottom line is QuickStart is working as expected.

I did however find a bug in Option 14, which finally explains why a beta tester was having problems. QuickStart does what it's supposed to do, but it doesn't actually attempt the task because the file it wants to edit doesn't exist. When I wrote the code, it did exist, but what I think I've learned is the file doesn't exist initially after an install or at least not until something else is done first to create the file. I always use this function after a install, so the file always existed for me when I started writing this module in QuickStart.

Since I thought the beta tester's computer/file system might have been different, I wrote it so QuickStart looks for the file and if not found pops-up a message saying 'not found' and then takes you back to main menu. That's what it did for me after a clean install.

I'm going to format my laptop again and re-install just to make sure the file doesn't exist on install and then re-code to accommodate.

Thanks....

---

### Post by brucewagner on 2008-01-14
mdpalow,

A Suggestion:

Since some people are using QuickStart in conjunction with a fresh Ubuntu install -- just to get DVD, Java, codecs.... installed quick & easy...

And others are using it to Backup & Restore their system(s)....

Perhaps it would make sense to display two sections on the Main Menu.....

One, at the top, called something like "New Ubuntu Install Musts"..... which would include the DVD, codecs, Java, Wine, etc. 

And a second section called "Backup & Restore"...

This way, the absolute total novice user would be VERY CLEAR which options they are to run on a new install...

Make sense?

---

### Post by Polygon on 2008-01-14
> **Polygon said:**
> im trying a backup now, will tell how it goes :D

my backup worked, and seems to be 3 gb smaller then backups created with sbackup. Good work!

---

### Post by mdpalow on 2008-01-14
Hi Everyone,

Ok, now that I know the %conf.xml file doesn't exist in desktop with a new install, I was able to recode Option 14 (Show/Hide Desktop Icons) so it should work for everyone.

I just ran about 5 or 6 tests and appears to work nicely now even if the file hasn't been created by your system yet.

If it already has been created and exists then QuickStart will forgo the creation of it and simply edit the one you already have.

Update is on the server.. you only need to use Option 16 on QuickStart to update your software.

thanks...

---

### Post by tobydeemer on 2008-01-14
Hi all-

mdPalow-

I've been using Gutsy for a few months now, and when I first started I had a few newb hiccups like everyone does- bad experience with Automatix and Envy, ATI card freaking out when I hooked up a second monitor (and crashed my screen setup...) so I've done my share of reinstalls. 

But I've been stable now for about three months. (Without trying another second-monitor-hookup.)

But I have NOT been able to get DVD playback to work properly. 

I found your program in the forums, and it is a beautiful piece. A godsend, especially since I was looking for a good backup tool as well. So here's the thing- DVD playback starts to work, but when I click on "play" on the DVD screen menu, Totem freezes, and I have to force quit, and then it refuses to start again until I reboot. Rrrg...

I'm running AMD Turion 64bit, ATI Radeon card, 1GB RAM, 80GB HD dual boot with XP. 

Thanks for any help, and also for the great program. Really awesome job.

-toby

---

### Post by Het Irv on 2008-01-14
Is there a way for me to get an offline version of the install files.  It is not easy for me to get a wired connection to my main computer and I would like a way to install QuickStart on my computer and run a restore without having to hook up to the internet.

---

### Post by mdpalow on 2008-01-14
Hi Toby,

Thanks for the kind words.

I'm sorry that I can't be of any help to you on this question. I'm actually chatting with a friend right now who has an ATI and I remember him going through some problems with totem and his ATI drivers.

However, I would recommend you post parts of this message into another post in the [Multimedia & Video forum]("http://ubuntuforums.org/forumdisplay.php?f=138"). You'll probably get a good answer there as those guys are pretty smart about all that stuff.

Good luck and thanks again...

---

### Post by mdpalow on 2008-01-14
> **Het Irv said:**
> Is there a way for me to get an offline version of the install files.  It is not easy for me to get a wired connection to my main computer and I would like a way to install QuickStart on my computer and run a restore without having to hook up to the internet.

Not sure what you mean by an off-line version, but you already have everything you need to run QuickStart on any computer. There is no real "INSTALL" when you download the program. All you're doing is downloading three files and QuickStart makes a directory for them and then puts them in the folder. Not really a whole lot more than that going on. Just copy the QuickStart folder and you have everything you need. :)

Hope that answers your question...

---

### Post by Het Irv on 2008-01-14
Duh. Sorry I stopped thinking with my Linux brain for a little bit sorry about that.

I don't know if you care to know this but I just ran a full backup (19.9G of data) and the total size of the finished backup was 1.9G

That be 10% the original size.  Good Job.

Edit: 10.2Gb of Data was backed up

---

### Post by tobydeemer on 2008-01-14
> **mdpalow said:**
> Hi Toby,

Thanks for the kind words.

I'm sorry that I can't be of any help to you on this question. I'm actually chatting with a friend right now who has an ATI and I remember him going through some problems with totem and his ATI drivers.

However, I would recommend you post parts of this message into another post in the [Multimedia & Video forum]("http://ubuntuforums.org/forumdisplay.php?f=138"). You'll probably get a good answer there as those guys are pretty smart about all that stuff.

Good luck and thanks again...


Ah well, thought I'd ask. I did create a back up though, and it went really quickly and smoothly, and was not too  big. Fit onto a 2GB flash drive. Great job.

---

### Post by mdpalow on 2008-01-14
>  Originally posted by: corn13read

Great app great job! I do think that the addition of backup to remote location and choose method (ssh, ftp) would be great additions.

Thanks...

I think what you're referring to is a program 'altonbr' is working on. You can find his name by doing a search and I think he has a link to this program in his signature.

Worth a look see... :)

thanks...

---

### Post by Mithrilhall on 2008-01-14
[http://synkron.sourceforge.net/](http://synkron.sourceforge.net/)

---

### Post by mitsugiri on 2008-01-14
Hi mdPalow,
This is a great piece of software.  Now if I can only get it to work the way I want it to....

I want to do a complete backup of the system but exclude some volumes that are mounted like /data1 and /data2 that have my media files that are huge and already backed up somewhere else.  When I select option 1 to do a partial backup, it gives me the choice to select folders to backup but when I select the ones that I want and hit enter, it backs up everything, even the volumes that I do not want it to backup? I just want to be able to bring my system back up with all the customizations and all the extra packages if I have installed. 

How can I achieve this?  I have found that option 3 works with only the selected folders but when it comes time for a system restore how do I know I have everything backed up as far as Ubuntu and the packages are concerned?

Thanks for your help and this great software contribution.

---

### Post by mdpalow on 2008-01-15
> **mitsugiri said:**
> Hi mdPalow,

I want to do a complete backup of the system but exclude some volumes that are mounted like /data1 and /data2 that have my media files that are huge and already backed up somewhere else.  When I select option 1 to do a partial backup, it gives me the choice to select folders to backup but when I select the ones that I want and hit enter, it backs up everything, even the volumes that I do not want it to backup?

How can I achieve this?  I have found that option 3 works with only the selected folders but when it comes time for a system restore how do I know I have everything backed up as far as Ubuntu and the packages are concerned?

Thanks for your help and this great software contribution.

I think you misunderstood the pop-up window that explains how to exclude folders during a /home back-up. :)

When you make a back-up of /home you are allowed to select folders you _do NOT want to back-up_; not folders you want to back-up. In other words, QuickStart is going to back-up your entire /home directory, but before it starts, it's going to afford you an opportunity to tell it which folders you want to EXCLUDE from the back-up.

So, try a /home back-up again and this time look for the pop-up that appears and talks about EXCLUDING folders. Once that pop-up goes away and the file browser comes up, press and hold the CTRL key on keyboard and then click on /data1 and /data2. Now, EVERYTHING except those folders will be backed-up. QuickStart has the EXCLUDE feature built into the /home back-up module exactly for the reason you mention. Sometimes we have huge folders that are already backed-up elsewhere and don't want to include them in our system back-up.

You definitely do NOT want to use option three for a system back-up.

Hope this helped you... let me know if not.

...

---

### Post by mitsugiri on 2008-01-15
In my case, /data1 and /data2 are separate partitions that are mounted and not in the /home directory.  When I use option 1, does it only allow me to exclude directories in the /home or can I also exclude directories from the root?

Alternatively, would this work if I were to back up  /home only first and then do the / directory on a second pass?

The other thing that I just thought of is what if I were to unmount the /data1 and /data2 volumes before doing the backup?

Thanks

---

### Post by mdpalow on 2008-01-15
> **mitsugiri said:**
> In my case, /data1 and /data2 are separate partitions that are mounted and not in the /home directory.  When I use option 1, does it only allow me to exclude directories in the /home or can I also exclude directories from the root?

Alternatively, would this work if I were to back up  /home only first and then do the / directory on a second pass?

The other thing that I just thought of is what if I were to unmount the /data1 and /data2 volumes before doing the backup?

Thanks

Just as your message came in I was keying in on the word "Volumes" and then suspected you were talking about partitions outside of the /home directory. Sorry... 

Yeah, when you're doing a back-up of /home you can only exclude folders within /home because it's not going outside of /home. Unfortunately, the / back-up does not give you the option to exclude folders or partitions.

However, aren't the /data1 and /data2 in your /media folder? If so, they wouldn't get backed up even with a / back-up as this folder (/media) is excluded by default since we don't typically want to back-up other volumes or cd-roms, etc, etc..

Let me know...

---

### Post by mdpalow on 2008-01-15
> **mitsugiri said:**
> In my case, /data1 and /data2 are separate partitions that are mounted and not in the /home directory.  When I use option 1, does it only allow me to exclude directories in the /home or can I also exclude directories from the root?

Alternatively, would this work if I were to back up  /home only first and then do the / directory on a second pass?

The other thing that I just thought of is what if I were to unmount the /data1 and /data2 volumes before doing the backup?

Thanks

Was just looking at QS /home back-up and wondering why /data1 and /data2 would even show up in your /home folder IF they are in fact separate volumes. Don't those two volumes show up on the left hand side of the file browser beneath and SEPARATE from your /home/your_name folder?

They shouldn't be even looked at by QuickStart during a /home back-up...

Assuming I'm following you right and understand all this... when you do a /home back-up - QuickStart only backs up files that are in /home and nothing outside of this folder. Now let me just say your name is John for example purposes and because I don't know your login name... if you do a /home back-up, QuickStart will do a back-up of /home, but allow you to exclude folders within /home/john. Anything outside of /home should not even come into play for the back-up.

Am I helping any or am I missing your point completely?

Thanks...

---

### Post by mitsugiri on 2008-01-15
> **mdpalow said:**
> Was just looking at QS /home back-up and wondering why /data1 and /data2 would even show up in your /home folder IF they are in fact separate volumes. Don't those two volumes show up on the left hand side of the file browser beneath and SEPARATE from your /home/your_name folder?

They shouldn't be even looked at by QuickStart during a /home back-up...

Assuming I'm following you right and understand all this... when you do a /home back-up - QuickStart only backs up files that are in /home and nothing outside of this folder. Now let me just say your name is John for example purposes and because I don't know your login name... if you do a /home back-up, QuickStart will do a back-up of /home, but allow you to exclude folders within /home/john. Anything outside of /home should not even come into play for the back-up.

Am I helping any or am I missing your point completely?

Thanks...

Sorry!
I did not make myself clear.  The home folder backs up fine.  It's the other partitions that are mounted as /data1 and /data2 under the filesystem that I was trying to exclude when I did a / (root?) directory  backup.   I have these extra partitions mounted as /data1 and /data2.  
I am going to try your suggestion and mount those partitions under the /media directory and that should take care of the problem.

The only thing is that I've never changed a mounting point so I hope I don't screw things up.  I've been doing some searching and it seems the best way to do it would be to boot up using the live cd and change the mounting points using gparted.

Could anybody confirm this?

Thanks

---

### Post by mitsugiri on 2008-01-15
My problem above is solved.  A big thank you to Mdpalow.   Like he suggested, I ended up remounting my extra partitions under /media which is where it should have been in the first place. Because I am a FOWB (fresh of the Windows boat) and don't really know enough about the linux file system, when I installed Ubuntu I manually gave those partitions those mount points instead of letting the Ubuntu installation handle it.  Thus I ended up with the partitions as separate mount points under the / directory.  

This was a problem when I tried to use Quickstart to do a complete system backup because it would back everything up under the / directory even my huge data partitions.  Moved the partitions under /media,  Quickstart ignores it and problem solved.

Thank you again Mdpalow.

---

### Post by mdpalow on 2008-01-15
=D>

well done...

---

### Post by mikprice on 2008-01-16
Hi There

I have tried this on 32bit Ubuntu 7.10 but I still get the problem in Totem whereby it complains about libdvdcss being required. Any thoughts?

---

### Post by mdpalow on 2008-01-16
> **mikprice said:**
> Hi There

I have tried this on 32bit Ubuntu 7.10 but I still get the problem in Totem whereby it complains about libdvdcss being required. Any thoughts?

QuickStart does install libdvdcss2, so it should be good, but you could try it again in a terminal window with:

```
sudo apt-get install libdvdcss2
```

---

### Post by alnhntr29 on 2008-01-16
I posted about getting this to run on freespire, well I switched to the 7.10 version of Kubuntu. I installed correctly but, when I click on the icon I just get an icon bouncing for a minute,(which is what kde does when you open a program, and it never starts. Any ideas?

---

### Post by mdpalow on 2008-01-16
> **alnhntr29 said:**
> I posted about getting this to run on freespire, well I switched to the 7.10 version of Kubuntu. I installed correctly but, when I click on the icon I just get an icon bouncing for a minute,(which is what kde does when you open a program, and it never starts. Any ideas?

I'm sorry, but I really don't know anything about Kubuntu as I've never used it. Maybe someone in this thread has some experience with it and can share.

Anyone...?

---

### Post by OffHand on 2008-01-16
> **alnhntr29 said:**
> I posted about getting this to run on freespire, well I switched to the 7.10 version of Kubuntu. I installed correctly but, when I click on the icon I just get an icon bouncing for a minute,(which is what kde does when you open a program, and it never starts. Any ideas?

Try to run it from the terminal and see if you get a traceback

---

### Post by tobydeemer on 2008-01-16
mdPalow-

I tried to create a Windows image backup, and Quickstart asks me to install required files first. Which files do I need to install? So far everything else works great.

---

### Post by mdpalow on 2008-01-16
> **tobydeemer said:**
> mdPalow-

I tried to create a Windows image backup, and Quickstart asks me to install required files first. Which files do I need to install? So far everything else works great.

Theres a checkbox to select that option, which will install the necessary files for you. Just select it and click OK.

---

### Post by tobydeemer on 2008-01-16
Um... oh. Duh. 

Tonight's not been my best Linux night, that's for sure. Oy.

---

### Post by mdpalow on 2008-01-16
:)  No problem... it happens...

---

### Post by Horrendus01 on 2008-01-16
Just got it, worked like a charm.  Thanks

---

### Post by fairb on 2008-01-17
Just found this, sounds great.  Cant wait to try it.  Surely every PC sold and distro should have something this comprehensive to get users started.

---

### Post by mitsugiri on 2008-01-17
> **fairb said:**
> Surely every PC sold and distro should have something this comprehensive to get users started.

Totally agree with you. I recently switched to Ubuntu from Windows. So for a newbie like me who is just exploring I consider this a must-have script.  I've gotten my Ubuntu Gutsy install and some essential packages to a point where everything is working.  I've just backed up my system with QuickStart 6.0 and now I have the confidence to go and play around with Ubuntu and not worry about starting from scrath if I mess anything up. 

mdpalow, at the very least, I think there should be a link in the Absolute beginners'sticky threads for this script so that other newbies can get a good start on the Linux path. 

For beginners who may be on this thread, just go to the very first post of this thread and follow the directions on the install and you should be good to go.  Very easy to install and use and a very useful script.  Thanks again mdpalow

---

### Post by mdpalow on 2008-01-17
Some time ago and after several suggestions to do just that, I wrote a moderator and asked if it would be possible and the answer I got was 'No' because it's not a written out "HowTo," but instead a program that runs for you. I think I remember him saying also because it was a third party program it wouldn't be allowed.

I don't know....:roll:

---

### Post by mdpalow on 2008-01-17
> **alnhntr29 said:**
> I posted about getting this to run on freespire, well I switched to the 7.10 version of Kubuntu. I installed correctly but, when I click on the icon I just get an icon bouncing for a minute,(which is what kde does when you open a program, and it never starts. Any ideas?

I downloaded Kubuntu to see what was going on. When you said it installed correctly, I'm not so sure. The _install file_ checks for zenity in your system and if not found requires you to enter your password to download. In Kubuntu, even after changing the permissions, I didn't get a 'Run in Terminal' option. I did find this option, but couldn't get it to work as expected. I'm thinking you don't have zenity installed, which you must have or QuickStart won't work.

So, I installed zenity manually (sudo apt-get install zenity) and QuickStart came up right away; no problem. However, I'm seeing some differences in the Kubuntu file structure that will make some options in QuickStart not work properly. I haven't tested them all, but I think it's safe to say that QuickStart won't work optimally with Kubuntu unless some changes are made to the code. One example is in Ubuntu - 'gedit' is used to edit text files, but in Kubuntu I believe it's 'Kate' that is used. I also didn't find the /boot folder in /etc, so I don't know if it's somewhere else or just not there because I'm running the Live CD only right now. If /etc/boot... isn't there in a real install then one of the back-up functions and the view/edit config files options won't work properly.

I'll have to look at this some more...

---

### Post by mdpalow on 2008-01-17
Hi Everyone,

Not many questions these past couple days/nights and it's given me a little time to review QuickStart.

I found an oversight since adding the ability to back-up a Windows partition. I failed to add the Windows back-up file as an exclusion to a SCHEDULED BACK-UP, which means IF you SCHEDULED a back-up it will back-up your Windows partition as well if the file is located anywhere in your Ubuntu File System. That's really not good to have your back-up back-up a back-up! ;) A bit redundant, right...

So, if you've backed up your Windows partition (dual booters) AND you've scheduled a back-up, you'll want to run the scheduled back-up again. However, you don't have to run all of it again. You can exit QuickStart right after it tells you that it's building your schedule files as this is the file that will be recreated and overwrite any previous one you have and fix the oversight.

QuickStart update is already uploaded to server. You can click Option 16 to update your software.

Thanks...

---

### Post by reubeni on 2008-01-18
After the 1st install of QS on my system did not work I did a complete install with reformat of /& home partions both using ext3 I noticed some huge space on both about 6g in total that would not go away.
Anyhow proceeded with the install when done after reboot looked at drives and found a folder on each called lost&found so deleted them and that caused another install because it crashed the system.
So after some investigation reformatted again this time using reiserfs file system reinstalled everything started QS and 25mins latter backup was complete.
ext3/2 are not very robust FS and they leave alot of data locked up in those2 files in hind sight maybe I should have just deleted the files not the folders
Many thanks mapalow for the great QS and the learning tree.:wink:

---

### Post by dje on 2008-01-18
A few questions about Quickstart....

[LIST=1]
[*]Why does it install to your home folder?
[*]Why not provide the source code, why a binary file?
[/LIST]

Thanks

---

### Post by lespaul_rentals on 2008-01-18
> **dje said:**
> Why not provide the source code, why a binary file?

He gave us the source in the first post of this thread.

I looked it over and I must say it looks very good!  Nice job, and thanks for your contribution!  =D>=D>=D>

---

### Post by dje on 2008-01-18
> **lespaul_rentals said:**
> He gave us the source in the first post of this thread.

The installer or the actual program? I'm not intending to be horrible i'm just wondering.

---

### Post by altonbr on 2008-01-18
> **dje said:**
> The installer or the actual program? I'm not intending to be horrible i'm just wondering.

It wouldn't possibly be because you have a backup script running as well, would it? [http://ubuntuforums.org/showthread.php?t=574176](http://ubuntuforums.org/showthread.php?t=574176)

He said he's not releasing the source code at the moment because of the dangerous implications of modifying the code and destroying your hard drive...

---

### Post by dje on 2008-01-19
No i would **not** intend to copy any of his program for mine i would just be interested to see how his worked. I understand why he doesn't release it now. How do you make those binary files from scripts anyways? I apologise if anyone got the wrong message, quickstart is a very well thought out and useful program

---

### Post by ubukool on 2008-01-20
Hi mdpalow,

Thanks for a wonderful way of backing up my system.  I've been using it for some time now, but this morning I used the automatic update feature to get quickstart 6, and then tried to backup my system as usual, but I ran into some problems.  When I started the backup, my system started to 'slow down' and the backup seemed to be taking so many resources that my display would update intermittently, and eventually even the cursor wouldn't move!  The system came to a complete standstill before it had even finished the backup.  I've tried to repeat this several times, always with the same result - a complete 'freeze' and reboot required.

Any idea what might be happening? :)  Thanks for any help.  I'd really like to keep using Quickstart.

---

### Post by supersnoop on 2008-01-20
Fantastic-Many Thanks

---

### Post by rrr0321 on 2008-01-21
This is an excellent program for performing many tasks. Many thanks for your hard work and sharing with the community!

---

### Post by Het Irv on 2008-01-21
How hard is it to compile something into a .deb?  Your current method of distributing this program is great but a .deb would make it easier to get it into the 8.04 Repos.  Wouldn't it?  Or am I way off the mark?

---

### Post by sonofabics on 2008-01-22
Thanks for sharing it! great work!

=D>

---

### Post by mdpalow on 2008-01-22
> **ubukool said:**
> Hi mdpalow,

Thanks for a wonderful way of backing up my system.  I've been using it for some time now, but this morning I used the automatic update feature to get quickstart 6, and then tried to backup my system as usual, but I ran into some problems.  When I started the backup, my system started to 'slow down' and the backup seemed to be taking so many resources that my display would update intermittently, and eventually even the cursor wouldn't move!  The system came to a complete standstill before it had even finished the backup.  I've tried to repeat this several times, always with the same result - a complete 'freeze' and reboot required.

Any idea what might be happening? :)  Thanks for any help.  I'd really like to keep using Quickstart.

We've had some mention since 6.0 came out about resources being too high on some lower end computers, but this posting got me really looking at it again. It seems for the most part people are not having a problem with it and even my computer gets through it with no problem... however, in the interest of making QuickStart a better OVERALL back-up solution for those who really need/want it, I made a minor change that seems to have fixed the problem. Basically, all I did was insert a short (1 second) sleep cycle into the terminal window as it displays your files being backed up. I sent a custom update to 'ubukool' and they quickly reported back to me that it solved his issue.

I did notice however that adding the one second sleep interval did allow the resource to be released easier once the back-up was complete, so I _think_ this fix will be permanent. Personally, I like to see the files being backed up scroll continuously, but since resources are a bigger concern, I can live with the 1 second pause in display.

If you choose to update and perform a back-up, you'll see what I mean if I'm not being very clear above.

Thanks very much to 'Ubukool' for his involvement in this...

---

### Post by n2stc on 2008-01-22
Pretty slick!  Thanks.\\:D/

---

### Post by brucewagner on 2008-01-22
**Stupid Question of the Day**

How does the backup using QuickStart compare with the other backup programs available under Applications-->Add/Remove....  

For example:

[LIST]
[*]Simple Backup
[*]Home User Backup
[/LIST]
Just wondering what the differences are...

---

### Post by zorro123 on 2008-01-23
Thanks for this program.

---

### Post by ugm6hr on 2008-01-24
Just wanted to say I finally used the restore facility for /home, which has worked flawlessly.

Basically, I wanted a bit of room on my HD temporarily to allow me to compile a custom kernel (don't ask!), and thankfully, all my files are returned to their original position afterwards.  Most concerned about my thunderbird emails - but everything is as it was.

                                                                                                 :guitar:

---

### Post by brucewagner on 2008-01-24
Another Question:    When QuickStart backs up the /home directory....  and it requires multiple DVDs....  

Is there any way to be able to tell how many blank DVDs it will need?

Does it fill the DVD entirely -- slicing the data -- to maximize the storage on each DVD?

For example, my home directory contains 256.4 GB right now.

---

### Post by Mze on 2008-01-24
There's no way I would contemplate backing 256.4 GB to DVD. Even if the data was compressed to 1/2 the original size that would be over 100 GB and you would need 25 DVDs approximately. Who has the time to watch 25 DVD's burn? 

Consider an external hard drive for the price these days, that would be your better option.

---

### Post by CanonKen on 2008-01-25
> **brucewagner said:**
> Another Question:    When QuickStart backs up the /home directory....  and it requires multiple DVDs....  

Is there any way to be able to tell how many blank DVDs it will need?

Does it fill the DVD entirely -- slicing the data -- to maximize the storage on each DVD?

For example, my home directory contains 256.4 GB right now.
Likes been said above an external hard drive would be better but if you have to burn it to DVD's I'd create a new directory in home, back it all up to DVD's then exclude that directory when you use Quickstart again

---

### Post by bw44 on 2008-01-25
> **mdpalow said:**
> ...IF you SCHEDULED a back-up it will back-up your Windows partition as well if the file is located anywhere in your Ubuntu File System. That's really not good to have your back-up back-up a back-up! ;) A bit redundant, right...

So, if you've backed up your Windows partition (dual booters) AND you've scheduled a back-up, you'll want to run the scheduled back-up again. However, you don't have to run all of it again. You can exit QuickStart right after it tells you that it's building your schedule files as this is the file that will be recreated and overwrite any previous one you have and fix the oversight.

So I finally sprung for an external hard drive -- sorry I couldn't do it in time to help beta-test your Windows partition backup function. But now I'm ready to try it. Just a couple of questions first (I searched the thread for answers -- sorry if I missed any):

1.  My new HD is formatted Fat32 -- should it be formatted to NTFS before running Option 6 (Back-up and Restore Windows)?  I don't intend to use the HD with XP, except to back it up with your procedure.

2. What (in general terms if not specifics) are the "required files" that have to be installed before doing the Windows backup? (I just like to have some idea of what's going under the hood!)

3. In your message above you mention "if the backup file is located anywhere in the Ubuntu file system."  I just want to be sure I understand this:  I back up my Windows partition (that's on my internal HD) to my external HD (which, being a USB device is not "permanently" mounted); then I schedule an (Ubuntu) system  backup.  This backup wouldn't include the the Windows partition backup on the external HD, would it?  I wasn't sure if "Ubuntu file system" technically includes things on removable devices.

Thanks very much.
bw44

---

### Post by mdpalow on 2008-01-25
> **bw44 said:**
> 

1.  My new HD is formatted Fat32 -- should it be formatted to NTFS before running Option 6 (Back-up and Restore Windows)?  I don't intend to use the HD with XP, except to back it up with your procedure.

2. What (in general terms if not specifics) are the "required files" that have to be installed before doing the Windows backup? (I just like to have some idea of what's going under the hood!)

3. In your message above you mention "if the backup file is located anywhere in the Ubuntu file system."  I just want to be sure I understand this:  I back up my Windows partition (that's on my internal HD) to my external HD (which, being a USB device is not "permanently" mounted); then I schedule an (Ubuntu) system  backup.  This backup wouldn't include the the Windows partition backup on the external HD, would it?  I wasn't sure if "Ubuntu file system" technically includes things on removable devices.

Thanks very much.
bw44

Hi bw44,

No, your new hard drive doesn't need to be formatted FAT/NTFS in order to write/store your Windows back-up. I keep all my back-up files on my EXT3 file system.

There are 2-4 files installed (I can't remember right now), but they are nothing more than compatibility files that allow your Ubuntu to work with Windows. At least one or two of the files is already installed by default with Ubuntu 7.10 and I just have QuickStart install it for individuals who may not have it for some reason on their computer.

No, it wouldn't back-up your Windows back-up. It wouldn't do so regardless of where you have it now as I updated the code to ignore the back-up to begin with. However, to answer your question - your USB HD is probably mounted to /media/xxxxxx and if so, that folder is excluded from back-ups anyway. Just make sure your new HD is mounted to /media (should be anyway), so that if you ever did have it on and a scheduled back-up occurred it didn't back-up that drive as well.

Congrats on the new HD...

---

### Post by bw44 on 2008-01-25
> **mdpalow said:**
> Hi bw44,

No, your new hard drive doesn't need to be formatted FAT/NTFS in order to store your Windows back-up. I keep all my back-up files on my EXT3 file system. 

Thanks for the super-fast response and the clear answers to my questions.

But what you said above just raised another question:  should I get Ubuntu to format the external HD as EXT3?  Does this question make sense?  Would I use the Partition Editor? Guess that's 3 questions!:)

Cheers,
bw44

---

### Post by mdpalow on 2008-01-25
> **bw44 said:**
> Thanks for the super-fast response and the clear answers to my questions.

But what you said above just raised another question:  should I get Ubuntu to format the external HD as EXT3?  Does this question make sense?  Would I use the Partition Editor? Guess that's 3 questions!:)

Cheers,
bw44

Sounds like what I would do. 

I would bring up gParted, find the CORRECT hard drive, probably have to umount it first, then select format/EXT3, and then apply.

unmounting and selecting format can be done using right-click on mouse when hovering over drive info with your mouse.

Just remember that gParted will show you your first drive by default when it comes up. You have to click icon in top right corner to select other hard drives. Please just make sure you have the correct HD selected when formatting. :) You can usually tell by size of drive displayed in gParted or even the current file system. In your case, it should say FAT.

---

### Post by bw44 on 2008-01-25
> **mdpalow said:**
> Sounds like what I would do. 

I would bring up gParted, find the CORRECT hard drive, probably have to umount it first, then select format/EXT3, and then apply.

unmounting and selecting format can be done using right-click on mouse when hovering over drive info with your mouse.

Just remember that gParted will show you your first drive by default when it comes up. You have to click icon in top right corner to select other hard drives. Please just make sure you have the correct HD selected when formatting. :) You can usually tell by size of drive displayed in gParted or even the current file system. In your case, it should say FAT.

Super - and thanks for the cautions!

bw44

---

### Post by bw44 on 2008-01-25
> **mdpalow said:**
> Sounds like what I would do. 

I would bring up gParted, find the CORRECT hard drive, probably have to umount it first, then select format/EXT3, and then apply.

unmounting and selecting format can be done using right-click on mouse when hovering over drive info with your mouse. Everything smooth as silk so far:  HD re-formatted to EXT3, MBR and XP partition backed up. 

But while QuickStart had no problem writing to the external HD, I don't seem to be able to now! :(

When I put in a SDram chip the system automatically mounts it and permits me to read and write to the device.  Is this because it's a FAT32 device/partition?  Before I reformatted the HD from FAT32 to EXT3 I could write to it.  How do I set the permissions for the EXT3 device.  It must be in the disk Properties>Volume>Settings tab but what should the Mount Options be?

Thanks in advance.
bw44

PS. the current mount options are: rw nosuid nodev data=ordered

---

### Post by mdpalow on 2008-01-25
sounds like you're not mounting the drive properly in your fstab file, but you'll have to post this question in the forum for help. I don't have a USB drive that is formatted EXT3; mine is formatted NTFS. My EXT3 drives are all internal. Sorry I can't be of more help to you...

---

### Post by bw44 on 2008-01-25
> **mdpalow said:**
> sounds like you're not mounting the drive properly in your fstab file, but you'll have to post this question in the forum for help. I don't have a USB drive that is formatted EXT3; mine is formatted NTFS. My EXT3 drives are all internal. Sorry I can't be of more help to you...

OK, thanks.  (Why did you format your external USB drive NTFS -- is that where your Windows system(s) live?)

bw44

---

### Post by mdpalow on 2008-01-25
> **bw44 said:**
> OK, thanks.  (Why did you format your external USB drive NTFS -- is that where your Windows system(s) live?)

bw44

No, it was an internal HD with NTFS on it before. I think I have an EXT3 partition on it, but I really don't use it, so I don't even know. It's never even turned on.

My Windows partition is on my first HD (SDA1) and my back-up for it is on SDA2 (EXT3) and SDB1 (EXT3). I keep two back-ups of everything on two separate HD's.

---

### Post by Polygon on 2008-01-25
hey, is there any way to create incremental backups with this program? i cant seem to find an option for it.

---

### Post by bw44 on 2008-01-26
> **mdpalow said:**
>  I keep two back-ups of everything on two separate HD's.  That's impressive!

---

### Post by corn13read on 2008-01-26
I think it would be cool for backups to have the option to repeat at a certain time. 

If you wanted to make this easy on new users easiest way for you would be to ask for the timing and have the script first install gnome-schedule and then load it in there so if they wanted to remove it in the future you could just instruct them to go to applications -> system tools -> schedule to see the added backup tasks. 

Maybe even with an estimated time for local disks vs. removable disks based on size and speed.

Just a thought.

---

### Post by mdpalow on 2008-01-26
> **Polygon said:**
> hey, is there any way to create incremental backups with this program? i cant seem to find an option for it.

Not with QuickStart because incremental back-ups can only be done with TAR if you don't compress the file, which QuickStart does.

Maybe something I need to look at again, since I'm sure a lot of people probably would like the option of doing this. I'm on the fence about whether or not I want/need it personally, but it shouldn't be too hard to add at all.

Thanks for the suggestion...

---

### Post by mdpalow on 2008-01-26
> **corn13read said:**
> I think it would be cool for backups to have the option to repeat at a certain time. 

If you wanted to make this easy on new users easiest way for you would be to ask for the timing and have the script first install gnome-schedule and then load it in there so if they wanted to remove it in the future you could just instruct them to go to applications -> system tools -> schedule to see the added backup tasks. 

Maybe even with an estimated time for local disks vs. removable disks based on size and speed.

Just a thought.

Thanks for the suggestion corn..,

Open QuickStart and click on Option 4 (Scheduled Back-Ups)

This will schedule your back-up every day, week, month.

Take care...

---

### Post by corn13read on 2008-01-26
you could just have a reoccurring rsynch option for someone that just wants to know that their data is getting backed up every (unspecified day of the week) at such and such time... I guess that wouldn't require a time estimate except for the first time.

---

### Post by MaxVK on 2008-01-26
Forgive me if this has been asked before (Its a long thread to do more than skim!).

Am I right in thinking that the backup files created are not specific to a particular *sized* drive?

I ask because I am using a triple boot, with Win2k, WinXP and Ubuntu, but I want to remove XP and re-install Ubuntu, using the extra space from XP. This would leave me with a much larger / partition and a much larger /home partition. The configuration of a separate /home partition is the same as it is now.

Would it then be possible to use the backup files created on these larger partitions, to restore the system to its state at the time of the backup?

Thanks

Max

---

### Post by Polygon on 2008-01-26
> **MaxVK said:**
> Forgive me if this has been asked before (Its a long thread to do more than skim!).

Am I right in thinking that the backup files created are not specific to a particular *sized* drive?

I ask because I am using a triple boot, with Win2k, WinXP and Ubuntu, but I want to remove XP and re-install Ubuntu, using the extra space from XP. This would leave me with a much larger / partition and a much larger /home partition. The configuration of a separate /home partition is the same as it is now.

Would it then be possible to use the backup files created on these larger partitions, to restore the system to its state at the time of the backup?

Thanks

Max

your thinking of disk images, like with partimage. These arnt disk images, instead they are just .tgz files with all the folders in your like home directory tar'ed and compressed, and you can move it anywhere you want. and i imagine when you want to restore it, it just restores the archive to your home directory.

---

### Post by mdpalow on 2008-01-26
> **MaxVK said:**
> Forgive me if this has been asked before (Its a long thread to do more than skim!).

Am I right in thinking that the backup files created are not specific to a particular *sized* drive?

I ask because I am using a triple boot, with Win2k, WinXP and Ubuntu, but I want to remove XP and re-install Ubuntu, using the extra space from XP. This would leave me with a much larger / partition and a much larger /home partition. The configuration of a separate /home partition is the same as it is now.

Would it then be possible to use the backup files created on these larger partitions, to restore the system to its state at the time of the backup?

Thanks

Max

That's a really good question. My instinct is to say yes it would work. If I understand you correctly, you want to back-up a partition, then perhaps format it and make it even bigger with gParted and then use QuickStart to restore the / and/or /home back and have it work as before. I don't see any reason why this wouldn't work. Both QuickStart and TAR don't care about the original size of the partition, so it should work no problem.

Anyone reading this have a differing opinion as to why it wouldn't work. If so, pls share 'cause it's not coming to me if there is a reason it won't.

Thanks...

---

### Post by MaxVK on 2008-01-27
Polygon: Yes, I have disk images in mind. I know this is not the same but I wanted to check it out first.

mdpalow: Thanks. It makes sense that this would work, but I figured to run it past a few people first. I wont be doing this immediately, but as soon as I have some free time Ill be getting onto it.

---

### Post by perixx on 2008-01-27
Hi MaxVK!

Perhaps that is what you're looking for - **ntfsclone**:
[http://www.linux-ntfs.org/doku.php?id=ntfsclone]("http://www.linux-ntfs.org/doku.php?id=ntfsclone")

Note, though, that you'll need to put quite some effort into getting a whole backed-up Windows partition back to 'life' again, in terms of booting it (read the info and links on the page)...

**Edit:** oh, sorry - I overlooked that you likely want to backup **Linux**, not XP! I'm not all sure about it, maybe using an appropriate 'dd if=/ of=/...' command would do the job (restoring onto a larger drive). 
Apart from that - you might also use 'Gparted' to delete XP, move Ubuntu to the former starting point of Ubuntu and then enlarge Ubuntu's drive (I've done so several times) - this way, you could spare the re-installation of Ubuntu...

If I'm not mistaken, you're using ntloader as chainloader for all other OS's? If so, you'll have to store a new copy of your Ubuntu's partition-bootsector in the form of a 'bootsect.lnx' or similar into C:\ of W2k...
   
perixx

---

### Post by mdpalow on 2008-01-27
> **perixx said:**
> 
You'll need to put quite some effort into getting a whole backed-up Windows partition back to 'life' again, in terms of booting it (read the info and links on the page)...


QuickStart already does it for you and it requires no effort at all.

---

### Post by perixx on 2008-01-28
Really? I'll give it a try anytime soon!

perixx

---

### Post by Kevin Funnell on 2008-01-28
mdpalow,  Thanks for your excellent programm downloaded and install.  did a full backup, all went well, As yet I have not had to use the reinstall but if it works like the backing up, I think there should be a lot of happy Ubuntu users,  Thanks again/  Old Kevin

---

### Post by MaxVK on 2008-01-28
Thanks perixx.... I think? I mean I know the words you used, but in that order...  ;)

Just to clarify:
I have a triple boot running from GRUB: Ubuntu, Windows 2000 and Windows XP.

I want to remove XP and reformat its space for use by Ubuntu. Ill then reinstall Ubuntu into this new, larger space, and (hopefully) use QuickStart to restore the Ubuntu *content*, so that I'm back where I am now, only with more space for Ubuntu.

I'm also in agreement with Kevin here too. I certainly need to thank mdpalow for QuickStart, because without it Id be having a hard time backing things up at all!

---

### Post by bw44 on 2008-01-28
> **MaxVK said:**
> I have a triple boot running from GRUB: Ubuntu, Windows 2000 and Windows XP.

I want to remove XP and reformat its space for use by Ubuntu. Ill then reinstall Ubuntu into this new, larger space, and (hopefully) use QuickStart to restore the Ubuntu *content*, so that I'm back where I am now, only with more space for Ubuntu.

When you say "reinstall Ubuntu" does this, in your mind, include re-installing all the additional packages you may have installed after running the live CD, but before taking the QuickStart backup?

We need to be clear about this!  My understanding is that you **do** have to re-install all those packages before "restoring" from the QuickStart backup.

Hopefully, mdpalow will confirm this one way or the other -- and yes, we owe him a big THANKS for all his efforts!

bw44

---

### Post by mdpalow on 2008-01-28
> **bw44 said:**
> When you say "reinstall Ubuntu" does this, in your mind, include re-installing all the additional packages you may have installed after running the live CD, but before taking the QuickStart backup?

We need to be clear about this!  My understanding is that you **do** have to re-install all those packages before "restoring" from the QuickStart backup.

Hopefully, mdpalow will confirm this one way or the other -- and yes, we owe him a big THANKS for all his efforts!

bw44

No No No

Just install the LIVE CD. After rebooting, go straight into loading QuickStart and then restoring your back-up.

Here's how I do it and recommend doing it.

Clean install
Install all updates
Enable restricted drivers
Install all applications you want/need
Make all settings changes you want (eye candy stuff)

basically setup you computer doing everything you can think of that will get you back to this exact spot should you need to restore.

Then make a back-up.

How I've restored a dozen times already...

Install LIVE CD

After reboot, go STRAIGHT INTO loading QuickStart and then IMMEDIATELY restore back-up files.

All updates, settings, restricted drivers, etc, etc... are exactly like the day I made the back-up. I don't have to do anything after restore.

Hope this helps.

---

### Post by timseal on 2008-01-28
I'd like to give this a try, but I'm not about to run something of this nature without being able to look at the source code first.  Is this thing always going to be closed source?

---

### Post by mdpalow on 2008-01-28
Yes, for the immediate future.

---

### Post by timseal on 2008-01-28
That's going rather against the grain.  Good luck.

---

### Post by OffHand on 2008-01-28
> **mdpalow said:**
> Yes, for the immediate future.

Why? What is the reason you will not release the code?

---

### Post by bw44 on 2008-01-28
> **mdpalow said:**
> No No No

Just install the LIVE CD. After rebooting, go straight into loading QuickStart and then restoring your back-up.

Here's how I do it and recommend doing it.

Clean install
Install all updates
Enable restricted drivers
Install all applications you want/need
Make all settings changes you want (eye candy stuff)

basically setup you computer doing everything you can think of that will get you back to this exact spot should you need to restore.

Then make a back-up.

How I've restored a dozen times already...

Install LIVE CD

After reboot, go STRAIGHT INTO loading QuickStart and then IMMEDIATELY restore back-up files.

All updates, settings, restricted drivers, etc, etc... are exactly like the day I made the back-up. I don't have to do anything after restore.

Hope this helps.

Glad I was wrong -- thanks for setting me straight!

I guess what I was trying to get at is  that anything updated or installed **after** the complete initial install (including updates, applications and "eye candy") and initial backup, would have to be re-applied if you needed to restore your system.  Given that Ubuntu frequently recommends new updates and I'm constantly tinkering with things, I guess the message is that we need to strike a balance between more frequent backups and keeping extensive logs of what has changed since the initial backup.  Yes?

---

### Post by K.Mandla on 2008-01-28
Moved to General Help.

---

### Post by perixx on 2008-01-28
> Yes, for the immediate future. Unhappy to hear that.... are you planning to make money with this? 
Or is your code too dangerous to spread openly :)
Just kidding ^^)

perixx

---

### Post by mdpalow on 2008-01-28
> **bw44 said:**
> Glad I was wrong -- thanks for setting me straight!

I guess what I was trying to get at is  that anything updated or installed **after** the complete initial install (including updates, applications and "eye candy") and initial backup, would have to be re-applied if you needed to restore your system.  Given that Ubuntu frequently recommends new updates and I'm constantly tinkering with things, I guess the message is that we need to strike a balance between more frequent backups and keeping extensive logs of what has changed since the initial backup.  Yes?


Yes, that's why I always try and remember everything I want to initially setup, so when I make the back-up the only thing I should have to do is add any new updates that have come in since the back-up if/when I restore. I know you tinker more than me, so yeah - you might want to keep some kind of running log of what you've been doing since your back-up OR make more back-ups. :)

---

### Post by mdpalow on 2008-01-28
> **perixx said:**
> Unhappy to hear that.... are you planning to make money with this? 
Or is your code too dangerous to spread openly :)
Just kidding ^^)

perixx

No money - just a few personal reasons and trying to look out for everyone. I see we've been moved again. Last time we were moved I was told the 'Cafe' is where we belonged. Now we're in General Help. I think it's all very subjective how we get moved around.

---

### Post by altonbr on 2008-01-28
I don't see how hiding the source code is progressive or constitutes as 'safe'. The majority of programs under the GNU/Linux kernel are open source/GPLed and I haven't heard of that hurting anybody...

---

### Post by mdpalow on 2008-01-28
I already know your opinion about all this altonbr, so why not just drop it once and for all.

---

### Post by bw44 on 2008-01-28
> **mdpalow said:**
>  I see we've been moved again. Last time we were moved I was told the 'Cafe' is where we belonged. Now we're in General Help. I think it's all very subjective how we get moved around.

You're not serious about being told this thread be in "Community Cafe"!?!?!  Since I've been subscribed to this  thread almost from the start,  I couldn't even tell you what forum(s) it was in before. 

Is this another aspect of what you said in an earlier post about "they" not feeling this thread was worthy of a sticky post because it didn't spell out the "how to" that's built in to QuickStart?

There should definitely be a place in "Absolute Beginner" for a procedure like QuickStart. If not as a sticky, at least as a conspicuous thread.   I thought Ubuntu was supposed to appeal to people who have used Windows for years (with all its failings) yet who never had to know what a .dll is, or how to code in C#).

I love Ubuntu because it's both much more user-friendly than when I first tried a Linux distribution, but at the same time it still  allows you to roll up your sleeves and delve into the internals.  But not every noob wants to become a Linux geek (no offense to anybody -- I wish I had what it takes to be a true geek!)

QuickStart isn't perfect: a few posts to this thread have questioned aspects of its content and packaging.  But at the end of the day, it addresses some really frustrating problems that beginning users face, and which haven't been adequately addressed by the basic Ubuntu distro: Ubuntu** and** Windows dual boot backup (I tried the other backup options and they just didn't work well); getting video streams to work and DVD's  to play.  This is pretty basic stuff -- in fact these things should be provided for and work "out of the box!"

Maybe that's why there's resistance to more openly supporting QuickStart -- it points up some of the current Ubuntu's failings.  Maybe these will all be fixed in 8.04.  If not I hope you'll use the same talents to come up with a procedure to make my laptop sound card and modem work!

I'll get off my soapbox now -- I'm probably just preaching to the converted!

Cheers.

---

### Post by mdpalow on 2008-01-28
QuickStart isn't perfect?

;)

---

### Post by ezak on 2008-01-29
Just wanted to drop a small line to mdpalow. :KS 

Excellent work with this script you have submitted here and with integrating the QuickStart installer.

 I myself, including quite a few others here, would love to see QuickStart in the Ubuntu packages.

 Keep up the good work with this, if you continue to do. :)

---

### Post by ugm6hr on 2008-01-29
A few comments, if I may...

I think Quickstart is great, and works well.  I've just installed it on my mum's laptop too for easy restoration (if she manages to mess things up!)

I've realised that Quickstart is designed more for restoration of the system than a "back-up" per se.  Is that intentional?  I know there is a "custom" backup option available (which I have used), but there are a couple of "auto" options that may help some users (by that I mean me ;)

1. Backup /home but exclude all hidden directories / files (i.e. anything starting with a ".")  Is this possible?  Reason I ask, is that I would like to keep the setup files backed up as they are now, but have the option to create repeat backups of personal files easily.  Does that make sense?

2. Backup /var/cache/apt/archives and then offer to run an apt-get clean (i.e. empty that folder) to free up disk space.  This would allow reinstallation of updates / packages without having download again, but without having to maintain a large uncompressed archive directory.

3. I can see lots of comments about the Quickstart installation procedure.  I have no problem with it, although agree a .deb would be nice if it is possible.  Especially if you are hoping for inclusion in a repo, which would be nice for the future.  Anyway - my actual point is that it requires internet access on the computer that is being restored.  Which is fine for me (my wifi & ethernet both work out of the box).  But some users need to download / install stuff in order for it to work.  Hence your "restore" function is not available to them until they have fixed their wifi etc.  Perhaps making the ftp location of the actual program available as a link from the OP, together with instructions indicating that downloading the package and script to desktop and running script works too?

Just a few suggestions - if you were interested...

---

### Post by OffHand on 2008-01-29
> **ugm6hr said:**
> 
3. I can see lots of comments about the Quickstart installation procedure.  I have no problem with it, although agree a .deb would be nice if it is possible.  Especially if you are hoping for inclusion in a repo, which would be nice for the future.
In order to be included he would first have to open the source....

---

### Post by perixx on 2008-01-29
> There should definitely be a place in "Absolute Beginner" for a procedure like QuickStart.
VS
> In order to be included he would first have to open the source....
I suppose the second statement applies here... unless it's gonna be included in the 'restricted' section :]

Hm. I can't quite follow the idea why a private person would insist of keeping secrets in an open community, unless there's alien proprietary code included - like some driver projects. Isn't it always better to have several people reviewing a piece of code? If I write a very long text, chances are very good to overlook a few typos, even if I skim it 3 times. 
> QuickStart isn't perfect? None can judge. It's like presenting a black box and claiming it's containing a piece of gold, just by judging it's weight. Could as well contain lead ^^

For companies - I understand, ok, they have commercial reasons - but private persons :confused: 
 
perixx

---

### Post by OffHand on 2008-01-29
The application is fine, the dev is a decent guy but keeping it closed source is good for nothing but making money out of it. No need to protect us from people doing malicious stuff with your code.

---

### Post by Kevbert on 2008-01-29
Wow.  An excellent post, thanks mdpalow.  This is the sort of program which should be part of the Ubuntu OS install.:):):)

---

### Post by mdpalow on 2008-01-29
> I've realised that Quickstart is designed more for restoration of the system than a "back-up" per se.  Is that intentional?  I know there is a "custom" backup option available (which I have used), but there are a couple of "auto" options that may help some users (by that I mean me ;)

No, not intentional at all.

> 1. Backup /home but exclude all hidden directories / files (i.e. anything starting with a ".")  Is this possible?  Reason I ask, is that I would like to keep the setup files backed up as they are now, but have the option to create repeat backups of personal files easily.  Does that make sense?

Actually, this is already possible when making a /home back-up. When asked what folders you want to exclude, just select all the hidden folders along with anything else you would like to exclude.

> Backup /var/cache/apt/archives and then offer to run an apt-get clean (i.e. empty that folder) to free up disk space.  This would allow reinstallation of updates / packages without having download again, but without having to maintain a large uncompressed archive directory.

This is already possible as well. When you make a / back-up you have the .deb files backed-up. You can then run the 'house cleaning' option ( 8 ) to remove the .deb files along with other unnecessary files and save some hard drive space.


> I can see lots of comments about the Quickstart installation procedure.  I have no problem with it, although agree a .deb would be nice if it is possible.  Especially if you are hoping for inclusion in a repo, which would be nice for the future.

Yeah, the installation hasn't always been the same. Before, it probably was a bit more problematic and that's why there were a lot of comments back then. Seems to be easy enough now.

I've never given the idea of getting QS into the repo's more than a brief thought to be honest with you.

> Anyway - my actual point is that it requires internet access on the computer that is being restored.  Which is fine for me (my wifi & ethernet both work out of the box).  But some users need to download / install stuff in order for it to work.  Hence your "restore" function is not available to them until they have fixed their wifi etc.  Perhaps making the ftp location of the actual program available as a link from the OP, together with instructions indicating that downloading the package and script to desktop and running script works too?

Even if I were to put it on an FTP server, you would still have to have Internet access to get QuickStart. I guess I always assumed:

1. People who wanted to continue using QS would simply back-up the program to another drive or save it to disk.

2. Once you made the back-up of /home, you would have the QS program backed up and you could simply extract the program (1 file only) from the QS folder and run it.

Also, if someone setup their system so the wifi/ethernet worked and then made a back-up, the wifi/ethernet would work after restoring the system and they would never have to go on the Internet to get anything until after they had restored their system AND only if it was something like a new update that had come out since making the back-up. I probably should add something to the help file explaining how to keep a copy of QS on another disk, but I doubt many people read it - let alone even know it exits even though it's an option in the program. :)

> Just a few suggestions - if you were interested...

Always interested in hearing suggestions for an addition/fix to QuickStart.

thanks ugm6hr

---

### Post by Het Irv on 2008-01-29
The main reason I need a system restore function for my system is for my wireless.  I have a Linksys wireless card that works with the restricted drivers, but you need to download the drivers and build-essential to install them.  This means that I have to lug my Desktop across the house to the Cable box set it back up and download 5 or 6 files (a minute on my connection) and then lug it all back.  Although I have not tried it, If I understand what QS does correctly I can do a system restore and have my system back-up and running 

One question though, what would happen if I used a back-up made from a 7.10 computer to one that was installed with 8.04?  I know that /home would work great (theoretically), but what about the others, namely wherever my wireless drivers are stored?

Thanks for all of the help and the great program. +1 to moving to Open Source.

---

### Post by ukripper on 2008-01-29
Is there any one way sync facility with it? also is it incremental and auto backup? or do i have to create my own script to automate?

thanks

---

### Post by mdpalow on 2008-01-29
> **Het Irv said:**
> The main reason I need a system restore function for my system is for my wireless.  I have a Linksys wireless card that works with the restricted drivers, but you need to download the drivers and build-essential to install them.  This means that I have to lug my Desktop across the house to the Cable box set it back up and download 5 or 6 files (a minute on my connection) and then lug it all back.  Although I have not tried it, If I understand what QS does correctly I can do a system restore and have my system back-up and running 

One question though, what would happen if I used a back-up made from a 7.10 computer to one that was installed with 8.04?  I know that /home would work great (theoretically), but what about the others, namely wherever my wireless drivers are stored?

Thanks for all of the help and the great program. +1 to moving to Open Source.

I would say you understand correctly, but I wouldn't want to say what would happen if you restored 7.10 on to 8.04. I think you stand a better than 50/50 chance of it working, but I really couldn't say for sure. That's the ticket though.. if you knew where the drivers were loaded, you could just archive them with file browser and wouldn't even have to use QS.

Anyway you can save off the drivers to a disk or another drive?

---

### Post by mdpalow on 2008-01-29
> **ukripper said:**
> Is there any one way sync facility with it? also is it incremental and auto backup? or do i have to create my own script to automate?

thanks

There is a one-way sync option if I understood correctly. There is a "auto back-up" called Scheduled Back-up, but none of it is incremental because the back-ups are compressed and tar won't increment to a file that is compressed.

Hope I answered your question...

---

### Post by ukripper on 2008-01-29
> **mdpalow said:**
> There is a one-way sync option if I understood correctly. There is a "auto back-up" called Scheduled Back-up, but none of it is incremental because the back-ups are compressed and tar won't increment to a file that is compressed.

Hope I answered your question...

Thanks mate. I will try it today.

---

### Post by ugm6hr on 2008-01-29
> Actually, this is already possible when making a /home back-up. When asked what folders you want to exclude, just select all the hidden folders along with anything else you would like to exclude.
I had spotted that option, but was just interested to know how straightforward it would be to automate that process (i.e. can I be cheeky and ask you to modify the program just for me!)  But this is no big deal, actually.

> This is already possible as well. When you make a / back-up you have the .deb files backed-up. You can then run the 'house cleaning' option ( 8 ) to remove the .deb files along with other unnecessary files and save some hard drive space.
This is a reflection of the predominant "restore" rather than backup option.  Let me illustrate with an example.  I have installed my system just as I like it.  I do a Quickstart backup of everything.  I do a "house clean", which wipes the .deb archives.  A week later, having installed a few new apps, I decide to backup again.  However - this time, the "/" backup doesn't include all the original .debs, only the ones installed in the last week.  Maybe it is just me, but I like the security blanket of having all my .debs stored somewhere.  Currently, there are 180+ updates on a default install, equating to 300+MB.  Hence, once downloaded, I'd like to be able to access them again (just in case, or if I want to transfer to my mum's laptop later).

This may just be a reflection of how I want to use QuickStart, but let me explain some more.  I do a base install, update everything, install my multimedia stuff and a few other selected apps.  I then do a QS backup.  From then on, all I need to backup weekly(-ish) are additional .debs and personal files (i.e. not settings files / hidden files).

> 1. People who wanted to continue using QS would simply back-up the program to another drive or save it to disk.

2. Once you made the back-up of /home, you would have the QS program backed up and you could simply extract the program (1 file only) from the QS folder and run it.

I probably should add something to the help file explaining how to keep a copy of QS on another disk, but I doubt many people read it - let alone even know it exits even though it's an option in the program. :)

:oops: Errrmmm...  Guilty as charged.  Never read it.

A quick explanation in the OP about how to backup QS for future use might help some people though.  I didn't realise you could just backup the program file.  That just seemed too obvious to work!

---

### Post by perixx on 2008-01-29
> The application is fine, the dev is a decent guy. I suppose so. Perhaps I'm a little too suspicious. But all the proprietary mumbo jumbo under Windows made me actually coming to Linux. I even chose Xubuntu at the very start for that reason, which isn't the easiest of the Ubuntu-flavours to set up. 

So be it, if having an offline computer, that one seems to be off-limits to the program anyway, if I understood correctly.  

perixx

---

### Post by jryprt on 2008-01-29
Very nice & Easy to use.

---

### Post by OffHand on 2008-01-29
> **perixx said:**
> I suppose so. Perhaps I'm a little too suspicious. But all the proprietary mumbo jumbo under Windows made me actually coming to Linux.
It's good to be suspicious. I'm suspicious too. Actually I should have said: It seems like he is a decent guy. (That's not an attack - we just don't know).
> **perixx said:**
> 
 I even chose Xubuntu at the very start for that reason, which isn't the easiest of the Ubuntu-flavours to set up. I don't get this? Both are released under the same license as far as I know.

---

### Post by locolobo on 2008-01-30
Thank You Very Much!!!!! Good Job!!!:):)

---

### Post by locolobo on 2008-01-30
THANK YOU VERY MUCH!!!! Have used several of the options already ..
They went very smooth and added new zip to the OLD laptop I am working on.
 MY Sys: OLD  Sony VAIO laptop , AMD Duron 800 MHZ - Model PCG-FX215 with max
 mem 256 Mb and 150 Gb HDD  +USB 1.1 NO wireless and 2 PCMCIIA slots.
 IT was too OLD and too slow to run Win XP...   I added new life when I wiped off
Windows totally and loaded Fiesty Fawn unbuntu after I had carefully selected right
PCMCIIA wireless card from NetGear.. After several updates and upgrade I am now
running ubuntu 7.10 with only 1 restricted driver for wireless card. This Machine will
NEVER have windows on it AGAIN. THANKS AGAIN ..YOUR HELP HAS BEEN INVALUABLE!!:):):guitar:

---

### Post by perixx on 2008-01-30
> *I even chose Xubuntu at the very start for that reason, which isn't the easiest of the Ubuntu-flavours to set up.*
I don't get this? Both are released under the same license as far as I know.
Erm, yes. I was referring to the smoother designed menu's in general. Also, many apps that make life easier are designed for the Gnome- or KDE-desktop  - you can install them but you'll have to fiddle around, making starter buttons and create workarounds instead of simply accessing it from the new menu entry. I have the feeling that you've got to hack around a bit more, if using Xfce.

perixx

---

### Post by AutumnPhoenix on 2008-02-03
> E: Couldn't find package lib32z1  what do I do?

---

### Post by mdpalow on 2008-02-03
Did you install the Ubuntu 32-bit version or the 64-bit version?

---

### Post by wrongdave on 2008-02-05
Thanks for the very useful program. 
As a long-time windows user, I've been disappointed whenever I toyed with linux (have been running multiboot systems for several years with several versions of Suse Linux) because I would always bump into something that I just could not get to work. 
I recently installed ubuntu and was pleased at how ubuntu made it easy to install audio codecs to play CDs and MP3s (something I struggled with in Suse), but had problems getting DVD movies to play and getting Flash (youtube and ifilm videos) to play in firefox (kept freezing up ubuntu). 
I ran the Flash and DVD options from your program and everything seems to be working now. In fact, my DVDs play better now on Ubuntu than they do on Windows XP with a commercial DVD viewer. 
I'm a pretty hardcore Windows user so I'm not ready to give up Windows yet, but I'm happy to finally have a linux desktop system up and running that actually works for much of what I do on my home pc.

---

### Post by whitefang5412 on 2008-02-08
Hm, couldn't find the libraries to run 32 bit programs on a 64 bit system...

---

### Post by mdpalow on 2008-02-09
Are you sure you're running Ubuntu 64 bit? If so, did you open a terminal window and enter

```
sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0
```

If you're actually running Ubuntu 64 bit then the files should automatically install. I don't use 64 bit, so is there anyone out there who knows of any changes in the repos perhaps?

The above code has been tested though on a 64 bit Ubuntu OS install and it works, so unless there's been a change to were these files are located - it should be fine.

Please update us with anything you find out.

Thanks

---

### Post by evilc on 2008-02-09
I have a problem, yesterday I reinstalled 7.10 and re-setup all my programs, I then made backups of config/home/sys which took approx 6 minutes no problems. Today it started to do the weekly backup as I have setup, but after 1/2 hour all that's showing on desktop is the 3 icons with a lock in corner of each. Looking in Nautilus each icon (tar file) shows the following.
config:  3.2KB  (about right)
Home:  20bytes
System:  1.2MB

My original backup shows in same order 3.2KB - 53.9MB - 715.7MB

Any idea what is going wrong?

tia

---

### Post by BenTyrer on 2008-02-09
This fixed my DVD playback issues, thus preventing me from switching to linux mint! Thankyou very much!

---

### Post by locolobo on 2008-02-10
Thanks again - loaded on 2nd Sys - I would purchase a CD of this if possible!!
                    THANKS MUCH........:):popcorn::guitar:

---

### Post by locolobo on 2008-02-10
Hit a little problem after loading Java and flash plug in >> on doing updates >>
get response > E: dpkg was interrupted > need to manually run ' dpkg-- configure-a
Tried that from term under sudo - command not found ???
Will turn in bug report but wanted to talk to you first,,,,:confused:

---

### Post by freebeer on 2008-02-10
little typo there, I think.  I believe the correct form is:

```

dpkg --configure -a

```

The "command not found is the hint to the problem.  It saw "dpkg--" as the command and "configure -a" as the argument, whereas it needs to be "dpkg" as the command and "--configure -a" as the arguments.  Watch those spaces!  :D

---

### Post by mdpalow on 2008-02-10
> **evilc said:**
> I have a problem, yesterday I reinstalled 7.10 and re-setup all my programs, I then made backups of config/home/sys which took approx 6 minutes no problems. Today it started to do the weekly backup as I have setup, but after 1/2 hour all that's showing on desktop is the 3 icons with a lock in corner of each. Looking in Nautilus each icon (tar file) shows the following.
config:  3.2KB  (about right)
Home:  20bytes
System:  1.2MB

My original backup shows in same order 3.2KB - 53.9MB - 715.7MB

Any idea what is going wrong?

tia

No idea really. It appears your crontab is working fine as you are getting all three files placed on your desktop as they should be. That being the case, I would look in your home directory and look for folder named 'Cron' and look at the three tar lines towards the bottom in the 'my_scheduled_backup' file.

Maybe you might want to post them here, so we can take a look at them. The fact you have three files on your desktop is a good sign, but we have to look at the last bit to see where the problem lies..

Thanks

---

### Post by mdpalow on 2008-02-10
> **locolobo said:**
> Hit a little problem after loading Java and flash plug in >> on doing updates >>
get response > E: dpkg was interrupted > need to manually run ' dpkg-- configure-a
Tried that from term under sudo - command not found ???
Will turn in bug report but wanted to talk to you first,,,,:confused:

Sounds like someone did not follow the instructions very well. ;)

If you did what I think you did - don't worry... you're not the first and you won't be the last. 

Just a reminder to everyone. When installing Java 6, read the pop-up windows I've programmed in as it will keep this from happening to you. I know because it happened to me too.

When in the license page, you have to use the ARROW keys on your keyboard to move the cursor to the OK button and then press ENTER. If you get frustrated and and don't figure this out and then exit the window, you'll be getting a "E: dpkg was interrupted > need to manually run ' dpkg..... "

Sorry Loco if that was not actually what you did. :)

---

### Post by evilc on 2008-02-10
> **mdpalow said:**
> No idea really. It appears your crontab is working fine as you are getting all three files placed on your desktop as they should be. That being the case, I would look in your home directory and look for folder named 'Cron' and look at the three tar lines towards the bottom in the 'my_scheduled_backup' file.

Maybe you might want to post them here, so we can take a look at them. The fact you have three files on your desktop is a good sign, but we have to look at the last bit to see where the problem lies..

Thanks

Here it is:

tar cvpzf config_backup_`date +%Y.%m.%d`.tgz $inc1 $inc2 $inc3 $inc4 $inc5


tar cvpzf system_backup_`date +%Y.%m.%d`.tgz $ex01 $ex02 $ex03 $ex04 $ex05 $ex06 $ex07 $ex08 $ex09 $ex10 $ex11 $ex12 $ex13 $ex14 $ex15 /


tar cvpzf home_backup_`date +%Y.%m.%d`.tgz $ex01 $ex02 $ex03 $ex09 $ex10 $ex16 $ex17 $ex18 /home

Hope that makes sense to you :)

---

### Post by brucewagner on 2008-02-10
Now that Ubuntu is being automatically updated with some of the fixes for these media issues...

I'm confused.

On new installs of Ubuntu, am I better off following the install instructions from this thread, "A New Back-Up Solution if You Want It" --- the QuickStart instructions for installing video stuff ( [http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462) )

Or this thread, " Complete Streaming, Multimedia & Video How-to" ( [http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833) ).

I am a newbie myself, but I see that brand new installs of Ubuntu are getting automatic updates now which DO successfully play YouTube videos, for example.  But I don't know about all the other media issues (commercial DVD playback, MP3 , video codecs, streaming video, etc.)...

On new installs for friends, Should I...

(a)   Just let Ubuntu's automatic install update their systems
(b)   Follow the "A New Back-Up Solution if You Want It" how to instructions    ~or~
(c)   Follow the " Complete Streaming, Multimedia & Video How-to" instructions   ?

---

### Post by mdpalow on 2008-02-10
> **evilc said:**
> Here it is:

tar cvpzf config_backup_`date +%Y.%m.%d`.tgz $inc1 $inc2 $inc3 $inc4 $inc5


tar cvpzf system_backup_`date +%Y.%m.%d`.tgz $ex01 $ex02 $ex03 $ex04 $ex05 $ex06 $ex07 $ex08 $ex09 $ex10 $ex11 $ex12 $ex13 $ex14 $ex15 /


tar cvpzf home_backup_`date +%Y.%m.%d`.tgz $ex01 $ex02 $ex03 $ex09 $ex10 $ex16 $ex17 $ex18 /home

Hope that makes sense to you :)

Yes, it does.

Your script file looks fine AS LONG as that file also has the $incl and $ex towards the top, which are being referenced in the tar lines. I'm sure they're there.

Not really sure what's going on. You're the first person to post a problem with a scheduled back-up. I've personally tested it and it works. Is anyone else having this problem?

---

### Post by mdpalow on 2008-02-11
Bruce,

Some of the tools on QuickStart were added only as a temporary fix to a bug that existed either in Ubuntu or adobe. If/when the updates are out and it solves the problem, I will be removing them from QuickStart. 

So, I guess I'm saying is that at some point you'll just let the install do it all for you. 

Hope I answered your question..

---

### Post by brucewagner on 2008-02-11
Ok...  Thanks.

Nathan is the author of the other How To...   "Complete Streaming, Multimedia & Video How-to"  at [http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

Here is his response to the same question:

> **reassuringlyoffensive said:**
> Adobe Flash is proprietary and isn't installed by default, niether is java, codecs for wmv's or mp3's. Only free software is installed by default so it's good to bookmark this how-to. 
 
I'm making some changes monday just so you know. Mostly to part 1 and part 3.
 
Nathan

I just wish it wasn't such a massive long list of terminal commands.   It's quite intimidating.   Especially for new users...

I wish it were automated.... into a GUI.... like QuickStart is...

(hint, hint ;) )

---

### Post by evilc on 2008-02-11
> **mdpalow said:**
> Yes, it does.

Your script file looks fine AS LONG as that file also has the $incl and $ex towards the top, which are being referenced in the tar lines. I'm sure they're there.

Not really sure what's going on. You're the first person to post a problem with a scheduled back-up. I've personally tested it and it works. Is anyone else having this problem?

If anyone can have a weird problem I can :) Here is the full script file, I tried to remake it and on all 4 occasions it stops at the same place. For your information the config tar is right and the home tar has nothing in it.

#!/bin/bash
#!/bin

# This file and folder it's located in were created by QuickStart and are used for your
# scheduled back-up(s). Please do not delete either or your scheduled back-up
# will not occur.

#Excludes
ex01="--exclude=system_backup_*.tgz"
ex02="--exclude=home_backup_*.tgz"
ex03="--exclude=config_backup_*.tgz"
ex04="--exclude=/home"
ex05="--exclude=/media/*"
ex06="--exclude=/mnt/*"
ex07="--exclude=/proc/*"
ex08="--exclude=/sys/*"
ex09="--exclude=lost+found/*"
ex10="--exclude=.Trash/*"
ex11="--exclude=/boot/grub/menu.lst"
ex12="--exclude=/boot/grub/device.map"
ex13="--exclude=/etc/fstab"
ex14="--exclude=/etc/mtab" 
ex15="--exclude=/etc/X11/xorg.conf"
ex16="--exclude=/home/clive/.thumbnails/fail/gnome-thumbnail-factory/*"
ex17="--exclude=/home/clive/.thumbnails/normal/*"
ex18="--exclude=windows_backup_*.img"

#Includes
inc1="/boot/grub/menu.lst"
inc2="/boot/grub/device.map"
inc3="/etc/fstab"
inc4="/etc/mtab"
inc5="/etc/X11/xorg.conf"

cd /home/clive/Desktop


tar cvpzf config_backup_`date +%Y.%m.%d`.tgz $inc1 $inc2 $inc3 $inc4 $inc5


tar cvpzf system_backup_`date +%Y.%m.%d`.tgz $ex01 $ex02 $ex03 $ex04 $ex05 $ex06 $ex07 $ex08 $ex09 $ex10 $ex11 $ex12 $ex13 $ex14 $ex15 /


tar cvpzf home_backup_`date +%Y.%m.%d`.tgz $ex01 $ex02 $ex03 $ex09 $ex10 $ex16 $ex17 $ex18 /home

 The sys tar file has in it an empty . folder, a usr/lib folder, inside that a gcc folder and 15 files. I tried to add the tar file but kept coming up invalide file.

---

### Post by mdpalow on 2008-02-11
I'm sorry, but I don't know exactly what is going on with your system.

I just scheduled a daily back-up for 6:30 pm and it started exactly on time and created three files on my desktop and each file was properly populated with the files it should have had.

You do have a "/home" directory, right? It's not named something else like "/media/home" or anything else is it?

Thanks...

---

### Post by evilc on 2008-02-11
All folders are standard installation (out of box) type. I will try removing ubackup and reinstall using a new d/l version (should be what i've got now) and try again.

---

### Post by evilc on 2008-02-11
OK reinstalled setup schedule backup checked cron file still reads the same. Backup started and left running for 45 minutes, checked files exactly same as before? I then did normal backup of all 3 took 6mins all look good.
Open for suggestions:) for now will make my weekly backup manually.

---

### Post by mdpalow on 2008-02-11
Sorry Clive... Nothing is coming to mind that might be the reason for your problem. I will be giving it some more thought and if I think of something I'll reply again.

---

### Post by evilc on 2008-02-11
> **mdpalow said:**
> Sorry Clive... Nothing is coming to mind that might be the reason for your problem. I will be giving it some more thought and if I think of something I'll reply again.

Thanks, no problem will continue to do manual backups for now.

---

### Post by brucewagner on 2008-02-11
Apparently, the Ubuntu folks are busy at work improving the way things work...

Just thought you'd like to know:

On two brand new Ubuntu Gutsy installs today, this was my experience...

Without installing ANYTHING other than the automatic updates...

I tried to open an MP3 file,
		mp3 – I was prompted to install “Gstreamer extra plugins” (mp3, etc.)
                and the files now play fine.

Upon visiting a YouTube video page, 
	        youtube flash video – I was prompted to install Adobe Flash
                and all the videos play fine now.

I opened an AVI file, 
		divx avi – I was prompted to install “Gstreamer ffmpeg video plugin” 
                   (for divx. mwv)
                now divx avi files play fine.
		wmv – also plays in Totem without installing anything else at all.

I visited a web site that uses Java extensively,
                java -- I was prompted to install “The Java(TM) Plug-in, Java SE 6”
                now the java functions fine.

So all of these things installed automatically (or semi-automatically) with Ubuntu now.

Am I missing anything?

---

### Post by Michl on 2008-02-15
Very nice ... amazing actually.  Worked on desktop and laptop.
Thank you!!

---

### Post by mdpalow on 2008-02-18
It appears the Flash install is working again, so I think it might be time to remove flash install from QuickStart. It was nice while needed, but was only intended as a quick-fix until the bug was worked out.

Can anyone confirm any additional fixes that make some of the functions in QuickStart redundant or even unnecessary? If so, please let me know, so I can trim QS down some.

thanks...

---

### Post by money2themax on 2008-02-19
will this work on other distros

---

### Post by wrongdave on 2008-02-19
> **mdpalow said:**
> It appears the Flash install is working again, so I think it might be time to remove flash install from QuickStart. It was nice while needed, but was only intended as a quick-fix until the bug was worked out.

Can anyone confirm any additional fixes that make some of the functions in QuickStart redundant or even unnecessary? If so, please let me know, so I can trim QS down some.

thanks...

I'm not sure when flash was supposedly fixed, but as of a couple of weeks ago when I installed Ubuntu on my desktop, I had a hell of a time getting flash to work (firefox would freeze when trying to view youtube or other flash video sites). Your install package solved my problems. Now a week ago I installed on an old laptop, and didn't need your program (for flash). So either it was fixed, or it is a problem with certain hardware configurations.

---

### Post by captainzott on 2008-02-19
Have 64 bit running, so I followed your instructions on how to enable 32 bit to enable this add on to work. Went smoothly and your add on is simple and easy to use, particularly like the swiss army knife icon when you drag to desktop - thanks

---

### Post by Het Irv on 2008-02-19
Would it be possible for QS to install to a Hidden Directory in the Home folder.  I like keeping the number of folders showing in there to a minimum.
Thanks for all of your great work so far.

---

### Post by mdpalow on 2008-02-19
> **Het Irv said:**
> Would it be possible for QS to install to a Hidden Directory in the Home folder.  I like keeping the number of folders showing in there to a minimum.
Thanks for all of your great work so far.

Well, I think for it to be hidden you'd have to change the folder name to .QuickStart and that might then cause a problem in the path when QS is done with something and wants to reload the Main Menu for you.

I'm not in Linux right now, so I can't even test it out for you. Why not give it a try? :)

---

### Post by Het Irv on 2008-02-19
Thats why I posted, I originally had it set up to be hidden, but I hadn't clicked on the program to see if it still worked. I click on it to update and I had to unhide the folder to get it to work.

---

### Post by mdpalow on 2008-02-19
> **wrongdave said:**
> I'm not sure when flash was supposedly fixed, but as of a couple of weeks ago when I installed Ubuntu on my desktop, I had a hell of a time getting flash to work (firefox would freeze when trying to view youtube or other flash video sites). Your install package solved my problems. Now a week ago I installed on an old laptop, and didn't need your program (for flash). So either it was fixed, or it is a problem with certain hardware configurations.

Thanks wrongdave...

Yeah, I'm thinking it's fixed 'cause I removed the QS fix and then downloaded/installed flash (like we used to) and it worked.

Now if someone could verify Java for me. :)

---

### Post by mdpalow on 2008-02-19
> **money2themax said:**
> will this work on other distros

I remember someone coming in the thread saying it worked on a different distro, but I doubt it worked 100%.

I tried it once on.... I think it was Kubuntu, but there were too many differences that it didn't work well - if at all.

So, I guess the short answer is No. Sorry.

---

### Post by angry_johnnie on 2008-02-21
wow, thanks!  I seriously doubt things get any easier than this.

---

### Post by meazz1 on 2008-02-21
I never thought backing data up in  linux would be that easy!!!!!

thanks

---

### Post by mdpalow on 2008-02-22
> **meazz1 said:**
> I never thought backing data up in  linux would be that easy!!!!!

thanks

What's even better is the back-up actually works every time too.

Enjoy...

---

### Post by Phosphoric on 2008-02-23
Hi mdpalow,

I've read with great interest the whole 50 pages of this thread from the first version of uBackup! to version 6.0 of Quickstart.
What an astounding piece of work. :KS

Thank you so much for your efforts to make life easier for the new Ubuntu users, it gives us so much more confidence to stick with the OS and keep learning.

I've made my first backup and I'm now off to explore differential backups across two hard drives.

Thanks again.

---

### Post by mdpalow on 2008-02-23
> **Phosphoric said:**
> Hi mdpalow,

I've read with great interest the whole 50 pages of this thread from the first version of uBackup! to version 6.0 of Quickstart.
What an astounding piece of work. :KS

Thank you so much for your efforts to make life easier for the new Ubuntu users, it gives us so much more confidence to stick with the OS and keep learning.

I've made my first backup and I'm now off to explore differential backups across two hard drives.

Thanks again.

Thank you for the wonderful posting Phosphoric. Very nice to hear. :)

---

### Post by pvalley1967 on 2008-02-23
I've installed it but can I back up to DVD?

---

### Post by mdpalow on 2008-02-23
> **pvalley1967 said:**
> I've installed it but can I back up to DVD?

No, not with QuickStart. You'll need to use a linux cd/dvd writing program (I can't remember the name of it) that will break up your back-up into increments that will fit onto a disk. However, if your back-up is less than 4 gigs - you can simply write it to the disk yourself.

Good luck.

P.S. Anyone know/remember the name of the program that will write to multiple disks?

---

### Post by pvalley1967 on 2008-02-23
I have both CD/DVD creator that comes with gnome but I also use K3B what I am looking to do is back my system up to dvd so any help would be grateful

Paul

---

### Post by pvalley1967 on 2008-02-23
> **pvalley1967 said:**
> I have both CD/DVD creator that comes with gnome but I also use K3B what I am looking to do is back my system up to dvd so any help would be grateful

Paul
Ok I've found the CD/DVD backup program its called CDTAR it allows you to backup to DVD-R thanks for all the hard work on quickstar and helping me

Paul

---

### Post by Phosphoric on 2008-02-24
Hi mdpalow,

I've created my first scheduled backup set and 3 files have appeared on my desktop:
System,home and config_backup_2008.2.24.tgz.

Couple of questions:
Will the next scheduled set be incremental?
Can I choose a different location?

Thanks. :)

---

### Post by mdpalow on 2008-02-24
> **pvalley1967 said:**
> Ok I've found the CD/DVD backup program its called CDTAR it allows you to backup to DVD-R thanks for all the hard work on quickstar and helping me

Paul

That's not the program I was talking about. The program I was describing simply lets you copy a file that is larger than a CD/DVD to multiple CD/DVD's.

If you prefer to use that program to make your back-ups, be sure you know which files to exclude and put in a separate back-up, so your restore works properly if/when your system has changed.

Good luck

---

### Post by mdpalow on 2008-02-24
> **Phosphoric said:**
> Hi mdpalow,

I've created my first scheduled backup set and 3 files have appeared on my desktop:
System,home and config_backup_2008.2.24.tgz.

Couple of questions:
Will the next scheduled set be incremental?
Can I choose a different location?

Thanks. :)

No, the next back-up is not incremental. It will be everything again. TAR doesn't allow for incremental UNLESS the back-up is uncompressed. Since QuickStart compresses everything.......

You can't chose a different location on scheduled back-ups and here's why:

When I wrote QuickStart, I knew the back-up was going to take up a lot of resources while it was working. I also knew two weeks or a month later, I would forget I had a back-up scheduled. I was concerned that I might see the HD light going crazy and my computer acting very slow and that I wouldn't remember a back-up is in progress and simply reboot the machine to see what was going on. So, I put the back-up files on the Desktop, so I would see them and know a back-up was occurring. If you didn't know, a scheduled back-up doesn't show all the windows a regular back-up does.

I have a message box come up initially to tell you it's about to begin, but if you're away from the computer, you'll miss that message when it goes away in 10-15 seconds.

I did just think of something though that might be a way to allow for a change and still have you know it's doing a back-up. I'll look into it. If it works, we could make it so you can chose a back-up location as well.

thanks

---

### Post by Phosphoric on 2008-02-24
Thanks for the information.

I have a further couple of questions.

I copied the backup files that appeared on my desktop to my preferred location, but in doing so I noticed that they were effectively empty.  For example the /home_backup was only 20 bytes. :confused:

I thought that I must have done something wrong so went through the procedure  again and set up a slightly different time.  No other options appeared that I might have done wrong initially, so now I have 2 scheduled backups.
Any idea what might have gone wrong with my first "empty" scheduled backup and how do I delete the extra one?

Thanks. :)

---

### Post by mdpalow on 2008-02-24
> **Phosphoric said:**
> Thanks for the information.

I have a further couple of questions.

I copied the backup files that appeared on my desktop to my preferred location, but in doing so I noticed that they were effectively empty.  For example the /home_backup was only 20 bytes. :confused:

I thought that I must have done something wrong so went through the procedure  again and set up a slightly different time.  No other options appeared that I might have done wrong initially, so now I have 2 scheduled backups.
Any idea what might have gone wrong with my first "empty" scheduled backup and how do I delete the extra one?

Thanks. :)

When you say you have two scheduled back-ups, do you mean that you have to schedules now or that you have two back-ups. If you meant schedules, you don't actually have two. QuickStart always deletes the previous schedule before creating a new one.

I'm not sure what could have gone wrong with your back-up IF your second back-up worked. The principles of the back-up code are sound and should work for everyone as they do me. I've tested it on a few separate computers and it worked on desktops/laptops and 32/64 bit machines.

I do know - there was one other person who posted not too long ago about the same problem (small file size) when he did a back-up, but we never figured that one out.

If you mean how to delete the back-up file(s) that were created.... well then just drag them into the trash can or right click on them and select the "move to trash" option.

Hope it's working for you now...

---

### Post by johnleonard on 2008-02-24
Good work - thanks!

---

### Post by evilc on 2008-02-24
> **Phosphoric said:**
> Thanks for the information.

I have a further couple of questions.

I copied the backup files that appeared on my desktop to my preferred location, but in doing so I noticed that they were effectively empty.  For example the /home_backup was only 20 bytes. :confused:

I thought that I must have done something wrong so went through the procedure  again and set up a slightly different time.  No other options appeared that I might have done wrong initially, so now I have 2 scheduled backups.
Any idea what might have gone wrong with my first "empty" scheduled backup and how do I delete the extra one?

Thanks. :)

Looks like the same as I got, check my post on page 48. Ended up for now doing only manual backups.

---

### Post by mdpalow on 2008-02-24
> **mdpalow said:**
> 

I do know - there was one other person who posted not too long ago about the same problem (small file size) when he did a back-up, but we never figured that one out.



Already mentioned. :)

---

### Post by Phosphoric on 2008-02-25
> **evilc said:**
> Looks like the same as I got, check my post on page 48. Ended up for now doing only manual backups.

Same again last night. :(

How did you remove the automatic backup?

---

### Post by evilc on 2008-02-25
> **Phosphoric said:**
> Same again last night. :(

How did you remove the automatic backup?

In Quickstart create a schedule backup in there delete schedule backup. Hope we can find answer to our problem  :)

---

### Post by handy on 2008-02-25
Thanks for the great script! :KS

I will explore it further as requirements dictate...

---

### Post by Phosphoric on 2008-02-25
> **evilc said:**
> In Quickstart create a schedule backup in there delete schedule backup. Hope we can find answer to our problem  :)

Thanks, didn't see that option. :)

---

### Post by mdpalow on 2008-02-25
Just a thought for those who are using scheduled back-up and would like the files placed in a location other than the desktop. If you created a scheduled back-up, you'll find a 'Cron' folder located in your /home/your_name folder. Looking in there, you'll see a file named 'My_Scheduled_Backup'

If you open that file, you'll see some 'excludes,' 'includes,' a 'cd' command, and finally the Tar/Back-up commands.

If you change the 'cd /home/your_name/Desktop' to another location - that's where the files will be placed. :)

Just remember to always do that IF/when you change the scheduled date/time.

Still trying to find what could be causing two individuals' sched. back-up to not work.

Just ran another sched. back-up on my computer and it worked fine. Still looking what it could be...

---

### Post by Phosphoric on 2008-02-25
thanks mate,

glad to see you're still on the case. :)

I'll try a good old windows favourite.  Delete the application re-boot and re-load.  You never know!

[Load in embarrassment mode].  I'm not sure how to delete  Quickstart.  I didn't aptget or Synaptic so I'm not sure what to do.  [/embarrassment mode]

---

### Post by mdpalow on 2008-02-25
> **Phosphoric said:**
> thanks mate,

glad to see you're still on the case. :)

I'll try a good old windows favourite.  Delete the application re-boot and re-load.  You never know!

[Load in embarrassment mode].  I'm not sure how to delete  Quickstart.  I didn't aptget or Synaptic so I'm not sure what to do.  [/embarrassment mode]

no problem :)

Just delete the QuickStart folder located in your home path.

However, if you have QuickStart 6.0 - there's really nothing to re-install as it's just one file. Don't think it would help.

Just out of curiosity.. your /home folder is not located in some unique path is it? For instance, mine is /home.

I know that if you re-install Ubuntu your default option for the /home path is actually different. If you used a different path somehow, the back-up wouldn't work.

---

### Post by tobydeemer on 2008-02-25
Hi-

Just a note- 

I installed Quickstart (after using it a lot myself) on a friend's laptop who wanted Ubuntu after seeing my machine, and when I used it to install the DVD codecs, it didn't get playback enabled. I don't think I missed any steps or anything, but is there something I may have forgotten to do after using the codec install feature?

Thanks,

toby

---

### Post by crgutierrez on 2008-02-25
Noticed that you added quiteinsane to your QuickStart programs, but still it does NOTt work on my 64bit 7.10. lsusb DOES list my Epson V350 Photo scanner, but so far it only works on 32 bit. Gratefull for any advice. Best

---

### Post by mdpalow on 2008-02-25
> **crgutierrez said:**
> Noticed that you added quiteinsane to your QuickStart programs, but still it does NOTt work on my 64bit 7.10. lsusb DOES list my Epson V350 Photo scanner, but so far it only works on 32 bit. Gratefull for any advice. Best

Sorry, can't help you at all on this one. I added the QuiteInsane scanner application ONLY because my friend uses it and he asked me to add this application for him when he installs. I don't even have a scanner.

---

### Post by mdpalow on 2008-02-25
> **tobydeemer said:**
> Hi-

Just a note- 

I installed Quickstart (after using it a lot myself) on a friend's laptop who wanted Ubuntu after seeing my machine, and when I used it to install the DVD codecs, it didn't get playback enabled. I don't think I missed any steps or anything, but is there something I may have forgotten to do after using the codec install feature?

Thanks,

toby

What kind of video card is in the laptop. During some testing, I remember that the install didn't always take on a laptop that had an ATI card. After some fooling around with it, it did work. I wish I could remember all the details, but it was several months ago.

Check your drivers and also make sure you have the best drivers if you went to a website and downloaded any.

Good luck...

---

### Post by oioi on 2008-02-26
Thanks a lot!
I've downloaded Quick Start and it's working great!
The once unwatchable DVD is now running like magic, and I can finally back up my files in a cinch. 

Though I do have one little question; does  Quick Start has any newer versions?
Even though I'm running  Quick Start v6.0, I only have 12 options in the  Quick Start window. 

And somehow Quick Start just doesn't appear in "Applications -> Accessories ->  Quick Start", 
but only reside on my desktop instead...  I'm running on ubuntu 7.10 32-bit.

Sorry if this question has been posted before, but I have browsed through some 20 pages but found no answer so far, and my Linux know-how is woefully little. 

Thanks again for an extremely helpful  program!

---

### Post by cmuluna on 2008-02-26
I have a conceptual question about QuickStart and upgrading to new releases of Ubuntu. Let's say I have a backup of my 7.10 system, and I want to upgrade to 8.04. Would you recommend that I use Ubuntu's built in upgrade program, and THEN create a new backup? Or should I burn an 8.04 LiveCD, wipe out my 7.10 installation, install 8.04, and restore my system with the 7.10 backup? Basically, I want to know if the backup files that QuickStart creates are version specific. I've read that completely installing new versions of Ubuntu, rather than upgrading, is the way to go. But I don't have enough experience to know for sure if that's true. Thanks for the advice!

---

### Post by mdpalow on 2008-02-26
> **oioi said:**
> Thanks a lot!
I've downloaded Quick Start and it's working great!
The once unwatchable DVD is now running like magic, and I can finally back up my files in a cinch. 

Though I do have one little question; does  Quick Start has any newer versions?
Even though I'm running  Quick Start v6.0, I only have 12 options in the  Quick Start window. 

And somehow Quick Start just doesn't appear in "Applications -> Accessories ->  Quick Start", 
but only reside on my desktop instead...  I'm running on ubuntu 7.10 32-bit.

Sorry if this question has been posted before, but I have browsed through some 20 pages but found no answer so far, and my Linux know-how is woefully little. 

Thanks again for an extremely helpful  program!

Hi Oioi,

Sounds like you have the latest version. We had 15 options up until just last week, but with the fix of a few bugs in Flash etc, it was possible to remove those functions from the program.

If for some reason your icon isn't sitting in Applications -> Accessories, you can easily enough add it there by simply going to Preferences -> and then Main Menu and adding it.

Glad you're enjoying the program and I hope it continues to help you out.

Take care...

---

### Post by mdpalow on 2008-02-26
> **cmuluna said:**
> I have a conceptual question about QuickStart and upgrading to new releases of Ubuntu. Let's say I have a backup of my 7.10 system, and I want to upgrade to 8.04. Would you recommend that I use Ubuntu's built in upgrade program, and THEN create a new backup? Or should I burn an 8.04 LiveCD, wipe out my 7.10 installation, install 8.04, and restore my system with the 7.10 backup? Basically, I want to know if the backup files that QuickStart creates are version specific. I've read that completely installing new versions of Ubuntu, rather than upgrading, is the way to go. But I don't have enough experience to know for sure if that's true. Thanks for the advice!

Hi Cmulna,

I guess to start off with I'd say - if you backed up your 7.10 system, upgraded to 8.04 and then restored your back-up, you'd essentially be back at 7.10. So, that's probably not the way to go. 

You're question is a good one though and it's got me thinking how I'm going to do it myself. After a quick think through - here's probably what I'm going to do:

I already have a really good back-up of my 7.10 system. Using it get's me to about 99% of where I want to be after using it. So, before the 8.04 ver. comes out, I'll probably clean my system with a format and use my back-up to restore it. I'll then let all the updates I didn't get since the last back-up come in and install them. I'll then make another/new back-up at that point. 

In terms of upgrading vs. clean install, I'll probably try the update process; whatever that is and see how it goes. Saw a lot of people with problems doing this from 7.04 to 7.10, but I'll try it. I will however download a copy of 8.04 and burn it to disk and be ready to use it at a moments notice if I have to.

If I had to install a clean copy of 8.04, then I would do that and only restore the '/home' back-up.

Hope this helps some...

---

### Post by cmuluna on 2008-02-26
That helps a lot. So, in essence, with a clean 8.04 install and then a restore of the home directory, that would do the same thing as having the home directory on its own partition, as many forums recommend?

I'm hoping that the upgrade procedure is easier to 8.04 as it apparently was to 7.10. Thanks again!

---

### Post by mdpalow on 2008-02-26
> **cmuluna said:**
> That helps a lot. So, in essence, with a clean 8.04 install and then a restore of the home directory, that would do the same thing as having the home directory on its own partition, as many forums recommend?

I'm hoping that the upgrade procedure is easier to 8.04 as it apparently was to 7.10. Thanks again!

If I understand you correctly, restoring the /home directory from a back-up will have nothing to do with how you partitioned your install.

If you want the /home to be a separate partition, then you have to do that during install of the OS.

---

### Post by OvenMitt Bandit on 2008-02-26
If you make a backup using QuickStart in Ubuntu, could you load it into a Xubuntu install? I doubt it because of the Gnome settings from Ubuntu, but just thought I would ask.

---

### Post by cmuluna on 2008-02-26
Ah, sorry. I see now that I wasn't clear. I meant that restoring just the home directory on a fresh install would be *essentially* the same as having the home directory on its own partition. (i.e. - all of the /home info would be there). Apologies for the confusion.

---

### Post by mdpalow on 2008-02-26
> **cmuluna said:**
> Ah, sorry. I see now that I wasn't clear. I meant that restoring just the home directory on a fresh install would be *essentially* the same as having the home directory on its own partition. (i.e. - all of the /home info would be there). Apologies for the confusion.

yeah, I'll go with that... :)

---

### Post by randiroo76073 on 2008-02-26
mdpalow, my wife sends you kisses and hugs for this nice, time saving prgm.  She was thoroughly tired of hearing me cuss/fuss every time I would mess something up and have to do a re-install. Only 1 quick question:  Do you think this will work on other debian based OS's as I am multibooted.  Myself, I don't see why not, but then I'm not a programmer.  Anyway I'll drink a toast to you!

---

### Post by mdpalow on 2008-02-26
> **randiroo76073 said:**
> mdpalow, my wife sends you kisses and hugs for this nice, time saving prgm.  She was thoroughly tired of hearing me cuss/fuss every time I would mess something up and have to do a re-install. Only 1 quick question:  Do you think this will work on other debian based OS's as I am multibooted.  Myself, I don't see why not, but then I'm not a programmer.  Anyway I'll drink a toast to you!

LOL... well, I don't know what to say about that! :)

I think the back-up and restore has a good chance of working. However, I would want to know if the config files (i.e. xconf, device.map, fstab, etc., etc.) have the same name and are located in the same folder name(s). If so, I don't see why not since we're basically using a tar command.

One thing is for sure, it shouldn't do anything bad to your system. :)

You should try it and let us know. I wrote the program for Ubuntu, but I remember one guy a while back saying he used it on another distro and that it worked. Not sure what function he used, but I DO KNOW FOR A FACT that much of the program won't work on Kubuntu as I did test that one a while back. 

Good luck...

---

### Post by money2themax on 2008-02-26
> **mdpalow said:**
> One thing is for sure, it should do anything bad to your system. :)
umm...dont you mean ```
"One thing is for sure, it should[COLOR=Red]_***n't***_[/COLOR] do anything bad to your system."
```

---

### Post by mdpalow on 2008-02-26
Yep... that's what I meant.

Just checking to make sure you all are paying attention. ;)

---

### Post by UK-Wobbie on 2008-02-26
I like to say this  QuickStart tool is F**KING TOP!
I love it :lolflag: Nice tool i got to say. Easy to use and got good stuff in it.
Can i ask about the daily backup on it. How do it make the backup? Will it make it as a ISO image. :) 

Thanks and good work =D>\\:D/:mrgreen::p

---

### Post by mdpalow on 2008-02-26
> **UK-Wobbie said:**
> I like to say this  QuickStart tool is F**KING TOP!
I love it :lolflag: Nice tool i got to say. Easy to use and got good stuff in it.
Can i ask about the daily backup on it. How do it make the backup? Will it make it as a ISO image. :) 

Thanks and good work =D>\\:D/:mrgreen::p

Thanks Wobbie...

I really wouln't make a daily back-up. Not even sure why I put that option in QuickStart. If you really want a lot of back-ups, then consider doing weekly or monthly and if you HAVE to have a back-up in between - then just do a manual one for that day.

No, TAR is not an ISO file. When you tar something, it compresses all the files into one file. However, QS will create three files for you in an effort to make it better for you in the future.

Give it a go, if you haven't already, and you'll see what I mean.

Thanks....

---

### Post by money2themax on 2008-02-27
> **mdpalow said:**
> Yep... that's what I meant.

Just checking to make sure you all are paying attention. ;)
sure yah were i believe you

---

### Post by oioi on 2008-02-27
Hello mdpalow, 

Thanks for you help! 

Quick Start is now sitting comfortably in Applications -> Accessories now. 

And now I can share ubuntu with more people! 

Its ease of using and generous help on the web certainly tops something called Vista...

Cheers!

---

### Post by Dngrsone on 2008-02-27
Wow, that was a lot of reading.

Running a backup right now; hope it helps me since I have to reinstall Ubuntu 32bit.

It looks and sounds like an awesome program.

---

### Post by UK-Wobbie on 2008-02-27
> **mdpalow said:**
> Thanks Wobbie...

I really wouln't make a daily back-up. Not even sure why I put that option in QuickStart. If you really want a lot of back-ups, then consider doing weekly or monthly and if you HAVE to have a back-up in between - then just do a manual one for that day.

No, TAR is not an ISO file. When you tar something, it compresses all the files into one file. However, QS will create three files for you in an effort to make it better for you in the future.

Give it a go, if you haven't already, and you'll see what I mean.

Thanks....

That's cool thanks :)

---

### Post by tobydeemer on 2008-02-27
> **mdpalow said:**
> What kind of video card is in the laptop. During some testing, I remember that the install didn't always take on a laptop that had an ATI card. After some fooling around with it, it did work. I wish I could remember all the details, but it was several months ago.

Check your drivers and also make sure you have the best drivers if you went to a website and downloaded any.

Good luck...

Hi-

Yes, it was an ATI card, so that makes sense. After some tinkering around, I got it to work without too much difficulty, so no worries. 

Apart from that little hiccup, I've had no bad experiences with Quickstart, and I've used it several times to run backups. I even backed up my 15GB XP partition into a single DVD. That's a nifty program that can do that. Thanks.

---

### Post by Bruce M. on 2008-02-27
Just got it, couldn't believe how easy it was to setup.... mouse-clicks.
Will try it, and post back when I have some results.

Bruce

EDIT:
[LIST=1]
[*]The setup is almost too easy.
[*] I can't believe the speed, it's very fast
[*] It has to be one of the easiest backup programs I have ***ever*** used.
[/LIST]

Have to try the W2K backup just to see. Even though I haven't used the OS since installing Ubuntu. I log in once a month or so just to let the anti-virus program upgrade it's database. Wife insists we keep it because our ISP doesn't support Linux (too many versions).

---

### Post by Jose Catre-Vandis on 2008-02-27
Thanks, will give it a try :)

---

### Post by Bruce M. on 2008-02-28
Hi mdpalow,

I downloaded version 6.0 yesterday.
Today I decided to read the first 20 pages here and make comments, ask questions etc, then continue reading.

Yesterday I used:
[LIST]
[*]Option 7 - House Cleaning
[*]Option 1 - all three /, /home, config files
[/LIST]
and today while reading:

[LIST]
[*]Option 8 - alltray, devede, k3b, k9copy, ntp, quiteinsane
[*]Option 9 Install DVD and Codecs Files - haven't tried it because I'm here.
[/LIST]

I'm going to make a new backup as I continue typing here.

I noticed in the "Help File" that version 6 has 15 options:
[LIST=1]
[*]Create a Back-Up
[*]Restore a Back-Up
[*]Create a Scheduled Back-Up
[*]Syncronize Selected Folders
[*]Back-Up and Restore Windows
[*]**Display Mounted Drives**
[*]View/Edit Config Files
[*]House Cleaning
[*]Install Common Applications
[*]Install DVD and Codecs Files
[*]**Install Flash Plugin 32/64-bit**
[*]**Install Java 6**
[*]Show/Hide Desktop Icons
[*]Display Help
[*]Download Updates for QuickStart
[/LIST]
but the **bold** options don't showup in my Version 6.0.

What happened?

> **bw44 said:**
> Just downloaded QuickStart 3.0 -- the E(mergency) R(escue) feature is great addition.
Many thanks!

Where did this go?  I see no ER!

> **bw44 said:**
> Hey, don't make it too easy ! ;)

Someone sew his lips shut with steel fishing line and then use Crazy Glue on his fingertips so if he so much as touches the keyboard....!  :lolflag:

Mankind, as a whole, is into complicating the simple things, (read a MS EULA if you don't believe me), here we have a breath of fresh air where mdpalow is simplifying something complicated (for us new to Linux) and I read this, I just couldn't help making those suggestions.  :)
[CENTER][B]
[SIZE="5"]Thank you, mdpalow,
for QuickStart![/SIZE]
and your continuing
work on improving it!
[/B][/CENTER]

---

### Post by mdpalow on 2008-02-28
Thanks Bruce...

Yes, you're right. I need to update the help file AGAIN. As Ubuntu is updated and things are either working correctly or enhanced - there becomes no need for a function in QuickStart anymore. For example... a few months ago the Flash download was broke and everyone was scrambling to find a fix, so we could have Flash on our computers. Option 11 was a fix for everyone to use that would install Flash for them. However, since it's fixed now - I took it out. Same with Java.

The mounted drives thing was a hold-over from QuickStart (back when it was called uBackup!) and really not very helpful.

The ER file should be in your QuickStart folder as a separate file. It's nothing more than a text based, back-up recovery program (ubackup! days) in case you're at the prompt and either have no graphics or zenity (application which QuickStart is based on).

Hope this helps. :) 

Take care...

---

### Post by zigx on 2008-02-28
thanks for posting this!

---

### Post by Bruce M. on 2008-02-28
> **Dragon43 said:**
> Make more stuff to make it easy for us.... :D

See Dragon43 agrees with me. See my previous post RE: fishing line and Crazy Glue  :)

> **mdpalow said:**
> I really wouln't make a daily back-up. Not even sure why I put that option in QuickStart.

This would be a nice idea, if there was a function/option like:
Number of daily backups to keep: x
Choose Daily Back-up folder: 
Say a user keeps 5 back-ups, when he creates the 6th one the oldest is deleted.

However saying that we come to what follows, making Daily Backups ... duh!:

> **mdpalow said:**
> Hi Everyone/Anyone,

I need some help making a decision.

Currently, QuickStart 4.0 will synchronize selected folders from the OS to a back-up drive or partition. As we may know by now, this can happen each hour, once a day, or once a week - depending on which schedule you select.

Leave it out... ??

If your vote is to leave it out then please tell me why we shouldn't create revisions of our sync'd files.

thanks...

*Leave it out.*
**Why:** Simple, your example is with one file only, what about multiple files that may be updated several time in the same day?
Most programs that create something (OO, Gedit, etc) can be configured to make backups (~) so they are there by default. I couldn't imagine looking at a bunch of files ending in ~1~, ~2~ and trying to decide which is which.

Remember: K.I.S.S. (Keep It Simple Stupid) which I prefer to mis-quote as: *Keep It Stupidly Simple.*

> **DoctorMO said:**
> Programmers Error, This package fails to abide by one of the programming tennants for tools: "Do one thing only and one thing well."

And God said, Remember the Swiss Army Knife, use the Icon, mdpalow!

> **money2themax said:**
> 1 small problem in the US it's illigal to have a linux distro that can play DVD for what i've heard

OK, but there are at least a couple more of us Linux users that don't reside in the US or it's territories.

> **mdpalow said:**
> Thanks Bruce...

Yes, you're right. I need to update the help file AGAIN. As Ubuntu is updated and things are either working correctly or enhanced - there becomes no need for a function in QuickStart anymore. For example... a few months ago the Flash download was broke and everyone was scrambling to find a fix, so we could have Flash on our computers. Option 11 was a fix for everyone to use that would install Flash for them. However, since it's fixed now - I took it out. Same with Java.

OH, I didn't realize that, I thought I was missing something.  :)

> **mdpalow said:**
> The mounted drives thing was a hold-over from QuickStart (back when it was called uBackup!) and really not very helpful.

Hmm, yes, I believe the option is somewhere in the menus, just can't find it.  :)

> **mdpalow said:**
> The ER file should be in your QuickStart folder as a separate file. It's nothing more than a text based, back-up recovery program (ubackup! days) in case you're at the prompt and either have no graphics or zenity (application which QuickStart is based on).

Hope this helps. :) 

Take care...

What I have in /QuickStart is:
QuickStart
QuickStart 6.0
READ ME

No ER file.  :(

I love the program though. I've been searching for a while for a good Back-up/Restore program,  [here's why]("http://ubuntuforums.org/showthread.php?t=679925").

---

### Post by mdpalow on 2008-02-28
Thanks again Bruce...

You're right. ER is no longer packaged in the download. I see I removed the command I used to use, which included the ER file into the final product.

Couple things here...

Sometimes I forget where QuickStart is in terms of functions or actual procedures or what have you because I'm not looking at it every day. There have been many, many changes and updates over the months and sometimes they all seem to overlap for me. Like now, I actually had to see for myself why ER wasn't in the download. I think I remember taking it out because IF you were to place QS on a CD/DVD, Flash Drive or some other media along with your back-ups, you should always be good because you can use the Ubuntu 7.10 Live Disk to always boot up. That's my best guess anyways as to why it's not included anymore. 

:)

---

### Post by OvenMitt Bandit on 2008-02-28
I apologize if this has been answered before, I just didn't want to sift through 50+ pages of posts to find an answer.

I backed up my /home, / , and config using QuickStart onto an external hard drive. I then reformatted my hard drive (not the external one) and reinstalled Ubuntu. I downloaded and installed QuickStart, then went to the Restore Backup option. I selected the /home restore option and pointed it towards the file on the external drive. It said that it had restored everything, and told me to reboot. I did, and when it booted back up, nothing had changed, home was just the way it was before the reboot. I'm not quite sure what happened, but it didn't restore anything. What did I do wrong?

---

### Post by perixx on 2008-02-28
> money2themax:  View Post
1 small problem in the US it's illigal to have a linux distro that can play DVD for what i've heard

Unlike in Windows, it's unlawful to playback DVD's in the U.S. and other countries, partly true (don't know why Windows is different here, because you need a separate player as well in certain cases; but you got 'Mediaplayer' shipped with it - whoever likes it -  and I guess that Mickeysoft has to pay licence fees for it's decryption algorithms). 

With open source Linux players, nobody pays license fees for anything, which is evil :) 
BUT: you can buy a regular decryption software for Linux as well (forgot what it's called - which includes paying for license fees), legalizing the decryption - not the playback, which isn't illegal at all - and you're on the 'clean' side.

Please correct me if I'm wrong...


perixx

---

### Post by mdpalow on 2008-02-28
> **OvenMitt Bandit said:**
> I apologize if this has been answered before, I just didn't want to sift through 50+ pages of posts to find an answer.

I backed up my /home, / , and config using QuickStart onto an external hard drive. I then reformatted my hard drive (not the external one) and reinstalled Ubuntu. I downloaded and installed QuickStart, then went to the Restore Backup option. I selected the /home restore option and pointed it towards the file on the external drive. It said that it had restored everything, and told me to reboot. I did, and when it booted back up, nothing had changed, home was just the way it was before the reboot. I'm not quite sure what happened, but it didn't restore anything. What did I do wrong?

Hi,

Well, it was just suggested a reboot might be necessary - and sometimes it is, but probably not for what you were doing. Let me tell you how I've done it a hundred times with perfect success each time. :)

1. Make back-up of all three  /, /home/ and config files
2. Put them somewhere safe and preferably duplicated in two places.
3. Format computer using live disk and install new OS
4. Reboot
5. Load QuickStart straight away ( I don't do anything with OS at this point)
6. Restore BOTH / and /home
7. Check to make sure restricted drivers are enabled and download any new updates
8. Make a new back-up that includes new updates

20 minutes later I'm done.

I think you should have restored both files (/ and /home) to get your system back to where you wanted it to be. If you didn't change any hardware or partition stuff since last back-up AND you had some unique display settings you want back - then restore your config files as well. If not, don't bother with it as your system is running fine as it is. :)

Hope it helps

---

### Post by Bruce M. on 2008-02-28
> **mdpalow said:**
> Thanks again Bruce...

You're right. ER is no longer packaged in the download. I see I removed the command I used to use, which included the ER file into the final product.

Couple things here...

Sometimes I forget where QuickStart is in terms of functions or actual procedures or what have you because I'm not looking at it every day. There have been many, many changes and updates over the months and sometimes they all seem to overlap for me. Like now, I actually had to see for myself why ER wasn't in the download. I think I remember taking it out because IF you were to place QS on a CD/DVD, Flash Drive or some other media along with your back-ups, you should always be good because you can use the Ubuntu 7.10 Live Disk to always boot up. That's my best guess anyways as to why it's not included anymore. 

:)

You *"forget where QuickStart is in terms of functions or actual procedures"*.
Well, gee, no wonder, I just read through 85% of this thread (to see the progress in action) and you've one busy little programmer!  Completely understandable.

Have you ever thought of QS working directly with a CD R/W, DVD R/W?
I mean it would be great:
Weekly back-ups to second HD
Monthly Back-Ups to a DVD
Check the Monthly backup - if good, delete the weeklies and start again.

Just a thought
Bruce

---

### Post by CanonKen on 2008-02-29
> **Phosphoric said:**
> I noticed that they were effectively empty.  For example the /home_backup was only 20 bytes. :confused:
I've only used the manual option but I thought i'd try the scheduled one out and see what happened, I only get the file thats 20 bytes too :confused:
I've looked in the backup files and I get:
/home is empty
Config as got boot and etc
when I try and open the system backup I get a dialog box pops up saying "An error occurred while loading the archive."
If i select the "command line output" it says
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

---

### Post by mdpalow on 2008-03-01
Sorry, but as with the others - I don't know what the problem could be. It's pretty simple really. QuickStart creates two entries in the crontab file. One is simply for the pop-up window telling you a back-up is about to ocurr and the other is the path to the script, which is located in the Cron folder. In the Cron folder, the script is pretty straight forward with some basic Tar commands. If you're getting the three files placed on your desktop, then we at least know the script is being read. Why it's not doing what it's supposed to for you and a few others is the question. Since the first person posted this type of message I ran a test with my system and it worked perfectly, so I don't know why it wouldn't work on yours and a few others.

Also, since the script is in the Cron folder, you can look at it and see the programming for yourself.

I'll take another look tomorrow to see if I can find anything...

---

### Post by CanonKen on 2008-03-01
Thanks mdpalow,
I've no idea what any of that means in them files to be honest.

I take it the $ex01 $ex02 etc is excluding ex01="--exclude=system_backup_*.tgz" and 
ex02="--exclude=home_backup_*.tgz"

Can it be anything to do with the /home listed in the quote below?
```
tar cvpzf home_backup_`date +%Y.%m.%d`.tgz $ex01 $ex02 $ex03 $ex09 $ex10 $ex16 $ex17 $ex18 /home
```
Like I say, I'm only guessing really, no idea what any of that means

---

### Post by mdpalow on 2008-03-01
> **CanonKen said:**
> when I try and open the system backup I get a dialog box pops up saying "An error occurred while loading the archive."
If i select the "command line output" it says
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

Ken,

This is also a message you would get if you tried to access the back-up file BEFORE it was finished creating it. You sure it was done backing up before you attempted to look inside the archive?

thanks...

---

### Post by Bruce M. on 2008-03-01
@ mdpalow

Do you know if QuickStart works in **Xbuntu 7.10**?

I have Install_QuickStart.sh sitting on my desktop, but right-clicking and looking in permissions there is **no**: Make executable option there.

haven't tried:

```
chmod 755 /Desktop/Install_QuickStart.sh
```

Since I'm not sure it will work in XFCE.  :(
But I sure am hoping you have good news for me.

Bruce

**EDIT:** Never mind, it works fine.

---

### Post by emshains on 2008-03-02
Still cant run any dvd movie. It wont start little miss sunshine on Totem, but it will run on mplayer, only it looks like i dont have any codecs. Anyone who knows how to fix it ?

---

### Post by mdpalow on 2008-03-02
> **emshains said:**
> Still cant run any dvd movie. It wont start little miss sunshine on Totem, but it will run on mplayer, only it looks like i dont have any codecs. Anyone who knows how to fix it ?

Did you use QuickStart to install the codecs files for your particular Ubuntu OS?

---

### Post by tdrusk on 2008-03-02
I'm using this right now. Great job.

---

### Post by bw44 on 2008-03-03
mdpalow,

You recently answered someone's question about how to use QuickStart to help to restore your system after a fresh install.  That got me to thinking about the coming upgrade to Hardy Heron (8.04).

Is there any reason not to use QuickStart as it exists "out-of-the-box" with the new version of Ubuntu? Do you think it be necessary and, if so, will you have time (he asked, hopefully) to install 8.04 and check it out for any release dependencies?

Thanks.

bw44

---

### Post by say2sky on 2008-03-03
> [COLOR="Red"]15. Back-up Your Windows Partition (dual booters) While in Ubuntu[/COLOR].

[COLOR="Red"]18. Restore Your Windows Back-Up While in Ubuntu[/COLOR].


Your planned features include backup Windows partition, would you give some idea about if it is directory tree backup or bit-to-bit backup which includes meta data?

Thanx!

---

### Post by Bruce M. on 2008-03-04
A Classic example of **RTFI**
[CENTER]**[SIZE="4"]R[/SIZE]**ead **[SIZE="4"]T[/SIZE]**he **[SIZE="4"]F[/SIZE]**ull **[SIZE="4"]I[/SIZE]**nstructions[/CENTER]

I recently did a backup of my /home folder that was empty. ](*,)

[CENTER]
[[IMG]http://img233.imageshack.us/img233/2940/rtfinp6.th.jpg[/IMG]](http://img233.imageshack.us/my.php?image=rtfinp6.jpg)
[/CENTER]

**NOW** I notice the third sentence.

Works like a charm when one applies: **RTFI** \\:D/

---

### Post by bw44 on 2008-03-04
> **Bruce M. said:**
> A Classic example of **RTFI**
[CENTER]**[SIZE="4"]R[/SIZE]**ead **[SIZE="4"]T[/SIZE]**he **[SIZE="4"]F[/SIZE]**ull **[SIZE="4"]I[/SIZE]**nstructions[/CENTER]

I recently did a backup of my /home folder that was empty. ](*,)

[CENTER]
[[IMG]http://img233.imageshack.us/img233/2940/rtfinp6.th.jpg[/IMG]](http://img233.imageshack.us/my.php?image=rtfinp6.jpg)
[/CENTER]

**NOW** I notice the third sentence.

Works like a charm when one applies: **RTFI** \\:D/That's cool -- I know others have made the same mistake.  I've done it at least once!

Are you aware of the include attachments (like screen shots) feature of the forum?  It would be quicker, probably for you, and certainly for the reader, if you used it. Check under additional options the next time you post and try "Manage Attachments". (Just a suggestion!)

Cheers

---

### Post by mdpalow on 2008-03-04
> **Bruce M. said:**
> A Classic example of **RTFI**
[CENTER]**[SIZE="4"]R[/SIZE]**ead **[SIZE="4"]T[/SIZE]**he **[SIZE="4"]F[/SIZE]**ull **[SIZE="4"]I[/SIZE]**nstructions[/CENTER]

I recently did a backup of my /home folder that was empty. ](*,)

[CENTER]
[[IMG]http://img233.imageshack.us/img233/2940/rtfinp6.th.jpg[/IMG]](http://img233.imageshack.us/my.php?image=rtfinp6.jpg)
[/CENTER]

**NOW** I notice the third sentence.

Works like a charm when one applies: **RTFI** \\:D/

Don't feel bad... I've done it myself once or twice when I was doing a back-up real quick and forgot which window I was on and just clicked Ok.

Just in case someone missed it or doesn't understand I'll write it here.

Because of several requests, I programmed QuickStart to offer you an opportunity to EXCLUDE directories from a /HOME back-up. If you want to EXCLUDE any directories, you have to select them and then press Ok. If you don't want to EXCLUDE anything you must click the CANCEL button. If you don't read the pop-up window just before and click the Ok button, you will essentially be telling QuickStart you don't want to back-up anything because by default, the file manager (window you use to select excluded folders) is sitting on your /HOME folder. So, by pressing Ok, you're essentially telling QuickStart to NOT back-up anything.

I wish this explained the non-working, Scheduled back-up phenomenon.

:)

---

### Post by mdpalow on 2008-03-04
> **bw44 said:**
> mdpalow,

You recently answered someone's question about how to use QuickStart to help to restore your system after a fresh install.  That got me to thinking about the coming upgrade to Hardy Heron (8.04).

Is there any reason not to use QuickStart as it exists "out-of-the-box" with the new version of Ubuntu? Do you think it be necessary and, if so, will you have time (he asked, hopefully) to install 8.04 and check it out for any release dependencies?

Thanks.

bw44

Hi Bw44,

Sorry for the late reply to you and others. I didn't realize I had more posts waiting for me to answer.

It think QuickStart is going to work 'out of the box' with 8.04 and see no reason why you couldn't/shouldn't use it. Yeah, I'll be upgrading and checking it against QuickStart to make sure it's all in order.

---

### Post by mdpalow on 2008-03-04
> **say2sky said:**
> Your planned features include backup Windows partition, would you give some idea about if it is directory tree backup or bit-to-bit backup which includes meta data?

Thanx!

Sorry for the late reply..

The Windows partition back-up is a bit2bit back-up of all data on that drive/partition.

---

### Post by Bruce M. on 2008-03-04
> **bw44 said:**
> Are you aware of the include attachments (like screen shots) feature of the forum? (Just a suggestion!)

Yes, I'm aware of it, but I think there is a limit, I may be wrong.
Thanks for the suggestion though.
Bruce

---

### Post by Bruce M. on 2008-03-04
> **mdpalow said:**
> Don't feel bad... I've done it myself once or twice when I was doing a back-up real quick and forgot which window I was one and just clicked Ok.

You too!  I don't feel so bad now.  :)

If I may make a suggestion of a small change next time you are editing things:

> You selected the /home folder to be archived.

[SIZE="4"]**NOTE:**[/SIZE] If you do **NOT** wish to exclude any folders, select **[Cancel]** in the next window.

To select folders to EXCLUDE from this archive, in the next window, press [CTRL] while making your selections. Then press [OK] when done.

> **mdpalow said:**
> I wish this explained the non-working, Scheduled back-up phenomenon.

Not working? Mine seems to be.
Mind you I chose the: Do the first one now option.
I'll have to check tomorrow and see it it was updated.

---

### Post by mdpalow on 2008-03-04
Unfortunately the pop-up window doesn't allow for bolding, character sizing, etc... Pretty limited.

Would be easier to just take it all out and have it back-up everything, but that's not good either 'cause I know there are times where you don't need/want to back-up everything in the /home directory.

thanks...

---

### Post by bw44 on 2008-03-04
> **Bruce M. said:**
> Yes, I'm aware of it, but I think there is a limit, I may be wrong.

Bruce

No, you're right: there are individual size limits and maybe with  number of attachments. But I've never found it too restrictive, and the advantage is the attachments should never get separated from the post for any reason.  

That being said, I kind of like the fact that your image attachment appears right in the body of your message -- that's a plus.

(mdpalow: sorry to go off-topic on this!)

bw44

---

### Post by imon9 on 2008-03-04
hello mdpalow, 

thanks for the nice piece of "software" / script u wrote for everyone...
due to some reason, i need to uninstall Quickstart but don't know how to do it cleanly.

can u tell me how? (also, it would be nice to add an option to uninstall it, since it is not listed in the synaptic)

thanks in advance :)

---

### Post by mdpalow on 2008-03-04
> **bw44 said:**
> 

(mdpalow: sorry to go off-topic on this!)

bw44

no problem. :) I was actually going to answer myself, but couldn't remember the facts 100%. Was going to say I think it's restricted to 1MB for pics.

---

### Post by mdpalow on 2008-03-04
> **imon9 said:**
> hello mdpalow, 

thanks for the nice piece of "software" / script u wrote for everyone...
due to some reason, i need to uninstall Quickstart but don't know how to do it cleanly.

can u tell me how? (also, it would be nice to add an option to uninstall it, since it is not listed in the synaptic)

thanks in advance :)

You're welcome.

No problem. It's very easy. Just go to /home/your_name and look for a folder called QuickStart. Delete it and you're done. :)

It's not like other programs that install themselves everywhere or have config folders..etc.. Just one file that does it all.

Take care

P.S. Good idea to do something for uninstall. Might remove any confusion. Thanks for the suggestion.

---

### Post by imon9 on 2008-03-04
> **mdpalow said:**
> You're welcome.

No problem. It's very easy. Just go to /home/your_name and look for a folder called QuickStart. Delete it and you're done. :)

It's not like other programs that install themselves everywhere or have config folders..etc.. Just one file that does it all.

Take care

P.S. Good idea to do something for uninstall. Might remove any confusion. Thanks for the suggestion.

thanks for the prompt reply, though after i remove that folder, the entry remains in my "start menu"/// now i am doing a full search over the file system for it to delete it... hope u are aware of that

---

### Post by money2themax on 2008-03-04
:KSthey need to add this to the programs list:KS

---

### Post by mdpalow on 2008-03-04
Yeah, the icon would stay in the menu. Simply go to System -> Preferences -> Main Menu and just delete the icon.

thanks..

---

### Post by money2themax on 2008-03-05
> **money2themax said:**
> :KSthey need to add this to the programs list:KS

no no no you mis under stand me i mean as a program you know like when you add vlc or firefox thru the add/remove program

---

### Post by Dngrsone on 2008-03-05
> **money2themax said:**
> no no no you mis under stand me i mean as a program you know like when you add vlc or firefox thru the add/remove program

In other words, you want it in a repository so it can be uploaded/added through Synaptic?

---

### Post by DamonChyld on 2008-03-05
I am new to ubuntu/linux and keep feeling the need to do a fresh install after trying a new package and finding unexpected results, even after a complete removal of the offending package. I would like to use QuickStart to clone my system so that I will be able to restore to a previous state with programs/packages installed after one of these blunders, but seem to keep running into difficulties.

I have tried to restore with the backups on the same drive but that causes ubuntu to freeze on restart. I have tried restoring from a removable drive but that immediately gives the output "Restore Finished! [...] It may be necessary to reboot your computer." and does not make any changes. I suppose my last option would be to backup to a dvd but I don't want to use a static media if at all possible.

I am sure that I am doing something wrong but have been unable to discover what after extensive searching. I have been tempted to switch over to sbackup but would rather use quickstart as it seems to be the most supported/widely used backup app, and I love the full feature set.

Can someone clue me in? Thanks all!

---

### Post by altonbr on 2008-03-05
@mdpalow:

Have you considered asking QuickStart to be included in Hardy or Hardy+1 on brainstorm.ubuntu.com. I see all sorts of posts regarding a "dead simple backup program is needed" and I'll reply, "Have you heard of QuickStart?" and post a link, but that's not good enough.

Maybe add an idea that says "Include QuickStart in Hardy or Hardy+1", link it to this thread, and see how it goes.

Hope that helps!

---

### Post by Bruce M. on 2008-03-05
> **altonbr said:**
> @mdpalow:

Have you considered asking QuickStart to be included in Hardy or Hardy+1 on brainstorm.ubuntu.com. I see all sorts of posts regarding a "dead simple backup program is needed" and I'll reply, "Have you heard of QuickStart?" and post a link, but that's not good enough.

Maybe add an idea that says "Include QuickStart in Hardy or Hardy+1", link it to this thread, and see how it goes.

Hope that helps!

+1 : GREAT idea, I'd support it.

---

### Post by mdpalow on 2008-03-05
> **DamonChyld said:**
> I am new to ubuntu/linux and keep feeling the need to do a fresh install after trying a new package and finding unexpected results, even after a complete removal of the offending package. I would like to use QuickStart to clone my system so that I will be able to restore to a previous state with programs/packages installed after one of these blunders, but seem to keep running into difficulties.

I have tried to restore with the backups on the same drive but that causes ubuntu to freeze on restart. I have tried restoring from a removable drive but that immediately gives the output "Restore Finished! [...] It may be necessary to reboot your computer." and does not make any changes. I suppose my last option would be to backup to a dvd but I don't want to use a static media if at all possible.

I am sure that I am doing something wrong but have been unable to discover what after extensive searching. I have been tempted to switch over to sbackup but would rather use quickstart as it seems to be the most supported/widely used backup app, and I love the full feature set.

Can someone clue me in? Thanks all!

Let me suggest going back a few days in this thread and read a message I posted about how I do a restore. It might help you. If you can't find it or it doesn't work for you, let me know. I always do a restore from another drive after reinstalling a fresh copy of the OS. After install, I go DIRECTLY to restore without doing anything else first.

Let me know if you have problems after all this. :

Thanks

---

### Post by mdpalow on 2008-03-05
> **altonbr said:**
> @mdpalow:

Have you considered asking QuickStart to be included in Hardy or Hardy+1 on brainstorm.ubuntu.com. I see all sorts of posts regarding a "dead simple backup program is needed" and I'll reply, "Have you heard of QuickStart?" and post a link, but that's not good enough.

Maybe add an idea that says "Include QuickStart in Hardy or Hardy+1", link it to this thread, and see how it goes.

Hope that helps!

Thanks altonbr...

I would consider it, but I'm getting too many people telling me that my Scheduled Back-up isn't working for them.

Seems silly suggesting QuickStart when one of it's better functions isn't working on everyone's computer.

I'm still looking into that though..

---

### Post by DamonChyld on 2008-03-05
Thanks for getting back to me mdpalow.

After you last message I made new Quickstart restores of /, /home, and config, reinstalled ubuntu from a live cd, installed quickstart, opened quickstart from applications > accessories, selected option 2 (Restore a Back-up), selected 'restore /' and directed to the system backup from my external usb drive, and said ok. I_ immediately_ get a popup saying "Restore finished! [...] It may be necessary to reboot your computer". 

After a restart nothing has changed. I have tried the above process with "restore /home" with the same results. Do you know what I might be doing wrong?

> Hi,

Well, it was just suggested a reboot might be necessary - and sometimes it is, but probably not for what you were doing. Let me tell you how I've done it a hundred times with perfect success each time.

1. Make back-up of all three /, /home/ and config files
2. Put them somewhere safe and preferably duplicated in two places.
3. Format computer using live disk and install new OS
4. Reboot
5. Load QuickStart straight away ( I don't do anything with OS at this point)
6. Restore BOTH / and /home
7. Check to make sure restricted drivers are enabled and download any new updates
8. Make a new back-up that includes new updates

20 minutes later I'm done.

I think you should have restored both files (/ and /home) to get your system back to where you wanted it to be. If you didn't change any hardware or partition stuff since last back-up AND you had some unique display settings you want back - then restore your config files as well. If not, don't bother with it as your system is running fine as it is.

Hope it helps

---

### Post by mdpalow on 2008-03-05
Can you check your /, /home, and config back-up files and tell me how large/big they are? 

Thanks..

---

### Post by DamonChyld on 2008-03-05
Config 3.2k
Home 12.3mb
System 1gb

---

### Post by mdpalow on 2008-03-05
> **DamonChyld said:**
> Config 3.2k
Home 12.3mb
System 1gb

looks good. When you reformatted the OS and re-installed, did you put the / and /home directories as such or did you leave the default (2nd time around) to /media/ and /media/home or did you remove the "/media"  ?

Also, when you restore - you realize you have to do each back-up file separately, right? It's not like back-up where you select all three and then walk away. On restore, you have to do / and then when it's finished you do /home.

thanks

---

### Post by DamonChyld on 2008-03-05
Yes, I named my / dir / and my /home dir /homeon the new install. I used the option to create my own partitions (not the guided) and formatted them as well. The drive is formatted ntfs, could this be issue? It is recognized immediately by machine and I am able to read/write to it though.

---

### Post by mdpalow on 2008-03-05
> **DamonChyld said:**
> Yes, I named my / dir / and my /home dir /homeon the new install. I used the option to create my own partitions (not the guided) and formatted them as well. The drive is formatted ntfs, could this be issue? It is recognized immediately by machine and I am able to read/write to it though.

Nice when people start giving real details and not just saying something doesn't work. :)

Yeah, I would think it being NTFS is keeping it from working correctly.

---

### Post by DamonChyld on 2008-03-05
Sorry mdpalow, I am a few weeks into linux... tried to give all relevant info but I am still trying to get it all worked out!

I used parted magic to create a ext3 partition on the drive and it looks to be working now. Thank you for your help

---

### Post by DamonChyld on 2008-03-05
Hmm, another issue now though... when I try to restore /home the quickstart windows close (configuration files window stays open with nothing in it) and it appears to just be sitting there. 

I have let it be for about 10 min and nothing has changed. When I go to restart I have suspend and hibernate as options but no shut down or restart.

Also, if I try to start quickstart again it says 'starting quickstart' on the bottom panel and then quits

---

### Post by mdpalow on 2008-03-05
> **DamonChyld said:**
> Sorry mdpalow, I am a few weeks into linux... tried to give all relevant info but I am still trying to get it all worked out!

I used parted magic to create a ext3 partition on the drive and it looks to be working now. Thank you for your help

no problem. glad it works. Sorry if you misunderstood me. I meant that I was glad you gave me that little extra bit of information. A lot of times I will just get it doesn't work and I don't get anything else. I was saying it was nice that you gave me more. :)

thanks and glad it's working for you.

---

### Post by mdpalow on 2008-03-05
> **DamonChyld said:**
> Hmm, another issue now though... when I try to restore /home the quickstart windows close (configuration files window stays open with nothing in it) and it appears to just be sitting there. 

I have let it be for about 10 min and nothing has changed. When I go to restart I have suspend and hibernate as options but no shut down or restart.

Also, if I try to start quickstart again it says 'starting quickstart' on the bottom panel and then quits

Looking at this now.... give me a few minutes to reply.

---

### Post by money2themax on 2008-03-05
> **Dngrsone said:**
> In other words, you want it in a repository so it can be uploaded/added through Synaptic?
YES! exactly that what i was trying to say i just couldn't remember the word

---

### Post by DamonChyld on 2008-03-06
Thank you very much for all your help mdpalow! He has been pm'ing me back and forth all day about this but we got it figured out ;)

Tip: If you don't have restart or shutdown after doing a restore try restarting x by ctrl, alt, backspace and that should restore em for you.

---

### Post by mudora on 2008-03-06
mdpalow,

Good job! QuickStart works great! It saved me hours after re-installing ubuntu (which won't happen again thanks to you) because I'm going to try your Backup tool. ;)

Sorry if this has already been suggested but is it possible to have a progress bar while QuickStart is working? Or have a list of which files it is installing/downloading? For e.g Totem 100%, XXX 25%, At one point, I wasn't sure QuickStart was working, so a progress bar of some sort would give an approx. time left.

Many thanks again!

mudora

---

### Post by bw44 on 2008-03-06
> **DamonChyld said:**
> Thank you very much for all your help mdpalow! He has been pm'ing me back and forth all day about this but we got it figured out ;)

Tip: If you don't have restart or shutdown after doing a restore try restarting x by ctrl, alt, backspace and that should restore em for you.Glad to hear you got it working, and, yes, mdpalow has got to be one of the most helpful people on the forums!

Could you clarify your tip?  What did you mean by "you don't have rstart or shutdown" after doing a restore?  Did you mean that when you click the "off" (?) button in the upper right corner of the desktop that they don't appear on the menu with the other options?

And what happens when you do a ctrl, alt, backspace?  I've heard you can use that sequence if you get locked out of your desktop, but I tried it once and it didn't do anything.  Does it reboot you, or just restart the desktop?  Was anything else missing before you did it?

Thanks.

---

### Post by mdpalow on 2008-03-06
thanks bw44....

He just means that after you're done restoring, you might not have the option to shutdown or restart your system. I've always done a logout/login and then reboot.

Also... for everyone...

[SIZE="3"][COLOR="Red"]**There's a fix out tonight.**[/COLOR]
[/SIZE]
I found an omission in code that was causing the files to NOT be displayed in the pop-up window when restoring. Very surprised to have missed that. I know it doesn't always show for the configuration files because I have a short delay built in and sometimes the configuration file is done restoring before it ever makes it to the window. Shouldn't have happened with / or /home, but it was.... fixed now.

Anyways, please update your QuickStart program when you have a chance.

---

### Post by mdpalow on 2008-03-07
> **DamonChyld said:**
> Thank you very much for all your help mdpalow! He has been pm'ing me back and forth all day about this but we got it figured out ;)

Tip: If you don't have restart or shutdown after doing a restore try restarting x by ctrl, alt, backspace and that should restore em for you.

To make a long story short... his restore of /home didn't seem to be working properly. I re-did my laptop with Ubuntu to test some complaints, but couldn't recreate the problem. His problems seemed to fix themselves on another attempt when it worked as expected. Just another example of gremlins. 

At least my look into his problems did make me realize there was some code missing in the restore feature that causes the restored files to not be shown in the pop-up window.

Also, since I installed a fresh copy of Ubuntu 7.10, I thought I would run a scheduled back-up to see if it would work since some people are having problems with it.

I'll admit the first time it didn't work properly for some reason. I went to add 'mailx' to do some troubleshooting and because it will tell me sometimes what a problem might be and why something isn't working.

I installed it and went to run the scheduled back-up again and it worked. Now MAILX doesn't have anything to do with back-up, so it wasn't that I'm sure.

I deleted the schedule, rebooted and created another schedule (just now), and ran a scheduled back-up and as I type this it's backing up the / directories.

So this is becoming the real gremlin...

---

### Post by mdpalow on 2008-03-07
> **mudora said:**
> mdpalow,

Good job! QuickStart works great! It saved me hours after re-installing ubuntu (which won't happen again thanks to you) because I'm going to try your Backup tool. ;)

Sorry if this has already been suggested but is it possible to have a progress bar while QuickStart is working? Or have a list of which files it is installing/downloading? For e.g Totem 100%, XXX 25%, At one point, I wasn't sure QuickStart was working, so a progress bar of some sort would give an approx. time left.

Many thanks again!

mudora

Thanks mudora...

Sorry, but an actual progress bar that tells you percentages isn't possible right now. Apparently, the zenity progress bar isn't that good and won't do what you're asking. Also, it's been a while (I'd have to look into this again to be sure this is actually true), but I think I remember you needed to know what files are being installed, so you can put % markers in between. Since I have no control over:

1. What you are planning on installing

2. More importantly... what files are actually downloaded and installed from the repositories

I can't put markers anywhere to give you a % complete.

Hope all that makes sense. Bottom line... I agree and would have done it like you suggest if I could have. Tried in the beginning, but no joy...

Thanks...

---

### Post by mudora on 2008-03-08
> **mdpalow said:**
> Thanks mudora...

Sorry, but an actual progress bar that tells you percentages isn't possible right now. Apparently, the zenity progress bar isn't that good and won't do what you're asking. Also, it's been a while (I'd have to look into this again to be sure this is actually true), but I think I remember you needed to know what files are being installed, so you can put % markers in between. Since I have no control over:

1. What you are planning on installing

2. More importantly... what files are actually downloaded and installed from the repositories

I can't put markers anywhere to give you a % complete.

Hope all that makes sense. Bottom line... I agree and would have done it like you suggest if I could have. Tried in the beginning, but no joy...

Thanks...
It's ok mdpalow! :) It was not that important anyway. Thank you for such a user-friendly script!

---

### Post by jryprt on 2008-03-10
Hi I only have 12 options your 1st post has 19 now how do I get the rest ?
I did the # 12 Download updates . Still the same.

---

### Post by bw44 on 2008-03-10
> **jryprt said:**
> Hi I only have 12 options your 1st post has 19 now how do I get the rest ?
I did the # 12 Download updates . Still the same.You'll have to wait for mdpalow to explain why for various reasons the others were removed, but the 12 options you have with the latest download are the "official" supported functions.  You're not missing anything!

Cheers

PS.  Actually, if you read back through the posts on this thread, you'll find discussions and explanations of why the original functions were dropped.

---

### Post by evilc on 2008-03-10
mdpalow,

Just to let you know the schedule backups now working. What I did was to install mailx, for some reason this seemed to fix our problem :confused:. Will have to see what mailx is exactly.

---

### Post by mdpalow on 2008-03-10
> **evilc said:**
> mdpalow,

Just to let you know the schedule backups now working. What I did was to install mailx, for some reason this seemed to fix our problem :confused:. Will have to see what mailx is exactly.

Are you kidding me!

WTH.

Mailx shouldn't have anything to do with this. However, I did have mailx installed when I programmed QuickStart.

We need someone else to install this and see if their Scheduled Back-up works then.

VERY glad you posted this. If it proves true, then I'll update QuickStart to install it. 

Thanks..

P.S. Any volunteers? :)

---

### Post by mdpalow on 2008-03-10
If you just made a download of QuickStart, you have the latest version. I just haven't updated the pictures on the first posting.

Thanks...

---

### Post by evilc on 2008-03-10
> **mdpalow said:**
> Are you kidding me!


P.S. Any volunteers? :)

Have pm the other person who had the same problem to run it also.

---

### Post by mdpalow on 2008-03-10
Not sure that its MAILX.

Just uninstalled it, rebooted, and then ran scheduled back-up and it still works on my machine. In fact, it's backing up right now.

I wish I could remember the command that tells you everything you have installed on your computer. I could look at it and see if there's anything that might be making it work. However, I did just do a clean install on my laptop and scheduled back-up did work on the second go around. Not sure why it needed two times.

---

### Post by evilc on 2008-03-11
OK Just climbed off the ceiling :) uninstalled mailx and tried a new schedule... it is now working?? I have, since the first post saying it failed, have only had Ubuntu updates and checked today for update to Quickstart. I installed mailx after reading another post so I tried it. I have setup a schedule for Sunday and
if that works ( I expect it to),  we can put it down to a glitch that's been cleaned up by an update.

---

### Post by Het Irv on 2008-03-11
You have to love the problems that fix themselves.  I am working on getting a Virtual Box up and running, one of the things I am going to try is QS6 on 8.04(a6). It may be a while before I get to it though.  I will keep you updated.  I also have some other distros that I may try it on.

---

### Post by Bruce M. on 2008-03-11
**@ mdpalow**

Tuesday 11 Mar 2008
Downloaded new update.
@ 17:10 - Scheduled Backup to start in 5 minutes @17:15
Will keep you posted.

Bruce
**EDIT: 11 Mar 2008 @ 17:32** - home empty - installing mailx - will try after that.
**EDIT: 11 Mar 2008 @ 18:22** - installed mailx - ran a Scheduled Backup - *worked beautifully*!

I would be inclined to think it's not mailx so much as maybe of the the dependencies.
I'm going to delete "mailx" leaving the dependencies and see what happens with a new test.

**EDIT: 11 Mar 2008 @ 19:20** - deleted mailx - not the dependencies and ran a Scheduled Backup - *worked beautifully*!

It has to be one of the dependencies that mailx needs.

---

### Post by CanonKen on 2008-03-11
Looks like there is something in this, after installing mailx i'm 9 mins into a scheduled backup and according to the properties of the /home backup its now at 2.8gb and still going - will confirm when its finished

Edit - backup complete now and worked like it should

---

### Post by evilc on 2008-03-11
> **Bruce M. said:**
> **@ mdpalow**

Tuesday 11 Mar 2008
Downloaded new update.
@ 17:10 - Scheduled Backup to start in 5 minutes @17:15
Will keep you posted.

Bruce
**EDIT: 11 Mar 2008 @ 17:32** - home empty - installing mailx - will try after that.
**EDIT: 11 Mar 2008 @ 18:22** - installed mailx - ran a Scheduled Backup - *worked beautifully*!

I would be inclined to think it's not mailx so much as maybe of the the dependencies.
I'm going to delete "mailx" leaving the dependencies and see what happens with a new test.

**EDIT: 11 Mar 2008 @ 19:20** - deleted mailx - not the dependencies and ran a Scheduled Backup - *worked beautifully*!

It has to be one of the dependencies that mailx needs.

Yup that's what I did too, agree with you on dependencies I think the pre-installed version of mailx was missing something.

---

### Post by bw44 on 2008-03-11
> **evilc said:**
> Yup that's what I did too, agree with you on dependencies I think the pre-installed version of mailx was missing something.Me too!  Good detective work, Bruce M.! The packages that QuickStart scheduled back-up depends on are exim4, exim4-base, exim4-config, and exim4-daemon-light. If you elect to install exim4 with Synaptic it includes the other three exim4 modules automatically.  (mailx requires these exim4 packages also, plus liblockfile1, but neither mailx nor liblockfile1 is required for QuickStart -- based on my tests, anyway.)  

I wonder why?  I noticed two, probably unrelated, things while testing the scheduled backup: 1) I don't get the QuickStart popup displayed for 20 seconds when my scheduled backup starts.  It plays the little wav file but there's no message.  2) The other thing is that it doesn't require entering my admin password (which is obviously the way it **should** work), and I wondered if to accomplish this QuickStart uses some function for scheduled backups that it doesn't for user-initiated ones. 

No doubt in time mdpalow will solve the mystery. :)

---

### Post by bw44 on 2008-03-11
> **mdpalow said:**
> Not sure that its MAILX.
. . .
I wish I could remember the command that tells you everything you have installed on your computer. I could look at it and see if there's anything that might be making it work. . . .I don't think it  is mailx (see my previous post).

The command ```
dpkg --get-selections  >  ~/Desktop/pkgs_installed
``` will put a list of currently  installed packages in a file on your desktop.

---

### Post by evilc on 2008-03-12
> **bw44 said:**
> I don't think it  is mailx (see my previous post).



Just done a test I installed gutsy on new hard drive and checked if mailx was installed, it's not. I then tried to run Quickstart schedule, not working Ithen installed mailx and tried again.. worked. It has to do with one of the mailx files for sure.

---

### Post by bw44 on 2008-03-12
> **evilc said:**
> Just done a test I installed gutsy on new hard drive and checked if mailx was installed, it's not. I then tried to run Quickstart schedule, not working Ithen installed mailx and tried again.. worked. It has to do with one of the mailx files for sure.Sorry, I didn't make myself clear.  If you install mailx, Synaptic will force the installation of exim4, exim4-base, exim4-config, and exim4-daemon-light and also something called liblockfile1. But mailx and liblockfile1 are not required for QuickStart scheduled backup to work.  On my system I do NOT have mailx or liblockfile1 installed, but DO have the four exim4 packages.

I'm not suggesting you bother to test it -- the point is to get QuickStart scheduled backup to work, and you're right, installing mailx acccomplishes this.  But for purposes of figuring out why QuickStart scheduled backups haven't been working, it looks to me like the exim4 stuff is what's important not mailx per se.

Exim4 is a replacement for an old mail transport agent (MTA) called sendmail.  Why QuickStart scheduled backup would need it, only mdpalow may be able to figure out.  I haven't a clue!

Cheers.

---

### Post by mdpalow on 2008-03-13
> 2) The other thing is that it doesn't require entering my admin password (which is obviously the way it should work), and I wondered if to accomplish this QuickStart uses some function for scheduled backups that it doesn't for user-initiated ones.

Hey BW...

If I remember right, the reason for not having to put in your password is because I set the scheduled back-up to be run by ROOT from Cron. When you're doing a regular back-up, you're doing it from your own account and NOT root.

This is good news about the MAILX. I admit that after saying I wasn't sure that was it, I was considering the possible dependencies. When I uninstalled it - to test - I did a 'sudo apt-get remove mailx,' which as you know doesn't removed dependencies. 

I think I might have to add some code to ensure MAILX is installed when running QuickStart. Keep an eye out for and update soon.

Thanks for EVERYONE's involvement and help in figuring this out.

---

### Post by Bruce M. on 2008-03-13
> **mdpalow said:**
> Thanks for EVERYONE's involvement and help in figuring this out.

It's we who owe you a vote of Thanks mdpalow.

You've made a lot of things simple for us with your work and dedication.

Helping out when and where we can is only helping you to help us even more.

```

sudo apt-get Standing_Ovation_for_mdpalow!

```

---

### Post by mdpalow on 2008-03-13
> **Bruce M. said:**
> It's we who owe you a vote of Thanks mdpalow.

You've made a lot of things simple for us with your work and dedication.

Helping out when and where we can is only helping you to help us even more.

```

sudo apt-get Standing_Ovation_for_mdpalow!

```

LOL :)    Thanks Bruce

---

### Post by mdpalow on 2008-03-13
[COLOR="Red"][SIZE="3"]NEW UPDATE AVAILABLE[/SIZE][/COLOR]

Ok, I ran a test with a friend and it appears the schedule back-up worked for him too after installing MAILX.

What a wierd coincidence that when I was creating QuickStart I used MAILX to help me isolate some programming errors and as it turns out - scheduled back-up needs some file(s) within MAILX to work properly.

Ok, well if you guys want to help make sure it's working as expected again can you please get the new update, completely remove all of mailx to include dependencies, run scheduled back-up and report back. :)

I added a little code to check if you have MAILX and if not to install it.

Would be wonderful if this does it once and for all.

SORRY to all who I kept telling "It's working for me. How could it not for you?" Who would have thunk MAILX was the culprit and what are the odds that a scheduled back-up script would need some files within this to work.... crazy.

New update is loaded to server.... fire at will.

---

### Post by evilc on 2008-03-13
> **mdpalow said:**
> [COLOR=Red][SIZE=3]NEW UPDATE AVAILABLE[/SIZE][/COLOR]


Ok, well if you guys want to help make sure it's working as expected again can you please get the new update, completely remove all of mailx to include dependencies, run scheduled back-up and report back. :)

I added a little code to check if you have MAILX and if not to install it.

Would be wonderful if this does it once and for all.

New update is loaded to server.... fire at will.

Tested and pleased to report Mailx got installed from Quickstart update and schedule backup worked. :guitar:

---

### Post by Bruce M. on 2008-03-13
> **mdpalow said:**
> [COLOR="Red"][SIZE="3"]NEW UPDATE AVAILABLE[/SIZE][/COLOR]
New update is loaded to server.... fire at will.

[CENTER]**[COLOR="Red"]I N C O M I N G ![/COLOR]**[/CENTER]

Oh! It's just Mailx
Scheduled Backup sitting nicely in place.

---

### Post by mdpalow on 2008-03-13
Had a request by BW44 to redo code a little to only install the absolute necessary files OUT OF mailx. Basically leave unnecessary files out. Kind of like that thinking as it's just cleaner all the way around. Granted, the extra mailx files aren't too much - but if it's an easy fix; why not.

It looks like we may only need "sudo aptitude install exim4"

Can anyone confirm the directory this file is in 'cause I need QuickStart to look for it first and then install if not found. I've found it, but just want to make sure I'm seeing the same way everyone else is.

Thanks...
[COLOR="Red"][B][SIZE="4"]
EDIT:[/SIZE][/B][/COLOR]

Ok, in the interest of time and keeping people from having to update twice, I've rewritten the install to ONLY install the exim4 files. If we can test one more time and ensure this is right, then I think we can close the door on this problem. Please, if you have time, update your QuickStart again, get rid of all mailx and exim4 files using SPM to remove, run QS, and then another scheduled back-up. By the way, if you use:

sudo nautilus and go to file system  /etc/crontab   you can edit the time to start at the next minute instead of having to wait 15 minutes. :)

Thanks EVERYONE!!!

As always..... New update is loaded to server.... fire at will.

---

### Post by evilc on 2008-03-13
> **mdpalow said:**
> 

Can anyone confirm the directory this file is in 'cause I need QuickStart to look for it first and then install if not found. I've found it, but just want to make sure I'm seeing the same way everyone else is.

Thanks...

Here is my complete 'locate' of eim4 if that helps.

---

### Post by Bruce M. on 2008-03-13
> **mdpalow said:**
> [COLOR="Red"][B][SIZE="4"]
EDIT:[/SIZE][/B][/COLOR]

Ok, in the interest of time and keeping people from having to update twice, I've rewritten the install to ONLY install the exim4 files. If we can test one more time and ensure this is right, then I think we can close the door on this problem. Please, if you have time, update your QuickStart again, get rid of all mailx and exim4 files using SPM to remove, run QS, and then another scheduled back-up. By the way, if you use:

sudo nautilus and go to file system  /etc/crontab   you can edit the time to start at the next minute instead of having to wait 15 minutes. :)

Thanks EVERYONE!!!

As always..... New update is loaded to server.... fire at will.

Mailx - complete removal
all 4 of the exim4 files - complete removal.
Getting new QuickStart now.
---------------------------------------
EDIT:
I'm getting an error when QuickStart tried to get the exim4 file.  :(
Can't grab it because terminal is not open long enough.

E: Could not get lock '/var/lib/dpkg/lock - open (11 resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/) 

BELAY that last .... dummy (me) had synaptic open in another window.  :(
--------------------------------------
EDIT:

Trying to get the new "update" and QS keeps loading Mailx before going to the main menu.
OK, so now I have Mailx amd the exim4 files again.
Just got the NEW Update
Deleteing Mailx et al again.
10 min later - Mailx et al completely removed.
Starting QS - sets up mailx again  :(

---

### Post by Bruce M. on 2008-03-13
> **mdpalow said:**
> sudo nautilus and go to file system  /etc/crontab   you can edit the time to start at the next minute instead of having to wait 15 minutes. :)

Times are local...

20:17 - set up a Scheduled Back-up for 20:30
20:18 - back-up started, while opening: gksudo thunar.
20:30 - While here - Screen opens notifying me of the Backup is starting ??? System and Config are already done.

See attached, I have no /etc/crontab and the "Scheduled Back-up" started immediately not at 20:30

Here's my: my_scheduled_backup
```

#!/bin/bash
#!/bin

# This file and folder it's located in were created by QuickStart and are used for your
# scheduled back-up(s). Please do not delete either or your scheduled back-up
# will not occur.

#Excludes
ex01="--exclude=system_backup_*.tgz"
ex02="--exclude=home_backup_*.tgz"
ex03="--exclude=config_backup_*.tgz"
ex04="--exclude=/home"
ex05="--exclude=/media/*"
ex06="--exclude=/mnt/*"
ex07="--exclude=/proc/*"
ex08="--exclude=/sys/*"
ex09="--exclude=lost+found/*"
ex10="--exclude=.Trash/*"
ex11="--exclude=/boot/grub/menu.lst"
ex12="--exclude=/boot/grub/device.map"
ex13="--exclude=/etc/fstab"
ex14="--exclude=/etc/mtab" 
ex15="--exclude=/etc/X11/xorg.conf"
ex16="--exclude=/home/bruloo/.thumbnails/fail/gnome-thumbnail-factory/*"
ex17="--exclude=/home/bruloo/.thumbnails/normal/*"
ex18="--exclude=windows_backup_*.img"

#Includes
inc1="/boot/grub/menu.lst"
inc2="/boot/grub/device.map"
inc3="/etc/fstab"
inc4="/etc/mtab"
inc5="/etc/X11/xorg.conf"

cd /home/bruloo/Desktop


tar cvpzf config_backup_`date +%Y.%m.%d`.tgz $inc1 $inc2 $inc3 $inc4 $inc5


tar cvpzf system_backup_`date +%Y.%m.%d`.tgz $ex01 $ex02 $ex03 $ex04 $ex05 $ex06 $ex07 $ex08 $ex09 $ex10 $ex11 $ex12 $ex13 $ex14 $ex15 /


tar cvpzf home_backup_`date +%Y.%m.%d`.tgz $ex01 $ex02 $ex03 $ex09 $ex10 $ex16 $ex17 $ex18 /home

```

What happens now?
Bruce

---

### Post by bw44 on 2008-03-13
Hi Bruce M.,

crontab is a file not a folder.  Take a look further down the /etc directory and you should see it.

Does that help?  Hope so.

---

### Post by gecko98 on 2008-03-13
I just installed QuickStart and used the Dvd Play Back included on it.
However after I installed it, any Dvd Player won't stay open for more than 5 seconds.:confused:
Is there anyway to fix it?:popcorn:

---

### Post by mdpalow on 2008-03-13
> **Bruce M. said:**
> Mailx - complete removal
all 4 of the exim4 files - complete removal.
Getting new QuickStart now.
---------------------------------------
EDIT:
I'm getting an error when QuickStart tried to get the exim4 file.  :(
Can't grab it because terminal is not open long enough.

E: Could not get lock '/var/lib/dpkg/lock - open (11 resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/) 

BELAY that last .... dummy (me) had synaptic open in another window.  :(
--------------------------------------
EDIT:

Trying to get the new "update" and QS keeps loading Mailx before going to the main menu.
OK, so now I have Mailx amd the exim4 files again.
Just got the NEW Update
Deleteing Mailx et al again.
10 min later - Mailx et al completely removed.
Starting QS - sets up mailx again  :(


The original ERROR you were getting is because you had Synaptic Package Manager (SPM) open at the same time you were trying to install exim4 with QS in the Terminal window. You have to close SPM first.

I'm going to upload a new/fresh copy of QS to server just in case the swapped out code didn't take before I uploaded it. It should have, but who knows.... 

Other than this, I don't know why it would want to load mailx again or anymore as the install command is 'sudo aptitude install exim4 -y'

Can we please weigh in some more and get resolution on this? Also, if this is not working, I can just put mailx back in, which isn't a really bad thing; just a few more files.

Thanks...

[B][COLOR="Red"]
New File is Loaded to Server[/COLOR][/B]

---

### Post by mdpalow on 2008-03-13
> **gecko98 said:**
> I just installed QuickStart and used the Dvd Play Back included on it.
However after I installed it, any Dvd Player won't stay open for more than 5 seconds.:confused:
Is there anyway to fix it?:popcorn:

Hi Gecko,

What version of Ubuntu are you running, what did you install, what program are you trying to watch a movie with, what video card do you have (nVidia/ATI)???

The more info you can provide the quicker someone can help you out. :)

Based on your question, this is beginning to sound like you have an ATI card. Am I right by any chance?

Thanks

---

### Post by mdpalow on 2008-03-13
> **bw44 said:**
> Hi Bruce M.,

crontab is a file not a folder.  Take a look further down the /etc directory and you should see it.

Does that help?  Hope so.

zactly :)

look for a FILE named Crontab in the ETC directory. That's the file you can edit.

Thanks

---

### Post by gecko98 on 2008-03-13
> **mdpalow said:**
> Hi Gecko,

What version of Ubuntu are you running, what did you install, what program are you trying to watch a movie with, what video card do you have (nVidia/ATI)???

The more info you can provide the quicker someone can help you out. :)

Based on your question, this is beginning to sound like you have an ATI card. Am I right by any chance?

Thanks

Hi mdpalow,

   I'm currently running 7.10 Gutsy and I just installed the QuickStart program and I used that to install the package that says "Dvd Playback". Afterwards, I inserted a Dvd Movie and opened up the default Dvd Player. The Player wouldn't stay open, so I decided to download Kaffeine ( which wouldn't stay open either :( ) And yes I do have an ATI card, version x1300.
I hope this helps and thanks for helping me with my problem!:)
--------------------
Gecko98

---

### Post by evilc on 2008-03-13
> **mdpalow said:**
> The original ERROR you were getting is because you had Synaptic Package Manager (SPM) open at the same time you were trying to install exim4 with QS in the Terminal window. You have to close SPM first.

I'm going to upload a new/fresh copy of QS to server just in case the swapped out code didn't take before I uploaded it. It should have, but who knows.... 

Other than this, I don't know why it would want to load mailx again or anymore as the install command is 'sudo aptitude install exim4 -y'

Can we please weigh in some more and get resolution on this? Also, if this is not working, I can just put mailx back in, which isn't a really bad thing; just a few more files.

Thanks...

[B][COLOR="Red"]
New File is Loaded to Server[/COLOR][/B]

Just d/l the updated version still putting all dep in including mailx? There is only 6 files involved I would leave them, no use banging head why it's doing this it works. (Old proverb not broke leave alone) :)

---

### Post by mdpalow on 2008-03-13
> **evilc said:**
> Just d/l the updated version still putting all dep in including mailx? There is only 6 files involved I would leave them, no use banging head why it's doing this it works. (Old proverb not broke leave alone) :)

Not sure why it's still installing mailx, but I really don't have much time to look into this right now.

Can I get some of you smart guys to look into this just a little more and tell me if putting 'mailx' is better than putting in 'exim4?'

I can leave it either way, but since changing it to exim4, is it working properly. Is putting 'mailx' going to load more files than just with 'exim4?'

Are we saying with 'exim4' it's loading all the same files as 'mailx?'

I'll check this again in about 20 minutes and hopefully someone will have a definitive answer for me and I can either leave it or change back to mailx and upload one last time.

Thanks Guys....

---

### Post by mdpalow on 2008-03-13
> **gecko98 said:**
> Hi mdpalow,

   I'm currently running 7.10 Gutsy and I just installed the QuickStart program and I used that to install the package that says "Dvd Playback". Afterwards, I inserted a Dvd Movie and opened up the default Dvd Player. The Player wouldn't stay open, so I decided to download Kaffeine ( which wouldn't stay open either :( ) And yes I do have an ATI card, version x1300.
I hope this helps and thanks for helping me with my problem!:)
--------------------
Gecko98

Not sure what says "DVD Playback."

What option in QuickStart did you use to install this program?

May not have time to help Gecko too much with this problem tonight. Can anyone else please try and be of some assistance to him/her?

Thanks...

---

### Post by bw44 on 2008-03-13
> **mdpalow said:**
> Not sure why it's still installing mailx, but I really don't have much time to look into this right now.

Can I get some of you smart guys to look into this just a little more and tell me if putting 'mailx' is better than putting in 'exim4?'

I can leave it either way, but since changing it to exim4, is it working properly. Is putting 'mailx' going to load more files than just with 'exim4?'

Are we saying with 'exim4' it's loading all the same files as 'mailx?'

I'll check this again in about 20 minutes and hopefully someone will have a definitive answer for me and I can either leave it or change back to mailx and upload one last time.

Thanks Guys....

I just downloaded and installed QuickStart, after completely removing mailx, liblockfile1, exim4, exim4-base, exim4-config, and exim4-daemon-light.

The version of QuickStart I downloaded definitely installed mailx and liblockfile1 in addition to the four exim4 packages (as of 10:15 EDT). Next, I completely removed mailx and liblockfile1 with Synaptic Package Manager and re-booted for good measure.

Then I scheduled a QuickStart Backup for 10:30 and it ran fine (except I wasn't watching the screen  just when I think it should have been displaying a messaging telling me not to touch the backup files until it had completed the backup -- does everyone else see this message when their backups start?)

Point of story: mailx is a red herring.  It is not needed for QuickStart Scheduled backup to run successfully.  But that being said, mailx doesn't appear to do any harm and only takes up a few 100KB of disk space.

Mdpalow: I noticed the new version of QuickStart is quite a bit smaller than the pevious one -- I hope nothing got left out. ;)  Thanks for all your efforts to sort us out.

---

### Post by evilc on 2008-03-14
The problem file seems to be exim4-base when that goes in it also put mailx and the  liblockfile1, would suggest leave it as it was with mailx pre-installing.

---

### Post by bw44 on 2008-03-14
> **evilc said:**
> The problem file seems to be exim4-base when that goes in it also put mailx and the  liblockfile1, would suggest leave it as it was with mailx pre-installing.

That's very strange.  On my system, if I completely remove the four exim4 packages and then mark exim4-base for installation, the SPM only adds the exim4-config package for installation, not mailx or liblockfile1.  If I mark exim4 (which is described as a meta-package) for installation, it marks exim4-base, exim4-config and exim4-daemon-light for installation (again, not mailx and not liblockfile1). :confused:

But, I  guess my real question is why QuickStart scheduled backup apparently depends on a Mail Transport Agent (exim4 or some part of it) to run.  mdpalow seems pretty busy right now, so it seems unkind to bug him about this.  With the exim4 stuff installed (with or without the other packages) the scheduled backup works, so we should be satisfied. I'll go along with you and say leave it as it is.  (Can't be chasing after every gremlin hiding in Debian/Ubuntu!)

---

### Post by mdpalow on 2008-03-14
Hi Guys....

Quickly scanned through the messages this late and think I understand that we should just leave it with 'exim4' being installed since it's working correctly now. Right?

I won't be on much later now, but I will check in tomorrow as always and see if there is any other input.

Thanks to everyone for taking the time to help straighten this all out.

good night

---

### Post by bw44 on 2008-03-14
> **mdpalow said:**
>  . . . I understand that we should just leave it with 'exim4' being installed since it's working correctly now. Right?

All right by me!

---

### Post by chrisdugdale on 2008-03-14
Wow! I spent all afternoon loading various dvd players and nothing would play at all! You did a great job, wish I'd found it this morning when I first loaded Ubuntu 7.10. Now its 8:30pm and I can finally watch that dvd. Thanks heaps, everyone should easily find quickstart! I've done about 6 installls of ubuntu and this is the first time i got all dvd's to play! Had some before. The other stuff in there is also real useful. May reinstall tomorrow and do the quickstart b4 i touch anything. What an inspiration. Thanks again. Chris



> **mdpalow said:**
> Hi Everyone,

I've written a script to expedite some things I do on my computer. If interested, you're welcome to download and use it. I call it QuickStart and with it you can:

(screen shots are attached below)


[COLOR="Red"]1. Install the proper DVD & Codecs Files so you can Play a DVD in your drive using totem, etc. (works with 7.10 / 7.04 and 32-bit / 64-bit). [/COLOR]

2. Back-up Your /home folders  

3. Back-up Your / folders

4. Back-up Your Configuration files separately (fstab, device.map, mtab, menu.lst, and xorg.conf)

5. Create a Custom Back-up for selected folders

6. Create a Custom Scheduled (Recurring) Back-up (daily, weekly, or monthly). You decide the exact date and time

7. Create a Scheduled 1:1 Synchronized Back-Up of Selected Folders to Another Drive/Partition.

8. Restore Your System /home folders

9. Restore Your / folders

10. Restore Your configuration files

11. Install some common applications (aMSN, aMSN fix, Firestarter,  AllTray, and a few others). Nice when you're starting from scratch (clean install)

12. House Cleaning (delete unnecessary files throughout your computer). 

13. View or Edit Your Key Files (fstab, menu.lst, and xorg.conf).

[COLOR="Red"]14. Back-up Your Master Boot Record (MBR)[/COLOR].

[COLOR="Red"]15. Back-up Your Windows Partition (dual booters) While in Ubuntu[/COLOR].

16. Format Windows Partition in NTFS with gParted.

[COLOR="Red"]17. Restore Your Master Boot Record (MBR)[/COLOR].

[COLOR="Red"]18. Restore Your Windows Back-Up While in Ubuntu[/COLOR].

19. Download Updates/Upgrades with a click of the mouse.



**How to download and install QuickStart** (Please follow these instructions exactly as they are written) :

1. Left-click the Install_QuickStart.sh file below and save it to your [COLOR="Red"]DESKTOP[/COLOR]

2. RIGHT click the Install_QuickStart.sh file on your DESKTOP and select Properties, then select the Permissions tab at the top, and ensure the 'Execute' check-box is checked towards the bottom where it says 'Allow executing file as program'. Close window.

3. If you installed the Ubuntu 32-bit OS you can skip this step. If you installed the Ubuntu 64-bit OS, open a terminal window and copy/paste the following, so your system can run 32-bit applications: [COLOR="Red"]sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0[/COLOR]

4. Click or double-click the Install_QuickStart.sh file now located on your Desktop and select [COLOR="Red"]Run in Terminal[/COLOR]

You will now have a QuickStart icon in your menu ( Applications -> Accessories -> QuickStart ) 



[COLOR="Blue"]1.) Please post a message after downloading the program to bump it to the top for others to see in case they want it too.[/COLOR]

[COLOR="Blue"]2.) Probably a good idea to subscribe to this thread if you plan on using this program as some postings might be of interest to you.[/COLOR]
.

---

### Post by chrisdugdale on 2008-03-14
More people should see QuickStart, it would save a lot of angst in noobie land. I'd like to have the flash and java plugins for my AMD64 in there too, I can't seem to get some sites working. But this wot you've done is a miracle and really helps a lot. Chris

---

### Post by bw44 on 2008-03-14
> **chrisdugdale said:**
> More people should see QuickStart, it would save a lot of angst in noobie land. I'd like to have the flash and java plugins for my AMD64 in there too, I can't seem to get some sites working. But this wot you've done is a miracle and really helps a lot. ChrisFor help with your 64bit flash and java problems, have a look at this thread: [http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

It's not a script like QuickStart, but a how-to for streaming, multimedia and video.

---

### Post by mdpalow on 2008-03-14
> **chrisdugdale said:**
> More people should see QuickStart, it would save a lot of angst in noobie land. I'd like to have the flash and java plugins for my AMD64 in there too, I can't seem to get some sites working. But this wot you've done is a miracle and really helps a lot. Chris

I don't think they have Java for 64-bit yet, but what's the problem with Flash 64-bit? You should be able to easily install that now? Is there something wrong with the install of the 64-bit Flash?

thanks

---

### Post by mdpalow on 2008-03-14
bw44,

I just remembered a question you asked me yesterday about QS being smaller in size this time. Not sure if you meant from just the past couple of days or from a while ago.

Yeah, remember I took out the Flash fix/Java functions since they are pretty simple to do now with Synaptic. That took it down some. I also removed aMSN code a while back because I use eMeSeNe now, which I like better. That was a lot of code too, so that made QS smaller in size as well. I didn't touch any code inside a function that still exists within QS.

Hope that answers your question. :)

---

### Post by mdpalow on 2008-03-14
> **chrisdugdale said:**
> Wow! I spent all afternoon loading various dvd players and nothing would play at all! You did a great job, wish I'd found it this morning when I first loaded Ubuntu 7.10. Now its 8:30pm and I can finally watch that dvd. Thanks heaps, everyone should easily find quickstart! I've done about 6 installls of ubuntu and this is the first time i got all dvd's to play! Had some before. The other stuff in there is also real useful. May reinstall tomorrow and do the quickstart b4 i touch anything. What an inspiration. Thanks again. Chris

Thanks Chris..

That's a really good idea. Reinstall Ubuntu, use QS to get a QuickStart :) on a few things and then finish up with configuring your system just like you want it. Once you've got everything installed and configured - make a back-up and put it somewhere safe. Doing that will save you hours next time.

THEN... experiment all you want... Once you've learned what exactly you want to do with Ubuntu - format and use your back-ups. Then add the new things you learned about while experimenting and finally finish up with creating another back-up with the new stuff.

enjoy...

---

### Post by mdpalow on 2008-03-14
> **gecko98 said:**
> Hi mdpalow,

   I'm currently running 7.10 Gutsy and I just installed the QuickStart program and I used that to install the package that says "Dvd Playback". Afterwards, I inserted a Dvd Movie and opened up the default Dvd Player. The Player wouldn't stay open, so I decided to download Kaffeine ( which wouldn't stay open either :( ) And yes I do have an ATI card, version x1300.
I hope this helps and thanks for helping me with my problem!:)
--------------------
Gecko98

Sorry Gecko... just saw this answer by you...

did you by any chance install additional ATI drivers after installing? In other words, did you choose to install new ATI drivers rather than keep the Restricted Drivers Ubuntu wanted to install?

I only know of this problem because my friend has an ATI card and had the exact same problem. I just contacted him now (speaking to him as I write this) to try and get the fix from him.

He's telling me that you should install Envy and then allow/tell it to install your ATI video drivers. Envy is good in that it makes installing video drivers even easier than ever.

He's (my friend) asking for the link to the page with your question on it. Not sure, but he might reply to you personally or here to help you if he can.

I'll finish for now..

---

### Post by bw44 on 2008-03-14
> **mdpalow said:**
> I just remembered a question you asked me yesterday about QS being smaller in size this time. Not sure if you meant from just the past couple of days or from a while ago.
. . .
Hope that answers your question. :)I was only kidding! :rolleyes:  I noticed when I was backing up QuickStart that the older version it replaced was bigger.  I think it was a fairly recent one, but probably it was before you cleaned up and removed all that stuff.  Thanks for taking the trouble to answer though.

---

### Post by Het Irv on 2008-03-14
Hey, do you think that there is a way to redo the Mailx update so that it tells you that it is trying to install mailx.  Suspicious users might be wary of a random terminal popping up asking for their password. (bwt, I havn't gotten to the computer that has Hardy alpha on it yet, but it's still on the list).

---

### Post by mdpalow on 2008-03-14
> **Het Irv said:**
> Hey, do you think that there is a way to redo the Mailx update so that it tells you that it is trying to install mailx.  Suspicious users might be wary of a random terminal popping up asking for their password. (bwt, I havn't gotten to the computer that has Hardy alpha on it yet, but it's still on the list).

I'm sure I don't even know what you're talking about. :) LOL  What?

Right now, a window would pop-up telling you QuickStart needs 'exim4' to run and to enter your password. Then a terminal window will come up and show you the install process as it's going on. Then the window goes away and up comes QuickStart.

What did/do you mean by 'update?'

I'm reading your original post again..... Do you mean to make the pop-up asking for the password to install exim4 better? If so, I can do that easily enough, but what would you have me say in the pop-up that would be better?

I'll keep an eye out for your reply in hopes of getting a better understanding of what you're asking for.

Thanks Het Irv...

EDIT:

I just noticed that link in your signature. Wow! Thanks... :)

---

### Post by Het Irv on 2008-03-14
By update I meant the update of Quickstart that installed mailx if it was not on the system.    Going back and reading my post I see that it doesn't make sense, (it did at the time).  
I must have missed the popup window, cause that would be what I was asking for.  Sorry for wasteing everyones time.:lolflag:

---

### Post by mdpalow on 2008-03-14
> **Het Irv said:**
> By update I meant the update of Quickstart that installed mailx if it was not on the system.    Going back and reading my post I see that it doesn't make sense, (it did at the time).  
I must have missed the popup window, cause that would be what I was asking for.  Sorry for wasteing everyones time.:lolflag:

No problemo and u didn't waste my time. :)

Ok, just to be clear.. the pop-up window is TIED into the password. Meaning, the window that you put your password in has some text at the top that says "QuickStart needs to install 'exim4' to run." Then directly below, you would enter your password.

Then the terminal window comes up and shows you the install in progress. Then it goes away and up comes QuickStart.

So, although you could not have missed the pop-up window (asking for password) - you could easily have missed the small text at the top telling you why it wanted your password.

Hope this clears up any confusion someone else might have reading this...

Thanks again Het....

---

### Post by Bruce M. on 2008-03-14
> **bw44 said:**
> Hi Bruce M.,

crontab is a file not a folder.  Take a look further down the /etc directory and you should see it.

Does that help?  Hope so.

I knew that, I knew that.... ***No I didn't!***

Got a heck of a cold here and was not thinking straight.

OK, I see it and:

```

30 20   * * *   root    /home/bruloo/Cron/my_scheduled_backup    # # # QuickStart Entry # # #
30 20   * * *   bruloo    /home/bruloo/Cron/QuickStart_popup       # # # Zenity Entry     # # #

```
It says 20:30 ... so why did the backup start just after creating at 20:19?

Mind you the "QuickStart_popup" waited until 20:30  :)

Bruce

---

### Post by mdpalow on 2008-03-14
> **Bruce M. said:**
> I knew that, I knew that.... ***No I didn't!***

Got a heck of a cold here and was not thinking straight.

OK, I see it and:

```

30 20   * * *   root    /home/bruloo/Cron/my_scheduled_backup    # # # QuickStart Entry # # #
30 20   * * *   bruloo    /home/bruloo/Cron/QuickStart_popup       # # # Zenity Entry     # # #

```
It says 20:30 ... so why did the backup start just after creating at 20:19?

Mind you the "QuickStart_popup" waited until 20:30  :)

Bruce

No idea why that would happen. You're right, it's set for 20:30. Sounds like maybe a bug/glitch. You should try it again and see if it does it to you again.

thanks...

---

### Post by bw44 on 2008-03-14
> **Bruce M. said:**
> I knew that, I knew that.... ***No I didn't!***

Got a heck of a cold here and was not thinking straight.

OK, I see it and:

```

30 20   * * *   root    /home/bruloo/Cron/my_scheduled_backup    # # # QuickStart Entry # # #
30 20   * * *   bruloo    /home/bruloo/Cron/QuickStart_popup       # # # Zenity Entry     # # #

```
It says 20:30 ... so why did the backup start just after creating at 20:19?

Mind you the "QuickStart_popup" waited until 20:30  :)

Bruce Glad it's working.  but I have no idea (either) why it started right away.

But you do get the popup message telling you not to touch the files then? I guess I'll have to test it again, since I haven't seen it.

Hope your cold's better.

Cheers.

---

### Post by bw44 on 2008-03-14
> **bw44 said:**
> . . . But you do get the popup message telling you not to touch the files then? I guess I'll have to test it again, since I haven't seen the message.Nope, the popup message isn't displayed.  I hear the purple alert.wav and the backup starts, but no message.  When I just run the popup script it works fine.  All the other QuickStart message display OK  (unless there are others I'm not seeing! :)) This is weird.  Does anybody have any ideas?

---

### Post by mdpalow on 2008-03-15
Is anyone else NOT getting a pop-up window displayed JUST as the SCHEDULED back-up is about to begin?

Remember, this is for a scheduled back-up; not a regular one.

Thanks...

By the way bw44, I just remembered that when I installed ubuntu on my laptop the other day the pop-up window did come up. It didn't backup because I didn't load the exim4 or mailx, but the popup came up.

---

### Post by bw44 on 2008-03-15
> **mdpalow said:**
> Is anyone else NOT getting a pop-up window displayed JUST as the SCHEDULED back-up is about to begin?

Remember, this is for a scheduled back-up; not a regular one.

Thanks...

By the way bw44, I just remembered that when I installed ubuntu on my laptop the other day the pop-up window did come up. It didn't backup because I didn't load the exim4 or mailx, but the popup came up.While setting up to test my problem with the scheduled system backup, I noticed something else which may actually be a "bug" in QuickStart:

I had a "Synchronize Selected Folders" (option4) scheduled as well as a scheduled system backup (option 3).  When I deleted the scheduled system backup, the entry in /etc/crontab for the option 4 schedule was also deleted.  Help!  -- hope this isn't too hard to fix!

Will report back if I figure anything out about the system-backup-starting message not displaying. It's probably something wrong with my particular setup.

Thanks.

---

### Post by Bruce M. on 2008-03-15
From the beginning when I noticed this:

> **Bruce M. said:**
> Times are local...

20:17 - set up a Scheduled Back-up for 20:30
20:18 - back-up started, while opening: gksudo thunar.
20:30 - While here - Screen opens notifying me of the Backup is starting ??? System and Config are already done.

At 20:17 I start creating the "Scheduled Backup" to start at 20:30
At 20:18 the backup started with NO "QuickSart_popup" notification - 22 minutes early. I had started Thunar (sudo) in order to change the location to /media/sdb1/Backup/Schedule, but closed it out because the backup had started early.
At 20:30, after System and Config backups were done, the "QuickStart_popup" popped up to tell me the scheduled backup was starting. Shortly after that it started to backup /home.


> **bw44 said:**
> Glad it's working.  but I have no idea (either) why it started right away.

But you do get the popup message telling you not to touch the files then? I guess I'll have to test it again, since I haven't seen it.

Hope your cold's better.

Cheers.

Like stated above.  The pop-up message appeared 22 minutes after the backup started, at the correct time of 20:30, not right away.

I wonder if changing these lines, when creating a "Scheduled Backup" with QS, would make a difference?
```

30 20   * * *   bruloo    /home/bruloo/Cron/QuickStart_popup       # # # Zenity Entry     # # #
30 20   * * *   root    /home/bruloo/Cron/my_scheduled_backup    # # # QuickStart Entry # # #

```
Just a thought.

Today I'll do another test, creating a new scheduled back-up for 1 hour later than the time I create it.

IF I have the same experience as started above, the backup will be finished by the time the "pop-up" appears.

Will keep you posted.
Bruce

---

### Post by Bruce M. on 2008-03-15
All times are local:
[LIST]
[*]10:57 - created SB for 12:00 noon
[*]10:58 - CPU usage normal - no activity only gEdit running.
[*]11:04 - Thought: maybe this "instant start" only happens if it's created to start within a half hour?
[*]11:06 - no activity - going to change the default folder to: cd /media/sdb1/Back-ups/Schedule - 11:13 - done (and got a coffee)
[*]11:14 - going to change the times to start 2 minutes after hitting the Save button.
[*]11:16 - Have to find where that file is to change the time.
[*]11:25 - 11:27 it should start.
[*]11:27 - nothing
[*]11:28 - nothing
[*]11:29 - nothing
[*]11:29 - changing it back to 00 12 (12:00)
[*]11:31 - done - waiting until 12:00
[/LIST]
**NOTE:** I did **NOT** reverse the order of the two lines.

**EDIT:** 11:58 - getting close!
**EDIT:** 12:00 - Started! - Popup came up, CPU usage very high.  :)
**Huston, we have lift off!**
**EDIT:** 12:12 - added attachment - as you can see "system" is about 1/3 done - CPU at 100% - temp climbed approx 30°C, RAM usage at 31%, Disk Swap at 3%.  This is why I do it at night.  :)

Are **WishLists** allowed?  If so:

[LIST=1]
[*]Ability to select the folder for the Scheduled Back-up. [Default: Desktop]
[*]Ability to select the # of Scheduled Back-ups to keep. [Default: 0 = All, 1 = Today's backup only. Suggestion: up to 5]
[/LIST]

Yes, I know the reason for selecting Desktop ... so you can see it in action. Leave that as a "Default", but there must be some people out there, like me, that schedule these backups to happen when they are not using the computer.

---

### Post by Dynamo_Joe on 2008-03-15
Hi mdpalow, 

Downloaded, installed, will get round to playing with it later. 

Many Thanks!

---

### Post by mdpalow on 2008-03-15
> **Bruce M. said:**
> 
**EDIT:** 12:12 - added attachment - as you can see "system" is about 1/3 done - CPU at 100% - temp climbed approx 30°C, RAM usage at 31%, Disk Swap at 3%.  This is why I do it at night.  :)


Curious... Why is your last SYSTEM back-up only 300+ MB and not close to a Gig? Seems very small...

---

### Post by mdpalow on 2008-03-15
> **bw44 said:**
> While setting up to test my problem with the scheduled system backup, I noticed something else which may actually be a "bug" in QuickStart:

I had a "Synchronize Selected Folders" (option4) scheduled as well as a scheduled system backup (option 3).  When I deleted the scheduled system backup, the entry in /etc/crontab for the option 4 schedule was also deleted.  Help!  -- hope this isn't too hard to fix!

Will report back if I figure anything out about the system-backup-starting message not displaying. It's probably something wrong with my particular setup.

Thanks.

Thanks bw44... that was some tricky code I was doing there. Let me check it now. I was pretty sure I got that right. Maybe not....

---

### Post by mdpalow on 2008-03-15
> **bw44 said:**
> While setting up to test my problem with the scheduled system backup, I noticed something else which may actually be a "bug" in QuickStart:

I had a "Synchronize Selected Folders" (option4) scheduled as well as a scheduled system backup (option 3).  When I deleted the scheduled system backup, the entry in /etc/crontab for the option 4 schedule was also deleted.  Help!  -- hope this isn't too hard to fix!

Thanks.

EDIT... read your post wrong... let me do another test and look again...

---

### Post by Bruce M. on 2008-03-15
> **mdpalow said:**
> Curious... Why is your last SYSTEM back-up only 300+ MB and not close to a Gig? Seems very small...

It was only 1/3 done still had the other 2/3 to do.  :)
I was watching the numbers climb when I got the idea to send the attachment.
If you notice /home isn't there yet.  :)

Today's results:
[LIST=1]
[*]Config = 3.4 kB - equals all the rest
[*]System = 998.0 MB - yesterday's = 997.3 MB ( I added some stuff )
[*]Home = 218.8 MB - Yesterday's = 217.1 MB
[/LIST]

**EDIT:**  Oh, and my WishList - low priority. Not until the bugs/glitches ( or as some would say: features ) are set  :)

---

### Post by mdpalow on 2008-03-15
> **Bruce M. said:**
> It was only 1/3 done still had the other 2/3 to do.  :)
I was watching the numbers climb when I got the idea to send the attachment.
If you notice /home isn't there yet.  :)

Today's results:
[LIST=1]
[*]Config = 3.4 kB - equals all the rest
[*]System = 998.0 MB - yesterday's = 997.3 MB ( I added some stuff )
[*]Home = 218.8 MB - Yesterday's = 217.1 MB
[/LIST]

Thanks for that Bruce...

---

### Post by mdpalow on 2008-03-15
[COLOR="Red"][SIZE="3"]**Update Available at this time**[/SIZE][/COLOR]

Ok, bw44 found a problem where deleting the scheduled back-up (SB) deleted the synchronized back-up entry in Crontab as well.

Simple fix really. When I wrote SB, I told it to look for a key-word when deleting the Crontab entries.

Problem was... when I created the Synchronized Back-up (Later), I used the same key-word in the Crontab file. All that was needed was for me to add another word that would actually separate the two and make them individually identifiable, so QS would not delete them both.

thanks bw44.. since you found the jewel, can you please update and test again to verify it's been fixed to your satisfaction?

Thanks...

[COLOR="Blue"]**File is loaded to server...... fire at will**[/COLOR]

---

### Post by Bruce M. on 2008-03-15
> **mdpalow said:**
> [COLOR="Red"][SIZE="3"]**Update Available at this time**[/SIZE][/COLOR]

thanks bw44.. since you found the jewel, can you please update and test again to verify it's been fixed to your satisfaction?

Thanks...

[COLOR="Blue"]**File is loaded to server...... fire at will**[/COLOR]

Got it!
Looked at my Sync Folders just now, not done in a while either and file not there, I'll:

[LIST=1]
[*]Set up a new Scheduled Backup - as per normal for 22:30
[*]Set up a new Sync Folders
[*]Delete Scheduled Backup
[*]Check the Sync Folders
[/LIST]

Be right back

**EDIT:** Worked for me.  :)

---

### Post by mdpalow on 2008-03-15
> **Bruce M. said:**
> 

Are **WishLists** allowed?  If so:

[LIST=1]
[*]Ability to select the folder for the Scheduled Back-up. [Default: Desktop]
[*]Ability to select the # of Scheduled Back-ups to keep. [Default: 0 = All, 1 = Today's backup only. Suggestion: up to 5]
[/LIST]

Yes, I know the reason for selecting Desktop ... so you can see it in action. Leave that as a "Default", but there must be some people out there, like me, that schedule these backups to happen when they are not using the computer.

Bruce, Bruce, Bruce... what am I going to do with you. LOL :)

I'm joking with you above because I looked at this the last time you mentioned it and as it turns out... this would NOT be an easy change.

I must admit, I'm not sure this is a good idea for the majority as I KNOW someone is going to come back to their computer (after missing the pop-up window), see their computer hard drive light going crazy, not know what's going on, think they've been hacked, and shut their system down right in the middle of a back-up. :)

Let me look at it again right now and see if I can think of an alternative that will satisfy both you and me. :)

be back shortly...

---

### Post by Bruce M. on 2008-03-15
> **mdpalow said:**
> Bruce, Bruce, Bruce... what am I going to do with you. LOL :)

**Oh NO! NOT the belt!  I'll be good, promise!**

> **mdpalow said:**
> I'm joking with you above because I looked at this the last time you mentioned it and as it turns out... this would NOT be an easy change.

So leave it.  You told me what to edit to get it to the folder I wanted to use.  :)
I can pop in every now and then and clean out the old ones I don't want.
That's why I said: low priority.  :)

> **mdpalow said:**
> I must admit, I'm not sure this is a good idea for the majority as I KNOW someone is going to come back to their computer (after missing the pop-up window), see their computer hard drive light going crazy, not know what's going on, think they've been hacked, and shut their system down right in the middle of a back-up. :)

Yea, that would hurt wouldn't it.
**Maybe:** it could be done with a popup that stays in place until the SB has completed, with the option to close it if someone is using the computer.

[ducking the belt]  :lolflag:

> **mdpalow said:**
> Let me look at it again right now and see if I can think of an alternative that will satisfy both you and me. :)

be back shortly...

As I said before I understand your reasons. And you did give me half of the solution. And since it's permanent now it's not a biggie.

Bruce

---

### Post by scottym on 2008-03-15
Very nice work. Thanks!!!

---

### Post by Bruce M. on 2008-03-15
Just a general note.

One has to admire mdpalow.

He comes up with one of the greatest apps I've seen for us newbies to Linux/Ubuntu.  He bends over backwards to correct bugs/gliches ( features? ) and all the while has "*safety in mind*" for the people using QuickStart.

Five :KS :KS :KS :KS :KS :KS 's to you mdpalow.

( yes, I can count! )
Bruce

---

### Post by mdpalow on 2008-03-15
> **Bruce M. said:**
> **Oh NO! NOT the belt!  I'll be good, promise!**

You're funny with the "Belt."

Hmmm, you might have just hit on something. It was in my sub-conscious and it didn't occur to me until just now.

Zenity pop-ups MUST be closed in order for the next process to begin. However, the other day when I was testing SB because people were having problems - I think I remember seeing the hard drive light working even though the pop-up window was still up. Since this pop-up is not truly tied into the program, but instead a SEPARATE command... the back-up might begin even with the window up. If that's the case, then yes... I could leave the window up and allow the user to close it.

Can you run a test for me?

schedule a back-up in 2 minutes. Then edit your scheduled back-up file in CRON folder and put a # in front of the SYSTEM tar command OR remove it completely. This way you don't have to wait for the entire back-up to be completed. It will only do the /home and config back-ups.

then when it starts... see if it's backing up already while the pop-up window is still up.

I will be looking at the code to see how I can do this without having to re-write the whole thing.

Thanks..

---

### Post by Bruce M. on 2008-03-15
> **mdpalow said:**
> You're funny with the "Belt."

Ahh, but comes from real life experience.

> **mdpalow said:**
> Can you run a test for me?

schedule a back-up in 2 minutes. Then edit your scheduled back-up file in CRON folder and put a # in front of the SYSTEM tar command OR remove it completely. This way you don't have to wait for the entire back-up to be completed. It will only do the /home and config back-ups.

then when it starts... see if it's backing up already while the pop-up window is still up.

I will be looking at the code to see how I can do this without having to re-write the whole thing.

Thanks..

Going to do test now.  :)

**EDIT:**
At 15:00 I set one up for 15:15 and it starts immediately :(
Again no "popup", but before I can configure out #system, Config is finished and System started.  :(

**EDIT:** set one up for 22:15 - did the #System, changed time to 15:15 - 4 minutes to go.

**EDIT:** At 15:15 - Config and Home appear on my desktop along with the popup that stayed for about 10 seconds then disappeared. So yes, the backup started and finished Config and started /home while the popup was on the screen.

---

### Post by bw44 on 2008-03-15
> **mdpalow said:**
> [COLOR="Red"][SIZE="3"]**Update Available at this time**[/SIZE][/COLOR]

Ok, bw44 found a problem where deleting the scheduled back-up (SB) deleted the synchronized back-up entry in Crontab as well.

Simple fix really. When I wrote SB, I told it to look for a key-word when deleting the Crontab entries.

Problem was... when I created the Synchronized Back-up (Later), I used the same key-word in the Crontab file. All that was needed was for me to add another word that would actually separate the two and make them individually identifiable, so QS would not delete them both.

thanks bw44.. since you found the jewel, can you please update and test again to verify it's been fixed to your satisfaction?

Um, sorry, not quite. :( Here's what I did:

1. deleted all QuickStart schedules and checked /etc/crontab -- no evidence of QuickStart.

2. downloaded/installed latest QuickStart update.

3. set up a scheduled synchronization and ran it initially. 

4. set up a scheduled system backup.

5. deleted system backup

6. checked /etc/crontab -- no evidence of **any**  QuickStart schedules.

7. repeated test but checked /etc/crontab after creating sync schedule and before
  creating system backup schedule.  sync schedule was there. 

8. created system backup schedule and checked /etc/crontab: new system backup
 schedule was there, but the sync schedule entry was gone.

It looks like deleting **or adding** the system backup schedule deletes the sync shedule.
(I didn't test creating the system backup schedule first, then adding/deleting the sync schedule.)**

Sorry to be the bearer of bad news.

Been testing **my** zenity message missing problem, but no progress so far.

bw44

**PS just tested adding/deleting sync schedule after creating system backup schedule -- no problems there.  System backup schedule was unaffected,
so it's just a problem adding/deleting the system backup.

---

### Post by Bruce M. on 2008-03-15
> **bw44 said:**
> Um, sorry, not quite. :( Here's what I did:

6. checked /etc/crontab -- no evidence of **any**  QuickStart schedules.

Is the *Sync Folders Schedule* supposed to show in /etc/crontab as well?

If so mine are gone too since I just deleted a Scheduled Backup and created a new one for a test.

```

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#


15 15   * * *   root    /home/bruloo/Cron/my_scheduled_backup    # # # QuickStart Entry # # #
15 15   * * *   bruloo    /home/bruloo/Cron/QuickStart_popup       # # # Zenity Entry     # # #

```

Bruce.

**@ mdplow** ... forget what we were doing, this is a higher priority.

---

### Post by bw44 on 2008-03-15
> **Bruce M. said:**
> Is the *Sync Folders Schedule* supposed to show in /etc/crontab as well?

If so mine are gone too since I just deleted a Scheduled Backup and created a new one for a test.

```

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#


15 15   * * *   root    /home/bruloo/Cron/my_scheduled_backup    # # # QuickStart Entry # # #
15 15   * * *   bruloo    /home/bruloo/Cron/QuickStart_popup       # # # Zenity Entry     # # #

```

Bruce.

**@ mdplow** ... forget what we were doing, this is a higher priority.

Thanks, Bruce -- I was beginning to think I was crazy (or had another problem that no one else was having!)

bw44

---

### Post by Bruce M. on 2008-03-15
> **bw44 said:**
> Thanks, Bruce -- I was beginning to think I was crazy (or had another problem that no one else was having!)

bw44

I know what it is, two Canucks from Montreal.  That's got to be it. :guitar:

---

### Post by mdpalow on 2008-03-15
> **Bruce M. said:**
> 

**@ mdplow** ... forget what we were doing, this is a higher priority.

way ahead of you guys... please run the test mentioned earlier...

---

### Post by Bruce M. on 2008-03-15
> **mdpalow said:**
> way ahead of you guys... please run the test mentioned earlier...

Testing ... Be right back

---

### Post by mdpalow on 2008-03-15
[COLOR="Red"]**[SIZE="3"]New Update Available[/SIZE]**[/COLOR]


Ok, I think all fixes are made and Bruce's request to allow you to decide where back-ups go is in effect now. I was able to test it myself to see and then made fixes earlier.

If you guys want to download now and retest.

BW44... fixed problem with deleting sync schedule when creating/deleting SB. Same issue as before was problem with CREATING as well. Just had to separate again.

Thanks...


update is loaded to server.

---

### Post by Bruce M. on 2008-03-15
1. deleted all QuickStart schedules and checked /etc/crontab -- no evidence of QuickStart.
	done
2. downloaded/installed latest QuickStart update.
	done
3. set up a scheduled synchronization and ran it initially.
	done
	Checking: ~/Cron/folder_sync.sh

```
#!/bin/bash
cp -R --update --preserve /home/bruloo/.conkyscripts /media/sdb1/Back-ups/Sync
cp -R --update --preserve /home/bruloo/.fluxbox /media/sdb1/Back-ups/Sync
cp -R --update --preserve /home/bruloo/.gAcc /media/sdb1/Back-ups/Sync
cp -R --update --preserve /home/bruloo/.gnucash /media/sdb1/Back-ups/Sync
cp -R --update --preserve /home/bruloo/.jpilot /media/sdb1/Back-ups/Sync
cp -R --update --preserve /home/bruloo/.mozilla /media/sdb1/Back-ups/Sync
cp -R --update --preserve /home/bruloo/.mozilla-thunderbird /media/sdb1/Back-ups/Sync
cp -R --update --preserve /home/bruloo/BofM /media/sdb1/Back-ups/Sync
cp -R --update --preserve /home/bruloo/QuickStart /media/sdb1/Back-ups/Sync
cp -R --update --preserve /home/bruloo/scripts /media/sdb1/Back-ups/Sync
cp -R --update --preserve /home/bruloo/Wallpapers /media/sdb1/Back-ups/Sync

zenity --info --title="QuickStart" --text="Your selected folders have been synchronized."
```
-------------
	Checking /etc/crontab:

```
00 22   * * *   root    /home/bruloo/Cron/folder_sync.sh         # # # QuickStart Folder Sync Entry # # #
```
-------------

4. set up a scheduled system backup.
	Checking: ~/Cron/folder_sync.sh
same as above...
	Checking /etc/crontab:
```
00 22   * * *   root    /home/bruloo/Cron/folder_sync.sh         # # # QuickStart Folder Sync Entry # # #
30 22   * * *   root    /home/bruloo/Cron/my_scheduled_backup    # # # QuickStart Entry # # #
30 22   * * *   bruloo    /home/bruloo/Cron/QuickStart_popup       # # # Zenity Entry     # # #
```
	Checking /Cron/my_scheduled_backup
```
#!/bin/bash
#!/bin

# This file and folder it's located in were created by QuickStart and are used for your
# scheduled back-up(s). Please do not delete either or your scheduled back-up
# will not occur.

#Excludes
ex01="--exclude=system_backup_*.tgz"
ex02="--exclude=home_backup_*.tgz"
ex03="--exclude=config_backup_*.tgz"
ex04="--exclude=/home"
ex05="--exclude=/media/*"
ex06="--exclude=/mnt/*"
ex07="--exclude=/proc/*"	Checking: ~/Cron/folder_sync.sh
ex08="--exclude=/sys/*"
ex09="--exclude=lost+found/*"
ex10="--exclude=.Trash/*"
ex11="--exclude=/boot/grub/menu.lst"
ex12="--exclude=/boot/grub/device.map"
ex13="--exclude=/etc/fstab"
ex14="--exclude=/etc/mtab" 
ex15="--exclude=/etc/X11/xorg.conf"
ex16="--exclude=/home/bruloo/.thumbnails/fail/gnome-thumbnail-factory/*"
ex17="--exclude=/home/bruloo/.thumbnails/normal/*"
ex18="--exclude=windows_backup_*.img"

#Includes
inc1="/boot/grub/menu.lst"
inc2="/boot/grub/device.map"
inc3="/etc/fstab"
inc4="/etc/mtab"
inc5="/etc/X11/xorg.conf"

cd /media/sdb1/Back-ups/Schedule


tar cvpzf config_backup_`date +%Y.%m.%d`.tgz $inc1 $inc2 $inc3 $inc4 $inc5


tar cvpzf system_backup_`date +%Y.%m.%d`.tgz $ex01 $ex02 $ex03 $ex04 $ex05 $ex06 $ex07 $ex08 $ex09 $ex10 $ex11 $ex12 $ex13 $ex14 $ex15 /


tar cvpzf home_backup_`date +%Y.%m.%d`.tgz $ex01 $ex02 $ex03 $ex09 $ex10 $ex16 $ex17 $ex18 /home
```
5. deleted scheduled backup
	Done

6. checked /etc/crontab -- ( **EDIT: OOPS**:no evidence of any QuickStart schedules. ) <- delete between ( )
	Checking: ~/Cron/folder_sync.sh
	Still exists and same as above.
	Checking /etc/crontab
```
00 22   * * *   root    /home/bruloo/Cron/folder_sync.sh         # # # QuickStart Folder Sync Entry # # #
```
	Just as it should be.

YES!  And you did the select folder too!

---

### Post by mdpalow on 2008-03-15
still waiting on you bw44...... I just know you're looking. ;) :-\":roll:\\:D/](*,)

---

### Post by bw44 on 2008-03-15
> **mdpalow said:**
> [COLOR="Red"]**[SIZE="3"]New Update Available[/SIZE]**[/COLOR]


Ok, I think all fixes are made and Bruce's request to allow you to decide where back-ups go is in effect now. I was able to test it myself to see and then made fixes earlier.

If you guys want to download now and retest.

BW44... fixed problem with deleting sync schedule when creating/deleting SB. Same issue as before was problem with CREATING as well. Just had to separate again.

Thanks...

Our thanks to you!  Everything is working fine!

bw44

PS except, of course, my gdm doesn't want to display that zenity message . .. Guess one can't have everything.

---

### Post by bw44 on 2008-03-15
> **mdpalow said:**
> still waiting on you bw44...... I just know you're looking. ;) :-\":roll:\\:D/](*,)

Sorry, I'm just slow (but thorough!) :-k

---

### Post by mdpalow on 2008-03-15
> **bw44 said:**
> Sorry, I'm just slow (but thorough!) :-k

thorough you are my friend.... that's why I was waiting to hear from you. :)

[SIZE="2"]**Thanks to both you and Bruce for catching these problems/bugs. QuickStart is definitely getting better because of help from people like you.**[/SIZE]

Now that we know the pop-up for a SB doesn't effect the actual back-up, I'm very glad to see we can select another location for placement. Thanks for making me look at that again Bruce..

I really hope we don't end up having to make any changes when 8.04 comes out.

BW44... why not do a restore (if you haven't already) from your back-up and then see if the pop-up works. At least then you'll know for sure...

Let us know if you ever get the pop-up to work....

Thanks.

---

### Post by bw44 on 2008-03-15
> **mdpalow said:**
> . . . I really hope we don't end up having to make any changes when 8.04 comes out.

BW44... why not do a restore (if you haven't already) from your back-up and then see if the pop-up works. At least then you'll know for sure...

Let us know if you ever get the pop-up to work....

Thanks.I lent my 7.10 live CD to a friend, so maybe I'll try your suggestion if by the time I get the CD back I haven't figured it out.  I think it's some setting in gnome or x, or a permissions issue that's peculiar to my set-up.  I'm pretty sure a restore will put me back to where I am. (After all that's what it's s'pposed to do, isn't it?? ;) )

---

### Post by Bruce M. on 2008-03-15
> **bw44 said:**
> I lent my 7.10 live CD to a friend, so maybe I'll try your suggestion if by the time I get the CD back I haven't figured it out.  I think it's some setting in gnome or x, or a permissions issue that's peculiar to my set-up.  I'm pretty sure a restore will put me back to where I am. (After all that's what it's s'pposed to do, isn't it?? ;) )

**Lend my Ubuntu CD's! Never!**

I still have ISO files for: Ubuntu and Xubuntu 7.10 (both Live and Alt CD's). If someone wants to try it I burn them a copy. One just never knows when one might need that CD!

Didn't delete the Feisty ISO's until I knew I was staying with 7.10.  \\:D/

---

### Post by evilc on 2008-03-16
I have just cleaned up all the schedule backups and removed the schedule settings now it's all working properly now. I noticed that even though Quickstart said the schedule backup was removed there was still the crontab quickstart in /etc, could this be included in the removal as well.

tia

---

### Post by lolo67 on 2008-03-17
:lolflag: thanks nice program

---

### Post by irw on 2008-03-17
I also did not have a pop-up message from zenity.

I originally tried to get this working by either calling zenity direct from crontab or via a script, and neither worked.

In the end the only way that worked was by running ```
xhost +local:localhost
```  To get this running at start-up, I added it to the sessions list.
I tried to get it running at boot via rc.local (?correct name - i can't remember at this moment), but could not get that to work. For now I am adding a session to all users who need it.

I spent hours trying out different variations of  --display :0 without any effect.

Maybe this could help bw44?

Ian

---

### Post by bw44 on 2008-03-17
> **irw said:**
> I also did not have a pop-up message from zenity.

I originally tried to get this working by either calling zenity direct from crontab or via a script, and neither worked.

In the end the only way that worked was by running ```
xhost +local:localhost
```  To get this running at start-up, I added it to the sessions list.
I tried to get it running at boot via rc.local (?correct name - i can't remember at this moment), but could not get that to work. For now I am adding a session to all users who need it.

I spent hours trying out different variations of  --display :0 without any effect.

Maybe this could help bw44?

Ianirw,  

Many thanks for the how-to, and pointing out that --display:n  didn't solve the problem.  I was just about to go back and try playing with that.

I'm really stumped as to what it is that I have installed (or how I've set something up) that prevents zenity from displaying to the desktop, since some (most?) other users are not experiencing the problem.  I'm running a 32bit, single-user, non-networked system and I really don't do anything exotic.

Anyway, it was good to know I'm not alone --  thanks again!

bw44

---

### Post by Bruce M. on 2008-03-17
> **bw44 said:**
> irw,  

Many thanks for the how-to, and pointing out that --display:n  didn't solve the problem.  I was just about to go back and try playing with that.

I'm really stumped as to what it is that I have installed (or how I've set something up) that prevents zenity from displaying to the desktop, since some (most?) other users are not experiencing the problem.  I'm running a 32bit, single-user, non-networked system and I really don't do anything exotic.

Anyway, it was good to know I'm not alone --  thanks again!

bw44

I take it that his solution didn't help you than. :confused:

---

### Post by irw on 2008-03-17
mdpalow,

Can I suggest another file to be added to the 'Back-up Your Configuration files'?

I run an encrypted system, and /etc/crypttab is a key part of that, storing the key location or telling the system to ask for a passphrase.

Also, your pop-ups when running a backup / what-ever, don't come forward, and if you are running another program, they  will stay hidden behind it until you look for them.  I have no idea how to make them come forward - I assume it is possible?


Ian

---

### Post by Het Irv on 2008-03-17
Well, I finally got set up to test Quick Start in 8.04a6, and I have already run into a show stopping bug, sorry.  The good news is that it might be a quick fix.  

When you put in the code that installed mailx and dependencies, did you hard code it to download from the Gutsy Repos?  If so that would be why I got a ton of errors when it tried to install.  If you can you might want to code it so that it checks the version of Ubuntu that is being used and goto the correct repos, or just switch to supporting Gutsy when the time comes.

Also can you give me a list of things that you would like to be tested?

---

### Post by Het Irv on 2008-03-17
Ian, are you running Compiz-Fusion?  You might be having a problem with the pop-ups because they are not "stealing" focus from other running programs.  

Or it may not be Compiz-Fusion, the pop-ups may not gain focus at all.

---

### Post by bw44 on 2008-03-17
> **Bruce M. said:**
> I take it that his solution didn't help you than. :confused:Sorry, I wasn't clear on that.  I did not try irw's solution, though I've no reason to doubt it would work, and I may resort to it yet.  There are two reasons I didn't immediately try it: 1) I don't understand it, not because irw wasn't clear, but because I don't know enough about how the x-server works and what the command he suggested really does; and 2) I don't think I should **have** to use it. It's working for you and other folks without irw's xhost command, why not me?!? 

If I figure out whatmy problem is and am able to fix it another way, I'll post the result. It sounds like irw is managing a network and probably **had **get the problem resolved.  I have the luxury of trying to understand why it's not working on my system.

PS. Het Irv: I'm not sure if you were mentioning the possibiity of Compiz fusion causing my problem, or irw's focus problem.  I disabled Compiz and retested and it didn't help seeing the zenity message from the scheduled backup script.  But thanks, anyway.

---

### Post by bw44 on 2008-03-17
> **Het Irv said:**
> Ian, are you running Compiz-Fusion?  You might be having a problem with the pop-ups because they are not "stealing" focus from other running programs.  

Or it may not be Compiz-Fusion, the pop-ups may not gain focus at all.As I mentioned in my last post poscript, I've disabled Compiz and tested, but nothing changed. Can you suggest why the pop-up might not gain focus?  I've run the test with no other windows open on the desktop; could it still be an "unable to gain focus" problem? 

Thanks.

---

### Post by Het Irv on 2008-03-17
Under advanced settings manager ->General->Focus and Raise Behavior.

I think what I was thinking of was more of a Byrel problem, It was just an idea, but I don't think the problem is with Compiz.  
But if the pop-up is appearing just underneath everything, it is a focus problem.

Edit: Any is Default

---

### Post by bw44 on 2008-03-17
> **Het Irv said:**
> Under advanced settings manager ->General->Focus and Raise Behavior.

I think what I was thinking of was more of a Byrel problem, It was just an idea, but I don't think the problem is with Compiz.  
But if the pop-up is appearing just underneath everything, it is a focus problem.OK, I checked that.  I'm pretty new to this, so the setting "any" in the "Focus Prevention Windows" under "  advanced settings manager ->General->Focus and Raise Behavior" doesnt' mean a thing to me. But unless that's an obvious mistake (must be a default -- I never touched it), don't waste space in this thread with  an off-topic trying to clue me in!  I'll figure it out in time.

Thanks.

EDIT: ""any" is the default -- got it!

---

### Post by mdpalow on 2008-03-17
Geez!

When did all these messages get/come in. I just went to check my computer and see all these posts. :)

Unfortunately, I'm walking out the door now and won't be back for a few hours to respond. However, I will read them all again and follow-up tonight/tomorrow.

To answer one question I saw quickly...

There are Crontab files that are created each time you create a scheduled file. Personally, I don't want QuickStart deleting anyone's Crontab. That's why I make back-ups. Some stuff is just too 'touchy' and I don't want to overstep any boundaries by deleting that kind of stuff. I'd rather the user look at them and delete them. Personally, I just go in and delete all the Crontab files that have a number after them and I'm done. I made quickstart add the number of seconds from 1970 until now after the file name to differentiate them all as they're being created. 

Saw something also about adding a file to the config back-up. Shouldn't be a problem. Let me read that posting again later and see what it was all about.

Ok, running late now. Will get back to everyone later..

Good night...

---

### Post by mdpalow on 2008-03-17
> **irw said:**
> mdpalow,

Can I suggest another file to be added to the 'Back-up Your Configuration files'?

I run an encrypted system, and /etc/crypttab is a key part of that, storing the key location or telling the system to ask for a passphrase.

Also, your pop-ups when running a backup / what-ever, don't come forward, and if you are running another program, they  will stay hidden behind it until you look for them.  I have no idea how to make them come forward - I assume it is possible?


Ian

How do we as a whole benefit from this crypttab file being backed-up with the config files as opposed to the / files?

The config files I've moved separately because restoring them automatically can have some dire consequences.

If crypttab is restored with the / back-up, what's the difference?

By the way... I'm really asking... 'cause I don't know. So convince me that putting this file alone with the config files is a good idea and I'll do it. 

Thanks...

---

### Post by mdpalow on 2008-03-17
> **Het Irv said:**
> Well, I finally got set up to test Quick Start in 8.04a6, and I have already run into a show stopping bug, sorry.  The good news is that it might be a quick fix.  

When you put in the code that installed mailx and dependencies, did you hard code it to download from the Gutsy Repos?  If so that would be why I got a ton of errors when it tried to install.  If you can you might want to code it so that it checks the version of Ubuntu that is being used and goto the correct repos, or just switch to supporting Gutsy when the time comes.

Also can you give me a list of things that you would like to be tested?

No, not hard coded to check anywhere in particular. Just a simple apt-get install command. Some how I think this is going to self-fix itself shortly.

Yes, I can give you a list of what I would like tested:

Options 1-10  :lolflag:

really though... I think we're just going to have to wait until we all have 8.04. I'll have to go through it myself at first since I don't think anyone knows QuickStart as much as I do. Then, I might run some test questions by you guys to see what you think.

I think we're going to be Ok.


EDIT: Ok, not so many posts to answer. Several of them are just talk between other people. I'll just wait to hear about the CRYPTTAB file.

---

### Post by mdpalow on 2008-03-17
BW44...

Just sitting here looking at my machine and trying to think of why the pop-up isn't working for you.

The back-up is run by ROOT and the pop-up is run by YOU in the Crontab file.

Could this be a permission thing? Or do you have more than one User accounts where this account doesn't have administrative privileges? Or anything unique going on along those lines of thought?

I'm trying to get away from thinking it's something you loaded and trying to think along the lines of something in your setup/installation perhaps.

Give that some thought..

---

### Post by maxul on 2008-03-18
great application works very well and simple to use :) recommend this to all people:lolflag:

---

### Post by bw44 on 2008-03-18
> **mdpalow said:**
> BW44...

Just sitting here looking at my machine and trying to think of why the pop-up isn't working for you.

The back-up is run by ROOT and the pop-up is run by YOU in the Crontab file.

Could this be a permission thing? Or do you have more than one User accounts where this account doesn't have administrative privileges? Or anything unique going on along those lines of thought?

I'm trying to get away from thinking it's something you loaded and trying to think along the lines of something in your setup/installation perhaps.

Give that some thought..Thanks a lot for giving so much of your time.  I've been combing the forums and the net for things related to the Xorg.0.log message in the following sequence that appears every time I test:```
auth.log:   Mar 17 21:34:01 penguin-laptop CRON[19018]: pam_unix(cron:session): session opened for user bob by (uid=0)

auth.log:   Mar 17 21:34:01 penguin-laptop CRON[19020]: pam_unix(cron:session): session opened for user root by (uid=0)

syslog:     Mar 17 21:34:01 penguin-laptop /USR/SBIN/CRON[19019]: (bob) CMD (   /home/bob/Cron/QuickStart_popup       # # # Zenity Entry     # # #)

syslog:     Mar 17 21:34:01 penguin-laptop /USR/SBIN/CRON[19021]: (root) CMD (   /home/bob/Cron/my_scheduled_backup   # # # QuickStart Entry # # #)

Xorg.0.log: AUDIT: Mon Mar 17 21:34:02 2008: 5722 X: client 18 rejected from local host (uid 1000)

auth.log:   Mar 17 21:34:11 penguin-laptop CRON[19018]: pam_unix(cron:session): session closed for user bob

auth.log:   Mar 17 21:34:11 penguin-laptop CRON[19020]: pam_unix(cron:session): session closed for user root
```Does this ring any bells?

It may, as you suggest, be a permission issue, but I tend to think it's related to the suggestion that irw made:```
$ xhost +local:localhost
``` But I still don't know enough to guess what to try, or why X is rejecting the zenity client request (if I'm correctly interpreting what's happening).

I don't have any other users defined and as far as I know I have whatever privileges the default Ubuntu user gets. :(

---

### Post by mdpalow on 2008-03-18
well, now you kinda know why I wanted to load MAILX instead of just exim4. I think MAILX might give you a clue as to what the problem is. 

If you install MAILX, then let the SB start and then after the pop-up doesn't come up, you can look in /var/mail/your_name and see what it says as to why it's not working.

---

### Post by bw44 on 2008-03-18
> **mdpalow said:**
> well, now you kinda know why I wanted to load MAILX instead of just exim4. I think MAILX might give you a clue as to what the problem is. 

If you install MAILX, then let the SB start and then after the pop-up doesn't come up, you can look in /var/mail/your_name and see what it says as to why it's not working.

Here is the last message in my 30.3 MB /var/mail/bob file (shouldn't this get cleaned up somehow?  I didn't know it existed.  OK to delete it?):```
From: root@penguin-laptop (Cron Daemon)
To: bob@penguin-laptop
Subject: Cron <bob@penguin-laptop>    /home/bob/Cron/QuickStart_popup       # # # Zenity Entry     # # #
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin>
X-Cron-Env: <HOME=/home/bob>
X-Cron-Env: <LOGNAME=bob>
Message-Id: <E1JbUFA-00058p-LR@penguin-laptop>
Date: Tue, 18 Mar 2008 01:20:12 -0400

Setting pipeline to PAUSED ...
Pipeline is PREROLLING ...
Pipeline is PREROLLED ...
Setting pipeline to PLAYING ...
New clock: GstAudioSinkClock
Got EOS from element "pipeline0".
Execution ended after 527138000 ns.
Setting pipeline to PAUSED ...
Setting pipeline to READY ...
Setting pipeline to NULL ...
FREEING pipeline ...
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(zenity:19771): Gtk-WARNING **: cannot open display:
```

Are we getting closer?

---

### Post by mdpalow on 2008-03-18
Post that in the beginners help section and I'm sure someone will answer it in no time at all.

---

### Post by bw44 on 2008-03-18
> **mdpalow said:**
> Post that in the beginners help section and I'm sure someone will answer it in no time at all.OK. But you're hardly a "beginner" and if you don't know . . .  By 'that" I assume you  mean the mail  message I just sent you.  Before I post it, could you fill me in on how this message was produced, so I can describe where it came from, or how I came to have it?  It doesn't look like the sort of thing a beginner (like me) would just happen to stumble on!  

Thanks.

---

### Post by mdpalow on 2008-03-18
> **bw44 said:**
> OK. But you're hardly a "beginner" and if you don't know . . .  By 'that" I assume you  mean the mail  message I just sent you.  Before I post it, could you fill me in on how this message was produced, so I can describe where it came from, or how I came to have it?  It doesn't look like the sort of thing a beginner (like me) would just happen to stumble on!  

Thanks.

It was produced by MAILX because there was a fault in something you ran (pop-up didn't work). Getting kinda late here BW44, so I'm gonna let you draft your own question. You're very articulate and I know you'll formulate a good posting that even goes more into detail than is needed. ;)

I'm off to bed and will check in with you tomorrow. Send me PM's on this from now on please, so we don't fill thread with unique problem.

Thanks... and good night.

---

### Post by bw44 on 2008-03-18
> **mdpalow said:**
> It was produced by MAILX because there was a fault in something you ran (pop-up didn't work). Getting kinda late here BW44, so I'm gonna let you draft your own question. You're very articulate and I know you'll formulate a good posting that even goes more into detail than is needed. ;)Is that a left-handed compliment or what?!?! ;)

Thanks for your help. I won't clutter the thread with any more discussion of the problem (after this post anyway).  Ian ("irw") posted his solution earlier, which I didn't understand then> I also did not have a pop-up message from zenity.

I originally tried to get this working by either calling zenity direct from crontab or via a script, and neither worked.

In the end the only way that worked was by running```
xhost +local:localhost
```

To get this running at start-up, I added it to the sessions list. I tried to get it running at boot via rc.local (?correct name - i can't remember at this moment), but could not get that to work. For now I am adding a session to all users who need it.

I spent hours trying out different variations of --display :0 without any effect.I found a very similar solution in another thread by searching on ```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
```
[http://ubuntuforums.org/showthread.php?t=711631](http://ubuntuforums.org/showthread.php?t=711631) If any other QuickStart users run into the problem, they can certainly implement Ian's solution, which gets around the problem that just entering the command only fixes the problem until your system is re-booted. 

If anyone ever discovers why the problem occurs in the first place, but only for certain users, I would welcome a post (or private message) with the solution.

Cheers.

---

### Post by Techwiz on 2008-03-18
HELP!
My computer's files all dissappered (don't ask for details please) more to the point. I have a backup made by QuickStart 6.0 but, the computer will not restore it! I choose restore a backup>restore home>and I nacigate to my backup in the popup window. 0.5 seconds later, a popup tells me that the restore is complete. 1. I have 3.9 GB of data in that archive 0.5 seconds is not enough to extract and restore it, 2. after a reboot, it is not there. Could you help me?

---

### Post by MaxVK on 2008-03-18
First for Techwiz: Where is your backup? I just had a similar issue while my backup file was on an external disk. To get around it just copy the file to the desktop and use that one for the backup.


Now for the main post:
I just used Quickstart to relocate my entire installation to a larger space.
I installed Ubuntu onto the larger area, creating a separate partition for /home.
I then copied my backup to the desktop (See above) and performed the restore on /home and / (In that order, I have no idea if that would make any difference or not).

After a reboot everything worked perfectly except for my marble trackball, but it was eaasy enough to copy the configuration from the original installation.

A great many thanks for Quickstart - Excellent piece of kit!

Regards

Max

---

### Post by StiveG on 2008-03-18
Hi,

I'm giving it a try :)

French users must modify the .sh file before install, change all paths referring to "desktop" to "bureau"

:)

---

### Post by mdpalow on 2008-03-18
> **bw44 said:**
> Here is the last message in my 30.3 MB /var/mail/bob file (shouldn't this get cleaned up somehow?  I didn't know it existed.  OK to delete it?)

Yes, Ok to delete it. :)

EDIT:

It didn't exist until you installed MAILX. That file is what I used to troubleshoot some functions in QS when something didn't work as expected. If you delete it, MAILX will simply create another. If it's too much, you can always uninstall it.

---

### Post by mdpalow on 2008-03-18
> **Techwiz said:**
> HELP!
My computer's files all dissappered (don't ask for details please) more to the point. I have a backup made by QuickStart 6.0 but, the computer will not restore it! I choose restore a backup>restore home>and I nacigate to my backup in the popup window. 0.5 seconds later, a popup tells me that the restore is complete. 1. I have 3.9 GB of data in that archive 0.5 seconds is not enough to extract and restore it, 2. after a reboot, it is not there. Could you help me?

Hi Techwiz...

Very sorry to hear about your data and the current position you find yourself in.

What are the total sizes for all three back-ups you have? You should have /, /home. and config.

/ should be very close to 1 gig
/home depends on what you're doing obviously
config should be very small like 3 KB compressed

If you lost all the files on your computer then it sounds like you don't have enough files to even run QuickStart. If you're SURE you've lost everything AND you have a good back-up, then you might need to go ahead and restore your Live CD, QuickStart, and then your files again.

That's how QuickStart was written to work anyways.... that is - use Live CD first and then restore your back-up.

You can click on your back-up archives and look what's in them to see if you got it all backed-up properly.

Will keep an eye out for you.

---

### Post by mdpalow on 2008-03-18
> **MaxVK said:**
> First for Techwiz: Where is your backup? I just had a similar issue while my backup file was on an external disk. To get around it just copy the file to the desktop and use that one for the backup.


Now for the main post:
I just used Quickstart to relocate my entire installation to a larger space.
I installed Ubuntu onto the larger area, creating a separate partition for /home.
I then copied my backup to the desktop (See above) and performed the restore on /home and / (In that order, I have no idea if that would make any difference or not).

After a reboot everything worked perfectly except for my marble trackball, but it was eaasy enough to copy the configuration from the original installation.

A great many thanks for Quickstart - Excellent piece of kit!

Regards

Max

Thanks Max...

Doesn't matter which you restore first (/home or /). However, didn't you make a back-up of your config files along with your other two?

A complete QuickStart back-up consists of three archives.

Glad it worked out for you.

---

### Post by MaxVK on 2008-03-18
Indeed I did make a backup of all three, however, Ubuntu has moved physical drives (hda to hdb) and in another [thread]("http://ubuntuforums.org/showthread.php?t=723154&page=2") you said:

> Just don't restore your config files and you'll be fine

I assumed this would be because of the physical drive change (Perhaps some of the config would point to a particular hd partition etc)

Anyway, its working just fine and I still have my original installation sitting there for experimental use etc.

Nice one! :)

---

### Post by Tews on 2008-03-18
I just wanted to add my thanks for such a magnificent app!  Ive only been using linux for about 10 days now after 10+ years with Windows, and I cant begin to tell you how much I am amazed with it. Your script makes it so simple.  Kudos to everyone!!

---

### Post by tobydeemer on 2008-03-18
Hi-

I had another question. Here's my situation- I had an experimental install of Ubuntu dual-booting with Windows for several months. During that time, I experimented with a lot of things, like different window managers, desktop environments, etc, etc. Bottom line it, things were just a touch buggy from doing all the config and reconfig, install, uninstall, etc.

Well, after all that, I decided to do a total HD install and be rid of XP. What I have now is a fairly stock Ubuntu 7.10 install, set up with the apps and config how I like it after all the testing and messing. However, there is one program that is in the backups I ran before that (dumbass) I forgot to copy before I did the new install. 

My question is- can I get that one program and its data out of the backups and install it without reinstalling all the other data and configs? I don't want to do a complete backup restore, as the old configs are what were bugged up from my meddling. Any thoughts are appreciated, even if only to point me to an earlier post I missed. 

Thanks again for all your work.

Sorry- just though of another question. I don't know if this has been asked already, but what is the possibility of using a Quickstart backup of a Windows partition as an image for a VM?

---

### Post by terry_gardener on 2008-03-18
hello i seem to be having a little problem with the schedule part of this program. basically i setup the schedule and setup date time. it starts at this time and creates 3 files on desktop. 

when i check the archive of the files the config settings looks ok but the system and the home dont have everything in it. home is completly empty and system has some files from the dev folder but nothing else. 

when i run the file /home/username/Crom/my-schedule_backup and run in terminal it works fine. 

any ideas it is driving me nuts.

---

### Post by evilc on 2008-03-18
> **terry_gardener said:**
> 

when i check the archive of the files the config settings looks ok but the system and the home dont have everything in it. home is completly empty and system has some files from the dev folder but nothing else. 

when i run the file /home/username/Crom/my-schedule_backup and run in terminal it works fine. 

any ideas it is driving me nuts.

Install Mailx from the Install programs (8 option) this will fix the schedule problem.

---

### Post by 3pinner on 2008-03-18
Hello there,
This is a terrific program, and I have one little hitch I need help with.
After downloading and installing, all my media players stopped working, totem movie player, all ny audio players (cd players) will load, but won't palay anything. They just "grey out" and crash. they worked fine before.:confused:
Any suggestions????
installed on Ubuntu 7.10

EDIT: Spoke waaaaaaaaaaaay too soon. Everything fine after a reboot. Sorry no need to reply!

Thanks!

---

### Post by Tews on 2008-03-18
I have one problem .. maybe serious, maybe not.  Whenever I try to restore my config backup, I get no popup showing progress or when its done.  No hard drive activity ... it just sits there.  I let it sit like that and finally tried to re-boot, but that option is no longer displayed, so I did a log-out.  When it gets to the splash screen it freezes and the only option is to do a reinstall and restore (without config)  The only thing that I have to do at that point is enable my Nvidia driver and all seems good after that.  Any ideas????

---

### Post by mdpalow on 2008-03-18
> **tobydeemer said:**
> Hi-

I had another question. Here's my situation- I had an experimental install of Ubuntu dual-booting with Windows for several months. During that time, I experimented with a lot of things, like different window managers, desktop environments, etc, etc. Bottom line it, things were just a touch buggy from doing all the config and reconfig, install, uninstall, etc.

Well, after all that, I decided to do a total HD install and be rid of XP. What I have now is a fairly stock Ubuntu 7.10 install, set up with the apps and config how I like it after all the testing and messing. However, there is one program that is in the backups I ran before that (dumbass) I forgot to copy before I did the new install. 

My question is- can I get that one program and its data out of the backups and install it without reinstalling all the other data and configs? I don't want to do a complete backup restore, as the old configs are what were bugged up from my meddling. Any thoughts are appreciated, even if only to point me to an earlier post I missed. 

Thanks again for all your work.

Sorry- just though of another question. I don't know if this has been asked already, but what is the possibility of using a Quickstart backup of a Windows partition as an image for a VM?

Yes, I think you could remove a single application from a back-up, but you wouldn't do it using QuickStart. Just click on the archive and navigate the directories. If your app. is in a single folder and not spread all over the place, I don't see why you couldn't just EXTRACT HERE that folder/directory and then copy it to your hard drive.

As for copying your windows partition and then using it for a VM OS. I don't know, but I'm thinking that won't work. I don't want to write all the reasons why I think it won't work, but you can try it. I give it a very small chance of working.

---

### Post by mdpalow on 2008-03-18
> **MaxVK said:**
> Indeed I did make a backup of all three, however, Ubuntu has moved physical drives (hda to hdb) and in another [thread]("http://ubuntuforums.org/showthread.php?t=723154&page=2") you said:



I assumed this would be because of the physical drive change (Perhaps some of the config would point to a particular hd partition etc)

Anyway, its working just fine and I still have my original installation sitting there for experimental use etc.

Nice one! :)

Yes, you were right not to restore the config files blindly with the change in partitions. Just didn't understand your previous message and that's why I asked. :)

good for you for paying attention!  ;)

---

### Post by mdpalow on 2008-03-18
> **terry_gardener said:**
> hello i seem to be having a little problem with the schedule part of this program. basically i setup the schedule and setup date time. it starts at this time and creates 3 files on desktop. 

when i check the archive of the files the config settings looks ok but the system and the home dont have everything in it. home is completly empty and system has some files from the dev folder but nothing else. 

when i run the file /home/username/Crom/my-schedule_backup and run in terminal it works fine. 

any ideas it is driving me nuts.

Have you downloaded the latest QuickStart that came out only two days ago? If not, select the option to update QuickStart next time you open it up.

---

### Post by mdpalow on 2008-03-18
> **Tews said:**
> I have one problem .. maybe serious, maybe not.  Whenever I try to restore my config backup, I get no popup showing progress or when its done.  No hard drive activity ... it just sits there.  I let it sit like that and finally tried to re-boot, but that option is no longer displayed, so I did a log-out.  When it gets to the splash screen it freezes and the only option is to do a reinstall and restore (without config)  The only thing that I have to do at that point is enable my Nvidia driver and all seems good after that.  Any ideas????

The config file doesn't always bring up a window I've seen. I'm thinking because the file is so small that it's actually done before it gets to it. Not sure...

Not unusual to not have the reboot option after restoring files. Just logout, back-in OR when you logout then click the options at the bottom left and then click or reboot.

I haven't done a restore in a while, so I'm a little rusty on what we're seeing when done, but I DO Remember seeing the restricted drivers needed to be enabled after doing a restore. I THINK I've also seen it where I didn't have to enable restricted drivers when doing a restore. 

I will have to check it out next time I do a restore.

---

### Post by Tews on 2008-03-18
My main concern is restoring the config backup totally hoses my installation, forcing me to do a complete reinstall of the OS.  If the config backup isnt really necessary, no problem, however if it IS then ....

---

### Post by mdpalow on 2008-03-19
> **Tews said:**
> My main concern is restoring the config backup totally hoses my installation, forcing me to do a complete reinstall of the OS.  If the config backup isnt really necessary, no problem, however if it IS then ....

The config file restore is hosing up your complete restore because SOMETHING has changed since you made that CONFIG FILE back-up, right?

The config file is most certainly NOT needed to do a restore. However, IF you have certain monitor or hard drive settings you want to use again then it would be. However (again), if something (hardware or partition settings for example) have changed then you wouldn't want to restore it, BUT instead just open those files separately onto your desktop and copy the entries out of the individual files and paste the info into the NEW config files.

Make sense? If not, read the HELP Wiki where it explains this in more detail. Speaking of HELP. Does ANYONE read the HELP file? ;)

Good night everyone...

---

### Post by Tews on 2008-03-19
No, actually, I didn't.  I made the initial restore after downloading QuickStart, then did a reinstall of the OS to test it.  Its really not that big of a deal as I didnt lose anything... and yes, I do read the help files!:lolflag:

---

### Post by mdpalow on 2008-03-19
> **Tews said:**
> No, actually, I didn't.  I made the initial restore after downloading QuickStart, then did a reinstall of the OS to test it.  Its really not that big of a deal as I didnt lose anything... and yes, I do read the help files!:lolflag:

I'm sorry, but I don't see how that's possible. Maybe I'm misunderstanding something.

Good to know at least one person is reading the help file. :) thanks..

---

### Post by Tews on 2008-03-19
I got to thinking about it this morning and there was one thing I did ... I ran the update manager before restoring ... sure enough that was the problem .. did a re-install, then a restore without updating and everything went smooth as ... well you get my meaning ;) ...  Thanks again!

---

### Post by mdpalow on 2008-03-19
> **Tews said:**
> I got to thinking about it this morning and there was one thing I did ... I ran the update manager before restoring ... sure enough that was the problem .. did a re-install, then a restore without updating and everything went smooth as ... well you get my meaning ;) ...  Thanks again!

Ok, good.

That makes better sense.

Just a reminder to everyone. When restoring:

1. Use Live CD to install OS

2. Install QuickStart immediately after step one above

3. Restore archives, enable Restricted Drivers if needed

4. Restart/Reboot

That should do it. At this point you should only have to install new updates that came out SINCE/AFTER you made your back-up.


Thanks Tews...

---

### Post by terry_gardener on 2008-03-19
i tried both fixes suggested mailx and update. 

scheduled backup and it works 

thank you so much it was driving me nuts.

---

### Post by tobydeemer on 2008-03-19
> **mdpalow said:**
> Yes, I think you could remove a single application from a back-up, but you wouldn't do it using QuickStart. Just click on the archive and navigate the directories. If your app. is in a single folder and not spread all over the place, I don't see why you couldn't just EXTRACT HERE that folder/directory and then copy it to your hard drive.

As for copying your windows partition and then using it for a VM OS. I don't know, but I'm thinking that won't work. I don't want to write all the reasons why I think it won't work, but you can try it. I give it a very small chance of working.

-Thanks for getting back. I was thinking about it after I posted last night, so I did start looking at the archives and figured I may be able to pick and choose like you said. So that's good.

-The VM thing... well I was just thinking on a long shot anyway, no sweat there.

Thanks again and keep up the awesome work.

---

### Post by mdpalow on 2008-03-19
> **terry_gardener said:**
> i tried both fixes suggested mailx and update. 

scheduled backup and it works 

thank you so much it was driving me nuts.

Yeah, the update now checks to see if you have some other files needed to run a scheduled back-up and if not - then it downloads/installs them.

Either way, you're Ok now.

Enjoy...

---

### Post by Bruce M. on 2008-03-19
> **mdpalow said:**
> Ok, good.

That makes better sense.

Just a reminder to everyone. When restoring:

1. Use Live CD to install OS

2. Install QuickStart immediately after step one above

3. Restore archives, enable Restricted Drivers if needed

4. Restart/Reboot

That should do it. At this point you should only have to install new updates that came out SINCE/AFTER you made your back-up.


Thanks Tews...

I'm curious about something...

> 1. Use Live CD to install OS

Why the Live CD and not the Alt CD?

I haven't used a Live CD to install since my very first install of Dapper. I've used the Alt CD since then as it gives me the option as to where to put my **/home** folder and I create a separate partition for that.

Bruce

---

### Post by mdpalow on 2008-03-19
> **Bruce M. said:**
> I'm curious about something...



Why the Live CD and not the Alt CD?

I haven't used a Live CD to install since my very first install of Dapper. I've used the Alt CD since then as it gives me the option as to where to put my **/home** folder and I create a separate partition for that.

Bruce

Sorry....

Use whatever CD you want to get Ubuntu loaded on your machine. :)

I just use Live CD, so that's what I'm thinking when I write stuff like this.

---

### Post by Techwiz on 2008-03-19
Ok, all the stuff I had a couple of weeks ago is back. It is all fine now! QuickStart is a really great program! Thanks for all your help. Oh and only one problem, My video's thumbnails are the generic icon, not as they were before, the "preview". How can I enable the preview thumbnail for movie files?

---

### Post by Bruce M. on 2008-03-19
> **mdpalow said:**
> Sorry....

Use whatever CD you want to get Ubuntu loaded on your machine. :)

I just use Live CD, so that's what I'm thinking when I write stuff like this.

[SIZE="1"]And I heard a mysterious voice say:[/SIZE]

> Use the Force Luke, use either CD, Bruce

OK, thanks, Yo ... er ... mdpalow

---

### Post by mdpalow on 2008-03-19
> **Techwiz said:**
> Ok, all the stuff I had a couple of weeks ago is back. It is all fine now! QuickStart is a really great program! Thanks for all your help. Oh and only one problem, My video's thumbnails are the generic icon, not as they were before, the "preview". How can I enable the preview thumbnail for movie files?

Gotta go, gotta go, gotta go.

Can someone help with this?

Thanks

---

### Post by Bruce M. on 2008-03-19
> **Techwiz said:**
> Ok, all the stuff I had a couple of weeks ago is back. It is all fine now! QuickStart is a really great program! Thanks for all your help. Oh and only one problem, My video's thumbnails are the generic icon, not as they were before, the "preview". How can I enable the preview thumbnail for movie files?

Check out: [Video file preview thumbnails]("http://ubuntuforums.org/showthread.php?t=663072")

Ask again if you need more help.
Bruce

EDIT:  Did you know that Ubuntu has it's own Google Search engine?

[Ubuntu Search Engine]("http://crunchbang.org/ubuntu-search-engine/")

---

### Post by Bruce M. on 2008-03-19
> **mdpalow said:**
> Gotta go, gotta go, gotta go.

Can someone help with this?

Thanks

Done.  :)

---

### Post by Dynamo_Joe on 2008-03-20
Hi mdpalow, 

Apologies for getting back to you so late. 

1. Did a backup on the old (smaller) HDD of all three files. 

2. Install Ubuntu on the new (bigger) HDD. 

3. Let the new install detect any updates (and applied the updates). 

4. Restored "/" first followed by "/home". 

5. Loss the "Shut Down" and "Restart" buttons - no probs, did a "CTRL-ALT-Backspace" to restart GDM. 

6. Got the buttons back - did a "Restart". 

7. Just finished checking everything was okay - no majors. 

8. Many thanks for such a useful tool.

---

### Post by Bruce M. on 2008-03-20
> **Dynamo_Joe said:**
> Hi mdpalow, 

Apologies for getting back to you so late. 

1. Did a backup on the old (smaller) HDD of all three files. 

2. Install Ubuntu on the new (bigger) HDD. 

3. Let the new install detect any updates (and applied the updates). 

4. Restored "/" first followed by "/home". 

5. Loss the "Shut Down" and "Restart" buttons - no probs, did a "CTRL-ALT-Backspace" to restart GDM. 

6. Got the buttons back - did a "Restart". 

7. Just finished checking everything was okay - no majors. 

8. Many thanks for such a useful tool.

It probably would have been easier this way...

[LIST=1]
[*] Did a backup on the old (smaller) HDD of all three files.
[*] Install Ubuntu on the new (bigger) HDD. 
[*] **Restore "/" and "/home".**
[*] **Detect and apply updates.**
[/LIST]

#4 may not have been necessary, and if it was; to a lesser degree.

But, hey, whatever works ... right!

And QS works.  :)

---

### Post by Bubba64 on 2008-03-20
I installed the basic program and realize I don't really need it I have been unable to remove it what is the actual program name for apt-get removal or where is it at I couldn't find it in synaptic or add remove.

---

### Post by Bruce M. on 2008-03-20
> **Bubba64 said:**
> I installed the basic program and realize I don't really need it I have been unable to remove it what is the actual program name for apt-get removal or where is it at I couldn't find it in synaptic or add remove.

Too easy...

In your /home folder you'll see a QuickStart folder with three files in it.

Delete the folder and files ... you're done!

Bruce

---

### Post by Bubba64 on 2008-03-20
I Did That after posting thanx for the confirmation. When I do a search for there is residual stuff still coming up though, I haven't done a restart that may be all I need to do.

---

### Post by Bruce M. on 2008-03-20
> **Bubba64 said:**
> I Did That after posting thanx for the confirmation. When I do a search for there is residual stuff still coming up though, I haven't done a restart that may be all I need to do.

What "residual stuff" are you talking about?

QuickStart only has three files.

Bruce

---

### Post by Bubba64 on 2008-03-20
Nothing comes up now after a restart. I wish I could give you a good answer to your question but I am just a basic user who knows a few terminal commands. I may have been seeing something not associated with quickstart. So put me down as a thank you to Bruce M.

---

### Post by Zoltarp on 2008-03-20
Thanks for the great utility!

---

### Post by madara_sama on 2008-03-20
Nice backup utility, great job, and I have to try it.
Thanks.

---

### Post by mdpalow on 2008-03-21
[COLOR="Red"]**[SIZE="3"]NEW UPDATE AVAILABLE[/SIZE]**[/COLOR]

Hi Everyone,

Bruce contacted me and asked if I could make option 6 (view/edit config files) use either 'gedit' or 'kate' depending on what OS you were using. Didn't seem like a difficult request, so why not.

Now QuickStart will open your config files regardless of which editor (gedit/kate) you're using. 

Also, it seemed like the right time to add the option to UNINSTALL QuickStart from your computer. Therefore, the new option 13 (Lucky 13) is to remove/uninstall QuickStart from your machine.

I never had an uninstall built in because I never in a million years would have guessed ANYONE would EVER want to remove QuickStart from their computer! What's wrong with you! ;)

I also thought it was pretty simple to delete the folder, but in hindsight - I'm not sure it was fair to assume a user would know to look at /home/their_name/QuickStart. I think we're so used to Windows loading things EVERYWHERE, we just assume QuickStart has hundreds of files scattered all over the place. It only has three (3) VERY SMALL files by the way.

Ok, so new update is loaded to server...... Fire at will.

---

### Post by Bruce M. on 2008-03-21
> **mdpalow said:**
> [COLOR="Red"]**[SIZE="3"]NEW UPDATE AVAILABLE[/SIZE]**[/COLOR]

Hi Everyone,

Bruce contacted me and asked if I could make option 6 (view/edit config files) use either 'gedit' or 'kate' depending on what OS you were using. Didn't seem like a difficult request, so why not.

Now QuickStart will open your config files regardless of which editor (gedit/kate) you're using. 

Also, it seemed like the right time to add the option to UNINSTALL QuickStart from your computer. Therefore, the new option 13 (Lucky 13) is to remove/uninstall QuickStart from your machine.

I never had an uninstall built in because I never in a million years would have guessed ANYONE would EVER want to remove QuickStart from their computer! What's wrong with you! ;)

I also thought it was pretty simple to delete the folder, but in hindsight - I'm not sure it was fair to assume a user would know to look at /home/their_name/QuickStart. I think we're so used to Windows loading things EVERYWHERE, we just assume QuickStart has hundreds of files scattered all over the place. It only has three (3) VERY SMALL files by the way.

Ok, so new update is loaded to server...... Fire at will.

GOT IT!
And, since 13 is unlucky I'll never use it.  :)

Bruce

---

### Post by Bubba64 on 2008-03-21
> **mdpalow said:**
> [COLOR="Red"]**[SIZE="3"]NEW UPDATE AVAILABLE[/SIZE]**[/COLOR]

Hi Everyone,

Bruce contacted me and asked if I could make option 6 (view/edit config files) use either 'gedit' or 'kate' depending on what OS you were using. Didn't seem like a difficult request, so why not.

Now QuickStart will open your config files regardless of which editor (gedit/kate) you're using. 

Also, it seemed like the right time to add the option to UNINSTALL QuickStart from your computer. Therefore, the new option 13 (Lucky 13) is to remove/uninstall QuickStart from your machine.

I never had an uninstall built in because I never in a million years would have guessed ANYONE would EVER want to remove QuickStart from their computer! What's wrong with you! ;)

I also thought it was pretty simple to delete the folder, but in hindsight - I'm not sure it was fair to assume a user would know to look at /home/their_name/QuickStart. I think we're so used to Windows loading things EVERYWHERE, we just assume QuickStart has hundreds of files scattered all over the place. It only has three (3) VERY SMALL files by the way.

Ok, so new update is loaded to server...... Fire at will.

It is all right to question my intelligence on wanting to delete this program, I wonder about it all the time. The reason I don't need it  basically is, I have 2 computers with the same set up and the one I put the program on is a a21m IBM laptop which I will replace soon. This is an ancient computer and I have nothing to lose on in it if it went belly up I would give it a good smattering of applause for lasting as long as it has with over 300 errors on the hard drive and still running Gutsy. I also am pretty aware of what not to do to safeguard my computer against screwing it up, at least thats what I tell myself.. I finally looked in the home folder before I read Bruce M's post, why I hadn't I am not sure, I guess I wasn't that concerned, it seemed like a harmless program unless I got it to start any process. I have been told I was 1 in a million in positive and negative ways, but I just ignore both sides due to the projection factor that we all practice.

---

### Post by mdpalow on 2008-03-21
> **Bubba64 said:**
> It is all right to question my intelligence on wanting to delete this program, I wonder about it all the time. The reason I don't need it  basically is, I have 2 computers with the same set up and the one I put the program on is a a21m IBM laptop which I will replace soon. This is an ancient computer and I have nothing to lose on in it if it went belly up I would give it a good smattering of applause for lasting as long as it has with over 300 errors on the hard drive and still running Gutsy. I also am pretty aware of what not to do to safeguard my computer against screwing it up, at least thats what I tell myself.. I finally looked in the home folder before I read Bruce M's post, why I hadn't I am not sure, I guess I wasn't that concerned, it seemed like a harmless program unless I got it to start any process. I have been told I was 1 in a million in positive and negative ways, but I just ignore both sides due to the projection factor that we all practice.

:)

I sure hope you didn't take my post the wrong way. I wasn't even really bothered because this has been asked many times and I only just now got around to doing something I should have done several months ago.

Your posting just hit at a really good time when I had a free moment to do it and also wasn't feeling so beat up by QS that I didn't want to do anything to it.

QS was a lot of work. After something like that - you kinda get burned out for a while and just don't want to do anything else for a while.

thanks.

---

### Post by Bubba64 on 2008-03-21
> **mdpalow said:**
> :)

I sure hope you didn't take my post the wrong way. I wasn't even really bothered because this has been asked many times and I only just now got around to doing something I should have done several months ago.

Your posting just hit at a really good time when I had a free moment to do it and also wasn't feeling so beat up by QS that I didn't want to do anything to it.

QS was a lot of work. After something like that - you kinda get burned out for a while and just don't want to do anything else for a while.

thanks.
No offense taken I thought it was funny I forgot and left out the smiley faces to convey this. I also have a gigantic ego, but through the study of Jungian Psychology and being a student studying to work as a professional in the Psychology field, I recognize that I am no different than anybody else in my accomplishments. Offense is usually taken when somebody criticizes you on something you already question in yourself, in simple terms self esteem. I appreciate your concern though.

---

### Post by newbieforever on 2008-03-22
isnt [http://www.mondorescue.org](http://www.mondorescue.org) better?
simply real power in your hand, in a 123 snap!
i really love mondo...
it is very easy to get, use, and restore: 2 minutes to install, 30 seconds to start the backup (or drive image), you go to launch, when you are back you really have  your [B]bootable backup dvd
[/B]not to say you can do selective back and/or restore

enjoy

nbfe

---

### Post by Tews on 2008-03-22
I really dont think that its a matter of which one is "better", but which one does what **YOU** want it to do!  For me, Quick-Start is truly a "set and forget" app.  I dont have to burn a DVD/CD to completely restore my drive.  All of my backups are automatic and stored to an external drive so I dont have to worry about losing my data if something happens to my internal drive.  It takes me 25 minutes to do a complete restore and Ive yet to find any other app that does it as quickly as that.

If you are happy with MondoSecure then by all means, use it, however, I'm sticking with Quick-Start! :D

---

### Post by jakupl on 2008-03-22
great !:KS

---

### Post by fourthofjuly on 2008-03-22
> **mdpalow said:**
> Hi Everyone,

I've written a script to expedite some things I do on my computer. If interested, you're welcome to download and use it. I call it QuickStart and with it you can:

(screen shots are attached below)


[COLOR="Red"]1. Install the proper DVD & Codecs files so you can play a DVD in your drive using Totem, etc. (works with 7.10 / 7.04 and 32-bit / 64-bit). [/COLOR]

2. Back-up Your /home folders  

3. Back-up Your / folders

4. Back-up Your Configuration files separately (fstab, device.map, mtab, menu.lst, and xorg.conf)

5. Create a Custom Back-up for selected folders

6. Create a Custom Scheduled (Recurring) Back-up (daily, weekly, or monthly). You decide the exact date and time

7. Create a Scheduled 1:1 Synchronized Back-Up of Selected Folders to Another Drive/Partition.

8. Restore Your System /home folders

9. Restore Your / folders

10. Restore Your configuration files

11. Install some common applications (aMSN, aMSN fix, Firestarter,  AllTray, and a few others). Nice when you're starting from scratch (clean install)

12. House Cleaning (delete unnecessary files throughout your computer). 

13. View or Edit Your Key Files (fstab, menu.lst, and xorg.conf).

[COLOR="Red"]14. Back-up Your Master Boot Record (MBR)[/COLOR].

[COLOR="Red"]15. Back-up Your Windows Partition (dual booters) While in Ubuntu[/COLOR].

16. Format Windows Partition in NTFS with gParted.

[COLOR="Red"]17. Restore Your Master Boot Record (MBR)[/COLOR].

[COLOR="Red"]18. Restore Your Windows Back-Up While in Ubuntu[/COLOR].

19. Download Updates/Upgrades with a click of the mouse.



**How to download and install QuickStart** (Please follow these instructions exactly as they are written) :

1. Left-click the Install_QuickStart.sh file below and save it to your [COLOR="Red"]DESKTOP[/COLOR]

2. RIGHT click the Install_QuickStart.sh file on your DESKTOP and select Properties, then select the Permissions tab at the top, and ensure the 'Execute' check-box is checked towards the bottom where it says 'Allow executing file as program'. Close window.

3. If you installed the Ubuntu 32-bit OS you can skip this step. If you installed the Ubuntu 64-bit OS, open a terminal window and copy/paste the following, so your system can run 32-bit applications: [COLOR="Red"]sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0[/COLOR]

4. Click or double-click the Install_QuickStart.sh file now located on your Desktop and select [COLOR="Red"]Run in Terminal[/COLOR]

You will now have a QuickStart icon in your menu ( Applications -> Accessories -> QuickStart ) 



[COLOR="Blue"]1.) Please post a message after downloading the program to bump it to the top for others to see in case they want it too.[/COLOR]

[COLOR="Blue"]2.) Probably a good idea to subscribe to this thread if you plan on using this program as some postings might be of interest to you.[/COLOR]
.
thanks a lot.... much appreciated utility...

truly user-friendly, since a newbie like me could backup my entire server...!!!

Sir, maybe your utility could be included in upcoming Ubuntu distros if you would like to?

please do reply... thanks once again...

regards,

devang.

---

### Post by Bruce M. on 2008-03-22
> **Tews said:**
> I really dont think that its a matter of which one is "better", but which one does what **YOU** want it to do!  For me, Quick-Start is truly a "set and forget" app.  I dont have to burn a DVD/CD to completely restore my drive.  All of my backups are automatic and stored to an external drive so I dont have to worry about losing my data if something happens to my internal drive.  It takes me 25 minutes to do a complete restore and Ive yet to find any other app that does it as quickly as that.

If you are happy with MondoSecure then by all means, use it, however, I'm sticking with Quick-Start! :D

+1.  I started out with HUBackup/HURestore and when I needed it, Restore didn't!
So I looked around at various backup/restore procedures, programs.

For me, mdpalow's QuickStart is a GEM for just the backup/restore functions. The other things it does, and does extremely well, would make this utility a nomination for a Programmer's Guild Oscar if such a thing existed.

Set it, forget it!

My Scheduled Backups go to a second HD completely away from Ubuntu, every night as well as my "Scheduled Sync'ed Folders".

And if I want to test something, there is always the "Do it now" manual option in case the test goes south.

So yes, I agree with Tews enough to repeat what he said:

> **Tews said:**
> I really dont think that its a matter of which one is "better", but which one does what **YOU** want it to do!

Bruce

---

### Post by Bruce M. on 2008-03-22
Today I used QuickStart restore for real!

I was here in the forums and Firefox froze, chewing up 100% of my CPU.
I couldn't get out, so I did a Ctrl+Alt+Backspace ... without doing enything I was shocked!

I lost both panels in Xfce

I found out how to get them back [[SOLVED] Xfce: Help, I've lost my panels.]("http://ubuntuforums.org/showthread.php?t=731978") But in the process I only had partial generic panels.

I tried extracting just **panels.xml** from the backup, but that didn't work, there was something else somewhere that was needed, or maybe because I had created the generic panels, I don't know.

Between last nights backup and today I received three emails (answered) sooooooooo.

I restored my **/home** folder.  YES!  Panels back.

God Bless you mpadlow, and all of your descendants, for making QuickStart!
Have a Super-Fantastic Weekend my friend
Bruce

---

### Post by Tews on 2008-03-22
I was in an adventurous mood so I thought I'd give the latest LTS build of Hardy Herron a go ... Burnt a new ISO, booted and installed without a hitch ... Not really paying attention I installed QS and proceeded to do a restore .. whooo boy!  Needles to say it wern't a pretty sight ... seems that the kernal headers from the previous kernal do not play nicely with the updated ones ... So be careful if you do a clean install ... When my head stops spinning I'll attempt an upgrade and see if that does any better!

Caio!!!

---

### Post by mdpalow on 2008-03-22
> **Tews said:**
> I was in an adventurous mood so I thought I'd give the latest LTS build of Hardy Herron a go ... Burnt a new ISO, booted and installed without a hitch ... Not really paying attention I installed QS and proceeded to do a restore .. whooo boy!  Needles to say it wern't a pretty sight ... seems that the kernal headers from the previous kernal do not play nicely with the updated ones ... So be careful if you do a clean install ... When my head stops spinning I'll attempt an upgrade and see if that does any better!

Caio!!!

I would think it was more than just the kernal that wasn't playing nicely. :) I think we'll only be able to restore the '/home' archive at the very most and hope for the best there.

I think it might be best we put a few questions out to some people who are "in the know" and find out how restoring the files from our /home directory is/would effect the new 8.04 version. If they changed folder/file names, we could be in for some trouble.

Now when I say trouble, I just mean that our current back-ups might just not be useable any more. However, we can still easily take out all our pics, docs, music, work, etc., etc. and put them in the 8.04 version AND then make a new back-up. I just hate the idea of having to reconfigure everything the way I like it before I can back-up again.

Now there is ONE idea I had for a smooth transition. Here's what I'm thinking I'm going to try/do.

1. Wipe my computer clean.
2. Install 7.10
3. Install QuickStart
4. Restore my back-up files
5. Install new updates since my back-up was made
6. Make a new back-up and store in safe place
7. Perform an UPGRADE to 8.04
8. Make a new back-up for 8.04 if the upgrade went well. :)

I'm hoping that will work out nicely. As long as the upgrade function is good/clean, it should work for us.

...

---

### Post by Bruce M. on 2008-03-22
Hey, that's very close to what I said I was going to do.

Thread: [Your plans for the Hardy Heron??]("http://ubuntuforums.org/showpost.php?p=4553653&postcount=27") :lolflag:

Bruce

EDIT: Curious, how often do you backup?

I do one every night while we are eating and watching a movie.  :)

---

### Post by mdpalow on 2008-03-22
> **Bruce M. said:**
> Hey, that's very close to what I said I was going to do.

Thread: [Your plans for the Hardy Heron??]("http://ubuntuforums.org/showpost.php?p=4553653&postcount=27") :lolflag:

Bruce

EDIT: Curious, how often do you backup?

I do one every night while we are eating and watching a movie.  :)

I think there's a posting I made some time ago that is the same as this. I'm probably just repeating myself at this point. :)

I haven't made a back-up (in the strictest sense) in quite a while actually. I do however have an hourly sync going on.

The only thing I back-up is QuickStart whenever I make changes to it. I've got that thing backed up so many places it's ridiculous.

...

---

### Post by Bruce M. on 2008-03-22
> **mdpalow said:**
> I think there's a posting I made some time ago that is the same as this. I'm probably just repeating myself at this point. :)

I haven't made a back-up (in the strictest sense) in quite a while actually. I do however have an hourly sync going on.

The only thing I back-up is QuickStart whenever I make changes to it. I've got that thing backed up so many places it's ridiculous.

...

You make one of the best little backup/Restore programs going and you don't backup?

WELL I NEVER!   :lolflag:

Hourly sync?  Why hourly?

I know Sync seems to fly by, and I tested it a few times to see.  Deleting the files and redoing it a few time.  My head was saying;

> No, this is impossible, I'm syncing some pretty heavy folders to a second drive and it's doing it in a minute.

but they just keep showing up there.

Correct me if I'm wrong here but if I have:

/folder/blue.tgz
/folder/yellow.txt
/folder/green.doc
/folder/purple.xml
/folder/red.html

and they are being "sync'ed" and I delete:

/folder/green.doc

in: media/sdb1/backup/sync/

/folder/green.doc

will stay there, getting larger as time goes on and I delete files but they remain in:

in: media/sdb1/backup/sync/

Am I right?
Bruce

Time to eat amd watch a movie with my wife.  Later  :)

---

### Post by mdpalow on 2008-03-22
I don't like to sync more than hourly because I don't want my back-up overwritten so fast in-case I find a problem with the work I've done in the past hour and want to revert back to the beginning. 

Not sure I understand your question, but here goes.

The sync ONLY copies the file to a sync folder IF the file has changed in some way. If nothing has changed then nothing happens. If you have 10 folders and only change one small text file then THAT'S ALL that gets written during that sync period.

Since this is only a sync job, nothing gets deleted from your sync folder if you delete a file in the original folder. Just 'cause you delete /folder/green.doc from original folder doesn't mean that green.doc in the sync folder is deleted. No - it stays there. Safety first...

...

---

### Post by Tews on 2008-03-23
> **mdpalow said:**
> 
Now there is ONE idea I had for a smooth transition. Here's what I'm thinking I'm going to try/do.

1. Wipe my computer clean.
2. Install 7.10
3. Install QuickStart
4. Restore my back-up files
5. Install new updates since my back-up was made
6. Make a new back-up and store in safe place
7. Perform an UPGRADE to 8.04
8. Make a new back-up for 8.04 if the upgrade went well. :)

I'm hoping that will work out nicely. As long as the upgrade function is good/clean, it should work for us.

...
 
I went ahead and did the upgrade .. took a bit more than an hour which wasn't tooooo bad.  Everything seemed ok after restoring the home folder ... everything except my wlan!  It was MIA.  Its ok running the live CD but for some strange reason the upgrade hoses it ... **BUT** Quick Start performed flawlessly!!  :lolflag:  Guess Ill wait for a bit before jumping into HH ..

caio!

---

### Post by fourthofjuly on 2008-03-23
sir,

please if you could read my suggestion above? you might have missed it....

thanks & regards,

devang.

---

### Post by Bruce M. on 2008-03-23
> **mdpalow said:**
> Since this is only a sync job, nothing gets deleted from your sync folder if you delete a file in the original folder. Just 'cause you delete /folder/green.doc from original folder doesn't mean that green.doc in the sync folder is deleted. No - it stays there. Safety first...
...

This is what I was getting at, you said it in a lot less words. :)
Sometime I can be so complicated.  :)

SO: "historical archive" - I like that.

> **mdpalow said:**
> Safety first...

Yes, I forgot: Your Motto!

Bruce

---

### Post by Bruce M. on 2008-03-23
> **fourthofjuly said:**
> Sir, maybe your utility could be included in upcoming Ubuntu distros if you would like to?

> **fourthofjuly said:**
> please if you could read my suggestion above? you might have missed it....

Poor mdpalow.  He is very busy ironing out little "un-known features" in QuickStart.

So if I may be so bold as to offer an answer. ( Sorry if I'm stepping on toes here mdpalow )

mdpalow has been asked this question before and if I recall correctly he feels it's just not ready yet. He's still working on it.

Personally I feel it's ready and I'd like to see it not only in the Repos, but on all of the install CD's.

However there seems to be an issue with HH that needs to be fixed, so maybe it's not ready for the Install CD's but definitely for the Repos as a choice to be downloaded in the Utilities section.

Having said that I have to respect mdpalow's decision.  He has his reasons and like he says: Safety First.  

Have a great day.
Bruce

---

### Post by gladstone on 2008-03-23
> **mdpalow said:**
> Bruce contacted me and asked if I could make option 6 (view/edit config files) use either 'gedit' or 'kate' depending on what OS you were using. Didn't seem like a difficult request, so why not.

Now QuickStart will open your config files regardless of which editor (gedit/kate) you're using. 

Could you please account for us Xubuntu users and allow 'mousepad' to that?

Regarding installation/updates; I'd prefer that QuickStart was not installed to my home folder. Can I move it to someplace else without it breaking it and the update/uninstall feature? Why is QuickStart being installed there in the first place instead of say /usr?

Also, everytime I start, QS asks to install "exim4". What does this do? When I run QS from terminal, I get this: ```
line 39: gnome-terminal: command not found

``` (I am running XFCE4).

Nevertheless, thanks for this useful tool!

---

### Post by fourthofjuly on 2008-03-23
> **Bruce M. said:**
> Poor mdpalow.  He is very busy ironing out little "un-known features" in QuickStart.

So if I may be so bold as to offer an answer. ( Sorry if I'm stepping on toes here mdpalow )

mdpalow has been asked this question before and if I recall correctly he feels it's just not ready yet. He's still working on it.

Personally I feel it's ready and I'd like to see it not only in the Repos, but on all of the install CD's.

However there seems to be an issue with HH that needs to be fixed, so maybe it's not ready for the Install CD's but definitely for the Repos as a choice to be downloaded in the Utilities section.

Having said that I have to respect mdpalow's decision.  He has his reasons and like he says: Safety First.  

Have a great day.
Bruce
i would request mdpalow to pass it on to the repos surely to make it more popular... more users exploring the tool and giving their feedback... if there are any issues they can be reported back by the community...

i think the utility can mature very fast that way...!!!

do correct me if i am wrong...

thanks & regards,

devang.

---

### Post by Bruce M. on 2008-03-23
> **fourthofjuly said:**
> i would request mdpalow to pass it on to the repos surely to make it more popular... more users exploring the tool and giving their feedback... if there are any issues they can be reported back by the community...

i think the utility can mature very fast that way...!!!

do correct me if i am wrong...

thanks & regards,

devang.

Again I don't want to step on any toes, especially yours mdpalow.

I understand what you are saying and in part agree.
The other part of me has to agree with mdpalow.

Iron out the "undocumented features" and have it working for all distros of Ubuntu; Xfce, Gnome, KDE, and Edbuntu

It's very close to that now I might add.  :)

Bruce

---

### Post by Bruce M. on 2008-03-23
> **gladstone said:**
> Could you please account for us Xubuntu users and allow 'mousepad' to that?

Regarding installation/updates; I'd prefer that QuickStart was not installed to my home folder. Can I move it to someplace else without it breaking it and the update/uninstall feature? Why is QuickStart being installed there in the first place instead of say /usr?

Also, everytime I start, QS asks to install "exim4". What does this do? When I run QS from terminal, I get this: ```
line 39: gnome-terminal: command not found

``` (I am running XFCE4).

Nevertheless, thanks for this useful tool!

Hi Gladstone,

I'm sure mousepad will be coming shortly.  :)

As to exim4 it is required for the backing up your /home folder.
Did you allow QS to install it?

Personally I like the fact QS is in the /home folder, it allows it to be a part of the "Synchronize Selected Folders" options.

Also when/if you do a re-install of / (root) keeping your /home folder as is, QS is available  for use.

The best option here is:

1. Re-install / - DO NOT get updates yet!
2. Run QS and restore "System" and "Config"
3. Allow Ubuntu to get updates *if necessary*

Hope this helps.
Have a Great Day
Bruce

---

### Post by mdpalow on 2008-03-23
To be more precise... the exim4 files are what make it possible for the Scheduled Back-ups to work.

I would like to remind everyone that QuickStart is a utility I built for UBUNTU. There are enough differences in the other Operating Systems that lead me to believe QuickStart won't work 100%.

I remember some time back a Kubuntu user having a problem with something. You could probably find it in the thread where I installed Kubuntu on my laptop to run some tests and reported back that parts of QuickStart did work while others didn't..

'Mousepad,' huh? :) Hear that Bruce? What a coincidence. lol

Yes, I'll look into that again I'm sure very soon.

I think before QuickStart is ever to become a part of the default OS, it probably could still use some work. I mean it was just a few days ago that we finally realized we needed the exim4 files to make the SB work properly. I don't think there's any rush and with people telling each other about it via the forums, QuickStart will get it's share of people trying it out. I'd say there have been close to 2,000 downloads of QS. If even 25% continue to use it and tell others about it, QuickStart will be on enough computers that having it a part of the install won't make it better.

Thanks to all of you that feel this way...

---

### Post by Bruce M. on 2008-03-23
> **mdpalow said:**
> To be more precise... the exim4 files are what make it possible for the Scheduled Back-ups to work.

I would like to remind everyone that QuickStart is a utility I built for UBUNTU. There are enough differences in the other Operating Systems that lead me to believe QuickStart won't work 100%.

I remember some time back a Kubuntu user having a problem with something. You could probably find it in the thread where I installed Kubuntu on my laptop to run some tests and reported back that parts of QuickStart did work while others didn't.

I'm happy to report that QS works 100% with Xubuntu. Well, except for mousepad, but I have Kate installed anyway.  :)

> **mdpalow said:**
> 'Mousepad,' huh? :) Hear that Bruce? What a coincidence. lol

Yes, I'll look into that again I'm sure very soon.

Honest, I had absolutely nothing to do with that.
But is did do, ***Opps! chuckle chuckle***, when I saw it.  :)

> **mdpalow said:**
> I think before QuickStart is ever to become a part of the default OS, it probably could still use some work. I mean it was just a few days ago that we finally realized we needed the exim4 files to make the SB work properly. I don't think there's any rush and with people telling each other about it via the forums, QuickStart will get it's share of people trying it out. I'd say there have been close to 2,000 downloads of QS. If even 25% continue to use it and tell others about it, QuickStart will be on enough computers that having it a part of the install won't make it better.

Thanks to all of you that feel this way...

Hey, I think I can say for most of us here that use QS, we love it and appreciate your work you've put into it.  And it's being demonstrated by those "It should be a part of Ubuntu" comments as well.  Again I'll say, I respect you for your reasons not to do that yet. I hope you do consider it for the future though.

And as I said before to you, I'll say here in the forums, I'll beta test QS with Xubuntu for you any time you want.  And I have a habit of NOT testing or running betas.  So that goes to show the faith I have in you and in QS.

Have a great day.
Bruce

---

### Post by mdpalow on 2008-03-23
> **gladstone said:**
> Could you please account for us Xubuntu users and allow 'mousepad' to that?

Regarding installation/updates; I'd prefer that QuickStart was not installed to my home folder. Can I move it to someplace else without it breaking it and the update/uninstall feature? Why is QuickStart being installed there in the first place instead of say /usr?

Also, everytime I start, QS asks to install "exim4". What does this do? When I run QS from terminal, I get this: ```
line 39: gnome-terminal: command not found

``` (I am running XFCE4).

Nevertheless, thanks for this useful tool!

Ok, I just 'accounted' for "Mousepad" in QuickStart. Will upload it shortly.

"exim4" are files required to run the Scheduled Back-up option. It's only three files; let them install.

What is the terminal command to bring up another terminal in Xubuntu? I can probably fix that pretty easy, so you don't get that anymore....

Will wait to hear back...

---

### Post by Bruce M. on 2008-03-23
> **mdpalow said:**
> Ok, I just 'accounted' for "Mousepad" in QuickStart. Will upload it shortly.

"exim4" are files required to run the Scheduled Back-up option. It's only three files; let them install.

What is the terminal command to bring up another terminal in Xubuntu? I can probably fix that pretty easy, so you don't get that anymore....

Will wait to hear back...

xterm

But I didn't say that  :)
Bruce

EDIT: Gnome terminal calling xterm ( attached )

---

### Post by mdpalow on 2008-03-23
> **gladstone said:**
> Regarding installation/updates; I'd prefer that QuickStart was not installed to my home folder. Can I move it to someplace else without it breaking it and the update/uninstall feature? Why is QuickStart being installed there in the first place instead of say /usr?

hmmm. I think probably because when I was originally programming QuickStart, I had all my related files in a folder I created in the /home directory.

I think that even if I had QuickStart sitting in /usr, I would have to create a QuickStart folder for the additional files that came with it a while back. Now, only one file accompanies QuickStart, but it has to go somewhere and since the folder already exists, why not keep it all together?

What is your reasoning for not wanting it where it currently sits?

Also, to answer your question - no it wouldn't work to move it. Sorry.

---

### Post by mdpalow on 2008-03-23
> **Bruce M. said:**
> xterm

But I didn't say that  :)
Bruce

Thanks Bruce... you gonna be online for a short while? If so, e-mail me and I'll make some quick modifications and maybe you can beta it for me real quick.

Thanks...

---

### Post by Bruce M. on 2008-03-23
@ mdpalow,

Before someone askes

Kubuntu uses konsole for a terminal  :)

From Synaptic:

> X terminal emulator for KDE 
Konsole is an X terminal emulation which provides a command-line interface
(CLI) while using the graphical K Desktop Environment. Konsole helps to
better organize user's desktop by containing multiple sessions in a single
window (a less cluttered desktop).

Its advanced features include a simple configuration and the ability to use
multiple terminal shells in a single window

Using Konsole, a user can open:

 Linux console sessions
 Midnight Commander file manager sessions
 Shell sessions
 Root consoles sessions

This package is part of KDE, and a component of the KDE base module.
See the 'kde' and 'kdebase' packages for more information.


Bruce

---

### Post by Bruce M. on 2008-03-23
Hi Folks,

I use QuickStart to make backups every night.

As you can imagine this collects 3 files every day.
Since I only want to keep a weeks worth of backups I went looking for a script to delete any file older than 7 for each of the files.

If you are interested it can be found here:  [[SOLVED] Need a script - Any writers available? ]("http://ubuntuforums.org/showthread.php?t=732286")

I'm going to pop that sucker into a startup file and it will do it for me automatically.

Enjoy it if you want

Have a Great day
Bruce

---

### Post by gladstone on 2008-03-23
> **Bruce M. said:**
> xterm

But I didn't say that  :)
Bruce

EDIT: Gnome terminal calling xterm ( attached )

Or preferably```
xfce4-terminal
```

> **mdpalow said:**
> hmmm. I think probably because when I was originally programming QuickStart, I had all my related files in a folder I created in the /home directory.

I think that even if I had QuickStart sitting in /usr, I would have to create a QuickStart folder for the additional files that came with it a while back. Now, only one file accompanies QuickStart, but it has to go somewhere and since the folder already exists, why not keep it all together?

What is your reasoning for not wanting it where it currently sits?

Also, to answer your question - no it wouldn't work to move it. Sorry.

I want to keep my /home folder for personal files only and not have any intruding applications sitting in there. I could put up with it being hidden though with a "." 

I'm not sure what you mean with the "additional files", though I did notice it installed a readme and the .desktop file into /home/QuickStart. Since the .desktop file was already in /usr/share/applications, I safely deleted it from the /home directory and QuickStart still showed in my Applications "Start" menu.

Is this another slight difference with gnome and xfce which needs to be changed?

> **Bruce M. said:**
> Hi Gladstone,

I'm sure mousepad will be coming shortly.  :)

As to exim4 it is required for the backing up your /home folder.
Did you allow QS to install it?

Personally I like the fact QS is in the /home folder, it allows it to be a part of the "Synchronize Selected Folders" options.

Also when/if you do a re-install of / (root) keeping your /home folder as is, QS is available  for use.

The best option here is:

1. Re-install / - DO NOT get updates yet!
2. Run QS and restore "System" and "Config"
3. Allow Ubuntu to get updates *if necessary*

Hope this helps.
Have a Great Day
Bruce

I think I understand what your saying there and agree it would be useful. But if I ever needed to reinstall "/" (my /home is on a seperate partition anyway atm) and wanted to use QS to reinstall my system config files, then surely I could easily just reinstall QS first?

Btw, your script sounds interesting, I'm gonna have a look at it, thanks.

---

### Post by Bruce M. on 2008-03-23
> **gladstone said:**
> Or preferably```
xfce4-terminal
```

When I try to use that it's the same as [Ctrl]+[Alt]+[Backspace] - every time.  :(

xterm has always worked for me.  :)

> **gladstone said:**
> I think I understand what your saying there and agree it would be useful. But if I ever needed to reinstall "/" (my /home is on a seperate partition anyway atm) and wanted to use QS to reinstall my system config files, then surely I could easily just reinstall QS first?

Btw, your script sounds interesting, I'm gonna have a look at it, thanks.

I have my /home on a separate partition as well.  I allow Ubuntu to use it any way it wants.

All my personal files, images, documents, PDF's, etc etc are on my second drive. Nothing personal is saved on the "Ubuntu" HD at all.

Well, except for Firefox bookmarks and e-mail in Thunderbird, only because I don't know how to get those programs to use the other HD for those files (yet!).

Are you talking about the script to delete the backups older than 7 days?
It is nice isn't it.

Bruce

---

### Post by gladstone on 2008-03-23
Hmm, not sure why xfce4-terminal is acting like that. What happens if you start it from XFCE menu: Applictions\Accessories\Terminal?

Since you keep all your personal files on a separate drive completely, it sounds like you would understand why I want to keep my /home dir for personal files only. If I had another drive available for use, I would do that!

And yeah your "delete the backups older than 7 days" script, it is nice indeed. Perhaps we could have something like that implemented in QuickShare natively?

---

### Post by Bruce M. on 2008-03-23
> **gladstone said:**
> Hmm, not sure why xfce4-terminal is acting like that. What happens if you start it from XFCE menu: Applictions\Accessories\Terminal?

That's where I try it from and it does a [Ctrl]+[Alt]+[Backspace] every time.
If it works on your system great, I'll have to creat a thread and ask why it's not working here.

However xterm is on your system (it installs with Xubuntu) and is well suited for QS's needs as it only opens to show you the files as they are being processed.  You can even close it while the backups are going on, it has no adverse affect.

> **gladstone said:**
> Since you keep all your personal files on a separate drive completely, it sounds like you would understand why I want to keep my /home dir for personal files only. If I had another drive available for use, I would do that!

Oh, I understand you.  But Ubuntu puts a lot of stuff there as well, hidden configuration files, etc etc. So in part some of the stuff there is not really yours, but Ubuntu's to use. :)

> **gladstone said:**
> And yeah your "delete the backups older than 7 days" script, it is nice indeed. Perhaps we could have something like that implemented in QuickShare natively?

Oh I wouldn't think to impose that on mdpalow.

Besides, this way it is customizable by each individual to suit their own needs and system.  It doesn't even have to be run daily.  Because the way it is created if you run 10 days after doing daily backups, it will delete three days of the oldest backups (the +6, because 0=day1, 1=day 2, etc).

Bruce

---

### Post by gladstone on 2008-03-23
> **Bruce M. said:**
> That's where I try it from and it does a [Ctrl]+[Alt]+[Backspace] every time.
If it works on your system great, I'll have to creat a thread and ask why it's not working here.

However xterm is on your system (it installs with Xubuntu) and is well suited for QS's needs as it only opens to show you the files as they are being processed.  You can even close it while the backups are going on, it has no adverse affect.

It looks as though it is a known bug, check here:

[http://ubuntuforums.org/showthread.php?t=620168](http://ubuntuforums.org/showthread.php?t=620168)

I'm trying to find out what the **actual** default Terminal is in Xubuntu. I believe it might actually be [x-terminal-emulator]("http://ubuntuforums.org/showpost.php?p=3818211&postcount=5") rather than xfce4-terminal. Or they might be both the same :confused:

In Applications/Settings/Preffered Applications it says "[XFCE Terminal]("http://ubuntuforums.org/showpost.php?p=3819146&postcount=18")"

> **Bruce M. said:**
> 
Oh, I understand you.  But Ubuntu puts a lot of stuff there as well, hidden configuration files, etc etc. So in part some of the stuff there is not really yours, but Ubuntu's to use. :)

True, but I do like my config files all stored in one place (alot more organised than Windows ever was for me). As for them being in /home I can put up with it since, as you rightfully say, they are hidden. Perhaps atleast QS can do that?

> **Bruce M. said:**
> 
Oh I wouldn't think to impose that on mdpalow.

Besides, this way it is customizable by each individual to suit their own needs and system.  It doesn't even have to be run daily.  Because the way it is created if you run 10 days after doing daily backups, it will delete three days of the oldest backups (the +6, because 0=day1, 1=day 2, etc).

Bruce

Just gotta get my head around it all! It's very useful nevertheless :) Might be handy in QS

---

### Post by Bruce M. on 2008-03-24
> **gladstone said:**
> It looks as though it is a known bug, check here:

[http://ubuntuforums.org/showthread.php?t=620168](http://ubuntuforums.org/showthread.php?t=620168)

Whoa!  Great stuff!  See this: [Re: [SOLVED] xfce4-terminal causes log-out]("http://ubuntuforums.org/showthread.php?p=4576734#post4576734")

Thanks to you I now have xfce4-terminal up and running. And it is so close to gnome-terminal that I can deep6 GT.  :)

**[SIZE="4"][CENTER]THANK YOU![/CENTER][/SIZE]**

> **gladstone said:**
> I'm trying to find out what the **actual** default Terminal is in Xubuntu. I believe it might actually be [x-terminal-emulator]("http://ubuntuforums.org/showpost.php?p=3818211&postcount=5") rather than xfce4-terminal. Or they might be both the same :confused:

I can clear that up for you.  x-terminal-emulator is in fact xfce4-terminal.

Do a test for yourself:

[Alt]+[F2] - x-terminal-emulator - leave it open and;
[Alt]+[F2] - xfce4-terminal - you'll see that they are the same program  :)


> **gladstone said:**
> In Applications/Settings/Preffered Applications it says "[XFCE Terminal]("http://ubuntuforums.org/showpost.php?p=3819146&postcount=18")"

Yup, mine too now. 

> **gladstone said:**
> True, but I do like my config files all stored in one place (alot more organised than Windows ever was for me). As for them being in /home I can put up with it since, as you rightfully say, they are hidden. Perhaps atleast QS can do that?

But now you are asking everyone that is using QS to change to meet your needs/desires.

I have to admire mdpalow for creating "uBackup" for his own use, and when it worked he put it here for others to use.  It was setup that way on his system, it worked, he started fixing "bugs" (undocumented features, as I like to call them) and it has grown to what it is today: QuickStart with only three files in the **/home** folder. Asking that it be moved or changed for "cosmetic" reasons my just may unleash a whole new set of "un-documented features" 

Somehow mdpalow's setup makes sense to me, if your **[SIZE="4"]/[/SIZE]** folder get corrupted you can re-install a clean **[SIZE="4"]/[/SIZE]** and QS is still there to restore, before doing the on-line updates step, *_and_* maybe eliminating that step all together.

Imagine restoring your system without having to go on-line at all.  PRICELESS!
Possible because QS is NOT in /usr/bin.

As for hiding QS, I'm afraid I have to disagree with you there. It amounts to unnecessary changes to code for "cosmetic reasons" (see above), after all it would still exist in your /home folder.

I'd prefer to putting our minds together to help mdpalow iron out the finer details of getting it up and running at as close as 100% as possible.
 
> **gladstone said:**
> Just gotta get my head around it all! It's very useful nevertheless :) Might be handy in QS

Well, my **dod.sh** doesn't work. It exists, it is executable ... it must have an un-documentented feature some place.  :)
```

#!/bin/bash
find /media/sdb1/Back-ups/Schedule -mtime +6 -type f -delete

```
but...
```

-(~)----------------------------------------------------------(12:28 Mon Mar 24)
bruloo@bruloo [164] --> dod.sh
zsh: command not found: dod.sh

```
However putting that line into terminal:
```

find /media/sdb1/Back-ups/Schedule -mtime +6 -type f -delete

```
works just fine.  :)

Have a great day
Bruce

---

### Post by mdpalow on 2008-03-24
[COLOR="Red"][SIZE="3"]**UPDATE AVAILABLE**[/SIZE][/COLOR]


Hi Everyone,

Made some additions/changes to QS to better server more people. Hope they are well received.

1. Added both KATE and MOUSEPAD to Option 6 for viewing and editing config files.

   The order of precedence is: GEDIT - don't have -> go to KATE - don't have go to MOUSEPAD.

2. Added KONSOLE and xfce4-terminal TERMINAL windows. This should help display properly for people using Kubuntu or Xubuntu during back-up/restore.

    From what I'm seeing in these posts,  "xfce4-terminal" is a correct file name, yes? 

3. Made a procedural change to CREATE A BACK-UP. Had another incident where user didn't press CANCEL during /home folder exclusion and they ended up excluding everything and therefore had an empty home_backup. Now, QS will ask you if you want to exclude any folders. If you say yes, you're taken to the exclude window. If you say No, it goes directly into backing up.

My thinking was if you said Yes, you would probably be more likely to use the exclusion window correctly.

4. Changed length of timeout windows by making them a little shorter, so we don't have to wait as long to be returned back to main menus.

Update is loaded to server.....

---

### Post by mdpalow on 2008-03-24
> **gladstone said:**
>  True, but I do like my config files all stored in one place (alot more organised than Windows ever was for me). As for them being in /home I can put up with it since, as you rightfully say, they are hidden. Perhaps atleast QS can do that?


With a little thought behind this... I do see where you're coming from. You, and probably others, see QuickStart as an application and therefore don't care to see it in your /home folder along with your Documents, Pictures, etc., etc..

I see/look at QuickStart as a project/work and therefore it makes perfect sense for me to have a QuickStart folder in my /home.

I think this might just warrant some looking into. I mainly have to see how much of a change it means in the code. Pretty sure it won't be too hard as I did use a variable to returning to main menu.

I will look into how QS is being installed now-a-days since some things have changed from when it first came out. I'll look into either putting it in /usr/bin or making the QuickStart folder hidden by default.

---

### Post by mdpalow on 2008-03-24
**[COLOR="Red"][SIZE="2"]check out the POLL question at the top of the page[/SIZE][/COLOR]**

---

### Post by Bruce M. on 2008-03-24
> **mdpalow said:**
> **[COLOR="Red"][SIZE="2"]check out the POLL question at the top of the page[/SIZE][/COLOR]**

24 Mar 2008 @ 15:29 local, my vote is registered.  :)

---

### Post by Bruce M. on 2008-03-24
> **mdpalow said:**
> [COLOR="Red"][SIZE="3"]**UPDATE AVAILABLE**[/SIZE][/COLOR]
    From what I'm seeing in these posts,  "xfce4-terminal" is a correct file name, yes? 


Yes it is.
Bruce

---

### Post by money2themax on 2008-03-24
> **mdpalow said:**
> [COLOR=Red][SIZE=3]**UPDATE AVAILABLE**[/SIZE][/COLOR]


Hi Everyone,

Made some additions/changes to QS to better server more people. Hope they are well received.

1. Added both KATE and MOUSEPAD to Option 6 for viewing and editing config files.

   The order of precedence is: GEDIT - don't have -> go to KATE - don't have go to MOUSEPAD.

2. Added KONSOLE and xfce4-terminal TERMINAL windows. This should help display properly for people using Kubuntu or Xubuntu during back-up/restore.

    From what I'm seeing in these posts,  "xfce4-terminal" is a correct file name, yes? 

3. Made a procedural change to CREATE A BACK-UP. Had another incident where user didn't press CANCEL during /home folder exclusion and they ended up excluding everything and therefore had an empty home_backup. Now, QS will ask you if you want to exclude any folders. If you say yes, you're taken to the exclude window. If you say No, it goes directly into backing up.

My thinking was if you said Yes, you would probably be more likely to use the exclusion window correctly.

4. Changed length of timeout windows by making them a little shorter, so we don't have to wait as long to be returned back to main menus.

Update is loaded to server.....

what company is hosting your server? If you don't mind me asking.

---

### Post by MeTylerDurden on 2008-03-25
I just installed Ubuntu 7.10 yesterday and have been tweaking ever since..  have had issue with flash player.. anyway  i bookmarked your page  and will probly try this soon   just dropping a line to ask how much positive vs neg input you got from your gem..   and does it deal with the flash issue

---

### Post by blue_bullet on 2008-03-25
Great utility.  I have been using it for several weeks and have enjoyed seeing all the enhancements.  Now that you have opened up the editors in Option 6 how about keying off  the environment variable EDITOR first? If it exists, use its value for the path/executable name for editing.  I use "the" (The Hessling Editor) and "xthe" (X11 version of the same) for editting.  I have the path to the executable "the" defined in EDITOR in .bashrc.   Others may have their own favorite specified in EDITOR.  What do you think?  Pretty picky, eh? 

rob@fargo:~$ echo $EDITOR
/usr/bin/the

Anyway you have done a super job of enhancing QuickStart and being responsive to user requests.

---

### Post by mdpalow on 2008-03-25
> **MeTylerDurden said:**
> I just installed Ubuntu 7.10 yesterday and have been tweaking ever since..  have had issue with flash player.. anyway  i bookmarked your page  and will probly try this soon   just dropping a line to ask how much positive vs neg input you got from your gem..   and does it deal with the flash issue

I'd say there's about 80 pages of input you can reference to see what you think. :) If you want an actual figure - I don't know... 95% positive and 5% negative ??? I mean it hasn't blown anyone's computer up or destroyed it if that's a concern. :)

The Flash function has been taken out of QuickStart since it's been fixed now in Ubuntu. What issue are you talking about? Is there a new issue with Flash now?

Please let me know...

Thanks

---

### Post by mdpalow on 2008-03-25
> **blue_bullet said:**
> Great utility.  I have been using it for several weeks and have enjoyed seeing all the enhancements.  Now that you have opened up the editors in Option 6 how about keying off  the environment variable EDITOR first? If it exists, use its value for the path/executable name for editing.  I use "the" (The Hessling Editor) and "xthe" (X11 version of the same) for editting.  I have the path to the executable "the" defined in EDITOR in .bashrc.   Others may have their own favorite specified in EDITOR.  What do you think?  Pretty picky, eh? 

rob@fargo:~$ echo $EDITOR
/usr/bin/the

Anyway you have done a super job of enhancing QuickStart and being responsive to user requests.

Maybe it's late, or I'm tired, or maybe I've even had one too many drinks, but I'm sorry to say that I don't understand what the h... you're talking about. LOL :)  Just playing...

I'll read this again tomorrow and maybe it'll make more sense. Can you, in the meantime, break it down to like... say 8th grade speak?

Thanks. ;)

---

### Post by money2themax on 2008-03-25
> **mdpalow said:**
> Maybe it's late, or I'm tired, or maybe I've even had one too many drinks, but I'm sorry to say that I don't understand what the h... you're talking about. LOL :)  Just playing...

I'll read this again tomorrow and maybe it'll make more sense. Can you, in the meantime, break it down to like... say 8th grade speak?

Thanks. ;)
your a Linux user so you should be ashamed of what  you just said jklol

---

### Post by newbieforever on 2008-03-25
sorry, i think this my second post on this thread: there are over 7 hundreds posts, and it is very difficult to me to understand why; :confused:

**could anyone kindly summarize the problem about this software?** why almost 800 posts? where is the problem? it is a backup utility, aint it?

but why all these complications? why not a complete affordable simple to use [mondo]("http://www.mondorescue.org/") to have an image of the entire system on a 3 partition disk (root, home, swap)?
this image is not a solid rock, you can always extract single parts, if you really need, but this would have to be the exception, if you a regular backup policy;

as i already said you simply can a bootable dvd set with [mondo]("http://www.mondorescue.org") in the time of a lunch, or a walk in the sun, o in the snow, or in the falling leaves, on in the spring blossoms, and forget it your backup problems...
do your system crash? you can have it resurrected in the time of a good tea!

or you simply can save the marked installed packages in synaptic (plus backupping the local installed packages) and have a really no-bogging clean new installation leaving all your configurations in "home" without touching it;

you even could transfer your image on a disk with a completely different geometry; 

(mondo is actually quite sophisticated and customizable, but you could use at the level you prefer)

the rest is obvious: you should make a rapid copy of the home partition, after having cleaned (backupped and stored) it from the _stable_ big data (documents, projects, pictures, music, videos, and other stuff _you have closed once for all_)

i really do as i just said in this post, and i safe and relaxed...so: **what am i not understanding or mistaking? :confused:**

thanks for your help and patience,

(please notice that all this is absolutely not polemics, just the fact that i cant afford over 700 posts, and a **summary of the problem** could help the newcoming subscribers to this very active thread)

nbfe

---

### Post by Tews on 2008-03-25
There **_isn't**_ a problem with Quick-Start!  It is a _**work in progress.**_  What started out as one mans idea for a simple and efficient manner of backing up and restoring data and applications turned into one of the best applications the Ubuntu community has seen in years. Naturally when the author (mdpalow) released it for everyones' used it generated a tremendous response as seen by the number of posts/views that this thread has generated.  I think what you are seeing is what the FOSS/Linux movement had in mind when they developed their philosophy of "Free and Open" software. A community coming together around an idea and supporting its development and distribution to the Linux community.

There's no need to go into which method (Mondo vs Quick-Start) is better ( I've covered that in a previous post ) however to equate the quality of a program to the number of posts is simply silly.

Tews

**Quick-Start ... Learn it ... Live it ... Love it!**  :lolflag:

---

### Post by newbieforever on 2008-03-25
> **Tews said:**
> There **_isn't_** a problem with Quick-Start!  It is a _**work in progress.**_ (...)
(...)efficient manner of backing up and restoring data and applications turned into one of the best applications the Ubuntu community has seen in years. (...)
(...)tremendous response as seen by the number of posts/views that this thread has generated(...)
(...)There's no need to go into which method (Mondo vs Quick-Start) is better ( I've covered that in a previous post )
(...)however to equate the quality of a program to the number of posts is simply silly.

Tews

**Quick-Start ... Learn it ... Live it ... Love it!**  :lolflag:

i will follow your advice, and i will choose the one is best suiting my needs

but i'm convinced that 11 pages of 75 posts each, about quickstart, to read are too much for everyone: 800 posts are so "quick" to start with quickstart?

i read 11 rows about mondo (small to medium enterprise solution), 
i try it in 11 nanoseconds 
i learn it in 11 seconds, 
i set it in 11 seconds,
i restore my system in 11 minutes

so dont you agree that a summary should be fair to novices? 
may be that 1 "how to" new thread thread with 11 points could rise the interest of the novices

i dont judge the quality of quickstart, 
i disagree that 800 post are a qualitative information resource

and i dont think that (1) sinthesis after (800) analysis is silly

thank you for your time, but i still need a summary to decide between mondo and quickstart

nbfe

---

### Post by Tews on 2008-03-25
I agree that 800 posts are a lot to read ... I know I didn't read them all ...  I didn't have to, I recognized that this was something I wanted to use after reading the first page. That being said, I also didn't expect to come here expecting to find endless comparisons of Quick-Start to other backup solutions.

As to which one is for you, the proof is in the pudding, as they say. If you want to see a thread doing a point by point comparison, then I suggest you start one. :)

---

### Post by newbieforever on 2008-03-25
> **Tews said:**
>  however to equate the quality of a program to the number of posts is simply silly.
Tews


> **mdpalow said:**
> Continue to use Mondo and please stop posting here.
Thank you.


very fair, i ask about such an incredible number of posts about a good backup program, where i obviously cant find what's the point

then...

first i am silly (according to Tews), 

then i am asked to go away (mdpalow) because i would like to know more about the program, and where to find some consistent information... 

i was only asking "maybe quickstart is better: how much time have i to spend to understand whether that is true for me?"

thank you, 

please report my posts if you think i am not fair

nbfe

---

### Post by mdpalow on 2008-03-25
You weren't called 'Silly' by Tews. What you're doing is silly is how I understand it to mean.

You weren't asked to 'go away,' you were asked to stop posting in this thread because your postings seem like nothing more than empty words that are only used to promote a program called 'Mondo,' which you apparently love.

See your first post on page 76 (post 757)
> 
isnt [http://www.mondorescue.org](http://www.mondorescue.org) better?
simply real power in your hand, in a 123 snap!
i really love mondo...
it is very easy to get, use, and restore: 2 minutes to install, 30 seconds to start the backup (or drive image), you go to launch, when you are back you really have your bootable backup dvd
not to say you can do selective back and/or restore

enjoy

nbfe 

I personally think if you REALLY were interested in QuickStart and how it compared against your program, you would simply have read at least a handful of posts AND tested it for yourself. I have to believe you've installed software to test it before. Why would this be any different?

It's great you've found a program you love. I/we get that from your post above. I encourage you to continue using it. :)

---

### Post by fourthofjuly on 2008-03-25
Sir,

can i clone my entire system with its installed themes, installed applications, network settings etc. to another system which has Ubuntu freshly installed?

if this has been answered earlier, point me to the link please?

thanks & regards,

devang.

---

### Post by Het Irv on 2008-03-25
Yes sir, you can.  Just do a full back-up, /, /home, and config files, and then restore them to the new computer.

---

### Post by mdpalow on 2008-03-25
> **fourthofjuly said:**
> Sir,

can i clone my entire system with its installed themes, installed applications, network settings etc. to another system which has Ubuntu freshly installed?

if this has been answered earlier, point me to the link please?

thanks & regards,

devang.

This has been asked once before that I can remember. I think, if I remember right, my answer was Yes, you could do it IF the hardware was the same. I've never done it, but it makes perfect sense that it would work. I know that Ubuntu will download and install files during an installation (at the end of install). It's what's being installed at this time that makes me not 100% positive.

Keep in mind though you probably wouldn't want to copy the config files over because then you would have to have the same video card, hard drive(s) configuration. I would leave the config back-up out completely if doing that.

You should give it a try and let us know...

Thanks

---

### Post by mdpalow on 2008-03-25
> **Het Irv said:**
> Yes sir, you can.  Just do a full back-up, /, /home, and config files, and then restore them to the new computer.

I wouldn't do the config files since they're already loaded/working fine. Might just be asking for problems in some circumstances.

That's good to know that it works though...

Thanks Het Irv

---

### Post by fourthofjuly on 2008-03-25
> **Het Irv said:**
> Yes sir, you can.  Just do a full back-up, /, /home, and config files, and then restore them to the new computer.
thanks, that's really great...

is it possible if the machines are of different configurations?

what if they run different flavours, like say Ubuntu Fiesty to Edubuntu Gutsy? this is not very important for me, but am just curious...

regards,

devang.

---

### Post by Het Irv on 2008-03-25
If that is true I would only do the /home.  the "/" is the accutual OS files, going over those would change the OS

Yeah, you may want to be careful about the configs, different hardware could be a problem if it is different manufacturer

---

### Post by fourthofjuly on 2008-03-25
> **mdpalow said:**
> This has been asked once before that I can remember. I think, if I remember right, my answer was Yes, you could do it IF the hardware was the same. I've never done it, but it makes perfect sense that it would work. I know that Ubuntu will download and install files during an installation (at the end of install). It's what's being installed at this time that makes me not 100% positive.

Keep in mind though you probably wouldn't want to copy the config files over because then you would have to have the same video card, hard drive(s) configuration. I would leave the config back-up out completely if doing that.

You should give it a try and let us know...

Thanks
how about installed apps? 

for example, in a 30-machine computer lab with Edubuntu, we could download apps on one system, create an archive and clone it to all the remaning 29?

---

### Post by mdpalow on 2008-03-25
I'll defer to you on that one Het Irv  :)

Surprisingly, the poll is, so far, in favor of leaving QuickStart right where it is during installation. That is.. /home/your_name/QuickStart

I've asked if people want to hide it (the QS folder) or even move the QS file itself to /usr/bin and remove the folder completely, but so far it's - leave it alone.

I must admit.. I'm surprised.

If you have a preference, pls weigh in 'cause I'll go by the popular vote. :)

---

### Post by fourthofjuly on 2008-03-25
ok, so restoring config files are only for the same machine

---

### Post by mdpalow on 2008-03-25
> **fourthofjuly said:**
> how about installed apps? 

for example, in a 30-machine computer lab with Edubuntu, we could download apps on one system, create an archive and clone it to all the remaning 29?

In a 30-machine lab, I would think there is a strong probability they were all purchased at the same time and have the same equipment. If so, then absolutely.

If they're not all the same, then I would not restore the config_backup_xxxx.tgz file as it might cause problems. For example, the config_backup file contains the xorg.conf file, which has information pertaining to your installed Video Card. You wouldn't want to overwrite your existing configuration files with your backed up files in case they weren't compatible.

I think you'll be fine and by the sounds of it... Het Irv has already done it and proved it does work.

---

### Post by Het Irv on 2008-03-25
If all of the computers in the Lab have the same hardware, and you want to have the setup from one computer used in all of them, then I would use all 3 backup files.  If the Hardware is different, but you still want the same OS version and programs, I would do everything but the config files.

Edit: Sorry for the delay, Firefox froze on me. Can't wait for 8.04 and FF3

---

### Post by fourthofjuly on 2008-03-25
> **mdpalow said:**
> In a 30-machine lab, I would think there is a strong probability they were all purchased at the same time and have the same equipment. If so, then absolutely.

If they're not all the same, then I would not restore the config_backup_xxxx.tgz file as it might cause problems. For example, the config_backup file contains the xorg.conf file, which has information pertaining to your installed Video Card. You wouldn't want to overwrite your existing configuration files with your backed up files in case they weren't compatible.

I think you'll be fine and by the sounds of it... Het Irv has already done it and proved it does work.
i was suggesting cloning of only installed applications e.g. educational games

only a single system can have wwweb access... which can download and rest 29 can simply copy them... maybe we can even do without thin clients then, i guess? we are planning to reuse our old Celeron machines for the kids lab... the major problem was installing applications on each system since all would not have internet access...

perhaps cloning config files on different configuration of machines will be risky and can best be avoided...

---

### Post by mdpalow on 2008-03-25
> **fourthofjuly said:**
> i was suggesting cloning of only installed applications e.g. educational games

only a single system can have wwweb access... which can download and rest 29 can simply copy them... maybe we can even do without thin clients then, i guess? we are planning to reuse our old Celeron machines for the kids lab... the major problem was installing applications on each system since all would not have internet access...

perhaps cloning config files on different configuration of machines will be risky and can best be avoided...

No, you won't be able to clone just the games. However, it shouldn't matter. Just get the Internet machine perfect and then make your back-up. Then go around installing. If you add/update internet machine, then make new back-up and restore on other machines.

In this example, I don't even think I would use the Live CD. I would just do a straight restore on the other computers, which will take only a few minutes each.

---

### Post by fourthofjuly on 2008-03-25
we were indeed worried on the thin client part with Edubuntu server, which atleast in the beginning we wanted to avoid because of complexity...

Quick Start should come in handy here...

Long live Quick Start...!!! 

thank you so much...

---

### Post by fourthofjuly on 2008-03-25
> **mdpalow said:**
> No, you won't be able to clone just the games. However, it shouldn't matter. Just get the Internet machine perfect and then make your back-up. Then go around installing. If you add/update internet machine, then make new back-up and restore on other machines.

In this example, I don't even think I would use the Live CD. I would just do a straight restore on the other computers, which will take only a few minutes each.
could you please elaborate the 2nd part? apart from the first machine, won't the other systems also need installation from the live CD?

i guess i am missing something?

---

### Post by mdpalow on 2008-03-25
> **fourthofjuly said:**
> could you please elaborate the 2nd part? apart from the first machine, won't the other systems also need installation from the live CD?

Yes, sorry. 

What I'm talking about is IF any future installs are/were made to the original machine, you wouldn't need to use Live CD for the others. You could simply restore and you should be fine.

Did that make better sense?

---

### Post by fourthofjuly on 2008-03-25
> **mdpalow said:**
> Yes, sorry. 

What I'm talking about is IF any future installs are/were made to the original machine, you wouldn't need to use Live CD for the others. You could simply restore and you should be fine.

Did that make better sense?
yes Sir, thank you... 

i shall update you as early as possible...

regards,

devang.

---

### Post by Bruce M. on 2008-03-25
> **fourthofjuly said:**
> ok, so restoring config files are only for the same machine

Absolutely.  Those file are pointing to "specific" hardware.

If you want to try a test, pull your Ubuntu HD out of your machine that is working perfectly and put it in another machine with different specs.

99% chance Ubuntu won't work, you'll need to install [SIZE="4"]**/**[/SIZE] at a minimum.

---

### Post by gladstone on 2008-03-25
> **Bruce M. said:**
> Whoa!  Great stuff!  See this: [Re: [SOLVED] xfce4-terminal causes log-out]("http://ubuntuforums.org/showthread.php?p=4576734#post4576734")

Thanks to you I now have xfce4-terminal up and running. And it is so close to gnome-terminal that I can deep6 GT.  :)

**[SIZE="4"][CENTER]THANK YOU![/CENTER][/SIZE]**

Glad to have helped Bruce.

mdpalow: good work on the update ;) and I made my vote on the poll (I bet you guys can guess what I voted for :P) I'm surprised by the results so far aswell, but I guess its the fairest way of doing things.

Lots and lots of activity on this thread! That can only be good!

---

### Post by Dynamo_Joe on 2008-03-25
Hi mdpalow/BruceM, 

Registered my vote! 

Keep up the good work and don't get snared on the "flame-bait". 

Take care.

---

### Post by Bruce M. on 2008-03-26
> **fourthofjuly said:**
> we were indeed worried on the thin client part with Edubuntu server, which atleast in the beginning we wanted to avoid because of complexity...

Quick Start should come in handy here...

Long live Quick Start...!!! 

thank you so much...

Curious about something.

Are you running the Gnome Edbuntu or the Xfce Edbuntu.  I saw somewhere that that's an option.

---

### Post by dmgExP on 2008-03-26
I've discovered the most amazing commercial software developed for Windows that also does a perfect job on a Ubuntu system.

It is [Acronis True Image Home edition]("http://eu.acronis.com/homecomputing/products/trueimage/") 
As the proud owner of an windowless, Ubuntu only, machine I find that it does the job perfectly. It will read and write to ext partitions and create complete (highly compressed) partition images that can be restored and even resized to create a perfect working machine straight from backup.
Acronis is probably the best value for money software that I've ever paid for.

Acronis will only install on a Windows machine but the CD is bootable and that is all you need.

---

### Post by Bruce M. on 2008-03-26
> **dmgExP said:**
> I've discovered the most amazing commercial software developed for Windows that also does a perfect job on a Ubuntu system.

It is [Acronis True Image Home edition]("http://eu.acronis.com/homecomputing/products/trueimage/") 
As the proud owner of an windowless, Ubuntu only, machine I find that it does the job perfectly. It will read and write to ext partitions and create complete (highly compressed) partition images that can be restored and even resized to create a perfect working machine straight from backup.
Acronis is probably the best value for money software that I've ever paid for.

Acronis will only install on a Windows machine but the CD is bootable and that is all you need.

I'm glad for you, what ever you paid for that piece of software, I just saved by using QuickStart.

I'm happy!

EDIT: Just checked out the link, I just saved 49.95 Euros ... I'm VERY VERY VERY VERY VERY happy now!

---

### Post by mdpalow on 2008-03-26
People always THINK they have a good back-up with programs like Acronis, but when it comes time to actually use the back-up to restore - there's almost always a little surprise waiting for them.

Surprise = 6 hours of re-installing everything again and being pretty angry at what you've lost.

Been there.. done that.

I know QuickStart works 'cause I and my friend have probably used it close to 100 times already.

And... since I know QS works with MS Windows as well -  I will definitely not be paying $75-$100.

Go read the Acronis website (forum) and see how many problems their users are having.

:)

---

### Post by vladimir4 on 2008-03-26
Hi there
Is there source code available for  QuickStart 6.0  ? Thanks, v4

---

### Post by Het Irv on 2008-03-26
No, despite our best efforts, QuickStart is a closed source program.
but that could <cough>change</cough>.

---

### Post by mdpalow on 2008-03-26
> **vladimir4 said:**
> Hi there
Is there source code available for  QuickStart 6.0  ? Thanks, v4

Your very first bean and that's your question?  hmmmm....

---

### Post by dmgExP on 2008-03-26
> **mdpalow said:**
> People always THINK they have a good back-up with programs like Acronis, but when it comes time to actually use the back-up to restore - there's almost always a little surprise waiting for them ... Been there.. done that.

I've also had the same unfortunate experience  -- with an earlier version of Norton Ghost (way inferior to Acronis)  And, admittedly Acronis looks expensive now -- until you try it -- I got lucky and paid just $37 USD for version 10 in a box at the local store.

My Acronis backups have allowed me to restore old and deleted files from incremental backups -- easy as browse and click.  I have also restored Windows and Linux primary partitions without a hitch -- it even grew the new partitions automatically when I restored onto a new hard drive.

Key advantages are: (A)  Archives are split into CDR or DVD sized chunks that can be burned to disk.  (B) No OS support is required, therefore you get a complete snapshot of a dormant filesystem without any open, active or locked files.

When you restore with QS you restore the many parts of an active, unstable system.  This kind of backup is a copy of the filesystem and not the disk sectors.  I'm just wondering what would happen if the critical boot loader files were to be moved to the wrong sectors.

---

### Post by mdpalow on 2008-03-26
That's probably a question for a TAR thread since that's what QS is using to back-up the OS. At least for the Ubuntu side of things anyways.... And... since TAR has been around for quite a while and seems to work so well - I'm very comfortable with the technique being used.

Since QS works best when used in conjunction with the Live CD, I don't think you'll have the problem(s) you mention.

Please let's not begin comparing Acronis to QuickStart now and add a number of unnecessary posts/pages to this thread. Acronis is a full-fledged commercial package, which probably has many programmers on the payroll. They're not even in the same class.

Thanks...

---

### Post by Tews on 2008-03-26
> Please let's not begin comparing Acronis to QuickStart now and add a number of unnecessary posts/pages to this thread.

+1

> I've discovered the most amazing commercial software developed for Windows that also does a perfect job on a Ubuntu system.

It is Acronis True Image Home edition
As the proud owner of an windowless, Ubuntu only, machine I find that it does the job perfectly. It will read and write to ext partitions and create complete (highly compressed) partition images that can be restored and even resized to create a perfect working machine straight from backup.
Acronis is probably the best value for money software that I've ever paid for.

Acronis will only install on a Windows machine but the CD is bootable and that is all you need.

I know that I'm probably wrong but all of this "x is better than y" is what I call flame baiting.  Everyone has their own favs and Quick Start is mine. Please, go somewhere else to extol the virtues of yours!

---

### Post by Dynamo_Joe on 2008-03-27
+1

---

### Post by fourthofjuly on 2008-03-27
> **Bruce M. said:**
> Curious about something.

Are you running the Gnome Edbuntu or the Xfce Edbuntu.  I saw somewhere that that's an option.
well, we are not yet running but it has been planned...

but it will be GNOME preferably...

---

### Post by Tews on 2008-03-27
I was creating a backup this morning and wanted to exclude a folder in my /home folder.  I selected the folder, and the files I wanted to exclude however when QS created the backup, it failed to exclude the folder/files that I thought I had marked not to be backed up.  Thinking that I had made a mistake, I redid the backup but the same thing happened.  I ended up having to move the folder to my external hard drive, then complete the backup. Is it a bug, or just me? :confused:

---

### Post by vladimir4 on 2008-03-27
> **Het Irv said:**
> No, despite our best efforts, QuickStart is a closed source program.
but that could <cough>change</cough>.

If it is a closed source program, who guarantee that it is "back door free" (as the root password is required the potential impact is high). No offense please I'm only asking to be assured  :confused:.

Thanks, v4

---

### Post by Tews on 2008-03-27
> If it is a closed source program, who guarantee that it is "back door free" (as the root password is required the potential impact is high). No offense please I'm only asking to be assured .

You've been using Windows for too long.  In Linux, back-doors, viruses, malware etc are very seldom seen in the wild. The reason is because that the OS is locked down so tightly and scum that like to write them, dont have the time or skills necessary to perform a successful hack for the very reason that you mention .. a password is required.  They have much greener pastures to graze in with Windows machines.  The only reason that QS requires a password is to access the /home directory so it can back it up.  I hope this answers your question..............

The bottom line is that Quick Start is closed source and is likely to remain so! :)

---

### Post by vladimir4 on 2008-03-27
> **Tews said:**
> You've been using Windows for too long.  In Linux, back-doors, viruses, malware etc are very seldom seen in the wild. The reason is because that the OS is locked down so tightly and scum that like to write them, dont have the time or skills necessary to perform a successful hack for the very reason that you mention .. a password is required.  They have much greener pastures to graze in with Windows machines.  The only reason that QS requires a password is to access the /home directory so it can back it up.  I hope this answers your question..............

The bottom line is that Quick Start is closed source and is likely to remain so! :)

Thanks for your response, actually the opposite is true about the Windows influence :  I've been using Linux from beginning of '90 (before 1.0 kernel, i was able to run parallel environment on my 386 PC (PVM)) - I used before self assembled Linux systems, but now, because of the lack of time, I switched  to distribution based installations (red hat) and recently to Ubuntu (2 years ago - for my laptop).

I like the idea of those distributions that everything works out of the box and is self-configured (but some sound card and wifi...), but on the other hand it is more difficult to fully control what is installed and how it is configured. But I have confidence to Ubuntu's people, so OK. 
The further step is this kind of scripts - as QuickStart, automatix, ... - another level of abstraction but completely without any control from the user! So the confidence should be even stronger.

You will be surprised how many back-doors can be opened by a simple "bad guy" script on Unix systems, especially when the script is suid or when is asking for administrator's password :)
  
On the installations like Ubuntu it is much easier to hide back doors than in the self-built systems where you know exactly which configuration file and what script do what. So to use QuickStart on something so complicated as Ubuntu configuration requires a lot of confidence, especially if the system is used for such a things like the internet banking.

sorry for the long post

---

### Post by bw44 on 2008-03-27
> **Tews said:**
>  . . .The bottom line is that Quick Start is closed source and is likely to remain so! :)Anyone who has followed this thread from the beginning, knows that the issue of "why isn't QuickStart open source" has been raised a number of times.  And mdpalow has defended his reasons for not doing so.

Unfortunately, there are a great many posts and newcomers to the thread don't always have the patience to read them all and see what's been discussed.

I think Tews underestimates the danger of malicious code and the damage it could do to  your system.  That's all vladimir4 was trying to point out, and I didn't get the feeling he was attacking QuickStart or mdpalow.

Anyone who has followed this thread and seen the amount of help, patience and consideration that mdpalow has devoted to developing, testing and improving  his script would find it pretty difficult to suspect  that he would include malicious code, spyware or anything like that.  To me, anyway, it's simply inconceivable. I trust the guy.  

Like other recent issues concerning alternatives to QuickStart, we are free to choose.  If one is sufficiently committed to the principle of open source, that one doesn't want to take advantage of QuickStart, fine.  If one sees the benefit of using something that isn't open source and has confidence in the person producing it, then maybe the principle should be "trusted source."

Just my 2 cents worth on the subject.

bw44

---

### Post by mdpalow on 2008-03-27
Will check it now. always worked for me, but maybe something got messed up with all the changes being made.

What flavor and version are you using.

---

### Post by mdpalow on 2008-03-27
> **Tews said:**
> I was creating a backup this morning and wanted to exclude a folder in my /home folder.  I selected the folder, and the files I wanted to exclude however when QS created the backup, it failed to exclude the folder/files that I thought I had marked not to be backed up.  Thinking that I had made a mistake, I redid the backup but the same thing happened.  I ended up having to move the folder to my external hard drive, then complete the backup. Is it a bug, or just me? :confused:

Hi Tews,

I just ran a back-up excluding certain folders and it worked for me like it should. Are you using Ubunut 7.10 or... ??

Private message me and let's see what's going on. If you want, PM a phone number and I'll call you so we we can go through it over the phone just to see what's going on.

take care..

---

### Post by Dynamo_Joe on 2008-03-27
> **bw44 said:**
> Anyone who has followed this thread from the beginning, knows that the issue of "why isn't QuickStart open source" has been raised a number of times ... .  

... then maybe the principle should be "trusted source."

Just my 2 cents worth on the subject.

bw44

Trust is a fragile thing ... but if you are unwilling to take the first step in trusting somebody how will others trust you in return when you yourself offer help to others? 

mdpalow hasn't done anything to break our trust in him, so trust him (this is after reading through the 800+ posts and the help and generosity he has given without reservation to all who asks). 

Back on topic, I'm downloading the latest Hardy beta to play with a little bit later and hope QS will be upgraded to support it. :)

---

### Post by mdpalow on 2008-03-27
> **vladimir4 said:**
> If it is a closed source program, who guarantee that it is "back door free" (as the root password is required the potential impact is high). No offense please I'm only asking to be assured  :confused:.

Thanks, v4

NO OFFENSE taken at all. I guess no one can guarantee that, but me. So, for whatever it's worth - I'll tell you that I have never programmed anything into QS that is intended to break into your system or used to hack a computer. To be honest with everyone - If you asked me right now how to even do that, I couldn't tell you.  

QuickStart is a program for me first and foremost. When I saw that it worked nicely for me, I offered it up freely for anyone else who wanted to use it. QuickStart is NOTHING MORE than the 13 functions you see on the main menu. :)

I think your concern is certainly a valid one and if I were on the other side, I'm sure it would have crossed my mind like others in this thread. However, BW44 hit it right on the head with his comments and the point he made is the one I would have used as well. If there had been anything inside QuickStart that was intended to be bad, someone would have caught it by now I'm sure and the gig would have been up.

QuickStart is a friendly offer for you (others) to use. It's free and works as expected with Ubuntu 7.10. If you're looking for a small program that will help you out with backing up your system then feel free to use it when you feel comfortable with the idea of installing/using it. If not, stop by the thread every now and again and read some. At some point you'll get to know me and maybe feel comfortable enough to give it a try.

There's always the ACRONIS back-up software for $40-$70. :)  LOL  (don't know if you got that joke from several posts back)  

take care...

---

### Post by mdpalow on 2008-03-27
> **Dynamo_Joe said:**
> Back on topic, I'm downloading the latest Hardy beta to play with a little bit later and hope QS will be upgraded to support it. :)

Oh yea. 

I use QuickStart too you know! It has to be compatible...  lol ;)

Just praying 8.04 doesn't have a big impact on QS.  [-o<

---

### Post by Bruce M. on 2008-03-27
**[CENTER]With regards to Ubuntu Hardy 8.04[/CENTER]**

Just so people know... between pages 41 and 83 of this thread there are at least 5 or 6 Hardy 8.04 Development Users using QuickStart.  I know, I checked two days ago, sending PM's to people that didn't have their Ubuntu version displayed, to help mdpalow with a question.

**[CENTER]So it's going to be fine with 8.04.[/CENTER]**

Today I received a response from one of those PM's and we actually have one "poster" here who doesn't even have a computer at the moment.  His computer died a while back and he has one being built now.  He has been researching Ubuntu looking for the one thing he wanted; a nice simple easy backup/restore program. He plans on putting Ubuntu 8.04 on his new machine and getting QuickStart just from the things he has read here.

Now something else.

I trust mdpalow, and until just now had no idea that QS was "closed".  Not being a programmer I never even thought to try to look at the code. Have no idea even how.  Since I've met mdpalow I've come to trust him and his decisions for doing things. How many times I've seen him say: Safety First!

I picked up QS because when I ***needed*** to do a restore I found that the program I was using ***didn't restore***!  Great news for something that is in the repositories: HU(Home User)Backup, HURestore.  So I had to go hunting for a method to get my backup restored Well I [found it]("http://ubuntuforums.org/showthread.php?t=679925"), got what I needed and immediately deleted HUBackup and went looking for something else.

Saw some wonderful threads and websites on backing up Ubuntu. Some looked cryptic with the CLI coding to backup and restore. As I said before, not being a program I wanted a GUI thing (not afraid of the CLI at all, just really new here with Linux ), and that's when I found QuickStart.

I agree, there are a lot of options out there for backup/restore programs, disk images, backup to CD/DVD etc. etc. But here I found the person that created it, offering the program for use and supporting it! I read a lot of the pages and saw how he was helping people as fast as he could. Wiping his laptop clean and reinstalling Ubuntu to test the restore function at times. That was good enough for this newbie.

Use what you want, I'm happy for you. 
I'll use what I want, I'm happy for me.

Thanks mdpalow, I'm really happy you're here.
Bruce

---

### Post by money2themax on 2008-03-27
> **mdpalow said:**
> Oh yea. 

I use QuickStart too you know! It has to be compatible...  lol ;)

Just praying 8.04 doesn't have a big impact on QS.  [-o<

no you want 8.04 to have a big impact on QS but you want it to be a good impact not a bad one and by the looks of it it's gonna be just fine

---

### Post by mdpalow on 2008-03-27
> **money2themax said:**
> no you want 8.04 to have a big impact on QS but you want it to be a good impact not a bad one and by the looks of it it's gonna be just fine

I just don't want to have to go into it and change a bunch of code to make it work. I don't think that's going to happen though. If it does - well then we fix it as fast as possible.

:)

---

### Post by Tews on 2008-03-27
> **mdpalow said:**
> Hi Tews,

I just ran a back-up excluding certain folders and it worked for me like it should. Are you using Ubunut 7.10 or... ??

Private message me and let's see what's going on. If you want, PM a phone number and I'll call you so we we can go through it over the phone just to see what's going on.

take care..

Well, all seems to be working fine now ... must be a gremlin or something..

:lolflag:

---

### Post by money2themax on 2008-03-27
> **mdpalow said:**
> I just don't want to have to go into it and change a bunch of code to make it work. I don't think that's going to happen though. If it does - well then we fix it as fast as possible.

:)

i doubt it it looks like not much of the core of the OS is gonna change but i hope they change certain things like having to do with personal preference  for example not being able to tweak the screensaver ect

---

### Post by dmgExP on 2008-03-27
> **Tews said:**
> I know that I'm probably wrong but all of this "x is better than y" is what I call flame baiting.  Everyone has their own favs and Quick Start is mine. Please, go somewhere else to extol the virtues of yours!Some people will jump on their high horse and charge off to battle over nothing -- that's their Iraq.

My intention was simply to inform the community about another solution they may have overlooked -- especially those with critical data who also use Windows.

Anyway I surrender! :)

---

### Post by money2themax on 2008-03-27
> **dmgExP said:**
> Some people will jump on their high horse and charge off to battle over nothing -- that's their Iraq.

My intention was simply to inform the community about another solution they may have overlooked -- especially those with critical data who also use Windows.

Anyway I surrender! :)
i second that motion

---

### Post by mdpalow on 2008-03-28
> **dmgExP said:**
> Anyway I surrender! :)

Your surrender is accepted. :)

Tews isn't jumping on his horse to charge off to battle. Some of us are just a little tired of people coming in the thread for all of a minute, not even trying QuickStart, and right off the bat talking about some off the shelf (commercial) product and suggesting we should buy it instead.

You might have meant well, but others do come in the room periodically telling us how they're only trying to HELP THE COMMUNITY by telling us something we already know (we're all pretty clever by the way) and acting as if they know something we all don't know. 

You have to know that some of the people in this thread have been here since the beginning and have read most, if not all, of the messages. Several of them have written most of the posts in the thread I think! LOL However, when someone  comes in and starts talking about "back doors," security risks, why you shouldn't trust QuickStart, what you should use/buy instead, it just makes those people angry because they're the ones that have either:

Beta tested the software

Given me a suggestion (that was implemented) to make QuickStart better

Actually helped me with some of the code

Taken my PHONE CALL when I offered to call them to help them with a problem

Seen me format my computer just to test something that didn't work on their computer, so I could try to find/fix a problem for them

Worked with me over IM to go over functions

Been spared hours and hours of tinkering with their computer to try and get something to work when QuickStart fixed it for them in less than 60 seconds. 

Helped me shape QuickStart into what it is now, when I wasn't sure which direction I wanted to go on a given problem

QuickStart may have started out as my program, but it's become a little more in that others feel like they've had a say in how their program should work for them. I think it's nice that users of QuickStart know they can post a message, Private Message me, or even e-mail me directly if/when they have a concern and KNOW that I'll be answering them usually within a very short time to either help them or fix whatever it is they think needs fixing.

So for all of you who would come into this thread wanting SAVE US, HELP US, TEACH US, or FIX US, please remember we're all a little close to this and please THINK before you write/type. A little courtesy will go a long way.

Now PLEASE.... let this be the last message on this and let's get back to better discussions. :)

---

### Post by money2themax on 2008-03-28
> **mdpalow said:**
> Your surrender is accepted. :)

Tews isn't jumping on his horse to charge off to battle. Some of us are just a little tired of people coming in the thread for all of a minute, not even trying QuickStart, and right off the bat talking about some off the shelf (commercial) product and suggesting we should buy it instead.

You might have meant well, but others do come in the room periodically telling us how they're only trying to HELP THE COMMUNITY by telling us something we already know (we're all pretty clever by the way) and acting as if they know something we all don't know. 

You have to know that some of the people in this thread have been here since the beginning and have read most, if not all, of the messages. Several of them have written most of the posts in the thread I think! LOL However, when someone  comes in and starts talking about "back doors," security risks, why you shouldn't trust QuickStart, what you should use/buy instead, it just makes those people angry because they're the ones that have either:

Beta tested the software

Given me a suggestion (that was implemented) to make QuickStart better

Actually helped me with some of the code

Taken my PHONE CALL when I offered to call them to help them with a problem

Seen me format my computer just to test something that didn't work on their computer, so I could try to find/fix a problem for them

Worked with me over IM to go over functions

Been spared hours and hours of tinkering with their computer to try and get something to work when QuickStart fixed it for them in less than 60 seconds. 

Helped me shape QuickStart into what it is now, when I wasn't sure which direction I wanted to go on a given problem

QuickStart may have started out as my program, but it's become a little more in that others feel like they've had a say in how their program should work for them. I think it's nice that users of QuickStart know they can post a message, Private Message me, or even e-mail me directly if/when they have a concern and KNOW that I'll be answering them usually within a very short time to either help them or fix whatever it is they think needs fixing.

So for all of you who would come into this thread wanting SAVE US, HELP US, TEACH US, or FIX US, please remember we're all a little close to this and please THINK before you write/type. A little courtesy will go a long way.

Now PLEASE.... let this be the last message on this and let's get back to better discussions. :)
so what your trying to say is it started out as a program and turned into comunity effort to help them selves and others and they don't like ppl not try and dogging their hard work right..and lets not forget you mdpalow as the creator of Quickstart

---

### Post by Tews on 2008-03-28
Thanks mdpalow!  Ive been trying to form a reply to post all night and yours said it all!  If my response offended anyone, please accept my apology.

---

### Post by NikS on 2008-03-28
Looks Quite Handy!!

Would Love To Try It!!!

---

### Post by Officer Dibble on 2008-03-28
Is the link to QuickStart in post 1 the current version, and will this run under 8.04+, please?

:)

---

### Post by Tews on 2008-03-28
Yes and Yes! :lolflag:

---

### Post by Bruce M. on 2008-03-28
> **Officer Dibble said:**
> Is the link to QuickStart in post 1 the current version, and will this run under 8.04+, please?

:)

> **Tews said:**
> Yes and Yes! :lolflag:

Very direct and to the point.
I would have answered with a 300 word essay to say the same thing.  :)

For: Officer Dibble: The latest version is always put there ***just before*** mdpalow tells us it's there.

---

### Post by Tews on 2008-03-28
Im thinking of installing the 64bit Hardy Heron when its released ... will Quick Start run on a 64bit box??

---

### Post by mdpalow on 2008-03-28
> **Tews said:**
> Im thinking of installing the 64bit Hardy Heron when its released ... will Quick Start run on a 64bit box??

Yes, but read the very first post in this thread for instructions on what you have to do first. Pretty simple really, just need to install a few files.

Thanks...

---

### Post by Papa-san on 2008-03-28
Not only do I think this is pretty cool, but this has finally convinced my wife to get away from Windows! 
I was given a link to this thread in my own that was me asking for a way to keep my functional system functioning properly. All that and a backup! BONUS!!!

Thank you!:popcorn:

---

### Post by Tews on 2008-03-28
> I was given a link to this thread in my own that was me asking for a way to keep my functional system functioning properly. All that and a backup! BONUS!!!
:lolflag: I posted that link!  Im glad to see that you made it over!  Im sure that Quick-Start will do everything that you need .

---

### Post by Bruce M. on 2008-03-28
> **Papa-san said:**
> Not only do I think this is pretty cool, but this has finally convinced my wife to get away from Windows!

Now there's a testament for QuickStart if I ever saw one.
I hope you both enjoy the experience.  :)
{slight bow, due to name}
Bruce

---

### Post by mettlewk on 2008-03-29
Thanks for posting this backup routine, it sure helped.

One thing.

It looked like I had the option of choosing where the backup files would be stored but they ended up in the home dir. 
Not a problem, just needed to copy them to removable media.
You might note that.

Gene

---

### Post by mdpalow on 2008-03-29
> **mettlewk said:**
> Thanks for posting this backup routine, it sure helped.

One thing.

It looked like I had the option of choosing where the backup files would be stored but they ended up in the home dir. 
Not a problem, just needed to copy them to removable media.
You might note that.

Gene

Can someone pls verify this comment for me? I actually took out (by mistake) the short command for ensuring the back-up is placed where you selected. HOWEVER, I don't remember uploading that mistake to the server because I caught it too. Please let me know. If so, I'll upload the fix directly after.

Thanks..

---

### Post by mdpalow on 2008-03-29
LOL  :)  

This was sent to me. I went to the actual post and just copied it.

> I have a screwed upgrade, so i cloned my lvm partition with **[COLOR="Red"]acronis[/COLOR]** to my usb hard drive.I have since re-installed it and now want to get back the data on it, but it won't acknowledge the partition even thought it's shown on my usb drive. Any tips????

Good timing. ;)

See, even Acronis isn't perfect.

---

### Post by Bruce M. on 2008-03-29
> **mdpalow said:**
> Can someone pls verify this comment for me? I actually took out (by mistake) the short command for ensuring the back-up is placed where you selected. HOWEVER, I don't remember uploading that mistake to the server because I caught it too. Please let me know. If so, I'll upload the fix directly after.

Thanks..

I'm testing #2 of a manual backup of /home.
I set them to go to: /media/sdb1/Backups/Manual
The folder is empty, and so is my desktop.
EDIT: Both files: in /home

Bruce

---

### Post by Tews on 2008-03-29
I too did a manual backup of /home and it too ended up in the /home directory (/scratches head)

---

### Post by bw44 on 2008-03-29
> **Tews said:**
> I too did a manual backup of /home and it too ended up in the /home directory (/scratches head)

I'm a few QuickStart updates behind the current one, and the manual backup of home goes were I asked it to. So I guess something has changed. Does that help?

---

### Post by Bruce M. on 2008-03-29
> **bw44 said:**
> I'm a few QuickStart updates behind the current one, and the manual backup of home goes were I asked it to. So I guess something has changed. Does that help?

Yea, I'm going to extract an older version (a weeks worth of backups) and try one.
I got the one that is on the server now, and it simply is not doing manual backups.

Bruce

---

### Post by bw44 on 2008-03-29
> **Bruce M. said:**
> Yea, I'm going to extract an older version (a weeks worth of backups) and try one.
I got the one that is on the server now, and it simply is not doing manual backups.

BruceI should have checked before and mentioned the date on my QuickStart program.  It's March 06 (which surprised me because I thought it was more recent.  I think I backed out a version when there seemed to be issues with the exim4/mail thing).

Anyway, the one that seems to be working fine for manual backups is dated March 06.

---

### Post by Bruce M. on 2008-03-29
> **bw44 said:**
> I should have checked before and mentioned the date on my QuickStart program.  It's March 06 (which surprised me because I thought it was more recent.  I think I backed out a version when there seemed to be issues with the exim4/mail thing).

Anyway, the one that seems to be working fine for manual backups is dated March 06.

I don't have it back that far.  Not to worry, the Scheduled Backup are working just fine  :)

---

### Post by mettlewk on 2008-03-29
When I tried to save the tarball  it first offered all the virtual drive addresses, I picked the western digital removable drive and a named subdirectory in it.  I told it to backup.

I then looked in the sub dir on the removable drive and there was nothing there.

I ran it again, this time I went to "root" /media/western-digital-etc/ and there it showed all my subdirectories on the removable drive, I picke the one I wanted and started the backup.

I scratched my head and then looked in the home directory . . . There were two sets of tarballs.
backup-old* and backup*  I then copied those off to the removable media and all was well.

The guy talked about converting his wife. . . This machine belongs to mine. 
Windblows died when an old program was installed,  the restore partition on the hard  disk was crap and had generated a crap recovery disk.  I happened to have a very old Ubutu disk my brother gave me, years ago, I stuck it in and had it up  and running in minutes.  
She whimpers a bit about having to come up to the office to use quickbooks, but for all her other work, this has been working just fine it reads the windows network just fine, and we have converted everything over to open office other than the bookkeeping and my cad stuff.

I had an issue with the HD doing repeated seek/park cycles every 15 secs or so... It had happened after a software update Gibbon installed over apps running on feisty fawn . . .  and the after this therefore (possibly) because of this - caught my attention. I started looking for reports of problems here. Didn't find any cures so I thought I would take it in and have the drive checked out physically.
I was disappointed
Don't go to the Geek Squad, they told me after they had billed me and  misdiagnosed the problem that they don't service linux machines Though the were happy to announce that the drive was bad and sell me a new one. I don't think they ever really checked the drive independent of the the laptop.
  

Gene

---

### Post by jesrani on 2008-03-29
hello, i have installed and used QuickStart, but I dont need it I feel. Please let me know how to uninstall it. I have made a scheduled backup and the program made some files in /Cron folder under my /home folder. How do I delete the scheduled backup and uninstall the program.

---

### Post by 3pinner on 2008-03-29
AAaaaaaaaaaaaaand I have a question!
I just did my first backup, will move the 3 tar files to another hard disk formatted as FAT32.
The 3 files have a lock symbol on them (I'm kinda new here) will that cause any problems during restore?

Thanks!

---

### Post by money2themax on 2008-03-29
> **mettlewk said:**
> When I tried to save the tarball  it first offered all the virtual drive addresses, I picked the western digital removable drive and a named subdirectory in it.  I told it to backup.

I then looked in the sub dir on the removable drive and there was nothing there.

I ran it again, this time I went to "root" /media/western-digital-etc/ and there it showed all my subdirectories on the removable drive, I picke the one I wanted and started the backup.

I scratched my head and then looked in the home directory . . . There were two sets of tarballs.
backup-old* and backup*  I then copied those off to the removable media and all was well.

The guy talked about converting his wife. . . This machine belongs to mine. 
Windblows died when an old program was installed,  the restore partition on the hard  disk was crap and had generated a crap recovery disk.  I happened to have a very old Ubutu disk my brother gave me, years ago, I stuck it in and had it up  and running in minutes.  
She whimpers a bit about having to come up to the office to use quickbooks, but for all her other work, this has been working just fine it reads the windows network just fine, and we have converted everything over to open office other than the bookkeeping and my cad stuff.

I had an issue with the HD doing repeated seek/park cycles every 15 secs or so... It had happened after a software update Gibbon installed over apps running on feisty fawn . . .  and the after this therefore (possibly) because of this - caught my attention. I started looking for reports of problems here. Didn't find any cures so I thought I would take it in and have the drive checked out physically.
I was disappointed
Don't go to the Geek Squad, they told me after they had billed me and  misdiagnosed the problem that they don't service linux machines Though the were happy to announce that the drive was bad and sell me a new one. I don't think they ever really checked the drive independent of the the laptop.
  

Gene
yeah they are notorious for that kind of junk but it does sound like the drive is failing btw tell them...it's like a mac

---

### Post by Bruce M. on 2008-03-29
> **3pinner said:**
> AAaaaaaaaaaaaaand I have a question!
I just did my first backup, will move the 3 tar files to another hard disk formatted as FAT32.
The 3 files have a lock symbol on them (I'm kinda new here) will that cause any problems during restore?

Thanks!

YES!  You'll loose file permissions if put on a FAT32 system

---

### Post by 3pinner on 2008-03-30
Thought so. I reformatted the partition I will store it on to ext3.
thanks for the reply!

---

### Post by Bruce M. on 2008-03-30
> **3pinner said:**
> Thought so. I reformatted the partition I will store it on to ext3.
thanks for the reply!

No problem.

---

### Post by DJ_Peng on 2008-03-30
Forgive me if this has been asked already, I did go through several pages of the topic and I think I know the answer to this but I'd rather ask it and make sure. I'm running Hardy and I need to do a full backup, but my data is spread across multiple partitions with one for root, one for home, and three more for data. (Rather than have a couple nice big drives I have one fairly large and two smallish drives so I have to spread out my files farther than I'd really prefer to do.) I'm assuming QS can handle backing up my root and home partitions, but will it also get my three additional partitions? And am I right to assume that it will back up to DVD without any problems?

---

### Post by Tews on 2008-03-30
> **jesrani said:**
> hello, i have installed and used QuickStart, but I dont need it I feel. Please let me know how to uninstall it. I have made a scheduled backup and the program made some files in /Cron folder under my /home folder. How do I delete the scheduled backup and uninstall the program.

All you need to do is delete the 3 files then choose the uninstall option from the main menu..

---

### Post by bw44 on 2008-03-30
> **Bruce M. said:**
> YES!  You'll loose file permissions if put on a FAT32 system
Hi Bruce,

I just want to clarify/confirm what you said. I thought mdpalow once told me that you could move a tarball to a Fat32 (or NTFS) partition and it would keep the permissions for files inside the archive.

I ask because one thing I do is a daily synchronize of certain files to my Desktop, then archive the synchronized files  and move the archive to a USB data stick which is formatted Fat32.  To recover, I copy the tar back to my Ubuntu partition and extract it there.  It seems to work, but am I losing something? or did I misunderstand you?  Did you mean that you couldn't extract the files to a Fat32 partition and keep their permissions?  That makes sense to me though I admit I've never tested it.

Thanks.

bw44

---

### Post by cajunbulldog on 2008-03-30
:shock::shock:Thank you so much.Now another ex windows person can enjoy his movies!!

---

### Post by Bruce M. on 2008-03-30
> **bw44 said:**
> Hi Bruce,

I just want to clarify/confirm what you said. I thought mdpalow once told me that you could move a tarball to a Fat32 (or NTFS) partition and it would keep the permissions for files inside the archive.

I ask because one thing I do is a daily synchronize of certain files to my Desktop, then archive the synchronized files  and move the archive to a USB data stick which is formatted Fat32.  To recover, I copy the tar back to my Ubuntu partition and extract it there.  It seems to work, but am I losing something? or did I misunderstand you?  Did you mean that you couldn't extract the files to a Fat32 partition and keep their permissions?  That makes sense to me though I admit I've never tested it.

Thanks.

bw44

Let me do more research into this, but I think you're saving yourself by:

> To recover, I copy the tar back to my Ubuntu partition and extract it there.

The file was created and recovered/restored to/from an ext3 partition.

I may well have been wrong in my response about "storing" them on a FAT32 partition, but not if you "backup/restore" to/from the FAT32 system, there you will loose the permissions.

---

### Post by mdpalow on 2008-03-30
> **jesrani said:**
> hello, i have installed and used QuickStart, but I dont need it I feel. Please let me know how to uninstall it. I have made a scheduled backup and the program made some files in /Cron folder under my /home folder. How do I delete the scheduled backup and uninstall the program.

Just delete the Cron folder and QuickStart folder in /home and that's it.

---

### Post by mdpalow on 2008-03-30
> **3pinner said:**
> AAaaaaaaaaaaaaand I have a question!
I just did my first backup, will move the 3 tar files to another hard disk formatted as FAT32.
The 3 files have a lock symbol on them (I'm kinda new here) will that cause any problems during restore?

Thanks!

hi...

no, no problem.

Not a lock symbol... it's a sudo symbol. Meaning it was done (back-up) with extraordinary powers. ;)

I move them all the time and use them... don't worry about it.

---

### Post by mdpalow on 2008-03-30
> **Bruce M. said:**
> Let me do more research into this, but I think you're saving yourself by:



The file was created and recovered/restored to/from an ext3 partition.

I may well have been wrong in my response about "storing" them on a FAT32 partition, but not if you "backup/restore" to/from the FAT32 system, there you will loose the permissions.

You're not losing anything because the files are archived WITHIN a tar file. If you were just copying ind. files to a fat32, you would lose permissions.

---

### Post by mdpalow on 2008-03-30
> **cajunbulldog said:**
> :shock::shock:Thank you so much.Now another ex windows person can enjoy his movies!!

Thanks. :)

These, I have to admit, are always my favorite posts. ... The one's  where people finally get their movies to play...

---

### Post by mdpalow on 2008-03-30
Sorry for being away a bit, but I'm having some difficulties loading Ubuntu 7.10 on a friend's computer, which has taken over my desk at the moment.

Weirdest things happening while trying to install and now it won't see my USB external drive, which I put some files on to help this installation go more quickly.

I will catch up more when I'm able...

---

### Post by mdpalow on 2008-03-30
By the way... I downloaded QS last night off the server and put on this computer and did a back-up. Told QS to place files on Desktop.. Worked for me. What's the problem?

---

### Post by SaddleTramp on 2008-03-30
Just downloaded.  Definitely looks like what I've been looking for (i.e. something easy and to-the-point !!

---

### Post by housam on 2008-03-30
Good work

---

### Post by SaddleTramp on 2008-03-30
First let me say QuickStart is an outstanding app.!!  Very good job!!
Also, I am very new to Linux OS. Figured Ubuntu would be an easier way to learn about it.  Figured I can still learn a few new tricks and besides, I'm an MS survivor !!  I can do anything (welll...almost anyway :lolflag:).

Got a couple of ?'s tho'...

1.  I'm not real familiar with Tar, but compressing from 5.8GB down to 1.25GB!??!  C'mon now...really????????  No joke.  Full backup and that's what it did. (Like I said, I'm new on Linux(Ubuntu), so really don't have a whole lot on here yet.)

2.  Does QuickStart backup protected, hidden, restricted directories/files of any/every kind?

3.  Tried to install DVD/codecs...no joy!!  HOWEVER, I elected NOT to select the versions of Ubuntu offered since I'm running 8.04 64bit (Hardy, which of course you know is still in beta).  But if it would work selecting v7.10, then I'll give it a shot.  Would rather wait to hear back on this before I try it tho'.

All in all, I would recommend this to any/everyone looking for a reliable backup app that's simple, to-the-point, with a good help page, and so far as I've seen on this thread, outstanding support.  

Again, Good Job! and keep up the good work!
Oh yeah, and thanks for sharing it!!

---

### Post by mdpalow on 2008-03-30
> **SaddleTramp said:**
> 

Got a couple of ?'s tho'...

1.  I'm not real familiar with Tar, but compressing from 5.8GB down to 1.25GB!??!  C'mon now...really????????  No joke.  Full backup and that's what it did. (Like I said, I'm new on Linux(Ubuntu), so really don't have a whole lot on here yet.)

2.  Does QuickStart backup protected, hidden, restricted directories/files of any/every kind?

3.  Tried to install DVD/codecs...no joy!!  HOWEVER, I elected NOT to select the versions of Ubuntu offered since I'm running 8.04 64bit (Hardy, which of course you know is still in beta).  But if it would work selecting v7.10, then I'll give it a shot.  Would rather wait to hear back on this before I try it tho'.

All in all, I would recommend this to any/everyone looking for a reliable backup app that's simple, to-the-point, with a good help page, and so far as I've seen on this thread, outstanding support.  

Again, Good Job! and keep up the good work!
Oh yeah, and thanks for sharing it!!

1. Yeah, compressing from 5 gigs to 1.25 is definitely doable, so I'm not surprised at all. I think mine went from 11 gigs to 5 at one time.

2. Yes, if the folder/file is in the / or /home and NOT one of the folders I have purposely excluded; it'll get backed up regardless of whether it's hidden or not.

3. Good question. I'm not sure it would work with QS because of the repository that QS will go to for the download. It will want to go to 7.10 and I'm not sure how that would go over when installing the DVD codecs files.

Thanks and glad you like QS.

---

### Post by DJ_Peng on 2008-03-30
> **DJ_Peng said:**
> Forgive me if this has been asked already, I did go through several pages of the topic and I think I know the answer to this but I'd rather ask it and make sure. I'm running Hardy and I need to do a full backup, but my data is spread across multiple partitions with one for root, one for home, and three more for data. (Rather than have a couple nice big drives I have one fairly large and two smallish drives so I have to spread out my files farther than I'd really prefer to do.) I'm assuming QS can handle backing up my root and home partitions, but will it also get my three additional partitions? And am I right to assume that it will back up to DVD without any problems?Um, anyone?

---

### Post by mdpalow on 2008-03-30
> **DJ_Peng said:**
> Um, anyone?

I don't think it'll back-up your data unless the data falls within the /home or / folder. I imagine if it's in a different partition, but falling under the /home folder it'll work, but otherwise - I don't think so.

No, QuickStart doesn't back-up to DVD. I chose to back-up to hard drive(s) instead. You could write the back-up to DVD when finished if you like and if the files aren't too big.

Thanks.

P.S. Don't be afraid to back-up your system and see what the results are.... it's not going to break anything. :)

---

### Post by DJ_Peng on 2008-03-30
Thanks for the response. Unfortunately I'll need to look for another backup solution. Backing up to hard drives is out of the question in my system, and the additional partitions aren't in the /home partition. But it's good to see something that helps so many people. I'll definitely keep this in mind for when people ask me for backup solutions.

---

### Post by mdpalow on 2008-03-30
ok, no problem. I edited above to say data must be in / or /home, but it can't be in /media, because I exclude that folder.

Thanks

---

### Post by SaddleTramp on 2008-03-31
> **mdpalow said:**
> 1. Yeah, compressing from 5 gigs to 1.25 is definitely doable, so I'm not surprised at all. I think mine went from 11 gigs to 5 at one time.

2. Yes, if the folder/file is in the / or /home and NOT one of the folders I have purposely excluded; it'll get backed up regardless of whether it's hidden or not.

3. Good question. I'm not sure it would work with QS because of the repository that QS will go to for the download. It will want to go to 7.10 and I'm not sure how that would go over when installing the DVD codecs files.

Thanks and glad you like QS.


1.  Good Deal!!
2.  'Ditto'
3.  NP...I'll just try something that don't use Q'stream...that seems to be a common prob with Hardy, although they may have it straightened out in the final release.

Here's a thought tho'...maybe a little script in QS that'll look for the versiion of the OS running and match results in it's repository search...don't know how feasible that is or is that complicated if it would be worth the trouble.
FYI I'm totally satisfied with all the others options as it is.

Thanks again for the QS.
Ya'll take care now and check U later...

S'Tramp

---

### Post by mdpalow on 2008-03-31
> **SaddleTramp said:**
> 1.  Good Deal!!
2.  'Ditto'
3.  NP...I'll just try something that don't use Q'stream...that seems to be a common prob with Hardy, although they may have it straightened out in the final release.

Here's a thought tho'...maybe a little script in QS that'll look for the versiion of the OS running and match results in it's repository search...don't know how feasible that is or is that complicated if it would be worth the trouble.
FYI I'm totally satisfied with all the others options as it is.

Thanks again for the QS.
Ya'll take care now and check U later...

S'Tramp

Hi S'Tramp...

When 8.04 is officially released, I'll update QS so it works properly with the new version. I'm hoping it's only a few minor modifications.

Shouldn't be much longer. :)

---

### Post by mdpalow on 2008-03-31
**[COLOR="Red"][SIZE="3"]UPDATE AVAILABLE[/SIZE][/COLOR]**

Uploaded a fix that solves the problem with QS not saving back-ups where you told it to.

Sorry about this.. This was a dummy move on my part.

A short while ago I was combing the code and saw a very basic command (the one that tells QS where to put the back-up files) that looked like it was duplicated. I should have looked a little more closely, but I didn't - and I took it out.

I then caught the mistake a short while later and put it back in. The problem was, I didn't remember making an update at the same time, so I thought the deletion and restoration of the command was only on my copy and not the one on the server.

To compound the problem, I downloaded QS again today and it seemed to work fine for me. It also worked for me yesterday when I put it on someone else's machine.

However, today I got another message from someone testing this out for me and they said it was happening to them too. 

Ok, so I uploaded my copy again - with the proper command put back in place - and I just got a message saying this copy worked for them properly.

Good deal. Sorry for the hassle... :(

Please update your QuickStart if it's not placing the back-up files where you want them currently.

---

### Post by Tews on 2008-03-31
Thanks for the quick fix!! .... **_This is why I use Quick-Start!!!**_  

Nuff Said!  :)

---

### Post by David Vincent-Jones on 2008-03-31
Thanks ... a much needed utility.
I am very happy to dump sbackup, the total nightmare!

---

### Post by mdpalow on 2008-03-31
> **David Vincent-Jones said:**
> Thanks ... a much needed utility.
I am very happy to dump sbackup, the total nightmare!

I've never used SBACKUP, but I've heard that many times.

Glad you're with us.

Enjoy

---

### Post by Het Irv on 2008-03-31
If was helping another user on a different post, and he found something y'all should be aware of, I don't know if there is much you can do about it other than put it in the FAQ's or something.

Here's the post:
> **JEdwardP said:**
> 
This isn't a bug, I'm sure, just a result I didn't expect in my ignorance of the program. I had expected the restore function to exactly restore my system to its previous state, which I've no doubt it would've done were I not in the habit of uninstalling about half a dozen of Ubuntu's default applications.

For example, I uninstall EoG and replace it with Mirage. Although QuickStart did restore my installation of Mirage, the fresh installation obviously included EoG. The restoration put back whatever config files inform the system EoG was removed, but it could not remove the EoG files, which the fresh install deposited.

The result was that, although EoG's files were on my drive, synaptic reported it as not being installed, its menu icons were present but blank, and neither EoG nor Mirage were set as the default image viewer.

This set of circumstances was repeated for all default applications I had previously uninstalled (Tomboy being another example). As synaptic did not report these apps as installed, I had it install them, and immediately uninstall them again. This restored my system exactly to its previous state.

Thanks once again for your help. In the eight months that I've used Ubuntu as my primary OS, I've rarely failed to find or receive an answer to my questions in these forums.

---

### Post by mdpalow on 2008-04-01
Not a REAL show stopper I think since most people probably aren't removing the default applications that come with a fresh install.

However, and I posted this in his thread as well, if you were one to remove default applications like he does -  I would then do a fresh install of Ubuntu. I would then add all the applications I wanted to have/use (pretty normal so far). I would NOT remove/uninstall anything YET. Once my system was right where I wanted it, I would make a back-up.

THEN I would go in and uninstall the few applications I didn't want.

This way... SPM would have a record of the default programs and you could easily go in and remove the few applications after doing a restore.

Make sense?

---

### Post by bw44 on 2008-04-01
> **mdpalow said:**
> Not a REAL show stopper I think since most people probably aren't removing the default applications that come with a fresh install.

However, and I posted this in his thread as well, if you were one to remove default applications like he does -  I would then do a fresh install of Ubuntu. I would then add all the applications I wanted to have/use (pretty normal so far). I would NOT remove/uninstall anything YET. Once my system was right where I wanted it, I would make a back-up.

THEN I would go in and uninstall the few applications I didn't want.

This way... SPM would have a record of the default programs and you could easily go in and remove the few applications after doing a restore.

Make sense?It does make sense, but it should be pointed out that if you also like to use QS to periodically back up your system after major software updates (for example), then you'd have to re-install the uninstalled applications before making the new back-up, make the backup, and then uninstall them again, if you don't want SPM to lose track of what's what.

(The only reasons I can think of to remove default applications, is if they somehow conflict with non-default ones you want to use, or if you are really strapped for disk space.  Not that JEdwardP's  reasons aren't legitimate, but I'm guessing most users wouldn't need to do this.)

---

### Post by Tews on 2008-04-01
My head is already spinning!  Oo  :confused:

---

### Post by bw44 on 2008-04-01
I was helping Bruce M. to test some possible problems with the latest version of QuickStart and was reminded to run the House Cleaning optiion (#7). 

It doesn't clear my ~/.thumbnails/normal folder though the alert box comes up saying it has. :(

Don't know if this is related to the other problems discussed recently, but thought I should mention it.

PS. I just re-implemented the earlier version of QuickStart, and I thought it was doing all the house cleaning functions just fine, but it's not working now, either. :confused:

---

### Post by mdpalow on 2008-04-01
k, thanks BW44. I haven't touched that code in a while and it was working when I left it. Let me look at it.

brb

---

### Post by mdpalow on 2008-04-01
[COLOR="Red"][SIZE="3"]**Update Available**[/SIZE][/COLOR]

It was working; just backwards.

When I tested the code it worked, but when I put it all together in QuickStart - I inadvertently swapped the two 'thumbnail' directories. So, when you clicked on #2 it was actually deleting #1 and # 1 was deleting #2.

I uploaded the swap to the server if you want to grab it and test again.

Thanks....

---

### Post by bw44 on 2008-04-01
> **mdpalow said:**
> k, thanks BW44. I haven't touched that code in a while and it was working when I left it. Let me look at it.

brbI just tried something else:  I checked** both** the "Delete Thumbnails 1" and "Delete Thumbnails 2" and then QS  deleted the ones in ~/.thumbnails/normal.

Probably I always checked them both before when using the House cleaning Option.  But "Delete Thumbnails 2" doesn't seem to work if checked just by itself.

I hope this helps.

EDIT: It didn't help :) -- mdpalow had figured it out and solved the problem while I was keying in my post!  Thanks!

EDIT2: Tested and it works fine!

---

### Post by mdpalow on 2008-04-01
> **bw44 said:**
> I just tried something else:  I checked** both** the "Delete Thumbnails 1" and "Delete Thumbnails 2" and then QS  deleted the ones in ~/.thumbnails/normal.

Probably I always checked them both before when using the House cleaning Option.  But "Delete Thumbnails 2" doesn't seem to work if checked just by itself.

I hope this helps

Read my post above. You were typing this question as I was already answering it.

You did the same thing I did when testing. That's why we didn't see it at first. :)

---

### Post by Bruce M. on 2008-04-01
> **mdpalow said:**
> [COLOR="Red"][SIZE="3"]**Update Available**[/SIZE][/COLOR]

Got it!

---

### Post by JEdwardP on 2008-04-01
Hello all,

I apologize if I've stirred up any confusion or seemingly tried to create a problem where none exists. I'm not at all strapped for disk space---especially not now----since thanks to Het Irv telling me of QuickStart, I was essentially able to move my Gutsy installation from its original 80GB drive to my 500GB one.

I did my first hard installation of Linux in July '07, after having played with live CD of various distros off-and-on for over two years, and I'm still in the process of re-programming my instincts after 17 years of working daily with DOS/Windows.

Those instincts are geared toward a need to tweak, modify, hack, and otherwise beat my OS into submission, to re-make it into what I want/need, rather than what MS insists on believing I need. A big part of that has always been to replace the apps. bundled with Windows with better ones, and to uninstall those that supposedly cannot be uninstalled.

I've already discovered, of course, that there's much less need for this in Linux, but I have found a handful of examples in which, for me, the default applications are useless, or relatively inferior to other apps. that are available, therefore I've either uninstalled them just to have them gone, or replaced them as seems applicable.

I'm very glad to have been pointed to QuickStart, because I was looking for just such a thing, and I found sbackup to be inadequate. I'm sure sbackup is perfectly suited for many users, perhaps even most, but not for me.

Again, I appreciate the help and information I've gotten here; y'all have helped to make my transition to Ubuntu so smooth that I'm a bit upset with myself for not beginning that transition sooner than I did.

---

### Post by mdpalow on 2008-04-01
You didn't stir up anything I think. We're just talking about you behind your back.  LOL  Just kidding!

Glad you're with us. :)

Your point was well taken actually. In fact, it was made once before by BW44 "I THINK."

Wasn't it you BW that also stumbled on all this?

Anyway, welcome to this thread and hope to see you around...

---

### Post by bw44 on 2008-04-01
> **JEdwardP said:**
> . . .
Again, I appreciate the help and information I've gotten here; y'all have helped to make my transition to Ubuntu so smooth that I'm a bit upset with myself for not beginning that transition sooner than I did.

> **mdpalow said:**
> You didn't stir up anything I think. We're just talking about you behind your back.  LOL  Just kidding!

Glad you're with us. :)

Your point was well taken actually. In fact, it was made once before by BW44 "I THINK."

Wasn't it you BW that also stumbled on all this?

Anyway, welcome to this thread and hope to see you around...

Just to second mdpalow's post -- I don't think anyone was bothered by your raising the issue you did. And thanks for writing up your experience with making the transition to Ubuntu.

I think :) I did once notice some inconsistency between what was installed and what SPM reported was installed, but I certainly never figured out how it was related to using QuickStart.
Thanks for clearing it up.

Cheers.

bw44

---

### Post by coffee on 2008-04-01
Looks cool, I am giving it a try

---

### Post by mdpalow on 2008-04-01
Got an e-mail through forum about QuickStart not working with Mint KDE. Can't return your e-mail 'cause you have that function turned off.

Anyway..... QuickStart was written for Ubuntu 7.10.

Although some functions apparently work in other distros, there will be some compatibility issues when you use anything else.

Thanks

---

### Post by money2themax on 2008-04-01
> **mdpalow said:**
> Got an e-mail through forum about QuickStart not working with Mint KDE. Can't return your e-mail 'cause you have that function turned off.

Anyway..... QuickStart was written for Ubuntu 7.10.

Although some functions apparently work in other distros, there will be some compatibility issues when you use anything else.

Thanks

it looks like it was written for Gnome too not KDE right?

so would it work for Mint Gnome?

---

### Post by mdpalow on 2008-04-01
[COLOR="Red"][SIZE="3"]**update available**[/SIZE][/COLOR]

Hi Everyone,

I was remembering how some people didn't know what to do when QuickStart was finished with the back-up. Meaning... what to do with the terminal windows that were showing you the files being backed up.

So, I basically removed the message after each back-up and created just one message that comes up at the very end and tells you to close the terminal windows when you are done reviewing your back-up. This message stays up until you close it, so we shouldn't be missing that message anymore. :)

Nothing major, but will help many of the new people who aren't sure if the back-up is really complete because the terminal windows didn't go away on their own.

On the server now for your taking....

---

### Post by NullHead on 2008-04-01
> **mdpalow said:**
> [COLOR="Red"][SIZE="3"]**update available**[/SIZE][/COLOR]

Hi Everyone,

I was remembering how some people didn't know what to do when QuickStart was finished with the back-up. Meaning... what to do with the terminal windows that were showing you the files being backed up.

So, I basically removed the message after each back-up and created just one message that comes up at the very end and tells you to close the terminal windows when you are done reviewing your back-up. This message stays up until you close it, so we shouldn't be missing that message anymore. :)

Nothing major, but will help many of the new people who aren't sure if the back-up is really complete because the terminal windows didn't go away on their own.

On the server now for your taking....

Great news! Keep up the good work! :popcorn:

---

### Post by arpad on 2008-04-02
Is there some reason QuickStart ends a backup prematurely? 

I've tried to back up my home directory a couple of times and the best I've managed to do so far is a 160 meg backup file. I've got individual files bigger then that so I'm pretty sure QuickStart's backup function didn't work right. 

There weren't any messages or warnings and the USB drive I'm backing up too has about 100 gig of free space so it's nowhere near filled up.

---

### Post by Tews on 2008-04-02
Just to be on the safe side, download the latest version ( it was updated yesterday ) and wait until you see the "backup completed" message displayed. It sounds to me that with such a large /home directory, you might not be allowing it enough time to complete the process, but I could be wrong ..

---

### Post by mdpalow on 2008-04-02
> **arpad said:**
> Is there some reason QuickStart ends a backup prematurely? 

I've tried to back up my home directory a couple of times and the best I've managed to do so far is a 160 meg backup file. I've got individual files bigger then that so I'm pretty sure QuickStart's backup function didn't work right. 

There weren't any messages or warnings and the USB drive I'm backing up too has about 100 gig of free space so it's nowhere near filled up.

Why not back up your system to your DESKTOP just as a test. If the back-up works... then maybe it's something to do with your flash drive?

When asked where you want to place the back-up files... put your DESKTOP. 

I'll keep an eye out for your reply...

Thanks

---

### Post by arpad on 2008-04-02
tews, mdpalow, I'm going to guess from the quickness of your replies that there's some unpleasantness that can occur with USB drives? By going to the desktop I've breezed by the previous largest backup file size and everything seems to be going pretty well.

If it is a problem with the USB drive it can't just be me so should I be looking for a solution? That's the drive I want to use for backups.

Thanks.

---

### Post by David Vincent-Jones on 2008-04-02
Getting a problem trying to back-up my Windows FAT32 partition.
I have done all of the prelim. steps but at the final point I get a report after 1/2 second that the work is done ... but nothing obviously is.
Is this a FAT32 problem?

---

### Post by ibuclaw on 2008-04-02
I think in the /usr/local folder would be best, separates it from most common stuff.

Something in the general thinking of:
** /usr/local/bin** has an executable text file with commands to execute QuickStart.
** /usr/local/include/QuickStart** is where the files are kept.

[EDIT]
I've just had a look and my local/bin directory only has apps that I've made. And my local/include directory is empty.

Seems like a good idea to me to store it there.

Regards

---

### Post by mdpalow on 2008-04-02
> **arpad said:**
> tews, mdpalow, I'm going to guess from the quickness of your replies that there's some unpleasantness that can occur with USB drives? By going to the desktop I've breezed by the previous largest backup file size and everything seems to be going pretty well.

If it is a problem with the USB drive it can't just be me so should I be looking for a solution? That's the drive I want to use for backups.

Thanks.

Not really. I was just at the computer when you posted and it was the first thing that popped into my head. 

I've never written directly to a flash drive, but have copied my back-ups there before.

---

### Post by mdpalow on 2008-04-02
> **David Vincent-Jones said:**
> Getting a problem trying to back-up my Windows FAT32 partition.
I have done all of the prelim. steps but at the final point I get a report after 1/2 second that the work is done ... but nothing obviously is.
Is this a FAT32 problem?

Are you saying you're using OPTION 5: Back-up and Restore Windows?

What "prelim" steps are you talking about? Installing the required files?

If you're using OPTION 5, what hard drive did you enter to back-up/clone?

---

### Post by mdpalow on 2008-04-02
> **arpad said:**
> tews, mdpalow, I'm going to guess from the quickness of your replies that there's some unpleasantness that can occur with USB drives? By going to the desktop I've breezed by the previous largest backup file size and everything seems to be going pretty well.

If it is a problem with the USB drive it can't just be me so should I be looking for a solution? That's the drive I want to use for backups.

Thanks.

Give me a minute to write a back-up to my flash drive and see what happens... brb

---

### Post by David Vincent-Jones on 2008-04-02
Just tried to dump to my Desktop ... trying to eliminate possible USB problems.
The Master Boot Record appears to have gone correctly but the same quickie 'completion' for the Win image.
A real shame since this looks like a really worthwhile utility set.

---

### Post by mdpalow on 2008-04-02
> **David Vincent-Jones said:**
> Just tried to dump to my Desktop ... trying to eliminate possible USB problems.
The Master Boot Record appears to have gone correctly but the same quickie 'completion' for the Win image.
A real shame since this looks like a really worthwhile utility set.

Sounds to me like you entered the wrong partition to back-up.

I just installed QuickStart on a friend's computer a few days ago and used it to back-up their Windows partition.

Both the MBR and Windows partition were copied and written to the Desktop with no problem.

---

### Post by mdpalow on 2008-04-02
Ok, I have to leave in about 15 minutes and will be gone for several hours. However, let me update everyone real quick with what I've learned.

QS did NOT write to my Flash Drive. Kept going to my Desktop. I looked at the drive in Nautilus and immediately knew what was going on. My Flash Drive is named USB DRIVE. That's two words. If you try and go there in the terminal with two words for the name, it can't find it.

So, I had to change the code to accept a name exactly how it is displayed; spaces and all.

It's working now and writing my / to the Flash Drive as I write this. I will see if it completes the task. Should be done in just a short while.

I will upload change to server shortly or when I get back - depending on how this test goes.

thanks..

---

### Post by mdpalow on 2008-04-02
[COLOR="Red"][SIZE="3"]**UPDATE AVAILABLE**[/SIZE][/COLOR]

Ok, the back-up being written directly to my Flash Drive was successful with no problems. It was 1.2 gigs and when it was finished, I was able to open the archive and see all the files/folders.

I did however update QS to go to a path regardless of the name. Just needed some simple QUOTES around the "$location" command, which tells it to take the entire name/entry exactly as it is and go there.

You can download it now with the fix.

Thanks and good night..

---

### Post by mdpalow on 2008-04-02
> **David Vincent-Jones said:**
> Just tried to dump to my Desktop ... trying to eliminate possible USB problems.
The Master Boot Record appears to have gone correctly but the same quickie 'completion' for the Win image.
A real shame since this looks like a really worthwhile utility set.

David...

Before I leave for the night. If you're using option 5 and trying to back-up/clone your windows OS - Remeber, your MBR is on a drive name and Windows is on a Drive PARTITION.

Therefore, I'm assuming when asked where Windows is located, you should be entering either:

HDA1 or SDA1

Your MBR back-up entry would have said either HDA or SDA. If you have SATA drives, use the 'S'   If you have a regular hard drive use HDA.

I'll check back in later with you to see if you've had any success.

Good luck...

---

### Post by NullHead on 2008-04-03
Just a thought here. Did you ever thing of version numbering QS?? I think it'd be a very nice if it did have version numbers in it's file name.

---

### Post by mdpalow on 2008-04-03
> **NullHead said:**
> Just a thought here. Did you ever thing of version numbering QS?? I think it'd be a very nice if it did have version numbers in it's file name.

Yes, I had considered it - but didn't do it because I always removed the version number when I saw it in a file name.

---

### Post by NullHead on 2008-04-03
> **mdpalow said:**
> Yes, I had considered it - but didn't do it because I always removed the version number when I saw it in a file name.

oh :lolflag: well I suppose it'd do you no good then. I was simply thinking of the version scheme idea just because archiving the files would be easier if there were version numbers.

---

### Post by mdpalow on 2008-04-03
Anyone know how to remove a POLL from the thread?

I can't find anything to get rid of the poll.

Thanks..

---

### Post by Tews on 2008-04-03
I think that is something that one of the mods will have to do..

---

### Post by Bruce M. on 2008-04-03
> **mdpalow said:**
> Anyone know how to remove a POLL from the thread?

I can't find anything to get rid of the poll.

Thanks..

> **Tews said:**
> I think that is something that one of the mods will have to do..

Yup, I just did some checking, mdpalow will have to ask a mod to close it.

---

### Post by BlizzofOZ on 2008-04-05
1. Left-click the Install_QuickStart.sh file below and save it to your DESKTOP

2. RIGHT click the Install_QuickStart.sh file on your DESKTOP and select Properties, then select the Permissions tab at the top, and ensure the 'Execute' check-box is checked towards the bottom where it says 'Allow executing file as program'. Close window.


I'm fairly new to Ubuntu... I have ver 7.10 installed with Xubuntu.  Haven't worked much on GUI side...

Could someone explain in more detail on how to save a file to the DESKTOP?  I'm guessing that once it is in the desktop area, I can the right click to install.


UPDATE:
I got it to the desktop, but I don't see the check box to Execute as a program.  I am guessing that is because of Xbuntu... how can I get to work?

---

### Post by Bruce M. on 2008-04-05
> **BlizzofOZ said:**
> 1. Left-click the Install_QuickStart.sh file below and save it to your DESKTOP

2. RIGHT click the Install_QuickStart.sh file on your DESKTOP and select Properties, then select the Permissions tab at the top, and ensure the 'Execute' check-box is checked towards the bottom where it says 'Allow executing file as program'. Close window.


I'm fairly new to Ubuntu... I have ver 7.10 installed with Xubuntu.  Haven't worked much on GUI side...

Could someone explain in more detail on how to save a file to the DESKTOP?  I'm guessing that once it is in the desktop area, I can the right click to install.


UPDATE:
I got it to the desktop, but I don't see the check box to Execute as a program.  I am guessing that is because of Xbuntu... how can I get to work?

Open Thunar and right-click on the file then Properties > Permissions. The check box will be there.

---

### Post by iThinkergoiMac on 2008-04-05
Installed it... looks pretty sweet.

My only question is what does the scheduled backup actually back up? It's pretty vague... or do I have to set that up in the "create backup" part?

---

### Post by Tews on 2008-04-05
Quick-Start will backup your / folder ( system ), /home folder and your /config folder.  Be sure to keep a copy of the Quick-Start install.py file in your backup folder as well.

Quick-Start is meant to be used in conjunction with the Live CD.  In the event that your system is hosed ( God forbid, but sometimes it DOES happen),  all you will need to do is reinstall, run the Quick-Start install file, then restore your system from your backup folder. Depending on how much data your backup contains, a typical restore should take about 30-45 minutes tops. :biggrin:

---

### Post by David Vincent-Jones on 2008-04-05
I suspect that some of my confusion comes from the speed with which I get the "backup done" message.
I think now that the image file is still 'in transit' ...  a quick look at the external drive only shows a miniscule file ... that was deceiving me.
Other system backups have some sort of reasuring 'task in process' bar .. that would be helpful with the windows transfer.
The real problem with backups is that you never know how valid they are until one has an emergency ... then it is just too late.

David

---

### Post by NullHead on 2008-04-05
Perhaps a good idea would be to produce an md5sum file after the backup is complete and compare the md5 of the folder/location to the md5 after the backup is complete. 

I'm curious. Does this backup system use a external backup program, example: sbackup, or is it a new/custom one you wrote to use in QuickStart?

---

### Post by JEdwardP on 2008-04-05
Hello again all,

When I did my latest back-up, I put the tars on my USB stick, which also happened to contain some files I'd gotten for my closest colleague (a confirmed Windows user who absolutely refuses to even look at Linux, even on a live CD).

When I was scanning those files with the Windows version of Avast anti-virus, it claimed my back-up tars were infected with a trojan. I got a good chuckle out of that, so I report it in hopes that some of y'all will too.

Interestingly, there IS a Linux version of Avast, but I couldn't test it if I wanted to, because its deb package won't install on 64-bit systems, which both of mine are.

---

### Post by Tews on 2008-04-05
Since I dont use Windows <spit> anymore I couldn't say one way or another, however Ill bet my Vaio VGN-AR630e that its a false positive.  If you wanted to you could untar the package and confirm it for us..  ;)

---

### Post by BlizzofOZ on 2008-04-05
> **Bruce M. said:**
> Open Thunar and right-click on the file then Properties > Permissions. The check box will be there.

Thanks, got it to work!

---

### Post by mdpalow on 2008-04-05
> **iThinkergoiMac said:**
> Installed it... looks pretty sweet.

My only question is what does the scheduled backup actually back up? It's pretty vague... or do I have to set that up in the "create backup" part?

Sorry for the late reply. Just got back in town. Scheduled back-up will back-up everything for you into three archive files.

---

### Post by BlizzofOZ on 2008-04-06
How do get the app off  the desktop and into the Applications menu?

---

### Post by Bruce M. on 2008-04-06
> **BlizzofOZ said:**
> How do get the app off  the desktop and into the Applications menu?

Hi BlizzofOz

From the first post here:

> **mdpalow said:**
> 

2. RIGHT click the Install_QuickStart.sh file on your DESKTOP and select Properties, then select the Permissions tab at the top, and ensure the 'Execute' check-box is checked towards the bottom where it says 'Allow executing file as program'. Close window.

3. If you installed the Ubuntu 32-bit OS you can skip this step. If you installed the Ubuntu 64-bit OS, open a terminal window and copy/paste the following, so your system can run 32-bit applications: sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0

4. Click or double-click the Install_QuickStart.sh file now located on your Desktop and select Run in Terminal

Hope this helps
Bruce

---

### Post by BlizzofOZ on 2008-04-06
> **Bruce M. said:**
> Hi BlizzofOz

From the first post here:



Hope this helps
Bruce

Thanks Bruce... I believe I did everything as specified.  The program is sitting on my desktop and is executable... meaning, when I double click on the icon, the program runs.

I think because I have Xubuntu, that may be why I don't see it in the Applications.  Where in Applications would it show?  I don't see it...

---

### Post by Bruce M. on 2008-04-06
> **BlizzofOZ said:**
> Thanks Bruce... I believe I did everything as specified.  The program is sitting on my desktop and is executable... meaning, when I double click on the icon, the program runs.

I think because I have Xubuntu, that may be why I don't see it in the Applications.  Where in Applications would it show?  I don't see it...

QS was/is created for Gnome primarily.  I can't recall if it was in my Applications Menu or not when I ran Xubuntu.

What I did was create a "Quick Launch" for it on the Upper Panel, then I deleted it from the Desktop.

If you right click on the Desktop Icon for QuickStart and then Properties, you can get all the information you need to do the same on the Panel.

If you need more help, just ask.
Bruce

---

### Post by BlizzofOZ on 2008-04-06
> **Bruce M. said:**
> QS was/is created for Gnome primarily.  I can't recall if it was in my Applications Menu or not when I ran Xubuntu.

What I did was create a "Quick Launch" for it on the Upper Panel, then I deleted it from the Desktop.

If you right click on the Desktop Icon for QuickStart and then Properties, you can get all the information you need to do the same on the Panel.

If you need more help, just ask.
Bruce

I'm sorry... I have no idea what that means.  What is the "Upper Panel"?  Is that the Applications drop down?

---

### Post by Bruce M. on 2008-04-06
> **BlizzofOZ said:**
> I'm sorry... I have no idea what that means.  What is the "Upper Panel"?  Is that the Applications drop down?

Across the top and bottom of your screen there are "Panels"

The top has:
Left side: Applications & System or Applications and Places
Right Side: Network Manager, Speaker Control, Date and the [Quit-Restart] button

On the Bottom:
Left Side: The [Desktop] Icon
Right Side: the Windows and the Trash Can

If you right click on the Desktop Icon for QuickStart and then on Properties, you can get all the information you need to do the same on the Panel.

Right-click in the middle of the top Panel > Add to Panel > Application Launcher
And create an "shortcut" to run QS.

If you need more help, just ask.
Bruce

---

### Post by bw44 on 2008-04-06
> **Tews said:**
> Quick-Start will backup your / folder ( system ), /home folder and your /config folder.  Be sure to keep a copy of the Quick-Start install.py file in your backup folder as well.:Tews,

I was just getting caught up on posts to the thread and I saw the above.  What's the install.py file? I don't seem to have one on my system (that I know of!) Or does "install.py" stand for something else?

I usually just copy the whole QuickStart folder to my backup device.

Thanks.

---

### Post by Bruce M. on 2008-04-06
> **bw44 said:**
> Tews,

I was just getting caught up on posts to the thread and I saw the above.  What's the install.py file? I don't seem to have one on my system (that I know of!) Or does "install.py" stand for something else?

I usually just copy the whole QuickStart folder to my backup device.

Thanks.

Let me pop in here, the install.py file is the file you download from the very first post in this thread.

I'm like you though, I have my QuickStart directory in various locations:

/home/bruloo/QuickStart
/media/sdb1/Backups/Hourly/QuickStart (Synced every hour)
/media/sdb1/QuickStart <-> copied from /home whenever there is an upgrade to get.

Bruce

---

### Post by Tews on 2008-04-06
> **Bruce M. said:**
> Let me pop in here, the install.py file is the file you download from the very first post in this thread.

I'm like you though, I have my QuickStart directory in various locations:

/home/bruloo/QuickStart
/media/sdb1/Backups/Hourly/QuickStart (Synced every hour)
/media/sdb1/QuickStart <-> copied from /home whenever there is an upgrade to get.

Bruce

What he said!!  :lolflag:

---

### Post by bw44 on 2008-04-06
> **Tews said:**
> What he said!!  :lolflag:

Bruce, Tews,

Thanks, guys!  Since mdpalow put in the menu option to update QS, I never went back to the first post to download it.  Didn't know what you were talking about.

bw44

---

### Post by Bruce M. on 2008-04-06
> **bw44 said:**
> Bruce, Tews,

Thanks, guys!  Since mdpalow put in the menu option to update QS, I never went back to the first post to download it.  Didn't know what you were talking about.

bw44

Not a problem. I had to go and look to see if that was the file in question before I answered.
And for the same reason too, got to love Option 12!  :lolflag:


**EDIT:** OK, how many of you opened QS to see just what Option 12 is?

---

### Post by mdpalow on 2008-04-06
Not install.py though.... it's install.sh  :)

---

### Post by Tews on 2008-04-06
LOL .. I was going to edit that but I got caught up in something ... Thanks!  :lolflag:

---

### Post by mdpalow on 2008-04-06
No problemo. :)

However, you did have me going #-o

For a minute, I thought I had forgotten about something. 

:popcorn:

Good night

---

### Post by Bruce M. on 2008-04-07
> **mdpalow said:**
> Not install.py though.... it's install.sh  :)

Oh, I missed that.

Guess I'm not perfect anymore. :lolflag:

Like: **Was I ever?**

---

### Post by Tews on 2008-04-08
I have been holding off upgrading to HH 8.04, but I didn't have anything better to do this morning so I ran the upgrade.  Im happy to say that I had no problems .. zero .. sip .. nada! ( not that I was worried, I had 7.10 backed up! )   So I fired up Quick-Start ... made a backup .. worked flawlessly!!  I just cant say enough about this program ... Thanks md!!!

---

### Post by altonbr on 2008-04-09
Since I can't hack the source code, what about a non-gui version that backs up the usres /home, /var, etc. for server purposes?

I'm running into that problem right now ;)

---

### Post by nilarimogard on 2008-04-09
Yeah, I'd like to be able to back up any folder i want

---

### Post by gmvolk on 2008-04-09
Installed quickstart and made my three backups, no problem.  Just a quick question about doing a full restore.

When I boot from the live CD, and re-install Ubuntu do I need to create the same user account and password as on my backups, or when I restore the backups will this set the same user(s) accounts/passwords as it was before the re-install and overwrite the account I created during the install process?:confused:

Thanks for supplying such a useful utility!  Now, if I screw something up while learning Ubuntu, I will be able to get back my system easier!  I wish this was around when I tried Ubuntu a few years back,  I messed up something and basically gave up on Ubuntu.  I could have been so much further in knowing this great OS!

---

### Post by mdpalow on 2008-04-09
> **gmvolk said:**
> Installed quickstart and made my three backups, no problem.  Just a quick question about doing a full restore.

When I boot from the live CD, and re-install Ubuntu do I need to create the same user account and password as on my backups, or when I restore the backups will this set the same user(s) accounts/passwords as it was before the re-install and overwrite the account I created during the install process?:confused:



Good question.

I don't have multiple accounts, so I've never actually tested this concept.

However, I'm guessing when you install Ubuntu with your userid/password and then do a restore - all accounts will be put back as they were when you made the back-up.

Please let us know for sure if/when you have to actually do it...

---

### Post by mdpalow on 2008-04-09
> **nilarimogard said:**
> Yeah, I'd like to be able to back up any folder i want

Why not just highlight all the folders you want in your file browser, right click, and then select Archive. Same thing as QS except you can select ONLY the folders you want. :)

---

### Post by nilarimogard on 2008-04-10
Yeah but i'd like to be able to do this automatic, every X hours :D

---

### Post by jeffspen on 2008-04-10
wow! great smple and really useful software. all of it's features are things i was looking for.
thanks

---

### Post by Tews on 2008-04-10
> **jeffspen said:**
> wow! great smple and really useful software. all of it's features are things i was looking for.
thanks

Welcome to Ubuntu!!  

Now that you have found Quick-Start, you can feel confident that if something happens while you are learning the "ropes", you wont have to spend endless time "rebuilding" your system from scratch!  

Remember that if you run into any problems, you have the best community here to help you out!!

---

### Post by mdpalow on 2008-04-10
> **altonbr said:**
> Since I can't hack the source code, what about a non-gui version that backs up the usres /home, /var, etc. for server purposes?

I'm running into that problem right now ;)

I've read this a couple times and don't get it. What is QS not doing for you?

Also, if you want a non-gui back-up, why not simply create a basic TAR command (multiple ones perhaps to cover everything you want backed up) and put it in an executable text file and then point the Crontab to it or run it by double-clicking?

Thanks...

---

### Post by glentrino2quad on 2008-04-11
Great Tool for Ubuntu! Thanks!

---

### Post by Het Irv on 2008-04-11
No, its not.  It is free to use, but the source is not open.

@Mdplow, I guess you need to put this on the first post, it seems to be a recurring theme.

---

### Post by mdpalow on 2008-04-11
> **Het Irv said:**
> No, its not.  It is free to use, but the source is not open.

@Mdplow, I guess you need to put this on the first post, it seems to be a recurring theme.

Thanks Het Irv... I updated the original post with your comments.


Wow! We're actually coming up on 100 pages. I wonder who's going to be the first 100th page thread poster.

---

### Post by Tews on 2008-04-11
Hmmm ..... maybe you could give away a Delux Edition of Quick-Start :lolflag:

---

### Post by Bruce M. on 2008-04-11
> **Tews said:**
> Hmmm ..... maybe you could give away a Delux Edition of Quick-Start :lolflag:

I'll take it, along with one regular for nostalgia sake. :)

**EDIT:** Darn it, page 99, I loose!

---

### Post by Tews on 2008-04-11
I have a Windows Vista <spit> Ultima disk that I'll convert to a l337 coaster! :lolflag:

---

### Post by Bruce M. on 2008-04-12
> **Tews said:**
> I have a Windows Vista <spit> Ultima disk that I'll convert to a l337 coaster! :lolflag:

Hey, I use to do that with old diskettes, don't like using the CD's though, the hole in the middle leaks liquids.  :)

---

### Post by jakupl on 2008-04-12
I have used QuickStart for several months now, and I must say, it makes a lot of things easyer, specially for a newbie. Thank you very much for that.

---

### Post by jakupl on 2008-04-12
forgot to ask, when I choose "Delete Stored .deb Files" in "House Cleaning", it usually frees about 1G !
What in earth is it doing?

---

### Post by mdpalow on 2008-04-12
> **jakupl said:**
> forgot to ask, when I choose "Delete Stored .deb Files" in "House Cleaning", it usually frees about 1G !
What in earth is it doing?

When you install an application using a .deb file, it (the .deb file) is kept on your hard drive. Imagine it kind of like this.. you download MS Word to your desktop, install it, and the download is left on your hard drive as a back-up. A lot of wasted space for some...

So, you are essentially removing all the .deb files that have been left on your hard drive.

Hope that helps...

---

### Post by talsemgeest on 2008-04-13
They are the ones stored in /var/cache/apt/archives/ right?

---

### Post by chrisdugdale on 2008-04-13
Quickstart worked nicely in Ubuntu 8.04 beta. It got Totem and VLC working straight up after a reboot. Didn't test other functions. Thanks. Chris

---

### Post by mdpalow on 2008-04-13
> **talsemgeest said:**
> They are the ones stored in /var/cache/apt/archives/ right?

Right

---

### Post by mdpalow on 2008-04-13
> **chrisdugdale said:**
> Quickstart worked nicely in Ubuntu 8.04 beta. It got Totem and VLC working straight up after a reboot. Didn't test other functions. Thanks. Chris

Chris,

Are you saying you used Option 9 (Install DVD and Codecs Files) for Ubuntu 8.04 and it worked? Somehow, I think I'm misunderstanding that...

---

### Post by the8thstar on 2008-04-13
This is a great tool and judging by the pages written (100 so far), it fits right in. One could hope to see it in Ubuntu by default in the next releases.

---

### Post by Tews on 2008-04-13
> **mdpalow said:**
> Chris,

Are you saying you used Option 9 (Install DVD and Codecs Files) for Ubuntu 8.04 and it worked? Somehow, I think I'm misunderstanding that...

Hmmm .. Id like to know too ... Ive done 3 reinstalls of Hardy trying to get that option to work correctly ... o0

---

### Post by mdpalow on 2008-04-13
> **Tews said:**
> Hmmm .. Id like to know too ... Ive done 3 reinstalls of Hardy trying to get that option to work correctly ... o0

It should also be stated that I gave TEWS an updated/changed version of QuickStart just for this purpose. :)

Option 9 will not work at all for anyone else who's upgraded to 8.04 and has not received an upgrade from me.

We are just testing out some theories right now... The change/fix has not been proven to work with 8.04... yet.

If/when we get it working, then we'll update and put back on server for everyone to take.

---

### Post by Bruce M. on 2008-04-13
OK, I'm a dyed in the wool NON-beta tester. A left over from my days with that other OS and one failed attempt at Feisty Beta.  But since QuickStart I have come to believe in this program enough to know that if I got 8.04 and it didn't work QS would get me back to 7.10 painlessly.

So three days ago I got 8.04 directly after a scheduled backup. Sadly to say I never got to test QS's restore feature under real conditions as HH worked out-of-the-box so to speak.

But it is my confidence in QS that provoked me testing HH, and it's still backing up on schedule every night.  :)

Thanks mdpalow for a GREAT program

Have a nice day
Bruce

---

### Post by coffee on 2008-04-13
Where can I get the source for QuickStart.  I am working on getting into coding and thought this might be fun to play around with. Anyway can you let me know where to find it so I can look into adding some functionality.

---

### Post by Tews on 2008-04-13
Sorry, but Quick-Start is a closed sourced program..

---

### Post by wagb278 on 2008-04-13
After spending a few hours reading this thread I installed the tool.  Nice!

Feature to think about - unless  i missed it in the discussion: 

An option to backup directories of my choosing via a configuration file or some other mechanism.  I intend to use MySQL with Apache/PHP for a home (as in house) server meaning that I will have MySQL database files (probably in /usr/lib/mysql) and HTTP documents and data files (probably in /srv/www/htdocs).  I would like to use script(s) to backup/restore the files associated with an application (such as VideoDB, for one).  Is this too unique to me, or have others desired such a capability?

I am thinking this is too unique per user to standardize, but figured it doesn't hurt to ask.

Again - nice work!

---

### Post by coffee on 2008-04-13
Oh bummer,  I will work on something else then.

Thank you anyway

---

### Post by rbradt on 2008-04-14
Fairly new user.. just downloaded Quick-Start.

I just did some 'House Cleaning' and it saved me about a GB.

Nice work!  This should be exactly what I need when I'm messing around with my system.  Carefully of course.

Thanks a lot!

---

### Post by hums07 on 2008-04-14
QuickStart works also with Kubuntu, does it??

---

### Post by Tews on 2008-04-14
> **hums07 said:**
> QuickStart works also with Kubuntu, does it??

Yes! .. Quick will work on all flavors of Ubuntu .. However the proof is in the pudding as they say, so grab it and give it a test drive.. :lolflag:

---

### Post by Het Irv on 2008-04-14
mdplow, I ran house cleaning today and it didn't empty my trash.   I have the latest version of QuickStart, Ubuntu 8.04 beta (fully updated as well).  Can someone else test it in 8.04 and 7.10 to make sure it is working.

---

### Post by Tews on 2008-04-14
I just ran option 7 and recovered 1.7GB on 8.04 ... strange that you are having that problem Het!! ](*,)

---

### Post by Het Irv on 2008-04-14
I ran it and removed about 2~3g worth of stuff, but my trash still had stuff in it.  I think it is only that part of the removal option that is broke.  I am about to see if the root one works or not.

---

### Post by David Vincent-Jones on 2008-04-15
Usage Problems:

QuikStart has worked well for my backups but in doing a restore a problem has ocurred. I have been doing the 'home', 'system' and 'config' backups as well as securing my Windows partition.

Yesterday I appeared to have trashed something relating to a single program on my system. The problem was not resolved after a re-installation of the offending program and since my backup was only 2 days old I decided to do a comprehensive system wide restore. 

I ran the 'system' and 'home' restore elements and everything appeared to be back in order. The problem with the offending program was all solved. .... Just as advertised.

However .. my hard drive now appears tobe nearly full! ... My linux partition is 90 GB and prior to the restore I had 50 GB free ... now I have just 10 GB free!

I have looked at individual folders and simply cannot find the 40 GB culprit. Any idea where to look .. 

David

---

### Post by Tews on 2008-04-15
Try option 7 ... thorough cleaning ...  you can also check option 1 to see exactly what you will be trashing ... let us know if that helps...

---

### Post by mdpalow on 2008-04-15
> **David Vincent-Jones said:**
> Usage Problems:

QuikStart has worked well for my backups but in doing a restore a problem has ocurred. I have been doing the 'home', 'system' and 'config' backups as well as securing my Windows partition.

Yesterday I appeared to have trashed something relating to a single program on my system. The problem was not resolved after a re-installation of the offending program and since my backup was only 2 days old I decided to do a comprehensive system wide restore. 

I ran the 'system' and 'home' restore elements and everything appeared to be back in order. The problem with the offending program was all solved. .... Just as advertised.

However .. my hard drive now appears tobe nearly full! ... My linux partition is 90 GB and prior to the restore I had 50 GB free ... now I have just 10 GB free!

I have looked at individual folders and simply cannot find the 40 GB culprit. Any idea where to look .. 

David

Hi again,

I have a couple of thoughts I want to throw out there. I hope this time you'll respond.

1. Did you by any chance RENAME any of the back-ups you've made AFTER making them?

2. How big is your /home back-up?

3. When you did a complete reinstall of your system, did you change the default path from /media/ and /media/home to / and /home during installation? The 'media' path becomes the default on a re-install and would cause you to create another partition if you didn't change it. If so, check gParted to see how many partitions you have now. You might have simply created a new partition and never removed the old one.

4. Click System -> Administration -> System Monitor and then click on the FILE SYSTEMS tab at the top. Does anything look strange like an extra partition or does anything show as being really large?

5. Look in your /home and click CTRL + H to show any hidden folders that might be sitting in there.

Let us know what you find out...

---

### Post by mdpalow on 2008-04-16
> **Tews said:**
> Yes! .. Quick will work on all flavors of Ubuntu .. However the proof is in the pudding as they say, so grab it and give it a test drive.. :lolflag:

Eeeeeeeasy TEWS.... lol :)

I'm pretty sure QuickStart will not work on all flavors; at least not all the functions within QS.

However, as TEWS said, you'll have to try it to see.

---

### Post by Bruce M. on 2008-04-16
> **mdpalow said:**
> Eeeeeeeasy TEWS.... lol :)

I'm pretty sure QuickStart will not work on all flavors; at least not all the functions within QS.

However, as TEWS said, you'll have to try it to see.

I know it works on Xubuntu, I use it.

---

### Post by mdpalow on 2008-04-16
> **Het Irv said:**
> mdplow, I ran house cleaning today and it didn't empty my trash.   I have the latest version of QuickStart, Ubuntu 8.04 beta (fully updated as well).  Can someone else test it in 8.04 and 7.10 to make sure it is working.

I just ran it on my computer (U 7.10) and it emptied the trash. I even ran another test where I created trash files that had an extension (ex: something.ext) and a file with no extension and they were both deleted.

---

### Post by mdpalow on 2008-04-16
> **wagb278 said:**
> After spending a few hours reading this thread I installed the tool.  Nice!

Feature to think about - unless  i missed it in the discussion: 

An option to backup directories of my choosing via a configuration file or some other mechanism.  I intend to use MySQL with Apache/PHP for a home (as in house) server meaning that I will have MySQL database files (probably in /usr/lib/mysql) and HTTP documents and data files (probably in /srv/www/htdocs).  I would like to use script(s) to backup/restore the files associated with an application (such as VideoDB, for one).  Is this too unique to me, or have others desired such a capability?

I am thinking this is too unique per user to standardize, but figured it doesn't hurt to ask.

Again - nice work!

Thanks,

I wouldn't mind adding this feature to help you and others out, but there's a limitation in the Zenity programming, which I think would become a problem. Based on your explanation of what you said you wanted to back-up, it would even be a problem for you. The Zenity file selection tool doesn't allow for going in folders, selecting a folder, backing out of that folder and then going into another folder, selecting a folder, etc. etc....

It's good for selecting files/folders at one level. Once you leave that level - anything you've selected becomes deselected.

I'm not saying it can't be done somehow, but I just wonder how cheesy I'd have to make it in order to work.

I'm not going to be on the computer much today, but I will give this some more thought and look into it. 

In the mean time, if you'd like - Private Message me if/when you're ready to make a custom schedule for your server stuff and I'll write one for you specifically with instructions on how to install it.

Thanks...

---

### Post by David Vincent-Jones on 2008-04-16
> **mdpalow said:**
> Hi again,

1. Did you by any chance RENAME any of the back-ups you've made AFTER making them?

2. How big is your /home back-up?

3. When you did a complete reinstall of your system, did you change the default path from /media/ and /media/home to / and /home during installation? The 'media' path becomes the default on a re-install and would cause you to create another partition if you didn't change it. If so, check gParted to see how many partitions you have now. You might have simply created a new partition and never removed the old one.

4. Click System -> Administration -> System Monitor and then click on the FILE SYSTEMS tab at the top. Does anything look strange like an extra partition or does anything show as being really large?

5. Look in your /home and click CTRL + H to show any hidden folders that might be sitting in there.

Let us know what you find out...

Thanks for the feedback .. could have got back to you sooner but one has to sleep sometimes.

one .. no rename of any file or directory

two .. /home backup is around 40 GB

three .. no path change .. and gparted still shows everything located in just one partition

four .. system monitor also shows just one partition with 90% usage

five .. no hidden files with large data amounts.

It is just as if I have a ghost partition within the system. I think that I will do a full rebuild and reformat .. with Ubuntu and a 2 day old backup it may be the fastest route.

David

---

### Post by mdpalow on 2008-04-16
> **David Vincent-Jones said:**
> ...could have got back to you sooner but one has to sleep sometimes.

 I think that I will do a full rebuild and reformat .. with Ubuntu and a 2 day old backup it may be the fastest route.

David

Ok

For future restores... pls remember the above is how you should do it every time. 

Let us know what it looks like when you're done this time.

Thanks

P.S. Sleep is for the weak.        JUST KIDDING! :lolflag:

No problem on answering after a day. I was referring to the last time you posted a question and I responded to you on two/three occasions, but never got an answer. :)

---

### Post by silvagroup on 2008-04-16
Been looking for a good back up utility. DId not think that was going to be such a big problem in Linux.
This sounds like it maybe it, will this work on Kubuntu also, it is an Ubuntu flavor, right?

---

### Post by mdpalow on 2008-04-17
> **silvagroup said:**
> Been looking for a good back up utility. DId not think that was going to be such a big problem in Linux.
This sounds like it maybe it, will this work on Kubuntu also, it is an Ubuntu flavor, right?

I don't know if it will or not. I remember several months ago testing QuickStart on - I THINK - Kubuntu. I remember seeing something that made me think QuickStart wouldn't work properly in it. I think parts of it might, but not sure about he whole thing.

Give it a try...

You can be our Kubuntu tester if you like. :)

If so, Private Message me with questions or comments. Might be able to make some changes for you as long as they don't interfere with Ubuntu.

thanks

---

### Post by cegpope on 2008-04-18
maybe I am a bit paranoid, but why is the source closed? and why should I as a supporter of  the F.S.F. and an opponent of Microsoft's "just trust us" model, take your word that this program is safe and trust worthy?

---

### Post by Tews on 2008-04-18
> maybe I am a bit paranoid, but why is the source closed? and why should I as a supporter of the F.S.F. and an opponent of Microsoft's "just trust us" model, take your word that this program is safe and trust worthy?

The following is just my opinion and does not necessarily reflect the authors views ... maybe :lolflag:

First and foremost Quick-Start is **still** a work in progress!  I know if I were the person developing an app like QS, I wouldnt even consider releasing the code until it was perfected.  QS was originally created for mdpalows' personal use.  He graciously released it to the public even though it was still in development.  If the code were to be released, I can only imagine the problems that might arise ... then again maybe not ;) .. There is nothing in the philosophy of FOSS that requires the source code to be available to anyone that wants it.  Mdpalow has made the decision that this will be a closed source program and thats good enough for me, I will always respect his decision on this.

No one is asking you to take his/our word that this or any program is safe or trustworthy ... you only have to read the threads and posts about Quick Start and then decide for yourself if it is a program that you might want to use.  Of course the ultimate test is to try Quick Start for yourself.  I'm sure that once you do, your questions/fears will be answered.

---

### Post by talsemgeest on 2008-04-18
> **Tews said:**
> The following is just my opinion and does not necessarily reflect the authors views ... maybe :lolflag:

First and foremost Quick-Start is **still** a work in progress!  I know if I were the person developing an app like QS, I wouldnt even consider releasing the code until it was perfected.  QS was originally created for mdpalows' personal use.  He graciously released it to the public even though it was still in development.  If the code were to be released, I can only imagine the problems that might arise ... then again maybe not ;) .. There is nothing in the philosophy of FOSS that requires the source code to be available to anyone that wants it.  Mdpalow has made the decision that this will be a closed source program and thats good enough for me, I will always respect his decision on this.

No one is asking you to take his/our word that this or any program is safe or trustworthy ... you only have to read the threads and posts about Quick Start and then decide for yourself if it is a program that you might want to use.  Of course the ultimate test is to try Quick Start for yourself.  I'm sure that once you do, your questions/fears will be answered.
Well said!

---

### Post by Bruce M. on 2008-04-18
> **Tews said:**
> The following is just my opinion and does not necessarily reflect the authors views ... maybe :lolflag:

First and foremost Quick-Start is **still** a work in progress!  I know if I were the person developing an app like QS, I wouldnt even consider releasing the code until it was perfected.  QS was originally created for mdpalows' personal use.  He graciously released it to the public even though it was still in development.  If the code were to be released, I can only imagine the problems that might arise ... then again maybe not ;) .. There is nothing in the philosophy of FOSS that requires the source code to be available to anyone that wants it.  Mdpalow has made the decision that this will be a closed source program and thats good enough for me, I will always respect his decision on this.

No one is asking you to take his/our word that this or any program is safe or trustworthy ... you only have to read the threads and posts about Quick Start and then decide for yourself if it is a program that you might want to use.  Of course the ultimate test is to try Quick Start for yourself.  I'm sure that once you do, your questions/fears will be answered.

Again, I repeat: Well said, Tews.

And if I might add, I agree with you totally, <opinion> and probably the same for most that use QS<end opinion>.

mdpalow's support for QS has been, is and probably will continue to be "above and beyond the call of duty" to put it in military vernacular!

Also one must note that **"if"** mdpalow had written something in the code that was "bad" it would have shown up by now. 

Just my opinion / comments
Have a nice day.
Bruce

---

### Post by cegpope on 2008-04-18
> **Tews said:**
> The following is just my opinion and does not necessarily reflect the authors views ... maybe :lolflag:
First and foremost Quick-Start is **still** a work in progress!  I know if I were the person developing an app like QS, I wouldnt even consider releasing the code until it was perfected.  QS was originally created for mdpalows' personal use.  He graciously released it to the public even though it was still in development.  If the code were to be released, I can only imagine the problems that might arise ... then again maybe not ;) .. There is nothing in the philosophy of FOSS that requires the source code to be available to anyone that wants it.  Mdpalow has made the decision that this will be a closed source program and thats good enough for me, I will always respect his decision on this.

No one is asking you to take his/our word that this or any program is safe or trustworthy ... you only have to read the threads and posts about Quick Start and then decide for yourself if it is a program that you might want to use.  Of course the ultimate test is to try Quick Start for yourself.  I'm sure that once you do, your questions/fears will be answered.

You are obviously not familiar with the main tenets of FOSS or the FSF. In order for a project to be considered FOSS and/or meet the ideals of the FSF software must, and I quote, "grant the right of users to study, change, and improve its design through the *availability of its source code.*" 

Part of the benefit of GNU/Linux and Ubuntu is the ability for multiple programmers to work together, to share ideas, and to constantly develop and improve software in such a way as to improve computing for the entire community.

I understand and respect his rights as a developer to keep the source closed, that is his prerogative. My paranoid inquiry is more for understanding why a developer working on a project intended to be utilized on an Ubuntu GNU/Linux system would choose to shun the core ideals which make Ubuntu and GNU/Linux possible. [http://www.ubuntu.com/community/ubuntustory/philosophy](http://www.ubuntu.com/community/ubuntustory/philosophy) 


Closed source gives you Windows, Free/Libre/Open Software brings about Ubuntu GNU/Linux.


> **Bruce M. said:**
> 
Also one must note that **"if"** mdpalow had written something in the code that was "bad" it would have shown up by now. 


I tend to agree; I am more interested from a philosophical point of view than a functional one.





**I feel I should add that I have experimented with the program; I find it handy and beneficial, and I thank mdpalow for making it available at all.** However, I can not pretend that I am not disappointed that a program intended for use on a "Free" system, developed by a member of the Ubuntu community, does not subscribe to the ideals that make such a system possible.

---

### Post by mdpalow on 2008-04-18
We've been through this enough times that I'm not going to answer it again and every time someone new comes in and wants to question the philosophical reasons for why it is the way it is.

I appreciate the fact you like the software and if you want to use it - feel free to.

I'm really done answering this question or even getting into the discussion any more.

:)

---

### Post by money2themax on 2008-04-18
what ver are we @?

---

### Post by mdpalow on 2008-04-18
> **money2themax said:**
> what ver are we @?

6.0

---

### Post by money2themax on 2008-04-18
ok i wasn't sure

---

### Post by Bruce M. on 2008-04-18
> **cegpope said:**
> **I feel I should add that I have experimented with the program; I find it handy and beneficial, and I thank mdpalow for making it available at all.** However, I can not pretend that I am not disappointed that a program intended for use on a "Free" system, developed by a member of the Ubuntu community, does not subscribe to the ideals that make such a system possible.

There are a **lot** of programs you can get for Linux and/or Ubuntu that are closed source, and again some that will cost you as well.

I find no fault with his decision. It is after all, his choice.

Bruce

---

### Post by talsemgeest on 2008-04-18
> **cegpope said:**
> maybe I am a bit paranoid, but why is the source closed? and why should I as a supporter of  the F.S.F. and an opponent of Microsoft's "just trust us" model, take your word that this program is safe and trust worthy?
If you want to right an an open source program, feel free...

---

### Post by iiviip3 on 2008-04-18
Thanks so much for making this it's great! I'm backing up right now. Really appreciate the hard work my friend. Keep up the good work.

---

### Post by cegpope on 2008-04-19
So why exactly does quickstart need mailx and exim? I realize: > exim4" are files required to run the Scheduled Back-up option. It's only three files; let them install.
but the exim files and the mailx files (that I get prompted for when I open quickstart) are a mail transfer agent and a mail user agent. What exactly is this program doing that it needs access to mail capabilities?

additionally, why is it that in the history of this thread I seem to be the only person that has a problem with blindly allowing the installation of files that will allow the program to relay information to a third-party without seeing the code and knowing what quickstart is intending to do with mail capability?

---

### Post by talsemgeest on 2008-04-19
Beacuse a big part of ubuntu is trust.

---

### Post by mdpalow on 2008-04-20
> **cegpope said:**
> So why exactly does quickstart need mailx and exim? I realize: 
but the exim files and the mailx files (that I get prompted for when I open quickstart) are a mail transfer agent and a mail user agent. What exactly is this program doing that it needs access to mail capabilities?

additionally, why is it that in the history of this thread I seem to be the only person that has a problem with blindly allowing the installation of files that will allow the program to relay information to a third-party without seeing the code and knowing what quickstart is intending to do with mail capability?


[-o<

---

### Post by Tews on 2008-04-20
Why is it that you seem unable or unwilling to accept the answers to the questions that you pose??  In fact after admitting that your questions are purely** philosophical**, why are you posting questions of this type at all? This is a support thread for Quick-Start.  If you want to discuss the ethics of FOSS or your concerns about which files are used in the program, please post them in The Community Cafe where they belong!  

The bottom line my young friend, if you don't like it **DON'T USE IT!**, and please cease with all of your flame baiting ...

---

### Post by wagb278 on 2008-04-20
> **mdpalow said:**
> Thanks,

I wouldn't mind adding this feature to help you and others out, but there's a limitation in the Zenity programming, which I think would become a problem. Based on your explanation of what you said you wanted to back-up, it would even be a problem for you. The Zenity file selection tool doesn't allow for going in folders, selecting a folder, backing out of that folder and then going into another folder, selecting a folder, etc. etc....

It's good for selecting files/folders at one level. Once you leave that level - anything you've selected becomes deselected.

I'm not saying it can't be done somehow, but I just wonder how cheesy I'd have to make it in order to work.

I'm not going to be on the computer much today, but I will give this some more thought and look into it. 

In the mean time, if you'd like - Private Message me if/when you're ready to make a custom schedule for your server stuff and I'll write one for you specifically with instructions on how to install it.

Thanks...

Thanks for the offer.  I may take you up on that, but I will try myself first.  My questions were relating to a computer I do not have yet - should arrive late April 08. I have not determined how I will set up partitions or where (directories) to store database and server files.  I was just thinking ahead to how to plan for isolating server-related Data, Scripts, etc. and facilitate backup and restore.

Yesterday I did a fresh install of Ubuntu 7.10-server, then Desktop on an old computer.  First addition to that install was QuickStart.  I started install of Codecs (don't remember option number) and it has been running for over 2 hours and for the last hour there has been no noticeable Hard Disk activity.  I have the sliding bar saying "Installing Codecs - One Moment Please".  Could I have a problem here or is that normal?  This is a 32-bit system, and I selected 32-bit U-7.10 but there is no DVD on the computer.  Computer is P-III, 500 MHz, 384 Meg Ram, 6 GB HDD.

Thanks for a great tool.  

If I might chime in on the Openness of source subject - Are not the Codecs, Flash, etc. not opensource, yet most users install them with no issues or thoughts of being compromised?  So what is the big deal with this script?

---

### Post by mdpalow on 2008-04-20
> **wagb278 said:**
> Thanks for the offer.  I may take you up on that, but I will try myself first.  My questions were relating to a computer I do not have yet - should arrive late April 08. I have not determined how I will set up partitions or where (directories) to store database and server files.  I was just thinking ahead to how to plan for isolating server-related Data, Scripts, etc. and facilitate backup and restore.

Yesterday I did a fresh install of Ubuntu 7.10-server, then Desktop on an old computer.  First addition to that install was QuickStart.  I started install of Codecs (don't remember option number) and it has been running for over 2 hours and for the last hour there has been no noticeable Hard Disk activity.  I have the sliding bar saying "Installing Codecs - One Moment Please".  Could I have a problem here or is that normal?  This is a 32-bit system, and I selected 32-bit U-7.10 but there is no DVD on the computer.  Computer is P-III, 500 MHz, 384 Meg Ram, 6 GB HDD.

Thanks for a great tool.  

If I might chime in on the Openness of source subject - Are not the Codecs, Flash, etc. not opensource, yet most users install them with no issues or thoughts of being compromised?  So what is the big deal with this script?

Thanks WAGB,

No, it's not normal to be running this long. Actually, the length of time it takes to install is less than a minute. Almost sounds like it's not getting connected to the medibuntu site to download the files it needs.

I just ran the option to install codecs (U 7.10) and it worked fine.

Just thinking out loud... you mentioned Ubuntu 7.10 SERVER and then Desktop. I don't know anything about SERVER, so it might be a problem there.

Can anyone else chime in on this with any thoughts/ideas as to what may be different about SERVER that's causing this not to work?

thanks...

---

### Post by wagb278 on 2008-04-20
> **mdpalow said:**
> Thanks WAGB,

No, it's not normal to be running this long. Actually, the length of time it takes to install is less than a minute. Almost sounds like it's not getting connected to the medibuntu site to download the files it needs.

I just ran the option to install codecs (U 7.10) and it worked fine.

Just thinking out loud... you mentioned Ubuntu 7.10 SERVER and then Desktop. I don't know anything about SERVER, so it might be a problem there.

Can anyone else chime in on this with any thoughts/ideas as to what may be different about SERVER that's causing this not to work?

thanks...

I tried again after a restart, which the system was telling me was required.  Same results - hung installing codecs.  I wanted the Adobe Flash add-in for FireFox.  Is this not working?  I saw posts indicating there were problems associated with Adobe Flash.  I can get it manually - I think.

If you think there might be a compatibility issue with the 7.10 server install and want me to perform some tests, or debug log thingie for you I can.  Remember I don't have a DVD drive on this system. 

I used QS to install Gparted and that worked just fine.  So QS is functioning for that feature on the server install.

---

### Post by Het Irv on 2008-04-20
The Flash issues should have been fixed a while back.  With the codecs, try going to Add/Remove and installing the GStreamer packages.

---

### Post by mdpalow on 2008-04-20
> **wagb278 said:**
> I tried again after a restart, which the system was telling me was required.  Same results - hung installing codecs.  I wanted the Adobe Flash add-in for FireFox.  Is this not working?  I saw posts indicating there were problems associated with Adobe Flash.  I can get it manually - I think.

If you think there might be a compatibility issue with the 7.10 server install and want me to perform some tests, or debug log thingie for you I can.  Remember I don't have a DVD drive on this system. 

I used QS to install Gparted and that worked just fine.  So QS is functioning for that feature on the server install.

The Adobe Flash install function was taken out of QuickStart some time ago since the bug was fixed several weeks ago. Fixing the Flash issue was just a temporary fix I put in place to help people out.

I don't think it's a compatibility thing with QS and SERVER. I think SERVER uses something different perhaps and since QS was built on Ubuntu 7.10 alone - it might not be working with SERVER because of those differences.

Thanks for the offer to run some tests, but I think in the end, we would need you to have a DVD player to make sure.

---

### Post by cegpope on 2008-04-21
> **mdpalow said:**
> [-o<

> **Tews said:**
> Why is it that you seem unable or unwilling to accept the answers to the questions that you pose??  In fact after admitting that your questions are purely** philosophical**, why are you posting questions of this type at all? This is a support thread for Quick-Start.  If you want to discuss the ethics of FOSS or your concerns about which files are used in the program, please post them in The Community Cafe where they belong!  

The bottom line my young friend, if you don't like it **DON'T USE IT!**, and please cease with all of your flame baiting ...


Has someone actually responded with a real answer to a question I have posed...
hmmm.... got flamed a couple times for asking about the source....
hmmm.... got flamed a couple times for admitting that it **seems helpful**, but I question the motive of a closed source program for an open system....
hmmm.... got flamed for ASKING A TECHNICAL QUESTION about a security concern. 

Yup, looks like I am the one unable to accept answers, but you of-course are right. Having reviewed the entire thread while trying to discover a reason for the program to be accessing mail agents, I should have known that the only time the author, or his minions of praise, answer questions is when they pertain to an actual glitch in the operation of the program, but whenever anyone inquires as to why something fishy is happening the person is flamed for not simply trusting or moving on.

For the record, I said mostly philosophical, but I still happen to like the ability to review how and why a program is working which is entirely a technical question and source is 100% support related, which as you note is the purpose of this thread.

That being said, my most recent question which deals completely with trying to understand an occurrence that points to a glaring security concern. If there is nothing to hide there is no reason that a technical question should have been met with insult and a complete lack of explanation. I asked a TECHNICAL SUPPORT question about an aspect of quickstart that has a long history of causing trouble and has NEVER been explained, and to what surprise, the questionable action is yet again NOT explained.

This program has obvious security concerns and anyone smart enough to have an interest in keeping their computer secure should definitely avoid this program until it's questionable actions are explained. 



All I am asking is why quickstart is telling me that it needs to have mail user and mail transfer agents installed?

---

### Post by billgoldberg on 2008-04-21
> **cegpope said:**
> Has someone actually responded with a real answer to a question I have posed...
hmmm.... got flamed a couple times for asking about the source....
hmmm.... got flamed a couple times for admitting that it **seems helpful**, but I question the motive of a closed source program for an open system....
hmmm.... got flamed for ASKING A TECHNICAL QUESTION about a security concern. 

Yup, looks like I am the one unable to accept answers, but you of-course are right. Having reviewed the entire thread while trying to discover a reason for the program to be accessing mail agents, I should have known that the only time the author, or his minions of praise, answer questions is when they pertain to an actual glitch in the operation of the program, but whenever anyone inquires as to why something fishy is happening the person is flamed for not simply trusting or moving on.

For the record, I said mostly philosophical, but I still happen to like the ability to review how and why a program is working which is entirely a technical question and source is 100% support related, which as you note is the purpose of this thread.

That being said, my most recent question which deals completely with trying to understand an occurrence that points to a glaring security concern. If there is nothing to hide there is no reason that a technical question should have been met with insult and a complete lack of explanation. I asked a TECHNICAL SUPPORT question about an aspect of quickstart that has a long history of causing trouble and has NEVER been explained, and to what surprise, the questionable action is yet again NOT explained.

This program has obvious security concerns and anyone smart enough to have an interest in keeping their computer secure should definitely avoid this program until it's questionable actions are explained. 



All I am asking is why quickstart is telling me that it needs to have mail user and mail transfer agents installed?

+1

The guy has a point. 

I'm sure as hell ain't going to use the program now.

---

### Post by talsemgeest on 2008-04-21
Ah well, no ones asking him to.

---

### Post by PartisanEntity on 2008-04-21
**cegpope** has a point, part of getting feedback from the community includes answering questions. **cegpope** merely asked why certain packages are being used, I would be interested in the answer too.

The reactions to his questions so far have been disappointing. My impression so far is that the developer does not want to answer the question. Why?

Why should people use Quickstart if the developer doesn&#8217;t have the decency to explain to users and testers what it is they are installing on their machines?

---

### Post by insane_alien on 2008-04-21
i was going to install this till i read cegpopes post.

why does it need a mailclient? it does seem fishy for a backup program. Of course there are plenty of legitimate reasons i can think of for why it could use them but would rather hear from the developer. though he has avoided the question which casts doubt on his motives.

---

### Post by Xbehave on 2008-04-21
> If I might chime in on the Openness of source subject - Are not the Codecs, Flash, etc. not opensource, yet most users install them with no issues or thoughts of being compromised? So what is the big deal with this script?
codecs cant/shouldnt run code on your system
flash is published by a large company and used by many people
A you could ask the same question about malware.exe on windows.

if all quickstart code is yours, then your free to release it under a may not be copied or distributed claws, meaning your still free to do what you want with the code, but people worried about security will feel safe too.

I very much doubt ill install it because this sounds alot like the [dancing pigs/bunnies]("http://en.wikipedia.org/dancing_pigs") problem, only in this case it plays on a users desire for an easy backup solution.

---

### Post by mdpalow on 2008-04-21
> **cegpope said:**
> 

additionally, why is it that in the history of this thread I seem to be the only person that has a problem with blindly allowing the installation of files that will allow the program to relay information to a third-party without seeing the code and knowing what quickstart is intending to do with mail capability?

All I am asking is why quickstart is telling me that it needs to have mail user and mail transfer agents installed?

I doubt it's _what_ your asking CEGPOPE - it's _how_ you're asking.

Are you sure MAILX is just for relaying information to third parties?

Go into a thread Steam Rolling like you do and your questions will probably fall on deaf ears. Come into a thread politely asking questions without all the implied non-sense and you'll get a quick and friendly reply. Private Message me a polite and well crafted question and you'll get the same in return.

So many ways to get what you want without all the DRAMA of back door conspiracies and security leaks. 

"Having read the entire thread..."   Really? This subject has been brought up before and I think it would have been somewhat obvious as to what's going on. AND, if it wasn't - you could certainly post a politely crafted question.

Please don't call the people who use and like QuickStart "Minions." Your use of the word is negative towards the good people in this thread and it's not appreciated.

I think it's good that you can choose not to install and use QuickStart. There are probably a lot of programs out there that can back-up your system. I encourage you and your friends to find one you like and use it.

---

### Post by mdpalow on 2008-04-21
> **insane_alien said:**
> i was going to install this till i read cegpopes post.

why does it need a mailclient? it does seem fishy for a backup program. Of course there are plenty of legitimate reasons i can think of for why it could use them but would rather hear from the developer. though he has avoided the question which casts doubt on his motives.

Thanks insane_alien,

Not avoiding the question really... just get tired of dealing with some people sometimes.

Thanks for your politely crafted question.

Where oh where do I start. :)

When I programmed QuickStart I did it in pieces. When something new came along that I wanted to be able to do, I added it to the program.

At one point, I was running into some problems and couldn't figure out why it wasn't working. So, I installed MAILX. MAILX looks out for errors and then will report them in an e-mail type text file within your file system, which you can read. Basically, it will tell you what the problem was and when it happened. I used this tool to identify what was going on when I was having problems with a function.

Now comes the time when I wanted to do Scheduled Back-ups. I wrote the code and finally got it working the way I wanted. I then updated the server with the new function and basically gave it to anyone that wanted to use/have it.

It had been a couple weeks I think and I never heard anything about it. Then all of the sudden, I got a few people wanting to use the Scheduled Back-up function, but it didn't work for them. It was the weirdest thing because it worked perfectly on my system, but didn't work for them. I kept telling people that it must be something with their system.

So, finally I formatted my laptop with the intent of finding out what was wrong. Sure enough it didn't work on my laptop. I couldn't figure it out. So, I installed MAILX to try and see what it would tell me the problem is/was. After installing MAILX, I went to run Scheduled Back-up again, but this time it worked. I thought it was weird, but I couldn't explain it; it just worked. I told some people in the thread about it and they ran some tests after installing MAILX and sure enough the problem was fixed. Shortly after that, it was determined that EXIM4 (four files that are not part of MAILX) would also work and that we could take out the larger (100kb) MAILX and use it instead. I didn't even know what EXIM4 was, but it worked. So, I quickly replaced MAILX with EXIM4 and the problem was solved. This all took place in a couple hours.

Now you have to remember that QuickStart is first and foremost a program for me to use. But, I give it out in case anyone else wants to use it. One of the options in QS is to install some commonly used applications. Remember now... these are apps that I USE and want to have installed immediately when a do a complete clean. MAILX was one of those applications. Later, I thought I could knock out two birds with one stone by taking MAILX out of the common applications and installing it immediately since Scheduled Back-up needs it to work. So, I decided to take out EXIM4 and use MAILX instead. Basically saved me a step.

Why does MAILX make Scheduled Back-ups work? I REALLY DON"T KNOW. :) I just know it does. In fact, there's no code in the program that even has 'MAILX' in it. I have it installed at the very beginning of the program and that's it; no more reference to it.

Oh, another reason I put in MAILX is because I noticed one time while testing QS that when it installed EXIM4, it was installing some MAILX files. I thought "well if it's doing that, I might as well just install MAILX and be done with it."

So, as you can see. I was never even aware that my Scheduled Back-ups were working because I had something installed (for a completely different reason) on my computer that actually made it work. Hence, MAILX wasn't even a part of QuickStart for several months until we noticed the connection.

I use the EXACT same QuickStart as everyone else. When someone tells me about a bug, I try and fix it and then test it. When testing, I use the same file on my own personal computer. When I'm done testing and reasonably sure it's been fixed, I simply package it - which is nothing more than putting my personal file into a zipped folder for uploading onto the server. When I install QuickStart from the server on my laptop or on a friends computer, I use the EXACT same version as everyone else that I download from the Ubuntu forum and then pull from the server.

So, that's pretty much how MAILX got incorporated into QS. It's really nothing so exciting as a 'back door conspiracy' or any other hyped up DRAMA someone could think of. :)

Hope I answered your question...

---

### Post by Tews on 2008-04-21
Question asked and answered!  Now I can put my tinfoil hat back on the shelf!!  :lolflag:

---

### Post by Dave Otter on 2008-04-21
Will this work in Hardy 8.04

---

### Post by Het Irv on 2008-04-21
For the most part it does, but I have had problems with the house cleaning functions.  If you have any problems, please report them.

---

### Post by mdpalow on 2008-04-21
> **Dave Otter said:**
> Will this work in Hardy 8.04

I think for the most part it is going to work. I need to wait until it actually comes out on the 24th and then look at the DVD/Codecs section, which I've already programmed into a QS that is on stand-by. It doesn't seem to want to work even though the change from 7.10 to 8.04 was so minimal you would think it should have.

Thanks...

---

### Post by mdpalow on 2008-04-21
> **Het Irv said:**
> For the most part it does, but I have had problems with the house cleaning functions.  If you have any problems, please report them.

HET,

I thought we fixed the last mix-up that was in 'House Cleaning?' Can you remind me what the problem is 'cause it all seems to work on my end.

Thanks..

---

### Post by Het Irv on 2008-04-21
Heres what I did:

Boot to 8.04rc
Run updates on QS
Right click on desktop - new folder - delete (so trash contains only one unnamed, empty folder)
Copy random document, send copy to trash.

Open trash folder, confirm that it contains the doc, and folder
Close trash folder
Open QS, option 7, only check the box for delete my trash. 
Box comes up saying "existing trash deleted"
Open trash, doc and folder still there.

Tried w/ a full option 7, same results.
Also tried Root, no luck.

---

### Post by mdpalow on 2008-04-21
ah... I see that. It deletes everything but folders. K, let me fix that. I forgot about folders and only programmed in files.

I have my Trash on my desktop, so I don't use QS to delete Trash.

Let me look now.

---

### Post by Het Irv on 2008-04-21
I have files in there as well, and they are not being deleted.
I don't use this much either, but there happened to have trash in there when I ran it the first time.

Where is QS looking for the trash?
My trash is going to 'trash:///' not '/home/hetirv/.Trash'

---

### Post by mdpalow on 2008-04-21
> **Het Irv said:**
> I have files in there as well, and they are not being deleted.
I don't use this much either, but there happened to have trash in there when I ran it the first time.

Where is QS looking for the trash?
My trash is going to 'trash:///' not '/home/hetirv/.Trash'

yeah, QS is looking at /home/hetirv/.Trash for anything to delete.

What is "trash:///' ??

---

### Post by Het Irv on 2008-04-21
~/.Trash doesn't exsist on my computer.  But if I click the button to show the path file, that is what shows when I am in the trash file.

---

### Post by mdpalow on 2008-04-21
Someone just PM'd me that you're using a beta 8.04. Is that right?

QS isn't built on 8.04, so some changes/fixes/additions will have to be made once the final version comes out.

I'll see what I can do now though since this might be a simple update that will allow this function to work in both versions.

---

### Post by Het Irv on 2008-04-21
Roger, Roger

Root looks to be built the same way.

Q: Is there a way you could code it so that it checks both Locations, for both versions?

---

### Post by mdpalow on 2008-04-21
> **Het Irv said:**
> Roger, Roger

Root looks to be built the same way.

Q: Is there a way you could code it so that it checks both Locations, for both versions?

that's what I'm doing right now...

---

### Post by mdpalow on 2008-04-21
Het,

What's the full path to the new location of this 8.04 trash? Do you know?

---

### Post by Het Irv on 2008-04-21
/home/hetirv/.local/share/Trash/

There are two folders there, files and info, both need to be deleted.
Man that was a pain to find, I just kinda stumbled across it.

---

### Post by Het Irv on 2008-04-21
Heads up, I thought you would like to see this and add some comments.
[http://ubuntuforums.org/showthread.php?t=761232](http://ubuntuforums.org/showthread.php?t=761232)

---

### Post by KiwiNZ on 2008-04-21
> **mdpalow said:**
> We've been through this enough times that I'm not going to answer it again and every time someone new comes in and wants to question the philosophical reasons for why it is the way it is.
 
I appreciate the fact you like the software and if you want to use it - feel free to.
 
I'm really done answering this question or even getting into the discussion any more.
 
:)
 
This is an inappropriate answer. If you dont want  to answer a question multiple times over a period of time put up a FAQ , dont chastise members for asking a question they really need an answer for.

---

### Post by Het Irv on 2008-04-21
At the bottom of the first post there is a line that states that QS is not open source. mdplow, maybe you could add a line saying something to the effect that it is the choies of the devloper to keep this closed source and that will not change untill the dev decides to change this. 

As a side note, I have never really liked your answer on this, but the benifits that this program brings outweigh this.  I have seen the benifits that closed source can bring, and I trust that you won't steal my identity or what not.

---

### Post by Tomosaur on 2008-04-21
> **mdpalow said:**
> Thanks insane_alien,

Not avoiding the question really... just get tired of dealing with some people sometimes.

Thanks for your politely crafted question.

Where oh where do I start. :)

When I programmed QuickStart I did it in pieces. When something new came along that I wanted to be able to do, I added it to the program.

At one point, I was running into some problems and couldn't figure out why it wasn't working. So, I installed MAILX. MAILX looks out for errors and then will report them in an e-mail type text file within your file system, which you can read. Basically, it will tell you what the problem was and when it happened. I used this tool to identify what was going on when I was having problems with a function.

Now comes the time when I wanted to do Scheduled Back-ups. I wrote the code and finally got it working the way I wanted. I then updated the server with the new function and basically gave it to anyone that wanted to use/have it.

It had been a couple weeks I think and I never heard anything about it. Then all of the sudden, I got a few people wanting to use the Scheduled Back-up function, but it didn't work for them. It was the weirdest thing because it worked perfectly on my system, but didn't work for them. I kept telling people that it must be something with their system.

So, finally I formatted my laptop with the intent of finding out what was wrong. Sure enough it didn't work on my laptop. I couldn't figure it out. So, I installed MAILX to try and see what it would tell me the problem is/was. After installing MAILX, I went to run Scheduled Back-up again, but this time it worked. I thought it was weird, but I couldn't explain it; it just worked. I told some people in the thread about it and they ran some tests after installing MAILX and sure enough the problem was fixed. Shortly after that, it was determined that EXIM4 (four files that are not part of MAILX) would also work and that we could take out the larger (100kb) MAILX and use it instead. I didn't even know what EXIM4 was, but it worked. So, I quickly replaced MAILX with EXIM4 and the problem was solved. This all took place in a couple hours.

Now you have to remember that QuickStart is first and foremost a program for me to use. But, I give it out in case anyone else wants to use it. One of the options in QS is to install some commonly used applications. Remember now... these are apps that I USE and want to have installed immediately when a do a complete clean. MAILX was one of those applications. Later, I thought I could knock out two birds with one stone by taking MAILX out of the common applications and installing it immediately since Scheduled Back-up needs it to work. So, I decided to take out EXIM4 and use MAILX instead. Basically saved me a step.

Why does MAILX make Scheduled Back-ups work? I REALLY DON"T KNOW. :) I just know it does. In fact, there's no code in the program that even has 'MAILX' in it. I have it installed at the very beginning of the program and that's it; no more reference to it.

Oh, another reason I put in MAILX is because I noticed one time while testing QS that when it installed EXIM4, it was installing some MAILX files. I thought "well if it's doing that, I might as well just install MAILX and be done with it."

So, as you can see. I was never even aware that my Scheduled Back-ups were working because I had something installed (for a completely different reason) on my computer that actually made it work. Hence, MAILX wasn't even a part of QuickStart for several months until we noticed the connection.

I use the EXACT same QuickStart as everyone else. When someone tells me about a bug, I try and fix it and then test it. When testing, I use the same file on my own personal computer. When I'm done testing and reasonably sure it's been fixed, I simply package it - which is nothing more than putting my personal file into a zipped folder for uploading onto the server. When I install QuickStart from the server on my laptop or on a friends computer, I use the EXACT same version as everyone else that I download from the Ubuntu forum and then pull from the server.

So, that's pretty much how MAILX got incorporated into QS. It's really nothing so exciting as a 'back door conspiracy' or any other hyped up DRAMA someone could think of. :)

Hope I answered your question...

Well, that's a fair enough explanation, but don't you think you'd be better off finding out what MAILX is doing? Seems like a bug to me - the software doesn't work without some other code, but you don't know why :S

Obviously it's up to you, but I do think a lot of people would appreciate it if you could get rid of the dependency on MAILX.

---

### Post by mdpalow on 2008-04-21
I've removed QuickStart from the server and will not continue to support it as I have been over the past several months.

I've REALLY enjoyed all the discussions we've had and the opportunity to make QuickStart work for each and everyone of you. It has been a lot of fun.

QuickStart has helped a lot of people over the months and that's something I'm very happy about.

Thanks CEGPOPE for: [http://ubuntuforums.org/showthread.php?t=761232]("http://ubuntuforums.org/showthread.php?t=761232")

For those of you using QuickStart, continue to use it. There's nothing in it that is malicious or passes info to any third party or whatever else you can think of. It is what it is... a back-up tool with a couple add-ons and nothing more. Don't let people like CEGPOPE scare you into a frenzy fearing the worst. There's nothing happening in the background. Even my best friends use QuickStart - the same copy/file you use and I use. We're all using the exact same file/program. :)

Take care...):P

---

### Post by mdpalow on 2008-04-21
> **Tomosaur said:**
> Well, that's a fair enough explanation, but don't you think you'd be better off finding out what MAILX is doing? Seems like a bug to me - the software doesn't work without some other code, but you don't know why :S

Obviously it's up to you, but I do think a lot of people would appreciate it if you could get rid of the dependency on MAILX.

Thanks Tomosaur...

Yes, I could/would have taken mailx out and put exim4 back in, but at this point I'm just fed up with some of the people in this forum and even SOME of the so called unbiased administrators.

QuickStart works wonderfully for me as is and since I'm not going to make it available any longer, I'll probably keep it the way it is since I do use MAILX for debugging.

Thanks...

---

### Post by mdpalow on 2008-04-21
> **Het Irv said:**
> I have seen the benifits that closed source can bring, and I trust that you won't steal my identity or what not.

You know better Het.

---

### Post by mdpalow on 2008-04-21
> **KiwiNZ said:**
> This is an inappropriate answer. If you dont want  to answer a question multiple times over a period of time put up a FAQ , dont chastise members for asking a question they really need an answer for.

There is a FAQ. I believe it may even be posted in the thread somewhere along the way. Did you ask if there was a FAQ?

Chastised? Somewhat subjective. I could show you chatised, but I'm trying to remain as professional as possible at the moment.

You administrators are something else. Many of you are VERY quick to jump in with your comments and punishments without doing your homework. I'm sure you've handled this whole situation very efficiently and worked it out in the best interest of the Ubuntu community, right?

It's ok, you don't have to reply. This was the last reply I wanted to get out before signing off.

---

### Post by Tews on 2008-04-22
I want to thank mdpalow for his time, effort and devotion in the development of, and his willingness to make Quick-Start available to the Linux community.  It saddens me that he has discontinued support and distribution of Quick-Start.

That being said, I don't think I've ever seen such a display of a community turning on "one of its own" over unsubstantiated charges of malicious code. I would be willing to bet that very few if any of the detractors of Quick-Start have taken the time to read any of the posts that addressed these charges ( that would take some effort on your part ).

This whole episode was started when one individual started demanding answers to questions regarding the philosophical reasoning of the closed source status of Quick-Start.  Not being satisfied with the answers, he then switched his questions to the inclusion of a particular program in the code, warning everyone that Quick-Start could be collecting data.  The bottom line is that he was pi**ed of because no one was willing to cater to his demands. 

Then there was a particular member of the Forum Staff that said > This is an inappropriate answer. If you dont want to answer a question multiple times over a period of time put up a FAQ I wasn't aware we had to run our replies by you before posting them. There is a FAQ.. take the time to search for it ... and get over yourself..

There was another Forum Staff that said in a post on another thread .. > .. Re: Warning! Quickstart Potentially Malicious!
I've looked over both this and the other thread, and I'm not particularly enthused by this response to someone's contribution to the community. I don't see where it was ever proven to be malicious; in fact, it seems the author has withdrawn it over similar comments. To me that's a shame, since someone's efforts, for good or bad, were scuttled for no apparent reason.
Thank-You Sir ...

No one was being forced to use this program ... it was not part of an update.. The bottom line is that if you did not like it you didn't have to use it! The point is moot, because NO ONE will be able to use it now!       **Congratulations!**

---

### Post by talsemgeest on 2008-04-22
Hear hear!

---

### Post by quibbler on 2008-04-22
I too would like to thank mdpalow for all his work on what I feel is a fine and needed program.
You have been treated badly by a few, but also know, you have made a lot of friends.

My very best regards

quibbler

---

### Post by smartboyathome on 2008-04-22
I am sad to see quickstart go. If you would, would you send the proprietary copy to me? I would like to "poke and prod" it to see its functions, I was already trying to make a copy of it which was open. Thanks, and sorry to see this great project go.

Smartboy

---

### Post by Bruce M. on 2008-04-22
> **mdpalow said:**
> I've removed QuickStart from the server and will not continue to support it as I have been over the past several months.

It's a sad day! One of the greatest little utilities available and now it is gone.

I'd like to take this opportunity to thank you and all your hard work to make QS what it is. There are those of us that appreciate what you have done for us by sharing this little gem.

[SIZE="4"][CENTER]**Thank you mdpalow.**[/CENTER][/SIZE]

> **mdpalow said:**
> I've REALLY enjoyed all the discussions we've had and the opportunity to make QuickStart work for each and everyone of you. It has been a lot of fun.

QuickStart has helped a lot of people over the months and that's something I'm very happy about.

Me too my friend, me too. I hope all your future endeavours are a success.

> **mdpalow said:**
> Thanks CEGPOPE for: [http://ubuntuforums.org/showthread.php?t=761232]("http://ubuntuforums.org/showthread.php?t=761232")

I lost the support of one of my favourite programs because of this. And since my grandmother told me; "If you can't say anything nice, don't say anything at all." So I have no further comment!

> **mdpalow said:**
> For those of you using QuickStart, continue to use it. There's nothing in it that is malicious or passes info to any third party or whatever else you can think of. It is what it is... a back-up tool with a couple add-ons and nothing more. Don't let people like CEGPOPE scare you into a frenzy fearing the worst. There's nothing happening in the background. Even my best friends use QuickStart - the same copy/file you use and I use. We're all using the exact same file/program. :)

Take care...):P

Oh I will I will.  Thank you once again my friend for everything

Have a GREAT day, you've earned it.
Bruce

---

### Post by Het Irv on 2008-04-22
Well, I guess this just goes to show that it only takes one person to screw up everyones fun.  mdplow, you program has been one of the best tools I have come across on Windows or Linux, and it has given me some peace of mind knowing that can restore my data at any time, or if I need to rebuild, that I only have one place to go for all my needs.

I'm gonna stick with the "if you can't say anything nice" because I don't want to get an infraction slapped on me.  But keep in mind that I consider what CEGPOPE did Slander/Liable.

[SIZE=6]Good Job and Good Luck on Future Endveours[/SIZE]

---

### Post by Het Irv on 2008-04-22
accidental double post

---

### Post by cegpope on 2008-04-22
IN MY OWN DEFENSE

I never said it **IS** malicious only that it **COULD BE**. Reminding people to be vigilant is not liable or slander. 



I posted my Warning (meaning cautionary statement) after receiving a series of private messages from other users that have/had similar concerns over the way in which posters with doubts are treated in this thread.  



I should also note that although I can not prove it, I reported MYSELF using the report post button shortly after making the post, because I wanted to edit/delete my post to make it less harsh, but at that point the forum software prevented it.



If mdpalow chooses not to continue sharing his program that is fine with me. If expressing security concerns and cautioning other users about the potential pitfalls of trusting anonymous, closed programs is all it takes to initiate the retraction of a program, then maybe it is my tin foil hat speaking, but that sounds as though added scrutiny is unwelcome.



As I said (although I admit, rather unkindly) in my thread, I do not know whether or not quickstart is malicious. However, in this era of identity theft, computer hi-jacking, and the role malicious code in otherwise helpful programs plays, all computer users need to question and need to doubt ANY time you are told to simply trust.

All I have ever been looking for was a reason to trust and saying, "trust me," is not a reason.

---

### Post by Het Irv on 2008-04-22
> **cegpope said:**
> IN MY OWN DEFENSE

I never said it **IS** malicious only that it **COULD BE**. Reminding people to be vigilant is not liable or slander. 



I posted my Warning (meaning cautionary statement) after receiving a series of private messages from other users that have/had similar concerns over the way in which posters with doubts are treated in this thread.  



I should also note that although I can not prove it, I reported MYSELF using the report post button shortly after making the post, because I wanted to edit/delete my post to make it less harsh, but at that point the forum software prevented it.



If mdpalow chooses not to continue sharing his program that is fine with me. If expressing security concerns and cautioning other users about the potential pitfalls of trusting anonymous, closed programs is all it takes to initiate the retraction of a program, then maybe it is my tin foil hat speaking, but that sounds as though added scrutiny is unwelcome.



As I said (although I admit, rather unkindly) in my thread, I do not know whether or not quickstart is malicious. However, in this era of identity theft, computer hi-jacking, and the role malicious code in otherwise helpful programs plays, all computer users need to question and need to doubt ANY time you are told to simply trust.

Yeah, I understand what you are saying, but one of the other things that sucks about this era is that most of the time its not what you say, but how you say it.  I'll admit, it might have been a bit harsh, but like I said, your timing sucked.  The QuickStart thread was meant to be a support & Development thread and people kept trying to shift it to a code philosophy thread.  It was getting frustrating.

---

### Post by Tews on 2008-04-22
I think you've done enough damage here. There is no defense for what you have done unless being a spoiled, self-centered child, jerk and all around troll is a defense!  There, now you **have** been flamed!!! Dont go away mad .... just go away!

---

### Post by Bruce M. on 2008-04-22
The sad thing here is, new users, myself included, that found QuickStart found it to be a real gem of a utility. We, new users, are not CLI literate, and some have a fear of the CLI, look what QS did for us. It got us up and running with a sense of confidence knowing we have a reliable backup/restore system that is "almost" too simple to use, set-up a schedule and forget it. Create a manual backup at any time in case I wanted to try something radical. Confidant that I could restore if it messed up.

It installed DVD codecs with a push of the button and even backed up our Windows Partitions. We could edit config file with easy, the original was always backed up on the Desktop where we could see it. It does "house cleaning" and installs some common files as well. 

It's gone, the how's and why's are now documented. And I can't help but feel sad over all this. Mdpalow was sharing something he created for himself. No one twisted my arm to use it, I did so by choice. I've PM'd mdpalow, we've sent emails back and forth in support of QuickStart.

Considering that it is a single 88.2kB file that does everything it does, with the simplicity that it does it made it a "must have" for new users, and some veterans, to Linux (Ubuntu).

Lets all hope that it is already 8.04 compatible, because that's two days away folks, and while mdpalow was working on that with a few 8.04 beta users, that support is now gone.

cegpope, I hope you are happy but I want you to know that I certainly am not happy.

CHIMO!
Bruce

---

### Post by Het Irv on 2008-04-22
> **Bruce M. said:**
> The sad thing here is, new users, myself included, that found QuickStart found it to be a real gem of a utility. We, new users, are not CLI literate, and some have a fear of the CLI, look what QS did for us. It got us up and running with a sense of confidence knowing we have a reliable backup/restore system that is "almost" too simple to use, set-up a schedule and forget it. Create a manual backup at any time in case I wanted to try something radical. Confidant that I could restore if it messed up.

It installed DVD codecs with a push of the button and even backed up our Windows Partitions. We could edit config file with easy, the original was always backed up on the Desktop where we could see it. It does "house cleaning" and installs some common files as well. 

It's gone, the how's and why's are now documented. And I can't help but feel sad over all this. Mdpalow was sharing something he created for himself. No one twisted my arm to use it, I did so by choice. I've PM'd mdpalow, we've sent emails back and forth in support of QuickStart.

Considering that it is a single 88.2kB file that does everything it does, with the simplicity that it does it made it a "must have" for new users, and some veterans, to Linux (Ubuntu).

Lets all hope that it is already 8.04 compatible, because that's two days away folks, and while mdpalow was working on that with a few 8.04 beta users, that support is now gone.

cegpope, I hope you are happy but I want you to know that I certainly am not happy.

CHIMO!
Bruce

Sorry to say but, its not perfect for 8.04 but it should work for the most part.

---

### Post by Tews on 2008-04-22
> **Het Irv said:**
> Sorry to say but, its not perfect for 8.04 but it should work for the most part.

The only part that is now MIA is the update function ...

---

### Post by Bruce M. on 2008-04-22
> **Het Irv said:**
> Sorry to say but, its not perfect for 8.04 but it should work for the most part.

As long as the "backup/Restore" part works I'll be happy.

QS has issues with my motherboard, believe it or not, because my MB has issues with Xfce4-terminal. The "bug fix" got the terminal working, but I'm not so sure it got "everything" working.

mdpalow was helping me with this... thanks to some that's gone now. :cry:

---

### Post by gladstone on 2008-04-22
As much as I liked the program, I feel this is the best way to go because of the inherent disagreement and confusion raised in this thread. I'm not gonna start pointing fingers nor share any more of my opinion - I even did abit of testing for mdpalow in the past but haven't actually used the program much (I felt it was overkill for my use). Some of the points raised on both sides of the argument are interesting and even more valid when it comes down to the sensitive data the program is managing. If important issues like this are even being questioned, I feel this outcome is best for users in the long run.

---

### Post by talsemgeest on 2008-04-23
Well at least the other thread has been locked because of it's outrageous and harmful comments. Kudos to K.Mandla for his actions.

---

### Post by CanonKen on 2008-04-24
Well I hope all of you that was after the source code are very happy now, had a great helpful person that written a cracking little program and helped many people out - me included, all that,s gone now

Well done Mdpalow in creating QS in the 1st place and thanks for everything, I'll continue to use it for as long as I can, just hope it works with future versions of Ubuntu

---

### Post by weaver4 on 2008-04-25
I come to this forum to get the latest version of QuickStart for 8.04 and this is what I find.

What a sorry lot!  No Ubuntu for you; and I am not talking about the distribution.

---

### Post by Lazul on 2008-04-25
QuickStart is one of the best things I have ever used, it's simple and has all the utilities I would ever need.  Shame on the unfaithful for causing all of this, it is understandable for one or two to say that it *might* be dangerous, trying to help people, but for it to come to this is horrible.

---

### Post by Therion on 2008-04-25
> **weaver4 said:**
> I come to this forum to get the latest version of QuickStart for 8.04 and this is what I find.
You and me both.  

What a sad statement that our community can be so easily marred by what appears to be nothing more than, at best, the paranoid ramblings of a very vocal - very minor - minority.

An elegant little application I tried once and immediately couldn't live without.  

I don't know which makes me sadder: Not having QS anymore, or the moronic attitudes and postings in "my" community that took it away, not just from me, but from everyone.

I'm truly stunned.

---

### Post by brucewagner on 2008-04-25
MDPalow,

Thanks for sharing this utility with us all.  I understand that supporting such a thing must make you sometimes feel like you've created a monster... asking yourself, "What have I created?"

I'm sure that when you shared QuickStart, you at least created another part-time job for yourself... if not another FULL time job.

It was exceedingly generous of you.

Although it's sad that some might jump to the worst possible conclusions about your intensions, I guess that is to be expected when dealing with the public.   There's one idiot (at least) in every crowd who gets off on causing trouble.

Hell.  As we all know, if it weren't for Closed Source (with all of its possible trojan horses of evil code), my video card would not even be able to display Ubuntu on my monitor.

Anyway, I'm sure that supporting this utility was not your number one life mission...  Your calling...  Your chosen vocation.   And I'm certain that it was a huge responsibility -- albeit one you did with joy.

Thank you for your kind generosity.

PS - For anyone (like me) who was using QuickStart primarily to get video codecs, java, etc. working...   I recommend checking out this How To...  (and it is updated for Hardy Heron 8.04, as well as earlier versions of Ubuntu):   [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Cheers & Hugs,

Bruce Wagner

---

### Post by David Vincent-Jones on 2008-04-25
Such a fine program .. quite a loss

We can only hope that the author can be persuaded to pass the flame over to others with more time. Maybe even as fully open source.

Thanks anyway for those who made it happen.

---

### Post by David Vincent-Jones on 2008-04-25
Such a fine program .. quite a loss

We can only hope that the author can be persuaded to pass the flame over to others with more time. Maybe even as fully open source.

Thanks anyway for those who made it happen.

---

### Post by Tews on 2008-04-25
It may not be as dead as you think :lolflag:  Stay Tuned!!!

---

### Post by john_scott_reardon on 2008-04-26
Hi,  I'm sorry I was late finding this thread.  I could really use a program like this.  It looks like a great one.  Please bring it back.

---

### Post by locolobo on 2008-04-26
I must wonder about the age of the rabble rousers that ran off the support
of this thread. QUICK START just saved my beacon again when I tried to upgrade and IT didna work for whatever reason. QUICK START is a fine program
and it was very kind of the GENTLEMAN to share it with us all!!
HE will be sorely missed , unlike some of his detractors.
I have followed this thread from start and have learned a lot about the attitude of the participants...........:(
I would gladly pay the author for a CD copy of Quick Start!!

---

### Post by mdpalow on 2008-04-27
Thanks for everyone's kind posts. They ARE appreciated. As TEWS suggested, QuickStart isn't dead. Too many people are/were contacting me via PM's and E-mail for me to feel right about closing this down for good. Maybe I just needed some time to cool down. So glad I never clicked the "Submit" button on a few posts I wrote. LOL

I'm currently building a QuickStart forum of my own, which I will use to support everyone/anyone who has questions/comments. Unfortunately, I think it's the only way to do this. Using the Ubuntu forum is great and very convenient, but it's problematic; especially with the subjective viewpoints of SOME posters and moderators.

Now, with our own forum, I/we (me and Mods) will be able to handle people like CEGPOPE and those situations as need be.

I think it's possible the forum could be up as early as today, but not 100% sure just yet. I'll post here again with a link when it's up.

Also, I have a QuickStart update, which I was working on just before all this mess started, for 8.04 that allows the DVD/Codecs option to work with 8.04... and I updated a portion of the 'House Cleaning' utility to work with 8.04 as well.

Look forward to talking with all you wonderful QuickStart friends again,

mdpalow :)

---

### Post by Phosphoric on 2008-04-27
Oh Joy.:)

Well done mdpalow for not bowing down to the shameful way that you have been treated on this forum.....by moderators no less.:(

Good luck with the new forum and the continued development of your great piece of software.  That's what the Linux community should be about. :KS

---

### Post by talsemgeest on 2008-04-27
This has completely made my day!

---

### Post by mdpalow on 2008-04-27
> **Phosphoric said:**
> Oh Joy.:)

Well done mdpalow for not bowing down to the shameful way that you have been treated on this forum.....by moderators no less.:(

Good luck with the new forum and the continued development of your great piece of software.  That's what the Linux community should be about. :KS

Thanks Phosphoric! :)


TO ALL MY NEW/OLD FRIENDS - 

QuickStart is technically up and running again on a server where I feel more comfortable giving my support. I love the Ubuntu forum and I KNOW it's more convenient for you to get what you need from there, but as some of you  know this was necessary.

If you'll just bookmark this URL it shouldn't be too much trouble for you to come over and visit every once in a while to see how/what we're doing:

[http://quickstart.phpbb.net](http://quickstart.phpbb.net)  - This will take you to forum

[http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11) - take you to download

Stop in and say hello if you like. I would love to meet up with some of you again.

Best wishes...

---

### Post by jakupl on 2008-04-27
wypii :D thankyou very much :) finally it's back. Now i can get it..

---

### Post by locolobo on 2008-04-30
I am directing this reply mainly to KiwiNZ AND CEGPOPE ..>>
When you make slurs about Mdpalow's 'minnions of praise' you cast
aspersion upon an awful lot of people that you know absolutely nothing
about!! YOUR juvenile behavior leads to serious questions about
your true motives.....:(:(

---

### Post by mdpalow on 2008-05-18
Hi Everyone,

For those of you who might still be watching this thread and not the new QuickStart forum - pls read below.


I've put QuickStart 7.0 on the server if anyone wants to download and use it.

For those that have QS, you can update from program and for those that don't have, pls see the first posting of THIS thread.

One important bit of info:

Please rename all your existing TAR back-up files by placing " tar_ " in front like " tar_home_backup_....."

The reason...

So many different types of back-up files can now be created using QuickStart that it's getting hard to keep alike files together because of previous naming convention. With new update, all alike files will appear in type order first and then by name.

Also, QuickStart is now programmed to exclude "tar_" files from back-ups. If you don't put "tar_" in front, you'll be backing up your tar back-up files, which is redundant and going to make for a very large file. This will only occur if you're back-up files are located on the drive/partition you're backing up. :)

So, if you're using QuickStart 7.0, pls add "tar_" to all your currently existing QuickStart back-ups.

example:   

tar_home_backup
tar_system_backup

---

### Post by Malta paul on 2008-05-24
A big thank you mdpalow for a great program and now even better with version 7.0.06

Paul

---

### Post by 2hot6ft2 on 2008-05-24
Thanks mdpalow for writing such a nice little piece of art. Keep up the good work.
:guitar:

---

### Post by mdpalow on 2008-06-05
> **2hot6ft2 said:**
> Thanks mdpalow for writing such a nice little piece of art. Keep up the good work.
:guitar:

Thanks - will do. :)

---

