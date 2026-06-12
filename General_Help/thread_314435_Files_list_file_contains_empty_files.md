---
title: "Files list file contains empty files"
date: 2006-12-07
forum: General Help
---

### Post by Nequeo on 2006-12-07
Hello Ubunteros,

I would like to ask a quick question - and then follow up with a rather more involved story of why exactly I am asking this question, and what I have tried thus-far to solve it.

This question is this. I cannot apt-get install, remove or upgrade anything at present. Each time I do it fails with a message along the lines of:

"Files list file for package 'gnome2-user-guide' contains empty files". How can I fix this? It seems to me that reinstalling gnome2-user-guide would solve my problem. But this error prevents me even from removing gnome2-user-guide with a "dpkg --remove --force-all"

Now with that out of the way, let me tell you a story...

A couple nights back I turned on my PC. It booted fine to GDM just fine, but as soon as I logged in some of my panel applets crashed. Then the application crash reporter kicked in... and it crashed too. Then I got an error message from other panel applets about some png files not being available.

Well, I dimly recalled installing an update for libpng recently, and thought maybe that had gone bad. I tried to open a terminal, but couldn't. So I switched to the virtual console and tried an apt-get update. It seg-faulted.

I rebooted into single-user mode, and during the boot process fsck ran. It reported a whole lotta errors and "repaired" them for me. Almost. After resizing some inodes, and trying to clean up multiply claimed blocks, the whole machine shuddered to a halt with a Kernel Panic.

At this point I suspected my brand new shiny hardware had gone bad. I ran memtest86, and sure enough during the very first test it lit up red and errors scrolled off the screen. 

So now I have replaced my RAM (under warranty, thankfully. Please steer clear of cheap, generic RAM lest the same thing happen to you!). The system once again boots and in most respects seems to function fine. But *something*, somewhere, was damaged by the fsck.

When I tried to install my updates the other night, it failed with the message "files list file for gnome2-user-guide is missing newline at end of file". So I opened up the file list, and not only was the newline missing, it had been replaced by a huge chunk of garbage. I put the newline back in, but now get the error message I described above. 

Any ideas? I survived a dist-upgrade from Dapper to Edgy without major problems. So after that, an fsck running on a root with data-corrupting RAM shouldn't be a problem, right... Right?

Regards,

---

### Post by Nequeo on 2006-12-07
...never mind.
[http://speeves.unt.edu/newindex/?p=90](http://speeves.unt.edu/newindex/?p=90)

---

