---
title: "Please HELP with login Ubuntu"
date: 2008-03-21
forum: General Help
---

### Post by pleasure on 2008-03-21
whenever i run Ubuntu i dont need to log in . However when i play with my laptop today. I press ctrl+Alt +backspace then it suddenly requires me to login i try many ways but can log in. I did shutdown and restart but doesnt matter how many times i log in i still cant log in
Help please

---

### Post by InvIsiBlekID on 2008-03-21
During your ubuntu install you would have created a username and a password for your default user.  You will need to provide that information to your login screen to get in.  If you can't, then you may need to reinstall ubuntu.

---

### Post by sujoy on 2008-03-21
are you sure you didnt mistype the password in the wrong case?check CAPS LOCK.

the login name & password is the same one you entered during installation, unless you changed it later.

---

### Post by pleasure on 2008-03-21
too bad i hav many things installed in ubuntu.
I tried the default user pass too but it didnt work
I dont want to loose all of my stuff.
Please is there any other way?

Im sure i did type user name and pass correctly

---

### Post by sujoy on 2008-03-21
try to login to the rescue mode(from grub menu), which normally gets you to root account, there enter this command,

passwd <username>

it will ask for new password and verification of the same. thats it you are done :)

---

### Post by sisco311 on 2008-03-21
Reboot your computer and select Recovery Mode from the Grub menu.
When the computer first starts up, you have a few seconds to push esc to go into GRUB.

When the command prompt appears, issue the command:
```
ls /home
```This command will print the home folders.(home folder name = user name)

Type:
```
passwd *username*
```to change your password.
     
```
reboot
```to reboot your computer.

---

### Post by pleasure on 2008-03-21
> **sujoy said:**
> try to login to the rescue mode(from grub menu), which normally gets you to root account, there enter this command,

passwd <username>

it will ask for new password and verification of the same. thats it you are done :)
is that the recovery mode?

Ok i im trying now thanks

---

### Post by sujoy on 2008-03-21
> **pleasure said:**
> is that the recovery mode?

Ok i im trying now thanks

yes its the recovery mode

---

### Post by pleasure on 2008-03-21
hic...hic its still the same i can not log in

---

### Post by sujoy on 2008-03-21
any error message shown?

---

### Post by pleasure on 2008-03-21
> **sujoy said:**
> any error message shown?

it doesnt say any thing, it comes back with  black screen : /etc /rc.local /for 2 seconds  and switch back to log in screen again for me to log in
However when i press ctrl+alt+F3 then im able to log in and do eveything just like on terminal but can not switch back to Desktop. And if i press ctrl+alt +F7 then theres a screen that tells me to log in like original again

---

### Post by pleasure on 2008-03-21
i forgot to tell what i did before this happened:
when i started finishing install this stuff for my desktop
[PHP]sudo apt-get install xserver-xgl [/PHP]
After that, i press ctr + alt+backspace and the screen appears asking for login until now i couldnt log in

ITS ok i got it fixed THANK YOU

---

### Post by sujoy on 2008-03-22
thats good, but you might consider posting how exactly the problem got solved in case someone else encounters the same.

---

### Post by pleasure on 2008-03-28
I just remove xserver-gxl and im able to log in the Desktop:)

---

