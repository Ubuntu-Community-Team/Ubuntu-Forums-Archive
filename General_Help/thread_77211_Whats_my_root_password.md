---
title: "Whats my root password ?"
date: 2005-10-16
forum: General Help
---

### Post by chetanthaker on 2005-10-16
Hey guys

I FINALLY decided to install Ubuntu 5.10 and the installation was a breeze

But the thing I noticed was that it did not ask me for a root password :S

Im wondering if therez any way to reset it or sumthin

Please.... oh PLEASE do reply ASAP

Need to install da drivers... cant do it without da root password


P E A C E !!

CeeTee

---

### Post by kvidell on 2005-10-16
Ubuntu is centric on Sudo.
The first user you created is automagically in the Sudo system as root, so just use it :)
- Kev

---

### Post by Hikaru79 on 2005-10-16
Ubuntu doesn't support root by default. You can turn root on, but it's better not to. Instead, use 'sudo'. Your 'sudo' password is the same as your user's password.

A lot of Ubuntu beginners feel naked without root, but trust me -- once you get used to sudo you'll never want to go back.

---

### Post by earobinson on 2005-10-16
sudo has its pros and cons. 
pro - auto log out (you will never leave your root loged in)
con - timed log out, eg if you do something with sudo then leave the computer i could run up fast and us sudo. (there is a sudo logout flag but no one uses it lol)
con - with su you can use the tab key to auto compleat stuff, you cant after typing sudo.

not sure if it has been said but this is how to set your su password
```
sudo su
(type user password)
passwd
(type new passwrd)
```

---

### Post by chetanthaker on 2005-10-16
WOW guys, that was FAST


But then thing is when I said "su", it asked me for da password -- I entered my user password but it was invalid :S

I was not asked for any administrative password when I installed Ubuntu

I'll try out that sudo su thingy rite away
Will reply back in a minute :)


CeeTee

---

### Post by lithorus on 2005-10-16
[QUOTE=chetanthaker]WOW guys, that was FAST
But then thing is when I said "su", it asked me for da password -- I entered my user password but it was invalid :S[/QUOTE]
sudo and su works differently. Sudo is for running a single command with super user right(root), and su is for switching user (root by default) and therefore requires the password of the user, unless you have super user rights.

---

### Post by chetanthaker on 2005-10-16
Hey guys

thanx a LOT

it worked !!!

BTW, im having problems installing my graphic drivers now !!

It says that I dont have some directory installed

Can someone help please ?

I'm attaching a screenshot


CeeTee

---

### Post by Hikaru79 on 2005-10-16
Hm, are you trying to install the nvidia driver from nvidia.com ? That's not neccesary, simply do: ```
sudo apt-get install nvidia-glx
``` and then ```
sudo nvidia-glx-settings enable
```, then restart, and you're all set! You don't need to go through all the trouble of what you seem to be doing. :)

---

### Post by taavi on 2005-10-16
Hi.

I find dealing system things with root user more intuitive and confortable. To gain root privileges, I just:

1. $ sudo su - // always do "*su -*" because it loads root users enviroment fully 
2. # passwd // just set password for root user to get root privileges without sudo later going just: *$ su -* and typing password

---

### Post by chetanthaker on 2005-10-16
Hey Hikaru

I tried the first command, it did install something, but could not get the 2nd command working

Please help !!

CeeTee

---

### Post by Hikaru79 on 2005-10-16
[QUOTE=chetanthaker]Hey Hikaru

I tried the first command, it did install something, but could not get the 2nd command working

Please help !!

CeeTee[/QUOTE]
Ah, that sometimes happens. No worries! All that that command does is edit your /etc/X11/xorg.conf file, and changes the video driver from 'nv' to 'nvidia'. You can do that manually :)

---

### Post by chetanthaker on 2005-10-16
Hi Hikari

How do you suggest I enter in the settings ??

I got me a GeForce4 Onboard display driver

Please help !

I'm downloading the latest drivers -- lets see if it runs -- 
Can we chat on MSN  - [email]chetanthaker@hotmail.com[/email]

Ceetee

---

### Post by avallach on 2005-10-16
what I do is:

sudo passwd root

it prompts you for a password, type your password...then it prompts you to enter & re-enter a root password.

---

### Post by earobinson on 2005-10-19
glad it worked, as for the drivers im sure there is another post on it if you search

---

### Post by Cathbard on 2005-10-19
I like to see a root prompt too but I haven't created a root password or enabled root login. It isn't necessary.
Just type: sudo -s
enter your user password. You now have a root prompt for the duration of that shell and don't have to keep typing sudo before every command. ;)

---

### Post by SickTwist on 2005-10-19
[QUOTE=chetanthaker]Hi Hikari

How do you suggest I enter in the settings ??

I got me a GeForce4 Onboard display driver

Please help !

I'm downloading the latest drivers -- lets see if it runs -- 
Can we chat on MSN  - [email]chetanthaker@hotmail.com[/email]

Ceetee[/QUOTE]

**sudo apt-get install nvidia-settings**

That command will install a nice GUI for configuring your graphics card. The settings are stored in your home directory so each user can have his/her own graphics preferences. Start the program by opening a terminal and running "nvidia-settings" (without quotes). Or you could just create a launcher in the menu or on the panel for it--your choice :)

In Ubuntu, most things that you need to install can be done with apt-get or Synaptic if you prefer a GUI. There is usually little need to download drivers or programs manually unless it is something that is not in the repository. Once you start using apt-get you'll love it--especially when you see how easy it is to upgrade everything system wide.

---

