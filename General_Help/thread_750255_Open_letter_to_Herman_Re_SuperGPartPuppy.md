---
title: "Open letter to Herman Re SuperGPartPuppy"
date: 2008-04-09
forum: General Help
---

### Post by unutbu on 2008-04-09
Dear Herman,

If the little star medal was enabled on your Ubuntu forums posts, I think I would  press every single one of them. Thank you so much for all the helpful, intelligent information you have been sharing.

This morning I made my very own SuperGPartedPuppy rescue disk following your instructions at
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html).

It works beautifully, but I wanted (along with thanking you) to alert you to a speedbump I encountered along the way.

If readers of your guide use the latest version of SGD, v. 0.9701, (from [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)) the /boot/grub/menu.lst that comes with it  has the stanza 

```
title Super Grub Disk
# The two commands: setgrubdevice and usbshift are needed
# so that SGD works well.
usbshift
configfile $(grub_device)/boot/sgd/sgd.lst

```
Note the configfile line points to sgd.lst, not menu.lst as it says in your guide. To experienced grub users its probably obvious this should not be changed, but I was a little unsure at first. 

Since Adrian15 is apt to change SGD again in the future, it might be wise to describe what things in particular need to be edited in menu.lst instead of suggesting to copy the menu.lst straight out of your webpage. (I also ended up burning a disk with a grub entry entitled 'Puppy-2.16-Seamonkey-Fulldrivers' even though its really Puppy-3.01-seamonkey, but I should have caught that. Doh!)

Also, while I have your attention, may I suggest a few very minor improvements for the webpage?
1) Please find/replace 'superpartpuppy'  -> 'supergpartpuppy' and
2) 'supergrub.iso' -> 'supergrubiso'.
3) Some code boxes have "Code:" written above them, some do not. Making it consistent would improve the look of the page.

Anyway, many thanks for all the extremely helpful things you've done for the Ubuntu community. I salute the greatness that is Herman!

Regards,
Unutbu

---

### Post by adrian15 on 2008-04-09
> **unutbu said:**
> 
Since Adrian15 is apt to change SGD again in the future, it might be wise to describe what things in particular need to be edited in menu.lst instead of suggesting to copy the menu.lst straight out of your webpage. 

Do not doubt it, current quick menu is not obvious and discourages people to use SGD. However I think that main menu.lst will always link to sgd.lst.

adrian15

---

### Post by Herman on 2008-04-09
:) Thank you for the compliments and for your helpful information there, unutbu. :)

Now I am thinking about what to do with that how-to.
Obviously, it needs updating. Super Grub Disk has changed a lot since that was made and so has GParted and Puppy Linux too. 

Regards, Herman :)

---

