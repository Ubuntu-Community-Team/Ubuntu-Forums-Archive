---
title: "Kubuntu hanging on boot"
date: 2006-12-16
forum: General Help
---

### Post by PetePete on 2006-12-16
tried to restart my kubuntu and it wont get past the last little bit on the progress bar, just hangs.

boots into recovery mode fine, but i dont really know what to do to recover it.

is there any repair feature?

I did install sshd, so that might have caused the problem.

Where is the script which boots all the services so i can uncomment some stuff.

cheers

---

### Post by taurus on 2006-12-16
You can remove sshd for now to see if that's the problem after all.  From the recovery mode, run

```
aptitude remove openssh-server
reboot -h now
```

p.s.  Need to watch the language around here, okay!!!

---

### Post by PetePete on 2006-12-16
thanks, will watch the language :D

but it didn't work, helped  a bit, now how a mouse cursor which i can move.

is there a way to see the text output when booting (like in older versions) eg, loading xyz -- ok

---

### Post by matthew on 2006-12-16
I edited your title.

---

### Post by PetePete on 2006-12-16
ta, i edited again to be more specific. ;)

it's still fuc..... messed up though :p

---

### Post by taurus on 2006-12-16
> **PetePete said:**
> thanks, will watch the language :D

but it didn't work, helped  a bit, now how a mouse cursor which i can move.

is there a way to see the text output when booting (like in older versions) eg, loading xyz -- ok

Just remove the "quiet" or both "quiet splash" at the end of the entry for kernel in /boot/grub/menu.lst...

```
sudo nano -w /boot/grub/menu.lst
```

---

### Post by PetePete on 2006-12-16
thanks
very strange, just removed the quiet parts in menu.lst and now it boots perfectly?!!

---

### Post by jbtito03 on 2006-12-20
Hi... i did a KUBUNTU UPGRADE 6.06 -> 6.10.... error after error...

System crash... repaired... after reboot... grub... boot... File system has not /sbin/init or something....

How can i fix this?

Cheers


JB

P.S. Kubuntu upgrade is a mess :(

---

