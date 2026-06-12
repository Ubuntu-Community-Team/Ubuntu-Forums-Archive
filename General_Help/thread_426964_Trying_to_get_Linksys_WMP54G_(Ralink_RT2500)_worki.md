---
title: "Trying to get Linksys WMP54G (Ralink RT2500) working in Feisty without internet."
date: 2007-04-29
forum: General Help
---

### Post by Bslashingu on 2007-04-29
Kind of in a jam here. I'm not very wise in the world of Linux, but I  know a bit about the terminal and what-not, just basic commands.

Been working for a little while on trying to get my Linksys WMP54G (confirmed it to be Ralink RT2500) in Feisty Fawn 64bit, but since I have no internet connection, it's becoming a problem. My wireless router uses WPA Personal as it's security, and when I try to select the security in GNOME Network Manager, the option doesn't show up. I've been pounding my head against the wall, mostly because every single Distribution I've tried has the same problem.

I'm dual-booting Windows on another hard drive, and since I have no internet on Ubuntu, transferring information back and forth is a real pain.

If someone can help out, it'd be appreciated a whole ton. If you need anymore information about my computer or any logs, anything at all, I'll try to post it.

:popcorn:

---

### Post by crispy_420 on 2007-04-29
WPA is not there by default, you will need wpa-supplicant. If I were you I would try to connect via hardline to setup network manager. Take your system to a friends house if possible.

Does rt2500 linux driver even support WPA?

---

### Post by Bslashingu on 2007-04-29
In Windows I can run WPA fine. A wired connection doesn't work either, Ubuntu won't connect to the internet through both of my Ethernet ports, although it detects them.

---

### Post by Bslashingu on 2007-04-30
Bump.
Trying out all of these tutorials on the internet isn't helping, I already had to reinstall Ubuntu, and hopping back and forth isn't fun either. :(

---

### Post by frying_fish on 2007-05-02
I'm having the same issue as you Bslashingu, I can get the card working either unsecured or by WEP, but as yet I cannot make it work with WPA, it just will not show the option, even trying the commandline options for iwpriv (after turning off network-manager) fails, the tutorials haven't helped me so far, but which ones are you relating to?

---

### Post by Bslashingu on 2007-05-13
Giving it a quick bump before I give up completely.

---

