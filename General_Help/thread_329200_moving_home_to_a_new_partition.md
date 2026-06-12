---
title: "moving home to a new partition"
date: 2007-01-01
forum: General Help
---

### Post by andyp11 on 2007-01-01
I'd like to move my home from / to a different partition - hda9, already mounted, but not from a fstab entry, on /media/hda9. I know the guide on [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome) of which this is a distillation. But without using a live cd or anything, is this right? and would it muck anything up and if all working well then I just delete the old home dir?

#in a terminal
cd /home
#then
find . -depth -print0 | sudo cpio --null --sparse -pvd /media/hda9/
#Then add this to fstab (which otherwise doesn't mention hda9)
/dev/hda9 /home ext3 nodev,nosuid 0 2
#then reboot

What do you reckon?

---

### Post by moma on 2007-01-01
It's better to rename the old /home before you replace it with /dev/sda9.
Do this:

$ [COLOR="Green"]cd /home[/COLOR]
$ [COLOR="Green"]find . -depth -print0 | sudo cpio --null --sparse -pvd /media/hda9/[/COLOR]

# Check the ownership of the files on /media/hda9/.  
# Who owns the files after the copy, you or the root?
$ [COLOR="Green"]ls -la  /media/hda9/ | less[/COLOR]
$ [COLOR="Green"]ls -la  /media/hda9/username | less[/COLOR]

# If the file ownership is wrong, fix it with this command.
$ [COLOR="Green"]sudo chown -R username:username /media/hda9/username [/COLOR]
# Replace "username" with your login name.

#Then add this to fstab (which otherwise doesn't mention hda9)
[COLOR="Green"]/dev/hda9 /home ext3 nodev,nosuid 0 2[/COLOR]

# Rename the old /home to /home-old. This command will terminate the X-windows and put you on the command line. It's single-user mode (or maintenance mode).
$ [COLOR="Green"]sudo init 1[/COLOR]

# Rename the old /home.
[COLOR="Green"]mv /home  /home-old[/COLOR]

Create new mount-point for /media/hda9/ -> /home
[COLOR="Red"]mkdir /home [/COLOR]

#then reboot
[COLOR="Green"]reboot [/COLOR]

My recommendation is that you change the fstab line to:

> /dev/hda9   /home     ext3    defaults        0       2

---

### Post by andyp11 on 2007-01-01
a very detailed response thanks v much.

Will study to understand what it all does and then try it out.

Cheers

---

### Post by andyp11 on 2007-01-01
Well, that all worked beautifully.

Cheers

---

