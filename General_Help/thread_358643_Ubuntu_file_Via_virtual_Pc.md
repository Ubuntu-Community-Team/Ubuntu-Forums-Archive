---
title: "Ubuntu file Via virtual Pc"
date: 2007-02-11
forum: General Help
---

### Post by Rhaddad on 2007-02-11
Hello,
I use VMware as my virtual PC for windows XP so I can use Programs like dreamweaver Delphi Photoshop.

but i am wondering if i can access my ubuntu files through my virtual PC which runs on Windows Xp.

Thanks

---

### Post by koenn on 2007-02-11
I think that if you install VMWare Tools, it offers the possibility to share files between the host and the guest OS - but I've never tried it before. 

If you're VMware is set up for "bridged networking", you have a network connection between the guest and the host (the virtuual machine and the physical machine) so you should be able to use samba to share the ubuntu files to the xp machine

---

### Post by Rhaddad on 2007-02-12
yea i get that but it tells me to type the username and the password, i try my ubuntu username and password but it does not accept

---

### Post by koenn on 2007-02-12
oh -  why didn't you say so ?

When setting up Samba to share the ubuntu files, you need to create a 'samba' account which you will authenticate with when accessing the shared files from an other computer. Most people use the same name and password as their regular Linux account. 
say your linux account is "joel" : 
```
# smbpasswd -a joel
New SMB password: secret
Reenter SMB password: secret
Added user joel
```

That should allow you to get passed the aythentication dialogue. Next step might be permissions. these are configured in smb.conf

---

### Post by Rhaddad on 2007-02-13
oh thanks man, thanks heps appreciated!!!

that made my whole network easier as well :D

but isn't there a GUI way I can do it?

by the way note for everyone u have to be super user.

---

### Post by koenn on 2007-02-13
y're welcome.
don't know of any gui for samba confog. I don't think typing "smbpasswd" is that difficult.  :)

and you're correct about the super user, of course. I alwways forget to add that, because i usualla have a root session in a terminal so i don't need 'sudo' in front of every command i type.

---

### Post by Rhaddad on 2007-02-13
Oh yea it isn't,

another question, how do you run the terminal as root :P

sorry about all the questions:confused:

---

### Post by haricharan on 2007-02-13
use ```
sudo
``` before the commands..for the first time it would ask your password..enter your Ubuntu password...

---

### Post by koenn on 2007-02-13
> another question, how do you run the terminal as root :P
I created a launcher with
```
gksu /usr/bin/x-terminal-emulator
``` as "command" - and put it in the top panel.

First time I ran it, i changed the default colors to black background, green text. So it's visually different from a normal terminal - as a reminder that i'm 'root' when i'm using it.

When i'm doing sysadmin stuff, I usually have that terminal running in one of the workspaces
You really should only use it for sysadmin stuff. 

 [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

