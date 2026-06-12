---
title: "Default User-Settings"
date: 2008-03-15
forum: General Help
---

### Post by Apfelmaennchen on 2008-03-15
Hi there!

Since Sabayon is constantly crashing on me (Ubuntu 7.10, amd64):

What other ways are there, to accomplish something similar?
First of all:
Is ther ANY documentation on "/etc/gnome-system-tools/user/profiles" available???

Since Ubuntu sets up the home-directory in a certain way, there needs to be some sort of skel-directory for it right?

If so: Where the heck is it???

Thanks in advance

Apfelmaennchen

---

### Post by pointone on 2008-03-15
I have no idea what you're asking or what you want to accomplish.

/etc/skel/ is the skeleton for the home directory, but isn't really necessary.

---

### Post by Apfelmaennchen on 2008-03-15
Sorry for being imprecise in the first place...

The problem:
The "users-admin" application of the gnome-system-tools provides three different profiles for new users - "Desktop user", "Unprivileged" and "Administrator".
However:
I couldn't find any documentation on how to expand/customize this somewhat limited set.

I finally figured out, that these profiles are set up in "/etc/gnome-system-tools/user/profiles" and was able to add new profiles with accompanying group and homedir settings.
Still:
The manpages of users-admin do not mention this file or anything related to it and I have no clue where to find information on the available options.
For Example:
Is there a way to provide DIFFERENT skel-directories for DIFFERENT profiles and if so, how's the syntax?

While I was searching for documentation on how to edit the aforementioned user profiles, I found multiple references to the program "Sabayon" which sounded very promising at first.
At the second look I cannot remember a single application crashing on me that often and reproducibly - not even back in the days I was running Win 3.1...

So my questions stand:
1. Is there DECENT Documentation for gnome-system-tools and the files it uses?
2. Is there a way to have it use different skel-directories for different roles?
3. Is there any other application that can do that - except the shell way using adduser?

Cheers
Apfelmaennchen

---

### Post by pointone on 2008-03-15
Besides the GNOME System Tools [home page]("http://www.gnome.org/projects/gst/") and Google, I don't know where else you could find information about this. GNOME System Tools uses [System Tools Backends]("http://system-tools-backends.freedesktop.org/"), if that helps.

In general though, "dpkg --listfiles <package>" is what I use whenever I'm curious about a package's configuration files, etc.

---

