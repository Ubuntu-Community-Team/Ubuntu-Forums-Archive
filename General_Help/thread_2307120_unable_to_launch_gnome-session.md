---
title: "unable to launch gnome-session"
date: 2015-12-22
forum: General Help
---

### Post by Artnect on 2015-12-22
hi 
i get this message when running ubuntu .
[COLOR=#333333][FONT=Tahoma]unable to launch gnome-session --session=ubuntu X session -- 
[/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]gnome session -- session=ubuntu not found; falling back to default session[/FONT][/COLOR]

i don't have login page now .by using ctrl+alt+f1 i tried these commands :

[COLOR=#0000BB][FONT=monospace]sudo apt[/FONT][/COLOR][COLOR=#007700][FONT=monospace]-[/FONT][/COLOR][COLOR=#0000BB][FONT=monospace]get update [/FONT][/COLOR][COLOR=#007700][FONT=monospace]&& [/FONT][/COLOR][COLOR=#0000BB][FONT=monospace]sudo apt[/FONT][/COLOR][COLOR=#007700][FONT=monospace]-[/FONT][/COLOR][COLOR=#0000BB][FONT=monospace]get upgrade 
 
[/FONT][/COLOR]

[RIGHT][COLOR=#333333][FONT=Tahoma][LEFT][COLOR=#000000][COLOR=#0000BB]sudo apt[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]get install [/COLOR][COLOR=#007700]--[/COLOR][COLOR=#0000BB]reinstall ubuntu[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]desktop  
[/COLOR][/COLOR]
result :

Some packages could not be installed this mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of incoming....
the following information may help tp resolve the situation :
the following packages have unmet dependecies : 


ubuntu-desktop :listed packages name in here

E: unable to correct problems you have held broken packages .

also tried :
sudo apt-get install -f
output :
0 upgraded , 0 newly installed , 0 to remove and 311 not upgraded 
 and :
sudo apt-get install -f ubuntu-desktop
output:
E : unable to locate package ubuntu
E : unable to locate package desktop
and:
[COLOR=#000000]sudo apt-get purge ubuntu-desktop[INDENT]sudo apt-get install ubuntu-desktop
[/INDENT]


[/COLOR]


[/LEFT]
[/FONT][/COLOR][/RIGHT]
[COLOR=#000000]it says Package ubuntu-desktop is not installed, so not removed.
i have reinstalled ubuntu 3 times in this month don't want to do more .................. 
help pls ![/COLOR]

---

### Post by kc1di on 2015-12-22
Some things that may help you get answers:
1. what version of Ubuntu are you installing (What desktop)?
2. did you check the downloaded file to make sure it was a good download?
3. What machine are you trying to install on?
4. Try the following command in a terminal :

```
sudo dpkg --configure -a
``` Then ```
sudo apt-get autoremove && sudo apt-get autoclean 
```

List any error messages you receive here.

---

### Post by Artnect on 2015-12-22
> **kc1di said:**
> Some things that may help you get answers:
1. what version of Ubuntu are you installing (What desktop)?
2. did you check the downloaded file to make sure it was a good download?
3. What machine are you trying to install on?
4. Try the following command in a terminal :

```
sudo dpkg --configure -a
``` Then ```
sudo apt-get autoremove && sudo apt-get autoclen 
```

List any error messages you receive here.

1.ubuntu 14.04 ltd (by the i had added some kali linux repo but in start up page beside my windows 10 it shows kali gnu/linux option instead of ubuntu ! ) 
2.know actually don't know how to do !
3.didn't understand this question it is installed besied my windows 10 
4: output :
1.nothing
2. 0 upgraded , 0 newly installed , 0 to remove and 311 not upgraded

---

### Post by kc1di on 2015-12-22
#3 I was asking what is your PC your process , ram ?

Are you trying to run Unity desktop?
Could you go to a terminal and type the following command:  and post the output here.

I suspect your trouble may be because you mixed the operating system ubuntu/kali.

---

### Post by Artnect on 2015-12-23
> **kc1di said:**
> #3 I was asking what is your PC your process , ram ?

Are you trying to run Unity desktop?
Could you go to a terminal and type the following command:  and post the output here.

I suspect your trouble may be because you mixed the operating system ubuntu/kali.


i'm using Toshiba satellite p755 laptop 
processor intel core i5 2450m cpu @ 2.500GHz 2.50 GHz 
RAM 4 GB 
yes want to run unity by the way before happening these things i used xkill command i clicked on the top bar (mistake) maybe this caused this ?
i don't have login page but i have access to terminal by ctrl + alt + f1
which command ? 

is there any way to fix it ? (hope dont say reinstall it ! :| )

---

### Post by kc1di on 2015-12-23
This is what I would try.
```
sudo apt-get purge ubuntu-desktop
sudo apt-get install ubuntu-desktop
```

Then reboot.  if it works you good , if not I would save all important files and re-install ubuntu. 
good luck.

---

### Post by Artnect on 2015-12-23
> **kc1di said:**
> This is what I would try.
```
sudo apt-get purge ubuntu-desktop
sudo apt-get install ubuntu-desktop
```

Then reboot.  if it works you good , if not I would save all important files and re-install ubuntu. 
good luck.
as i mentioned in first post i have tried these commands before

can u pls tell me how can i fix unmet Dependencies  packages and also broken packages while i'm trying to use 
sudo apt-get install --reinstall ubuntu-desktop     i got these messages i think  when i solve these problems ( unmet dependencies and broken packages )
there wouldn't be necessary  to reinstall it 

any way thanks for answers i am going to reinstall to if i couldn't find a way to solve those 2 problems ......

---

### Post by philinux on 2015-12-23
Try this again.

```
sudo apt-get install -f
```

-f means fix broken packages if it can.

Post back any error messages.

---

### Post by Artnect on 2015-12-23
> **philinux said:**
> Try this again.

```
sudo apt-get install -f
```

-f means fix broken packages if it can.

Post back any error messages.
Reading package lists ... Done 
Building dependency tree 
Reading state information ... Done 
0 upgraded , 0 newly installed , 0 to remove and 311 not upgraded 
----------------------------------------------------------------------------------------------
there are some points that i guess they may help :(listed below)
when pc is turning on i dont see ubuntu option any more ! ( kali linux instead)
------------------------------------------------------------------------
while i use sudo apt-get update at the end of it , this is written :
```
E: Some index files failed to download . They have been ignored , or old ones used instead 
```
------------------------------------------------------------------------
i used startx command to check whether i can log in to desktop or not after it i have some line above the command line :
Kali GNU/linux 2.0 alireza-satellite-p755 tty1
alireza-satellite-p755 login : *Stopping cold plug devices [OK]
*Stopping log initial device creation [OK]
* Starting save udev log and update rules [OK]
* Stopping save udev log and update rules [OK]
-------------------------------------------------------------------------
i used katoolin script to add packages

---

### Post by philinux on 2015-12-23
Post your sources list.

```
cat /etc/apt/sources.list
```
Were there no other error messages from apt-get?

---

### Post by Artnect on 2015-12-23
im runing update again will notice u soon these are source list
[http://www.mediafire.com/view/al5982oox5alkjb/IMG_0678.JPG](http://www.mediafire.com/view/al5982oox5alkjb/IMG_0678.JPG)
[http://www.mediafire.com/view/d7d3dtgth9h4bth/IMG_0677.JPG](http://www.mediafire.com/view/d7d3dtgth9h4bth/IMG_0677.JPG)

---

### Post by Artnect on 2015-12-23
there is also 3 w: failed to fetch {URL} 404 not found
no thing more

---

### Post by Artnect on 2015-12-24
up

---

