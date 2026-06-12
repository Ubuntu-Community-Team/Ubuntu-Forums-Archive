---
title: "Compiz CSM not changing settings"
date: 2006-09-17
forum: General Help
---

### Post by ironfistchamp on 2006-09-17
Hey all

I got XGL and Compiz working but that CSM thingy doesnt seem to change anything. I try to set it up how I want but it doesnt make anything different. Is there something I am doing wrong. 

Also it says something about not being able to load gconf.

Any help much appreciated

Thanks

Ironfistchamp

---

### Post by PriceChild on 2006-09-17
Try this command:

sudo chown user:user -R /home/user

Where "user" is your username.

This will make sure that everything in your home directory is owned by yourself, allowing applications spawned by yourself, including alacarte and csm to change settings.

---

### Post by Adrayic on 2006-09-17
I am having the exact same problem.  I got XGL and Compiz working but I can't change any of the settings via the CSM.  I come up with the following error while running "thefuture" script described in the tutorial.

dublstea@SERVER:~$ thefuture
dublstea@SERVER:~$ XGL Present
compiz: Couldn't load plugin 'gconf'

I dont have a /home/use directory so I tried the command you listed on the /home directory to no avail.  I still get the same error.  Any insight would be greatly appreciated.  I am new to Linux but would really like to get this working :)

---

### Post by ironfistchamp on 2006-09-17
Thanks for the reply but it didn't do anything. Any other suggestions?

Thanks

---

### Post by astoltz on 2006-09-17
Try: ```
chmod -R 755 ~/.compiz
```

---

### Post by Adrayic on 2006-09-17
Well... I feel like an idiot... but nevertheless, I figured it out. 

I got rid of the "thefuture" script and just booted into gnome without XGL/Compix starting up.  Then I opened the terminal and entered:

compiz-start

and everything works.  CSM is working as well.  I'm sure this was probably documented somewhere but I guess I just didn't find it.  Hopefully this works for you.

---

### Post by bryanchapman9999 on 2006-09-17
Same here. Compiz and xgl installed and working perfectly. I want to tone down the 'wobble' but using CSM makes no difference. I've edited the 'thefuture' script and removed it for now!

Help please.

Cheers
Bryan

---

### Post by 3rdalbum on 2006-09-18
You have to log out and restart XGL.

---

### Post by ironfistchamp on 2006-09-18
using compiz-start works perfectly. No more scipt for me.

Thanks

Ironfistchamp

---

