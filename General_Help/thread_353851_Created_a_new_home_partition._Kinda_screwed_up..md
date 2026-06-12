---
title: "Created a new /home partition. Kinda screwed up."
date: 2007-02-05
forum: General Help
---

### Post by raul_ on 2007-02-05
I created a new /home partition using this guide:

[http://www.psychocats.net/ubuntu]("http://www.psychocats.net/ubuntu")

But something went wrong. When i restarted i noticed that my configuration options were back to the Ubuntu default: wallpaper,panel,theme,blablabla

So i tried to load aMsn and wondered "oh let me see if the theme folder is there" and it wasn't. So i compared the folder in the new /home partition and in the backup and they were different. So i tried copying all the hidden folders in my backup folder to my new /home and now it's fixed, but some things still bug me: For instance, i no longer have a favorite list application in USP.

I kinda screwed up first: forgot to rename the old /home folder. Did this affect the procedure? Should I do it again? Is copying a good solution,or just a crappy patch? 

Has anyone followed this guide? Because i wanted to make sure that if I do it again my preferences will be automatically be loaded, because copying alllllll the folders is a pain in the....well...u get the point :)

---

### Post by OffHand on 2007-02-05
If you have your old home folder you can just copy the stuff from there into your new one.

---

### Post by raul_ on 2007-02-05
Congrats for the 1000th post :) i'm on my way. 

Anyways, is it supposed to be like this? Not copying the hidden folders? (It's where all the configuration files from the applications are stored). Are those the only things missing?

---

### Post by OffHand on 2007-02-05
> **raul_ said:**
> Congrats for the 1000th post :) i'm on my way. 

Anyways, is it supposed to be like this? Not copying the hidden folders? (It's where all the configuration files from the applications are stored). Are those the only things missing?

Well, I made the same mistake as you and I copied the required files and folders manually because I wanted to keep the new home clean.

---

### Post by Rui Pais on 2007-02-05
> **raul_ said:**
> ...
Anyways, is it supposed to be like this? Not copying the hidden folders? (It's where all the configuration files from the applications are stored). Are those the only things missing?

No, you can use **cp -a /<mountpoint>/* /<destination>/** to copy all and preserving permissions.

Btw that guide seems too much complicated. 
When i need to do stuff like that i simply mount things and copy what i want with cp -a (sometimes full OSs...)

---

### Post by raul_ on 2007-02-05
Well i ended up just copying everything that was missing from the backup to the new folder. What brings me to the question:

Is that weird command really necessary? What would be the difference of just copying everything like Rui Pais said?

---

