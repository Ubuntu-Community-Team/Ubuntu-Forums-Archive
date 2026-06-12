---
title: "Error On Update.. I think"
date: 2007-02-19
forum: General Help
---

### Post by ghandi69_ on 2007-02-19
Hey guys..
However today when I rebooted.. it couldn't start xserver.. it tries a few times then brings up graphical screen that says xserver or whatever failed to start... if I check see error output...it gives me stuff like.
> "Fatal Error running install command for nvidia" & "Failed to load nvidia kernal module"

when I don't check to see more options...

> Fatal I/o error 104
 
is waiting for me at the terminal...

So far.. i have tried using my xconfig.backup file with no such luck..
and I have tried sudo dpkg-reconfigure xserver-xorg.. which asks me a ton of questions and that didn't work..

The only thing that I can remember during my last session was install the updates... but it was a normal user prompted shutdown and was running fine.

Oh, and I'm using Edgy.. and have an nvidia 7600GT graphics card.

Thanks in advance.

---

### Post by ghandi69_ on 2007-02-20
Update...

I have tried removing xorg and the nvidia drivers and gdm by doing...

sudo apt-get remove xorg nvidia-glx gdm

and then reintalling them..

but I get the same error.

---

### Post by dcstar on 2007-02-20
> **ghandi69_ said:**
> 
.......
So far.. i have tried using my xconfig.backup file with no such luck..
and I have tried **sudo dpkg-reconfigure xserver-xorg**.. which asks me a ton of questions and that didn't work..
.......

Do it again and select the "nv" driver, that should get a basic system working.

There are numerous posts in the forum about problems similar to this after the recent updates, I suggest you check them to see who has come up with a solution.

---

### Post by ghandi69_ on 2007-02-20
Will do... but if you happened to stumble upon any.. could you send me a link..

I've been searching and just looking back through pages and pages of threads and havent seen anything remotely similar....

---

### Post by ghandi69_ on 2007-02-20
Ok, I did the nv thing.. which makes it look like nothing is wrong... however... lots of things are still broken...

Whenever I start an application (such as a game.. like astromenace) ... it wont start because it said it can't access a certain resolution(one different than the one I'm running under)

Also.. whenever I do add/remove programs.. or try to use the package manager.. I get erros that read...

> Unable to copy the user's Xauthorization file.

and ideas?

---

