---
title: "no black in printing"
date: 2008-01-22
forum: General Help
---

### Post by AGSzabo on 2008-01-22
hello,

my psc1110 works fine as long as i only copy a page with it. the copy in black/white is perfect.

but when printing something, then the printer/cups acts like there was no black ink and everything comes out in green. the printing system in the menu-bar tells me that the ink is empty while in fact it is not! i just inserted a brand new inkhead.

why does my system think the black ink is empty and why comes all in green and not in black? copying in black/white works fine...

greets,
Andreas

---

### Post by jeffus_il on 2008-01-22
In the cups admin ```
localhost:631
``` in your browser, is the printer driver used ```
HP PSC 1110 Foomatic/hpijs
```  ???

---

### Post by mario.kostelac on 2008-01-22
I have the same problem and here is that driver used...
What to do?

---

### Post by AGSzabo on 2008-01-23
the driver is HP PSC 1100 Foomatic/hpijs

---

### Post by fragos on 2008-01-23
I don't think your 1100 uses the black ink cartrige when printing in color.  Color gets black by printinting all three colors.  Perhaps your color ink is getting low.  The HP Toolbox will show you ink levels.  It does with my PSC 1410.

---

### Post by Sef on 2008-01-23
> Perhaps your color ink is getting low. The HP Toolbox will show you ink levels. It does with my PSC 1410.

If you don't have it, then do this to get it:

Applications > Add/Remove > Search: type in HPLIP > Click on box > Apply Changes > Apply > Close  (Note: You might need to change the upper right box to 'All Available Applications'.)

---

### Post by AGSzabo on 2008-01-24
ok, the problem was that the red ink was empty in the color cartridge and the config was set to color only. now i set it to black+color and everything black is fine.

how can i start the hplip-gui or the tool that shows the ink level? im sure it is installed.

---

### Post by fragos on 2008-01-24
It's in System-> Preferences.  You may need to right click Applications and select "Edit menus" to make it visible.

---

