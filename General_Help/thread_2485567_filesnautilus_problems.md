---
title: "files/nautilus problems"
date: 2023-04-02
forum: General Help
---

### Post by jgw on 2023-04-02
I am assuming that files and nautilus are the same thing.  My problem is that files is not behaving.  I cannot, for instance, tell it to show hidden files.  The box is there but it just snaps back and not turn it on.  Same things with preferences.  All options, except for the very first one, do nothing.  The files version is 42.2  I don't know where to fix this stuff!  I also seem to be running into a lot of read only stuff which leads me to think I might have set something that shouldn't have been set.

I have a plain memory stick.  It was fine but, now, no longer accessable:
Unable to access "red63"
error creating mount point '/media/greg/red63':read-only file system

I then "sudo chown greg:greg //dev/sdd1
I gave it my password and it immediately went to awaiting another command (which is how it seems to work when it works)

I then tried to access red63 and got:
Unable to access "red63"
error creating mount point '/media/greg/red63':read-only file system
Tried again and got (same file, same thing):
Error creating temporary file: Read-only file system (g-io-error-quark,21)

Basically, all I can do with red63 is plug it in and out and little else.

Thoughts?

---

### Post by ajgreeny on 2023-04-02
Does ***Ctrl+h*** show your hidden files or is that still unsuccessful?

---

### Post by jgw on 2023-04-04
I am now on a different machine.  On this machine its all dandy with none of the problems above.  On this machine 'files' is the same version.  That being the case I suspect I have screwed up the existing nautilus/files and I should probably delete it and install another.

Next time I get on that other machine (tomorrow) I will try and fix my problem.  

Thank you for the reply!

---

