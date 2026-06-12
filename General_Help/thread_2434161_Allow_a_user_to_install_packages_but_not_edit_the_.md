---
title: "Allow a user to install packages but not edit the hosts file"
date: 2019-12-31
forum: General Help
---

### Post by zigbigadoorlue2 on 2019-12-31
For complicated reasons I need a user to be able to install packages but not have write access to the hosts file. One method would be to [install software without root]("https://askubuntu.com/questions/339/how-can-i-install-a-package-without-root-access") but that looks beyond my abilities/causes additional glitchyness.

I had another idea involving permissions but am not terribly clear on how permissions work. Would I be able to assign write permissions for /etc/hosts to a user that is not root and then restrict root (and by extension the system?) to only being able to read the file and not write to it? Is it even possible to restrict root's access to things? Anyways feedback on this or any other solution would be very helpful.

Thanks so much!
Luna

---

### Post by Impavidus on 2020-01-01
You can use the sudoers file to configure the system such that this user is allowed to use sudo, but only to run apt install commands. Maybe apt update and apt upgrade too. I wouldn't allow apt remove, as that would allow destroying the system. See [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers). Make a backup of the old sudoers file before making any edits. I've never done this myself.

---

