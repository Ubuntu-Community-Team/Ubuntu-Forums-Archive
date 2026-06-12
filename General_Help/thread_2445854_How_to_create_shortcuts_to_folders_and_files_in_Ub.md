---
title: "How to create shortcuts to folders and files in Ubuntu 20.04?"
date: 2020-06-20
forum: General Help
---

### Post by itzpastor on 2020-06-20
Hello, I'm relatively new to Ubuntu and I couldn't find a way to create shortcuts to files and folders for my desktop.
For example, I have a .txt file on my external hard drive and to avoid having to open 200 folders until I get to the file whenever I open it, I would like to create a shortcut (which will be on my desktop) for this purpose. It is possible?

---

### Post by ActionParsnip on 2020-06-20
Ubuntu 20.04 if you use Gnome doesn't allow desktop icons. I suggest you use the file manager and use favourites there. You can have lots of easily selectable icons in the left panel to accellerate access to the directories you use most

---

### Post by TheFu on 2020-06-20
i can't help with GUi stuff, but symbolic links are a file system capability for all Linux file systems.  They can be placed anywhere and point to any other location on a Linux file system.

UPDATED - thanks Dennis N! - 
There are multiple forms of the command but 
```
ln -s (existing file|directory) created_link_name
``` is common.  The target can be a directory and a link from the source will be made.  Try it out, see how it works.  if no target is provided, the PWD is used.  The manpage summary:
```
       ln [OPTION]... [-T] TARGET LINK_NAME
[B]       ln [OPTION]... TARGET
       ln [OPTION]... TARGET... DIRECTORY
[/B]       ln [OPTION]... -t DIRECTORY TARGET...
```

Actually, the manpage use of "TARGET" is opposite what we normally think of as the target.  The "TARGET" above already exists and is a file.  The created link will be the LINK_NAME or will be the name of the file linked into the DIRECTORY.

For example, there's a program in /opt/data/some-program/bin/ and I don't want to add that funky path to the global PATH environment variable.  ~/bin/ **is** in my PATH, so **ls -s /opt/data/some-program/bin/some-great-program ~/bin/** will create a symbolic link ~/bin/some-great-program. That link can be used almost always like the real program, if the developers wrote their code correctly. Some shell scripts need very special handling to allow that.

But for Desktop links, it should "just work" for everything except snap packages (which are constrained).

---

### Post by T6&amp;sfpER35% on 2020-06-21
or you could install the xfce DE (which would make it xubuntu) ,which does allow desktop icons/shortcuts

[https://linuxconfig.org/install-xfce-xubuntu-desktop-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/install-xfce-xubuntu-desktop-on-ubuntu-20-04-focal-fossa-linux)

---

### Post by Dennis N on 2020-06-21
> There are multiple forms of the command but
```
ln -s  source target 
```
is common.
The target can be a directory and a link from the source will be made.
The order should be reversed. 
```
ln -s target source
```
The target is first, the source (or link name) is second.

---

### Post by TheFu on 2020-06-21
> **Dennis N said:**
> 
The target is first, the source (or link name) is second.

You are correct!  I'll mark that above!  I should have checked the manpage.  I usually just let the PWD be used.

---

