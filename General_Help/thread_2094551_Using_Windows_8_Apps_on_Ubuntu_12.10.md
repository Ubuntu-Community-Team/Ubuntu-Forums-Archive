---
title: "Using Windows 8 Apps on Ubuntu 12.10"
date: 2012-12-14
forum: General Help
---

### Post by SandroWylie on 2012-12-14
Hi everyone,  is there any possibility to run the Windows8 Apps from the AppStore on Ubuntu? Or is there anything similiar for Ubuntu?

---

### Post by Rexilion on 2012-12-14
> **SandroWylie said:**
> Hi everyone,  is there any possibility to run the Windows8 Apps from the AppStore on Ubuntu? Or is there anything similiar for Ubuntu?

Linux distributions have something similar for *years*...




it's called a 'repository' (short: repo). A centralized location storing software (and it's metadata) for convenient installation by it's users.




Marketing makes you think it's the next 'best thing'... it is not.

---

### Post by Mark Phelps on 2012-12-14
> **SandroWylie said:**
> Hi everyone,  is there any possibility to run the Windows8 Apps from the AppStore on Ubuntu? Or is there anything similiar for Ubuntu?

Probably NOT -- because, to do so, you would first have to install them INSIDE Ubuntu, and from what I read, these are downloaded and installed automatically inside Win8.

Also, while there is Wine, and its derivatives, which allow you to run SOME Windows apps in Linux, experience has shown that the newer the app, the less likely it will work.  It takes CodeWeavers some time to figure out what changes they need to make to Wine for the new app, and then release a new version of Wine for that.

In the meantime, before you try to run anything in Wine, you should first check the WineHQ website, the application compatibility database, for the app and version you want to run.

If it is not listed, or if it has a rating less than Gold, installing it is going to be pretty much a waste of your time.

---

### Post by BlinkinCat on 2012-12-14
Here are the two Wine Sites in question -

[http://appdb.winehq.org/](http://appdb.winehq.org/)

[http://forum.winehq.org/](http://forum.winehq.org/)

Cheers - :p

---

### Post by Rexilion on 2012-12-15
Even if wine was able to run these apps, how would you access the store? Isn't that Windows 8 only?

---

### Post by Mark Phelps on 2012-12-15
> **Rexilion said:**
> Even if wine was able to run these apps, how would you access the store? Isn't that Windows 8 only?

Isn't that what I already said in post #3??

---

### Post by Rexilion on 2012-12-15
It was not explicitly mentioned that Ubuntu cannot access the store. Cuz if you could access it then, maybe with some fuzzing, you could make it work.


For example, wine offering a portal to the store pretending it's a valid Windows copy.

---

