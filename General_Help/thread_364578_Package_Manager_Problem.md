---
title: "Package Manager Problem"
date: 2007-02-18
forum: General Help
---

### Post by clucas on 2007-02-18
I've been messing around with installing Nerolinux. Had some difficulties but it seems to be working ok now. The problem I have is that the Update Icon has an error:

"An error occured, please run Package Manager from the right-click menu or apt-get on a terminal to see what is wrong. The error message was:'Unknown error:'exceptions.SystemError' (E: The package nerolinux needs to be reinstalled, but I can't find an archive for it.)'"

If I run Package Manager I get:

"E: The package nerolinux needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report."

When I click close on that screen, Package Manager shows NO programs at all.

What can I do to get rid of the message? And get the list of programs back.

---

### Post by Xzenome on 2007-02-18
Try *sudo apt-get remove nerolinux*, then install it again. That should sort it.

---

### Post by clucas on 2007-02-18
Tried that. Didn't work. This is what I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package nerolinux needs to be reinstalled, but I can't find an archive for it.

---

### Post by Maestro23 on 2007-02-18
> **clucas said:**
> Tried that. Didn't work. This is what I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package nerolinux needs to be reinstalled, but I can't find an archive for it.

How did you install it?  .deb, .rpm, .tar ?

---

### Post by clucas on 2007-02-18
deb

---

### Post by Maestro23 on 2007-02-18
> **clucas said:**
> deb

Try:

dpkg -r <package.deb>

---

### Post by clucas on 2007-02-18
This is what I get:

sudo dpkg -r nerolinux-2.1.0.4-x86.deb
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

---

### Post by Maestro23 on 2007-02-18
> **clucas said:**
> This is what I get:

sudo dpkg -r nerolinux-2.1.0.4-x86.deb
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

Sorry, try:

> sudo dpkg -r packagename (Leaves config files)

then

sudo dpkg --purge packagename (Removes config files/everything else)


---

### Post by clucas on 2007-02-18
Still no good:

After sudo dpkg -r nerolinux:

dpkg: error processing nerolinux (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 nerolinux


I tried sudo dpkg - nerolinux-2.1.0.4-x86.deb again and got:

Selecting previously deselected package nerolinux.
(Reading database ... 161332 files and directories currently installed.)
Preparing to replace nerolinux 2.1.0.4-1 (using nerolinux-2.1.0.4-x86.deb) ...
/var/lib/dpkg/info/nerolinux.prerm: 31: Syntax error: "(" unexpected
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 31: Syntax error: "(" unexpected
dpkg: error processing nerolinux-2.1.0.4-x86.deb (--install):
 subprocess new pre-removal script returned error exit status 2
/var/lib/dpkg/info/nerolinux.postinst: 70: Syntax error: "(" unexpected
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 nerolinux-2.1.0.4-x86.deb

---

### Post by darkROAM_1 on 2007-02-20
I'm having a very similar problem w/ using the install from this site instead of going to the froswire page. I've tried the ideas from this thread, same results. Here's for a working solution! :D

Edt: found my solution. I used this method of install and it removed the old install and reinstalled fresh. Worked fine for me. I had to make sure I did a perfect copy of the files but, it worked out fine.

[http://ubuntuforums.org/showthread.php?t=305337&highlight=install+frostwire](http://ubuntuforums.org/showthread.php?t=305337&highlight=install+frostwire)

---

