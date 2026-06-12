---
title: "Run-As-Root desktop shortcut"
date: 2021-03-02
forum: General Help
---

### Post by hornetster on 2021-03-02
It used to be possible to have a shortcut on the desktop, that you could click and drag a file/directory to from a file manager, a pop-up would then allow you to sudo, and the result would be an editor/file manager, logged in with root privileges (sooooo handy.)
Believe it used gksu %u , or similar to do the trick.

Realise that gksu is not generally available these days, but is this still possible using a different utility?
Thanks.

---

### Post by Holger_Gehrke on 2021-03-02
A drag-and-drop capable shortcut for editing could use something like
```

env EDITOR=/usr/bin/mousepad SUDO_ASKPASS=/usr/bin/X11/ssh-askpass sudo --askpass -e %F

```

This uses 'sudo -e' which - just like sudoedit - copies a file, runs an Editor (chosen through the environment variable EDITOR) on the copy then copies the edited file back. This has the advantage of **not** running an editor as root. It uses ssh-askpass from the package from the package of the same name to ask for the password in a graphical form.

Holger

---

### Post by TheFu on 2021-03-02
I don't think Gnome3, the default DE on Ubuntu, allows desktop icons.  There may be an addon for Gnome3 to enable this or you can use some other DE which does support desktop icons.

But really, you can just use **sudoedit**.

---

### Post by ActionParsnip on 2021-03-02
Could use nautilus-scripts to do same (I assume Gnome here). Sounds pretty useful for GUI kids :)

---

### Post by dragonfly41 on 2021-03-02
[Nautilus Python scripts here]("https://www.giuspen.com/nautilus-pyextensions/")

e.g. open-as-root.py

---

### Post by ActionParsnip on 2021-03-02
> **dragonfly41 said:**
> [Nautilus Python scripts here]("https://www.giuspen.com/nautilus-pyextensions/")

e.g. open-as-root.py

Pretty much what I said, just more exact :)

---

### Post by HermanAB on 2021-03-02
Note that for small utilities, there is a method called suid root.  A little googling for "linux suid root" will find you more information.

On an engineering machine, it is useful to set the network utilities such as ifconfig, ip, route and a few others to suid root.  What will then happen is that the utility will run with root permissions when launched from a common user account, without the need to invoke sudo or similar annoyances.  

For a computer used by an unsophisticated user in an office environment, this is not a good idea, so these utilities are not set that way by default.

---

### Post by hornetster on 2021-03-03
So... am I getting thicker and thicker... Sorry, coming from Opensuse (and may be going back :( )
Does drag'n'drop to open a file with an app, not work at all by default in Gnome? ie can't drag and drop a file on an executable, to open that file?

---

### Post by dragonfly41 on 2021-03-03
[COLOR=#000000][INDENT]> Does drag'n'drop to open a file with an app, not work at all by default in Gnome? ie can't drag and drop a file on an executable, to open that file?

Personally I don't follow that drage&drop workflow. Instead I use a tool (in my case Krusader dual-pane file manager), right click and select from list .. Open With.  Then a list of relevant apps show.  You can adapt this workflow to suit.

Also in Krusader I can open file with root permissions when needed, but largely I use in local user mode until I really needed root.[/INDENT]
[/COLOR]

---

### Post by hornetster on 2021-03-03
Think I'm going to head back to Opensuse for a while.
Although I quite like the way ubuntu/gnome works, and have been persevering with it for a month or so, now, I don't like the current 'disabled' desktop.
Will try again later....

---

### Post by QIII on 2021-03-03
... or, try a different flavor with a different DE.

But I hear ya.  Use what works and suits your flow.

---

### Post by hornetster on 2021-03-05
Yep, giving Kubuntu a try...

---

### Post by hornetster on 2021-03-07
OK, probably wrong way to do this (please tell me all the problems), but after moving to Kubuntu (although would think that this would also work in vanilla Ubuntu?? - xdg-open), have created a .desktop file with:

> Exec=pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY kde-open5 %u

and this works....
Can drop any type of file that is "root" permissions, and it will open the relevant program, allowing file to be edited, or if unknown, will ask which program to open with, after asking for login...
Thanks.

---

### Post by CatKiller on 2021-03-07
Just so you're aware, you don't need to run Kate as root to write to access-controlled files. Open them normally and you'll be prompted for authorisation when you save.

---

### Post by hornetster on 2021-03-07
Thanks for the tip!

---

