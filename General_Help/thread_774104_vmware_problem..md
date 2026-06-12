---
title: "vmware problem."
date: 2008-04-29
forum: General Help
---

### Post by Rainstride on 2008-04-29
i tryed to install vmware and the first try had some problem with not being able to copy install files:confused: and when i try to run it again it says theres a previous copy. i was woundering if anyone knows a terminal command i can run to reinstall or uninstall the failed copy(my terminal skill are minimal).iv only been using unbutu a week so any help would be great:D.

---

### Post by tszanon on 2008-04-29
I've read something about it a long time ago, so my instructions may be inaccurate.

Try deleting folders /etc/vmware, if it exists, and ~/.vmware.
In /etc/vmware, there should be configuration files created during the failed install, and in ~/.vmware there should be personal files (I think).

As I said, I don't quite remember. But the point is: delete everything related to vmware that was created during the failed installation.

---

### Post by Rainstride on 2008-04-29
tryed but i dont have permission to be able to delete it. and because i suck at terminal i cant figure out how to delete from there...

---

### Post by rbmorse on 2008-04-29
rainstride, Midnight Commander (mc) might help. It's a fake-GUI file manager similar to the old Norton Commander, if you are familiar with that. It runs in text mode but makes things a lot easier to see, and it's easy to start with root permissions so you can manipulate system files. 

Open your terminal and type

sudo mc<enter>  where <enter> is the <enter> key. Type in your user password when prompted. 

If the nice druid says mc is not installed but you can install it by entering 

sudo apt-get install mc<enter>

at a command line, please do that. When it finishes just type:

sudo mc

at the prompt.

---

### Post by Rainstride on 2008-04-29
worked great, but sadly i got the same problem "Unable to copy the source file ./installer/services.sh to the destination file 
/etc/init.d/vmware." but now i can at least work a little easyer.


im woundering if this is a problem with hardy(bug) or my setup. so im going to reinstall and see if it fixes my problem.

---

