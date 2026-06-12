---
title: "Is the filetype-to-app mapping situation in ubuntu the mess it seems to be?"
date: 2008-06-09
forum: General Help
---

### Post by crispinb on 2008-06-09
I'd be the first to admit lack of detailed knowledge, so happily welcome corrections or enlightenment, but isn't the situation regarding default applications for different filetypes on ubuntu/gnome a bit of a mess?

There's the 'preferred applications' app, /etc/mime.types, the debian update-alternatives, and the nautilus 'open with' pref. They all seem to have their effects in different situations, and overlap in (to me) unpredictable ways. 

I have no idea whether evince or acroread will open the next pdf I click on, and less idea about whether that will be the same or a different app from the one gnome-open will use for the same file if I prefer to launch from the command line. Add to the mix opening things from firefox (eg. downloaded files), with its own mechanisms but some relationships to system-defined mime types, and .... well, from my point of view there might as well just be an 'Open this file with randomly-chosen application' button. Except the label needs a snappier title.

Shouldn't ubuntu use some kind of unified scheme for choosing what application to open files of a particular type with, one that works across desktops, GUI, cli, and launches from other applications? Or have I just got all this entirely wrong?

---

### Post by crispinb on 2008-06-09
A bit more research, and the situation gets even more confusing. See [https://bugs.launchpad.net/ubuntu/+source/xdg-utils/+bug/209714](https://bugs.launchpad.net/ubuntu/+source/xdg-utils/+bug/209714)

gnome-open not only doesn't work correctly, it's not maintained any more.

Nuttier still: gnome-open seems to have been replaced with gvfs-open, which isn't even installed by default in hardy.

---

### Post by crispinb on 2008-06-14
Any thoughts?

---

