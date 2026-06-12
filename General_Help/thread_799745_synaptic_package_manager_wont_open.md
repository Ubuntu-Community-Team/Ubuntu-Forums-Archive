---
title: "synaptic package manager wont open"
date: 2008-05-19
forum: General Help
---

### Post by uper104 on 2008-05-19
every time i try to open my SPM i get an error message 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



what do i do??

---

### Post by overdrank on 2008-05-19
> **uper104 said:**
> every time i try to open my SPM i get an error message 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



what do i do??

HI and have you ran the command in the terminal
```
sudo dpkg --configure -a
```

---

### Post by prshah on 2008-05-19
> **uper104 said:**
> 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Exactly what it says; give the command ```
sudo dpkg --configure -a
``` in a terminal (Applications-Accessories-Terminal)

---

### Post by uper104 on 2008-05-19
ok... ive been trying for about 6 days now...and for the love of god i cant figure out how to install java... i probably have about 6 versions downloaded... 

i have a dell optiplex gx520 with 8.4 ubuntu installed 
so if anyone can give me some help that would be nice... any names of packages that i can open in the SPM that include java or something... im just really frustrated

thank you for the help with the SPM

---

### Post by i.t.guru on 2008-05-19
First things...   ...Relax brother. LOL! I will try to be more specific. Open your gnome start menu, ie; Applications.
Go to the first in the list named Accessories, then on that menu select Terminal. Once the terminal opens, type in the code [COLOR="Blue"]**sudo dpkg --configure -a**[/COLOR] and at the prompt for password, put in your password. Let the operation complete and once it does, close the terminal. Now try to open Synaptic again. Im no genius, so if you get stuck after this, I am out but I wish you the best of luck. I hope it helps and no offense to anyone, I just think he needed simple specifics. :) Cheers

---

### Post by Sakss on 2008-05-19
I have a similar problem

I try to open synaptic but i get the following message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


i run the command in terminal but i get this message.

dpkg: parse error, in file `/var/lib/dpkg/updates/0093' near line 1:

Any ideas?I tried many many  ways but nothing worked.

Thanks!

---

### Post by overdrank on 2008-05-19
> **Sakss said:**
> I have a similar problem

I try to open synaptic but i get the following message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


i run the command in terminal but i get this message.

dpkg: parse error, in file `/var/lib/dpkg/updates/0093' near line 1:

Any ideas?I tried many many  ways but nothing worked.

Thanks!

Hi and I have not seen that error but have looked in the /var/lib/dpkg/updates/0093 and see what is at line 1. I have nothing in the updates file on my system.

---

### Post by uper104 on 2008-05-19
ohkay i got it working (i can get into the SPM and its fully accesible) but when i inserted the command in the terminal and enterd the password for my computer it said it wasnt correct ... how do i check the root password?

and again ... java isnt working on here... what to do about that ??

---

### Post by Sakss on 2008-05-19
> **overdrank said:**
> Hi and I have not seen that error but have looked in the /var/lib/dpkg/updates/0093 and see what is at line 1. I have nothing in the updates file on my system.

 EOF

`93bd2f464b83f4_31bf3856ad364e35_6.0.6001.18000_none_7934ad96f0145855.manifest (first line of 0093)

this is  the error in terminal.

---

### Post by Fredizdman on 2008-05-19
You only need your user's password to use sudo, it is not a root password. So you should be able to use what you use when you login. That is as long as your user is in the sudo group.

As far as your java problem, if you have already 'installed' a few versions, you still have to select them.

```
sudo update-alternatives --config java
```

and then just select the java you want to use.

---

