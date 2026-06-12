---
title: "Mouse themes not getting applied completely"
date: 2007-08-16
forum: General Help
---

### Post by vapore0n on 2007-08-16
Hi

For all themes installed in Ubuntu, the default ones and the ones I have installed, they don't seem to get applied properly.

For example, Ubuntu seems to have a default "wait clock" icon, which is shown always, even if the specified theme provides its own. 

For example. Going to the Nautilus explorer shows the selected "wait clock" icon. Browsing the folders also gives the correct icon. Browsing any folder that requires sudo password shows the wrong one. 

More examples. 
Moving the cursor to the maximize/minimize/close buttons shows the wrong icon.

In firefox the "wait clock" icon shown is always the wrong one. Try opening tabs to see the problem.
Loading up Gimp shows the wrong icon too.

So there is some bad consistency in the mouse cursor icons.
Is this a bug? Is there a fix?

---

### Post by firefeather on 2007-08-27
I'm having the same or similar problem on Ubuntu 7.10 amd64. Really annoying! But I would assume it still works for some people on Ubuntu?

---

### Post by firefeather on 2007-08-27
I was persistent, and found this by sheer chance ([here]("http://jimmac.musichall.cz/themes.php?skin=7")) on Jakub 'jimmac' Steiner's website ("[Stopped Clock]("http://jimmac.musichall.cz/index.php")"):

> Looks like cursor theming isn't all that well tested. On some distributions it's required you log out and log back it *[sic]* for the theme to propagate itself everywhere.

I tried this with a icon theme that I knew had a working "wait" icon ([Fedora Core 6 Cursors]("http://www.gnome-look.org/content/show.php/Fedora+Core+6+Cursors?content=50533")) and it worked. So all it takes is a log-out and a log-in! :KS

(Never thought I'd post a solution to a problem here!)

EDIT: I realized that my solution may be incomplete. Applications run as sudo or gksudo (whether Nautilus or Synaptic Package Manager) have their own settings for controls and icons themes. The cursor theme might do the same thing. I'm able to confirm that the wait icon still reverts when I opened (and had my mouse over) Synaptic. I know there's a way to re-theme the administrator applications on Dapper and Edgy but I haven't heard of it working on (nor gotten it to work on) Feisty.

At any rate, I hope this fix works for you!

---

### Post by vapore0n on 2007-08-28
yes, I wanted to reply to the thread but forgot.

All it took was a reboot/re log to apply the mouse theme. Now Im happy. 

Though for gutsy it took a bit more, as the gcursor would not intsall the mouse theme

---

