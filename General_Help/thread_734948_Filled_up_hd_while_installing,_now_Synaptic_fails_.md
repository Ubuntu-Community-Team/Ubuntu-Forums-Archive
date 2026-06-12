---
title: "Filled up hd while installing, now Synaptic fails w/error"
date: 2008-03-25
forum: General Help
---

### Post by timzak on 2008-03-25
I'm trying to squeeze as much software on a small hard drive as I can, but it looks like I overdid it and filled up root while in the middle of installing apps through synaptic.  Now synaptic tells me to run dpkg --configure -a, which when I do, doesn't fix the problem.  I cannot load synaptic to uninstall some apps.  I tried manually uninstalling with apt-get remove and that returns the same error that Synaptic gives me.  The exact error is

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

It's an endless loop.  I run dpkg --configure -a and it returns:

> dpkg: failed to write status record about 'xfdesktop4' to '/var/lib/dpkg/status': no space left on device

Can anyone help me remove some apps and get synaptic back?

Thanks.

---

### Post by oligray on 2008-03-25
> **timzak said:**
> run dpkg --configure -a, 


i also had this error and it had nothing to do with space because i had 500 gb 

i never ran dpkg because im a newb and never knew how. I fixed it i think by upgrading the system, basically re downloading and reinstalling.

---

### Post by forestpixie on 2008-03-25
append sudo to the command

```
sudo dpkg --configure -a
```

once that's done run this to see what state drives are in
```
df -h
```

then we can look at clearing some of the apt cache if necessary

---

### Post by forestpixie on 2008-03-25
> **oligray said:**
> i also had this error and it had nothing to do with space because i had 500 gb 

i never ran dpkg because im a newb and never knew how. I fixed it i think by upgrading the system, basically re downloading and reinstalling.

A quick search would have shown you the need for sudo :)

If you are running a command which is going to work at asystem level you need to give the command root rights - sudo for command line things that work in the terminal, use gksudo for things that  are graphical 

eg

sudo apt-get install

gksudo nautilus

---

### Post by timzak on 2008-03-25
Sorry, guys.  This is in Debian and I was using root terminal.  That's why I didn't type sudo.

---

### Post by forestpixie on 2008-03-25
oh ok - clear the cache then

sudo apt-get clean  - or without :)

autoclean will remove packages which can no longer be downloaded, clean clears everything but the lock file

---

### Post by timzak on 2008-03-25
Thanks, apt-get clean worked.  Cleared 500 MB of space.  I had to work from command line because it would no longer let me boot to the GUI because of no memory errors.  I'm trying to sqeeze as much into 1.9 GB root partition as possible. ;)  I'll be more careful next time.

---

