---
title: "ack-grep"
date: 2013-10-17
forum: General Help
---

### Post by Ralph_Cook on 2013-10-17
I am a new Ubuntu user; I have installed ack-grep using "sudo apt-get install ack-grep".  When I attempt to use it, say with "ack-grep 'No valid roles' *.feature", I get the following message:


Use of uninitialized value $ext in split at /usr/share/perl5/App/Ack.pm line 420.


I can see a script named Ack.pm, but I don't know (what I assume to be) Perl, and don't understand what's wrong with either my command or my installation.  Can anyone help me out?

---

### Post by drmrgd on 2013-10-17
That's kind of odd.  I installed it and it seems to be working fine for me.  The error is actually in the Perl Module (hence .pm) that's driving the program.  But, I've tried this on several things and I don't seem to be able to replicate the error.  is there anything special about your *.feature files (odd encoding or something like that?

---

### Post by Ralph_Cook on 2013-10-18
Well, don't know of anything.  Files are edited with vi and gedit and eclipse, I haven't noticed anything that would indicate odd encoding.  I was hoping there was some common newbie install or config mistake that would produce this error, or this kind of error, that folks would recognize.  Thanks for checking.

---

