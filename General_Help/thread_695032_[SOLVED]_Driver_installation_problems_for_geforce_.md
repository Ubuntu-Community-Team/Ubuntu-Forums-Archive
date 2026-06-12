---
title: "[SOLVED] Driver installation problems for geforce 7600gs"
date: 2008-02-12
forum: General Help
---

### Post by upthelum on 2008-02-12
Hi all. Desktop effects and customization seems pretty quiet so i thought i'd post this here.

Driver installation produces an error which says i am running an x server, which is correct, but i must exit the server, which is fine, if i knew how to do that. Can someone tell me how to exit the x server to allow me to install these drivers i downloaded from nvidia website?

Any help greatly appreciated thanks....

---

### Post by apetresc on 2008-02-12
> **upthelum said:**
> Hi all. Desktop effects and customization seems pretty quiet so i thought i'd post this here.

Driver installation produces an error which says i am running an x server, which is correct, but i must exit the server, which is fine, if i knew how to do that. Can someone tell me how to exit the x server to allow me to install these drivers i downloaded from nvidia website?

Any help greatly appreciated thanks....
You could use Ctrl+Alt+F3 to go to a tty, then use 'kill' to kill the X Server, and then do everything you need.

However, I highly reccomend letting [Envy](http://www.albertomilone.com/nvidia_scripts1.html) install these drivers for you.

---

### Post by upthelum on 2008-02-12
Ran envy which gave the error in the screenshot...

---

### Post by upthelum on 2008-02-12
Bump bump

---

### Post by Whiffle on 2008-02-12
I posted sort of a wannabe howto on this here (post #8 ).  Be sure you remove *everything* nvidia related before you do it, and remember that if your kernel gets updated you'll have to do it over again.

[http://ubuntuforums.org/showthread.php?t=689897](http://ubuntuforums.org/showthread.php?t=689897)

---

### Post by upthelum on 2008-02-12
I got it installed using Envy. Thing is, i wanted compiz fusion running and thought this would be the fix but that's not so. This is side tracking from the initial post but as shown in this screenshot when opened compiz just hangs on the sand timer thingy then stops, any ideas? If not i'll post a new thread.
Thanks for your help.

---

