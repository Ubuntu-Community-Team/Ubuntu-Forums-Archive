---
title: "Remove Grub"
date: 2008-01-09
forum: General Help
---

### Post by Danyl on 2008-01-09
Hi all

Have scoured these forums but the solutions seem to be for people who want to ditch Ubuntu and go back to Windows. My scenario is vice versa (ie I have ditched Windows and want to keep Ubuntu).

I have deleted my Windows partition using Gparted and my computer still boots up with Grub giving me the option to select Windows.

I basically want to be able to turn the computer on and it run all the way to my Ubuntu desktop without worrying about Grub.

How do I make it so Grub doesn't pop up at boot up at all?

---

### Post by taurus on 2008-01-09
Edit /boot/grub/menu.lst

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
and change the timeout option from 3 seconds to 0 second.

```
timeout   0
```
Then, scroll down to the end of it and remove the entry for your windows since you don't need it anymore.

Save it and reboot.

---

### Post by LaRoza on 2008-01-09
Backup grub:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bk

```

Edit grub:

```

gksudo gedit /boot/grub/menu.lst

```

Now, delete the Windows entry(s). They will be at the end.
```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

It will look like that, delete the entry(s) below the ###END DEBIAN ... line, but don't delete that line

Now, look for:

```

# hiddenmenu

```

Remove the "#" 

Now, look for 

```

timeout 10

```

Change the number to a lower number (not 0), 3 will be good.

When you boot, you will see a little prompt in the upper left saying to press ESC to see the menu, and it will automatically boot Ubuntu in whatever time you specified.

**<edit>**
I noticed that another posted when I was typing, the advice to make it 0 is not really bad however, I recommend making it a low number so you can choose to see the menu if you ever have to go into the recovery console.
**</edit>**

---

### Post by Danyl on 2008-01-09
What a quick response! Thankyou both!

---

