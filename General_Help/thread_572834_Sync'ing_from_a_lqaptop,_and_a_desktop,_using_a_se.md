---
title: "Sync'ing from a lqaptop, and a desktop, using a server..."
date: 2007-10-10
forum: General Help
---

### Post by masam on 2007-10-10
so i have a server.
ok.

i have a laptop.
i write stuff on it.
shut down.

i have a desktop.
i write other stuff on it.
it stays online.....

how do i successfully "sync" the files on the server?
some files may change on either one, but i want them to be "sync'ed" on the server....
any thoughts?

most of this is going to be "Folder" specific...

(i just changed a few lyrics in [this song - folder])

thinking that SQL is somewhat involved....
not sure what to link, how to make it happen, or if it will be do-able(of course it will!)
help a newbie out huh?!?!
hehe!!!

---

### Post by suffice on 2007-10-10
from what i understand youll have to use rsync -  its a good one directional tool,so long as you then dont want to sync stuff from server to desk/lap....

im in the process of looking it up for myself...

---

### Post by drewlake on 2007-10-11
I was looking into the same thing as well and decided that since the Desktop was going to be on more often than not I would set up folders on the desktop mounted on the laptop using nfs. It works like a charm. If I ever need to use the folders when I'm out of range of my network I can mount using ssh.

---

### Post by masam on 2007-10-12
kewl(rsync), but do i/we have an option to re-sync back to the laptop?

---

### Post by dvenardos on 2007-10-15
Check out this thread:
[http://ubuntuforums.org/showthread.php?t=365253](http://ubuntuforums.org/showthread.php?t=365253)

---

