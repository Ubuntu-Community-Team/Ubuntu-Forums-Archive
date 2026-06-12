---
title: "X wont start"
date: 2006-12-20
forum: General Help
---

### Post by johnnyw on 2006-12-20
I tried to install office 2003 ( microsoft :-k ) on my dapper drake and after some time my X halted. I had to reset computer and when trying to acces X I got this:

"Failed to start the X server ( your graphical interface). It is likely that is not set up correctly. Would you like to view the X server configuration to diagnose the problem?"

How should I make things work as they did?

I am using winxp now ( as I used to)

---

### Post by aysiu on 2006-12-20
One approach you might want to take is typing in this command to regenerate your X config--answer the questions as best you can, and go with the defaults if you don't know the answer: ```
sudo dpkg-reconfigure xserver-xorg
``` Afterwards, you can try these commands to make sure you have everything installed and to try to restart the X server: ```
sudo aptitude update && sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm restart
``` Mind telling us the exact steps you took to try to install Office 2003?

---

### Post by studiesrule on 2006-12-20
First log in through the terminal as root. Press <ctrl> + <alt> + F2 at the login screen to get to terminal login. Then reconfigure you X by typing:
dpkg-reconfigure xserver-xorg
Select the appropriate options everywhere, and then reboot
Everything should be working fine after that

I never knew microsoft made ANY linux products. If you want another office suite try openoffice.org. It's pretty good, and will read all you ms office docs.

---

### Post by Denn1s on 2006-12-20
Try this in one terminal (ctrl+alt+F1 for example):

```
sudo dpkg-reconfigure xserver-xorg
```

and follow onscreen instructions, 
i hope it helps, good luck

edit:
this slow connection, i  hadnt seen they had already helped you, twice, i love this forums! u get help so fast...

---

### Post by johnnyw on 2006-12-20
First of all thanks for being so quick and nice with your answer :-D.

a)Some guys from other forums told me to try with these :

1-sudo dpkg-reconfigure xserver-xorg

and got as an answer:

broken or not fully installed

2-sudo /usr/bin/system-config-display

and got as an answer: 

command does not exist

b) Regarding office 2003 installtion, as a newbie to Linux and long time win user I installed Crossover Office. I think it was properly installed. After that I installed office just as I would in win: Pressing Next, Next :???:

---

### Post by aysiu on 2006-12-20
Then definitely try this command first: ```
sudo aptitude update && sudo aptitude install ubuntu-desktop
``` That will make sure you have all the necessary components installed.

---

### Post by johnnyw on 2006-12-20
Hey guys you are so quick and respect each other, I really love ya ( in a no gay way :mrgreen: )

I´ll try those commands ASAP.

J ( from Buenos Aires)

---

### Post by aysiu on 2006-12-20
If that command is successful, **then** try ```
sudo dpkg-reconfigure xserver-xorg
``` and then ```
sudo /etc/init.d/gdm restart
``` If it's *not* successful, post back any errors here.

---

### Post by johnnyw on 2006-12-21
It did not work. 

This one worked:

sudo aptitude update && sudo aptitude install ubuntu-desktop

could not make to work the other commands you mentioned.

TIA ( thank you in advance )

---

### Post by aysiu on 2006-12-21
Can you be more specific?

---

### Post by johnnyw on 2006-12-21
I´ve edited my post in which I did not say much :D

---

### Post by aysiu on 2006-12-21
[quote=johnnyw]could not make to work the other commands you mentioned.[/quote] I still need more details than that.

After you typed ```
sudo dpkg-reconfigure xserver-xorg
``` what happened? Did it take you through the blue/grey/red wizard and ask you a bunch of questions? If not, what did happen? If so, were there any error messages afterwards? After you typed ```
sudo /etc/init.d/gdm restart
``` what error messages did you get, if any?

"It didn't work" won't get us any closer to fixing the problem.

---

### Post by johnnyw on 2006-12-21
> **aysiu said:**
> I still need more details than that.

After you typed ```
sudo dpkg-reconfigure xserver-xorg
``` what happened? Did it take you through the blue/grey/red wizard and ask you a bunch of questions? If not, what did happen? If so, were there any error messages afterwards? After you typed ```
sudo /etc/init.d/gdm restart
``` what error messages did you get, if any?

"It didn't work" won't get us any closer to fixing the problem.

1)After I used the  command  : sudo aptitude update && sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm restart

I got something that said:

downgrade the following packages:
gimp... and the list kept on going

and I press yes and it started downloading a bunch of things

2) When I tried sudo dpkg-reconfigure xserver-xorg the command was to recognised.

3) I have not tried using:sudo /etc/init.d/gdm restart as I thought command number 2 must be applied in order for 3 to work

---

### Post by aysiu on 2006-12-21
So it asked you to downgrade a bunch of packages. Sounds as if something is screwy with your sources.list.

Can you try this?

Download this sources.list I just uploaded to my website: ```
wget -c http://www.psychocats.net/ubuntu/dapper.list
``` View the contents to make sure my server hasn't been compromised and some other weird thing put into it (it should look like a bunch of archive.ubuntu.com web addresses): ```
cat dapper.list
``` Then back up your old sources.list ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
``` and make this one you just downloaded your new sources.list: ```
sudo mv dapper.list /etc/apt/sources.list
sudo chown root:root /etc/apt/sources.list
sudo chmod 644 /etc/apt/sources.list
``` Finally, run this command, using the new, fresh sources.list: ```
sudo aptitude update && sudo aptitude install ubuntu-desktop x-window-system-core
``` If that's successful, run ```
sudo dpkg-reconfigure xserver-xorg
``` and then ```
sudo /etc/init.d/gdm restart
```

---

### Post by johnnyw on 2006-12-21
tks m8 Ill give it a try ASAP

---

### Post by johnnyw on 2006-12-23
> **aysiu said:**
>  ```
sudo mv dapper.list /etc/apt/sources.list

