---
title: "Unable to locate package gnome-encfs-manager"
date: 2013-11-22
forum: General Help
---

### Post by rdh61 on 2013-11-22
Hi,

I am trying to download the package gnome-encfs-manager.

I have followed the instructions [here]("http://www.libertyzero.com/GEncfsM/") , in particular this:

```
sudo add-apt-repository ppa:gencfsm && sudo apt-get update && sudo apt-get install gnome-encfs-manager
```

But I am told the package cannot be located:

```
E: Unable to locate package gnome-encfs-manager
```

Any help gratefully received.

Many thanks.

---

### Post by heir4c on 2013-11-22
Look in your link unther that command, than you see this:
"Packages for Debian, Fedora and openSUSE can be found here"
Click on the blue word "here".
Then in that page you see click on the Debian-bottum and than at the bottum of the text-field you see a link about the binairy package (here is it in Dutch) 
Than 2 links pop up to .deb files. One for 32bit and 1 for 64bit. 
Choose one and click on it and you can install directly.

Ubuntu is based on Debian so you can use this .deb files.
Direct links:
32bit:
[http://download.opensuse.org/repositories/home:/moritzmolch:/gencfsm/Debian_7.0/i386/gnome-encfs-manager_1.8.4_i386.deb](http://download.opensuse.org/repositories/home:/moritzmolch:/gencfsm/Debian_7.0/i386/gnome-encfs-manager_1.8.4_i386.deb)
64bit:
[http://download.opensuse.org/repositories/home:/moritzmolch:/gencfsm/Debian_7.0/amd64/gnome-encfs-manager_1.8.4_amd64.deb](http://download.opensuse.org/repositories/home:/moritzmolch:/gencfsm/Debian_7.0/amd64/gnome-encfs-manager_1.8.4_amd64.deb)
I hope it will work.

---

### Post by rdh61 on 2013-11-22
Thank you heir4c.

Unfortunately I need a package for powerpc. Maybe there isn't one and that is why apt-get install cannot locate it?

---

### Post by heir4c on 2013-11-22
Ok, that something else.
What you can do is contact with the team of the program (in the link on the right you see some link to email to them):
[https://launchpad.net/~gencfsm](https://launchpad.net/~gencfsm)
Who knows they can help you.

---

### Post by rdh61 on 2013-11-22
I tried Cryptkeeper instead but it won't open. I'll open another thread about that!

---

### Post by heir4c on 2013-11-22
Ok, I hope you find a solution!

---

