---
title: "first time to unbutu need help"
date: 2005-10-16
forum: General Help
---

### Post by hassan on 2005-10-16
well guys sorry for this stupid thread.i am using unbutu for first time and noob in linux.need littel help as i searched and got littel know how to insall programs.
   well first i want to install Gaim IM. but which version should i downlaod as there is nothing which indicates for Unbutu.?
            and from where i can access root where i input commands to install programs.if i find this i think i will eb able to enjoy.okease tell me step wise where i can found it,where i can input commands like sudo etc....
                     need your help guys.

---

### Post by m0biu5 on 2005-10-16
Hassan - 

What version are you running? gaim should be installed by default, so you shouldn't have to install it. 

To install programs via a gui, go to System > Administration > Synaptic Package Manager. It will prompt you for your password, and then open a program for you to install software with. 

As for where you input commands, that would be the terminal. In Breezy, I believe it is located in Applications > Accessories. In Hoary, it is Applications > System Tools.

Also, be sure to check out the beginner forums farther down the page.

---

### Post by Adrian_b on 2005-10-16
An easy way to install Gaim is:(i hope it is correct because i'm not on Ubuntu for  the moment, so i can't check)
-Open up a terminal.
-Type in 'sudo apt-get install gaim'.
-Fill in your password.
-See gaim being downloaded and installed.
-Type 'gaim' in the terminal.

P.S.: Always check [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by Muhammad on 2005-10-16
You don't need to install GAIM.

Check out [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by hassan on 2005-10-16
i just burned and install unbutu5.01"The Breezy Badger"
   thanks guys done :D  thanks for your support

---

### Post by rogelio on 2006-01-25
Hi, I install yesterday unbutu 5.01 Breezy Badger in a laptop averatec av4270-eh1. i never use unbutu or debian before. in the install i dont see askme for de root password?!. I reinstall and no ask for de password root. probably is a stupid question but what is the root password in a first install for unbutu???

---

### Post by bloodborne on 2006-01-25
[QUOTE=rogelio]Hi, I install yesterday unbutu 5.01 Breezy Badger in a laptop averatec av4270-eh1. i never use unbutu or debian before. in the install i dont see askme for de root password?!. I reinstall and no ask for de password root. probably is a stupid question but what is the root password in a first install for unbutu???[/QUOTE]

The user password that you first set up when you install Ubuntu is the password you use when you use sudo. Ubuntu doesn't use the usual su command for root.

---

### Post by njzillest on 2006-01-25
u can download anytihng that sais debian since ubuntu is based on debian.

---

### Post by carlosqueso on 2006-01-25
[QUOTE=njzillest]u can download anytihng that sais debian since ubuntu is based on debian.[/QUOTE]

Sort of.  Any .deb package will install on Ubuntu, but there is definitely a risk with installing strange debs since Ubuntu and Debian do have some differences.  My general rule is to compile from source unless it's an ubuntu-specific package (there are plenty in the repositories, and some projects are releasing ubuntu debs too).

---

