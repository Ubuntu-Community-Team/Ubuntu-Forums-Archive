---
title: "Garbled Display"
date: 2007-09-09
forum: General Help
---

### Post by zutronius on 2007-09-09
Today when I went to load up Ubuntu, all looked fine. The boot up screens and up to the login screen all worked fine. I enter my name and password and it goes to load up the main screen or main window, and that was when the screen goes all garbled and has hundreds of lines through it. I don't think it would be the video card because the display works fine until after I login and it goes nuts. How do I correct this? I have lots of data I would love to save without having to reinstall.

---

### Post by zutronius on 2007-09-09
Any help will be appreciated. I need this pc back up and running asap. :(

---

### Post by merlinus on 2007-09-09
Can you boot in recovery mode?  This will get you to a CLI, and you can try to reconfigure the x-server.

```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by nowshining on 2007-09-09
it would also be nice to let everyone know what your video card is , is it internal or external - what brand is it?? nvidia ati intel, and what model is it 82865g, FX5200., ??

---

### Post by zutronius on 2007-09-09
My video card is an ATI Radeon 9200 PCI card.

---

### Post by zutronius on 2007-09-09
I have just went through the reconfigure xserver step and i still have the same problem.

---

### Post by merlinus on 2007-09-09
Accept most defaults but select vesa as video driver.  Once you are at a gui, you can search for and install the correct drivers.

---

### Post by nowshining on 2007-09-09
ATI are the most problematic video card drivers for linux - it is/was closed source by was I mean just recently there was a post in cafe that they were to soon release open source drivers so it's a wait...

---

