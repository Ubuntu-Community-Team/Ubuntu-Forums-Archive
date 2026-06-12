---
title: "Error message on Ubuntu 14.04"
date: 2014-07-13
forum: General Help
---

### Post by mmcl26554 on 2014-07-13
This morning a red dot with a (-) sign in it showed up on the top of my screen.   I right clicked on it and the drop down window among other things said to run ```
apt-get update
``` I did this and at the end got this message:[HTML]Reading package lists... DoneW: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A47958D42B7E03A7[/HTML]
the warning didn't go away.   So update system was also one of the recommended things to do.  I did that and the red dot went away, but when I run```
 apt-get update
``` I still get the same error message.   What does it mean?
Michael

---

### Post by mmcl26554 on 2014-07-13
I fixed the problem with this solution from "AskUbuntu": [HTML]By far the simplest way to handle this now is with Y-PPA-Manager (which now integrates the launchpad-getkeys script with a graphical interface).To install it, first add the webupd8 repository for this program:
sudo add-apt-repository ppa:webupd8team/y-ppa-manager
Update your software list and install Y-PPA-Manager:
sudo apt-get update
sudo apt-get install y-ppa-manager
Run y-ppa-manager (from the dash if you like).
When the main y-ppa-manager window appears, click on "Advanced."
From the list of advanced tasks, select "Try to import all missing GPG keys" and click OK.
You're done! As the warning dialog says when you start the operation, it may take quite a while (about 2 minutes for me) depending on how many PPA's you have and the speed of your connection.[/HTML]
Michael

---

