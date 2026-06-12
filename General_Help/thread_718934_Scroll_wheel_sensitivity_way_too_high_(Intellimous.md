---
title: "Scroll wheel sensitivity way too high (Intellimouse Explorer 2.0)"
date: 2008-03-08
forum: General Help
---

### Post by zingyGecko on 2008-03-08
I have a Microsoft IntelliMouse Explorer 2.0, which scrolls WAY too fast in every application.  For example, in Opera when I barely move the scroll wheel up, its like pressing the up arrow key 8 times.  In gnome-terminal, scrolling up with the scroll wheel moves 4 lines at a time.

Is there a way I can adjust my scrollwheel speed or sensitivity?  (The Ubuntu or Gnome devs should really add a way to adjust this in System > Preferences > Mouse)

---

### Post by nilarimogard on 2008-03-08
it's because you probably just booted to windows and restarted in ubuntu. try: shutting down the computer, then power it up and boot into ubuntu, or unplug the mouse and plug it back in...

(i had that weird problem too untill i read about it on these forums)

---

### Post by donkeyX on 2008-04-18
Hey nilarimogard's,

I have the same mouse and the same problem. I had the problem sorted before i upgraded to hardy but i did a full install and have lost the config. My solution was a little more detailed but i cannot find the thread that had it. Basically, i had to edit a config file with the number of scroll lines, which i have no idea where it is. Will let you know as soon as i find it ;)

Cheers donkey.

---

### Post by nilarimogard on 2008-04-20
that would be xorg.conf found in /etc/X11

---

### Post by pannerrammer on 2008-05-20
Hi.

If you previously used imwheel see [http://ubuntuforums.org/showthread.php?t=787790](http://ubuntuforums.org/showthread.php?t=787790) which will give you control over the mouse.

Then in Terminal type ```
man imwheel
``` and read the bit about sensitivity.

You'll need to add it to the basic imwheel command ```
imwheel -k -f -b "0 0 0 0 8 9"
```Hope that points you in the right direction.

Best of luck.

---

