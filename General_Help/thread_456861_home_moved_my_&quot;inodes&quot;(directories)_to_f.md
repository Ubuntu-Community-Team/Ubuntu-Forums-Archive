---
title: "/home moved my &quot;inodes&quot;(directories) to /fost+found. How to recover them?"
date: 2007-05-28
forum: General Help
---

### Post by Rooibos on 2007-05-28
Hi,
I'm new in the forum since I tried to look in spanish ubuntu forum, and this forums, google, but I didn't found a solution to my problem.

[PROBLEM]

Some weeks ago my /home decieded to move to /lost+found. (I do not remember any system crash).
Now all the files are into a mess of inodes, every inode like a folder containing files.

I cannot start session with gdm since it says /home was not found.
The directory was deleted/moved too.

[THEORY]

As I supouse inodes are named to be allocated in the right place.
But they didn't return to their original place. That's what I'd like to do.

[AMPTEPMS TO SOLVE IT]

I used fsck options to try to run and force it, but it didn't worked it out.

I've tried to install by command e2salvage tool (despite my /home is in ext3), but it failed when making the
> make
> make install

[SOS]

I do not know what to do next.

Is there any command to ask the inodes to get back to their original place?

Should I create a NEW /home folder so that fsck works? Since this /home would be a new inode, Would it unable the inodes stored in /lost+found to get back to the new /home directory?

Somewhere, some clue, a manual, about how managin with inodes?

Thanks!

---

### Post by ruy_lopez on 2007-05-28
Run fsck on the unmounted volume from a Livecd. Use "df" to find out what device the root directory is on, before you reboot into the livecd.

---

