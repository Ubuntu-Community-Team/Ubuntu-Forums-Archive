---
title: "Apport file is corrupted, will not upload"
date: 2015-01-02
forum: General Help
---

### Post by ineuw on 2015-01-02
Apport generated a GTK error report on login but could not forward it because the file is corrupt. I checked the /var/crash folder and there was the corrupt file as well as two previous attempts by apport - both of which were empty (this happened before). I managed to take a screenshot of the maximized Apport notice, but I have no idea where to uploaded to. I tried to file a bug report with Ubuntu, but the process is so complex that I got lost. Is there a photo sharing site like pastebin is for text? And how can I report the bug by simply uploading the image because a picture is worth at least a thousand words or so.

BTW, I uploaded the image to [https://wiki.ubuntu.com/Home?action=info](https://wiki.ubuntu.com/Home?action=info) which is probably the wrong place. It's in the list unnumbered but it's the first image of 2015.

---

### Post by ibjsb4 on 2015-01-03
14.04?  Don't think apport is any help.
> During the development release we already collect thousands of crash reports, much more than we can ever fix. Continuing to collect those for stable releases is not really useful
[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

A pic is worth a thousand words, but launchpad has a procedure in place.

Are you actually experiencing a problem?  I do not consider apport a necessary package and have removed it.

If you wish to keep apport, have you tried removing /var/crash/*?

---

### Post by ineuw on 2015-01-03
ibjsb4, thanks for your reply. I have no problems aside from a series of failed apport crash reports - all dealing with lightdm or GTK. I also feel the same way about apport and prefer your judgement and uninstall it. I say this because in November 2014, I installed + reinstalled Xubuntu on six different occasions due to various reasons, i.e: video driver related problems, menulibre crashes, etc., (as I was teaching myself the do's and don'ts of an Xubuntu installation). Each install generated some errors, but I trusted apport to forward the details to Ubuntu. This was the first time that I took the trouble to analyze and realize that apport does nothing.

---

### Post by ibjsb4 on 2015-01-03
Welcome :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

