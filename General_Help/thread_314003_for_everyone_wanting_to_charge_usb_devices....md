---
title: "for everyone wanting to charge usb devices..."
date: 2006-12-06
forum: General Help
---

### Post by aosmith on 2006-12-06
check out:

/sys/class/usb_device/usbdev*.*/device/bMaxPower

i would assume that usbdev*.* indicated which socket.

*i havent tested this but if someone knows this is a dumb thing to change then please speak up*

**edit: for some reason the file cant be edited even when logged in as root...help?**

---

### Post by wieman01 on 2006-12-06
While the computer is turned on or off?

---

### Post by aosmith on 2006-12-07
...on? i'm assuming i need to boot from another drive to edit it.  I don't think its possible to edit files with the computer off?

---

### Post by Rhubarb on 2006-12-07
You should be able to mount it with the live CD.
.. That way you can edit the file when the computer is "off".

---

### Post by wieman01 on 2006-12-07
I mean charging while the computer is on or off. I was referring to the title of your thread. My idea is to charge USB devices (mobile phone, etc.) while the computer is not running. 

Yes, booting from Live CD should resolve your problem. Do you know how to mount your harddisk & make the necessary changes?

---

### Post by Chinkostu on 2006-12-07
i dont know if its a motherboard error, but my usb ports still work after a shutdown if i plug stuff in.
anyway, if you edited that file, it would still be turned off during a halt.

---

### Post by wieman01 on 2006-12-07
> **Chinkostu said:**
> i dont know if its a motherboard error, but my usb ports still work after a shutdown if i plug stuff in.
anyway, if you edited that file, it would still be turned off during a halt.
I also thought this is controlled by the BIOS & I have definitely turned it on. But somehow it does not work anymore. Anyway, that should be discussed in another thread.

---

### Post by aosmith on 2006-12-08
I just changed from xp to ubuntu and the bios is unchanged (for the most part)... My thought is that its somethign system oriented...

in the device manager / usb hub interface / advanced / usb.is_self_powered (bool = true)
kinda sounds like it make be the problem... also 
/usb hub* / advanced / usb.max_power (int = 0)

---

### Post by njkrut on 2006-12-17
I am not sure if this will work for anyone else but I made a quick shell script.

powerBlackberry.sh
```

BLACKBERRY=`hal-find-by-property --key usb_device.product --string "Blackberry Handheld"`
BLACKBERRY_USB=`hal-find-by-property --key usb.product --string "USB Vendor Specific Interface" --key usb.vendor --string "Research In Motion, Ltd."`
hal-set-property --udi $BLACKBERRY --key usb_device.max_power --int 500
hal-set-property --udi $BLACKBERRY_USB --key usb.max_power --int 500

```

Maybe it works, maybe not but my blackberry is charging and is not saying anything about needing more power.  =)

Cheers!
  Nick

---

### Post by losttale on 2007-03-27
> **aosmith said:**
> check out:

/sys/class/usb_device/usbdev*.*/device/bMaxPower

i would assume that usbdev*.* indicated which socket.

*i havent tested this but if someone knows this is a dumb thing to change then please speak up*

**edit: for some reason the file cant be edited even when logged in as root...help?**

the internets almost failed me until I found your post aosmith.  However, I wish to fiddle with my USB port power for a wholly different purpose.

These cool compaq usb powered fans arrived from woot today ([http://www.woot.com/Blog/BlogEntry.aspx?BlogEntryId=2144)](http://www.woot.com/Blog/BlogEntry.aspx?BlogEntryId=2144)), and I'd like to write a script so that I can mess with the usb port voltage to adjust the fan speed.  Any thoughts on how to do this? (as well as any risks I might be taking?) :grin:

---

### Post by mcduck on 2007-03-27
> **losttale said:**
> the internets almost failed me until I found your post aosmith.  However, I wish to fiddle with my USB port power for a wholly different purpose.

These cool compaq usb powered fans arrived from woot today ([http://www.woot.com/Blog/BlogEntry.aspx?BlogEntryId=2144)](http://www.woot.com/Blog/BlogEntry.aspx?BlogEntryId=2144)), and I'd like to write a script so that I can mess with the usb port voltage to adjust the fan speed.  Any thoughts on how to do this? (as well as any risks I might be taking?) :grin:
The voltage is by standard always 5V, only thing that is allowed to change is the current, which is usually set to minimum and then raised in steps if the device in question is smart enough to ask your operating system to do it.

I would seriously recommend against changing that in any way. If you want to control the fan speed, you'd better build the control in the fan itself. That should be pretty simple thing to do anyway.

---

### Post by losttale on 2007-03-27
very well....   i just thought it would be neat to map current control to a couple function keys on my stinkpad ;)

---

### Post by shmengie on 2007-11-27
> **njkrut said:**
> I am not sure if this will work for anyone else but I made a quick shell script.

powerBlackberry.sh
```

BLACKBERRY=`hal-find-by-property --key usb_device.product --string "Blackberry Handheld"`
BLACKBERRY_USB=`hal-find-by-property --key usb.product --string "USB Vendor Specific Interface" --key usb.vendor --string "Research In Motion, Ltd."`
hal-set-property --udi $BLACKBERRY --key usb_device.max_power --int 500
hal-set-property --udi $BLACKBERRY_USB --key usb.max_power --int 500

```

Maybe it works, maybe not but my blackberry is charging and is not saying anything about needing more power.  =)

Cheers!
  Nick

so, i know this is an old post, but when i run this script, i get:```
libhal.c 1676 : invalid paramater. *key is NULL.
error: libhal_device_set_property: (null): (null)

libhal.c 1676 : invalid paramater. *key is NULL.
error: libhal_device_set_property: (null): (null)
my_name@my_name-linux:~/Desktop$
```

do i need to move this script elsewhere to run it? am i missing some libraries?

(quick background: i've kept my system dual-boot xp/ubuntu specifically for my blackberry. i do all my blackberry management in xp, as wine doesn't do blackberry. in xp, my device charges fine. but, when i connect my device in ubuntu for a quick file copy or such, i get the low power warning on my blackberry. just looking for an answer to that).

thx!

---

### Post by DoctorMO on 2007-11-27
you need to install bcharge from the barry project. I'm working on an easy install package for ubuntu.  are you willing to help us out shmengie; for testing and syncing support?

---

### Post by shmengie on 2007-11-27
> **DoctorMO said:**
> you need to install bcharge from the barry project. I'm working on an easy install package for ubuntu.  are you willing to help us out shmengie; for testing and syncing support?
absolutely. as long as you're cool with the fact that i'm a super-skilled windows guy, but a relatively green *nix guy. i learn quickly and follow directions well. :)

---

### Post by DoctorMO on 2007-11-28
OK, email me your reddyness so I can keep everyone in the same place; there are lots of other people who have blackberries and we should be able to work together to improve things.

---

