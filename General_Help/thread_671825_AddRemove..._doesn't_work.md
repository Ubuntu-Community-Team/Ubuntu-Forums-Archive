---
title: "Add/Remove... doesn't work"
date: 2008-01-18
forum: General Help
---

### Post by Will Pittenger on 2008-01-18
I can uninstall stuff with it, but all the stuff I tried to install was marked "cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."

Furthermore, when I attempt to install something or refresh the application list, I see a message box with "The list of applications is not availabe  Click on 'Reload' to load it. To reload the list you need a working internet connection."  (The misspelling and grammar error are in the actual box.)

The refresh acts like there are no errors, but the situation doesn't improve.  In the case of one program that won't install, GParted, it runs (although with bugs) when I boot the install CD.  So why isn't GParted supported?

---

### Post by LaRoza on 2008-01-19
* What version of Ubuntu do you have?
* Is it 64 bit or 32 bit?
* What are you trying to install?

What does:

```

sudo apt-get update

```

```

sudo apt-get install gparted

```

do?

---

### Post by Casual Fan on 2008-01-19
I'm pretty sure you just need to go to system>administration>software sources>ubuntu software and make sure all the boxes are checked.

But I could be wrong.:)

---

### Post by Will Pittenger on 2008-01-19
> **LaRoza][LIST]
[*]What version of Ubuntu do you have?
[*]Is it 64 bit or 32 bit?
[*]What are you trying to install?[/LIST]What does:

```
sudo apt-get update
sudo apt-get install gparted
```do?
[/quote]
```
root@WLP-Linux:/# apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done
root@WLP-Linux:/# apt-get install gparted
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gparted is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gparted has no installation candidate

```[quote=Casual Fan said:**
> I'm pretty sure you just need to go to system>administration>software sources>ubuntu software and make sure all the boxes are checked.

But I could be wrong.:)
That is far better.  It is downloading, but may not change much.  I will post again after it finishes with all results.

---

### Post by Will Pittenger on 2008-01-19
[COLOR=Black]Definite improvement.  Thanks.[/COLOR]

---

