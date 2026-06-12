---
title: "Reformat SDCard locked by other user read write"
date: 2021-01-12
forum: General Help
---

### Post by Jonners59 on 2021-01-12
I have an SDCard I use in a Raspberry Pi4B to run nanoDLP(uses linux) OS for a 3D printer.
The printer stopped suddenly, something with the OS must have gone wrong, leaving me with no option but to turn off via the power switch.  I now have an SDCard that I can not use as it is locked by "a user" and my best option to fix things is to start over by reformatting the card.  Trouble is GPart, and all the cmds I know do not work.  They say they do not have the permissions required.

Any ideas please?

---

### Post by tea for one on 2021-01-12
When you open [COLOR="#0000FF"]gparted[/COLOR], you should see a window asking for authentication?

Enter your login password to access elevated privileges.

---

### Post by crip720 on 2021-01-12
If you have access to Windows, there is a SDcard formatter program that is good.  You did check to see if the little tab on side is in right position?  If using sudo with CMDs should not have problem with permissions unless the tab is in wrong position.

---

### Post by Jonners59 on 2021-01-12
> **tea for one said:**
> When you open [COLOR=#0000FF]gparted[/COLOR], you should see a window asking for authentication?

Enter your login password to access elevated privileges.

Thank you, but gparted always opens as administrator, requiring password.  That does not work.  But thank you.

> **crip720 said:**
> If you have access to Windows, there is a SDcard formatter program that is good.  You did check to see if the little tab on side is in right position?  If using sudo with CMDs should not have problem with permissions unless the tab is in wrong position.
Thank you, but none of these work.  This is a microSDCard so has no tab, and have tried Windows, with same.  I have used sudo, but also same.  Can not make changes.

---

### Post by crip720 on 2021-01-12
If using a micro SDCard holder, the holder will have a tab.  Might also be looking at a card that has bit the dust.  Even my cards that had only read permissions I could format easy.

---

### Post by tea for one on 2021-01-12
Please explain what happens when you open gparted and enter your password?
There must be something else wrong if your password fails to open it?

In the meantime try:-

gnome-disk-utility
gparted in a live session

---

### Post by Jonners59 on 2021-01-12
> **crip720 said:**
> If using a micro SDCard holder, the holder will have a tab.  Might also be looking at a card that has bit the dust.  Even my cards that had only read permissions I could format easy.

Thank you, but no.  It is not in a holder.  The card fits in the Pi without need for a holder, and I use it to work on in my PC which also does not need a holder - there is NO lock tab.

This is LOCKED in read only because the it was being used by the Pi and crashed, so it is locked "by another user".  I have used gparted and a couple of other formatters for about 15 yeas, they can not fix this.  This needs a higher level of administration and cmd.

> **tea for one said:**
> Please explain what happens when you open gparted and enter your password?
There must be something else wrong if your password fails to open it?

In the meantime try:-

gnome-disk-utility
gparted in a live session
It opens as normal after I enter my password and lists the card and it's contents, along with all the other HDs.  I then select the card as normal and select delete.  I then select action and it starts but stops saying it can not complete the action because the card is protected...  Just tried STartup Disc creator and it says 
Could not write the disc image (/media/Documents/Project Plans/3D Printing/Setup/nanoDLP/images/nanodlp.img) to the device (/dev/sde).

I need to reboot as GPart seems to be open in the background and not showing itself.

PS:  This is not an unheard of issue.  I have seen a number of these cases, some say there is no way to recover the disc, but I do not believe in never and it works, just locked to a non existent user

---

### Post by tea for one on 2021-01-12
Why not write a new partition table to the card rather than deleting a partition?

Or use [COLOR="#0000FF"]parted[/COLOR] via the terminal?

[https://www.tecmint.com/create-disk-partitions-in-linux/](https://www.tecmint.com/create-disk-partitions-in-linux/)

---

### Post by Jonners59 on 2021-01-12
> **tea for one said:**
> Why not write a new partition table to the card rather than deleting a partition?

Or use [COLOR=#0000FF]parted[/COLOR] via the terminal?

[https://www.tecmint.com/create-disk-partitions-in-linux/](https://www.tecmint.com/create-disk-partitions-in-linux/)

Same issues - read only whether parted in a terminal or GParted opened directly and add PW or in a terminal under sudo su
[ATTACH=CONFIG]287732[/ATTACH][ATTACH=CONFIG]287733[/ATTACH]

---

### Post by crip720 on 2021-01-12
When I was having trouble with read only cards, did find some posts that with a command would remount them as read/write again.  Google changing SD card to read write, and you should find them.  Have problem understanding why you can't format them though, unless it is broken.

---

### Post by Jonners59 on 2021-01-12
> **crip720 said:**
> .... Have problem understanding why you can't format them though, unless it is broken.

Thank you.
It is because the card was being read when the pi crashed.  SO it is locked to another user.  That has to be over-ridden.  It maybe it can not be done.  It is not that unusual, and googling finds some who say it can't be done and there are many solutions, of which none have worked.  I may have to throw it, but if I can save it I would rather.

---

### Post by tea for one on 2021-01-12
Try disk-destroyer - identify your device first to avoid catastrophe.

```
sudo dd if=/dev/zero of=/dev/sd[COLOR="#0000FF"]x[/COLOR] bs=1M count=10
```

Then see if gparted will allow you to add a partition table.

---

### Post by Jonners59 on 2021-01-12
> **tea for one said:**
> Try disk-destroyer - identify your device first to avoid catastrophe.

```
sudo dd if=/dev/zero of=/dev/sd[COLOR=#0000FF]x[/COLOR] bs=1M count=10
```

Then see if gparted will allow you to add a partition table.
Thanks for the try, but, no.
```
sudo dd if=/dev/zero of=/dev/sd[COLOR=#0000FF]e[/COLOR] bs=1M count=10
```
dd: failed to open '/dev/sde': Read-only file system

---

### Post by tea for one on 2021-01-12
This isn't going to plan yet, is it?

Are you familiar with [COLOR="#0000FF"]gdisk[/COLOR]

Here is the info [http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)

It may help, it may not...............

---

### Post by Jonners59 on 2021-01-12
> **tea for one said:**
> This isn't going to plan yet, is it?

Are you familiar with [COLOR=#0000FF]gdisk[/COLOR]

Here is the info [http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)

It may help, it may not...............

No, it isn't, but I didn't expect it too as I had tried all the usual stuff.  I'll need to go through this tomorrow.

---

