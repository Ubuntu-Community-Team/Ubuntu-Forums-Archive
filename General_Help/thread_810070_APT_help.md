---
title: "APT help"
date: 2008-05-27
forum: General Help
---

### Post by GammaPoint on 2008-05-27
Hi, I used to have Fedora on my computer so I'm trying to get used to this apt package manager. Here's a basic question that I've had trouble finding online and in the man pages.  

Let's say that I downloaded some files from a program call 'program' with the names 'program-engine', 'program-devel', and 'program-etc'.  

How do I view all the packages that I have installed of name program*?

Thanks for the help!

---

### Post by superyounan1 on 2008-05-27
> **GammaPoint said:**
> Hi, I used to have Fedora on my computer so I'm trying to get used to this apt package manager. Here's a basic question that I've had trouble finding online and in the man pages.  

Let's say that I downloaded some files from a program call 'program' with the names 'program-engine', 'program-devel', and 'program-etc'.  

How do I view all the packages that I have installed of name program*?

Thanks for the help!

why do you need to do that?

you could do:

```
dpkg -L <package name>
```

browse the man page for dpkg for other useful things

---

### Post by pointone on 2008-05-28
```
dpkg --list
```

...to view all installed packages.

So, naturally:

```
dpkg --list | grep <package>
```

---

### Post by Oldsoldier2003 on 2008-05-28
> **GammaPoint said:**
> Hi, I used to have Fedora on my computer so I'm trying to get used to this apt package manager. Here's a basic question that I've had trouble finding online and in the man pages.  

Let's say that I downloaded some files from a program call 'program' with the names 'program-engine', 'program-devel', and 'program-etc'.  

How do I view all the packages that I have installed of name program*?

Thanks for the help!

in addition to the above methods you can do a search in synaptic and the gui will give you a bit more detail on the packages.

---

### Post by GammaPoint on 2008-05-28
I see. Thanks for the help!

---

