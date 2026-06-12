---
title: "Running a windows application in Linux?"
date: 2004-11-04
forum: General Help
---

### Post by HiddenWolf on 2004-11-04
What would be the most relatiable way to run an application that is built for windows without actually booting to windows.

There are a few programs I can't really do without, like the Customer Relations Management package that I make my money with. 

Are there emulators far enough along, do I need to use a virtual pc type thing, what are the options, which has the biggest chance of succes?

---

### Post by Rancoras on 2004-11-04
Give wine a try first.  If that doesn't work, vmware or something like it may be the only way.

---

### Post by cseg on 2004-11-04
sudo apt-get install wine winesetuptk

then

wine myApplication.exe

---

### Post by Artiom on 2004-11-04
or you can try Cross Over office  :wink: 

but it's not free option

---

### Post by HiddenWolf on 2004-11-04
Gives a weird error.

'can't find sql.ini' // one of the programs file
but it refers to an 'Y' disc

---

### Post by jwb on 2004-11-04
If it's something your're actually making money on..... i.e. it's a legitimate business expense and thus possibly dedectable, and you can balance it against revenue..... all that Biz School garbage, I highly recommend VMWare.

It's rather expensive- last I priced it was $299.... maybe more now. But- it runs Windows perfectly. You fire up VMWare from within Linux, boot VMWare into Windows, go to full screen mode, and you are in Windows. Files can be shared back and forth between the systems, too. You'll be able to seamlessly move between your Linux apps and Windows apps. When you're done with Windows, you can minimize the window, or just "pause" it, and close VMWare.

If you have a rather quick machine (P4 2.0 GHz+ with at least 512MB RAM..... 1GB is better) it will be fairly peppy and should run fine.

The cool part is, you can run multiple OS's at the same time if you're in to devlopment across multiple platforms. And you can test drive multiple Linux's at the same time. I had been using Fedora 1 a while back, and I compared Fedora 2, Madrake and SUSE- and had XP and Windows Server 2000 running under VMWare also. I actually managed to run 3 OS's at the same time, and it wasn't too slow. (Just to see if I could.)

I highly, highly recommend it.

No, I don't work for VMWare. :-)

---

### Post by FLeiXiuS on 2004-11-04
VMWare
Wine
Wine-X (Cedega)
Crossover Office

---

### Post by Burgundavia on 2004-11-05
Winex/Cedega is a fork of Wine, primarily meant for gaming
Crossover office is wine, with some additional polish on top

The major difference between vmware and wine is that wine is not trying to run windows, just windows programs. Vmware emulates a PC, so you actually  have a copy of windows running, thinking that it is actually on a computer.

Corey

---

### Post by HungSquirrel on 2004-11-05
It should go without saying, but you will of course need a licensed copy of your Windows install media to use VMware.  So, if you want to use VMware you should factor in the cost of it plus the cost of the Windows disc.

I have had horrible luck with Wine and Winex lately.

---

### Post by FLeiXiuS on 2004-11-05
[QUOTE=HungSquirrel]It should go without saying, but you will of course need a licensed copy of your Windows install media to use VMware.  So, if you want to use VMware you should factor in the cost of it plus the cost of the Windows disc.

I have had horrible luck with Wine and Winex lately.[/QUOTE]


I have a version if you would like it, shh :-P  Its cedega 4.1.1.

---

### Post by HiddenWolf on 2004-11-05
I've got a legal winblows. Have to call MS every time I reinstall it, but it's legal

My problem atm is to get my vmware demo working.

---

