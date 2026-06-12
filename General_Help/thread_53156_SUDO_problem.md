---
title: "SUDO problem"
date: 2005-07-30
forum: General Help
---

### Post by proxess on 2005-07-30
everytime i try to use SUDO i get this:
sudo: must be setuid root

and if i try to open a root terminal i get this:
Failed to run /usr/bin/x-terminal-emulator:
Child terminated with 1 status

how can i fix this??


-Proxess

---

### Post by amohanty on 2005-07-30
post the result of:
>> ls -l /usr/bin/sudo

If the output does not look like this:
-rwsr-xr-x  2 root root 95288 2005-06-21 05:46 /usr/bin/sudo

possibly you screwed up somewhere... :) Dont worry, everybody does it.
The _s_ (fourth letter from left) is the suid thingy thats being mentioned by the message.

I am not sure about this, but try to drop into the recovery mode from grub and at the shell prompt type:
>> chmod u+s /usr/bin/sudo

HTH
AM

---

### Post by proxess on 2005-07-30
well i formated my ubuntu partitions anyhow cause it didnt make much difference from my last screw up. when we are newb, we screw up a lot i guess.

anyhow i'll remember this if i screw up in the same way. thanks

-Proxess

---

