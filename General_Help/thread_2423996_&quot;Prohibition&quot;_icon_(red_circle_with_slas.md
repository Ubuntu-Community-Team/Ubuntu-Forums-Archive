---
title: "&quot;Prohibition&quot; icon (red circle with slash) on menu bar button? Xubuntu"
date: 2019-08-01
forum: General Help
---

### Post by Datoyminaytah on 2019-08-01
What does it mean when there's a "prohibition" or "no" symbol displayed as the icon on the menu button on the top panel?

System seems normal, except for the icon. No other obvious warnings or errors. Google is finding nothing for this. Hard to search for an icon with no definitive name, at least that I know of.

Xubuntu 19.04

---

### Post by #&amp;thj^% on 2019-08-01
This makes it harder to help you with no icon names.
have you checked with:
```
sudo apt update
```
Will tell if the updater has any errors with sources and such. (Which is my first Guess)

If you created a third panel, and subsequently updated the “/panels” array to remove the new panel again, then any of its properties will remain present in the Xfconf system—as the following command will demonstrate:

```
 xfconf-query --channel 'xfce4-panel' --property '/panels/panel-3' --list
```

[B]Unless you made any modifications to its setup, only the “/panels/panel-3/position” property will be listed.
[/B]You can list panel2 also.
If none of this helps then post a screenshot so we can have a better idea on how to help.

---

### Post by Datoyminaytah on 2019-08-01
I've finally found a few results for the "red circle with a red slash." It appears it means the icon that was supposed to be displayed cannot be found.

Why would anyone use a big scary "PROHIBITION" symbol for a missing resource instead of something like a question mark? It appeared on my main menu button immediately after recovering from a crash/hang, so I assumed it was related to that, and indicative of a system problem.

I'll check packages tonight.

---

### Post by cruzer001 on 2019-08-01
That red is certainly an eye catcher :)  

Also sounds like a good time for some cleanup.
```
sudo apt autoremove && sudo apt autoclean
```
```
man apt-get
```

---

### Post by #&amp;thj^% on 2019-08-01
> **Datoyminaytah said:**
> I've finally found a few results for the "red circle with a red slash." It appears it means the icon that was supposed to be displayed cannot be found.

Why would anyone use a big scary "PROHIBITION" symbol for a missing resource instead of something like a question mark? It appeared on my main menu button immediately after recovering from a crash/hang, so I assumed it was related to that, and indicative of a system problem.

I'll check packages tonight.

Is the screenshot below, like what you see?

---

### Post by dragonfly41 on 2019-08-01
I get that quite often after corrupted update ..

I usually run this to restore normality 

```
sudo rm -rf /var/lib/apt/lists/*

apt-get update
```

---

### Post by Datoyminaytah on 2019-08-01
1fallen, no, it was the whisker button on the far left.

Anyway, I figured it out.

It wasn't corrupt packages. Checked them all out with debsums.

Then I tried changing appearance settings. On the Icons tab, selected different ones. Aha! For some of them, the whisker button changed to a question mark icon! So definitely some problem finding resources, but not for a specific theme, and it just so happened the theme I was using used the red circle/slash for missing icons, and others use a question mark.

So I googled how to reset to defaults, the answer being to back up and delete everything under ~/.config/xfce4 then log out and back in. It worked!

There must be more desktop config settings somewhere, because it retained my background color, dpi, cursor size, and some other settings. Not sure what happened with my config files to cause that problem.

What made me think I was having a bigger system problem is, I had just been editing fstab and reloading it, and the screen went blank, and the power light started flashing. I restored the original fstab in a remote ssh session and restarted, then saw the red circle icon (for the first time) and assumed it meant there was a serious system problem.

Whew!

---

### Post by Datoyminaytah on 2019-08-01
Actually, not out of the woods yet. After a reboot, all my desktop settings are gone, and the red circle is back. So I'll keep working on it.

---

### Post by again? on 2019-08-01
Just try different icon themes.
What icon theme are you using?
What application is showing the missing icon?

---

### Post by #&amp;thj^% on 2019-08-01
> **Datoyminaytah said:**
> 1fallen, no, it was the whisker button on the far left.


Ah yes the missing menu button, for this i just use:
```
xfce4-panel -r
```
usually (99% of the time) it sets things back to normal.
Or open the task manager and kill the xfce4-panel process. Don't worry. System will restart the panel just after is has been killed.

---

