---
title: "sudo password"
date: 2014-10-26
forum: General Help
---

### Post by kirkcudbright on 2014-10-26
i have just installed version 14.04 from a dvd as a clean install

the password that i gave during installation works ok for the username, software loads ets but when i enter sudo or su then it asks for a different password which i dont know

how do i find out what the sudo password is

---

### Post by lisati on 2014-10-26
Use the same password that you would use to login to your system. Don't panic if there's no visual feedback when you type it in, this is a normal security precaution, just type the password as normal.

---

### Post by sudodus on 2014-10-26
If your installation is correct, you should use your user-ID's password to elevate permissions with sudo, su, gksu and gksudo. If you have several users, at least one of them should have permission to use sudo. The other user-IDs might not have it, but you can add them to the ***sudo group*** and reboot.

- Make a backup copy of the file **/etc/group**

- Edit the file **/etc/group** (the line starting with sudo)

For example, if you want to allow sue to use sudo (the number, 27, will probably be different in your case; do *not* change it, and the user-IDs will be different)

from
```
sudo:x:27:kirk
```
to
```
sudo:x:27:kirk,sue
```

---

### Post by kirkcudbright on 2014-10-26
the file /etc/group contains the line
```
sudo:x:27:terry
```
but if i try su using the password for terry then i get authentication failure

---

### Post by sudodus on 2014-10-26
It seems this is your only user ID. Are you using some special characters in the password, that might be different in the terminal window compared to in the graphical login window?

In that case you can try to change password. If that does not work either, boot into recovery mode and try to reset the password.

[http://psychocats.net/ubuntu/](http://psychocats.net/ubuntu/)

---

### Post by kirkcudbright on 2014-10-26
no special characters - all alpha

---

### Post by kirkcudbright on 2014-10-26
hi again

i may be daft but how do i get into recovery mode
is it pressing an f key while booting

---

### Post by sudodus on 2014-10-26
At least in some systems you can ***press the left shift key during boot***, and you should get the grub menu. From there you can select advanced mode and from there boot in recovery mode.

---

### Post by kirkcudbright on 2014-10-26
hi
i have tried that before but just to make sure i have tried it again and does not work

i beleive that there is a way of getting into the grub menu using the install dvd - can you remind me how to do that

---

### Post by kirkcudbright on 2014-10-26
there is a possible clue
if i go into user accounts the password is shown as five asterics but in fact it is much longer
is that significant

---

### Post by bapoumba on 2014-10-26
Just for my info, please post the outputs to :
```
groups
sudo apt-get update
```

---

### Post by sudodus on 2014-10-26
This link

[https://help.ubuntu.com/community/Grub2/Setup#A.2BAC8-etc.2BAC8-default.2BAC8-grub](https://help.ubuntu.com/community/Grub2/Setup#A.2BAC8-etc.2BAC8-default.2BAC8-grub)

shows which file to edit in order to see the grub menu. You probably have

```
GRUB_HIDDEN_TIMEOUT=0
```

and if that is changed you will see the grub meny. Otherwise if you press the shift key at once, it *should* also work.

You can boot from the DVD and ***mount the root partition of the installed system***, and then edit the file
```

sudo mount /dev/sdax /mnt
``` where **x** is the partition number maybe 1, maybe 5.

```
sudo nano /mnt/etc/default/grub
```

according to the tips in the link above. But you must also get it into /mnt/etc/default/grub/grub.cfg, and that should be done with chroot and update-grub. (You can probably do the editing too in chroot, maybe even change password, but I have not done it.)

[https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot](https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot)

See particularly items

7 - mount (already described above)
11 - chroot
 13 - update-grub

I hope it helps :-)

---

### Post by mc4man on 2014-10-26
> **kirkcudbright said:**
> the file /etc/group contains the line
```
sudo:x:27:terry
```
but if i try su using the password for terry then i get authentication failure
just to check - you can't open a terminal & go su, it has to be sudo su, does the later work?

---

### Post by sudodus on 2014-10-26
> **mc4man said:**
> just to check - you can't open a terminal & go su, it has to be sudo su, does the later work?

good catch :KS

---

