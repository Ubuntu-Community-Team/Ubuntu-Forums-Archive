---
title: "how to set XLIB_SKIP_ARGB_VISUALS=1 for specific applications"
date: 2015-07-14
forum: General Help
---

### Post by WDYSUN on 2015-07-14
Dear all

emacs and some other software crashes on startup, it seems this is an old bug. The workaround is to launch emacs on the terminal doing

```
XLIB_SKIP_ARGB_VISUALS=1    emacs
```

The previous works, but I would like to make it automatic,  in the sense that whenever emacs is launched the "XLIB_SKIP_ARGB_VISUALS=1" is set automatically.

I tried to put the following in my .profile

```
XLIB_SKIP_ARGB_VISUALS=1
export XLIB_SKIP_ARGB_VISUALS
```

but doing this screws up the graphic interface completely.

There is any simple strategy to accomplish this?

Regards

Pierre

---

### Post by dino99 on 2015-07-14
i've never used emacs, but i suppose it might have some config file where this could be added

[https://help.ubuntu.com/community/EmacsHowto](https://help.ubuntu.com/community/EmacsHowto)

---

### Post by steeldriver on 2015-07-14
Would a simple alias do the job?

```

alias emacs='XLIB_SKIP_ARGB_VISUALS=1 emacs'

```

If it works, add it to your ~/.bashrc to make it persistent

For more complex environments you could consider a 'wrapper' script instead

---

### Post by WDYSUN on 2015-07-15
Hello

thanks for this. It works although it only works when emacs is called from terminal, this setting does not work if I click on the emacs icon form the menu, or when I do "open with" from the context menu.

It is very strange that a so popular software such as emacs has these  problems.

-P


> **steeldriver said:**
> Would a simple alias do the job?

```

alias emacs='XLIB_SKIP_ARGB_VISUALS=1 emacs'

```

If it works, add it to your ~/.bashrc to make it persistent

For more complex environments you could consider a 'wrapper' script instead

---

### Post by steeldriver on 2015-07-15
Apologies - I sometimes forget that people start things graphically ;) You could try this:

1. make a local copy of the emacs .desktop launcher[INDENT]```
cp /usr/share/applications/emacs24.desktop ~/.local/share/applications/
```
[/INDENT]
2. edit the copy, changing[INDENT]```
Exec=/usr/bin/emacs24 %F
```
[/INDENT]
to[INDENT]```
Exec=/usr/bin/env XLIB_SKIP_ARGB_VISUALS=1 /usr/bin/emacs24 %F
```
[/INDENT]

I can't really test it because I don't know what XLIB_SKIP_ARGB_VISUALS=1 does, however echoing the value of the variable from a shell inside emacs appears to confirm that it's been passed correctly. 

You can edit the /usr/share/applications/emacs24.desktop directly if you want to apply the variable to emacs system-wide, however your changes may get overwritten if emacs gets an update - instead, I'd suggest using /usr/local e.g.

```

sudo mkdir -p /usr/local/share/applications/
sudo cp /usr/share/applications/emacs24.desktop /usr/local/share/applications/

```

and make your changes there e.g. with nano

```

sudo nano /usr/local/share/applications/emacs24.desktop 

```

---

### Post by WDYSUN on 2015-07-15
Thanks a lot, this was very useful to understand how applications are called from the graphic system.

As soon as I am on my main machine I will try, and I will let you know!

Best Wishes
Pierre 





> **steeldriver said:**
> Apologies - I sometimes forget that people start things graphically ;) You could try this:

1. make a local copy of the emacs .desktop launcher[INDENT]```
cp /usr/share/applications/emacs24.desktop ~/.local/share/applications/
```
[/INDENT]
2. edit the copy, changing[INDENT]```
Exec=/usr/bin/emacs24 %F
```
[/INDENT]
to[INDENT]```
Exec=/usr/bin/env XLIB_SKIP_ARGB_VISUALS=1 /usr/bin/emacs24 %F
```
[/INDENT]

I can't really test it because I don't know what XLIB_SKIP_ARGB_VISUALS=1 does, however echoing the value of the variable from a shell inside emacs appears to confirm that it's been passed correctly. 

You can edit the /usr/share/applications/emacs24.desktop directly if you want to apply the variable to emacs system-wide, however your changes may get overwritten if emacs gets an update - instead, I'd suggest using /usr/local e.g.

```

sudo mkdir -p /usr/local/share/applications/
sudo cp /usr/share/applications/emacs24.desktop /usr/local/share/applications/

```

and make your changes there e.g. with nano

```

sudo nano /usr/local/share/applications/emacs24.desktop 

```

---

