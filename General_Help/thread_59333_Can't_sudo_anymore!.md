---
title: "Can't sudo anymore!"
date: 2005-08-23
forum: General Help
---

### Post by watje on 2005-08-23
Hi, i hope this is in the good forum.
This is my problem:
I changed something in /etc/sudoers, and now, everytime I try to run sudo, I get this error:
```
>>> sudoers file: syntax error, line 19 <<<
sudo: parse error in /etc/sudoers near line 19
``` 
But I can't change /etc/sudoers anymore, 'cause I can't sudo.
Can anybody help me out?

---

### Post by Aksu on 2005-08-23
Maybe you could do it from GRUB. Reboot and press Esc, so you will enter a recovery-mode as a root. There you can do whatever you want.

---

### Post by Chris Cromer on 2005-08-23
What you could do is go into System > Administration > Login Screen Setup

Assuming it still works without sudo, you should be able to fix your problem.

Then from there, click on the security tab. Then check the box next to "Allow root to login with GDM".

After that you should be able to login to the root account from the login screen. This way you won't need to use sudo to fix /etc/sudoers.

Just edit the file like you normally would, but you don't need to type sudo before the command to edit it.

And don't forget after your done, logout as root. Go back to your account. Then uncheck the box called "Allow root to login with GDM" that way nobody can login under root anymore.

---

### Post by arnieboy on 2005-08-23
[QUOTE=Chris Cromer]What you could do is go into System > Administration > Login Screen Setup

Assuming it still works without sudo, you should be able to fix your problem.

Then from there, click on the security tab. Then check the box next to "Allow root to login with GDM".

After that you should be able to login to the root account from the login screen. This way you won't need to use sudo to fix /etc/sudoers.

Just edit the file like you normally would, but you don't need to type sudo before the command to edit it.

And don't forget after your done, logout as root. Go back to your account. Then uncheck the box called "Allow root to login with GDM" that way nobody can login under root anymore.[/QUOTE]
before u do that u need to be sure ur root password isnt something random which u dont know. for that go to System-->Administration-->Users and Groups. search for user "root". hit properties and change the  passwordto somethingwhich u will remember. the initial password there is ubuntu system generated.

---

### Post by cazub on 2007-07-10
i'm in even more trouble! 

Administrator->  nothing  , thats my menu option.  I mean there are NONE of the things you guys mention such as "login and users" etc.  My options are Network Tools, and 2 other useless menu's. I have no synaptic, sudo would work but i'm not IN the sudo list,  i can't change my root password, can't add to sudoers file , basically i can't do ANYTHING. This is a verify'd copy of ubuntu from shipit so what the hell?! 

try'd the sudo root passwd , visudo for changing the sudoers , nothing works. Apt-get doesn't work either since i can't get permissions.

---

### Post by aysiu on 2007-07-10
Instructions to recover sudo:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by UJoe4 on 2007-07-10
As Aksu mentioned, if you're willing to do a cold reboot it should be no problem. Enter "Recovery Mode" from GRUB, which will log you into a console as root. Then just undo the changes you made to /etc/sudoers.

If you don't want to do a cold reboot (ie. you're worried about unsaved data, or you don't want to power off without unmounting) then I don't know. Wait and see if anyone else knows something that might work?

Quite frankly I remain rather unconvinced about Ubuntu's policy of disabling root by default, and this kind of thing is one of the reasons why.

---

