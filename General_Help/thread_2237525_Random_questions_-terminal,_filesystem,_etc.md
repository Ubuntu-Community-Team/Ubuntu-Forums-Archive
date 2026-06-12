---
title: "Random questions -terminal, filesystem, etc"
date: 2014-08-02
forum: General Help
---

### Post by zalvera on 2014-08-02
I'm working through the free EdX Introduction to Linux course and mostly having fun. It's very basic but that's exactly what I need! Only it seems like every time I learn something I end up with even more questions. Help?

First there were the terminal windows. What's the difference between these and the virtual terminals I can open on my desktop? When I switch to one, why do I have to log in again? Why are there six of them? Why not one, or two, or twenty-eight? And what's that mysterious blank display behind Ctrl+Alt+F8? 

And then there were 'symbolic links'. Soft links I think I understand, they're basically the same as a windows shortcut, right? But hard links? You make a copy of the file but somehow it's the same file? What use is that and why would you do it? If you change one does it automatically change the other? What if you whisk one away on a USB and *then* change it and then bring it back, will the computer explode in a fiery ball of paradox?

And then there were filesystems. Oh filesystems, why must you confuse me so? The whole thing starts at '/', root, right? But if I wander down through it I'll eventually come to /dev/sda1, which is my primary partition. How can the partition be *inside* the filesystem? Shouldn't it be the other way around? When I was installing the OS it automatically created a bunch of partitions, I think / is on one and /home and /swap are others and there might be a few more? In the course it mentioned this was a convention to ensure that vital systems would still be able to function if your hard disk filled up. That might have been sensible twenty years ago but is it still necessary in this age of vast hard drives? What would happen if I installed everything on a single partition?

All explanations are much appreciated, thanks!

---

### Post by tamser2 on 2014-08-02
I am responding mostly because I'm eager to hear the answers to some of these myself . Partitions , you can have one , two or as many as you want . I only have root and swap . I think if you have enough ram you probably don't even need the swap , in which case it would be fine to just have one partition . Some use a home partition so that you don't lose your personal files if you reinstall the OS . Hope this helps a little

---

### Post by The Cog on 2014-08-02
> **zalvera said:**
> First there were the terminal windows. What's the difference between these and the virtual terminals I can open on my desktop? When I switch to one, why do I have to log in again? Why are there six of them? Why not one, or two, or twenty-eight? And what's that mysterious blank display behind Ctrl+Alt+F8? 
The terminal (TTY) windows are seen by the OS as six different terminals all connected to the same computer. In the days of minicomputers, this would have been six different terminals at six different desks with six different users. It can be useful for one person to have more than one login though, so Linux allows 6 virtual terminals on the one screen/keyboard/desk. Six seems like a reasonable number. More recently, terminals can display graphics which allows opening several applications (including command prompts) on the one terminal, which is handy. But being one terminal, there is just one person sitting at it, and just one login. Since 1-6 are text TTYs, it is normal for the graphical terminal to appear on 7. 8+ are normally unused, although I have seen 8 used for guest logins sometimes, and you can start a new login for yourself on 8 but I forget how. I posted a command to do it earlier but got it wrong - don't do that if you saw it. 

> And then there were 'symbolic links'. Soft links I think I understand, they're basically the same as a windows shortcut, right? But hard links? You make a copy of the file but somehow it's the same file? What use is that and why would you do it? If you change one does it automatically change the other? What if you whisk one away on a USB and *then* change it and then bring it back, will the computer explode in a fiery ball of paradox?
Hard links existed before soft links were invented. All hard links to one file **must** be on the same filesystem - one disk. This removes the possibility of the universe disappearing in a fiery paradox. In both cases, you don't make a copy of the file, you make a new directory entry pointing the the same file. Like a shop having several entries in the telephone book, under atomobile servicing and under crash repairs perhaps. Well, with a soft link it doesn't point to the file, it points to the real entry. A bit like "Smiths Crash Repairs: see Smiths Auto Services".

> And then there were filesystems. Oh filesystems, why must you confuse me so? The whole thing starts at '/', root, right? But if I wander down through it I'll eventually come to /dev/sda1, which is my primary partition. How can the partition be *inside* the filesystem? Shouldn't it be the other way around? When I was installing the OS it automatically created a bunch of partitions, I think / is on one and /home and /swap are others and there might be a few more? In the course it mentioned this was a convention to ensure that vital systems would still be able to function if your hard disk filled up. That might have been sensible twenty years ago but is it still necessary in this age of vast hard drives? What would happen if I installed everything on a single partition?
Your primary partition is mounted at /, so any files/folders in the primary partition appears under /. But there is a separate partition for users home stuff, and that mounts under /home. This is the normal unix way of treating different partitions (unlike DOS which gives each partition a different drive letter and retains it as a separate filesystem root). If you looked at /home on the primary partition, you would only see an empty directory, and it's only when you mount the other partition that its contents appear insde the /home folder. So you are attaching a subtree to somewhere on the main tree, not making a separate tree root.

