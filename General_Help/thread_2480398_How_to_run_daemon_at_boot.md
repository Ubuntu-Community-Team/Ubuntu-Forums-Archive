---
title: "How to run daemon at boot"
date: 2022-10-28
forum: General Help
---

### Post by mroarty58 on 2022-10-28
I am running Ubuntu 22.04 and have installed "BOINC Manager" to run distributed computing tasks.  I've posted on the BOINC forums and haven't found a solution to my issue there, so trying here.  According to the BOINC forums I need to run the following in Terminal to be able to run the boinc-client daemon at boot:

sudo -i
(to login to root)

update-rc.d boinc-client defaults 98
(to allow boinc-client to run at boot)

I can successfully login to root with the sudo command (after entering my credentials).  I enter the update command and it appears to successfully run (no errors reported).  

However, I continue to need to manually run the boinc-client after a reboot.

Any suggestions on what I may need to do to get the client to run at boot?

---

### Post by TheFu on 2022-10-28
update-rc.d is from 2015.  What you need is a systemd unit file which replaced initd and upstart long ago (in internet years).

There are lots of examples on your system and millions of examples on the internet.  These files typically end in ".service" and are placed in /etc/systemd/ ...... somewhere.  And you get to learn all the new dependencies management techniques that systemd requires.  Oh joy.  Wouldn't it be nice if the systemd unit manager had a dependency called "last"?

[https://www.freedesktop.org/software/systemd/man/systemd.unit.html](https://www.freedesktop.org/software/systemd/man/systemd.unit.html) is one reference from "the horse".  The good news is that systemd unit files are the same on all Linux distros.  The bad thing is that systemd unit files aren't any easier to use than init.d/ scripts and are the same on all Linux distros.

How I miss the simple run-level stuff we had before.  Sigh.

---

