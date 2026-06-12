---
title: "Change my group / permissions"
date: 2007-05-30
forum: General Help
---

### Post by N/A.. on 2007-05-30
When I tried to install VirtualBox on my Ubuntu 7.04 I used the command
```
usermod -G vboxusers -a myuser
```
in order to add myself to this group.
I think this command changed my permissions or changed my group to vbosusers.

How can I recover my permissions or return myself to the original group.

btw i'm new in linux.

Please help me ASAP because I think maybe to format and re-install ubuntu just because of this.

---

### Post by bapoumba on 2007-05-30
What does ```
groups
``` return ?

---

### Post by N/A.. on 2007-05-30
```
shahar vboxusers
```

(shahar is my username)

---

### Post by Shadoweater12081980 on 2007-05-30
This from Liuxquestions.org

Yes, usermod can change the users groups belonging. when you use usermod username -G list_of_groups you tell the system, which groups the user belongs to.

Just type in the list the user belongs to and leave the ones you don't want the user to belong to, out of the list.

[http://www.linuxquestions.org/questions/showthread.php?t=342389]("http://www.linuxquestions.org/questions/showthread.php?t=342389")

See if that helps :p

---

### Post by ezrollers on 2007-05-30
Have you tried  

usermod -g shahar -G vboxusers

At any rate rather than reinstalling ubuntu, you can always create another user.

---

### Post by rillip on 2007-05-30
I think the only important group you belong to is admin, which you'll need to use sudo.

Here's the output of groups on my install, for comparison

peatheri adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin

---

### Post by N/A.. on 2007-05-30
I tried these: 
```
shahar@shahar-desktop:~$ sudo groups
Password:

```
There was no output after that.

And nothing happend after this one.
```
shahar@shahar-desktop:~$ usermod -g shahar -G vboxusers -a shahar
usermod: unable to lock password file
```

Creating new user will solve the problem? I it will please explain me how.

---

### Post by bapoumba on 2007-05-30
> **N/A.. said:**
> ```
shahar vboxusers
```

(shahar is my username)
From grub menu, please boot in recovery mode. You will be root with a # prompt:
```
adduser shahar admin
reboot

```
Then add yourself in the following default groups:
```
~$ groups
bapoumba adm dialout cdrom floppy audio dip video plugdev netdev lpadmin powerdev scanner admin
```
(except admin and "bapoumba" of course ;))
use the same adduser command, with sudo this time around: **sudo adduser shahar <group_to_be_added_in>**

---

### Post by N/A.. on 2007-05-30
thank you very much...
i'm going to try this now

---

### Post by N/A.. on 2007-05-30
it worked=]

**Thanks for everyone that helped or tried to.**

---

### Post by bapoumba on 2007-05-30
Glad to see you got it to work. And you're welcome!

---

