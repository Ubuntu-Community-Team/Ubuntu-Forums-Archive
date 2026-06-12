---
title: "help installing .tgz file?"
date: 2007-09-25
forum: General Help
---

### Post by flats on 2007-09-25
hey all... sorry if this is in the wrong section but dont know where else to turn.

im having a problem installing a .tgz file which dont understand whats wrong. i have my file in the desktop and type "tar -xvzf filename.tgz" and get this strange error...

tar:filename.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors



i dont get it because i do have the directory set to desktop. it does this for other tar files too such as tar.gz...

---

### Post by Maestro23 on 2007-09-25
Yeah, if file is on your Desktop.

> cd /home/username/Desktop

Then run your tar command.

tar xvzf ....

---

### Post by flats on 2007-09-25
ahh that solved my problem thanks :). i thought the desktop was just cd ./desktop guess i was wrong... Thanks again!

---

### Post by Maestro23 on 2007-09-25
> **flats said:**
> ahh that solved my problem thanks :). i thought the desktop was just cd ./desktop guess i was wrong... Thanks again!

No prob man.  Can also get to it like:

>  cd ~/Desktop

*What gets people is that Linux is case-sensitive: **D**esktop instead of deskstop.

---

