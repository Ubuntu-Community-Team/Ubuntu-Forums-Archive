---
title: "fluxbox help"
date: 2005-07-25
forum: General Help
---

### Post by blu.gecko on 2005-07-25
I have a slight problem, every time I try to go into symantec package manager, it tells me that my user password is incorrect. But its not, I like flux, alot, its light and customizable, The more I earn about linux the better it gets but this is a major issue for me, needs fixed a.s.a.p    ](*,)

---

### Post by Xian on 2005-07-25
This doesn't really sound like a fluxbox issue....
Have you been able to open Synaptic in the past?

From a terminal issue this command and post the output.

```
$ sudo synaptic
```

---

### Post by blu.gecko on 2005-07-25
well I have from gnome......

and I can from gnome, but I dont want to use gnome anymore.

---

### Post by Xian on 2005-07-25
Okay. What happend with the terminal command...?

---

### Post by blu.gecko on 2005-07-25
well it worked but why would it not work through the graphical interface? :-#

---

### Post by blu.gecko on 2005-07-25
Is it possible to uninstall gnome? or would this cause issues?

---

### Post by Xian on 2005-07-25
[QUOTE=blu.gecko]well it worked but why would it not work through the graphical interface? :-#[/QUOTE]
You probably have an menu entry that needs to be changed.
Open your /home/username/.fluxbox/menu file.

Place the entry below in any menu category you prefer.
Then try and run it from your right-click menu.

```
[exec] (Synaptic) {gksudo /usr/sbin/synaptic}
```

---

### Post by Jet2k5 on 2005-07-25
[QUOTE=blu.gecko]Is it possible to uninstall gnome? or would this cause issues?[/QUOTE]


I'm not thinking it might be that good of an idea.  Since gnome is the main desktop on Ubuntu, taking out gnome will take a lot and I mean a lot of dependencies with it.  I remember I tried getting rid of Firefox ( Use Konq ) and removing it would take the whole desktop with it.  So I think I might be possible and you might loose some programs.  Or it's possible with nothing changing besides gnome just going away.

But I guess you can try  ;-) , tell us how it goes.

---

### Post by Xian on 2005-07-25
[QUOTE=blu.gecko]Is it possible to uninstall gnome? or would this cause issues?[/QUOTE]
It's possible but it won't impact your issue.
More likely to cause just more problems....

Try the solution I posted and advise of results.

---

### Post by blu.gecko on 2005-07-31
Well I decided to kill out fluxbox, I just decided to customize my gnome pannel. altho it is not as light as flux, I was having to many issue using flux.

---

### Post by Xian on 2005-07-31
Fluxbox is relatively easy to run and configure, but it does take a little more prodding since many of the steps required to set it up to your liking requires a bit of scrutiny and manual editing.

I asked about the terminal output because if you can open synaptic without error using the proper command, then you can do the same from a menu entry. There is no doubt about that, so the only concern really would be to verify that the menu execution line is listed accurately.

---

### Post by bitra on 2005-08-17
[QUOTE=blu.gecko]Well I decided to kill out fluxbox, I just decided to customize my gnome pannel. altho it is not as light as flux, I was having to many issue using flux.[/QUOTE]

How is exactly you done that, "killing" your flux? I'm trying to install enlightenment on my gnome, but it doesn't appear on the session menu. I'm just thinking, is it possible that it was because I have to uninstall the flux first?

How many exactly the max number of window manager I can install?

---

