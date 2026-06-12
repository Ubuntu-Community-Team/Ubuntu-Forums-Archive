---
title: "[SOLVED] Problems with Emerald"
date: 2008-04-30
forum: General Help
---

### Post by slughappy1 on 2008-04-30
Has anyone else been having problems with Emerald not starting up like it should? In System -> Preferences -> Sessions, I added:
```
Name:     Emerald
Commands: emerald --replace
Comment:  Starts Emerald
```
But when I start up Ubuntu, metacity starts up. Why doesn't emerald start up at boot time? After it loads if I press Alt + F2 and type in emerald --replace it works just fine.

---

### Post by upforthedownstroke on 2008-04-30
I've had the same issue. Right now my emerald only functions after I open a terminal in X and run emerald. Emerald terminates when I close the terminal. I don't think it's possible to run an X program like Emerald in a virtual terminal...

---

### Post by slughappy1 on 2008-04-30
Well for that problem if you want this is what to do in the terminal ```
emerald --replace &
```This will allow you to close the terminal. You should also be able to press Alt + F2 and type in ```
emerald --replace
```

---

### Post by Stealth on 2008-04-30
Darn it, how frustrating. Just updated my laptop to Hardy as well and now Compiz broke (just like it did on my desktop, but this one seems more problematic). emerald --replace, compiz --replace, none of that does anything. I actually had "compiz" working, but without window borders. Now after some uninstall/reinstalling, nothing works at all.

---

### Post by Zorael on 2008-05-01
I'm just guessing now, but whatwith Compiz getting more integrated into Gnome, Gnome gets better support for different window managers. Perhaps your command in Sessions is run *before* Gnome reads its settings and starts metacity? Alternatively, Emerald fails because there aren't any window compositors running, and what you think is metacity is actually gtk-window-decorator.

Someone knowledgeable in the Gnomey ways can likely help you change the default. I, on the other hand, would recommend that you disable visual effects, then install **fusion-icon** and have that handle window managers and decorators. Naturally, add it to Sessions, as well. And use ccsm to configure Compiz. (package name [b]compizconfig-settings-manager[/b)

---

### Post by Stealth on 2008-05-01
Is metacity required to start before I can enable Compiz? Either way, what I see weird is that doing a --replace with compiz does nothing except make me lose my borders. The only error I can see in the fusion-icon output is that it couldn't load plugin ccp, but I've read that others run Compiz fine despite that error. :confused:

--replace with emerald or gtk-window-decorator (while running metacity) does nothing at all. No changes, no flickers, no errors output, nothing.

---

### Post by Zorael on 2008-05-01
Metacity replaces Compiz, so running 'metacity --replace' makes Compiz shut down. Likewise, running 'compiz --replace' makes Metacity shut down.

Compiz needs a window decorator to draw titlebars and borders (emerald, gtk-window-decorator, kde-window-decorator). Make sure you have the Window Decorations plugin enabled in ccsm (compizconfig-settings-manager).

---

### Post by Stealth on 2008-05-02
Well, window decorator is enabled in the Manager, compiz --replace doesn't output anything, just eats my borders. Then running an emerald --replace also does nothing. How do I at least this stuff to tell me something? I know Compiz used to go through a check list about Nvidia drivers, XGL, loading plugins, etc.

---

### Post by Zorael on 2008-05-03
> **Stealth said:**
> Well, window decorator is enabled in the Manager, compiz --replace doesn't output anything, just eats my borders. Then running an emerald --replace also does nothing. How do I at least this stuff to tell me something? I know Compiz used to go through a check list about Nvidia drivers, XGL, loading plugins, etc.
Compiz doesn't output anything? What build are you using; self-compiled or from the repositories? It's certainly supposed to go through that check list.

And borders eaten = no window decorator running in 9/10 of cases.
```
$ compiz --replace &
$ emerald --replace &
```

---

### Post by Stealth on 2008-05-03
I'm pretty sure there from the standard Hardy repos. I have a compiz 1:0.7.4-0ubuntu6. Perhaps I should try a 3rd party repo?

Yea, definitely no output with those commands.

---

### Post by Zorael on 2008-05-04
```
zorael@sunspire:~$ apt-cache policy compiz
compiz:
  Installed: 1:0.7.4-0ubuntu6
  Candidate: 1:0.7.4-0ubuntu6
  Version table:
 *** 1:0.7.4-0ubuntu6 0
        500 http://se.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
```
Well, your compiz seems borked in some fashion. I'd try completely removing its packages and then reinstalling it, and if it doesn't work, give that compiz-git script a go. It has its own huge thread somewhere here in the Desktop Effects forum. ("How to get all compiz scripts something something")

```
$ sudo aptitude **purge** ~ncompiz ~nberyl ~nemerald ~nlibdeco
$ sudo aptitude update
$ sudo aptitude clean
$ sudo aptitude install compiz compizconfig-settings-manager emerald
```
Make well sure you don't have any extra repositories enabled which might mess things up.

---

