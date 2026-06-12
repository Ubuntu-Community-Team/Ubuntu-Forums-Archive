---
title: "Problem with Wine repository (and repositories in general)"
date: 2021-02-20
forum: General Help
---

### Post by markblackrain on 2021-02-20
[SIZE=3][FONT=arial]Hello there. I'm new to Ubuntu and i'm having trouble with the repository while installing Wine. I'm using Ubuntu 20.10 Groovy Gorilla.
 I already installed Wine with sudo apt install wine (but it doesn't even appear in applications) so i followed a tutorial and i enabled 32 bit architecture with:
[/FONT][/SIZE]
sudo dpkg --add-architecture i386 


[FONT=arial][SIZE=3]then i tried to download and add the repository key with:
[/SIZE]

wget -nc [https://dl.winehq.org/wine-builds/winehq.key](https://dl.winehq.org/wine-builds/winehq.key)
sudo apt-key add winehq.key

Note: This lines were used from [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu) 

[SIZE=3]BUT this message appears: 


[/SIZE]Warning: apt-key is deprecated. Manage keyring files in trusted.gpg.d instead (see apt-key(8)).

[SIZE=3]
What can I do to solve this problem? 
[/SIZE]
[/FONT]

---

### Post by CatKiller on 2021-02-20
> **markblackrain said:**
> Hello there. I'm new to Ubuntu... I'm using Ubuntu 20.10 Groovy Gorilla. 

I would generally recommend that new users stick to the LTS releases rather than using the guinea pig interim releases. The important stuff gets backported to the LTS releases. 


> I already installed Wine with sudo apt install wine (but it doesn't even appear in applications) 

It wouldn't. It's a program for running other programs, rather than something that you run standalone. It doesn't get a launcher. By default it doesn't get the other handy menu entries (for things like the right click context menus) either. If you want a thing to launch so that you can manage those applications that run through Wine, Lutris is a good choice. 

> What can I do to solve this problem? 

There's nothing there that suggests that you have a problem. It's a warning message, not an error message, so the key likely successfully got added. At some point the instructions will be updated to show whatever the new-fangled method is instead.

---

### Post by markblackrain on 2021-02-21
Understood, thank you!

---

