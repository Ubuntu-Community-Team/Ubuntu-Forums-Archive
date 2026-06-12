---
title: "Command to Lock Screen Throws Error"
date: 2016-09-20
forum: General Help
---

### Post by texpat on 2016-09-20
so yes, the following command

```
~$ xdg-screensaver lock
```

gives me 

```
ERROR: Unknown command 'lock'
```

even though it is a legal command according to the command's manpages and other commands such as '[FONT=Courier New]**xdg-screensaver reset**[/FONT]' or '[FONT=Courier New]**xdg-screensaver status**[/FONT]' work normally.

This is on Xubuntu 14.04 with bash v 4.3.11(1)-release and xdg-screensaver v 1.0.2

I've looked around on the Internet but what I've found is either 5 years old or more and is too technical for my level of expertise, so I'd really appreciate help with this.
As always, thanks for reading.
Tx

---

### Post by CantankRus on 2016-09-21
I don't use Xubuntu but looking at the [**_[COLOR="#B22222"]14.04 manifest[/COLOR]_**]("http://cdimage.ubuntu.com/xubuntu/releases/14.04/release/xubuntu-14.04-desktop-amd64.manifest") it includes light-locker, a gnome-screensaver fork.

Try ...
```
light-locker-command --lock
```

---

### Post by texpat on 2016-09-21
Thanks CantankRus, that appears to work.

Good enough for my purposes anyway ;-) I don't *need* to know why the [FONT=Courier New]**xdg-screensaver**[/FONT] command doesn't work, although it does bug me a bit...

---

### Post by CantankRus on 2016-09-21
I only have a Xubuntu 16.04 iso which I installed and tested.
```
xdg-screensaver lock
```
works so may have been fixed or perhaps other installed desktops and associated screenlocks are interfering.

---

### Post by texpat on 2016-09-23
Now it ([FONT=Courier New]**xdg-screensaver lock**[/FONT]) seems to work on my 14.04 box, too. No idea what the problem was. Possibly it got solved by some update or other?
Marked thread as solved.
Thanks for your help CantankRus

---

