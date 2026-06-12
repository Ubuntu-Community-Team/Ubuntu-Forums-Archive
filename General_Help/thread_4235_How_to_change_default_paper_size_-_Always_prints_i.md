---
title: "How to change default paper size - Always prints in A4"
date: 2004-11-13
forum: General Help
---

### Post by tog on 2004-11-13
I have set up the following printers using the Gnome Printing tool

HP4050 using jetdirect.
Xerox using lpd
Epson C80 using lpd

In all cases, even after setting the paper size to letter, and paper region to letter in advanced tab, output from these printers continue to insist on A4 paper. I tried changing the values in the printer configuration ppd, but I am sure that is not the way to do it. Even then, I still get A4 printout. Where can I change the default paper size systemwide? Thanks.

Murali

---

### Post by mr_ed on 2004-11-14
*bump*

Any ideas?

---

### Post by tog on 2004-11-14
Well, after much digging around, I tried one approach. I edited the /etc/papersize file to indicate letter rather than A4 as the default, BEFORE I set up any printers.  It appears to have worked for one of my test installations. Now, I am planning to go and try it on the systems that were there on my initial post. 

Murali

---

### Post by tog on 2004-11-17
I can confirm it now. Changing the value to letter in /etc/papersize before setting up the printers will set up the default as letter for all printers.


Murali

---

### Post by electroglas on 2004-11-29
This also fixed my problem on an HP Laserjet 4. 

Thanks

---

### Post by clasqm on 2004-11-30
[QUOTE=tog]I can confirm it now. Changing the value to letter in /etc/papersize before setting up the printers will set up the default as letter for all printers.
Murali[/QUOTE]

I'm glad you solved your problem. But forgive me for chuckling just a little: just once we see the 'Murricuns bumping into the same problem the rest of the world has been struggling with for the last 30 years!  :D

---

### Post by easy_target on 2005-02-15
So, what are the steps? I e already had a printer installed (LaserJet 4P), deleted it, modified the file and reinstalled it and I still get the left and bottom  margins off. Can you please give directions step by step?

Thanks!!!

---

### Post by edopizza on 2006-06-24
> 
I can confirm it now. Changing the value to letter in /etc/papersize before setting up the printers will set up the default as letter for all printers.

Murali



That fixed also my HP LJ 2550. 
THANKS!

---

### Post by Chilli Bob on 2007-03-28
WTF? It took me 4 hours to get my Brother DCP-115C to work, and now I have to delete it again in order to use A4 paper? That's crazy. (Still it's better than Win98)](*,)

---

### Post by ziffnabb on 2007-03-28
I had the same problem with my Canon Laser.  It would only happen in evolution though.  Would print fine from open office.  Luckily, my printer has a "Continue Printing" button, which I push, and then everything is fine.

The only thing I notice is that the print quality is not as good as in XP, however it could be that my cartridge is getting low.  Have not wanted to boot into xp just to test it.  Would have to probably wait an hour for my old anti-virus program to update itself.

Ziffnabb

---

### Post by userthebuntu on 2007-10-06
Oh noes...I have everything set to A4 paper size even /etc/papersize is set to a4 and my LaserJet 4 Plus still insists on printing on letter size paper...which is kinda hard to get around here in ye good ole Europe.

Does anyone have any suggestions?

Seriously...it's all set to A4: Printer setup using CUPS is set to A4, openoffice writer is set to A4,...

---

### Post by FuturePilot on 2007-10-06
......

---

### Post by Xi80r6 on 2007-12-16
I was having the same problem with the Canon iP1700 using the iP2200 driver. I figured it was just because I was using an unsupported driver that I was running into this issue. Any of you who have had to perform this install know that its tedious to say the least. So needless to say I was not looking forward to uninstalling the printer after I discovered this thread.

However, after editing etc/papersize/ from "a4" to "letter" it works every time. No need to set up before installing. Printer recognized immediately.

---

