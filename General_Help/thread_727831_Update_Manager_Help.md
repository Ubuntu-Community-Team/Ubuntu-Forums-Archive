---
title: "Update Manager Help"
date: 2008-03-18
forum: General Help
---

### Post by TheMixtureMedia on 2008-03-18
HI there I am having problems with my update manager it and add remove program it comes up with this error

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I can not use terminal because for some reason terminal is all blank when I open it I see there is about 170 updates and I would sure love to update my computer can someone help please

---

### Post by kesman on 2008-03-18
hit alt+F2 and type xterm to open a terminal.
Then run the suggested command:
```

sudo dpkg --configure -a

```
after this, run in terminal
```

sudo apt-get update
sudo apt-get dist-upgrade

```
to get your updates.

---

### Post by TheMixtureMedia on 2008-03-18
I hit alt and f2 at the same time and nothing came up

---

### Post by sisco311 on 2008-03-18
type the commands in the terminal:

Applications -> Accessories -> Terminal

---

### Post by TheMixtureMedia on 2008-03-18
I try to go to that terminal and it is blank when it comes up it is all blank and when i try to type on it there is nothing no typing shows up

---

### Post by kesman on 2008-03-18
hit ctrl+alt+f2 to enter a new TTY, log in with your username and run the given commands. Then come back with ctrl+alt+f7

---

### Post by TheMixtureMedia on 2008-03-18
> **kesman said:**
> hit ctrl+alt+f2 to enter a new TTY, log in with your username and run the given commands. Then come back with ctrl+alt+f7


that does not work either no ctrl alt command works when I try what you tell me

---

### Post by TheMixtureMedia on 2008-03-18
This sucks I really want to install my updates :-(

---

### Post by sisco311 on 2008-03-18
Reboot your computer and select Recovery Mode from the Grub menu.
When the computer first starts up, you have a few seconds to push esc to go into GRUB.

When the command prompt appears, issue the commands.

To reboot your computer:
```
reboot
```

---

### Post by TheMixtureMedia on 2008-03-18
Ok I did that now it comes up with this error and I still can not get into terminal

E: ERROR: could not create configuration directory /home/root/.synaptic - mkdir (2 No such file or directory)

---

### Post by kesman on 2008-03-18
make that file while in recovery mode, just don't put anything in it

---

### Post by TheMixtureMedia on 2008-03-18
could u tell me how please :-(

---

### Post by kesman on 2008-03-18
on what command did it give you this error?
you can create the directory with
```

cd /home/root
mkdir .synaptic

```
if it's not there.

---

### Post by sisco311 on 2008-03-18
post the output of this commands:
```
ls -al /root
``````
ls -al /home/root
```

---

### Post by TheMixtureMedia on 2008-03-18
anyone please???

---

### Post by TheMixtureMedia on 2008-03-18
Now it is saying this

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


and still can not use terminal

---

### Post by TheMixtureMedia on 2008-03-18
this sucks I did what you guys told me to do and still nothing :-(

---

### Post by TheMixtureMedia on 2008-03-18
I can use terminal I just can not read the writing so i have to highlit it and put it in note pad and when I try to super user it comes up and says 

su: Authentication failure

and I do put in my password

---

### Post by kesman on 2008-03-18
don't try to use su in ubuntu, use sudo in front of command instead.

---

### Post by TheMixtureMedia on 2008-03-18
Solved

had to do log in through root but got it to download everything

thanks guys

---