```

I am stuck here. It prompts me: No such file or directory..

---

### Post by aysiu on 2006-12-23
But the first command worked?

Can you post the output of this command? ```
ls
``` There should be a file in your home directory called *dapper.list*.

---

### Post by johnnyw on 2007-01-13
Hi there I came back from holidays ;) 

the dapper file you mentioned exists after using ls

what should I do now?

---

### Post by aysiu on 2007-01-13
```
sudo mv dapper.list /etc/apt/sources.list
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
```

---

### Post by johnnyw on 2007-01-13
TY m8.. It gives me this:

xserver-xorg  broken or not installed :S

should I format as I used to do in winxp when this happened? I am kind of hopeless. I really thank AYSIU :D

---

### Post by aysiu on 2007-01-13
It says that even after ```
sudo aptitude install ubuntu-desktop
``` completed successfully?

---

### Post by johnnyw on 2007-01-13
I did´t pay attention to the outputs :-# 
Is there any way in which i can chek if installation of the desktop was a success?

---

### Post by aysiu on 2007-01-13
> **johnnyw said:**
> I did´t pay attention to the outputs :-# 
Is there any way in which i can chek if installation of the desktop was a success?
Well, xserver-xorg not being installed is not a good sign.

Since *ubuntu-desktop* is a huge metapackage (a package that points to other packages), let's try something smaller and to the point: ```
sudo aptitude update
sudo aptitude install x-window-system-core gdm
``` See if that gives you any errors. If it *doesn't*, then try these two commands: ```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
``` If it gives you errors, try to write them down and post them back here.

---

### Post by johnnyw on 2007-01-20
the first two commands gave me no error


sudo dpkg-reconfigure xserver-xorg 
gave me:

broken or not fully installed

sudo /etc/init.d/gdm restart 
gave me

command not found

---

### Post by aysiu on 2007-01-20
Hm... broken or not fully installed. That seems to be a problem. Can you try this, then? ```
sudo dpkg --configure -a
``` I'm not sure if that'll help...

---

### Post by johnnyw on 2007-01-20
should I type the apt commands first?
:-\"

---

