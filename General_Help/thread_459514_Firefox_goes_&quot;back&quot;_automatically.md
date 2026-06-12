---
title: "Firefox goes &quot;back&quot; automatically"
date: 2007-05-30
forum: General Help
---

### Post by alof8k on 2007-05-30
Hi,

I just did a clean install of edgy and whenever I use firefox, automatically the "back" button gets pressed somehow.  So for example, If I load up firefox and go to google.com and do a search, then while i'm scrolling down the search results, automatically the browser goes back to google's homepage.  

anyone have this issue or know how to fix it?

Any help is greatly appreciated :)

---

### Post by alof8k on 2007-05-30
Now i'm having the same problem but with application windows.  For example, if I have two firefox windows open, and I switch to the other window by clicking on the taskbar (bottom), then as I drag my mouse, the previous window comes on top.  

Anyone with any solutions? :(

---

### Post by Malibu Illusion on 2007-05-30
Shot in the dark: are you scrolling up/down with the middle mouse button at all?  The behavior of this can be emulated to do exactly what you're describing.

---

### Post by alof8k on 2007-05-30
> **Malibu Illusion said:**
> Shot in the dark: are you scrolling up/down with the middle mouse button at all?  The behavior of this can be emulated to do exactly what you're describing.

sometimes, yes.  but even when i don't scroll it happens simply when I move the pointer via touchpad.

my system is a ashton digital (ECS G730), and it has a synaptics touchpad.  could the touchpad be the issue here?  is it some kind of mouse gesture that's configured to behave this way when activated?

---

### Post by dagrump on 2007-05-30
(grumpy rant ) touchpads bite, I bought a usb mouse as the touch pad seems to think you've clicked something just from a slight change of pressure. There could be a way to adjust the sensitivity but I still hate touch pads. But, yes it very well could be the touch pad.

---

### Post by daimaru on 2007-05-30
since the touchpads defautl behaviour includes letting u scroll horizontally or vertically by touching the edges, u might just have a messed up mouse setting. you might want to plug in a external mouse and see if u still get the same problems and then try using the mousewheel to scroll if it activates the back and forward button of ur browser u have ur mouse configured wrong. as in z-axis etc in the /etc/X11/xorg.conf file.

---

### Post by alof8k on 2007-05-31
> **daimaru said:**
> since the touchpads defautl behaviour includes letting u scroll horizontally or vertically by touching the edges, u might just have a messed up mouse setting. you might want to plug in a external mouse and see if u still get the same problems and then try using the mousewheel to scroll if it activates the back and forward button of ur browser u have ur mouse configured wrong. as in z-axis etc in the /etc/X11/xorg.conf file.

thanks for the help, and yeah it does seem like a messed up mouse setting.  

what I did now was install gsynaptics and enabled SHMConfig in the xorg.conf and I've noticed the problem is gone when I disable horizontal scrolling(which the scroll wheel doesn't have anyway) and unchecking "continue scrolling on edge".  

however the problem comes right back if I close the gsynaptics (touchpad preferences) program.  when I re-open gsynaptics, the settings go back to the previous one.  so certainly the setings are not getting saved.  is there any way to save the settings that I edit via gsynaptics?

---

