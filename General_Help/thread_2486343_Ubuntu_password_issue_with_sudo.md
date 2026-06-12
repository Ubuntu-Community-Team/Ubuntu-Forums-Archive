---
title: "Ubuntu password issue with sudo"
date: 2023-04-26
forum: General Help
---

### Post by jack-tauson-sr on 2023-04-26
I have Ubuntu 20.04 app from MS store version on my Windows 10 Enterprise machine and in order to install a software ([docksal]("https://docs.docksal.io/getting-started/setup/")), with normal user I am able to see a prompt like this tan@MyComputername and in order to install Docksal, it's asking me to use sudo password for tan but all of my password attempts were unsuccessful.
On the other hand, if I start the ubuntu console using administrator, it ran find and I was able to install the docksal. But I want to do it with regular user with sudo command. How can I fix this password issue which is not working? I have tried putting the administrator password when it asks for password but that didn't work.

---

### Post by Quarkrad on 2023-04-27
When asked for the sudo password have you tried typing in the password and then hitting the Return key?  This is the normal practice with Ubuntu - it can seem a little odd at first in that when you type in the password nothing happens on the screen, so it appears you have not typed in anything.  Try typing in the password and then hitting Return.

---

### Post by ajgreeny on 2023-04-27
I'm confused!

You talk of being asked for the password of user **tan** but then also mention **administrator** password which does work.
Is the user tan in the admin or sudo group as that is needed for any package installation.

Normally we do not have different passwords for user and administrator in Ubuntu but use sudo instead with the user password when asked for it.
See **Root-Sudo** in my signature below for details.

Caveat:
If you're using the Windows WSL version of Ubuntu and not a normal installation of Ubuntu there may be some differences but I don't know WSL so you will have to await other answers.

---

### Post by SeijiSensei on 2023-04-27
I'd install VirtualBox on the Windows machine, then create an Ubuntu virtual machine.

---

