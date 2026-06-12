---
title: "How to boot init 3/runlevel 3 at booting"
date: 2006-08-07
forum: General Help
---

### Post by satimis on 2006-08-07
Hi folks,

What shall I add to grub at booting to boot, temporarily/one time, init 3/runlevel 3, just "init 3" or "3".  I tried both of them but they seemed not working still boot to the login page.  TIA

B.R.
satimis

---

### Post by sulobanks on 2006-08-07
Use your favorite editor to edit /etc/inittab (as root).  A few lines down from the start of the file is a line that reads id:2:initdefault.  Change the 2 to a 3 and you're set.  Then after the next boot, just go back and change it back to 2.

---

### Post by mlind on 2006-08-07
I think runlevel 3 is pretty much same as 2, unless you've defined your custom setup as runlevel 3. Ubuntu uses runlevels 1 and 2 by default, where 1 is single-user and 2 is multiuser environment.

To temporarily boot on runlevel 1, append **1** as kernel parameter by editing grub menu before you execute a boot target.

---

### Post by satimis on 2006-08-08
Hi mlind,

> To temporarily boot on runlevel 1, append **1** as kernel parameter by editing grub menu before you execute a boot target.It worked on FC5 only.  I have no problem there.  But I could not boot init 1/2/3, etc one time on Ubuntu.

B.R.
satimis

---

### Post by mlind on 2006-08-08
> **satimis said:**
> Hi mlind,

It worked on FC5 only.  I have no problem there.  But I could not boot init 1/2/3, etc one time on Ubuntu.

B.R.
satimis

huh? I know that you can get to runlevel 1 this way on Ubuntu, I've done it several times myself.

---

### Post by satimis on 2006-08-08
> **mlind said:**
> huh? I know that you can get to runlevel 1 this way on Ubuntu, I've done it several times myself.Yes, single user mode

satimis

---

