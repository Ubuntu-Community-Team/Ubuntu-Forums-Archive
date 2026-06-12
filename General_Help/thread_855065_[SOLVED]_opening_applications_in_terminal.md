---
title: "[SOLVED] opening applications in terminal"
date: 2008-07-10
forum: General Help
---

### Post by hamzaB on 2008-07-10
i'm new to ubuntu since i installed last week but i'm looking forward to learning the terminal . i learned all the basic commands and since i want to learn fast i decided to get to know the terminal by using it for a week and not touching the gui.my question is :how to open applications like firefox after pressing ctrl-alt-f1.and can anybody point me to a complete guide on how to operate the pc by only using that terminal.

---

### Post by mcduck on 2008-07-10
> **hamzaB said:**
> i'm new to ubuntu since i installed last week but i'm looking forward to learning the terminal . i learned all the basic commands and since i want to learn fast i decided to get to know the terminal by using it for a week and not touching the gui.my question is :how to open applications like firefox after pressing ctrl-alt-f1.and can anybody point me to a complete guide on how to operate the pc by only using that terminal.

You can't. Firefox is a graphical program, so it needs graphical environment to work.

But, generally, programs are started in terminal simply by using their name. For example, a common termial-based web browser would be Links2. it's started with command "links2".

---

### Post by Sealbhach on 2008-07-10
Here is a good start:

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)



.

---

### Post by hamzaB on 2008-07-10
so you can't open graphical programs in the terminal.but in when i typed firefox -h there was an option to specify the display.

---

### Post by hamzaB on 2008-07-10
@Sealbhach :actually i red that page but i was talking about using the terminal not the terminal emulator in the gui.

---

### Post by iaculallad on 2008-07-10
> **hamzaB said:**
> so you can't open graphical programs in the terminal.but in when i typed firefox -h there was an option to specify the display.

You CAN open graphical applications using the terminal. And remember to use **gksudo** before any GUI application command that needs authentication when you need to change/set settings.

i.e: 

```
gksudo gedit nautilus
gksudo gedit /boot/grub/menu.lst
```

---

### Post by danwood76 on 2008-07-10
Firefox relys on the X window system which isnt running in the CLI.
You can specify a display and but if X isnt running then it wont launch.

You can however launch firefox from a virtual terminal within X like the gnome terminal, where specifying thing slike which display etc will have an effect.
All programs in linux are launched from a command line, as they are in windows also, but not all apps run in a CLI only environment.

For example in the CLI you have to use nano (or vi, or whatever you like) instead of Gedit which is GUI only.

---

### Post by hamzaB on 2008-07-10
@iaculallad: so can you tell me how to open for example firefox while logged in in the terminal.

---

### Post by danwood76 on 2008-07-10
Read my post.
You CANT load GUI programs when logged in to one of the terminals (ctrl+alt+F1 etc) as there is no X running.

You CAN launch graphical apps from the virtual terminal within X like gnome terminal.

---

### Post by iaculallad on 2008-07-10
> **hamzaB said:**
> @iaculallad: so can you tell me how to open for example firefox while logged in in the terminal.

I was not clear with what I posted above: You can only open GUI applications if X server is active.

EDIT: Try to relate to the post above this post (2 post above this post actually).

---

### Post by hamzaB on 2008-07-10
@danxood76: thanks man for the response but i read a lot of power users saying that they only use the terminal for their day to day work.however,i'm not sure if they are talking about a terminal emulator or something else.anyway thanks for the replys and i hope i didn't annoy anyone with my noob questionq just that i wanted to become familiar with the cli so i can take advantage of its power.

---

### Post by danwood76 on 2008-07-10
I use the terminal a hell of a lot, what I meanb by terminal is the gnome terminal.
It acts the same as any of the terminals available on the F keys apart from the fact that you have a GUI and can launch GUI apps.

The F key terminals are very useful when X has died for some reason and you cant get it back!

You can't annoy people just by knowing less, the quickest way to learn is to ask questions ;)

---

