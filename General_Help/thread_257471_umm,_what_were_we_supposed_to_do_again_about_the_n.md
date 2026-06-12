---
title: "umm, what were we supposed to do again about the new compiz updates???"
date: 2006-09-14
forum: General Help
---

### Post by user1397 on 2006-09-14
i thought i read somewhere on here that youre supposed to do something after downloading the new compiz updates to get them working again.  i just can't seem to find it tho.  does anyone know off the top of their head?  

btw, im using the fglrx driver from the repos, on a radeon x1600pro 512mb card.

---

### Post by sanone on 2006-09-14
ehm and the problem you have is? I have stuff working perfectly here without doing anything special? 

So what's the problem, version, etc?

---

### Post by user1397 on 2006-09-14
> **sanone said:**
> ehm and the problem you have is? I have stuff working perfectly here without doing anything special? 

So what's the problem, version, etc?well the problem is that no effects work, and i don't know how to tweak the new compiz manger/configuration app, so i dont know how to get those effects back.. everything was working before i installed the updates.

---

### Post by user1397 on 2006-09-16
bump

---

### Post by ayoli on 2006-09-16
everything works fine for me since last update, configuration is still doable thru csm ,just had a little bug with workspace switcher which is fixed now as  explained here: [http://www.compiz.net/viewtopic.php?id=4473](http://www.compiz.net/viewtopic.php?id=4473)

---

### Post by astoltz on 2006-09-16
You need use the new method to start compiz.  The compiz-core package now provides the command "compiz-start" that you should use instead of any scripts that you may have been using.  There is also a package called compiz-manager that provides a little icon in the notification area that will switch between metacity and compiz.  You'd have to install that one separately though as it does not get installed during the update.

---

### Post by user1397 on 2006-09-16
> **astoltz said:**
> You need use the new method to start compiz.  The compiz-core package now provides the command "compiz-start" that you should use instead of any scripts that you may have been using.  There is also a package called compiz-manager that provides a little icon in the notification area that will switch between metacity and compiz.  You'd have to install that one separately though as it does not get installed during the update.the compiz-start command worked for me.  that's all i needed to do.  thanks for the help.

---

