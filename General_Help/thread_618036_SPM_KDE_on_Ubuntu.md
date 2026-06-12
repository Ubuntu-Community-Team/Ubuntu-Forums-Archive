---
title: "SPM KDE on Ubuntu?"
date: 2007-11-20
forum: General Help
---

### Post by brad1138 on 2007-11-20
Can I get/add KDE to my Ubuntu through SPM? In the past when I tried Linux (Red Hat I think) I had the option to switch back and forth between KDE and Gnome. I noticed KDE in SPM and thought maybe I could install it and do the same.

Thanks,
Brad

---

### Post by MrFSL on 2007-11-20
Yes. You can install KDE as you would in other distros. Either graphically or with:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install kde
```

---

### Post by brad1138 on 2007-11-20
Thank you. 1 other thing, It's probably obvious, but before I install the upgrade I want to know for sure, How will I switch between them?

Thanks again,
Brad

---

### Post by brad1138 on 2007-11-20
I found the answer to my last question here [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde).  The page mentions a drawback to having Gnome and KDE loaded at the same time in that you have a lot of apps for both listed in the apps menu. What happens when you run a KDE app in Gnome or Gnome app in KDE?  Will it hurt anything or just not run?

Brad

---

### Post by archivator on 2007-11-20
It will work just fine. Only its theme might be a little off compared to the rest of the applications. 

As for the total menu clutter, there are quite a few HOWTOs on these very forums that provide means of making sure the GNOME items are only in the GNOME menu and the KDE items are only in the KMenu.

---

