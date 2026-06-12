---
title: "Ubuntu equivalent to &quot;System Restore&quot;"
date: 2007-01-30
forum: General Help
---

### Post by anditwasgood on 2007-01-30
After installing some updates it appears Firefox no longer works...is there a "system restore" or "roll-back" in Ubuntu? Or a way to fix this issue?

---

### Post by crispy_420 on 2007-01-30
Did you try a reinstall of firefox?

There is a way to install an older version of firefox from command line. You have to know the version number though. I've done it for xorg (from that big error a few monthes back) so I assume it is possible for firefox. Sorry I can't help you with the exact command.

---

### Post by aysiu on 2007-01-30
Can you be more specific than "no longer works"?

Open up a [terminal](http://www.psychocats.net/ubuntu/terminal), type ```
firefox
``` and then highlight the output, right-click it, copy it, and then paste it into a post here.

---

### Post by FluffyElmo on 2007-01-31
In Synaptic, there are a couple of options that can help you roll back to a previous state but it's not automated. You can run Synaptic from *System->Administration->Synaptic Package Manager*.

First, select ***File->History*** form the menu to see a log of all updates for the past month. You can then search for packages that you think might be causing trouble. Then, after selecting an installed package you can choose ***Package->Force Version*** from the menu and make it roll back to a previous version if available.

---

