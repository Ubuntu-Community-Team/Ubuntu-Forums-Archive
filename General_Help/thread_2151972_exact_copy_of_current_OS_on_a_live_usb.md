---
title: "exact copy of current OS on a live usb"
date: 2013-06-06
forum: General Help
---

### Post by greatsirkain on 2013-06-06
How do I go about doing that?
 Kind of like the startup disk creator but I want to save the exact configuration & Ineed to save it to a usb stick not disk. I managed to do it on tails but it's got me a little befuddled in Ubuntu

---

### Post by TNFrank on 2013-06-06
I wonder if you could just backup the current image of your Op System to a USB and go from there? This is a good question, can't wait for an answer.

---

### Post by ahallubuntu on 2013-06-06
~

---

### Post by greatsirkain on 2013-06-06
thats an idea, if I make an ISO of the machine then I can make it bootable with unetbootin
found this:
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
off to get the Ubuntu customization kit

Edit: looking into the LVM too, looks interesting, thanks

---

### Post by Rebelli0us on 2013-06-06
You can boot a desktop CD and use gparted to copy your partition to USB using copy/paste.  But it might be easier to just install to USB and then copy over whatever you need.

---

### Post by C.S.Cameron on 2013-06-06
You might checkout Remastersys or it's fork OS4

[http://www.remastersys.com/](http://www.remastersys.com/)

[http://www.os4online.com/p/downloads-site-links.html](http://www.os4online.com/p/downloads-site-links.html)

---

### Post by greatsirkain on 2013-06-07
had a look, the remastersys guy has quit leaving a lengthy rant and the guys that took over haven't posted anything in months except for a few kb of source code...too tired to be compiling stuff or messing with gpg encryption keys & missing 404 pages :P

---

### Post by HermanAB on 2013-06-07
A CD is not big enough. Look into remastersys.

---

### Post by C.S.Cameron on 2013-06-07
> **greatsirkain said:**
> had a look, the remastersys guy has quit leaving a lengthy rant ... :P

Sometimes geniuses are like that.
I think you can still download Remastersys though.

---

### Post by greatsirkain on 2013-06-09
yup there was a massive 'downloads' button like there is on most places you go to download stuff & I couldn't see it (hadn't slept)
I'll have a tinker today after I've finished dinner.
Thanks folks

---

### Post by C.S.Cameron on 2013-06-09
Another option is to make an image file, (.img) of your O/S and then writing it to the flash drive using dd or a gui like Image Writer.
Sudodus has been having some fun with this method:

[http://ubuntuforums.org/showthread.php?t=1958073&highlight=sudodus](http://ubuntuforums.org/showthread.php?t=1958073&highlight=sudodus)

---

