---
title: "Sessions trouble"
date: 2007-02-08
forum: General Help
---

### Post by redsp1der on 2007-02-08
Hi,

I new to Linux and I'm really starting to like it but...

I am having a problem with controlling my sessions. Specifically when I log in, the sessions control window automatically loads halfway off the screen (and apparently crashes because an error window pops up and asks if I want to report the bug) along with another window for a folder I use for storage a la My Documents. Also, gdesklets, which I have set to load on start up, loads the desklet I want but the gdesklets icon does not appear in the system tray nor do I see an entry for it in the system monitor processes tab.

This all started when I was messing around with the sessions control trying to tweak things like change the color of the login screen and probably more importantly set it to automatically save changes to session. I did not like how that dramatically increased start up time so I tried to change it back.

I figured that my problem was because the these windows were open during session that was saved on the last time I logged out with it set to automatically save had been set as the default. So, tried setting everything up back the way it was and turning the auto save back on before logging out. Then logging on and turning off auto save. Alas, this almost worked but I encountered a new problem. Gdesklets loads ok, it seems, but the desklet loads in a window with a title bar and everything along with a tab for it in the task bar.

So, currently my situation is as described in the first paragraph (note: the automatically save changes to session is unchecked) and I cant seem to figure out if something is broken or if I just don't know what I am doing.

Also, I'll just ask this now. Is there a list or something I could use as a reference to learn general/basic/must know terminal commands, keyboard shorcuts and such? Because currently I find it hard to understand exactly what it is I am doing when using the terminal. I just cut and paste, miming what some on teh internets said.

I ask this because in an effort to really learn more Linux I installed fluxbox to see if I could build myself a sweet minimalist desktop. However, I am greeted with a completely empty desktop and start menu. Is there a keyboard short cut to bring up a terminal window in fluxbox?

I'm rambling now.
Thanks

---

### Post by etank on 2007-02-08
> **redsp1der said:**
> 
Also, I'll just ask this now. Is there a list or something I could use as a reference to learn general/basic/must know terminal commands, keyboard shorcuts and such? Because currently I find it hard to understand exactly what it is I am doing when using the terminal. I just cut and paste, miming what some on teh internets said.
Thanks

Take a look at some of the guides on [http://tldp.org/](http://tldp.org/). You can run ```
man *comecommand*
```or```
info *comecommand*
```to read what its purpose is and how to use it. It is a good idea to understand what the command is supposed to do before you run it. You never know who is trying to be helpful and who isn't.

---

### Post by dagnabit dang doohickey on 2007-02-08
In addition to TLDP (which has a wealth of info), you can take a look at these sites which are geared toward new users.

[http://www.tuxfiles.org]("http://www.tuxfiles.org/")
[http://www.linuxcommand.org]("http://www.linuxcommand.org")

And, here are a couple of command reference sites:

[http://www.ss64.com/bash/]("http://www.ss64.com/bash/")
[http://www.linuxdevcenter.com/linux/cmd/]("http://www.linuxdevcenter.com/linux/cmd/")

---

### Post by RedSquirrel on 2007-02-08
> **redsp1der said:**
> 
I ask this because in an effort to really learn more Linux I installed fluxbox to see if I could build myself a sweet minimalist desktop. However, I am greeted with a completely empty desktop and start menu. Is there a keyboard short cut to bring up a terminal window in fluxbox?


No, there isn't a keyboard shortcut to bring up a terminal in Fluxbox when you first install it. You could add one later if you want. The first thing you need to do is to set up the menu. 

Have a look at this to help you get a menu in Fluxbox:

Fluxbox Community Doc
[https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)

There is a section on "Menu Customization" and one on "Keyboard Shortcuts".

---

### Post by redsp1der on 2007-02-08
Thanks for the links guys. They've got a lot of the info I've been looking for.

However, I am still having problems with the sessions on my Ubuntu desktop. Its still loading the two windows on startup even though I don't have it set to automatically save changes to sessions.

---

