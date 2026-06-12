---
title: "Not in sudoers file + no root account"
date: 2005-07-20
forum: General Help
---

### Post by zacman on 2005-07-20
Just installed hoary on my new laptop...

X.org isn't working but i figure my xorg.conf file just needs some tweaking, so i logged into a terminal but i found that i can't use the sudo command.  I get the message "(my username) is not in the sudoers file. This incident will be reported."  I can't view or edit /etc/sudoers because i have no root account enabled... even though i specified a root password durring "expert" installation.

Any help much appreciated - Thanks

---

### Post by az on 2005-07-20
boot into recovery mode (hit escape if the grub menu is not revealed for you at boot time)

cat /etc/sudoers

It will let you know who has sudo priviledges.  Perhaps you misspelled your username?



From recovery mode do:

dpkg-reconfigure xserver-xorg

and then 

init 2

That's a good way to reconfigure x anyway....

---

### Post by Juergen on 2005-07-20
You can boot into single-user ('recovery-mode' , normally the 2. linux-entry in Grub menu) and then:
```
EDITOR=pico visudo
```
Now just copy the line for root and change one root to your username.

Then 'reboot' - sudo should work.

---

