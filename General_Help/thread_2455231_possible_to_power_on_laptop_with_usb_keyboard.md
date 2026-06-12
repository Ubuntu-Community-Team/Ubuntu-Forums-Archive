---
title: "possible to power on laptop with usb keyboard?"
date: 2020-12-15
forum: General Help
---

### Post by rawimage8 on 2020-12-15
hi everyone, 

Ubuntu (Budgie) Ubuntu 20.04 here - on an Asus Zenbook UX301 with a (perhaps weird) question: is there any chance I might be able to power on my Asus...by clicking on an external USB keyboard key as opposed to pressing the laptop's power button - after shutdown? Long story short, the Asus is permanently connected to a large PC monitor on the other side of the room, etc. I've found a couple of tutorials here and there - except that the solution suggested involves modifying the "Power Management” or “ACPI Management"inthe BIOS settings. I can't find this option in the Asus's BIOS...

any idea? thanx :)

---

### Post by #&amp;thj^% on 2020-12-15
> **rawimage8 said:**
> hi everyone, 

Ubuntu (Budgie) Ubuntu 20.04 here - on an Asus Zenbook UX301 with a (perhaps weird) question: is there any chance I might be able to power on my Asus...by clicking on an external USB keyboard key as opposed to pressing the laptop's power button - after shutdown? Long story short, the Asus is permanently connected to a large PC monitor on the other side of the room, etc. I've found a couple of tutorials here and there - except that the solution suggested involves modifying the "Power Management” or “ACPI Management"inthe BIOS settings. I can't find this option in the Asus's BIOS...

any idea? thanx :)

Yes..First of all&#65292;the keyboard must support power on by keyboard, it must be the PS/2 keyboard!!
Then you should have that option in your Bios.
I think it's under "Advanced">>"APM Config">> then under "Power On By PS/Keyboaard"

---

### Post by rawimage8 on 2020-12-15
no, unfortunately I don't have a PS/2 keyboard - only a USB keyboard. I didn't know this kind of keyboard even existed :) well, I guess walking up to the laptop is the only solution for the time being :) btw, I checked the BIOS once more and that option you mention is definitely not there...unless it's somehow separate from the BIOS menu I access by repeatedly clicking on "esc" as I power up the PC. I tried "F2" but nothing happens. I'm asking, just in case I might decide to get the PS/2 keyboard. Thanks for your help!

---

### Post by #&amp;thj^% on 2020-12-15
It's been such a long time since I used ASUS anything but see if pushing F7 gets you to the advanced area.
Memo&#65306;&#65288;1&#65289;ASUS BIOS can't support power on by USB keyboard&#65281;

             &#65288;2&#65289;If not connect PS2 keyboard, and see if the option of power on by keyboard now show when ready to do so.

---

### Post by CatKiller on 2020-12-15
As an alternative approach, which might also not be available if the UEFI is limited: you could try enabling Wake-on-LAN. You send a magic packet over the network from another computer, or a phone, which the machine is listening for as a signal to turn itself on.

---

### Post by rawimage8 on 2020-12-16
1fallen: thanks. A couple of sites suggest hitting "F8" and/or "delete" to access BIOS / UEFI ("F7" unfortunately doesn't work): "F8" doesn't work either and "delete" is just an alternative to "esc" > it leads to BIOS.

CatKiller: I like the wake-on-lan idea, except that it doesn't seem to be possible to access the relevant settings (see above). 

Could you please take a look at the two screenshots ("esc/delete" > "boot device" > "BIOS") and tell me if there's something I'm missing/could be done, perhaps? I tried every single option in "BIOS" but couldn't find any menu that deals with power management or keyboards. On the other hand, for some reason, "boot device" shows a list of three items (no idea why, I only have one OS installed on this PC, Ubuntu 20) that includes..."UEFI OS". Is it relevant at all? If I choose this option, it just boots Ubuntu (like the other two). 

thanks!

---

### Post by CatKiller on 2020-12-16
> **rawimage8 said:**
> CatKiller: I like the wake-on-lan idea, except that it doesn't seem to be possible to access the relevant settings (see above). 

The thing that you're calling the BIOS is the UEFI. The (now fairly old) UEFI does the same sorts of functions as the (much, much) older BIOS, and can pretend to be one for backwards-compatibility reasons through something called the Compatibility Support Module.

I can't see your picture on my phone, but I did say that it was possible you wouldn't have a setting for it; laptop options are often more limited than their desktop counterparts.

---

### Post by #&amp;thj^% on 2020-12-16
> **rawimage8 said:**
> 1fallen: thanks. A couple of sites suggest hitting "F8" and/or "delete" to access BIOS / UEFI ("F7" unfortunately doesn't work): "F8" doesn't work either and "delete" is just an alternative to "esc" > it leads to BIOS.

CatKiller: I like the wake-on-lan idea, except that it doesn't seem to be possible to access the relevant settings (see above). 

Could you please take a look at the two screenshots ("esc/delete" > "boot device" > "BIOS") and tell me if there's something I'm missing/could be done, perhaps? I tried every single option in "BIOS" but couldn't find any menu that deals with power management or keyboards. On the other hand, for some reason, "boot device" shows a list of three items (no idea why, I only have one OS installed on this PC, Ubuntu 20) that includes..."UEFI OS". Is it relevant at all? If I choose this option, it just boots Ubuntu (like the other two). 

thanks!

CatKiller is right about limitation, Laptops vs Desktop Bios.
I did see the Advanced tab in your bios, Anything there?

---

### Post by rawimage8 on 2020-12-16
no, 1fallen, it doesn't seem like there's anything interesting there - please see screenshot. 

I guess my laptop doesn't have what it's needed. I suppose there wouldn't be some Ubuntu power management software / script that overrides the laptop's own bios and let me do what I have in mind - well, provided that I got the right keyboard?

---

### Post by #&amp;thj^% on 2020-12-16
Yah I kind of thought that might be the case. :(
> [QUOTE]I suppose there wouldn't be some Ubuntu power management software / script that overrides the laptop's own bios and let me do what I have in mind[/QUOTE]
That would be like the old saying too many cooks spoil the broth. ;) And the fact you might not even have the PS2 slot on your laptop, Do You?
CatKillers idea on wake on lan might be the only solution/option you have.

---

### Post by rawimage8 on 2020-12-16
gotcha :) and it's true, no PS2 port to be seen, you're right. Well, at least I've learnt something and that's good. Thanks for your help!!!

---

