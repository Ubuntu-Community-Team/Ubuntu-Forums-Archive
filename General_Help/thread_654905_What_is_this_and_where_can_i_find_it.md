---
title: "What is this and where can i find it?"
date: 2007-12-31
forum: General Help
---

### Post by floydjunkie8 on 2007-12-31
Ok so i am switching to gutsy and am trying to follow this tutorial for my wifi card([http://ubuntuforums.org/showthread.php?t=588045&highlight=wusb54g](http://ubuntuforums.org/showthread.php?t=588045&highlight=wusb54g))

and in the thread it says to obtain:

> linux-headers-'uname -r' - which you can get from a quick search at packages.ubuntu.com 


i cant find this and am not even sure what it is

can someone give me a link or something

thanx

---

### Post by ~LoKe on 2007-12-31
In the terminal, type:
```
sudo apt-get install linux-headers-`uname -r`
```
They're the header files for the current kernel.

---

### Post by PeterJS on 2007-12-31
There are a bunch of packages all named linux-headers-<arch>, which contain the kernel headers that are needed to build system drivers, like your wifi drivers. What uname does is tell you about the architecture and other core system properties of your machine, the -r flag has it print just the architecture. So when put in to a shell linux-headers-`uname -r` will get translated in to the correct name of the headers package for your machine. To install them the full command would be:
```

sudo apt-get install linux-headers-`uname -r`

```

---

### Post by floydjunkie8 on 2007-12-31
will that work if i do not have internet

---

### Post by ~LoKe on 2007-12-31
> **floydjunkie8 said:**
> will that work if i do not have internet

No.

What is the output of **uname -r** in the terminal?

---

### Post by PeterJS on 2007-12-31
Well that depends, do you have the full install dvd handy? other than that you're going to need an internet connection to install anything. Couldn't you just hardwire yourself in until you get the wifi drivers setup?

---

### Post by floydjunkie8 on 2007-12-31
i hav a full install cd but it is not a dvd
will that work?

---

### Post by PeterJS on 2007-12-31
That's a real good question, I don't know. I know the DVD has *everything*, hence why it takes an entire dvd, the cd might, but I don't know, try it and find out.

---

