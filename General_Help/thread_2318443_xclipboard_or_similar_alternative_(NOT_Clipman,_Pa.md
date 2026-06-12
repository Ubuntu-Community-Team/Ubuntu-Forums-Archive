---
title: "xclipboard or similar alternative (NOT Clipman, Parcellite, Diodon)"
date: 2016-03-26
forum: General Help
---

### Post by gojira2016 on 2016-03-26
I am using Xubuntu 14.04 which runs XFCE. I need a clipboard manager which constantly shows what is in the clipboard.

I have been trying a number of clipboard managers: Clipman 1.2.5, Parcellite 1.1.7, Diodon. They are all useless to me because they do not show what is in the clipboard, I have to click on them to see what is in the clipboard.

I simply want to see what is in the clipboard right now, and not have to click on this tiny icon in the bar just to see what is there.

(I also tried Klipper but that one doesn't even start). 

Ideally, I want to use good old xclipboard.

However, xclipboard does not run on my system, I just get this error: "Error: another clipboard is already running".

[LIST]
[*]Is it possible to use xclipboard in combination with Xubuntu 14.04.4 and XFCE? If yes, how? 
[*]If it is not possible, can you recommend any clipboard manager which simply shows what is in the clipboard *without having to click* on the clipboard manager just to see what is in the clipboard? 
[/LIST]

---

### Post by vasa1 on 2016-03-26
> **gojira2016 said:**
> ...
However, xclipboard does not run on my system, I just get this error: "Error: another clipboard is already running".
...
What does *pgrep -l clipboard* or *pgrep -l clip* show? Is it *xfce4-clipman*?

Then *pkill* that (if you're sure it relates to clipboard management), ensure that whatever that was is removed from your autostart, and add *xclipboard* to your autostart instead or run *xclipboard* whenever you choose.

---

### Post by gojira2016 on 2016-03-26
> **vasa1 said:**
> What does *pgrep -l clipboard* show?

Nothing!

```
uname@uname-VirtualBox:~$ pgrep -l clipboard
uname@uname-VirtualBox:~$
```

---

### Post by vasa1 on 2016-03-26
See the edit ...

And I vaguely remember that there could be some issues with VMs and clipboards. Could be wrong though.

---

### Post by gojira2016 on 2016-03-26
Thanks for the help, but apparently there is nothing I can pkill, that's kinda the root fo the problem. I thought maybe XFCE takes care of the clipboard in some way, but I was asking on the XFCE forum already without success, there were calyming it's an [X]ubuntu issue not a XFCE issue...

---

### Post by vasa1 on 2016-03-26
> **gojira2016 said:**
> ...but I was asking on the XFCE forum ...
Link?

And what's the output of *ps -o pid,ppid,stime,time,command -u $USER*? Maybe someone can spot something there?

---

