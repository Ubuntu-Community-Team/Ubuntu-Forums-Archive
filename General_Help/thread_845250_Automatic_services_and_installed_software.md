---
title: "Automatic services and installed software"
date: 2008-06-30
forum: General Help
---

### Post by geo909 on 2008-06-30
Hello everybody,

back in XP times, when a program was installed it would 
set a couple of services to run on startup. Some of them were essential
but 90% of the time they were useless crap and one should run msconfig or services.msc to turn them off.

 My question is, is that the same in linux (particularly in debian related distros)? When I install something with apt-get or synaptic, will there be any services automatically set to start on boot? If yes, is it possible that there are useless ones? 

 Thanks in advance

---

### Post by avtolle on 2008-06-30
Look in System>>Preferences>>Sessions to see what is started upon boot. You can edit this to avoid things (or completely remove them) from starting that you don't use. As to adding, generally the user needs to add additional programs, apps, whatever, to start upon boot.

---

### Post by geo909 on 2008-06-30
The thing is that I currently don't use ubuntu for a while, I ask what is done in general.. If I apt-get install something, will it add services on startup?

---

### Post by avtolle on 2008-06-30
That is what I meant by the user adding them; I cannot say that there isn't something that will be added when the app is installed, but generally, there is a default set of apps to be run upon boot which doesn't change unless the user adds or deletes from the list. As I said, checking the System>>Preferences>>Sessions will let you see what is there. You can also do this after adding additional apps to see if anything was added to your list.

---

### Post by geo909 on 2008-06-30
Thanks a lot.. Got the idea!

Btw I can't go to System>>Preferences>>Sessions
because I don't have ubuntu, that is what I was talking
about..

---

### Post by forger on 2008-06-30
> **geo909 said:**
> Thanks a lot.. Got the idea!

Btw I can't go to System>>Preferences>>Sessions
because I don't have ubuntu, that is what I was talking
about..

You shouldn't have posted it here then :)
> General Help
All your general support questions for Ubuntu, Kubuntu, Edubuntu and Xubuntu.

But anyway, yes, it is possible that some stuff can be useless - to you, which is more of a personal opinion.

Ubuntu provides an all-around desktop solution, so some of it might seem bad to you. If you would use Ubuntu, you could easily disable stuff like that through System > Preferences > Sessions (package **gnome-session**), or System > Administration > Services (package **gnome-system-tools**)

If you're using debian, you can easily see what files are installed (after you install it), using: ```
dpkg -L name-of-package
```

---

