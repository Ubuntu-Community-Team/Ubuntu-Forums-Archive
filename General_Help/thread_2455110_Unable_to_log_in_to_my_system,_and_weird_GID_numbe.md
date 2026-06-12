---
title: "Unable to log in to my system, and weird GID number"
date: 2020-12-12
forum: General Help
---

### Post by tprimke2 on 2020-12-12
I'm a long-time Linux (and Ubuntu) user. A regular user, not an admin, yet I was always able to manage my computer on my own. (BTW, I also managed small Linux servers.)


My personal computer setup: a laptop, with SSD drive (128 GB), single partition.
Ubuntu 18.04 LTS. GDM + LXDE.
Just one user, let's assume it's joe. Of course, joe can become root, with sudo. joe has its own group, named also joe. I believe it's a standard setup for a single-user system.


The computer has been working flawlessly, for almost two years, until today.


What has happend: I have absolutely no idea. I just suspect that something weird has happend to my home directory, or even to my user's group.


What's weird:


1) The computer boots up. I mean everything goes well, and the login (GDM) screen is presented.
Then, when I try to log in (as joe), I can see that the password is correct, and then the screen just "blanks", and I'm getting back to the login screen. It happens every time.


In the log I can see that gdm-password creates a session for the user joe, and then, immediatelly, the session is closed. (I have no idea, why. It shouldn't have been closed at all.)


2) Just before I noticed it, I also noticed something weird: my home directory had the group ID of 999, instead of 1000 (as it should be - the joe GID is 1000).


The group id couldn't be changed back to 1000, even with the joe acting as root (sudo bash). In other words, the commands "chgrp joe file", or "chgrp +1000 file" did not report any errors, and there were no effects.


3) Up to this point, I thought that something weird has happend to my filesystem, to my /home/joe directory, to be precise. So I thought it would be enough to boot the computer from USB stick, and just to fix the group id of /home/joe back to 1000. (And, also, all the other files, and subdirectories.)


I managed to get the root access to the filesystem, but guess what: the gid of /home/joe was already 1000. Just as it should be!


I don't get it: when I access the /home/joe directory, booting my installed system (in the recovery mode, with root console and read-only access to the filesystem), I can see that GID is 999, while booting from the USB stick shows the same directory GID of 1000.


So, my initial plan to just "fix" the GID failed.


4) Working in the recovery mode (or emergency: I mean I have booted to the console, as root, using system from my SSD drive), I managed to remount the filesystem in rw mode (it was mounted in ro mode by default), and to create a new user, joe2, with a new group, also joe2. I gave joe2 access to the sudo command, so the user could work as root.


Then, I was able to login to my system, as joe2. No more "blank" screens, no more getting back to the login form. As joe2, I was able to run the installed software, without any problems.


One thing is weird, though. Even as joe2, I can see that the /home/joe directory GID is 999. joe2, working as root (sudo bash), still can't change this directory's GID back to 1000.


I'm not sure, whether this is the source of the problem. To be honest, I have never experienced such situation, and I've been using Linux since 2002.


I can still try the following trick:
1) rename the joe's home directory to something else than /home/joe (e.g. /home/joe-broken),
2) rename the joe's name to something else, e.g. joebroken,
3) rename the joe2's home directory to /home/joe,
4) rename the joe2 username to joe


and, as I suppose, everything would work the same, as before this weird accident, only the UID and GID would be different, but that's not a problem at all. (Well, I'm not sure about the SSH keys, but I think I could manage it.)


Yet, I would like to know, what really has happend, and whether it can be fixed in some other way.


What do you think? (If you'd like to know some logs, just tell me, where to look for them. I have no idea on what to look at.)

---

### Post by TheFu on 2020-12-12
I think the file system got corrupted.  Check the disk and file systems for problems.  Use fsck and smartctl.

I suspect when looking at the different file systems, perhaps the wrong one was seen.

As to the cause, using sudo with GUI programs can cause this, at least for releases before 20.04. Compare the permissions between joe and joe2 for the top-level dirs and 1 directory below.  Also look in the ~/.config/ directory for both users.

Thanks for saying the release and DE.

---

