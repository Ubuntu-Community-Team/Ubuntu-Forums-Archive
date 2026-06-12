---
title: "Automatic iPod backup"
date: 2008-01-28
forum: General Help
---

### Post by kambeishimada on 2008-01-28
I'm in the process of migrating from OS X to ubuntu. I'm looking into how to replace my current backup solution, which is as follows:

1)plug in iPod
2)a script recognizes it has been plugged in and mounts an encrypted sparse disk image stored on it
3)rsync syncs the files in the disk image with the files in my homedir
4)the image is unmounted and the script randomly compacts (defrags) the image 10% of the time
5)the ipod is automatically unmounted, so it will continue to charge but is available for listening to music

This is great, because I can turn on my laptop, plug in my ipod, go get coffee, and come back and immediately start using my ipod. ivman can handle the automatic mounting, and the rsync and unmount portions of the script should work without modification, but the hard part seems to be replicating the whole "sparse encrypted disk image" thing. I've come up with a few options so far:

1) use an encrypted loopback device
obviously won't grow and shrink by itself. I can use dd and growfs if I need it to be bigger later, but in the mean time it's always going to be taking up a sizeable chunk of my disk space. This is the current front runner

2) use tar and aespipe
requires rewriting the entire backup each time

3) use tar in incremental mode, and aespipe
makes restore a pain, and requires additional logic to handle the rotating of the full backup sets.

Anyone have a better solution? Maybe there's a way to mount a sparse loopback file I've missed?

---

### Post by swegner on 2008-03-11
Hi kambeishimada,

I just found your post on a search for a similar query.  While I don't have an answer for you, perhaps you can help me out.  I'm trying to automate synching music and podcasts on my rockbox iPod, and I think what you've described so far would do just the trick.  Do you think you could post your script, so I could use it as a general skeleton for mine?  I've never used ivman before, and they don't seem to have much documentation on the website.  My ideal script would be something along the lines of:

-- Automatically mount the iPod to a pre-defined directory when it's plugged in
-- Sync two different directories to the iPod mount using rsync, and log changes in a file
-- Then, unmount the iPod, so it's available for listening while still charging.

Scott

---