You can (and I sometimes do) install on a single filesystem. Two reasons for using a separate home:
* System won't crash if a user fills /home with photos, music, videos, whatever.
* You can do a fresh install of the OS on the root partition without deleting users data. 
I tend to use a large /home for user data, and two smaller / partitions, one for the current OS release and one for the next OS release while I try it out. 

If you installed on a single partition instead of using a separate /home partition then the /home folder in the main partition would contain all the users's directories instead of being empty. The swap partition does not get mounted into the filesystem. It is used by the OS to store copies of page memory, but not as a file system, just as blocks of bytes. 

/dev/ is another filesystem, but it is a virtual filesystem (not on disk at all, it's in the OS's imagination). /dev/contains device drvers, one for each device that the OS has a driver for. It is actually possible to view raw disk contents by reading /dev/sda, raw partition contents by reading /dev/sda1 etc. Do **NOT** try writing to these device drivers unless you know what you are doing. Writing to /dev/sda will overwrite the partition table on the disk. You will find file-like representations of all the computer hardware in /dev. There is also /proc which is another virtual filesystem containing information on every running process, and /sys which contains file-like representation of the running system configuration. You can change configuration (for instance, turn IP packet forwarding on/off) by writing the right values to the right "files" in there.

---

### Post by ajgreeny on 2014-08-02
Bear in mind that everything is a file in Linux, and that does mean everything that is on the computer.  Even your Windows installation, if you have one, will appear as a file in the Linux file system provided it is mounted.
Once you get used to it the layout and hierarchy of the Linux filesystem makes a great deal more sense than that of dos and Windows.

---

### Post by zalvera on 2014-08-02
@Cog - Thank you very much for taking the time to write up such a comprehensive reply. You've helped clear up much of my confusion :) Re this:

> **The Cog said:**
> You can do a fresh install of the OS on the root partition without deleting users data.

How far can you stretch this? I were to install a completely different OS (like Ubuntu > Fedora) and attempted to use my old /home partition with it, would this work fine or work badly or end in fiery computer death?

> **ajgreeny said:**
> Even your Windows installation, if you have  one, will appear as a file in the Linux file system provided it is  mounted.

Yes, I was impressed that linux could see and handle my windows partition just fine - the opposite certainly wasn't true! And you're right, it's really quite logical, it's just very different from what I'm used to.

---

### Post by The Cog on 2014-08-03
> **zalvera said:**
> How far can you stretch this? I were to install a completely different OS (like Ubuntu > Fedora) and attempted to use my old /home partition with it, would this work fine or work badly or end in fiery computer death?
It will work, mostly. Some of the settings stored in your home folder may not be compatible with different versions of the same app. For instance if the two distros ship different versions of gimp. Some of those application settings might point to files that live in a different place and cause the application to be unhappy until you find and clear the old settings out. GUI settings might be particularly troublesome as there can be a lot of them. But all this really just involves finding and removing application settings. 

The biggest difference I can think of is the user ID. Ubuntu numbers its users from 1000 upwards, and it is the user number that gets stored in the filesystem owner and group properties, not the name. Whenever I upgrade, I always do a fresh install rather than upgrade, and I am always careful to add the users back in the same order so they get the same ID. Me, then wife, then child. I think fedora numbers users from 500 up rather than 1000, so you may have to either change your user id to match the existing home ids, or change the ownership id of all the files in /home to match the new id. This example will change the ownershp in /home/zalvera and all its conents to whatever zalvera's new uid and gid are:
```
sudo chown zalvera:zalvera /home/zalvera
```
and the id correction are best done from the tty terminal before doing a graphical login (which may crash since it doesn't own files/folders it wants to use yet).

> Yes, I was impressed that linux could see and handle my windows partition just fine - the opposite certainly wasn't true! And you're right, it's really quite logical, it's just very different from what I'm used to.
Yes, it is both logical and different. The differences run deep and upset a lot of people who are used to windows and think they know all there is to know about "computers". Different OSs have different approaches to the problems that writing an OS present you. 

Here's an interesting one. In Linux, you can delete a file while a program still has it open and is using it. The file continues to exist on disk, maintained by the OS, although it is no longer indexed in any directories. The program can continue to use it until it closes the file, at which point the OS will release the disk contents. Some programs do this to get a temporary file that no-one else can read and that will auto-disappear when the program exits. In windows, a file must have exactly one directory entry. In Linux, a file normally has one directory entry, but can have none (deleted but still used) or several (by using hard links).


I found the command that creates a new graphical login on the Alt-F8 terminal. Log into one of the F1-F6 tty terminals (it's more impressive if you use a different user to the user already logged in on tty7). Then enter the command
```
startx -- :1
```
and it jumps to that user's GUI on tty8. At least, it does for XFCE, and used to for gnome desktops. I guess it probably would for others although Unity does a number of things differently, I gather.

---

