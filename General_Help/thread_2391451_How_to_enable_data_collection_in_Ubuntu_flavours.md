---
title: "How to enable data collection in Ubuntu flavours"
date: 2018-05-09
forum: General Help
---

### Post by junaidahmed2 on 2018-05-09
After the release of 18.04, when I've clean installed Ubuntu 18.04,  it informed me about some data it wants to collect about my system which  I was ok with. 

  However, Gnome had some performance problem on my old hardware and  I've installed Xubuntu 18.04 then. During installation, it didn't ask  me about any data collection. Does that mean they're doing it without my  permission(which is probably unlikely)? Or Xubuntu didn't include the data-collection part? How to  active/inactive data-collection on Ubuntu official flavours?

---

### Post by PaulW2U on 2018-05-09
> **junaidahmed2 said:**
> During installation, it didn't asked  me about any data collection. Does that mean they're doing it without my  permission(which is probably unlikely)? Or Xubuntu didn't include the data-collection part? How to  active/inactive data-collection on Ubuntu official flavours?
In Ubuntu there is a command line tool called **ubuntu-report**. When run it displays the information that has been collected and asks if you agree to the information being sent or not. I've just checked my Xubuntu installation and ubuntu-report is **not** installed by default so I installed it and when run the command behaves exactly as it does in Ubuntu.

I don't know if Canonical are collecting information for flavour installations or just Ubuntu but it is possible to send it to them by installing **ubuntu-report**.

---

### Post by junaidahmed2 on 2018-05-10
Thanks!

---

