---
title: "gimp 'freezes'when selecting Levels dialog"
date: 2013-11-03
forum: General Help
---

### Post by rebeltaz on 2013-11-03
I am asking this here, because I NEVER had this (or any other issues) before "upgrading" to 12.04.

When I open a photo in gimp, I can select, under the Colors menu, any of the options and they all work fine... EXCEPT for Levels. When I click Levels, it hesitates a couple of seconds and then the Level dialog box pops up. I cannot select any of the options, sliders or buttons - including OK or Cancel - nor can I close the dialog box. I can drag the box around the screen, but the gimp windows underneath the dialog box are never redrawn. 

The only way I can get out of the dialog box is to kill the gimp process. I have tried to apt-get --reinstall gimp but that had no effect on this issue.

Any ideas? Please?

---

### Post by rebeltaz on 2013-11-07
No?

---

### Post by rebeltaz on 2013-11-16
As usual, I will answer my own question, for the benefit of others with the same issue:

```

sudo apt-get purge gimp gimp-data
rm -r ~/.gimp-2.6
sudo rm -r /etc/gimp /usr/share/gimp
sudo apt-get install gimp gimp-data

```

---

