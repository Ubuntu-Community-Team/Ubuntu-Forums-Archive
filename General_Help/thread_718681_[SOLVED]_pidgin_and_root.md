---
title: "[SOLVED] pidgin and root"
date: 2008-03-08
forum: General Help
---

### Post by StOoZ on 2008-03-08
well I installed the latest pidgin from source, all is fine and working.
now I installed it under /usr/local/bin   which is a root dir.
when I launch it with "sudo pidgin" and then enter the pass it works great.

but if I put it in the sessions list, which where I want it to run at startup , it doesnt run... even with the sudo command , (since I cant give it the pass, I guess, I just call it with "sudo pidgin").
anyhow, any idea how to make it run?
also, even though it is under the /usr/local/bin dir, is there anyway to run it without using the sudo command all the time?
I've just heard that it is better to place programs under /usr/local/bin , and that's why I installed it there.
10x

---

### Post by StOoZ on 2008-03-08
someone? :(

---

### Post by jken146 on 2008-03-08
Don't run pidgin as root.  That's really dangerous.  Install it in /opt and place a symlink to the file *pidgin* in /usr/bin

Then you can use the command "pidgin" to launch pidgin.

---

### Post by StOoZ on 2008-03-08
Ok thanks.
and another question, where is the best place to install softwares where only I will use it?
( I mean in which directory)

---

### Post by StOoZ on 2008-03-08
Solved after doing this : 
> sudo mv /usr/local/lib/libpurple.la /tmp
sudo mv /usr/local/lib/libpurple.so.0.0.1 /tmp
sudo rm /usr/local/lib/libpurple.so.0
sudo ldconfig

thanks all!

---

