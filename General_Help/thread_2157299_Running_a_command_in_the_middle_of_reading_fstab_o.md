---
title: "Running a command in the middle of reading fstab on boot?"
date: 2013-06-24
forum: General Help
---

### Post by Ranko Kohime on 2013-06-24
Is there a way to set a command to be run at a specific part of the boot process, such as right in the middle of mounting drives in the fstab, and have mounting paused until the command returns a 0 exit value?

---

### Post by oldfred on 2013-06-25
I doubt if you can stop fstab in the middle as it is just one command mount that loads it.

But you could remove mounts from fstab if not the main system and load them with a script.

 Startup script is:
/etc/rc.local

---

### Post by Cheesemill on 2013-06-25
If you can let us know exactly what it is you're trying to achieve then there are probably other solutions. As oldfred mentioned above it isn't possible to run a command in the middle of mounting the contents of your fstab.

---

### Post by Ranko Kohime on 2013-06-25
My use case is that I have two drives, an SSD as /dev/sda, and a hard drive as /dev/sdb.  /dev/sda is currently encrypted, and serves /boot and /.  /dev/sdb is also encrypted, and provides /home.  there is a key file for /dev/sdb in /root, so I unlocked /dev/sda with a password and /dev/sdb automatically unlocks thereafter.

I'm planning on removing the encryption on /dev/sda when I upgrade here shortly, but I'm trying not to use a password for /dev/sdb.  So I've got the idea to keep the key file on my Ironkey, which requires mounting /dev/sr0, running the unlocker, then mounting the now available /dev/sdc, and thereafter mounting the decrypted side of /dev/sdb to /home.  (all of this, prior to login, of course)

---

### Post by Ranko Kohime on 2013-06-27
Another thought occurs, is it possible to have a script run exactly after the fstab is handled, and before anything else?

I could set /dev/sdb and /dev/sdc to 'noauto', and just mount them in a script afterwards.

---

### Post by Ranko Kohime on 2013-06-28
Bump to see if the last question can be answered.  :)

---

### Post by Lars Noodén on 2013-06-28
You might take a look in /etc/init/mountall.conf to see if that is what mounts everything.  If so, you could have it trigger your script.

[http://upstart.ubuntu.com/cookbook/](http://upstart.ubuntu.com/cookbook/)

---

