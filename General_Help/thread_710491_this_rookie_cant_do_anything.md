---
title: "this rookie cant do anything"
date: 2008-02-28
forum: General Help
---

### Post by 4me on 2008-02-28
1) i bought a sony vaio with 3GB's and 2 hard drives

2) i was able to 'partition' each drive...one with the windows vista and the other with ubuntu

both work.  that is the end of the good news

even trying to install automatix i get error: dependency is not satisfiable: tango-icon-theme-common

when i use the terminal i get 'couldn't find package'x''


any help would be appreciated.


do i need some 'basic' things before i get started?

---

### Post by Oldsoldier2003 on 2008-02-28
> **4me said:**
> 1) i bought a sony vaio with 3GB's and 2 hard drives

2) i was able to 'partition' each drive...one with the windows vista and the other with ubuntu

both work.  that is the end of the good news

even trying to install automatix i get error: dependency is not satisfiable: tango-icon-theme-common

when i use the terminal i get 'couldn't find package'x''


any help would be appreciated.


do i need some 'basic' things before i get started?
You might want to google for automatix. The general consensus I've seen in these forums is that automatix is dangerous to your system's stability (especially for a new linux user).

Use synaptic, aptitude or apt-get to install software and you're likely to have a lot better success and a more stable system.

---

### Post by pointone on 2008-02-28
Using Automatix is highly discouraged; it tends to break a lot of systems. You can install everything Automatix does with Synaptic/APT. 

For starters, try installing the "ubuntu-restricted-extras" package.

Make sure you have the universe and multiverse repositories enabled.

---

### Post by kellemes on 2008-02-28
> **4me said:**
> 1) i bought a sony vaio with 3GB's and 2 hard drives

2) i was able to 'partition' each drive...one with the windows vista and the other with ubuntu

both work.  that is the end of the good news

even trying to install automatix i get error: dependency is not satisfiable: tango-icon-theme-common

when i use the terminal i get 'couldn't find package'x''


any help would be appreciated.


do i need some 'basic' things before i get started?

Like previous posters I'd not use automatix unless the standard methods of installing packages don't work.
So.. what are you trying to do? Is there something you need to be installed? (besides automatix obviously)

---

### Post by tanman on 2008-02-28
If it helps at all I do a Podcast the is aimed towards new users. I try to stay away from to techy of issues.
I have a couple of videos on how to install applications. Have a look and maybe it will be helpfull.
The podcast is called MSC Giz Cast.

[MSC Giz Cast site]("http://www.mscgizcast.com")
Podcast epsiodes on Installing Applications:
[Video Episode 4]("http://www.mscgizcast.com/2007/11/msc-giz-cast-video-4-installing.html")
[Video Episode 5]("http://www.mscgizcast.com/2007/11/msc-giz-cast-video-5-installing.html")

---

### Post by 4me on 2008-02-28
the podcast sounds perfect......but of course i cant play it.  i download the plug ins and get an error message.

---

### Post by tanman on 2008-02-28
What are you getting for a error message?
Also did you go into synaptic and download Ubuntu restricted extras.
top panel click on system>administer>synaptic package manager. Do a search for ubuntu restricted extras and click to install. You will have to put a pasword in when opening synaptic.
I would also do a search for automatix2 in synaptic and make sure it is not installed.
hopefully this will help.
please let me know if it does.

---

### Post by 4me on 2008-02-28
good news.....looks like great progress.....found the 'software sources'.....even got some 'plug ins' going......then went for the gusto with 'compiz fusion', used the terminal and seem to have gotten it 'on', but

-have no effects
- have used system>admin>advanced desktop options.....and 'checked' the appropriate boxes and re-booted....

anything?

---

### Post by pointone on 2008-02-29
Try running "compiz --replace" from the terminal and see if any error messages are thrown.

---

