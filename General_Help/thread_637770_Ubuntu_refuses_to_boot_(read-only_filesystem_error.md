---
title: "Ubuntu refuses to boot (read-only filesystem error)"
date: 2007-12-11
forum: General Help
---

### Post by Volvagia356 on 2007-12-11
I am running Ubuntu 7.10 Gusty Gibbon but I use Vista more often.
Today, I decided to boot into Ubuntu and leave it overnight to update it as they're over 100 updates pending. When I booted everything went well until the loading bar reaches close to the end and this huge amount of errors appeared on the screen about some "Read-only Filesystem" and about stuff failing to load. Then, it just freezes there. There is still keyboard input but no commands I used had any reaction, the only command with a reaction is CTRL+ALT+DEL and that causes the system to send a TERM signal(reboot).

Here's a video of what happened:
[http://www.youtube.com/watch?v=OFJVGzy1KSQ]("http://www.youtube.com/watch?v=OFJVGzy1KSQ")
The quality is low but the text is still readable.

---

### Post by ken_vh on 2007-12-11
What you could do is running LiveCD, opening a console and going to the root folder of your installation.

Then you can run:
find -ctime 5 > output.txt
This will find all files that were changed in the last 5 days and output it to output.txt

You could also use these commandline parameters to find files in specific modes(eg read-only mode):

-perm mode
    File's permission bits are exactly mode (octal or symbolic). Symbolic modes use mode 0 as a point of departure. 
-perm -mode
    All of the permission bits mode are set for the file. 
-perm +mode
    Any of the permission bits mode are set for the file.

More on find:
[http://linux.about.com/od/commands/l/blcmdl1_find.htm](http://linux.about.com/od/commands/l/blcmdl1_find.htm)

The only problem is that this might be a huge list of files. Of course you can eliminte all the directories that are generated/created/altered at startup. Which I think are:
/sys/*
/proc/*


[edit] After looking at your video, I see that you can already see which files can't be changed or deleted because of the permission.
It's not clear to me if the problem is that they should get permission or that something is trying to maliciously get permission.

---

### Post by bingoUV on 2007-12-11
Is /var on a separate partition? Can you boot from a live CD and give the /etc/fstab of your installed system? Also "fsck" your linux partitions from there.

---

