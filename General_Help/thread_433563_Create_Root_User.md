---
title: "Create Root User"
date: 2007-05-05
forum: General Help
---

### Post by Soad123 on 2007-05-05
I have just installed Ubuntu 7.04  and during the install it only allowed me to create a normal user, I was not asked to create a root user, so how do I create the root user as certain tasks from the terminal require root privileges
Thanks

---

### Post by Thingymebob on 2007-05-05
The user you created during install will have root priveleges just enter sudo before the command

---

### Post by Soad123 on 2007-05-05
Thanks for the quick answer, is that not a bit dangerous

---

### Post by kpel on 2007-05-05
It is much more dangerous to run as a root user.  The sudo and gksudo commands will allow you to run as root for the duration of the given action and will then switch off.  As a root user anyone and anything can mess with your system at any time; running as a normal user prevents this while the commands give you the ability to work as root when you need to (and it requires a password in order to remain secure).

Edit: Reading material:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Thingymebob on 2007-05-05
sudo only escalates your priveleges for one command after that you priveleges are dropped back to your normal level. so you need to enter sudo before every command you want to run with root priveleges.

> 
With ubuntu, when you enter the sudo command for the first time, you will be prompted for a password. What password? Yours. That is, the password you normally use to log in. This is to prevent someone walking over to an unattended system from getting root access. In order to make it more convenient to do a series of commands as root, ubuntu remembers that you have run as root recently and doesn't require the password. But, after a short idle period, you will be asked for it again
source:[http://www.tuxmagazine.com/node/1000148]("http://www.tuxmagazine.com/node/1000148")

---

### Post by sdide on 2007-05-05
I don't see the big difference between sudo, and making a login shell as root, maybe except redirection won't work with sudo.

Hence

lets say I have the following: 
~$ ls -l testfile1
-rwx------ 1 root root 11 2007-05-05 12:53 testfile1

a file only readable and writeable by root.

lets say I want to redirect stadard out into testfile1, for example the output of ls

~$ ls > testfile1
bash: testfile1: Permission denied

so I just use sudo - right?  - Wrong!

~$ sudo ls > testfile1
bash: testfile1: Permission denied

The redirection is executed with the shells permission which is those of the user logged in - hence me, not root.

on the other hand if make a login shell for the root account 

~$ su -
Password:
I can easily make redirection all I want

~# ls > testfile1
~# 

With no problem.


So, its a matter of choice, I like making a shell and login as root from there.

I NEVER EVER login the GUI using the root account, that is unsafe.

---

### Post by ramjet_1953 on 2007-05-05
If yor really want to have access to the root account, you just type in a terminal:

[COLOR="Red"]sudo passwd root[/COLOR]

It will then ask for a new root password twice and confirm it.

You then have root access.

If you want to be able to log-in as root with GNOME you will need to go into [COLOR="Blue"]System>Administration>Login Window[/COLOR]. It will ask for your user password. After entering it, click on the [COLOR="Blue"]Security Tab[/COLOR] and then click on the box that says [COLOR="Blue"]"Allow local system administrator login. [/COLOR]

One caveat on all of the above. If you manage to hose your system when operating as root, don't blame me, or Ubuntu.

Even changing priveleges on some system files will totally trash your system.

That is why it is much better to use sudo.

Regards,
Roger 8)

---

### Post by Thingymebob on 2007-05-05
or **sudo -s**

---

### Post by greatshape on 2007-05-05
> **Thingymebob said:**
> or **sudo -s**

Yes, better choice ;-)

---

### Post by sdide on 2007-05-05
> **greatshape said:**
> Yes, better choice ;-)

Why is it better to type 

~$ sudo -s

over 

~$ su -

at least with "su -" you choose a special password for the root user.

---

### Post by greatshape on 2007-05-06
> **sdide said:**
> Why is it better to type 

~$ sudo -s

over 

~$ su -

at least with "su -" you choose a special password for the root user.

B4 you can use su on ubuntu you have to "activate" the root account.
It's always safer when the root account is locked. For example, ssh attacks, the user "root" is 
known by everyone and exists on most systems. The username of a regular user is hard to guess ;-)  
sudo -s gives you a root shell, but isn't a permanent "root account" on the system.

Kind Regards,
Steve

---

### Post by Thingymebob on 2007-05-06
I didn't mean it was better!!! - Just another option, (whatever suits the user is clearly the best) If we all wanted to work exactly the same way then  we would be still using windoze

---

### Post by asipi on 2007-05-07
> **sdide said:**
> I don't see the big difference between sudo, and making a login shell as root

if more user using the system and you want to give some of them root privileges it is more safer to use sudo thingy. why? so if you want to give the ones the one and only root pw you open the root account to them with the same pw, and so they have to know their own pw and the root pw. if you use sudo, they have to know only their own pw. in case of reliability problems u can easily revoke their admin group membership and the root privileges are gone for that user but the others could use it with their own pw.

if u think about for a while from more aspects you can realize that sudo could be more safer. of course nothing can protect from dumb and/or hostile users...

---

### Post by bry5an on 2007-05-23
what if i forgot my root pw? how can i get it back? :(

---

### Post by asipi on 2007-05-24
if your normal user still in group adm then sudo passwd and you can set it again, if not... it is also possible but it is a more longer story :)
principals: boot from a live cd or grub with init=/usr/bin/bash, changeroot to hardrive if you booted from cd, mount root fs as rw, change pass, reboot
That's all ;)

---

### Post by bry5an on 2007-05-24
ah ha.. i got it, thanks :)

---

