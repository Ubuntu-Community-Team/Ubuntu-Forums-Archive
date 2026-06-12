---
title: "aMSN stopped working..."
date: 2008-01-06
forum: General Help
---

### Post by Moonfrost on 2008-01-06
I have aMSN installed and use it a lot. All of a sudden yesterday it stopped working, I clicked on Applications/Internet/aMSN and nothing happens, also I clicked on the top panel menu in which I have a shortcut of it and still nothing happens...?

I tried uninstalling it from everywhere but can't find it thanks to the Ubuntu repositories always having the older version of aMSN (as usual) which I don't have installed, tried add/remove programs but still can't find it. So I downloaded aMSN again and tried re-installing...and this is some errors show up...these are the errors...

```
Checking for required C library versions ... OK
Checking for X ... OK
Checking for TCL Scripting Language ... OK
Checking for Tk GUI Toolkit ... failed
-------------------------------
Error: Could not find 'Tk GUI Toolkit'. Try using the native package manager for Ubuntu 7.10 (apt-get) to install a package with similar name to 'tk'. 

Error: Unable to prepare package AMSN MSN client.
```

And here is what I get when I try to start it from terminal

```
3: wish: not found
```

Help anybody?

---

### Post by patrickfromspain on 2008-01-06
If you want, you can install my amsn packages. It's the latest amsn version with antialiasing support. [http://ubuntuforums.org/showthread.php?t=649364&highlight=amsn](http://ubuntuforums.org/showthread.php?t=649364&highlight=amsn)

As for the problem, you don't have tk installed. You should: sudo apt-get install tk8.4

Hope that helps!

---

### Post by Moonfrost on 2008-01-06
> **patrickfromspain said:**
> If you want, you can install my amsn packages. It's the latest amsn version with antialiasing support. [http://ubuntuforums.org/showthread.php?t=649364&highlight=amsn](http://ubuntuforums.org/showthread.php?t=649364&highlight=amsn)

As for the problem, you don't have tk installed. You should: sudo apt-get install tk8.4

Hope that helps!

Well...how come it worked perfectly before for like 2 months?

---

### Post by patrickfromspain on 2008-01-06
Read my previous post:

**As for the problem, you don't have tk installed. You should: sudo apt-get install tk8.4**

;)

PS: if it's already installed: sudo apt-get install --reinstall tk8.4

---

### Post by Moonfrost on 2008-01-06
> **patrickfromspain said:**
> Read my previous post:

**As for the problem, you don't have tk installed. You should: sudo apt-get install tk8.4**

;)

PS: if it's already installed: sudo apt-get install --reinstall tk8.4

Yeah, I "installed" tk and it works perfectly but what I don't understand is that it stopped working out of nowhere, for no real reason...I didn't update it or anything...

---

### Post by patrickfromspain on 2008-01-06
maybe it was uninstalled automatically by apt, as it though it wasn't needed anymore.

---

