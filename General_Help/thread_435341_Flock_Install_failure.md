---
title: "Flock Install failure"
date: 2007-05-06
forum: General Help
---

### Post by JimS on 2007-05-06
...
I'm having trouble installing Flock.
I have downloaded flock-0.7.13.1.en-US.linux-i686.tar.gz 
and copied it to my desktop.
When I run in my Edgy box

In terminal I run
-desktop:~$ tar xzvf flock-0.7.13.1.en-US.linux-i686.tar.gz
and I get
tar: flock-0.7.13.1.en-US.linux-i686.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Don't understand why it doesn't find the directory and file.
I can see it sitting on my desktop.

JimS
...

---

### Post by asipi on 2007-05-08
rights are ok?
ls -l flock* what says?

if rights are ok try to download again

---

### Post by maninsitu on 2007-12-16
In terminal try:

tar -C /home/yourusername -xzvf flock-*.linux-i686.tar.gz

Replace yourusername above with your user name. Got these instructions from the Flock FAQ: [URL="http://www.flock.com/faq/how-do-i-install-flock-on-linux"]

It installed but I am having other problems have to ensure that:

Before you install Flock on Linux, please note:

* The Flock binaries are only for GNU/Linux on x86
* libstdc++5 is required

---

