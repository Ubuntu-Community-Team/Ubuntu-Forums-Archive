---
title: "Copy/Paste in PCManFM"
date: 2013-05-06
forum: General Help
---

### Post by Iggy64 on 2013-05-06
I am running PCManFM 0.9.10 in Precise (12.04) - actually Bodhi Linux 2.0.0.  For whatever reason, I cannot figure out how to copy/paste files or folders using PCManFM.  I right click a folder (or file), then choose Copy.  I then right click a target folder and choose Paste.  Nothing happens.  No error message, no file or folder copies.  I have also tried using Copy and Paste from the main menu, with the same null result.  I have not tried drag/drop because I cannot get the source and target in the same general window.  Yes, I could copy using a Terminal, but some of my path names are very long and tedious.  

Is there some trick to getting PCManFM to copy files?  I haven't found a permissions switch anywhere in its menus.  At least if it would give me an error message, I could learn what I am doing wrong.  Very frustrating.

Are there certain types of files or folders which cannot be copied from or pasted to?  I've tried various types without success.

---

### Post by Iggy64 on 2013-05-06
I have done more experimenting.  I've gotten some simple copying done, and I'm beginning to see that perhaps I was attempting a copy/paste that is not really ordinary.  I was trying to copy a Windows file from a FAT drive to my Linux ext formatted drive.  I guess that's the problem.  I wasn't thinking.  I'll have to learn how to copy a file from a FAT or NTFS drive to my Linux hard disk.  

Specifically, I want to copy Windows files onto a WINE c_drive.  I guess it's more complex than I first imagined.

---

### Post by Bashing-om on 2013-05-06
Iggy64;

Should work as is/// have you perhaps set up mounting the drives in /etc/fstab such that permissions are not set ?

When I re-boot tonight I will test with my lubuntu install and a fat32 thumb drive and get back to ya.
[INDENT=2]
regards

[/INDENT]

---

### Post by Dennis N on 2013-05-06
> **Iggy64 said:**
> ...  I was trying to copy a Windows file from a FAT drive to my Linux ext formatted drive.  I guess that's the problem.  I wasn't thinking.  I'll have to learn how to copy a file from a FAT or NTFS drive to my Linux hard disk.  

It's not the file system types involved, its that you need write permission for the destination folder. A file is just a string of bits, and when you copy it, it is saved in the format of the destination file system.

> **Iggy64 said:**
> Specifically, I want to copy Windows files onto a WINE c_drive.  I guess it's more complex than I first imagined.

Should work if the Wine files are in your home folder where you have write permissions.

---

### Post by Bashing-om on 2013-05-06
Iggy64;;

See Dennis N's last.

I just rebooted into my lubuntu install -- PCManFM version 0,9.10 and did the copy test - from and to PCManFM file manager/home folder - fat32 thumb drive. No problem at all; Either right click copy/past or drag and drop. As advised must be an access and/or file permission issue somewhere in your configuration.
[INDENT=2]
just try'n to help
[/INDENT]

---

### Post by Dennis N on 2013-05-06
> **Iggy64 said:**
>  Is there some trick to getting PCManFM to copy files?  I haven't found a permissions switch anywhere in its menus...Are there certain types of files or folders which cannot be copied from or pasted to?  I've tried various types without success.

There is a permission switch of sorts in pcmanfm to allow you to copy into a folder where you normally don't have write permissions (such as those owned by root, outside your home folder). Use with caution. 

Method:

1) open source folder in pcmanfm.

2) open a new window for the destination folder in pcmanfm which let's say is owned by root.

3) In the window open to the destination, use **Tools > Open Current Folder as Root**.

Enter your password, and a new root window opens up, and you can now paste into this new root window (or drag into it) from the source window.

EDIT: [COLOR="#FF0000"]Warning! This is not a replacement for the terminal's **sudo cp**, and can produce unexpected results. I would avoid it. Use caution. See Post #9![/COLOR]

---

### Post by Bashing-om on 2013-05-06
The use of the "root" PCManFM file transfer is well and good in the short term, however, -and correct me if I am in error - would not those files that are copied then be owned by root ? There by might that not generate additional problems at a later time ?
[INDENT=2]
just a thought 

[/INDENT]

---

### Post by Iggy64 on 2013-05-07
Many thanks for all the advice and education.  Learning Linux is more fun when those with more experience offer their help.  Looking forward to getting home from the job tonight and trying the suggestions.  Will check back in with progress.

Thanks, again.

---

### Post by Dennis N on 2013-05-07
> **Bashing-om said:**
> The use of the "root" PCManFM file transfer is well and good in the short term, however, -and correct me if I am in error - would not those files that are copied then be owned by root ? There by might that not generate additional problems at a later time ?
[INDENT=2]
just a thought 

[/INDENT]

I think you are right about that.

Just did a little test: 

1) Copy an image from Desktop to /usr/share/backgrounds with sudo cp in the terminal. As expected, the copy is owned by root. 

