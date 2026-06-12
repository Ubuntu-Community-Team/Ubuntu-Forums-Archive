---
title: "Kubuntu not loading - x-org reconfigure crashing"
date: 2008-02-15
forum: General Help
---

### Post by Jeztastic on 2008-02-15
Hi,

I have had Kubuntu running a while. I then put some desktop widgets on it, and now it's stopped working. It is just hanging on boot.

I have tried reconfiguring x-org, but when I get to the section where it tries to detect my monitor, it crashes. Blank screen, the lot. Please help! I went back to vi$ta for a while but I am missing lovely Kubuntu. :(

---

### Post by amingv on 2008-02-15
Try running:

```
sudo dkpg-reconfigure kdm kdesktop
```

You may loose all changes you made, but maybe it will work; then try to reconfigure xorg again.

---

### Post by Jeztastic on 2008-02-16
OK, I changed the graphics driver to Vesa, and now everything works. When I try to switch back to to fglrx it crashes again. How do I work out what is conflicting?

Jez

---

### Post by pointone on 2008-02-16
Check /var/log/Xorg.0.log after it crashes to find an explanation.

---

