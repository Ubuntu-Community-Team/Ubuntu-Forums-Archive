---
title: "re-enable root - sudo istn working"
date: 2016-10-13
forum: General Help
---

### Post by lukas34 on 2016-10-13
Hi
I switched my root account off, using this HowTo: [https://www.maketecheasier.com/hardening-ubuntu-server](https://www.maketecheasier.com/hardening-ubuntu-server)
Now I obviously can't login as root but the account I gave sudo rights can't execute sudo commands.
I get the following error message: 
```
sudo: /usr/bin/sudo must be owned by uid 0 and have the setuid bit 
```set
How can I restore the root account?
help! :( 
luggie

Recovery Mode hat geklärt:
sudo passwd -u root zum wiederherstellen und  
passwd zum erstellen eines neuen passworts.
mein neuer user (wie im HowTo) hat jedoch immer noch keine sudo befügnis. (gleiche fehlermeldung wie vorhin) wie kann ich das erreichen?

---

### Post by Impavidus on 2016-10-13
There seems something wrong with ownership or permissions of /usr/bin/sudo. You can check wit ls -l. This is what I get:```
$ ls -l /usr/bin/sudo
-rwsr-xr-x 1 root root 136808 aug 17 13:20 /usr/bin/sudo
```You can use chown and chmod from recovery mode or from your now enabled root account to fix it.

(Some people would be happier if you used english.)

---

### Post by lukas34 on 2016-10-13
sorry copy/paste from other german forums.
What I said was:
"Recovery mode did it
"sudo passwd -u" root to recover root profile, "passwd" to set new password"

---

### Post by Impavidus on 2016-10-14
Have you checked ownership and permissions of /usr/bin/sudo?

---

