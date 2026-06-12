---
title: "Cairo Dock - main menu"
date: 2008-05-16
forum: General Help
---

### Post by laffinet on 2008-05-16
Is there a main menu (like the gnome main menu, including all applications etc.) in Cairo dock ? If so, where is it ? How can I create one ?

I might be blind or stupid or both, but I just can't find anything...

Thanks for the help.

---

### Post by YldGuy on 2008-05-16
i guess you are looking for an option to manage cairo-dock?

you need to right-click on the cairo-dock to get the options.

---

### Post by laffinet on 2008-05-16
I know how to manage the dock itself.

I'm looking for an applet (or some other way) to have the main menu on the dock. On the AWN dock I've got an applet that opens the main menu, which holds all my applications, preferences, administration. Just like the main menu that you would normally find in the gnome-panel.
Does this exist for Cairo ?

Thanks

---

### Post by YldGuy on 2008-05-16
oh that one. I am sorry, I am not aware of any. 

I used to use cairo-dock but AWN proved to be terrific. currently using AWN.

---

### Post by laffinet on 2008-05-17
Anyone ? Any ideas ? Thanks.

---

### Post by fabounet on 2008-05-17
in v1.5.6 : create a launcher and write **<ALT>F1** as the command.
then remove the menu from your gnome-panel, and click on the launcher. it should show you the menu :-)

---

### Post by laffinet on 2008-05-18
Hm, I've got v1.5.5.4 installed at the moment and it doesn't work there. Do you still have to have a gnome-panel at all ?

Can't find V1.5.6 anywhere, though. Where can I get it ?

I'd like to move from AWN to Cairo, but not having the main menu keeps me from doing that at the moment.

Thanks.

---

### Post by kawaji on 2008-05-18
Ver.1.5.6 has been planned to be released in this week.
It have a new function to make possible for launchers to run keyboard shortcuts.
So, Gnome main menu is available by clicking on a launcher(to run <Alt>F1).

for details :
[http://translate.google.com/translate?u=http%3A%2F%2Fwww.cairo-dock.org%2Fmr_article.php%3Fb%3D1%26a%3D25&hl=en&ie=UTF8&sl=fr&tl=en]("http://translate.google.com/translate?u=http%3A%2F%2Fwww.cairo-dock.org%2Fmr_article.php%3Fb%3D1%26a%3D25&hl=en&ie=UTF8&sl=fr&tl=en")

---

### Post by laffinet on 2008-05-18
I see.

I shall wait for the new version to come out and try it then.

Thanks.

---

### Post by carrara47 on 2008-11-02
Hi,
There is a discussion about the main-menu in the cairo-dock at

[http://ubuntuforums.org/showthread.php?t=699970&page=2](http://ubuntuforums.org/showthread.php?t=699970&page=2)

In this discussion I have attached a script that add the main menu to the cairo-dock creating a launcher for each of the menu entries. This script has some problems with encodings, but I have modified it and now seems to work. The usage is still the same of the old script (described in that post)

Bye

---

### Post by fabounet on 2008-11-03
actually, there is a main menu applet (called GMenu) in the 1.6.3 ;-)

---

### Post by VeeDubb on 2009-01-29
> **fabounet said:**
> actually, there is a main menu applet (called GMenu) in the 1.6.3 ;-)

fabounet, I have seen you say this in a dozen discussions it seems, but from what I can tell nobody can find it, and I also cannot find it in 2.0.0-beta1

---

### Post by fabounet on 2009-01-29
which package did you install ?
some 64 bits packages lack of this applet, and the terminal applet too.
or try to see some warning in the terminal about gmenu.

anyway if you're under a 64bits system, I recommend to install the 32bits packages with getlibs, it's easy to do and run smoothly, and this package is 100% complete because I built it myself ;-)

---

### Post by VeeDubb on 2009-01-29
After playing in the terminal, it looks like I am indeed missing libgnome-menu.

The problems, is that running Intrepid 64bit, I can't find any package that provides it, not even with getlibs.


But, it's okay.  I'm happy with the alt-f1 launcher hack.

---

### Post by fabounet on 2009-01-30
you can try to compile it, it's a small lib with few dependancy (despite its name, it is not related to gnome at all)
did you search in debian packages ? they may have it.
or on getdeb ?

---

### Post by VeeDubb on 2009-02-01
I was eventually able to install it by using

getlibs /usr/lib/libgnome-menu.so.whatever


Very nice once the dependencies are fixed up.

The only problems I had with using the alt-f1 launcher hack were that it was a little slow, especially on first launch after login, and that it's position was sometimes inconsistant.

The gmenu plugin fixed both of these issues.

All that's left now is waiting for a better systray, and a 64bit build with easier dependencies to solve.

---

