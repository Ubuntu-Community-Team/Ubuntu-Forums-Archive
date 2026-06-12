---
title: "Problem installing Ubuntu"
date: 2013-01-20
forum: General Help
---

### Post by thefox93 on 2013-01-20
Hey all.

I'm a complete newbie when it comes to ubuntu.

I have been using the wubi and testing it but now I want to make the move to ubuntu only rather than windows 7.

I burned the .iso file to a disc, and when i try and boot it to install, I get the error message 'No Emulation System Type 00'

Does anybody know what this is, or how I can fix?

Will I need to remove the windows OS off the system first?

Thanks in advance

---

### Post by circa on 2013-01-20
I think that's a windows partition error. Try to change the boot order in your bios to read your CD first.

---

### Post by thefox93 on 2013-01-20
Just tried that, no success.

Still getting the same error message.

I'm really confused as to what it could be.

---

### Post by archery on 2013-01-20
1) Are you happy with the iso, have you used md5checksum to check the data integrity?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2) Did you burn the disk as data rather than an image i.e bootable?

Alternatively, use a USB pen to boot Ubuntu from, it'll be quicker.

In answer to your question, the Ubuntu installer will delete the Win 7 partition and automatically partition the hard drive (if that's what you want), you'll be presented with the options once you've booted successfully.

Hope this helps.

---

### Post by thefox93 on 2013-01-20
Checked the md5sum and they match up.

Disc is definitely burnt as an image, but I'm going to redownload and burn the download to a new disc.

I do have a USB Pen, but I think it's only 1gb

---

### Post by archery on 2013-01-20
> **thefox93 said:**
> Checked the md5sum and they match up.

Disc is definitely burnt as an image, but I'm going to redownload and burn the download to a new disc.

I do have a USB Pen, but I think it's only 1gb

1) What flavour of Ubuntu are you trying to install? 

2)Are you using the 32 bit or 64 bit version, if it's the latter make sure your CPU supports 64 bit instruction sets. 

3) Try booting the disc in another computer, if you have one. 

4) Having had boot problems with a couple of old laptops, a BIOS update sometimes did the trick. Take the necessary precautions i.e. make sure it's the right version and your laptop is plugged in. Only do this having made sure you've researched the steps and your confident in proceeding.

---

### Post by Wolfgange on 2013-01-20
> **jjmorgs1 said:**
> 1) What flavour of Ubuntu are you trying to install? 

2)Are you using the 32 bit or 64 bit version, if it's the latter make sure your CPU supports 64 bit instruction sets. 

3) Try booting the disc in another computer, if you have one. 

4) Having had boot problems with a couple of old laptops, a BIOS update sometimes did the trick. Take the necessary precautions i.e. make sure it's the right version and your laptop is plugged in. Only do this having made sure you've researched the steps and your confident in proceeding.
Yeah, I would check wheather you have the 64 bit or the 32 bit version and see which one you're system can handel. Is it a new computer?

---

### Post by thefox93 on 2013-01-21
The laptop is pretty old, I've had it since around 2006, and obviously with windows I'm experiencing some major performance issues atm.

I've downloaded the 32-bit version, as my windows is 32-bit as well.

Given up trying to boot from CD now, I think this laptop is just a piece of trash.

Borrowed a USB drive from my mate and hopefully the boot process will work.

About to attempt it now, so will keep you posted

---

### Post by archery on 2013-01-21
> **thefox93 said:**
> The laptop is pretty old, I've had it since around 2006, and obviously with windows I'm experiencing some major performance issues atm.

I've downloaded the 32-bit version, as my windows is 32-bit as well.

Given up trying to boot from CD now, I think this laptop is just a piece of trash.

Borrowed a USB drive from my mate and hopefully the boot process will work.

About to attempt it now, so will keep you posted

Did you check to see if there is a BIOS update available on the manufacturers website? I'd still be tempted to do that while you've got your Windows partition; typically the BIOS update tool will be a Windows executable. 

Also, if your using old hardware you may want to consider Lubuntu or Xubuntu. I can highly recommend the former. Both are official Ubuntu derivatives.

---

### Post by archery on 2013-01-21
Re the laptop being a piece of trash, I've given plenty of laptops older than yours a new lease of life, just requires tailoring your linux distro and packages to your hardware e.g Lubuntu/Xubuntu.

---

