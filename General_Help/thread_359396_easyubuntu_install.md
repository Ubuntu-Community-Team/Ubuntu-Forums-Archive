---
title: "easyubuntu install"
date: 2007-02-11
forum: General Help
---

### Post by Rabbit_Alex on 2007-02-11
Question 1:
[This page]("http://easyubuntu.freecontrib.org/get.html") about installing the EasyUbuntu scripts tells me to use this command after downloading the package.

```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
```

The terminal says that I am not in the sudoers file and this incident will be reported.  Isn't the point of the "sudo" command to temporarily give me admin rights so I can run the command?  How do you get around this?  I beleive this may be causing the problem for my second question

Question 2:
I am trying to install the EasyUbuntu scripts (just started using Ubuntu last week and found them today).  I have downloaded the package (a .deb file).  I double click on it and the package manager program pops up.  I click on "Install packages" and I get an error window that says:

"Failed to run gdeb-gtk '--non-interactive' '/home/alex/Desktop/easyubuntu_latest.deb' as user root.
The underlying authorization mechanism (sudo) does not allow you to run this program.  Contact your system administrator."

How do I run the package manager as root so I can install Easy Ubuntu?

Question 3:
Also, the option for "Synaptic Package Manager" has gone missing from my System->Administration menu in GNOME.  How do I get it back?

Question 4:
Also, the option for "Add/Remove applications" is missing from the bottom of my Applications menu.  I thought it was supposed to be there (like in XFCE).  How do I get it back?

Thank you kindly.

---

### Post by Rabbit_Alex on 2007-02-12
I got it working.  Somehow I was removed from the sudoers list.  I rebooted in recovery mode and added my name to the /etc/X11/group file and everything works now.

---

