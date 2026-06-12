---
title: "compiz working?"
date: 2008-05-03
forum: General Help
---

### Post by methodtwo on 2008-05-03
Hi there i've just installed ubuntu 7.10 and i don't know if compiz is working or not.I don't know how to test if it's working.Can anyone tell me how?...also what should i do if it's not working?.Thankx in advance

---

### Post by Zorael on 2008-05-03
You should be able to enable them under Visual Effects someplace up in the menus.

---

### Post by Nebutron on 2008-05-03
> **methodtwo said:**
> Hi there i've just installed ubuntu 7.10 and i don't know if compiz is working or not.I don't know how to test if it's working.Can anyone tell me how?...also what should i do if it's not working?.Thankx in advance

There are a couple of things you will need to do to use compiz.

1. Go to SYSTEM>PREFERENCES>APPEARANCE> and click on "EXTRA" to enable effects.  If you do not already have the restricted drivers enabled, you will get a message asking about this.  Go ahead and enable them.

2.  GO to SYSTEM>ADMINISITRATION>SYNAPTIC PACKAGE MANAGER> and click search.  Search for "COMPIZ" and look in the results for COMPIZ CONFIGURATIONS SETTINGS MANAGER.  Check the box next to it and click apply to install.

3.  Go to SYSTEM>PREFERENCES>ADVANCED DESKTOP SETTINGS (This is compiz).  Click on GENERAL OPTIONS>DESKTOP SIZE, and change the horizontal (top one) number to 4.

4.  Click the "BACK" button.  Go to "DESKTOP CUBE" and click the little box next to it to enable.

5.  Go to "ROTATE CUBE."  Check the box

Now you can exit or close out of the COMPIZ window.  To rotate the cube press control/Alt/ and the left arrow or right or down.  Your cube should be turning with the left/right arrows and should unfold when you use the down arrow.

You can also press control/alt and hold the left mouse button down to spin and manipulate the cube.  HAVE FUN!!

---

### Post by tommyhakinen on 2008-05-03
Yes, it works on Ubuntu Gutsy. First you need to install CompizConfig Settings Manager.

> 
sudo apt-get install compizconfig-settings-manager


then to enable it just simply press Alt + F2 then enter this

> 
compiz --replace


---

