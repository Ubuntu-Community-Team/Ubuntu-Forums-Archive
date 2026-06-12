---
title: "How to be the root user - Critical"
date: 2005-07-31
forum: General Help
---

### Post by erisco on 2005-07-31
I am using Ubuntu, and I went through the install, thinking my account on ubuntu would be the root one. Well turns out it isn't. How can I gain root control? I need it to access system files and such, where I don't currently have permissions.

PLEASE HELP - it is critical.

---

### Post by HAMM3R on 2005-07-31
sudo passwd root

....use the password for the user you set up during installation when it prompts you the first time.  The second time is the password you want to set for root.  Pick anything then.  

Once this is done, you can log onto root using:  su
^you will then be prompted for your pass

Or you can preform commands AS root using:  sudo <command>

 :)

---

### Post by astoltz on 2005-07-31
The "Ubuntu" way is to keep the root user disabled and simply use sudo when you need to.  There are MANY posts about this topic in the forums - search around.

sudo, when prefixed to any command, will execute that command with root privledges. In order to use sudo, you generally  have to be logged in as the FIRST user created during the install process. Then, when prompted for a password, enter the user's password.  For example, ```
apt-get update
``` fails with persimission denied, but ```
sudo apt-get update
``` works just fine.

---

### Post by woedend on 2005-08-01
if you want to browse/open/edit files...in console type: gksudo nautilus
enter password

you are now in nautilus, able to browse, open, delete, and edit files as root.

---

### Post by Sam on 2005-08-01
[QUOTE=woedend]if you want to browse/open/edit files...in console type: gksudo nautilus
enter password

you are now in nautilus, able to browse, open, delete, and edit files as root.[/QUOTE]
Beware, you can blow up your system just by removing a system directory (/etc, /usr, ...) !

If possible, use sudo. Read [this](https://wiki.ubuntu.com/RootSudo) !

---

