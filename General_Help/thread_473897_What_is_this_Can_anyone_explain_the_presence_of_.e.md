---
title: "What is this? Can anyone explain the presence of .exe files in /usr?"
date: 2007-06-14
forum: General Help
---

### Post by mthakur2006 on 2007-06-14
Have a look at the screenshot please. You will see .dll files and .exe files in /usr/lib/beagle
Can anyone explain what is going on here?
Is this some kind of rootkit?
Thanks.

---

### Post by hikaricore on 2007-06-14
I LOLed at that screenshot.

I can't tell you why they're there, but I can pretty much say no they aren't a rootkit.  How did you come to that conclusion?

---

### Post by mthakur2006 on 2007-06-14
> **hikaricore said:**
> I LOLed at that screenshot.

I can't tell you why they're there, but I can pretty much say no they aren't a rootkit.  How did you come to that conclusion?

aren't .exe and .dll files a windows thing? :confused:

---

### Post by jasonlfunk on 2007-06-14
My guess is that the linux and windows files for beagle got mixed in the package. If you google "/usr/lib/beagle exe" there are plently of results. It isn't anything to worry about.:popcorn:

---

### Post by hikaricore on 2007-06-14
> **mthakur2006 said:**
> aren't .exe and .dll files a windows thing? :confused:

Yes EXE and DLL files are generally for windows and dos based environments.

Finding them on a Linux system is usually strange unless you're using WINE, but never is it a
sign of a rootkit or a malicious software program.  If you were able to run such software (windows
software that is) on your linux OS, absolutely nothing would come of it because rogue EXE files
can't hurt you in Linux (for the most part).  ^_^  Perhaps there was an error made when packaging
beagle for ubuntu and the windows binaries were included as well is my best guess.

---

### Post by mthakur2006 on 2007-06-14
oh cool
but why have exe packages?

---

### Post by happy-and-lost on 2007-06-14
Beagle is written in Mono, which uses the .NET framework, and thus uses .EXE and .dll files

Edit: [http://en.wikipedia.org/wiki/Mono_(software](http://en.wikipedia.org/wiki/Mono_(software))

---

### Post by mthakur2006 on 2007-06-14
> **happy-and-lost said:**
> Beagle is written in Mono, which uses the .NET framework, and thus uses .EXE and .dll files

Edit: [http://en.wikipedia.org/wiki/Mono_(software](http://en.wikipedia.org/wiki/Mono_(software))

aahhhhhhhhhhh
i get it.

---

### Post by happy-and-lost on 2007-06-14
Good :)

Mono looks like a very exciting newish project to keep an eye on. It already has some stellar apps built on it, namely: F-Spot, Banshee and Tomboy (not to mention numerous others!)

---

### Post by mthakur2006 on 2007-06-14
oh k
cheers for the info. :D

---

