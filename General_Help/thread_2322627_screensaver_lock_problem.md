---
title: "screensaver/ lock problem"
date: 2016-04-29
forum: General Help
---

### Post by Evil Wayz on 2016-04-29
I am running 14.04.4 LTS, with the 4.3 kernel, and cinnamon 2.8 able to set my screensaver up running mint, but on  ubuntu I'm running into the following problem.  When my screen cuts off, when i mouse the mouse or hit a key, I get a window box to sign in. I do so, and then it goes to the cinnamon screensaver, and demands another password.  THat would be fine, but when I get back to my desktop, I don't have my panel anymore.  WHich means I have to either use the windows key to call things up and a;t-tab to switch between active program,s or running everything from terminal.

I read on askubuntu that removing gnome-screensaver sometimes helps, but I tried that and then i couldn't get back to my desktop at all, there was nowhere to sign in.   I have noisy roomates and teenagers in teh house so I'd like to be sable to lock my computer down without having to shut it off. 

Oh and i was running gnome-flashback prior to this, if you were wondering where gnome-screensaver came from.

---

### Post by gnusci on 2016-05-01
Maybe you need to reinstall the ubuntu desktop?

sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity

---

### Post by Evil Wayz on 2016-05-02
I never uninstalled it, and I have no plans to use it ever if I am not forced to.

---

### Post by Bucky Ball on 2016-05-02
> **Evil Wayz said:**
> ... I have no plans to use it ever if I am not forced to.

Am I right in my presumption you had Mint installed then installed ubuntu-desktop? That is a strange way to get the screensaver working in Mint. Mint may be based on Ubuntu, but it ain't Ubuntu and it is also not supported here.

If you have Ubuntu installed on top of Mint, yes, expect all sorts of unexpected. Take this as an example. You would also have duplicated apps (different name perhaps but do the same thing) in bloated applications menus.

---

### Post by Evil Wayz on 2016-05-02
> **Bucky Ball said:**
> Am I right in my presumption you had Mint installed then installed ubuntu-desktop? That is a strange way to get the screensaver working in Mint. Mint may be based on Ubuntu, but it ain't Ubuntu and it is also not supported here.

If you have Ubuntu installed on top of Mint, yes, expect all sorts of unexpected. Take this as an example. You would also have duplicated apps (different name perhaps but do the same thing) in bloated applications menus.


No, as I said in my original post, I was running Ubuntu 14.04 with Cinnamon 2.8.  I have a laptop with just Mint 17 on it also running 2.8 cinnamon and it doesn't have this problem.

---

### Post by Bucky Ball on 2016-05-02
Ah. Thanks. Clear now. Well, that seems pretty straightforward. You have two screensavers installed. Remove the one you don't want, reboot, close lid, open. Any different?

When you uninstall the screensaver, open a terminal and 

> sudo apt autoremove

... prior to the reboot and other stuff.

---

