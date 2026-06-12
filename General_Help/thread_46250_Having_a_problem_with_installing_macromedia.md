---
title: "Having a problem with installing macromedia"
date: 2005-07-03
forum: General Help
---

### Post by FreeJack on 2005-07-03
[B]Hi I'm resently new to linux and Ubuntu and I stuck with several problems like installing macromedia 7.0 it does the whole thing installing then after the process is done its says it failed and gives the option to do it manually, anyone got any suggestions?? another thing is trying to install Opera browser  so I went to terminal typed "apt-get install opera-static"  it wrote Reading package lists...Done
Building Dependency tree...Done then E: Couldn't find opera-static 
Am I doing something wrong??[/B]

---

### Post by primeirocrime on 2005-07-03
Hello freejack and welcome.

YOu must have tried to install it through firefox. the best way to install your flash player is following the instructions on the unnoficial ubuntu guide here

[http://ubuntuguide.org/](http://ubuntuguide.org/)

and Opera not beeing free software is not in the official repositories for the Ubuntu gnu/linux distribution.
Once again you might find everything you need there at the guide.

cheers.

---

### Post by FreeJack on 2005-07-03
Thank you mate I did find it alot of answers there that I was looking for long time , although I'm pretty dispointed about Opera cause I'm having trouble with Firefox is another good fast browser that works on Ubuntu besides Firefox?

---

### Post by primeirocrime on 2005-07-03
You could try ** epiphany** or the **mozilla** suite, just go to synaptic and search there for the names or in web-browsers.

But what are your problems with firefox?

---

### Post by FreeJack on 2005-07-04
somehow it  have problem with language interface some debuging isn't responsing weird....with not all languages but one specific one on the site that i'm on

---

### Post by irish_rainz on 2005-07-04
On your issue of installing opera browser...you can go to [http://opera.com/download/](http://opera.com/download/)   and there is a Ubuntu download in the distro dropdown box.  Then choose a location, and download it to where you want...I usually download to my /home/ directory.  Then you open the terminal as root and type dpkg -i then full path name of where you downloaded opera.  For me, I typed:
dpkg -i /home/eadon/opera-static_8.01-20050615-qt_en_i386.deb

after it ran everything, I went to the run application under applications and simply typed "opera", clicked "yes I agree" and now I have opera.

I don't blame you about Opera, It has been my favorite for a very long time and it will run great on many different Linux OS.

Irish Rainz

---

### Post by FreeJack on 2005-07-04
ok another question I'm trying to install old opennap client called TekNap if anyone knows it , when i do **dpkg -i/home/roni/TekNap1.4.1i386.deb** it gives me 
dpkg: unknown option -/

T[B]ype dpkg --help for help about installing and deinstalling packages [*];
Use dselect for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].
[/B] I understand that I'm doing something wrong but i cant figure what it is a client for debian so it suppose to work or maybe i'm wrong and its not suitable for it?? :-?

---

### Post by RastaMahata on 2005-07-04
> **FreeJack]ok another question I'm trying to install old opennap client called TekNap if anyone knows it , when i do **dpkg -i/home/roni/TekNap1.4.1i386.deb** it gives me 
dpkg: unknown option -/

T[B]ype dpkg --help for help about installing and deinstalling packages [*] said:**
> .
[/B] I understand that I'm doing something wrong but i cant figure what it is a client for debian so it suppose to work or maybe i'm wrong and its not suitable for it?? :-?
 try this:```
sudo dpkg -i /home/roni/TekNap1.4.1i386.deb
```

---

### Post by FreeJack on 2005-07-06
thank you Rasta of course super user command, like i said i'm just a beginer but i begin to like it with your help of course 
never thought i will be able to install linux not even talking about making it work :)

---

