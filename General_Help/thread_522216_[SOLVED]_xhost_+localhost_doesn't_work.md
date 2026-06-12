---
title: "[SOLVED] xhost +localhost doesn't work"
date: 2007-08-10
forum: General Help
---

### Post by dcroxton on 2007-08-10
I have two problems with xhost that have been bothering me ever since I started using Ubuntu back at Hoary.  I would really like to find a solution to them.

(1) The command "xhost +localhost" doesn't work.  It says it works, but I cannot open graphical applications as the root user (e.g., synaptic).  The only way I can get it to work is to use "xhost +", which everyone emphatically says you shouldn't do.

(2) I want to allow root to run graphical programs automatically, so I don't have to issue an xhost command every time.  This seems pretty basic.  I've seen the suggestion to put the xhost command in xinitrc, but that does not work.  Even when I insert the line "xhost +", I still start out unable to run graphical programs as root until I type "xhost +" in a shell.  (I just noticed that the first line of xinitrc is "#!/bin/sh", and I've used other shell files that say to change it to "#!/bin/bash"; could that cause the problem?)

Thanks for any help,
Derek

---

### Post by PaulFr on 2007-08-11
Okay, here are my answers:
1. ```
xhost +local:
```
2. If you are running bash, then put the following in your **~/.bashrc** file:```
# If this is an xterm turn on xhost permissions for local users
case "$TERM" in
xterm*|rxvt*) xhost +local: >/dev/null 2>&1 ;;
*) ;;
esac
```

---

### Post by dcroxton on 2007-08-13
That's a great help, thanks.  What file would I need to put it in so that xhost +local: runs every time I log in, not just if it's an interactive terminal?

---

### Post by PaulFr on 2007-08-13
I guess I did not understand your question: Do you want to

a. Run xhost +local: automatically for any user when they login, or
b. Run xhost +local: automatically for me when I login, or
c. Run xhost +local: for non-interactive terminals or non-xterm terminals ?

a. makes sense, and is achieved by editing **/etc/profile** and adding the code I posted in my answer 2 in my earlier post.

b. makes sense and is what I answered in answer 2. Edit **~/.bashrc** and add the code in answer 2.

c. I do not understand the point of this. xhost +local: has to be run by a user who has ownership of a X server - the basic idea being that user gives permission to other users. Still if you do want to do this, you can change the code I put in answer 2 to be just ```
# turn on xhost permissions for local users
xhost +local: >/dev/null 2>&1
```Hope this helps.

---

### Post by dcroxton on 2007-08-14
Thanks, (a) is what I was looking for, I think.  The thing is that .bashrc doesn't run when I log in via the usual Gnome graphical login, at least by my understanding.  I just wanted something that would be run automatically when I log in, not just when I open a shell.  This seems to answer my question.

Thanks for your help.

---

### Post by bodhi.zazen on 2007-08-14
> **dcroxton said:**
> I have two problems with xhost that have been bothering me ever since I started using Ubuntu back at Hoary.  I would really like to find a solution to them.

(1) The command "xhost +localhost" doesn't work.  It says it works, but I cannot open graphical applications as the root user (e.g., synaptic).  The only way I can get it to work is to use "xhost +", which everyone emphatically says you shouldn't do.

(2) I want to allow root to run graphical programs automatically, so I don't have to issue an xhost command every time.  This seems pretty basic.  I've seen the suggestion to put the xhost command in xinitrc, but that does not work.  Even when I insert the line "xhost +", I still start out unable to run graphical programs as root until I type "xhost +" in a shell.  (I just noticed that the first line of xinitrc is "#!/bin/sh", and I've used other shell files that say to change it to "#!/bin/bash"; could that cause the problem?)

Thanks for any help,
Derek

To run graphical programs as root you can always use gksu:

```
gksu synaptic
```

---

