---
title: "Installing HP PSC"
date: 2008-01-02
forum: General Help
---

### Post by sethfc on 2008-01-02
Hey guys,

I'm following these directions:

> 
1) Install the HPLIP packages.

Code:

sudo apt-get install hplip hplip-data hplip-ppds hpijs foomatic-db-hpijs

2) Run hp-makeuri /dev/usblp* (where * depends on how many printers you have, if you only have one, it will be usblp0), this will produce something like;

Code:

CUPS URI: hp:/usb/psc_1310_series?device=/dev/usblp0
SANE URI: hpaio:/usb/psc_1310_series?device=/dev/usblp0

Save the CUPS URI: line for later, you'll need it (just leave it in a terminal so you can copy/paste it later)

3) Open up a web browser and go to [http://localhost:631](http://localhost:631)

4) Click Add Printer. If you already have a printer driver installed for your HP PSC you'll want to remove it. If your printer worked before, but your scanner did not, this will get both of them working, and you'll be able to check your ink levels.

5) On the first screen, you'll only need to fill in the first entry. That is the Printer Name. You can name it whatever you want, but you cannot have certain characters in the name, including /, #, and no spaces. I named mine HP_PSC1315. Click Continue.

6) There is no number 6.

7) Leave this option on AppSocket/HP Jetdirect. This is important. Click Continue.

Now on the next page, you will see a place for entry that says socket. Delete that and paste in your CUPS URI: that you got from step 2. You only need the part that is AFTER CUPS URI: (in my example, it would be just hp:/usb/psc_1310_series?device=/dev/usblp0) Click Continue.

9) This page is a little pain. With me, if I tried to select the driver, it would just continuously load. So instead you may just want to take a shortcut and click the Browse button for a PPD. The PPDs for hplip are installed in /usr/share/ppd/hplip. Select the one that is closest to the model of PSC that you have. Click Continue.

10) You're done. Open up either the gnome-cups-manager (System -> Administration -> Printing) or KDE's print manager or wherever you want to print something from and you shoud be able to print.

11) You should now be able to scan as well. Open up xsane or kooka and try it out.


i'm on step #2.  What does it mean "run".  Do i type something in the terminal, or what?

I am WAY noob.  Sorry for a retarded question =x

-seth

P.S.: HP 1210 PSC.

---

