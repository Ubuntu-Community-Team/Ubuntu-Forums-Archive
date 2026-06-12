---
title: "Aptitude Menu has strange text"
date: 2007-04-25
forum: General Help
---

### Post by Rayzrshrp on 2007-04-25
Ok I'll do my best to describe this and have it make sense since I would really like to fix this.

I have 2 linux machines, one running Debian and the other running Ubuntu Fiesty Fawn.

I ssh into both of them from a Windows XP machine using the latest version of pUTTY.

When I login into my Debian box and run the command sudo aptitude the text drop down menus look normal and are easy to read. The same thing goes for tasksel or anything else for that matter which seems to be using ansi graphics in a text environment.

Now when I ssh into the Ubuntu box using the exact same setting in pUTTY the menus in aptitude and tasksel are all goofy looking with strange characters showing up.

I ran printenv on both machines and they both have term=xterm which is good so I don't understand what is different between these 2 machines. One does have mutt installed, the one that works correctly and the other, Ubuntu does not and has the goofy menus.

Below I will try to demonstrate the characters:

ââââââââââââââââââââââââââ
â Install/remove packages     g â
â Update package list             u â 
ââââââââââââââââââââââââââñ
â Mark upgradeable                 Uâ
â                                                â 
â                                                â
â                                                â
ââââââââââââââââââââââââââ

You get the jest from this I hope. It's like ncurses isn't installed or something but doing a apt-cache showpkg aptitude lists ncurses5 as being a dependent so any ideas?

What is different with my Debian box and my Ubuntu box to cause this?

---

### Post by bapoumba on 2007-04-25
Hi,
wild wild guess: UTF8 ?

---

### Post by Rayzrshrp on 2007-04-25
I have no idea. How would I check to see if that's what I'm using and or how do I change it?

---

