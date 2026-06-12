---
title: "how to activate compiz scale in feisty"
date: 2007-03-28
forum: General Help
---

### Post by ico on 2007-03-28
Hi all,

Anyone knows how to enable compiz scale option in Feisty? Corner activation has been disabled according to the launchpad and I was unable to locate anything in the gconf-editor that would allow me to customize the key (all options have <schema> value next to them)?

Any help is most appreciated!

Best wishes,

Ico

---

### Post by iamtherealwoody on 2007-03-28
I think the default is cntrl-alt-up.  I got the synaptic package gnome-compiz-manager and with it you can configure the mouse to scale and all that jazz.

matt

---

### Post by Camden on 2007-04-25
Install gnome-compiz-manager and set it up under the desktop tab.

---

### Post by SilverWave on 2007-04-29
As I wanted Scale aka "expose" (from Mac), to kick in when I move the mouse to top right I needed to change this:
gconf-editor
/apps/compiz/general/allscreen/options/close_window_edgebutton to 0 from 1

---

