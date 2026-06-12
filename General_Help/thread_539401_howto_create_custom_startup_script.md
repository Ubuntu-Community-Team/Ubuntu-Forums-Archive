---
title: "howto create custom startup script"
date: 2007-08-31
forum: General Help
---

### Post by ZenSpirit on 2007-08-31
Hi all ...
I would like to know how i could create a script that runs when booting.
This is what i currently enter i a terminal each time a want to use this server/client:

> sudo su postgres
type password
cd /home/username/tinyerp-server/bin
python2.4 tinyerp-server.py

Then i open another terminaltab and type:
> cd /home/username/tinyerp-client/bin
python2.4 tinyerp-cient.py

and in another terminaltab:
> cd /home/username/tinyerp
python2.4 start-tinyerp.py

This is for the TinyErp softwarepackage.
I first start the server, then the client, and last the webinterface.
See [http://tinyerp.org/wiki/index.php/InstallationManual/ServerInstallUbuntu](http://tinyerp.org/wiki/index.php/InstallationManual/ServerInstallUbuntu) for the manual that describes this.
I would like to have a way that this gets done automaticly when i boot my computer.
Thanks in advance for any help on this!

---

### Post by apetresc on 2007-08-31
You're looking to make an rc script. Luckily they are pretty easy to write up, here's a quick tutorial from the Gentoo Wiki: [http://gentoo-wiki.com/HOWTO_Make_an_rc_script](http://gentoo-wiki.com/HOWTO_Make_an_rc_script)

It's written for and by Gentoo users, but it should work exactly the same for Linux.

---

