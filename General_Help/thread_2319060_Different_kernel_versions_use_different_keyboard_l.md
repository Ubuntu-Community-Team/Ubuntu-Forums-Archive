---
title: "Different kernel versions use different keyboard layouts when inputting FDE pass"
date: 2016-03-31
forum: General Help
---

### Post by Stannis_King on 2016-03-31
I have kernels 4.2.0-16 and 4.2.0-34 installed on Lubuntu 15.10 system with full disk encryption.

When I boot up with 4.2.0-34 and get to the FDE pass prompt, the pass is input using US keyboard layout, but when I boot up with 4.2.0-16 the pass is input using a different keyboard layout.

During the installation of Lubuntu I choose a non-US keyboard layout and after the installation both kernels would use the non-US keyboard layout I chose. However, after the install in Language Support I chose English to "apply system-wide", but this seems to have been applied only to the 4.2.0-34 that I booted up with when I changed the settings. At least that's what I think happened.

So, how would I change the keyboard layout on 4.2.0-16 to US one, too?

** EDIT:** Well, this was a stupid question. Removing, purging and then reinstalling `linux-headers-4.2.0-16 linux-headers-4.2.0-16-generic linux-image-4.2.0-16-generic linux-image-extra-4.2.0-16-generic` did the trick.

---

### Post by QDR06VV9 on 2016-03-31
preferences->lxkeymap->select the language. click apply

Or in the terminal
```
 echo '@setxkbmap -option grp:alt_shift_toggle "en, us"' | sudo tee -a /etc/xdg/lxsession/Lubuntu/autostart

```
Hope i understood correctly.

---

### Post by Stannis_King on 2016-03-31
I already solved it by removing, purging and reinstalling the -16 kernel, but thanks anyways! :D

---

