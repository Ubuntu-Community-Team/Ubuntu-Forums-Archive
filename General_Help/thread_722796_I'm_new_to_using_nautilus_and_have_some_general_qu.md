---
title: "I'm new to using nautilus and have some general questions."
date: 2008-03-12
forum: General Help
---

### Post by Pogeymanz on 2008-03-12
First, why does it have a file-browser mode and a regular mode?

Also, how can I make custom actions, like with Thunar? I like to be able to open a terminal in the directory I'm viewing.

Finally, what is YOUR nautilus like? I only just installed gnome, so mine's default. What cool stuff should I do to it?

---

### Post by ibuclaw on 2008-03-12
1) Regular Mode? I've never heard of it. Or at least don't think I have. How do you get to it?

2) Nope, sorry.

3) I have a texted based location bar and Emerald Enabled so it has a nice looking window top (which you can see there as I took a window screeny).

[[IMG]http://img135.imageshack.us/img135/920/filebrowserog8.th.png[/IMG]](http://img135.imageshack.us/my.php?image=filebrowserog8.png)

---

### Post by BlowflyBob on 2008-03-12
1. Not sure what you mean.

2. To add "Open Terminal" to the context menu:
```
sudo apt-get install nautilus-open-terminal
```

3. Layout of mine looks like the default, with the gtk theme applied, really don't know what tweaks are out there for Nautilus, I have never looked.

---

### Post by Oldsoldier2003 on 2008-03-12
> **BlowflyBob said:**
> 1. Not sure what you mean.

2. To add "Open Terminal" to the context menu:
```
sudo apt-get install nautilus-open-terminal
```

3. Layout of mine looks like the default, with the gtk theme applied, really don't know what tweaks are out there for Nautilus, I have never looked.

dont forget to 

```
killall nautilus
``` after installing any extensions to nautilus or they wont work...

---

### Post by ibuclaw on 2008-03-12
[QUOTE=OldSoldier2003]```
sudo apt-get install nautilus-open-terminal
```[/QUOTE]

Wow, I didn't know this.

Looked up "Nautilus" in Aptitude in the light of this, and there's quite a few cool looking stuff in the repository that could be worth looking into.

---

### Post by Oldsoldier2003 on 2008-03-12
[http://library.gnome.org/users/user-guide/2.18/gosnautilus-440.html.en](http://library.gnome.org/users/user-guide/2.18/gosnautilus-440.html.en) talks about ways to extend nautilus

---

### Post by Pogeymanz on 2008-03-12
Let me articulate myself better. When I said regular mode, what I meant was: when I click on, for example, the home folder on the desktop, it opens a window that is not the same as the file browser. This window is like a really crappy file browser.

Anyway, thanks for those tips. Very helpful!

---

### Post by oldos2er on 2008-03-13
One Nautilus extension I can't live without is nautilus-gksu.

---

### Post by PeterJS on 2008-03-13
> **EmosSuck777 said:**
> Let me articulate myself better. When I said regular mode, what I meant was: when I click on, for example, the home folder on the desktop, it opens a window that is not the same as the file browser. This window is like a really crappy file browser.

Anyway, thanks for those tips. Very helpful!

That's one of the first things I change when I setup a new machine, the "normal" mode is called spatial mode, and apparently some people like it. Don't ask me I don't understand it either. But more importantly you can disable it all together, in Nautilus under Edit > Preferences > Behavior, one of the options is to always open in browser mode.

In the more over all spirit of the thread, I'd suggest the packages:
nautilus-open-terminal
nautilus-gksu

---

