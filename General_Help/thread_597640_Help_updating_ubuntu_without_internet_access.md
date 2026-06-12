---
title: "Help updating ubuntu without internet access"
date: 2007-10-30
forum: General Help
---

### Post by quickspark on 2007-10-30
Theres an ubuntu update that will allow me to connect to the internet. Right now, I can connect on my windows to the internet but not on ubuntu. I would like to know if there is any way I could download the updates on windows, put it on a usb stick and then install them on ubuntu.

Basically, I'm looking for a link to download ubuntu updates, any help?

And this is all very strange, as I have had ubuntu working for 2 months (with internet from the start) and when I decide to reinstall it, I can't access the internet.

---

### Post by ago on 2007-10-31
You can download the packages manually here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Note that you need to know in advance the package names and their dependencies.

Once in Ubuntu you install them with the command "dpkg -i" starting with the dependencies

---

### Post by quickspark on 2007-10-31
> **ago said:**
> You can download the packages manually here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Note that you need to know in advance the package names and their dependencies.

Once in Ubuntu you install them with the command "dpkg -i" starting with the dependencies

Thanks alot man, thats exactly the advice I was looking for.

---

