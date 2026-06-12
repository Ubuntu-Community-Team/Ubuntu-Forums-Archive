---
title: "Booting to Ubuntu First on Wubi"
date: 2007-07-23
forum: General Help
---

### Post by kevinmedina on 2007-07-23
Wubi has been awesome so far, and Ubuntu has given me so much confidence in Linux and all the open-source softwares that I'd like to take my relationship with Ubuntu to the next level.....

I want to Ubuntu to be listed first on Grub, and to boot to Ubuntu automatically after the 10 seconds.

Can anybody help me do this?  Is there any chance of seriously screwing things up because I'm using Wubi?

Thanks for any help you can give me :)

---

### Post by ecology2007 on 2007-07-24
Yes.
Reboot in windows and find c:\boot.ini.
It may be hidden and write protected.
Edit it and set the default and timeout options.

---

### Post by roganjosh on 2007-07-24
Alternatively, go to Start > Run and type

```
msconfig
```

Click the boot.ini tab and select the Ubuntu line (will most likely be the bottom one). Then press the "Make Default" button. You can also move it to the top of the list by pressing the "Move Up" button.

Edit: Also, there is a box in that dialog that allows you to change the timeout, default is 15.

---

### Post by kevinmedina on 2007-07-25
Thanks for the help!:grin::grin:

---

### Post by Epilonsama on 2007-07-28
If you wanna, you can also reinstall Ubuntu on an real partiton by using either LVPM or doing a clean install.

---

### Post by kevinmedina on 2007-07-31
I think I'm close to doing that.  I find myself using less and less of Windows XP.  I'm in the process of figuring out WINE, and once I get that going there really is absolutely no point of me even having Windows!!!  \\:D/\\:D/

---

### Post by ago on 2007-08-01
[http://www.wine-doors.org/](http://www.wine-doors.org/)

---

