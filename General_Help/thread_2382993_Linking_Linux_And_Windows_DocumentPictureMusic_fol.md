---
title: "Linking Linux And Windows Document/Picture/Music folders"
date: 2018-01-19
forum: General Help
---

### Post by mydroog on 2018-01-19
Hey everyone,

I dual boot Windows 10 and Xubuntu 16.04.3 

I have 3 hard drives: One running windows, one running linux, and one for media storage. In Windows, all my user documents are on the media drive (Documents, Pictures, Music, Downloads, Desktop, etc).

I was wondering how I can link my Linux user folders (specifically documents, downloads, music are important) to this drive, so that I can share what I do in these folders between the two systems?

Thanks in advance!

---

### Post by yancek on 2018-01-19
I'm not sure I understand our problem.  Are you trying to read/write to your Linux system from windows?  Doesn't work with a default windows install as it can not read or write to a Linux filesystem.  There is some third party software which you can install on windows which might be able to do this.  Might try an online search, I've never used any myself.

---

### Post by DuckHook on 2018-01-19
Your best strategy is as follows:

[LIST=1]
[*]Store all your data in an NTFS partition so that Windows—the less capable OS—can access it.
[*]In your Linux install, edit fstab in accordance with instructions in the following thread: [https://ubuntuforums.org/showthread.php?t=2198673](https://ubuntuforums.org/showthread.php?t=2198673)
[*]In your Linux install, make sure all directories that you want to map to their twin in your NTFS partition are empty.
[*]Delete all those *Linux* directories. ***BE CAREFUL***. Make sure you are deleting the empty Linux OSes and not your Windows ones.
[*]Create symlinks for those directories mapped to those on the NTFS partition. If necessary, use the *man* pages and online resources to learn how to symlink. You will only be able to (and should only) create soft links.
[/LIST]
You should now have directories transparently linked to those in your NTFS partition. Anything you store in those directories will now be visible when you reboot into Windows (and vice versa).

Good Luck and Happy Ubuntu-ing!

---

### Post by mydroog on 2018-01-19
> **yancek said:**
> I'm not sure I understand our problem.  Are you trying to read/write to your Linux system from windows?  Doesn't work with a default windows install as it can not read or write to a Linux filesystem.  There is some third party software which you can install on windows which might be able to do this.  Might try an online search, I've never used any myself.

Perhaps my wording is a bit off.

I have Windows OS on a hard drive. I also have a separate hard drive, in NTFS format, used for Data by Windows. It contains my desktop, documents, pictures, videos, and downloads directories. My Xubuntu is installed on a 3rd distinct hard drive. I wanted to have my Xubuntu documents/pictures/downloads/videos/music folders be located on this NTFS data drive, so that I can create documents in there in either OS, and access them on both OSes.

I believe if I mount the drive on Linux boot, and then create symlinks to those folders leading to the data drive, it should achieve what I'm looking for.

I am just uncertain of the commands to do so.

In other words, I have a distinct data drive formatted in NTFS that I want both Windows and Linux to use for the documents, pictures, music, downloads. The windows part is already configured, I want my Xubuntu folders to also be on this same drive and data to be shared.

I hope that makes sense!

---

### Post by DuckHook on 2018-01-19
> **mydroog said:**
> …I am just uncertain of the commands to do so…
Pls read through my post.

---

### Post by mydroog on 2018-01-19
> **DuckHook said:**
> Pls read through my post.

Super helpful DuckHook! That's exactly what I needed and absolutely perfect!

I'm going to do this right now! 

Sorry, I posted after you did. Thanks again, you're a gem!

---

