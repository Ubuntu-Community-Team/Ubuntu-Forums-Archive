---
title: "Lost /etc/group"
date: 2007-09-26
forum: General Help
---

### Post by darkfluid on 2007-09-26
Seems I made the mistake of looking at the gnome users and groups applet and it cleared out my entire /etc/group file.  Only root and nogroup exist.

Anyway to regen this info?

Thanks

---

### Post by ajgreeny on 2007-09-26
> **darkfluid said:**
> Seems I made the mistake of looking at the gnome users and groups applet and it cleared out my entire /etc/group file.  Only root and nogroup exist.

Anyway to regen this info?

Thanks

How on earth did just looking at the applets clear out your entire /etc/group file? You must have done something to change the file and then agreed to the changes before it was closed.  Let us know exactly what you did, or as much as you can remember, and something may be possible to help.  Also have a look with nautilus to see if there is a backup of the file called /etc/group~ or something similar, which you may be able to restore.  (you will probably have to make sure hidden files are showing in nautilus to see the backup, so Ctrl+h should do that.

---

### Post by darkfluid on 2007-09-26
I opened the users and groups applet under administration as I had noticed some simplistic group permissions assignments in there.  I was trying to use them to get access to sound previously (I've used linux and unix for a while but I'm not used to all this gui and desktop stuff, I mostly worked on servers.

None of my changes were working so I just edited the /etc/group directly, which worked.  A few days later and I can't get access to my video device unless I mod it 666.  Strange since the group already has rw (video) and I'm a member of that group.  Logout and back on...no go, reboot...no go, have to chmod 666 again.  So I figure, hey this goofy thing ignored the gui tool changes ( it didn't modify /etc/group) before, so maybe its some sort of new system where gnome has it's own set of creds...looking back it was desperation and impatience, not logic that drove me to this.  So I open the users and groups, and right click on my user's permissions/group stuff..strangely it's blank and it throws an error saying that it can't find something or other.  Click close and go to /etc/group for one last look..../etc/group is now empty accept for root and nogroup.  

Wish I was lying and actually broke something, but I didn't (purposefully at least).  Now I'm nervious about all the gnome tools, would feel better if I HAD done something stupid.  Think I'll stick to the old bash prompt from now on, since I know how to work under the hood.  Besides, it was annoying that I couldn't add most of the admin icons to my user's menus.  (when I clicked to show them they unclicked themselves a second later...even though those icons use the gksu command)

Thanks for any help, the nautilus thing is blown as I tried to reboot from the livecd to restore...only to remember that I only had the alternate cd on me.  Now gnome won't start due to lack of group permissions.  Booting into bash however and going to /etc/~ shows no backup of /etc/group :(

Downloading the live cd, hopefully I can copy a base from that and fill in the rest.  Might be reinstall time however.

---

### Post by bodhi.zazen on 2007-09-26
You might want to check to see if your editor made a back up copy, typically 

/etc/group~

* Always back up system files before you edit them and keep a copy of the working edited version *

---

### Post by darkfluid on 2007-09-26
I normally make backup copies, but when I just add a name to the end of the group line I don't.  Unfortunately the file was fine after I was last using vim to edit it, I was using less piped to grep to view the groups in question.  It was only after that gnome snafu that it disappeared, so unless gnome backed it up I may be hosed.  Normally I tar the whole /etc tree for backup once a system is set how I wanted, unfortunately this happened at the end of a two day install-fest, I was just shining up the last of my mythtv config when it happened :( .

As soon as the live cd downloads I'm going to try and copy a default /etc/group file and work off of that.

Thanks

---

