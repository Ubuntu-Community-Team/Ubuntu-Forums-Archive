---
title: "Cannot customize my desktop"
date: 2013-01-28
forum: General Help
---

### Post by _nikolaos on 2013-01-28
When I was working with 10.04, I had customized since 2010 my desktop with these elements:

1) gnome panel (and workspace switcher)
2) awn dock (and workspace shiny switcher)
3) compiz
4) Eight workspaces arranged 2 row x 4 columns.

As of my 2013 upgrade, and version 12.04 of Ubuntu, and supposedly up-to-date versions, it's always that one or more of these elements crashes.

Of course, I had similar difficulties in the past but managed to work out. This time everything goes bad. I don't know what my configuration should become at all. I tried to minimize the demands by picking up almost no effects, but this is not helpful anymore.

Is there anyone that has suffered as I do, but found a way?

Thanks.

---

### Post by raja.genupula on 2013-01-28
I am actually not getting what you want. you want have to your gnome back , then you can do installation of 

```
sudo apt-get install gnome-session-fallback
```

If you would like install gnome3 
```

sudo apt-get install gnome-shell
```

---

### Post by dino99 on 2013-01-28
better to start with a fresh new installation from scratch, due to huge changes since 10.04 (gnome2 -> gnome3, some apps no more maintained, ...) and some borked settings inside: .gconf, .local, .gnome2, .config  (all these hidden folders can be deleted, they are cleanly recreated with the default settings on the next reboot)

---

### Post by _nikolaos on 2013-01-30
I've managed to go on with a compromise, where I am not changing the configuration of the workspaces arrangement at the gnome panel and the awn applet. This arrangement is configured only at compiz settings.

That means, I am not going to right-click on either the two switcher icons, to change their workspace settings, although these will report that workspaces are 1x4-arranged, instead of 2x4 as they show and behave.

The awn switcher seems to respond very well. The panel switcher is a little out of shape, too small and half its normal size, but at least workable. The last appears to be one part of more problems that I have with gnome-panel. 

For example, I use the Left Win key to shift the keyboard layout (for Greek and English languages) and this blocks the customization of the gnome-panel elements. What is more, alacarte crashes whenever I try to modify menus with a separator.

I suppose I must dedicate some more time to fix all these things, but I cannot take time from my jobs. I will try the gnome 3 (in case I don't have it already, 'cause "about" boxes to see version are not easy to reach anymore) and upgrade in one of the next weekends and see how it goes. Creating another "fallback" session is second option.

Thank you for the answers.

---

