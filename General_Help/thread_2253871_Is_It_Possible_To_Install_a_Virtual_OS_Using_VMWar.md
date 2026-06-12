---
title: "Is It Possible To Install a Virtual OS Using VMWare On A WD My Passport"
date: 2014-11-23
forum: General Help
---

### Post by khan3 on 2014-11-23
Hi,

I am thinking of buying a WD My Passport. To install my existing virtual os (ubuntu) onto it.

[http://www.amazon.co.uk/gp/product/B00CSH19PI/ref=ox_sc_act_title_1?ie=UTF8&psc=1&smid=A3P5ROKL5A1OLE](http://www.amazon.co.uk/gp/product/B00CSH19PI/ref=ox_sc_act_title_1?ie=UTF8&psc=1&smid=A3P5ROKL5A1OLE)

1. Is it possible for me to have my virtual os installed on this hard drive? 

2. Do i need to do anything to the hard drive before it can work?

3. There should not be problems dual booting using this? host (windows).

---

### Post by nerdtron on 2014-11-23
You want the whole Ubuntu operating system installed on the external drive?

It sure is possible.
1. Create an bootable live ubuntu USB 
2. Disconnect internal hard drives on the computer (just to make sure nothing else gets wipe out).
3. Boot the computer from USB and plug the external western digital drive.
4. Install Ubuntu as usual since the only drive present is the western digital my passport drive.

Once done, you can boot ubuntu on any computer booting from USB. And you won't have to touch any windows system if you do this type of installation since all files/configs are on the external drive. It is independent on any other OS installed on the computer.

---

### Post by khan3 on 2014-11-23
I'm not asking how to do it, im asking if its possible. As i noticed else where WD is not good when it comes to linux and others have had problems. So i just wanted definitive answer as to whether someone has got ubuntu working on a WD My Passport

---

### Post by phidia on 2014-11-23
What specifically have you read about western digital and linux? They buy their hardware from pretty much the same place everyone else does so the fact that it has WD branded on it makes little difference-Unless you are trying to keep the my passport software intact that is. Have you considered just running linux from an external thumb drive? Info on mounting any external drive can be found [here]("https://help.ubuntu.com/community/Mount/USB")
and to use an external to boot from this [how-to]("http://askubuntu.com/questions/446682/how-to-install-ubuntu-on-portable-external-hard-drive?rq=1") should suffice. Because most newer computer are using UEFI that more than the external drive type is likely the snag for some trying to install that way. I would very much recommend reading and understanding how to boot from legacy mode and learning more about [UEFI booting]("http://askubuntu.com/questions/78582/what-is-uefi-and-secure-boot-how-do-they-affect-ubuntu").

---

### Post by cprofitt on 2014-11-23
Based on your original post I am uncertain if you are dual booting or Ubuntu a virtual machine.

In either scenario a WD Passport drive should work, but in the case of a dual boot your computer (laptop or desktop) would need to support booting to USB (most do). You are using USB 3.0, but there will still some performance impact with the OS booting from the external drive will be slightly slower.

---

### Post by Mike_Walsh on 2014-11-23
> **khan3 said:**
>  As i noticed else where WD is not good when it comes to linux and others have had problems. 

Hallo, khan3.

I really don't understand why there SHOULD be a bias against Western Digital drives! I have an elderly Caviar 'Black' series, which until recently has had up to 4 different OSs on it; and I have an external 500 GB Seagate, which currently has six...

I confess, I've not heard that the WD 'My Passport' has had any particular issues when it comes to Linux. The WD is a hard drive; Linux is an OS.....the two were designed to work together. Like Stilton cheese & port...

BTW; I also run 3 or 4 distros from flash drives, too.

Regards,

Mike.

---

### Post by QIII on 2014-11-23
The problem with the Passport might end up being the firmware - it's not a bare drive, but resides in a firmware driven enclosure.

Bare WD drives work fine.  I have several.

The Passport has that extra layer and that it what sometimes does not work with Linux.

---

### Post by khan3 on 2014-11-24
> **QIII said:**
> The problem with the Passport might end up being the firmware - it's not a bare drive, but resides in a firmware driven enclosure.

Bare WD drives work fine.  I have several.

The Passport has that extra layer and that it what sometimes does not work with Linux.

Extra layer? Not sure what you mean by that, is this something i could not use/uninstall and i would be fine?

---

