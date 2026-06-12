---
title: "Change UID ??"
date: 2005-10-19
forum: General Help
---

### Post by Ovulus on 2005-10-19
Hi all.

I'm muddling through the baby steps of configuring an NFS network between my Ubuntu box and a couple of Macintosh machines. So far, so good - I can mount the /etc/export/ drives on both macs, but even though the export file is set to read/write permissions, I can only read the contents of the drives.
I've learned that this is most likely due to the fact that the Linux user has a different UserID (1000) than the users on the OS X boxes (both 501).

My question, then, is: can I change the UID (and GID) for the existing linux users? I tried tinkering with the /etc/passwd and /etc/group files, but I'm not sure what I'm doing. Is there a way to change these IDs via the command line? They're grayed-out in the Gnome User Properties window, and I don't want to log in as root to do it if I don't have to.

Any help would be greatly appreciated! Thanks!

---

### Post by Ovulus on 2005-10-20
Well, I figured it out on my own. Used the 'usermod' and 'groupmod' commands (which I should have looked up in the terminal to begin with, I guess) and now all of my read/write permissions work properly across the network.
So, any mac users who are having similar problems - change your userid to match the userid on your mac (of course, this'll only work from one account, I think, but it solves my immediate problem).

By the way, is there a reason why Linux starts the user IDs at 1000 and OS X starts them at 500? Is there any reason I shouldn't have changed it? I don't plan on having more than 2 or 3 accounts on this machine.

---

