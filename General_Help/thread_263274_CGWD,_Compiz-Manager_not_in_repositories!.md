---
title: "CGWD, Compiz-Manager not in repositories!"
date: 2006-09-22
forum: General Help
---

### Post by dr_d on 2006-09-22
I've added these repos:

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main
deb [http://compiz-mirror.lupine.me.uk/](http://compiz-mirror.lupine.me.uk/) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main


But I cant install cgwd or compiz-manager...


Any suggestions?

---

### Post by goatflyer on 2006-09-22
Please post the output of the following commands so we can offer more specific help:

sudo apt-get update
sudo apt-get install cgwd

---

### Post by dr_d on 2006-09-23
hey..

sudo apt-get update doesnt give me any errors...

sudo apt-get install cgwd returns:

Package cgwd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package cgwd has no installation candidate



as for "referred to by another package" i'm pretty sure it's the right package name because from the nvidia xgl compiz tutorial:

sudo apt-get install xserver-xgl compiz-gnome cgwd cgwd-themes csm compiz-manager

([http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit))



any advise would be greatly appreciated.
cheers.

---

### Post by Juanra on 2006-09-23
The same thing happends to me..., csm package is not available and the compiz-plugins package(cgwd + cgwd-themes + etc, I think...) need it to install...

---

### Post by dr_d on 2006-09-23
glad to see i'm not the only one.. lol

maybe it's server end problem... if that's the case it should be fixed once it's noticed.

---

### Post by Darell on 2006-09-23
no they deleted their stuff! It's because they are working on a better version: Beryl.
It really sucks cause I had XGL + Compiz up and running 2 days ago, but now afeter a complete re-installation I can't install it anymore :(

---

### Post by dr_d on 2006-09-23
i thought beryl was a fork... and they were still maintaining packages for both versions?

that really sucks if everything is moving to beryl... because firstly the debs are not available yet and secondly the name sucks compared to compiz..

---

### Post by The Soundophiliac on 2006-09-23
You could use compiz-vanilla in the time being.

---

### Post by smylie on 2006-09-23
> **Darell said:**
> no they deleted their stuff! It's because they are working on a better version: Beryl.
It really sucks cause I had XGL + Compiz up and running 2 days ago, but now afeter a complete re-installation I can't install it anymore :(

exact same situation here. very annoying!
is there any other server's it's on?
how long you do reckon before it's back up?

cheers
Dave

---

### Post by dr_d on 2006-09-23
@ Dave,

yeah no idea... i'll probably hold off installing ubuntu until beryl comes out..

i guess just keep reading compiz.net and we'll see.. until then for me at least it's back to windows...

---

### Post by benjaminwr on 2006-09-23
Why do you want to go back to windows?, just because compiz isn't availlable for the moment... Im having the same problem aswell but I love gnome.

In the meanwhile metacity and gtk work great for me... anything rather that going back to win... not that I hate it... but, i love linux.

Im looking forward to seeing what they will do with beryl

Cheers

---

### Post by nik on 2006-09-23
Compiz has nothing to do with Ubuntu. Please go to compiz forums to ask about these things. Anyway, posted a reply here:
[http://www.ubuntuforums.org/showthread.php?t=263406](http://www.ubuntuforums.org/showthread.php?t=263406)

---

### Post by kipe on 2006-09-23
Any new ideas how to solve this?
I have the same problem I can't acces compiz through repositories! 
Thank you

---

### Post by Darell on 2006-09-23
I'm afraid you will have to wait until Beryl is out
It sucks I know :(

---

### Post by beerorkid on 2006-09-23
well this thread: [http://www.compiz.net/topic-4690-where-get-cgwd](http://www.compiz.net/topic-4690-where-get-cgwd)

has a few files attached.  seems like they are cleaning house or something.

would be nice if someone addressed this issue.

---

### Post by kikos on 2006-09-24
Is there any way to get these old packages?  A early version of Beryl is out, but it does not support ATI cards.

---

### Post by dr_d on 2006-09-25
@ benjaminwr,

yeah well it's kind of a long story... i dual boot with windows, and recently my ext3 partition got fuxored... so i was going to reinstall ubuntu... but i'll just wait until beryl is released.

> In the meanwhile metacity and gtk work great for me... anything rather that going back to win... not that I hate it... but, i love linux.

myself i'm really into exploit research... while gdb under linux does provide a very nice environment, a lot more action happens under windows...  that said, there are a lot of other things (genetic programming, messing with compilers, networking at the raw socket level, etc) that i would never do under windows.

so i wouldn't say that i love or hate either one... they're both good in different ways...

---

### Post by Dinerty on 2006-09-25
For people wishing to install the missing packages, check out:

[http://forum.beryl-project.org/topic-4690-2.html](http://forum.beryl-project.org/topic-4690-2.html) post #17

---

### Post by testube_babies on 2006-09-25
All individual packages are also available on [http://beerorkid.com/compiz/](http://beerorkid.com/compiz/)

---

### Post by beerorkid on 2006-09-25
sweet they must of put them back up.

nice find.

---

