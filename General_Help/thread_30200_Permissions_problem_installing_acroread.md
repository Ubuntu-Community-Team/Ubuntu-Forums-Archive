---
title: "Permissions problem installing acroread"
date: 2005-04-27
forum: General Help
---

### Post by Psquared on 2005-04-27
I downloaded the tar.gz and ran the ./INSTALL script. It asks me where I want it to install and suggests /usr/local/Adobe/Acroread7.0 which I accept. It then says it can't create the directory - permission denied. So, I created the directory for it and it now says it can't install in that directory - permission denied.

I tried /usr/share/Adobe and several others and got the same response.

Do I need the prefix "sudo" ./INSTALL? Do I need to change the permissions on the install file or the target directory?

Thanks in advance.

---

### Post by Alexander Kirillov on 2005-04-27
[QUOTE=Psquared]I downloaded the tar.gz and ran the ./INSTALL script. It asks me where I want it to install and suggests /usr/local/Adobe/Acroread7.0 which I accept. It then says it can't create the directory - permission denied. So, I created the directory for it and it now says it can't install in that directory - permission denied.

I tried /usr/share/Adobe and several others and got the same response.

Do I need the prefix "sudo" ./INSTALL? Do I need to change the permissions on the install file or the target directory?

Thanks in advance.[/QUOTE]
 you need sudo ./INSTALL

(for a good reason - as an ordinary user, you can only write to your own home directory, not to /usr/local/.. or /usr/share).

---

### Post by el000 on 2005-04-27
A normal user can't install under /usr. You need to install as root, using sudo.
As a user you can only install in your home directory.

P.S.There is also a debian package for Acrobat 7. You can get it from the debian-marillat repository.

---

