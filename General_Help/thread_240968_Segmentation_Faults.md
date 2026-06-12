---
title: "Segmentation Faults"
date: 2006-08-21
forum: General Help
---

### Post by Mau on 2006-08-21
I seem to be getting a lot of segfaults lately, but they happen in consistent places, but it's not predictable.  For example, Firefox will segfault for me when I try to parse certain pages using W3C's validator.  However, it will otherwise run normally.

Could this be a hardware problem?  Something leads me to say "no" simply because it happens in consistent places; my thinking is that if it was a hardware issue, it would happen randomly.  But, that just may be wishful thinking.

I'm currently running a memory test (Ubuntu memtest+), and so far I haven't encountered anything, but as I know, that doesn't mean there isn't a problem.

Do you think this could be software or hardware?

---

### Post by kuja on 2006-08-21
I'm no expert, but if it's happening in the same places, predictable or not, I would think it to be software.

---

### Post by leetcharmer on 2007-07-13
I'm getting Segmentation Faults all over the place.  It first happened when trying to do regular updates.  It created Broken packages in Synaptic.  So I removed them, but ever since then, anytime I install stuff or remove, I get pop up messages with cryptic information like this:

> E: samba-common: subprocess post-installation script killed by signal (Segmentation fault), core dumped
E: smbclient: dependency problems - leaving unconfigured
Terminal output says this:
> (Reading database ... 103897 files and directories currently installed.)
Removing gaim-data ...
Setting up samba-common (3.0.24-2ubuntu1.2) ...
dpkg: error processing samba-common (--configure):
 subprocess post-installation script killed by signal (Segmentation fault), core dumped
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 3.0.24-2ubuntu1.2); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 samba-common
 smbclient
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up samba-common (3.0.24-2ubuntu1.2) ...
dpkg: error processing samba-common (--configure):
 subprocess post-installation script killed by signal (Segmentation fault), core dumped
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 3.0.24-2ubuntu1.2); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured

Know how I can fix this?

---

### Post by leetcharmer on 2007-07-13
I fixed it!  Open up the terminal and type in these lines, one at a time :D

sudo apt-get update
sudo apt-get install -f

---

