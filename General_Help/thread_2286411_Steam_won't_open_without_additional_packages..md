---
title: "Steam won't open without additional packages."
date: 2015-07-12
forum: General Help
---

### Post by dsaechogaming on 2015-07-12
[ATTACH=CONFIG]263152[/ATTACH] 
I keep getting this message and I was wondering on how to install them.

---

### Post by QIII on 2015-07-12
Hello!

```
sudo apt-get install libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libc6:i386
```

should do it.

You will likely also get a lot of dependencies.

---

### Post by dsaechogaming on 2015-07-12
[ATTACH=CONFIG]263154[/ATTACH]
It didn't work

---

### Post by QIII on 2015-07-12
Which release of Ubuntu are you using and when was the last time you did 

```
sudo apt-get update
```

and

```
sudo apt-get dist-upgrade
```

---

### Post by dsaechogaming on 2015-07-12
[ATTACH=CONFIG]263155[/ATTACH]
I'm using the 14.04 release and Gnome. And I don't understand what this means.

---

### Post by QIII on 2015-07-12
The commands are to be executed one at a time.

Are you running a 64 bit installation or a 32 bit installation?

---

### Post by dsaechogaming on 2015-07-12
Sorry for the mess up. I'm using 64bit. And steam still needs those same 3 packages. Do I need to reboot to make it work?

---

### Post by QIII on 2015-07-12
Did you issue the command

```
sudo apt-get update
```

followed by

[sudo apt-get dist-upgrade[/code]?

(The last may require a reboot depending on what is upgraded, but you will be advised of that.)

Finally, issue

```
sudo apt-get install libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libc6:i386
```

---

### Post by Yellow Pasque on 2015-07-12
Does Ubuntu come with i386 enabled by default, or do you need to add it like you do on Debian?
```
sudo dpkg --add-architecture i386
sudo apt-get update
```

---

### Post by QIII on 2015-07-12
You may be on to something there ...

---

### Post by efflandt on 2015-07-12
64-bit 14.04 already includes 32-bit support. If you had kept your system up to date, you should have been able to just enter your password for sudo when installing or running steam per your original post, it should have installed those files. The only people who seem to end up with missing libs is if they install proprietary AMD/ATI graphics drivers (like fglrx) "before" installing steam. In that case they need to install steam "first", before installing drivers for AMD graphics (or install any missing 32-bit libs after).

That should not be a problem for default or nvidia graphics drivers. I have been running steam since Jan 2013 (originally in 64-bit Ubuntu 12.04 and currently in 14.04).

Note that if you manually update your system there is a difference between **upgrade** and **dist-upgrade** (see: **man apt-get**). Upgrade only upgrades existing packages if dependencies do not change, but might hold back packages that have changing dependencies. Dist-upgrade is much smarter about coordinating upgrades with dependency changes. Contrary to what it might sound like dist-upgrade upgrades the installed distribution version, it does not upgrade to a newer Ubuntu version.

---

### Post by dsaechogaming on 2015-07-12
How do you install steam before the drivers? I am using AMD, but don't the drivers install automatically?

---

### Post by Vladlenin5000 on 2015-07-12
> **dsaechogaming said:**
> How do you install steam before the drivers? I am using AMD, but don't the drivers install automatically?

The open source drivers - Radeon - yes, those are installed and in use, you wouldn't have video otherwise. Proprietary AMD drivers - fglxr - are the ones the user must explicitly install (System Settings > Software & Updates -> The rightmost tab "Additional Drivers" is the recommend method).

I agree with previous posts in that it seems the only users with such issues are the ones installing Steam after fglrx. However, I can't stress this enough, I NEVER had such issue in Ubuntu and I always install the proprietary drivers usually even before doing routine post-install updates. Likewise, in Manjaro - where proprietary AMD or Nvidia drivers are the default - installing Steam via AUR has always worked fine.

I strongly second Temüjin's suggestion:

```
sudo dpkg --add-architecture i386
sudo apt-get update
```

You have nothing to loose by doing this so...

---

