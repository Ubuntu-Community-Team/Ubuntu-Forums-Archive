---
title: "Screwed up a decent office 2000 install...help!"
date: 2007-05-31
forum: General Help
---

### Post by zachthejones on 2007-05-31
I got MS Office 2000 working pretty easily through wine using [these directions]("http://docs.mypclinuxos.com/InstallingOfficeWine").  Then I decided to tackle Dreamweaver....the only condition being that I have an old, old version of it, Dreamweaver 2.  I tried just running the install through wine and it acted like it had installed it, but Dreamweaver wouldn't run.  So I looked for more directions and found [these]("http://blog.publicidadpixelada.com/how-to-dreamweaver-running-on-ubuntu-in-10-easy-steps/")...which i followed up to the registry editing section.  It was there I decided to check my MS Office - and found it wouldn't work!

From there I figured i had messed up something copying all those files from my XP installation over, and decided to uninstall everything.  I used the good 'ole **apt-get remove wine** command and uninstalled it (after removing dreamweaver and ms office through wine's uninstaller - note, though, I just remembered I didn't uninstall the internet explorer in this process, I just reinstalled it over itself when I redid everything).  To finalize it, I deleted the hidden **.wine** folder.

I then redid my installation process of wine and internet explorer - but when I try to run the "setup.exe" my disc spins for awhile and then...nothing!

Any suggestions would be greatly appreciated!

---

### Post by dave-5B on 2007-06-01
there were probably some configuration files left from the original install

sudo aptitude purge wine

although im not sure if this works if you installed with apt-get in the first place, also Synaptic has "mark for complete removal", aptitude is like apt-get but newer and (apparently) better

being the free software nazi that i am, i have to ask.. why are you trying to install office and ie?

---

### Post by zachthejones on 2007-06-08
Thanks, I ended up completely uninstalling and deleting every trace of everything I could find associated with Wine or IE explorer - this time it worked and I was able to reinstall Wine and MS office correctly.  Thanks!

And yeah, I'd rather not use any microsoft product at this time, but I work with a lot of people that use MS office and I want to check my formatting to make sure that it will come up correctly in Word (and MS office needs IE to work...yay microsoft!).  As well as, I use Word to take notes in class and use the "document map" function heavily to organize my notes (which sometimes reach 30-40 pages) - and I haven't found the equivalent in any free word processor yet (OpenOffice, Abi Word, etc...), if you know of any, please let me know!

---

