---
title: "problems with update linux-headers-3.2.0-55-generic 3.2.0-55.85"
date: 2013-10-27
forum: General Help
---

### Post by christian-matthees on 2013-10-27
By today I started to update my system Ubuntu 12.04 with the paketmanager. Now the system hangs since 2 hours and don't go ahead with the update.
It's a dual core system: The whole time one cpu is at 100%.

*dpkg.log
2013-10-27 08:37:36 configure linux-headers-3.2.0-55-generic 3.2.0-55.85 <none>
2013-10-27 08:37:36 status unpacked linux-headers-3.2.0-55-generic 3.2.0-55.85
2013-10-27 08:37:36 status half-configured linux-headers-3.2.0-55-generic 3.2.0-55.85

What could I do to complete the process?
What's the reason?

Thanks for helping

* df -h
Dateisystem    Größe Benutzt Verf. Verw% Eingehängt auf
/dev/sda1       143G     28G  108G   21% /
udev            1,9G    4,0K  1,9G    1% /dev
tmpfs           778M    1,2M  777M    1% /run
none            5,0M       0  5,0M    0% /run/lock
none            1,9G    268K  1,9G    1% /run/shm

 df -i
Dateisystem     Inodes IBenutzt   IFrei IUse% Eingehängt auf
/dev/sda1      9510912   587514 8923398    7% /
udev            495494      527  494967    1% /dev
tmpfs           497830      468  497362    1% /run
none            497830        3  497827    1% /run/lock
none            497830        9  497821    1% /run/shm

---

### Post by coffeecat on 2013-10-27
Not a Chat thread.

*Thread moved to **General Help**.*

---

