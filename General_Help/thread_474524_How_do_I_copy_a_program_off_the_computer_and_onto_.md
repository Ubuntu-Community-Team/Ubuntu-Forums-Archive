---
title: "How do I copy a program off the computer and onto a disk?"
date: 2007-06-15
forum: General Help
---

### Post by weblordpepe on 2007-06-15
Hi there.

I'm a little lost. How can I copy a program off my Ubuntu computer and put it on a disk? Lets pick one at random - say aMSN.

It comes as a .deb, right? I downloaded it using the package manager so don't have the .deb. Or lets say that I didn't use the package manager and I deleted the .deb that I got off the web.

How can I go about this? Something with the package manager? I'm stuck. I would like to put a .deb onto a CDROM for my friend Joe McRandom who doesn't have the internet.

---

### Post by rich.bradshaw on 2007-06-15
you can look in /var/cache/apt/archives for packages downloaded using apt/synaptic etc.

You can use apt-get to just get the package for you, but can't remember how, try apt-get /?

---

### Post by weblordpepe on 2007-06-15
Well I would like a .deb to be created from the program already installed.

Basically I have the program on the computer. Synaptic/apt-get know how to delete the program off the computer but..

but I want to copy it onto a disk. My friend Joe McRandom doesn't have an internet connection and for the sake of it lets say I don't either.

I just want to copy a program to a disk.

---

### Post by jwh400 on 2007-06-15
The easiest way is to download the .deb package to your desktop then copy it to disc.

[Debian Packages]("http://packages.debian.org/stable/")

Edit: Never mind, I see what you're asking now. Would this have to be done as an ISO image?

---

### Post by weblordpepe on 2007-06-15
But but but but.
That isn't what I asked. I don't have an internet connection. Just got the program on the computer. 
I want to copy it off the computer and onto a disk. Or have a .deb file created from the installed software..which can then be put on a disk.
At all possible? ...without downloading.

---

### Post by weblordpepe on 2007-06-15
Hmm Im just looking through this.

Its pretty much what I wanted but there's no way of looking for dependencies. It would be nice if the package manager let you drag/drop programs onto the desktop, and created a .deb for you.

---

