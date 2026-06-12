---
title: "no hidden folders in home directory?"
date: 2013-04-11
forum: General Help
---

### Post by donkarziavelli on 2013-04-11
I feel like I'm making a stupid mistake. I'm in the home directory. I try to make dolphin show me the hidden files by checking the box "show hidden files". nothing happens. I try pcman. nothing happens. I try to get there with the terminal. nothing happens. it just sys the folder isn't there.

what do I do wrong? help ! :(

EDIT: I'm using lubuntu, not edubuntu.

---

### Post by nothingspecial on 2013-04-11
What does it say if you type ```
ls -a $HOME

``` in your terminal ?

---

### Post by donkarziavelli on 2013-04-11
oh! snap. I just figured out that being in the home directory means going in the user directory of home. that's really confusing but i found what i was looking for :)

thank you for your advice. after I tried "[COLOR=#000000][FONT=Ubuntu Mono]ls -a $HOME" I saw the folders of my user directory and looked there. [/FONT][/COLOR]

---

