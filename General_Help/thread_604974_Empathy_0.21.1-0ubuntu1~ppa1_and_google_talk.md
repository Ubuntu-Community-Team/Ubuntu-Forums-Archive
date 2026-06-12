---
title: "Empathy 0.21.1-0ubuntu1~ppa1 and google talk"
date: 2007-11-06
forum: General Help
---

### Post by ascii79 on 2007-11-06
Hi

I have installed Empathy 0.21.1-0ubuntu1~ppa1 from [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) gutsy main restricted universe multiverse

I am able to login and see a microphone against the buddy name .. When I click on it, opens a new window and everything is disabled on it ..

Want to know whether, I can do google talk or not ?

Regards,
Sachin.

---

### Post by suoko on 2007-11-08
I have the following 3 repo for empathy/telepathy in my source list:
deb [http://extindt01.indt.org/VoIP/apt/](http://extindt01.indt.org/VoIP/apt/) dists/unstable/main/binary-i386/
deb [http://ppa.launchpad.net/mantas/ubuntu](http://ppa.launchpad.net/mantas/ubuntu) gutsy main
deb [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) gutsy main restricted universe multiverse

try with them

---

### Post by ascii79 on 2007-11-08
No it didnt work for me .. :(

---

### Post by suoko on 2007-11-08
the way you're presented is ok: 
everything is disabled for me too but audio just works as soon as that window popups.
Regarding video I can see the output of my own camera but not the counterpart one.

Be aware that audio is working but I'm testing it with 2 pcs which use gutsy+empathy. I've no idea whether it works with the windows client or not.

---

### Post by ntetreau on 2007-11-09
I also installed evything from these repos but I cannot see the microphone beside the name of my googletalk friends... did you enable this somehow?

EDIT:  Actually, if I right click on the contact, there is a "Call" option although it is grayed out.

---

### Post by ramkumail on 2007-11-11
Hi,
 I am trying to voip gtalk windows users for almost two weeks. I am posting my experience here with every client. None seems to work. I am a new user. so please let me know if there is a mature gtalk voip client for linux. 
  I am behind a http proxy. so some programs dint connect and i cannot find any proxy config. options in them. being a new linux user i cannot also figure out what exactly is the error if some programs dint install and sometimes cannot deal with dependency hell.

Jabbin
 does chat well. No signal in gtalk windows when placed an audio call and no voice transmission. has proxy support

Gizmo project:(gtalk2voip)
 installed. did not connect. may be my proxy is blocking.

psi-jingle:
 cannot install. gave  some error. so i gave up.

ekiga:(gtalk2voip)
dint support proxy it seems.

openwengo:(gtalk2voip)
crashes after startup.

landell:
dependency not satisfied by the ubuntu package. cannot do svn because the proxy that i am behind doesnt support it.

free switch:
 said it cannot find make file 2. i have no idea what it is. 

(gtalk2voip) is a service that enables sip to communicate with other voips. more info at [http://gtalk2voip.com/](http://gtalk2voip.com/)

Since i am new linux the reasons are my own perceptions and can be wrong.
Is there any one who has successfully done gtalk voip to windows.
why cant ubuntu support some official package that will just do the job or google release a linux version of gtalk instead of just releasing jingle library.(though there are other use of jingle). 

ubuntu makers please listen to my crying voice..

doesnt have enough morale now to try empathy now. will face with it some other time.

 good luck for people trying gtalk voip in linux.

---

### Post by suoko on 2007-11-12
I tried to talk with a windows client of gtalk and found out that I can call from empathy  to win-gtalk but then I CAN'T answer the call.
below  is a list of  what I have installed:

libtelepathy-glib0                              install
libtelepathy2                                   install
python-telepathy                                install
telepathy-butterfly                             install
telepathy-core                                  install
telepathy-gabble                                install
telepathy-gnome                                 install
telepathy-haze                                  install
telepathy-idle                                  install
telepathy-mission-control                       install
telepathy-salut                                 install
telepathy-sofiasip                              install
telepathy-stream-engine                         install
libmissioncontrol-client0                       install
libmissioncontrol-server1                       install
telepathy-mission-control                       install
transmission                                    install
empathy                                         install
empathy-megaphone-applet                        install
libempathy-common                               install
libempathy-gtk-common                           install
libempathy-gtk6                                 install
libempathy5                                     install

---

### Post by ascii79 on 2007-11-12
> **ramkumail said:**
> Hi,
 I am trying to voip gtalk windows users for almost two weeks. I am posting my experience here with every client. None seems to work. I am a new user. so please let me know if there is a mature gtalk voip client for linux. 
  I am behind a http proxy. so some programs dint connect and i cannot find any proxy config. options in them. being a new linux user i cannot also figure out what exactly is the error if some programs dint install and sometimes cannot deal with dependency hell.

Jabbin
 does chat well. No signal in gtalk windows when placed an audio call and no voice transmission. has proxy support

Gizmo project:(gtalk2voip)
 installed. did not connect. may be my proxy is blocking.

psi-jingle:
 cannot install. gave  some error. so i gave up.

ekiga:(gtalk2voip)
dint support proxy it seems.

openwengo:(gtalk2voip)
crashes after startup.

landell:
dependency not satisfied by the ubuntu package. cannot do svn because the proxy that i am behind doesnt support it.

free switch:
 said it cannot find make file 2. i have no idea what it is. 

(gtalk2voip) is a service that enables sip to communicate with other voips. more info at [http://gtalk2voip.com/](http://gtalk2voip.com/)

Since i am new linux the reasons are my own perceptions and can be wrong.
Is there any one who has successfully done gtalk voip to windows.
why cant ubuntu support some official package that will just do the job or google release a linux version of gtalk instead of just releasing jingle library.(though there are other use of jingle). 

ubuntu makers please listen to my crying voice..

doesnt have enough morale now to try empathy now. will face with it some other time.

 good luck for people trying gtalk voip in linux.


jabbin worked for me .. but I was not using proxy .. 

Empathy -- I was not able to make the call. But was able to receive it.
During that time I could hear my friend but he couldn't listen to me .

---

### Post by ramkumail on 2007-11-15
thanks for the info.. i will try empathy. i will give it my final shot.

---

