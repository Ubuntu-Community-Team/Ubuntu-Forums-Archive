---
title: "[SOLVED] Edgy won't boot with latest update: how fix?"
date: 2007-02-27
forum: General Help
---

### Post by Hopalong on 2007-02-27
I have bug #67256 on a system dual-bootiing with Windows XP. Edgy (6.10) is from a disk downloaded some while ago (December) and automatically updated since.. I've seen the workaround in the Bugs and Workarounds forum, but as a beginner in Linux, I have two questions.  1. Since I can only run Edgy on the CD, how do I do the 'sudo update-initramfs . . . ' bit?, and will it change what's on the disk?  2. If I can't do that, can I save the data off the hard disk system before re-loading from the disk (or a later download)? I don't see how to access the hard disk file system from the CD.

---

### Post by madcow72 on 2007-02-27
Hey hopalong,

To answer your first 2 questions:  The 'sudo ...' line is a command which needs to be entered into a terminal.  You can do this by either going to "Applications -> Accessories -> Terminal"  or by hitting "Alt + F2" and typing "gnome-terminal" into the box that pops up.  Once you're in there, type in ```
sudo aptitude update-initramfs
``` (I think there was supposed to be either an "apt-get" or an "aptitude" in that command, right?) as well as any other lines of code that you need to update.  And no, this won't change anything on the CD.  In fact, everytime you boot up into the live CD, you'll have to recommit the 'sudo update-initramfs' line again.

However, if this is the 1st or 2nd Feisty CD, you may want to download the latest one if you can't get this working.  You may find less headache with the newest version.

To answer the rest of your question, Yes, you should be able to access all of the data on your hard drive while using the live CD.  However, to help you do this, you'll need to know what the filesystem is on your harddrive.  Has it been formatted with Linux to ext3, or does it contain the Windows ntfs format?

---

### Post by Hopalong on 2007-03-03
As I saw it, I couldn't execute the command to change the installed system when running off the CD - right? Nor could I save data, since the CD is my only output device! . . . So I reinstalled 6.10 anyway. Now I am offered auto updates galore, including the new kernel ones: I refused to have those this time round, and can now close and restart Ubuntu. Question: are the kernel updates still dodgy, or could I take them now?
  I'm still keen on Ubuntu, but why is a long story, and doesn't belong here. Thanks.:)

---

