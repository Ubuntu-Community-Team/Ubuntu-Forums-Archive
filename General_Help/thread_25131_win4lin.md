---
title: "win4lin"
date: 2005-04-09
forum: General Help
---

### Post by water on 2005-04-09
I've tried installing win4lin but [font=Verdana, Arial, Helvetica, sans-serif][size=2][font=Verdana, Arial, Helvetica, sans-serif][size=2]the install fails and i get the following error in the terminal window :  
[/size][/font][/size][/font] > installwinpro: launching guest installation... 
/opt/win4linpro/bin/mergepro-gfx: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory 
/opt/win4linpro/bin/mergepro-gmsg: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

has anybody managed to intall win4lin?

I've seen som threads indicating that it might be necesarry to patch the kernal, is this correct? if so does anybody know of good how-to for patching it for win4lin?

:water

---

### Post by Xian on 2005-04-09
[QUOTE=water]if so does anybody know of good how-to for patching it for win4lin?[/QUOTE]

Link: [Patching to Enable Your Kernel](http://www.netraverse.com/support/docs/kernel_patching.html)

---

### Post by water on 2005-04-10
turns out there's no need to patch the kernal with win4lin pro :grin:

all i had to do was install libgtk1.2

the only problem i've got now is that the istallation partly failed due to the cd not being recognized when the winxp installer requested it near the end of the installation. i'll give it another shot at work tomorrow.

:water

---

### Post by vtrac on 2005-04-13
[QUOTE=water]turns out there's no need to patch the kernal with win4lin pro :grin:

all i had to do was install libgtk1.2

the only problem i've got now is that the istallation partly failed due to the cd not being recognized when the winxp installer requested it near the end of the installation. i'll give it another shot at work tomorrow.

:water[/QUOTE]
 Did you get it to work?  What did you think of Win4Lin's performance?

---

### Post by water on 2005-04-14
The combination of Murhpy's Law & Catch 22 happening at work has made sure I haven't had the time to reinstall it... :neutral:

Hopefully I'll get time to give it onother shot during the weekend - if not it'll have to wait to the end of next week.

:water

---

### Post by Juzz on 2005-04-20
I'd be interested in hearing how win4lin is performing.

---

### Post by sgbeamer on 2005-04-20
I installed it in Warty with no problems.  I run Windows 2000 on it.  I have not upgraded to Hoary yet.  It looks like an implementation of Bochs or one of the other emulators and is a little slow even on my AMD64 3.0 GHz box with 1 G RAM.   I also have the older Win4Lin 5 which runs Windows 98 native and it is much nicer to use and extremely fast but can't run XP or 2000.

---

### Post by themelvin on 2005-04-21
I have problems with installing Mozilla, it shows the same error:
```

./mozilla-installer-bin: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

Where do I get this libgtk1.2* file and how do I install it.

Sorry, wrong thread.

---

### Post by loser72555 on 2005-04-23
try this command 

sudo apt-get install libgtk1.2-dev

---

### Post by Raven-sb on 2005-05-24
[QUOTE=loser72555]try this command 

sudo apt-get install libgtk1.2-dev[/QUOTE]

Thanks loser I was having problems with a number of programs that wouldn't install because of libgtk1.2 and couldn't figure out how to resolv the issue. Your post saved me a lot of frustration.:-P

Regards

Raven

---