2) Then opened these same two folders using pcmanfm windows and used the Tool> "Open Current Folder as Root" with the destination window, used drag and drop, and find the copy in /usr/share/backgrounds is still owned by me, not root. This was a surprise. Why did they choose to produce this result? I thought it would be doing the same operation as sudo cp.

```
dn@Kayleigh:/usr/share/backgrounds$ ls -l
total 32
-rw-r--r-- 1 dn  dn  8590 2013-05-06 07:53 America.jpg
-rw-r--r-- 1 dn  dn  9290 2013-05-06 08:51 Fragile.jpg
-rw-r--r-- 1 root root 6564 2013-05-07 06:34 Planet-P-Project.jpg

```

First two files copied with PCManFm and the "Open Current Folder as Root". Last file copied with terminal.

Don't think I would recommend using that Tool Option after seeing this.

---

### Post by Bashing-om on 2013-05-07
Well, What I do not know fills a big book, and there are those times when what I think I know is a misconception that flabbergast me !
I too had expected files copied within PCManFM with elevated privileges that the copy have "root" ownership.
 Uhh... permissions and access rights - THE strong point in linux - care and attention must always be applied and the use of "super user" privileges used with discretion.
Not to be used in one's own home directory as it is not needed and when thus used will cause problems
Use the copy command with the appropriate options to maintain proper permissions
As required change to the user rather than invoking super's powers.
I am sure you can think of other caveats also.

As it applies to our present situation; I suggest we look at the permissions on the files to be copied (what ever the source) and the permissions/access rights to the directories that the files are to be copied to. Then make adjustments either to the file's permissions or if these accesses are correct, look at the copy procedure. Bearing in mind that NTFS does not directly support file permissions and we may have to look at how the related partitions are mounted.
[INDENT=2]
all a learning experience

[/INDENT]

---

### Post by Dennis N on 2013-05-07
@Bashing-om

Thanks for your good advice to all.   

In the test, all three image files originally had the same owner and group (dn dn) and permissions 644. 

The destination directory: 

```
dn@Kayleigh:/usr/share$ ls -dl backgrounds
drwxr-xr-x 2 root root 4096 2013-05-07 07:50 backgrounds

```

I never have used the pcmanfm tool - just knew it was there, and wrongly assumed it functioned like sudo cp! Not sure why anyone would want that particular result.

---

### Post by Bashing-om on 2013-05-07
Imagine this if you will... computers back in the sixties,,, There was no such critter as a GUI ! Thus my background was and is a Command Line Interface. The CLI is always my first thoughts and I am not at all as conversant with the GUI tools. That is not to say I am not aware of the GUI, and all my installs have the GUI available and I do avail myself of it on occasion.

Later I will reboot and look at the file permissions on my testing with PACManFM (normal mode) and see if there is a difference in those file permissions too.
Meanwhile, back at the ranch, we await Iggy64's advisement of his status.
[INDENT=2]
hey, it's all to the good

[/INDENT]

---

### Post by Iggy64 on 2013-05-07
Using Dennis N's advice of opening the target folder as root, I finally was able to copy and paste into the target folder.  So apparently that answers the question as to why I was failing to paste successfully - permissions.

I partially understand the concerns other folks expressed about opening folders as root.  In my particular case, this may not be quite as risky as in others, since I am - and always will be - the sole user on this machine.  I suppose that, if I knew more, I might discover that I am still creating risk by doing this.  I guess I will learn eventually.  

For sure, I realize I have to study up a great deal more on permissions in Linux.  As a noob, I am clearly over my head at this point.  But I greatly appreciate the help, the advice, and the cautions offered by everyone in this thread.  Without it, I wouldn't realize how many things I need to study and try.

---

### Post by Bashing-om on 2013-05-07
Iggy64;
Glad that the immediate concern has been addressed. But to be honest, there is the need to look and see why elevated privileges are required and perhaps fix a possible file permission issue.

If you would like to pursue this, please provide us with an example source directory and file, and the destination's directory to see what directory access and file permissions are enabled at this time.

Good foundation materials for comprehension:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251) They are good reads !
[INDENT=2]
best regards

[/INDENT]
[INDENT]
[/INDENT]

---

### Post by Iggy64 on 2013-05-08
Thank you very much for the reference materials.  I want to learn and understand as much as I can.  This permissions thing has certainly been one of the more challenging aspects of learning Linux, for me. 

Also, I will try to take advantage of your kind offer to look at some of my examples.  I hope to have time this evening to put something together.

I really appreciate your help.

---

### Post by Bashing-om on 2013-05-08
Iggy64; Hey,

Not at all a problem to discuss and help (works both ways)..... This is open source and ubuntu...We are all in this together !

See BlinknCat's page(NewDocs) in my sig at the bottom of my post -> Guides to all things ubuntu. Use the "search" box on that page for obtaining extensive information.
[INDENT=2]
curiosity, still the mother of it all

[/INDENT]

---

