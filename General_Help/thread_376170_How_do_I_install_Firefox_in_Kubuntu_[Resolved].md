---
title: "How do I install Firefox in Kubuntu? [Resolved]"
date: 2007-03-04
forum: General Help
---

### Post by Honayo on 2007-03-04
> yes but it just takes a simple command to install it  also, most tasks can be done with the built in web browser/file browser; Konqueror

Could you elaborate on this? I am very new to Linux and Konqueror seems to do just about everything that I need done. But, I'm very familiar with FF and it's available on the dual boot system with Ubuntu and the KDE DE.

---

### Post by aysiu on 2007-03-04
> **Honayo said:**
> Could you elaborate on this? **Method 1: Slow GUI Method**
Click on the KMenu. Go to System > Adept Package Manager.

Click *Fetch Updates*.  Under *Quick Filter*, search for the word *firefox*. Right-click the result *firefox* and mark it for installation. Then click *Commit Changes*. 

**Method 2: Faster CLI Method**
Open [a Konsole terminal](http://www.psychocats.net/ubuntu/terminal) and paste in this command ```
sudo aptitude update && sudo aptitude install firefox
```

**Now it's installed**
Firefox should now be available in your KMenu under *Internet*. If not, press Alt-F2 and type ```
firefox
```

---

### Post by Honayo on 2007-03-04
Konsole terminal is the way to go. Though I'm still using Konqueror, FF is now installed and waiting.
It was really quick and really easy. Thanks for the help and support here!:)

---

### Post by aysiu on 2007-03-04
> **Honayo said:**
> Konsole terminal is the way to go. Though I'm still using Konqueror, FF is now installed and waiting.
It was really quick and really easy. Thanks for the help and support here!:) Glad it worked out for you.

---

