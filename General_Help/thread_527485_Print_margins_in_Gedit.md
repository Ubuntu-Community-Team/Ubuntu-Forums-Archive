---
title: "Print margins in Gedit"
date: 2007-08-16
forum: General Help
---

### Post by Jim Danner on 2007-08-16
When printing from Gedit, I can choose the paper size (A4 in my case), but can I also set the margins? By default the top and bottom margins are much too large for my taste (3.1 cm whereas the left margin is just 2.1 cm).

---

### Post by Jim Danner on 2007-08-20
One would think there should be some sort of template, which could be edited?

---

### Post by Bartkowiak on 2008-03-28
> **Jim Danner said:**
> When printing from Gedit, I can choose the paper size (A4 in my case), but can I also set the margins? By default the top and bottom margins are much too large for my taste (3.1 cm whereas the left margin is just 2.1 cm).

I've got the same problem. Because there's no way to config print margins via user interface it is necessary to edit the printing config file on
     ```
~/.gnome2/gedit-print-config
```

There you can edit the key with id "Margin". After defining the desired print margins it is necessary to close all gedit instances an restart it. If it takes no effect already, please log off and log in again. This workaround is user specific, so you can define separate printing properties for each user.

---

### Post by Luke.Hoersten on 2008-06-02
`File -> Page Setup -> Paper Size -> Manage Custom Sizes...` and then make a new page setup there. It took me a while to find it as well.

---

