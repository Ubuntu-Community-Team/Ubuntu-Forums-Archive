---
title: "user + groups issue"
date: 2007-02-21
forum: General Help
---

### Post by theBarge on 2007-02-21
Hi! I'm pretty new to Linux & Ubuntu.  I just set up an installation of 6.10 that I'm going to play around with.  I'm going to use it as an svn repository, and that's where the troubles begin.  I decided to make a new group, "svn", and join that group.  So, in my naivety, I used this command:
usermod --groups svn matt

So, unfortunately, this wiped out my membership in all of my other groups, including admin.  I also don't seem to be able to "sudo" anymore: any command I issue with sudo just returns instantly with no errors.  

Unfortunately I hadn't enabled the root account before I made all these mistakes, and I can't enable it now since I can't sudo, as far as I know.  So, what to do, what to do? Am I totally hosed here?  I'm not too attached to anything on the server, so if it came down to it, I could just re-install.

---

### Post by highneko on 2007-02-21
You could use a livecd to get root privileges maybe? I don't know anything about user groups tho. Good luck.
Here's what the output of the groups command looks like for me. Maybe it'll help:
highneko adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin

---

