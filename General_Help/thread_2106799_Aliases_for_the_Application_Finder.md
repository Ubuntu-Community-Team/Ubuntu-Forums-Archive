---
title: "Aliases for the Application Finder?"
date: 2013-01-20
forum: General Help
---

### Post by Alan_D. on 2013-01-20
Hello everyone,

I'm using Ubuntu 12.10 with XFCE. I really like XFCE, but one thing annoys me: the terrible long name of its terminal application ("xfce4-terminal").

My question is: can I somehow create a permanent alias which allows me to run a new terminal instance from the Application Finder (ALT+F2) by simply typing "terminal" instead of "xfce4-terminal"?

I already tried to create an alias in "/home/user/.bash_aliases", which works from inside an existing terminal, but the Application Finder seems to ignore this file...


Thanks,


Alan

---

### Post by sudodus on 2013-01-20
You are right, it is not convenient. By the way, running lubuntu-desktop in a system with 'all four desktop environments': Ubuntu 12.04 with lubuntu-desktop, xubuntu-desktop and kubuntu-desktop I get quick choices on a menu while typing, so I need not type more than say xfc to get all available completions.

But why not use the full power of a terminal window (with aliases, tab-completion etc)? In Xubuntu you can right-click on the desktop background and select 'Open terminal here'. Quick and easy :-)

---

### Post by Merrattic on 2013-01-20
Or just put a launcher in a panel.

If you need an alias, just create one in ~/.bashrc - towards the end of the file...

```
#myaliases
alias myterm = xfce4-terminal
```logout and in again for it to take. Probably won't work in Application Finder, but that is the long way round to open a terminal.

---

### Post by sudodus on 2013-01-20
> **Merrattic said:**
> [COLOR="Red"]Or just put a launcher in a panel[/COLOR].

If you need an alias, just create one in ~/.bashrc - towards the end of the file...

```
#myaliases
alias myterm = xfce4-terminal
```logout and in again for it to take. Probably won't work in Application Finder, but that is the long way round to open a terminal.
+1
I think there is a launcher for a terminal window in the default xubuntu desktop at least in some versions. Pull the mouse cursor to the bottom edge of the screen, and a panel will become visible. You can add launchers to that panel.

---

### Post by Alan_D. on 2013-01-20
First of all, thanks for your responses :)
I know that there are several ways to open a terminal. But somehow, I really got used to starting literally *everything* via ALT+F2 (imho one of *the* greatest inventions of the entire OS). And an application that I need as often as a terminal should have a shorter name than that, even if the Application Finder supports auto-completion (unfortunately, there are many applications starting with "xfce4-", so you have to type *at least* "xfce4-t"). But if the application finder is resistant against any aliases, I'll just have to stick with that...

Thanks,


Alan

---

### Post by sudodus on 2013-01-20
> **Alan_D. said:**
> First of all, thanks for your responses :)
I know that there are several ways to open a terminal. But somehow, I really got used to starting literally *everything* via ALT+F2 (imho one of *the* greatest inventions of the entire OS). And an application that I need as often as a terminal should have a shorter name than that, even if the Application Finder supports auto-completion (unfortunately, there are many applications starting with "xfce4-", so you have to type *at least* "xfce4-t"). But if the application finder is resistant against any aliases, I'll just have to stick with that...

Thanks,


Alan
It does not see your aliases, but there are always ways to fix it. You can make a symbolic link to the executable file. It must be in the system path, and should have a unique name, so that it won't 'steal' another command
```
echo $PATH
```
Example: Check that there is no command with the name xt
```
which xt
``` Maybe you should also check on the internet that there is no xt program in linux (that you might need later on).
Find the command to be linked and put the link in the same directory
```
which xfce4-terminal
```

```
sudo ln -s /usr/bin/xfce4-terminal /usr/bin/xt
```

Finally you can use ***xt*** instead of that long cumbersome string.

---

### Post by Alan_D. on 2013-01-20
@Sudodus: Thanks, that's awesome :D  Works perfectly now, thank you very much!

---

### Post by sudodus on 2013-01-20
You are welcome, I'm glad it works for you :-)

Please click on **Thread Tools** at the top of this page and mark this thread as SOLVED

---

