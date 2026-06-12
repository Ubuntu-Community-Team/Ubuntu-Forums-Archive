---
title: "looking for help with DVD-burning (Rome was easier) ..."
date: 2005-09-07
forum: General Help
---

### Post by werner2k on 2005-09-07
Hello from Vienna - I need help to create a data-dvd before I return to windows!
I googled the web, searched the forum - no solution found.
The situation: 

DVD-Recorder: LiteOn DVDRW LDW-851S
Worked fine under win2K (burning CD-R and DVD+R)

Ubuntu Hoary 5.04 

cdrecord-prodvd 2.01b31 installed, wrapper-script with key installed, cdrecord renamed, symlink set named cdrecord, pointing to wrapper-script for cdrecor-prodvd
tested by checking version (cdrecord-prodvd responds).

Tested frontends:
gnomebaker 0.3 (new version 0.4.2 not installable due to dependencies) - not acceptable, as no iso-joliet-support (filenames comming from an ntfs-volume are truncated)
graveman 0.3.12.4 - installed with synaptic, Burned Data-CD ok
when burning to DVD+R it responds with "input/output-error" after creating the temporary file.

in /var/log/messages I find only "localhost kernel: cdrom: This disc doesn't have any tracks I recognize!" (deduced from timestamp)

Any ideas from anybody out there? I realy would prefer a gnome-app over k3b.
Is there a way to log errors from cdrecord or the other external programs directed from graveman?

Thnk you in advance!
werner2k

---

### Post by emperor on 2005-09-07
Try "Xcdroast"

[http://www.xcdroast.org/manual/dvd.html](http://www.xcdroast.org/manual/dvd.html)

---

### Post by werner2k on 2005-09-10
Thank you, I will.

By the way, I tried k3b.
I undid my changes with cdrecord (removed the softlink, renamed it back to cdrecord).
Then I installed it with synaptics and started.
It identified the hardware and crashed twice while preparing the files to be written - this was due to an ecoding-error, so I just removed the annoying content.
I clicked again on "Burn" - after 7 minutes of intense hd-activity, it reported "preparing the burn-process"
2.14 minutes later every activity ceased - no timecounter anymore, no switching to alternate tasks anymore - the whole ubuntu was dead!
Only way out - hard-reset.
So k3b goes down the chute, too - or is there anybody who knows of this behaviour?

Thanks again 

Werner

---

