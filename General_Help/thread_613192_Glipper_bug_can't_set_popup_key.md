---
title: "Glipper bug: can't set popup key"
date: 2007-11-14
forum: General Help
---

### Post by Nameless_one on 2007-11-14
I am running Gutsy, and almost everyhting is perfect. A small but annoying exception is that I cannot set a key combination for glipper to popup the list of recently copied items. 

I go to the Preferences window, to the textbox for the key combination, and nothing I press has any effect on the box.

---

### Post by Nameless_one on 2007-12-04
Bump.

---

### Post by jroon on 2007-12-05
I have the same problem.

---

### Post by Nameless_one on 2007-12-05
There is no bug report on Launchpad, I checked. I don't have an account to report it myself. It only seems to happen on Gutsy, too. It worked fine in Edgy.

---

### Post by jroon on 2008-02-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/glipper/+bug/188306](https://bugs.launchpad.net/ubuntu/+source/glipper/+bug/188306) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This is still driving me nuts, so I filed a bug report:

---

### Post by Nameless_one on 2008-02-20
I found a workaround for this: you can write the key combination in text form. For examples, check **apps > metacity > global_keybindings** under the configuration editor (gconf-editor). 

For example, I wrote ```
<Control><Alt>c
```a dn it works.

---

