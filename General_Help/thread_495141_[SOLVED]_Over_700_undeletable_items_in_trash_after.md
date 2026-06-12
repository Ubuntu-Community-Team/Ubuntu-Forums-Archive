---
title: "[SOLVED] Over 700 undeletable items in trash after fsck"
date: 2007-07-07
forum: General Help
---

### Post by hydroxic on 2007-07-07
**EDIT: SOLVED, see below post for information.**

Hi, 

I booted up my Ubuntu(Studio) yesterday, and it did a fsck (normal...). However, when I logged in, I noticed that my trash had 702 items in it!!

I tried to delete (empty trash) those items, 
[http://img.photobucket.com/albums/v30/hydroxic/errorDeleting.png](http://img.photobucket.com/albums/v30/hydroxic/errorDeleting.png)

It seems I don't have permission... Another thing I noticed is (I think) they're all from /dev/ (if that means anything). 

Any advice in fixing this?

---

### Post by Megaqwerty on 2007-07-07
Well, I'd be a bit careful about deleting anything in /dev/ but if you want to be able to delete them, you need to be root. So, I'd run gksudo nautilus, and nautilus should open up with root permissions. From there you can navigate to your trash (if I remember correctly it's in /home/username/.trash) and delete the files.

---

### Post by hydroxic on 2007-07-07
Well, I forgot to mention that there is nothing in ~/.Trash ... Already tried that, but thanks anyway. 

I don't know where this "trash" with /dev items is getting it's data...

Wow...that's interesting.... I just decided to try something out: 
I did gksudo gedit /dev/testfile just out of curiosity...
Now, guess what shows up in my trash? 704 items -- the new "testfile" included (I'm guessing the other is "testfile~" (I'm not sure). 

So, somehow nautilus (or GNOME?) thinks that /dev is a trash location?!

What's going on here?!

---

### Post by Megaqwerty on 2007-07-07
I honestly have no clue in light of this new information. Maybe someone else will be able to help.

---

### Post by hydroxic on 2007-07-08
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-vfs2/+bug/85608](https://bugs.launchpad.net/ubuntu/+source/gnome-vfs2/+bug/85608) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**Just an update:**
I did some noodling around... First I looked around on Google to no avail, except that I learned that gnome's trash has something to do with gnome-vfs... 

Next I went searching in gconf-editor for something about it... Finally I looked under my home directory with a ls -a... Looking around in the ~/.gnome/gnome-vfs directory, I discovered a file called **trash_entry_cache**. 

This file seems to handle where your "trashes" are and brings them together when you go to trash: in nautilus. 

Finally, with some googling, I found this bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-vfs2/+bug/85608](https://bugs.launchpad.net/ubuntu/+source/gnome-vfs2/+bug/85608). A post there said to rename/remove the .trash_entry_cache file and restart your GNOME session. I did so, and my "/dev in trash" issue is solved! GNOME created a new .trash_entry_cache and everything is fine :). 

I just felt like posting that in case someone has a similar problem in the future. [Now I only wonder what caused it... I'm assuming the fsck, but I don't have enough experience to say]

---

