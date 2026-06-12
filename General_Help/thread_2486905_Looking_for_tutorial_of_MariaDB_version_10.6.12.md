---
title: "Looking for tutorial of MariaDB version: 10.6.12"
date: 2023-05-16
forum: General Help
---

### Post by satimis on 2023-05-16
Hi all,
[B][COLOR="#FF0000"]
Ubuntu 22.04
MariaDB Server version: 10.6.12[/COLOR][/B]

Please advise where can I find its tutorial and commands.  The syntax used looks different.  The commands used by me in the past are not all applicable to this version.

Thanks in advance

Regards

---

### Post by idmbe on 2023-05-16
Just google it you will find a lot of tutorials everywhere

for example:
[ https://mariadb.com/docs/server/deploy/operating-systems/ubuntu22/]("https://mariadb.com/docs/server/deploy/operating-systems/ubuntu22/#TOP")


Good luck

---

### Post by satimis on 2023-05-17
> **idmbe said:**
> Just google it you will find a lot of tutorials everywhere

for example:
[ https://mariadb.com/docs/server/deploy/operating-systems/ubuntu22/]("https://mariadb.com/docs/server/deploy/operating-systems/ubuntu22/#TOP")


Good luck
Hi,

Thanks for your advice and link.  I have made heavy searching before posting.  This is a mystery to me. Finally I found the solution as follow:-

This ia a LAMP server running on a VM of VirtualBox.  Later I discovered there are 2 passwords to login MariaDB/MySQL;
password-1
password-2

To login MariaDB with password-1
Running some MariaDB commands popup warnings -> Syntax error, running the command corresponding to the right version of MariaDB

To login MariaDB with password-2
All MariaDB commands work without problem.

This VM has been created and running for a long time.  Previously I have problem on this PCIe3.0 NVMe SSD compelling me to reinstall it.
Host - Ubuntu 22.04
VM - Ubuntu 22.04

The VMs were re-created on their .vbox images.  There are 6 VMs running.  I still have problem unsolved.  Some websites on VM unable to connect on browser with their internal IP addresses.  I don't know WHY?

I'll leave the problem unsolved until I found time to build a new PC.

Regards

---

