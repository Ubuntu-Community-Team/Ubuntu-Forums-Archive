---
title: "Epson Workforce 645: Evince and Double Sided Printing"
date: 2014-01-01
forum: General Help
---

### Post by piotrl on 2014-01-01
I am using Ubuntu 13.10.  I have an Epson Workforce 645 printer that is connected via a wireless connection.  I'm trying to print double-sided, but the option is grayed out.  On my other laptop it works fine.  I checked that the cups options in Synaptic are the same.  I downloaded the same driver file that I downloaded for the other computer, but double sided printing can't be accessed.  I saw other threads about borderless, paper option, but none of that works to enable double sided printing.  
I am not a programmer so if possible please dumb it down for me in the explanations if you have ideas on what I can try.
I really appreciate the help.

---

### Post by dave2001 on 2014-02-23
Hi Piotri, I have the exact same printer and version of 'buntu (although I am running KDE instead of Unity).

I just installed this printer recently, and am having some trouble with it. It works fine when connected via USB, but I can't get it to connect wirelessly. I've even tried to manually connect using the IPP method. What method of installation did you use to get yours connected wirelessly? Did you use the drivers from the Epson website, or some others? Which order did you install the various packages?

I'm sorry to say I can't offer much advice about the double sided printing, I haven't tried it yet, but I'll mess with mine later and see if I can get that working.

---

### Post by piotrl on 2014-02-23
I had to install the driver from the Epson website.  The driver is called:
epson-inkjet-printer-201106w_1.0.1-1lsb3.2_amd64.deb

I might have had issues though as my friend helped me fix some things with it.  I can't remember if it was because it wasn't working or because of a different issue.  See if this driver will work, but if not I don't know what the issue is.  If it doesn't work let me know and I can ask my friend to see if he knows what he did.

---

### Post by dave2001 on 2014-02-24
Thanks piotrl,
I did actually have all the drivers installed from the Epson site. I figured out my problem though! There was an old job in the print queue(from a windows computer on the same wireless network), that was messed up somehow and not printing. Once I canceled out the old job from Windows that was plugging things up, My linux laptop is printing wirelessly wonderfully.

I messed around a bit trying to figure out how to do double-sided printing. When I go to print something in Libreoffice or Kwrite, after choosing "print" , and then clicking the "properties" button brings up a menu where you can find "duplexing."

It has three options: off, back-front binding, or left-right binding. I believe this ***should*** be the way to do double sided printing, however, changing the setting seems to have no effect. The pages just print normally, one-sided, one after another. Sounds a bit different from your problem since my options aren't greyed out.. but we get the same effect: no double-sided printing. Maybe someone who knows more will chime in.

---

