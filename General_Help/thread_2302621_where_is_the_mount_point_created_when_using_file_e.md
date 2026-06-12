---
title: "where is the mount point created when using file explorer?"
date: 2015-11-11
forum: General Help
---

### Post by dave205 on 2015-11-11
When I use file explorer (in the gui) to mount my shared files on my home network (windows share), where does the system create the mount point?  I know these aren't permanent mounts as sometimes I connect as admin and sometimes I mount readonly.  

Think of it like this. If this were windows, I'd mount the remote folder as "drive x".  Then I could tell the software to "look on drive x" for the files it temporarily needs. (hope that helps)

I'm not totally new to linux but its been a long time and I'm rusty. :) thanks for any pointers!


edit to add, I type "mount" to see a list of all mounts and I don't see the path to the network share or the name of the share anywhere

---

### Post by TheFu on 2015-11-11
file-explorer mounts use gvfs.  They aren't like normal mounts.
These have moved depending on the release - older releases didn't properly secure them from other userids.

BTW, nautilus is probably the file-explorer being used, so you can look up where they are based on the release you run.  I think they all use the partition label in the automatic mount location.  They could be under /var or /media if my memory is correct.  I don't allow gvfs storage on most of  my systems; don't like end-users having the power to mount storage. Just seems like a terrible idea from a security standpoint.

---

### Post by dave205 on 2015-11-11
bingo!  thank you so much!  now that I know the name of the file explorer, I could do a proper search.  And interesting about gvfs. That's new on me so I have some reading to do.  So I assume that "find" and "locate" doesnt search these directories as I searched for a filename that I know is on the network share and it didnt find it.   apologies for not mentioning the release (15.10) as I surely didn't think it would matter.

nautilus gvfs mounts are here - [COLOR=#111111][FONT=Consolas]/run/user/<userid>/gvfs


[/FONT][/COLOR]

---

### Post by TheFu on 2015-11-11
They moved it again! ;)

**find** should work.
**locate** is not usually configured to index non-permanent or network mounts. Indexing is controlled by the updatedb config file.

---

### Post by coldraven on 2015-11-12
In Nautilus pressing Ctrl+L shows the path to folders. It's handy for copy/pasting paths to or from the terminal. I don't know if it works for networks but worth trying out.

---

