---
title: "gnome-launch-box segmentation fault"
date: 2005-06-03
forum: General Help
---

### Post by ubuntu_demon on 2005-06-03
Hi,

When I start typing in gnome-launch-box I get a segmentation fault. This is the output in the terminal :

```

Could not load icon "msn": Icon 'msn' not present in theme
Could not load icon "gnome-mime-application-vnd.sun.xml": Icon 'gnome-mime-application-vnd.sun.xml' not present in theme
Segmentation fault

```

(I use backports)

---

### Post by dcraven on 2005-08-05
This is fixed (according to the changelog) in the svn version available at the gnome-launch-box website. The problem was with an icon not being available in the currently used icon theme.

Cheers,
~djc

---

### Post by ubuntu_demon on 2005-08-06
thnx for the info

---

