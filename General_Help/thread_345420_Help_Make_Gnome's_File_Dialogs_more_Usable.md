---
title: "Help Make Gnome's File Dialogs more Usable"
date: 2007-01-24
forum: General Help
---

### Post by charlie. on 2007-01-24
Am I the only person who has an issue with Gnome's File dialogs: those save, save as and open dialogs that are all over the place?

For a good example, open up OOo Writer and hit File -> Save As. The dialog that appears is positively awful.

Here's what I want:
[LIST=1]
[*]The dialog must be BIGGER. Much BIGGER. This does not have to be the distribution's default, but I'd like them to remember the size I made the last one. It would be even better if all the similar dialogs across the whole system (save and open in all apps) remembered my size preference.
[*]"Browse for other folders" MUST be expanded by default. In fact, the dialog would be leaner and meaner if that prompt was dropped entirely.
[*]I'd love the "Toggle between button and text based location bar" button from Nautilus to appear in these windows too.
[*]I want to be able to hide hidden files and folders by default. I also want to be able to show them easily. These dialogs should, once again, use Nautilus' preferences if possible.
[*]If I type in a relative or absolute path to a directory and hit enter, the dialog should refresh the file view to display files in that directory.
[/LIST]

I'm sorry to say that the best example is the stock standard Windows save and open dialogs. Honestly, these are part of Microsoft's "common controls" and are much more usable. Gnome provides many features that Windows does not but, sadly, its file dialogs are not one of them.

Please hear my plea!

---

### Post by yopnono on 2007-01-24
In OOo you can select which save/open dialog to use. Tools > options > general
For the rest go to [https://launchpad.net](https://launchpad.net) and file for request/bugs.

---

### Post by chavo on 2007-01-24
You could install devilspie to take of the the sizing issue.
Or just install KDE and get on with your computing life :)

---

### Post by charlie. on 2007-01-25
Ok, so I can change the dialogs that OOo uses. What about every other Gnome app that uses a similar (if not quite so bad) dialog? (gedit is an example)

They also show all hidden files with no way to hide them.
They also ignore the size you made the last one.

Believe it or not, the size thing is not as bad as the hidden files thing. These dialogs normally open to your home folder which has about 20 hidden folders in it, making finding the one you want quite a pain in the arse.

---

### Post by charlie. on 2007-01-25
Are these dialogs a Gnome thing or an Ubuntu "Human" theme thing?

---

### Post by mdurham on 2007-01-25
charlie, just right click in the files dialog and select 'show/hide hidden files' or something like that.
Cheers, Mike

---

### Post by kalikiana on 2007-01-25
> **charlie. said:**
> Are these dialogs a Gnome thing or an Ubuntu "Human" theme thing?

You are probably referring to Gtk+2 dialogs in general, which are neither Gnome nor Ubuntu specific. What you are talking about doesn't have anything to do with the theme.

You can indeed right-click on the file list and hide or show 'hidden' files. I believe this settings can change automatically if the default folder is hidden.

File a bug or contact the mailing list about size being saved.

---

