---
title: "No desktop in Lubuntu"
date: 2020-06-04
forum: General Help
---

### Post by Walter_M_Green_III on 2020-06-04
I updated Lubuntu, now when I boot I get this, not my desktop...

[ATTACH=CONFIG]286093[/ATTACH]Lubuntu

---

### Post by ajgreeny on 2020-06-04
You appear to have an almost empty gnome 3 desktop showing; it looks nothing like either Lubuntu 18.04 or Lubuntu 20.04.

However, you have given us no information that will allow us to help you.
What Lubuntu version did you start with and what did you believe you were updating to?

---

### Post by guiverc on 2020-06-04
The image reminded me of Lubuntu daily images that had this result for roughly a week during a prior development cycle... but we don't have any details of what you're running or what you meant by 'upgrade' (prior response).

The obvious work-around would be to logout of the GNOME shell session, and login using Lubuntu. How this appears will depend on what release you are running (what DM you are using; `lightdm` was default for 18.04, `sddm` for modern releases, but if you've added GNOME to your system you may be using `gdm3` or something different).  

Changing session to Lubuntu at the login screen will at least switch you to using whatever Lubuntu desktop you have installed (ie. LXQt if modern Lubuntu, LXDE if legacy Lubuntu).

[https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1815837](https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1815837)  should anyone be interested in my *pointless* diversion

---

### Post by Walter_M_Green_III on 2020-06-05
Lubuntu 18.10 I think, however I do not know how to find out since this interface is so unknown to me.

---

### Post by Walter_M_Green_III on 2020-06-05
Also NO login screen. goes directly to what I have shown above.

---

### Post by Walter_M_Green_III on 2020-06-05
Also only options to reboot or shutdown, see no logout, sleep, or suspend options.

---

### Post by GhX6GZMB on 2020-06-05
What exactly does "I updated Lubuntu" mean? What did you do?

A boot from a live disk might be helpful...

---

### Post by guiverc on 2020-06-05
If you are using 18.10, Ubuntu/Lubuntu 18.10 is EOL (*end-of-life*), so refer [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)  [http://fridge.ubuntu.com/2019/07/19/ubuntu-18-10-cosmic-cuttlefish-end-of-life-reached-on-july-18-2019/](http://fridge.ubuntu.com/2019/07/19/ubuntu-18-10-cosmic-cuttlefish-end-of-life-reached-on-july-18-2019/)

For help using your GNOME system, maybe refer to [https://help.ubuntu.com/stable/ubuntu-help/](https://help.ubuntu.com/stable/ubuntu-help/)  (or one of it's pages, specifically [https://help.ubuntu.com/stable/ubuntu-help/shell-introduction.html.en](https://help.ubuntu.com/stable/ubuntu-help/shell-introduction.html.en) maybe)

I don't understand your issue, whilst i'm not a fan of GNOME, I don't find it difficult to navigate. I do recall when it appeared on my Lubuntu dailies, it gave me a shock & it was awhile before I was able to fully make use it.. so can somewhat appreciate you're stunned & feeling lost.

The upgrade though is important, if using a modern Lubuntu (LXQt) and upgraded from a legacy Lubuntu (using LXDE), there are numerous issues that can be encountered, which is why it was not supported (there is documentation written to handle some of it, but it may not fix everything and is rather technical; why it was decided to not support that upgrade path and re-install was recommended).

Normal keyboard commands like Ctrl+Alt+T to open a terminal, and `lsb_release -a` should work normally allowing you to see release details, but I still believe logging out (menu is top left on gnome, options such as logging out top right in panel) would allow you to switch desktops and into whichever Lubuntu desktop (LXDE or LXQt) you were using (*at worst I'd use the terminal to kill the GUI & return you to login/greeter, but that wouldn't be easy for a non-technical user, and I cannot provide commands for it as I don't know your release/desktop*).

---

