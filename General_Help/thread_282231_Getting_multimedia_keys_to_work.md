---
title: "Getting multimedia keys to work"
date: 2006-10-22
forum: General Help
---

### Post by srunni on 2006-10-22
Hi,

I have a Microsoft Wireless Laser Desktop 6000 keyboard/mouse combo. I got keyTouch so that I could use all the extra buttons that it has. However, many of them do not work. To find out whether these buttons had keycodes, I used the "xev" command. What I found out was, most of the keys do not have a keycode. However, one key, the "browser" key, does have a keycode, but doesn't work. I have rechecked the settings in keyTouch multiple times to make sure they were set up correctly, but I still could not fix the problem. Does anyone know why this could be? I could also use some help setting up keycodes for the other multimedia keys that I have.

Thanks in advance for the help!!

---

### Post by srunni on 2006-10-22
Any ideas?

---

### Post by srunni on 2006-10-22
...?

---

### Post by jester45 on 2006-10-22
you could write a sh
open a text editor and type
#!/bin/bash
xmodmap -e 'keycode ***=F**' # little discription of button
exit 0

save somewhere

open terminal type

chmod 755 /path/to/shell/script

then type this in the terminal

sh /path/to/chmoded/script

then open your keyboard settings and make a hot key the F** should be above F12 and the keycoade*** is the code for the key
you can also make the sh auto start

---

### Post by Ld. Ikon on 2006-10-22
You can use the keytouch editor to create a keyboard with your keys.

I got a hp dv1000 laptop, and the keymap included was wrong. So I remapped them.

---

### Post by srunni on 2006-10-22
I got keyTouch editor, but when I tried to run ```
keytouch-editor /dev/input eventX output-file
```, with X being 0, 1 or 2, I got ```
keytouch-editor: can't get version: Inappropriate ioctl for device
``` Any ideas?
EDIT: Never mind - trying again.

---

