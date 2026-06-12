---
title: "Installing LaTeX plugin for gEdit"
date: 2008-06-24
forum: General Help
---

### Post by hantabaru on 2008-06-24
I know it is probably straightforward, but could someone either explain or point me to a post on how to install the LaTeX plugin for gEdit?

I am having a stupid day today...:roll:

Cheers

---

### Post by ad_267 on 2008-06-24
Put it in ~/.gnome2/gedit/plugins then open up gedit and go to edit - preferences - plugins and tick it.

---

### Post by hantabaru on 2008-06-24
That's for that ad_267...

---

### Post by tasyhari on 2009-02-26
> **ad_267 said:**
> Put it in ~/.gnome2/gedit/plugins then open up gedit and go to edit - preferences - plugins and tick it.

Hi in my ubuntu, I don't have gedit foler under .gnome2. I try to make it myself and go along with that method. But it won't work. When I go to edit - preferences - plugins, there is nothing called latex. Could you advise me on this?

Thanks.

---

### Post by mrphd on 2009-02-26
Do you have a "/usr/share/gedit-2/plugins" directory?

---

### Post by Strohfeuer on 2009-03-02
After reinstalling Ubuntu I have the same problem. I have the plugin, and the folder where it belongs but it doesn't show up in the plugins when I restart Gedit. And I don't know if there was something else I had to take care off...:confused:
It doesn't matter if I put the whole folder or only the contents in the plugin directory, I will not work...
any ideas?

---

### Post by nortexoid on 2009-03-23
I had the same problem and then installed the plugin to user/lib/gedit-2/plugins. In that folder, drop the GeditLaTeXPlugin folder and the GeditLaTeXPlugin.gedit-plugin file. Then restart gedit and go to Preferences->Plugins and enable it there. It worked for me under Ubuntu 8.10.

The problem is that it doesn't seem to build the file (in pdflatex or anything), so that's probably not configured properly. (I do have latex installed, as I can build files from terminal.)

---

### Post by ad_267 on 2009-03-24
> **nortexoid said:**
> The problem is that it doesn't seem to build the file (in pdflatex or anything), so that's probably not configured properly. (I do have latex installed, as I can build files from terminal.)

You need to install [rubber]("http://www.pps.jussieu.fr/~beffara/soft/rubber/") (available in the repositories).

---

### Post by tasyhari on 2009-07-12
> **mrphd said:**
> Do you have a "/usr/share/gedit-2/plugins" directory?

Hi,

Finally after re-doing the whole thing again, I can have my plugin worked. Thanks a lot for the help 

:guitar:

---

