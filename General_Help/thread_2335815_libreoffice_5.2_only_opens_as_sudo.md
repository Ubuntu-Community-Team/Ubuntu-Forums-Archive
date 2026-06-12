---
title: "libreoffice 5.2 only opens as sudo"
date: 2016-09-01
forum: General Help
---

### Post by miatawnt2b on 2016-09-01
I've installed libreoffice 5.2 from the libreoffice ppa after first purging all libreoffice 5.1 from my ubuntu 16.04 install. After the install of 5.2, libreoffice will only open from a sudo terminal window. If I try to open it as my normal user, the oosplash screen pops up and hangs. I tried launching as myself from a command line to see if there were any error messages, but nothing at all comes up in the terminal window. Just a hanging splash screen. I've tried purging and reinstalling 5.2, chown-ing the .config/libreoffice in my home dir, as well as deleting the .config/libreoffice directory completely. Same issue.

Any thoughts as to what's happening and how I can fix it?

-J

---

### Post by #&amp;thj^% on 2016-09-01
The only thing that worked for me when this happened about a  year ago was to make sure everything was uninstalled
```
sudo apt-get remove --purge libreoffice*.*
```
And
```
sudo add-apt-repository ppa:libreoffice/ppa
```

```
sudo apt-get update
```

I think (I am Guessing) what might be going on with your setup is libreoffice-gtk not being fully removed.

```
sudo apt remove libreoffice-gtk
```
 And Now
```
sudo apt dist-upgrade && sudo apt install libreoffice-gtk2 libreoffice-gnome
```
You should now have a shiny new versions of LibreOffice Writer, Calc, Impress, et al.
Fingers Crossed

---

