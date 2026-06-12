---
title: "[SOLVED] Unmounting truecrypt volumes"
date: 2007-11-06
forum: General Help
---

### Post by a__l__a__n on 2007-11-06
Under ubuntu 7.10, I have created a truecrypt volume in a file which I mount under ~/data and which holds my .mozilla-thunderbird, .ssh, .gnupg, etc.  In my home directory I have created symbolic links to the .mozilla-thunderbird (etc) folders so everything "just works" after mounting the truecrypt volume.

My home directory is in a separate partition. If I forget to unmount the truecrypt volume before shutting down, on the next boot it complains that my home partition was not cleanly dismounted, and performs a filesystem check during boot.  I can try to always remember that manual step during shutdown, but -- hey -- this is a computer!  I want the machine to remember, because sometimes I don't. 

I've created a truecrypt script in /etc/init.d and linked it as K02truecrypt in my /etc/rc* folders in an attempt to be sure the truecrypt volume gets dismounted.  It works beautifully when I test it from a command line:

   sudo /etc/init.d/truecrypt stop

results in "truecrypt -d" and the truecrypt volume is dismounted.  But apparently during a shutdown, it does not dismount the truecrypt voume in time to allow the separate home volume to be dismounted, so I still get the complaint on the next boot cycle about home not being cleanly dismounted.

Any ideas or guidance about how to fix this?

---

### Post by ice60 on 2007-11-06
i mount my truecrypt volume at /mnt/ and never have that problem, you could try mounting there too if you don't and see if it helps.

---

### Post by a__l__a__n on 2007-11-12
I was able to resolve my problem by installing the init.d script with

  update-rc.d truecrypt default

where "truecrypt" is the name of the script I wrote and placed in /etc/init.d to handle stopping of the truecrypt service during shutdown.

I was apparently linking the script at the wrong point in the sequence when doing it by hand.  Now it does dismount the truecrypt volume during shutdown.

---

### Post by Minako on 2007-11-30
*deleted* sorry

---

