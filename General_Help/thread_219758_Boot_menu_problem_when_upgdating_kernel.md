---
title: "Boot menu problem when upgdating kernel"
date: 2006-07-20
forum: General Help
---

### Post by drfox on 2006-07-20
I originally double-booted, with / on hd0,4.
Now that I'm with Ubuntu as a sole OS, my / is on hd0,0
Everytime I update my kernel, the menu items in /boot/grub/menu.lst get changed to / on hd0,4.
There must be an editable file somewhere on my disk that will tell the menu.lst updater that my / partition in 0, not 4.
What file is that?

Thanks in advance. 

Larry

---

### Post by klytu on 2006-07-20
> **drfox said:**
> I originally double-booted, with / on hd0,4.
Now that I'm with Ubuntu as a sole OS, my / is on hd0,0
Everytime I update my kernel, the menu items in /boot/grub/menu.lst get changed to / on hd0,4.
There must be an editable file somewhere on my disk that will tell the menu.lst updater that my / partition in 0, not 4.
What file is that?

Thanks in advance. 

Larry

I think the file you seek is device.map I believe you will find it in /boot/grub, but just in case my memory is faulty try:

```
sudo updatedb 
locate device.map
```

to find where the file lives on your set-up.

---

### Post by Ramses de Norre on 2006-07-20
Hmm I think you need to edit your grub default options, in /boot/grub/menu.lst search for this line:```
# kopt=root=/dev/sda1 ro

```
And change it to your new root. Don't mind the # this is normal.
Then run ```
sudo update-grub
``` and check whether the root is set correctly.

---

### Post by scarabaeus on 2006-07-20
thanks Ramses de Norre. this was helpful. i had to manually change the menu.lst several times with a knoppix to get my system up and running and it was really annoying. hope this don't happen again with this...

cheers

---

### Post by ekravche on 2006-07-23
Had to change 
# groot=(hd2,0)
to 
# groot=(hd0,0)

and this fix seems to work for me

---

