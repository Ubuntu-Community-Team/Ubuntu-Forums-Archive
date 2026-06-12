---
title: "Continual errors even after reinstall"
date: 2018-02-23
forum: General Help
---

### Post by scott19998 on 2018-02-23
Last night I performed some updates and somehow my battery came loose and I was not plugged in.  When I restarted I received a notification of an internal error and the screen went to a teal green color.

I restarted a few times and each time it seemed to progress to a new screen and eventually I arrived at a limited desktop but without the left sidebar.  The only thing I could really do is right click and open a command box.  I tried a command update and that didn't help.

Eventually, after reading many forums, I tried a reinstall while saving my home file.  That didn't work and the error(s) persist.

As I'm short for time (I have work to do), I just backed up my personal docs and went for a new clean install.  I reinstalled (overwriting).  After restart I received an error that I have an internal error.  I tried downloading some software and it just thinks and thinks, nothing progresses.

I don't understand how an error can persist on a new clean install.

I just tried to update the OS and I received a warning that I have a system problem.  I tried to open it to copy what it says and it locks up.  Before, it seemed to download the entire OS update and when it tried to implement it I rec'd the error.  Now it still shows that it needs an update.  I try and update it again and nothing happens when I click the install button.  I tried installing other software and it shows "installing" but nothing happens.

I just did a restart to see if it persists and towards the end of the restart I got this:

"System program problem detected"

Details Action: com.ubuntu.apport.apport-gtk-root
Vendor: Apport

"Sorry, Ubuntu 16.04 has experienced an internal error.
If you notice further problems, try restarting the computer.
ExecutablePath
/usr/lib/snapd-glib/snapd-login-service

This is exactly the error I got after the system crashed.  Don't understand how this can persist if I did a clean install.  ???

---

### Post by scott19998 on 2018-02-23
I tried this:
sudo apt update
sudo apt upgrade
sudo apt full-upgrade

from here:

[https://ubuntuforums.org/showthread.php?t=2385262&highlight=apport+error](https://ubuntuforums.org/showthread.php?t=2385262&highlight=apport+error)

and it seemed to fix it :-)

I had previously tried the first two lines with no success it seems that the "full-upgrade" fixed it.

---

