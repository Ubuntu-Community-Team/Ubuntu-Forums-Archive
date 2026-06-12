---
title: "Quick help with rsync"
date: 2020-05-14
forum: General Help
---

### Post by goemonburo on 2020-05-14
I am in the complicated process of backing up a system that failed (Lubuntu 18.04LTS, Dell Studio XPS 8100), and having mounted and unencrypted my way to the home directory I am now trying to back it up.

I am using rsync (first -a and now with -trlzu) to try to copy the newly chrooted encrypted home dir, and get all the files.

What's baffling me is that when I view the original files with the window manager and choose "sort by modification time" I get them the way I want:  a jumble that goes from last to first...so the files I was working on yesterday are on the top.

Yet when I use rsync -a or rsync -t, it seems that this critical time info is lost.  Since when I choose to "sort by modification time" all I get is an alphabetical list in the newly created folder.

I would love to preserve all this info and feel like this SHOULD be done by -t.  Obviously, I'm not getting something.  I thought perhaps that info was lost since I mounted the home dir on a /tmp to access it...but it seems to have all that info properly in the original.

Any suggestions or help would be great.  Thank you!  :-)

---

### Post by goemonburo on 2020-05-14
(And sorry, that should be Lubuntu not Kubuntu in the thread list...must have clicked on the wrong one in the dropdown!)  I'm on Lubuntu!

---

### Post by deadflowr on 2020-05-14
> **goemonburo said:**
> (And sorry, that should be Lubuntu not Kubuntu in the thread list...must have clicked on the wrong one in the dropdown!)  I'm on Lubuntu!

Fixed

---

### Post by oldfred on 2020-05-14
What file system are you copying data to. Ext4?

---

### Post by goemonburo on 2020-05-14
I went back to the folder and oddly, though I'd swear it wasn't sorting by time before, it is now.  So I'm not thinking I need help after all.

---

### Post by rbmorse on 2020-05-14
Maybe the file browser doesn't always refresh until switched to another directory and back?  Nautilus on Gnome is like that sometimes.

---

### Post by TheFu on 2020-05-14
Don't mount to /tmp/!!!!!  That's a terrible place.  All sorts of processes write to that location, using root authority.

For temporary mounts, use /mnt/

I use ```
sudo rsync -avz {source}/ {target}/
``` all the time.  Rerunning the command over and over to refresh the target from the source.  rsync does NOT delete any files in the {target}, unless specifically asked to do so.  Chances are, with the storage mounted on /tmp/ that files are being created and written all the time.

Which file system is the target using?
How much data are you dealing with?

---

