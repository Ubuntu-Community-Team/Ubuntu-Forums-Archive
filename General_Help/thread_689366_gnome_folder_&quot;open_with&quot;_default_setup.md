---
title: "gnome folder &quot;open with&quot; default setup ?"
date: 2008-02-06
forum: General Help
---

### Post by lhoffmeyer on 2008-02-06
Hey all,

I have some folders on my desktop that I wish to create some special commands
for.  Currently, I have added a "open with" command that when I right click the
folder I can open the folder with a Full screen F-Spot program.

I would like to make this the default action for only these folders only when I
double-click (or perhaps) single-click on them with the mouse.

any ideas or programs that I can use to accomplish this task?

Lance

---

### Post by lhoffmeyer on 2008-02-08
Well,

Never did figure out how do accomplish the task so I opted for an alternate
solution.

I wrote a bash script 

if df | grep -q '/pub'
        then
           echo "Found mount point, running task"
           timidity "allblues.mid"
        else
           xmessage "Aborted because the disk is not mounted"
           # Do some error correcting stuff
           exit -1
fi

and created a launcher instead of trying to modify certain folder behaviors.

Lance

---

