---
title: "The desktop is not available anymore!"
date: 2015-11-04
forum: General Help
---

### Post by ahmed39 on 2015-11-04
Dear Ubunto Experts,

My Libre office hanged 3 times so I had to restart my notebook "Compaq c316' manually in each time and now when I open the pc, till i insert my password, it's ok but after that nothing appears but the mouse! No startmenu, even with prresing the windows button, no sidebar, no taskbar and i just manage to get to the files through ctrl+alt+del but also showing the usb flash for example unproberly when i try to copy files, which abrupts as well.

I tried to do recoverymood but it didn't help but I have access to the setting.

How can I fix such problem?

Regards
Ahmad

---

### Post by Bucky Ball on 2015-11-04
When you get to the login screen, hit contol+alt+F1. That should get you to a CLI. Login there and then run these commands, one after the other with return in between, and report, between code tags (see last link in my signature), any errors they cough up, if any. 

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

Reboot. None of these commands will upgrade your installed release to a newer one. 

Which release are you using?

---

### Post by ahmed39 on 2015-11-04
It's Ubunto 14.04.3 and the weird thimg that i can log normally from the guest session but not my account

---

### Post by Bucky Ball on 2015-11-04
Please read and do what is instructed in post #2 then report back. You don't need to log in to any session from the login screen to do this. You need to get to the CLI via control+alt+F1. Thanks. That may give us some more clues, although I have my suspicions.

---

### Post by ahmed39 on 2015-11-04
Can you guide me how to login? As i know the password but before that he writes the name of the pc name + login: ? What i should write here?

---

### Post by Bucky Ball on 2015-11-04
See post #2 and post #4 and report back. Helping you is difficult if you don't perform the instructions given and provide the output requested. Thanks.

---

### Post by ahmed39 on 2015-11-04
I already pushed ctrl+alt+f1 but then it writes the following and wait for entry, which i don't know what to write:
*lafo is the pc name, and then the password but then says that login data is incorrect
'LaFo login:'

I managed to log in finally and now following your instructions one by one

I did the unstructions but unfortunately have the same problem, the guest session work proberly but my session doesn't...the language as well in my session is only one not the normal 3 i have

---

### Post by ajgreeny on 2015-11-04
OK, using the command line again, login there with your username and password (password will not show on screen) then run the command 
```
ls -l .Xauthority
``` and report back here the output from that.  It should look very similar to this line, with your username  where I show *user user*:-
```
-rw------- 1 *user user* 163 Nov  3 19:01 .Xauthority
```
I suspect that either the permissions of that file (the -rw- - - - - - - at the start of the line) or the ownership (the *user user*) may be incorrect, but let's see what output you get before you do anything more.

---

### Post by ahmed39 on 2015-11-15
-rw------- 1 user user 98 Nov 15 09.05 .Xauthority

So? I still have the same problem with no access to my files and even starting to harm my usb sticks ...

---

