---
title: "Changing order of services to start"
date: 2005-03-29
forum: General Help
---

### Post by TjaBBe on 2005-03-29
With my laptop I allways access the internet via a wireless PCMCIA card. 
As this service is loaded after the synchronizing of the hardware clock to the Ubuntu server I would like to start this last service, wich now, offcourse, instantly failes, after the wireless connection is made. 

Is there some way to do this?

---

### Post by fdoving on 2005-03-30
[QUOTE=TjaBBe]With my laptop I allways access the internet via a wireless PCMCIA card. 
As this service is loaded after the synchronizing of the hardware clock to the Ubuntu server I would like to start this last service, wich now, offcourse, instantly failes, after the wireless connection is made. 

Is there some way to do this?[/QUOTE]
 There sure is.. in KDE you can use ksysv (which is in kdeadmin).. if you're not one of us KDE guys.. 

First, there is a system of files and filenames you should understand, bear with me.. 

The system is located in /etc/rc?.d/ and is like this:
Low number first.
S is for start.
K is for kill.

An easy example, if we have:

S11klogd
S12gdm
K99bootlogd

klogd will be started first, then gdm, and finally bootlogd will be stopped.


You can use update-rc.d (man update-rc.d) or rename the files in /etc/rc2.d yourself. This can breake your system, if you rename or move something you shouldn't.. and I strongly recommend using update-rc.d.


Hope you got something usefull out of this.

---

### Post by TjaBBe on 2005-03-31
[QUOTE=fdoving]There sure is.. in KDE you can use ksysv (which is in kdeadmin).. if you're not one of us KDE guys.. 

First, there is a system of files and filenames you should understand, bear with me.. 

The system is located in /etc/rc?.d/ and is like this:
Low number first.
S is for start.
K is for kill.

An easy example, if we have:

S11klogd
S12gdm
K99bootlogd

klogd will be started first, then gdm, and finally bootlogd will be stopped.


You can use update-rc.d (man update-rc.d) or rename the files in /etc/rc2.d yourself. This can breake your system, if you rename or move something you shouldn't.. and I strongly recommend using update-rc.d.


Hope you got something usefull out of this.[/QUOTE]

Thanks! I will try that when I get home. I'm afraid I'm not a kde kind of guy, so I will have to do it the second way then :).

---

