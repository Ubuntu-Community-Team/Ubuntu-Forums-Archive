---
title: "Can Instal Ubuntu from ISO without internet connection?"
date: 2018-02-24
forum: General Help
---

### Post by nexus77 on 2018-02-24
I am hoping to install Ubuntu to replace Windows 10.
I am currently downloading the Ubuntu ISO file  ( 3 hours to go).
I hope to install Ubuntu to overwrite Windows.
Can I do this *without* being connected to the internet?
My reason is that Windows is always trying to update my computer, but my connection is VERY slow.
With Ubuntu installing and Windows updates coming down, it will never complete.
Any help will be much appreciated.
Mike

---

### Post by QIII on 2018-02-24
Hello!

Depending on where you are, there may be a LUG (Linux User Group) nearby that would be more than happy to burn a DVD for you.

You needn't worry about what Windows is doing while you try to install Ubuntu -- it won't be running at all.  So it won't be consuming your bandwidth.

---

### Post by ubname on 2018-02-24
To answer your question, ***yes*** you do not need an Internet connection to install Ubuntu.
I also advise you to try the live session before removing win if you have only 1 PC, also consider to try it in a virtual machine to verify if it fits your needs and familiarize with it before you do "the jump" :)
In my opinion Ubuntu is overall a more user respectful (and friendly) OS than win but a rushed decision may give you a bad first impression.

---

### Post by nexus77 on 2018-02-24
Many thanks QIII.
I am installing to a netbook (no DVD), so I will persevere  with the USB.

---

### Post by nexus77 on 2018-02-24
Thanks for your input ubname.
I have 2 other computers running Windows, but my little netbook chokes on all the Windows updates.
My aim is to try Ubuntu on the netbook.

---

### Post by nexus77 on 2018-02-24
Sorry - I'm back again. I'm a complete amateur at this.
I'm trying to to install Ubuntu to my netbook.
I have the Ubuntu iso file on an 8GB USB drive, plugged in to my netbook.
I opened Rufus (which is on my C drive on the netbook) and went right through to "write in ISO image mode". At this point, I get "Error - access to device is denied".
Can anyone help me to move forward?
Many thanks

---

### Post by nexus77 on 2018-02-25
Back yet again :(
Well - I've managed to write the ISO file to the USB using Rufus, and in turn I installed it on my 'C' drive - well, I 'thought' I did.
When I open my computer now, I appear to have a full working version of Ubuntu - provided I have the USB drive attached and I select 'try Ubuntu without installing'
(if I don't, I get  'No Bootable Device'
But on the opening desktop, I see  'Examples'  and 'Install Ubuntu' - I thought I HAD installed it.
Do I now have to 'Install' it all again?
Any help will be much appreciated.
Mike

---

### Post by nexus77 on 2018-02-25
Just to clarify my earlier post, I have tried modifying the boot order (press F2 on starting) to ensure that it reads the first option (hard disc C), but to no avail.
Regards
Mike

---

### Post by ubname on 2018-02-25
> **nexus77 said:**
> Sorry - I'm back again. I'm a complete amateur at this.
I'm trying to to install Ubuntu to my netbook.
I have the Ubuntu iso file on an 8GB USB drive, plugged in to my netbook.
I opened Rufus (which is on my C drive on the netbook) and went right through to "write in ISO image mode". At this point, I get "Error - access to device is denied".
Can anyone help me to move forward?
Many thanks

You probably "flashed" you netbook drive instead of the usb, what you see when you boot is the live ubuntu session, you need to manage to flash the USB drive using rufus,
then boot off the USB and then install on the netbook; another thing you must be aware of is your cpu model, is it 32 or 64 bit? you must download the right ubuntu version.

---

### Post by Impavidus on 2018-02-25
> **nexus77 said:**
> 
I have the Ubuntu iso file on an 8GB USB drive, plugged in to my netbook.
I opened Rufus (which is on my C drive on the netbook) and went right through to "write in ISO image mode". At this point, I get "Error - access to device is denied".When your .iso file is stored on a usb drive, you can't use Rufus to write it to that same usb drive. The file would be overwritten by itself.

> **nexus77 said:**
> Back yet again :(
Well - I've managed to write the ISO file to the USB using Rufus, and in turn I installed it on my 'C' drive - well, I 'thought' I did.
When I open my computer now, I appear to have a full working version of Ubuntu - provided I have the USB drive attached and I select 'try Ubuntu without installing'
(if I don't, I get  'No Bootable Device'
But on the opening desktop, I see  'Examples'  and 'Install Ubuntu' - I thought I HAD installed it.
Do I now have to 'Install' it all again?
Any help will be much appreciated.
Mike
Not sure what happened... What did you do exactly? You're definitely running a live session. If it only works from the usb drive, that suggests that the usb drive is your live disk. And it seems there's nothing now on the internal hard drive.

BTW, now that Windows is gone, there's no C drive. C drive is Windows-speak. No Windows, no C drive.

---

### Post by nexus77 on 2018-02-25
OK - now I'm confused.  But many thanks for all your help to date.
If I insert the USB stick and turn the machine on, I get a B & W screen  GNU GRUB, from which I can choose to "try Ubuntu without installing". This appears to give me a full working version.
On the 'desktop' I have an icon "install Ubuntu".  If I run this, it tells me "this computer currently has Ubuntu 16.04.3 running on it.
My netbook is an Acer Aspire E11.  With the USB stick removed, I get "No Bootable Device"
Pressing F12 on boot, I have NO options to choose from.
Pressing F2 on boot, I have ensured that the HDD is at the top.
Any help will be greatly appreciated.  Have I got Ubuntu installed on the hard disc? or is it all on the USB?  How can I check?
Regards
Mike

---

### Post by Impavidus on 2018-02-26
OK, it seems Ubuntu is at least partially installed on the hard drive, but not bootable. Try [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). I normally recommend to only create a BootInfo summary so we can see what's going on, but as nothing valuable is on your hard drive, you could just as well run the recommended repair right away. If that doesn't fix it, seeing the link to the summay will help us.

---

### Post by nexus77 on 2018-02-26
Hello Impavidas.
Thank you - I have have downloaded and used Boot-Repair  - what a magic program!  - I ran the recommended repair and got a guy jumping for joy.
However, sadly for me - no joy.  With the Ubuntu iso disc plugged in, I still get GNU GRUB  with the options Try Ubuntu, Install Ubuntu etc.
Without the Ubuntu disc plugged in I get  'No bootable device'.
Sadly, I think the problem lies with my Acer Aspire E11 netbook.  I have checked and 'played with' the various boot options, but - no joy.
I think Ubuntu IS installed on the hard drive, but it won't boot.
Regards
Mike

---

### Post by kerry_s on 2018-02-26
you have secure boot disabled?

---

### Post by nexus77 on 2018-02-27
Hi Kerry
Yes, I have secure boot disabled.
(I've tried both ways - neither works)
Many thanks for your input.
Mike

---

### Post by kerry_s on 2018-02-27
have you tried installing again or just the 1 time?

---

### Post by nexus77 on 2018-02-28
Hi Kerry
I reinstalled a second time  (from the ubuntu 'desktop').
But no change.
Maybe I should  're-burn' to USB stick and try again?  what do you think?
It's working great as it is - but only with the USB stick plugged in.
Regards
Mike

---

