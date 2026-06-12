---
title: "Ubuntu will not boot from usb or dvd"
date: 2015-12-23
forum: General Help
---

### Post by dansar99 on 2015-12-23
Hi!...I have a 7yr old HP G60 235 DX laptop running Vista. The BIOS is a INSYDEH20. Trying to boot Ubuntu 14.04.3. When I go to Boot options it shows the DVD 1st and HD 2nd. USB does not show. I press enter on the highlight DVD option but it still boots to windows.  The boot order shows usb drive but will not show in options. DAN

---

### Post by Vladlenin5000 on 2015-12-23
The HP G60 235 _should_ boot from optical drives or USB flash drives.

Have you tested the installation/live media you're using somewhere else and confirmed it works?
Are you sure your optical drive is fine?
What method have you used for making the USB flash drive?

---

### Post by dansar99 on 2015-12-23
The usb drive with ubuntu boots fine in my HP Pavillion Slimline desktop.  Not sure about the DVD drive, It plays a  audio disc fine and it shows in the boot options. I used Utorrent and burned the disc on a newer Dell. I have 3 usb ports on the lap top and tried every one.  Dan

---

### Post by Vladlenin5000 on 2015-12-23
> **dansar99 said:**
> The usb drive with ubuntu boots fine in my HP Pavillion Slimline desktop.

The HP Pavillion Slimline is probably UEFI enabled; the HP G60 235DX definitely has the old BIOS.
Some tools like Rufus and a few others create different installation media for different hardware according to user's instructions. Types aren't interchangeable. That's why I asked about the method (software tool, options, etc.) you used to create the said USB...

> Not sure about the DVD drive, It plays a  audio disc fine and it shows  in the boot options.

CD and DVD use different lasers with different wavelengths. One working doesn't mean the other is fine. Can you read your Ubuntu DVD in Windows? And...

> I used Utorrent and burned the disc on a newer  Dell.
Considering you used torrents the ISO file integrity is (almost) guaranteed so there's one less item to worry about. Now, how exactly have you burned it? ISO files aren't to be burned as is... Have you tried to read that DVD after burning? If so, what were its contents? If it's a single file - the ISO you download - then you did it wrong.

---

### Post by dansar99 on 2015-12-23
I burned the ISO image like I've always did with success. I believe my DVD drive is messed up. Windows cant read the disc. So, I guess with the bios not recognizing my usb stick as a boot option I'm screwed unless I replace DVD drive. Thanks for your help.  Dan

---

### Post by Vladlenin5000 on 2015-12-23
Is the USB flash drive readable in Windows (in the same machine)? If not then obviously you also have a problem with the USB ports.

---

### Post by dansar99 on 2015-12-23
yes...windows does read the usb.   When I got "COMPUTER" F drive reads "Install Ubuntu".

---

### Post by Vladlenin5000 on 2015-12-23
Then I suggest you use Rufus in Windows to create it and/or use a different drive altogether because some computers are picky about what flash drive they allow booting from.

---

### Post by dansar99 on 2015-12-24
Thank you!!!  I had a HP flash dr. and used Rufus. Amazingly the usb boot appeared in Boot Options and was able to try Ubuntu.  Thank you again...DAN

---

### Post by Vladlenin5000 on 2015-12-24
Great news :-)

Now you can use the thread tools to mark it as solved.

---

