---
title: "Can someone please help with a dreamweaver problem??"
date: 2007-10-13
forum: General Help
---

### Post by bustherh on 2007-10-13
Hi, I am running kubuntu fiesty and I bought crossover office to run dreamweaver mx, I have already posted this question on the codeweavers ticket system but it has been over a week and they have not replied yet.

I installed dreamweaver and it seems to work very fast and smooth except when I try to connect to a remote site it crashes with a "fatal exception" every time.
Someone else posted this to the codeweavers ticket system but he got it working by uninstalling then re-installing a few times, he surmised that it must have been a server problem.
I don't think it is a server issue because I have dreamweaver running on a xandross machine and it works just fine.

I tried uninstalling then re-installing several times but I still get the same problem. I tried changing the FTP port and it says host found and then loads for a while and then says "ftp error could not connect to host" but it does not crash so I am assuming that the default was the correct port (21) but when it receives the remote file info something causes it to crash.

I really need to get this to work, it is the only thing stopping my boss from switching all of our computers to ubuntu or kubuntu. We are sick of all the virus and spyware problems with windows, it has practically killed our business before.

I would appreciate any help or suggestions, I am not a linux guru though so you may need to hold my hand through the technical stuff.

---

### Post by cssutto on 2007-10-13
I can not help with dreamweaver, but I installed Kompzer and use fireftp and I find it to be very easy.

This from a guy that kept a windoze machine just so I could run FrontPage to maintain my web page.

No more FrontPage!!!!!

---

### Post by #Reistlehr- on 2007-10-13
You cant use Dreamweaver MX successfully on linux yet using crossover OR wine (Same thing basically).

The reas is because Dreamweaver runs two proccesses in the background, ~Exxxx.dll and another clone just like it. Crossover has not been successful at porting the required proccesses to have a dll run as an executable as Dreamweaver requires.

This was my biggest thwart. Though, i just use gedit and eclipse for all my programming and coding. 

I only liked dreamweaver because i had SVN, FTP and an editor all in one..

---

### Post by leg on 2007-10-13
There are a lot of alternatives to using dreamweaver in Linux. One or two have already been mentioned but my current favourite is Bluefish. You can manage projects like dreamweaver and there are plenty of tool bars for inserting tags and such. Not sure about integrated ftp as I use fireftp as one of the previous posters mentioned.

Give it a shot and remove your dependency on overpriced software.

---

### Post by TeaSwigger on 2007-10-13
It's working in WINE on Kubuntu here.

Lifted it from my working Windows 2kPro installation, and also had to borrow msvcp60.dll (what's more must be capitolized to MSVCP60.dll), plus xmlparse.dll and xmltok.dll (from Program Files/GTK/bin) for HomeSite. Disclaimer here that these are legit purchased copies of consumer versions of said software, so no claims as to its applicability to any other situations, and that I'm no expert on any of these things.

Also have to point out the importance of getting WINE set up well. It's fiddly.

Of course if your needs can be met by open source software I'd strongly suggest it. Quanta Plus and Bluefish look interesting, and there's lots of great linux ftp apps to use for ftp purposes if need be. For Kubuntu try Kasablanca for one. Fast and user friendly.

---

