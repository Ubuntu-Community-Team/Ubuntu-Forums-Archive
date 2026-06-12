---
title: "Repositories....."
date: 2008-05-01
forum: General Help
---

### Post by Harkainos on 2008-05-01
Is there a dedicated list of Repositories out there? I would like to utilize the Synaptic Package Manager and install any software available.

---

### Post by Harkainos on 2008-05-02
bump :)

---

### Post by Bakon Jarser on 2008-05-02
I don't really understand what you're looking for.  The main, universe, and multiverse repositories should be enabled by default.  You can check to make sure under System > Administration > Software Sources.  

The only other popular repository I know of is the medibuntu repository, but I haven't needed it yet in 8.04.  I used it in previous versions for dvd support but there were different (easier) ways to do it in 8.04

But here it is.

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

If you want to get the latest versions of wine you can subscribe to their repository, but I wouldn't recommend it as they might not be stable.  You'll have to figure out how on their website.  [www.winehq.org](www.winehq.org)

---

### Post by Harkainos on 2008-05-02
that is pretty much what i was wondering. If there were any other repositories i may need. i did put the wine one in. ill put the mediverse in also, just in case. Thanks.

---

### Post by Achtung on 2008-05-02
The default repos should cover the needs of any regular user. You should not add another repository unless you need to download or you already have installed some piece of software that comes from it (and want to keep it up to date), as the extra repo will be scanned on every update. This may not seem like it matters much, but if the extra repo is not responding at the time you are updating, or if you simply have a big list of repos to update, it adds to your update time and eats your bandwidth. 

Add repositories only as you find the need for them.

---

### Post by Harkainos on 2008-05-02
should i disable the wine repo, unless i check to scan for it?

---

### Post by Achtung on 2008-05-05
If you use wine, you should keep it. 
If you do not use wine, you'd be better off unchecking the wine repo in the "third party software" tab of the software sources dialog, so that you're not scanning the repo for nothing. You can always add it later when you find a need for it.

---

### Post by forrestcupp on 2008-05-05
There are hundreds of 3rd party repos out there for various projects.  It all depends on what you want.  As far as I know, there aren't really any useful ones that have a lot of software.  Most 3rd party repos are just to keep updated on one certain app.

But if you want to keep more updated, you can enable your Unsupported and Pre-released updates.  Go to System->Administration->Software Sources, and in the Updates tab, enable them.  Remember to Reload after adding repos.

Also, it is ok to have the Wine repository enabled even though Wine is already in Ubuntu's repos.  It will just give you the latest version.

---

