---
title: "Problems with xfce after apt-get ubuntu-desktop"
date: 2007-01-22
forum: General Help
---

### Post by sabelsen on 2007-01-22
I have Xubuntu 6.10 installed on my machine, and yesterday I installed gnome (apt-get install ubuntu-desktop) to test something out. This, however, caused my xfce to run gdm as default instead of xfdesktop. Some first-hand problems I encounter are no right-click menu and various gnome icons on my desktop. This is typical problems when you for example launch nautilus without the --no-desktop option, where xfdesktop is replaced by gdm. 

I've searched for help on google and in these forums, but haven't found anything else than:
"try to launch xfdesktop while in xfce to replace gdm.". This did not make a difference.

Do you know or have any ideas on how to make xfce run with (or switch back to) its desired window manager? By the way, if i run sudo /etc/init.d/gdm stop while in xfce, xfce quits. Is that normal behavior?

Also, I have a second question. If some of you know the answer it'll be much appreciated.
When I run xfce 4.4's graphical installer, the configure-step of xfce4-mixer gives me an error. It can't find alsa >= 0.9. A simple apt-get install alsa reveals that it is already installed. I went into synaptic and installed alsa-source as well, but that didn't help. Do you know what I have to do in order to get xfce4-mixer to pass the configure-step?

Thanks.

---

### Post by sabelsen on 2007-01-22
Oh, I figured it out, it had nothing to do with gdm at all. 

However, my right-click menu is gone, and it doesn't help to reload xfdesktop. This happened after the xfce 4.4 install. Any ideas on how to bring it back?

---

