---
title: "Ubuntu Studio GDM theme"
date: 2008-07-03
forum: General Help
---

### Post by defcon3 on 2008-07-03
Hello: 

I have installed all ubuntustudio* packages via Synaptic. On all machines at home but one, the regular orange progress bar at startup is replaced by the Ubuntu Studio text (filling up/emptying) on both boot and shutdown. 

The one machine apart is acting weird, hence my message here: 
at boot time, the progress bar is the classic ubuntu orange
at shutdown, it is the one from ubuntustudio 

I tried selecting all ubuntustudio packages for reinstall, then purged them and installed them fresh - whatever I tried, it did not work on this single one machine. Please help me solve this mistery! 

I am not familiar with the boot process in the splash/logo thingies part. Grub I know well, including grub command line but not the fancy part... Can you imagine the hell I am going through when my girlfriends laptop isn't looking as mine
:lolflag:
and now that she has actually seen the "nicer" ubuntustudio on mine, she won't settle for reverting mine to the "old" orange bar... 

Silly to many, this may seem, but I need your help! Thanks a million.

---

### Post by Anzan on 2008-07-03
GUI:
System/Administration/Login Window

---

### Post by defcon3 on 2008-07-04
> **Anzan said:**
> GUI:
System/Administration/Login Window

And where exactly do you specify the boot progress bar?

---

### Post by angry_johnnie on 2008-07-04
Usplash can be configured/changed with startupmanager.
```

sudo apt-get install startupmanager
```

I believe it was in repos... :confused: if not, you can get it from [www.getdeb.net](www.getdeb.net)

Once it's installed, you'll find it in system > administration > startupmanager

---

### Post by defcon3 on 2008-07-04
> **angry_johnnie said:**
> Usplash can be configured/changed with startupmanager.
```

sudo apt-get install startupmanager
```

I believe it was in repos... :confused: if not, you can get it from [www.getdeb.net](www.getdeb.net)

Once it's installed, you'll find it in system > administration > startupmanager

I installed the package you recommended, selected the proper usplash from the menu, rebooted to find the system exactly as I wanted it! 

Thank you! :KS

---

