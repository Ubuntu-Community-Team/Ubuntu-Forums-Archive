---
title: "Help with Gnome Control Center"
date: 2019-06-22
forum: General Help
---

### Post by wjbmd48 on 2019-06-22
Hi:

I'm running Lubuntu 16.04, and trying to connect to my google drive account.

When I fire up gnome-control-center, I get a rather simple looking panel with only 3 icons: Language Support, Printers, and Software&Updates.

I don't see Online Accounts, nor do I see a way to add any items: there's only one settings-looking button that says "help" or "quit."

How do I access Online Accounts here? Maybe some other app?  In synaptic, I installed everything  I could see that contained the words "online-accounts."

Thanks!

Bill

---

### Post by kc1di on 2019-06-23
hello Bill,
My first advice would be to upgrade to 18.04.  But if you must stay with 16.04 here is a [web page]("https://www.omgubuntu.co.uk/2016/08/use-google-drive-ubuntu-16-04-linux-desktops") that may be of help.

---

### Post by wjbmd48 on 2019-06-23
Thanks!

I'm running Lubuntu 18.04 on another system, and there the problem is even worse. When I run 

gnome-control-center online-accounts

I ust get a blank page headed "Settings," with no way to add items that I can see.



Bill

---

### Post by wjbmd48 on 2019-06-23
Aha! After a lot of clicking around, here's the mother may I:

env XDG_CURRENT_DESKTOP=GNOME gnome-control-center

Again, thanks!

Bill

---

