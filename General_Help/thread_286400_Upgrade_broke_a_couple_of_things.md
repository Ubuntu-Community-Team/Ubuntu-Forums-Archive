---
title: "Upgrade broke a couple of things"
date: 2006-10-27
forum: General Help
---

### Post by Codegen on 2006-10-27
I seem to have lost my shell (I forget what it's called, when you go Alt+F#). I still have the x terminal, but I'd prefer to have this one back.

I also appear to have lost the bootsplash, as well. This is no big deal, but I'm sort of anal when it comes to this typr of thing :D

Thanks.

---

### Post by Codegen on 2006-10-30
Well, I've tried reinstalling usplash, and I've tried adding vga=773 to my kerenl line in my menu.lst. All that did was make the messages 1024x768 instead 640x480.

---

### Post by jeblinux on 2006-11-02
I think when you say 'shell' you are specifically referring to the virtual terminal. To switch virtual terminals you need to use the key combination CTRL + ALT + F# when the X console is active on your screen. This is because the ALT + F# key combination is captured by the desktop environment.

For example, after you login through gdm and Gnome has started you can switch away from the X console by typing CTRL + ALT + F1. This brings you to the first virtual terminal. You can now just use ALT + F2 to switch to the second virtual terminal. ALT + F7 will bring you back to the X console. It may be better just to use the CTRL + ALT + F# combination at all times to minimize confusion.

Most Linux distros have ttys waiting for you on virtual terminals one through six and number seven is where X is started. See the configuration file '/etc/inittab' to see firsthand what I am talking about. BSDs are are a little different.

Can't say what is going on with usplash. Sorry.

---

