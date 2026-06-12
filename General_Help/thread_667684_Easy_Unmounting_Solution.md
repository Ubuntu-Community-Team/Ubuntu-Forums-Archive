---
title: "Easy Unmounting Solution"
date: 2008-01-14
forum: General Help
---

### Post by christophski on 2008-01-14
I've been using ubuntu a lot more lately and there's one thing that bugs me the most. While I love the operating system, not being able to disconnect my thumbdrive without unmounting it first Iis very annoying, does anybody know of a program that would allow me to unmount it quickly, for example from the system tray? thanks

---

### Post by b0rka7a on 2008-01-14
Well... you can create a shell script for unmounting it :) For example - an icon on the Desktop.
If your thumb drive is /media/usb then make a script with these lines in it:
```
#!/bin/bash
gksudo umount /media/usb
```
Save it on your desktop with any name you want and in terminal type:
```
chmod +x ~/Desktop/<name_of_the_script>
```
Unfortunately it won't unmount it without password :)

---

### Post by gezzabob on 2008-01-14
Hi christophski,

You also may want to take a look into pmount.

To install it  type the following into a terminal.

sudo apt-get install pmount

Or add it with synaptic I guess.

And then read the man page for it with man pmount.  It may help you with your unmount without sudo issue but I don't know that much about it myself maybe you or somebody else could add it to a script for your desktop icon that you are looking for.

Good luck with that I hope this helps.

---

### Post by christophski on 2008-01-16
thanks for the replies guys :D This seems like a good solution for the time being.

---

