---
title: "Wine For Ubuntu?"
date: 2007-04-21
forum: General Help
---

### Post by thesilfieszone on 2007-04-21
I downloaded the program, and am reviewing the readme file and came accrost this...
[I]
"3. REQUIREMENTS

To compile and run Wine, you must have one of the following:

  Linux version 2.0.36 or above
  FreeBSD 5.3 or later
  Solaris x86 2.5 or later
  NetBSD-current

As Wine requires kernel-level thread support to run, only the operating
systems mentioned above are supported."[/I]

does that mean that wine will not run with ubuntu? how can i get this program to run with ubuntu?

---

### Post by RaZer0r on 2007-04-21
it wil run, under linux 2.x.x they mean the 2.x.x kernel, and ubuntu is currently running under: 2.6.20-15

you will probably run the same version but if you want to check what kernel you are using just typ:
```

uname -r

```
in the terminal window

---

### Post by Irony on 2007-04-21
Follow the instructions here and you can install the latest Wine for Ubuntu;

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Or you could simply install wine from the ubuntu repositories.

---

### Post by thesilfieszone on 2007-04-21
> **Irony said:**
> Follow the instructions here and you can install the latest Wine for Ubuntu;

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Or you could simply install wine from the ubuntu repositories.

how do i do that. Thanks so much for your help. i'm brand new to linux (it's only been installed for like 3 hours or so HAHAHAH)

---

### Post by mojoman on 2007-04-21
> **thesilfieszone said:**
> how do i do that. Thanks so much for your help. i'm brand new to linux (it's only been installed for like 3 hours or so HAHAHAH)

Open up a terminal through the meny and in it write:

```
sudo apt-get update
sudo apt-get install wine
```

Or you can install it through the menu, with add/remove software but my advice is to get familiar with the terminal. In the long run, it's worth it.

/mojoman

---

