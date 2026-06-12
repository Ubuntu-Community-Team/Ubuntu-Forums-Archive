---
title: "Firefox does not show it's window"
date: 2007-04-01
forum: General Help
---

### Post by mkljun on 2007-04-01
Hi!

I installed upgrades at the beginning of this week. Firefox started to act very very slow. Than I decided to restart the PC and neither FF and Thunderbird don't show their main windows. 

I tried to start FF from a terminal window and it starts normally. I can see the process running and even a window pops up asking me if I would like to restore previous session. The same goes for Thunderbird. I get few alerts like "Certificate expired" but the is no sign of the main window :(.

I found Mozilla's FAQ for this issue at [http://kb.mozillazine.org/Browser_will_not_start_up](http://kb.mozillazine.org/Browser_will_not_start_up) but neither of these solutions work for me.

I have Ubuntu 6.10, FF 2 and TB 1.5. 

Now I'm running standalone versions which work. But I prefer those installed trough apt system.

lp mk

---

### Post by tommcd on 2007-04-01
When you start FF via terminal everything is ok? It seems odd that it works ok via terminal and not from clicking the icon. 
A few rgings you can try:
1) either reoboot or type <killall firefox-bin> in terminal, then try to restart FF.
2) disable or uninstall any addons (extensions) you may have and see if FF is ok then. Some extensions may not be compatible with a new FF upgrade.
3) create a new profile. Do <killall firefox-bin> then <mv ~/.mozilla ~/.mozilla.bak> then restart FF. If it is ok then, then your old profile was corrupt.
4) you could try reinstalling FF from synaptic.

---

### Post by mkljun on 2007-04-01
The problem is that the FF process starts normally (with clicking the icon or running it from the terminal). I can see it with ps. But there is no browser window I can use. So the process is there but I can't see its window.

1) either reoboot or type <killall firefox-bin> in terminal, then try to restart FF.

Did that. Actual reboot and the kill command.
ps ax | grep firefox
and than kill all the processes


2) disable or uninstall any addons (extensions) you may have and see if FF is ok then. Some extensions may not be compatible with a new FF upgrade.

Did that as well. Actually I moved .mozilla dir to another one and started a new profile from scratch. As adons are a part of profile (am I wrong?) I kind of disabled them.

3) create a new profile. Do <killall firefox-bin> then <mv ~/.mozilla ~/.mozilla.bak> then restart FF. If it is ok then, then your old profile was corrupt.

No. I downloaded a stand alone version and it uses my profile. 

4) you could try reinstalling FF from synaptic.

I tried to reinstall it with first removing it from the system and reinstalling it again with
   sudo apt-get remove firefox.
But this wants to remove ekiga, ubuntu-desktop and all sorts of other software. So I decided not to do this as I colud end up with no Gnome at the end :). Then I tried to reconfigure FF with
  dpkg-reconfigure firefox.
No change.

I'm trying to reinstall FF with synaptic now. And I have to restart FF :). I'll see if this helps.

Nope. It did not work :(.

lpmk

---

### Post by neoaddict on 2007-04-01
mkljun, you don't happen to be using SCIM or any other input methods, right?

---

### Post by mkljun on 2007-04-01
> **neoaddict said:**
> mkljun, you don't happen to be using SCIM or any other input methods, right?

Not that I'm aware of. I know that this is some kind of input method but nothing more. OK, I have to search on Wikipedia :).

How would I use SCIM anyway?

lp mk

---

### Post by neoaddict on 2007-04-01
Just wondering, sometimes it's related to Firefox not starting properly... XD

Have you tried installing Firefox from Mozilla?

---

### Post by mkljun on 2007-04-03
Is that even possible? The only way to "install" FF is to move the extracted files (from a downloaded package) in a desired directory and create a (for example) launcher or shortcut.

---

