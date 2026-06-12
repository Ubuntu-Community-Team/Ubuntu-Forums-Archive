---
title: "Mounting a volume in Read-Only by default?"
date: 2015-09-02
forum: General Help
---

### Post by Kpenguin on 2015-09-02
Hi everyone,
I need to mount my Windows partition in read-only mode in order to access it from Ubuntu, is there a way to mount it in ro mode by default?

Thanks

---

### Post by TheFu on 2015-09-02
Use the "ro" option in the /etc/fstab entry for the partition you want mounted. [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Kpenguin on 2015-09-03
I'm not seeing the partition I want on the fstab file. The partition I want to mount in ro mode is:```
 /dev/sda4: LABEL="Windows" UUID="4472790F72790748" TYPE="ntfs"
``` but I don't see it on the list. Do I need to add it? If so, please give an example of how since I'm horrible at editing system files properly.
Thanks!
[ATTACH=CONFIG]264207[/ATTACH]

---

### Post by yancek on 2015-09-03
Check the Ubuntu site below, detailed instructions on mounting partitions and if you scroll down to the section "Two special Cases", there is an example for mounting read-only.

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by TheFu on 2015-09-03
> **Kpenguin said:**
>  Do I need to add it?  

Yes.  People new to Linux seem to get stuck on this. (I did too all those years ago) If you are editing a config file and what you need isn't inside already - yes, you need to add it.

Also - please use **sudoedit** for all editing of this type. There are many reasons for this. It is safer. All the places you see *sudo gedit* in how-tos are slightly dangerous. Under some situations, it might prevent a login.  You can review the manpage for both fstab and sudoedit if you'd like to learn more.  man fstab.

I find the lack of explaining manpages in these forums to be a terrible thing.  It is actually against forum guidelines to tell people to look at the manpages - which is the "help" system for all Unix machines, including Linux. People are smart. They can read and will learn to understand a manpage, but not if they don't try.  Just trying to teach people to fish for themselves here. We all get stuck, but if you've read the manpage first, things will get clearer and clearer over time. I promise.

---

### Post by Kpenguin on 2015-09-03
Will sudo nano work okay?

---

### Post by TheFu on 2015-09-03
> **Kpenguin said:**
> Will sudo nano work okay?

I think so - provided it doesn't save settings.  That's the issue.  I don't use nano - actually purge it as the first command after any install. **sudoedit** copies the file to a temporary location, runs the editor specified by EDITOR environment variable under your normal account, then you edit and when you close, it saves the file back to the original with the correct userid/group and all permissions.  Much safer.  GUI editors tend to save settings and when sudo is used, those settings will be owned by root, but stored in your HOME. This can be terrible.

Best to always use **sudoedit** to avoid any of these issues.

---

### Post by QIII on 2015-09-03
Directing people to the man pages isn't disallowed.

What we don't want is threads like:

User1:  I have x problem with y.

User2:  man y

We also don't want LMGTFY or RTFM.  User2's answer is RTFM.

A brief explanation of the answer and what to look for specifically in the man pages and how to use them is most certainly fine.  Just bear in mind that to a new user the man pages may be more inscrutable than the apparent problem.  The man pages presume some basic understanding of the issue and a bit of a sense of what answer to look for.  There really aren't many "man pages for dummies".

And when I direct people to other resources, I always tell them to come back with any questions they may have if they don't understand.

If you want to give an answer like "Type xyz -a in the terminal and post the results.  By the way, you can find out what the -a flag does, and a lot of other options, by having a look at man xyz." that would be great.

Give a man a fish for the current problem.  Teach a man to fish for the next.  Win, win.

---

### Post by Kpenguin on 2015-09-29
I did something wrong because whenever I start Ubuntu, I get a message on the boot screen that says "The disk drive for /dev/sda4 is not ready or not yet present. Continue to wait, press S to skip mounting or M for manual recovery." Here's what I added to /etc/fstab:
```
UUID="4472790F72790748 /dev/sda4 ntfs ro
```
Did I add something I shouldn't have or is my syntax wrong? Please show me exactly what I need to add here.
Thank you very much,
Kpenguin

---

### Post by SeijiSensei on 2015-09-29
> **Kpenguin said:**
> I did something wrong because whenever I start Ubuntu, I get a message on the boot screen that says "The disk drive for /dev/sda4 is not ready or not yet present. Continue to wait, press S to skip mounting or M for manual recovery." Here's what I added to /etc/fstab:
```
UUID="4472790F72790748 /dev/sda4 ntfs ro
```
Did I add something I shouldn't have or is my syntax wrong? Please show me exactly what I need to add here.
Thank you very much,
Kpenguin

First, you have that extraneous quotation mark after the equals sign that should be removed.  

Second, you're probably going to want some more options than just ro.  Take a look at "option one" of [https://help.ubuntu.com/community/MountingWindowsPartitions#Manual_Configuration](https://help.ubuntu.com/community/MountingWindowsPartitions#Manual_Configuration). The "umask=222" parameter grants read and "execute" permissions to everyone, but no write permissions.  The execute permission is required to list files and subdirectories below the mount point.

---

### Post by Kpenguin on 2015-09-29
Thanks everyone for your help everyone! It's working perfectly now!

---

