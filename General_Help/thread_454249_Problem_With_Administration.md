---
title: "Problem With Administration"
date: 2007-05-25
forum: General Help
---

### Post by timr92 on 2007-05-25
All of my Administration interfaces in the System > Administration menu is not working. When i click on it, it asks for my password, which i give it, but then it says "Failed to run *-admin (users-admin/network-admin) as user root"

"The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator."

Anyone have any ideas??

---

### Post by mbradlcu on 2007-05-25
can you tell me what groups you're a member of:
```
groups your_user_name
```
the following account doesn't have any issue with admin proggys, here's the groups output:
> daturan@matt-x64:~$ groups daturan
daturan : daturan adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin fuse
I suspect you'll need to be a member of the "admin" and/or "adm" group.

---

### Post by timr92 on 2007-05-26
i typed in "groups timothy" into a terminal (is that what i needed to do?) and it said "timothy: timothy lpadmin"

---

### Post by mbradlcu on 2007-05-27
this is a little strange, do you have another account that was created during the initial install?
If not, 1 way to add your account to the admin groups is:
start your PC and at the grub menu hit the Esc key,
Select your Ubuntu boot option if needed with the up and down arrows,
use the "e" key to edit the boot options, select the second line "kernel /boot/....."
at the end of the line enter "single" and hit the "Enter" key and the "b" to start to boot process
you should get a root shell prompt now type:
```
useradd -G admin timothy
```
you may need to do add yourself to the 'adm' group too.. I'm not sure,, but after that reboot and you should be able to use the admin tools again

---

### Post by timr92 on 2007-05-27
Nope, i only created "timothy". I tried that and one of the things that i noticed in that console as it was loading was:

```
chown: 'root:utmp' : invalid group
chown: 'root:tty' : invalid group
chgrp: invalid group 'adm'
```

then i did:

```
root@ubuntu-lap01:~# useradd -G admin timothy
useradd -G admin timothy
useradd: unknown group admin
root@ubuntu-lap01:~# useradd -G adm timothy
useradd -G adm timothy
useradd: unknown group adm
```

I also noticed, on my ubuntu desktop this is the output for my groups:
```
timothy@ubuntu-desktop-01:~$ groups timothy
timothy : timothy adm dialout cdrom floppy audio dip video plugdev scanner netdev lpadmin powerdev admin
```

And on the laptop it is just "timothy : timothy lpadmin"

Also, my root user's groups on the laptop comes out as, "root : david"

The user "david" was a user that i created, which started all this mess.

If i do "groups david" on the laptop it says unknown user.

On my Desktop PC, if I do "groups root" it says "root : root"

Hope that helps.

---

### Post by mbradlcu on 2007-05-29
oops,, looks like a give you some bad advice on the adduser usage, it's reversed,, so:
```
adduser timothy admin
```
but it seems you're already a member of the groups authorized to use the admin tools..
try this command and see if you password works to bring up the network gui.. 
```
sudo network-admin
```

---

### Post by timr92 on 2007-05-29
I have already tried that ```
sudo network-admin
``` thing. And the reversed thingy didn't work either.

---

### Post by timr92 on 2007-06-01
should i just re-install my ubuntu installation, or does someone else have an idea?

---

### Post by cordle on 2007-06-08
I have the same problem as this...and when i typed
```
groups stephen
```
"adm" was one of them...but i cant get into any type of application that needs administrator priviledges, despite having tried every password i have ever created on the machine.

i'm using xubuntu 7.04 alternate install (am running it on an old 448MHz Pentium III, 128MB RAM, 8GB HDD) if that makes a difference.

---

### Post by mbradlcu on 2007-06-08
this wouldn't be a proper fix, but either create another account with admin privs or enable the root account. you may want to check out the various /etc/pam.d/common-* files against a working machine. let me know if you don't have a reference and I'll post mine.

---

