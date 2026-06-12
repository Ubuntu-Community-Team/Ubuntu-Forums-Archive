---
title: "Need help with command terminal."
date: 2007-02-19
forum: General Help
---

### Post by insyted on 2007-02-19
How do I view my drives from the terminal such as my cd rom and hard drive?
I would like to go to those drives, and view the contents.

---

### Post by tronica on 2007-02-19
well the contents of you drive are at "/" so,

> cd /

then 

> ls

and your cdrom depends on what its labeled as, for me its

> cd /media/cdrom0

again
> 
ls

---

### Post by insyted on 2007-02-19
what is the default?
So to go to my hard drive, just type:
cd /

and to go to my cd drive type:
cd /media/cdrom0 

Then when I am in the drive, I can view the files by typing:
ls

Is that all correct?
Is there a way to see the disk size and available space from the terminal prompt?
Any basic guides for learning Ubuntu commands?

Thanks!

---

### Post by sb770 on 2007-02-19
Sounds like you are interested in basic Linux commands, which are generally common throughout the Linux world, regardless of what distro you're using (ls is ls is ls, wherever you go).  Just grab Google and search for "Linux commands tutorial" or a variation on that.  Lots of free help out there!

---

### Post by Maestro23 on 2007-02-19
> **sb770 said:**
> Sounds like you are interested in basic Linux commands, which are generally common throughout the Linux world, regardless of what distro you're using (ls is ls is ls, wherever you go).  Just grab Google and search for "Linux commands tutorial" or a variation on that.  Lots of free help out there!

Yep, just google it.  Here is one to get the OP started: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by bodhi.zazen on 2007-02-19
This one is not bad either : [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

---

### Post by steve.horsley on 2007-02-19
> Is there a way to see the disk size and available space from the terminal prompt?
**df -h** is one I use a lot.

---

