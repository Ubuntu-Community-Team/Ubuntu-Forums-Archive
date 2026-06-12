---
title: "Remove applications without losing ubuntu-desktop"
date: 2005-06-17
forum: General Help
---

### Post by gwon on 2005-06-17
I'd like to uninstall the version of gimp that comes with Hoary, the problem is when I run "sudo apt-get remove gimp", it tells me that ubuntu-desktop will be removed to, which as I'm sure you all know could be slightly problematic ;)

So is there a way around this?

---

### Post by Seandq on 2005-06-17
[QUOTE=gwon]I'd like to uninstall the version of gnome that comes with Hoary, the problem is when I run "sudo apt-get remove gimp", it tells me that ubuntu-desktop will be removed to, which as I'm sure you all know could be slightly problematic ;)

So is there a way around this?[/QUOTE]

I'm thinking there's not. The way I look at it -- is that ubuntu-desktop is tied in and dependent upon GNOME and Gimp. With that being said, it can most likely be used with other desktops, yet it cannot be used without GNOME.

Why would you want to remove GNOME?

---

### Post by gwon on 2005-06-17
[QUOTE=Seandq]I'm thinking there's not. The way I look at it -- is that ubuntu-desktop is tied in and dependent upon GNOME and Gimp. With that being said, it can most likely be used with other desktops, yet it cannot be used without GNOME.

Why would you want to remove GNOME?[/QUOTE]
 sorry that was a mistype. I meant to say gimp.

---

### Post by tread on 2005-06-17
Removing ubuntu-desktop isn't dangerous unless you want to perform a dist upgrade, at which time it should be there to install any new packages available then. Till then you can remove ubuntu-desktop, it is just a meta package depending on all the packages the ubuntu people want to include in the desktop.

---

### Post by trivialpackets on 2005-06-17
[QUOTE=gwon]I'd like to uninstall the version of gimp that comes with Hoary, the problem is when I run "sudo apt-get remove gimp", it tells me that ubuntu-desktop will be removed to, which as I'm sure you all know could be slightly problematic ;)

So is there a way around this?[/QUOTE]
 ubuntu-desktop is not gnome.  It's a package that is searched for that installs all of the programs that you have currently, removing it will not disable your system.  No worries.  For kicks, search for kubuntu-desktop, and see how many packages that will give you.  :)

---

### Post by gwon on 2005-06-17
[QUOTE=eric.proctor]ubuntu-desktop is not gnome.  It's a package that is searched for that installs all of the programs that you have currently, removing it will not disable your system.  No worries.  For kicks, search for kubuntu-desktop, and see how many packages that will give you.  :)[/QUOTE]
 I knew it was a metapackage, I was just under the impression that you could uninstall the packages referenced in a metapackage by removing it.

That's perfect, cheers guys.

---

### Post by Seandq on 2005-06-17
[QUOTE=gwon]I knew it was a metapackage, I was just under the impression that you could uninstall the packages referenced in a metapackage by removing it.

That's perfect, cheers guys.[/QUOTE]
 Oops, my fault. Enjoy.

---

