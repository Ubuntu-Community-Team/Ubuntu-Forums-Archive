---
title: "Chromium prints in inverse black and white"
date: 2018-10-30
forum: General Help
---

### Post by webmiester on 2018-10-30
Hi Everyone,

I am using Chromium 60 on Ubuntu 16.04 on rpi.  I isolated my unit from the internet by using iptables.

My problem started yesterday when my chromium started printing in inverse black and white.  I don't know why.  When I use the system print dialogue it prints fine but chromium keeps reversing the colors.  I am using it as kiosk so I cannot have the users switch to system print dialogue all the time.

What caused this problem?  

So I upgraded my chromium browser to version 70, and the rest of Ubuntu as well.  Now the version 70 keeps closing when it prints.  Why is this?  I am unable to find a solution.  Most of my machines are still with the old setup but many have started to print in inverse colors too.  It's very strange.  Has anyone encountered these problems before?

Other notes: my printers are Epson m100 printers but I use Epson Office 1100 driver since m100 has no driver for arm processors.  It prints fine using system dialogue.

---

### Post by dino99 on 2018-10-30
' journalct -b ' is your best friend to catch the trouble reason.
Is your system cleaned ? Use : autoremove, gtkorphan, bleachbit (as root, carefully select settings)

---

