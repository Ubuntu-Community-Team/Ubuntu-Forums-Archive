---
title: "Problem Help--NEWB"
date: 2008-01-05
forum: General Help
---

### Post by NoobToast on 2008-01-05
KK, heres the problem, me being curious, went into System > Prefrenses or administration(cant remember what it is) > Screens and Graphics(somin like that). and changed the resolution set and such to a different one than the preset(it is bigger). Now the screen has like 5 different mouse pointers and about 5 copies on the same screen. Help ME PLZ

Also, before all that happened i went into the terminal and tried to use the sudo command and it asked me for a password. how do i figure out that password.

---

### Post by NoobToast on 2008-01-05
Help Would Be Nice

---

### Post by MattBD on 2008-01-05
Well, I don't know about the resolution issue, but the password for sudo is the same one you use to login.

---

### Post by NoobToast on 2008-01-05
ug kk thanks

---

### Post by xeth_delta on 2008-01-05
Once presented with the desktop, press **Control-Alt-F1**. You will be prompted to enter your user-name and password.

Make a back-up of your /etc/X11/xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```
Reconfigure the xserver:
```
sudo dpkg-reconfigure xserver-xorg
```
Follow the instructions. Go back to X11 with **Alt-F7**. If the output is still bad, reset the X11 server with **Control-Alt-Backspace**.

Xeth

---

### Post by Digger78 on 2008-01-05
try restarting X

```
ctrl+alt+backspace
```

login and see if it fixed the problem

---

### Post by NoobToast on 2008-01-05
where do i restart X though, when it first loads grub at the log in screen or when i log in.

---

### Post by xeth_delta on 2008-01-05
> **NoobToast said:**
> where do i restart X though, when it first loads grub at the log in screen or when i log in.

Either when you are presented with the log-in screen or after logging in.

---

### Post by NoobToast on 2008-01-05
none of it works, whenever i enter the code to back it up it says something about there being no directory and when i try to restart X it dosent work. anything else or should i just reinstall it?

---

### Post by xeth_delta on 2008-01-05
> **NoobToast said:**
> none of it works, whenever i enter the code to back it up it says something about there being no directory and when i try to restart X it dosent work. anything else or should i just reinstall it?

Can you please post the command, as you typed it, and the error you get?

---

### Post by NoobToast on 2008-01-05
Heres what i did 
-logged in
-pressed Ctrl-Alt-F1
-typed user name and password
-typed the backup code
-then it asked me to long into sudo
-then it wanted me to type the code again, so i did
-then i got the error below

back up error:

```
CP: cannont create regular file `/etc/X11/xorg.conf-backup': no such file or directory

```

---

### Post by xeth_delta on 2008-01-05
> **NoobToast said:**
> Heres what i did 
-logged in
-pressed Ctrl-Alt-F1
-typed user name and password
-typed the backup code
-then it asked me to long into sudo
-then it wanted me to type the code again, so i did
-then i got the error below

back up error:

```
CP: cannont create regular file `/etc/X11/xorg.conf-backup': no such file or directory

```

Hmmm,  I just  made an exact copy-paste on my computer, it worked. Sorry for asking, are you completely sure you typed exactly as I wrote? Copy to something different, like /etc/X11/xorg.conf-bkp.

---

### Post by NoobToast on 2008-01-05
pretty sure, but ill try again.

---

