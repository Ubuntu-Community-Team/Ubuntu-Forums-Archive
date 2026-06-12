---
title: "USB error?"
date: 2008-04-29
forum: General Help
---

### Post by Gauvenator on 2008-04-29
```
usb1-8: device descriptor read/64, error -110
```

Anyone know why I'm getting this?  It happens 3 or 4 times when the initrd is starting during bootup in Ubuntu 8.04 and Fedora 8.

After it I get an error about usb1-8 not accepting addresses 6 and 7.

Any ideas why this is happening?  It wasn't occurring yesterday...

---

### Post by mc4man on 2008-04-29
You might get some further or useful info from some of your logs. Maybe try shutting down, uplugging any usb devices, _shut down power supply_, wait a bit and restart

---

### Post by Gauvenator on 2008-04-29
> **mc4man said:**
> You might get some further or useful info from some of your logs. Maybe try shutting down, uplugging any usb devices, _shut down power supply_, wait a bit and restart

Worked like a charm lol.

I powered it down, including the psu, jiggled/replugged some cables, and now the error is gone.  It was so weird...it happened consistently every time I rebooted too.  Cold boot did the trick! :D

Thanks!

---

### Post by jimoz on 2008-04-30
wish that would work for me! im trying to install ubuntu on a friends pc. initially on gg 7.10, just tried hh 8.04 today. USB doesnt work- outputs "read/64 error 110" messages no matter what device is plugged in, sometimes "device not accepting address" messages. Have tried fiddling with the ultra-DMA settings as suggested from other post, have also tried turning ehci_hcd and ohci_hcd on and off also as suggested on another post. Have tried all available usb ports. lsusb will sometimes identify the component, but cannot use the device. Other times lsusb will hang and produce no output. Computer uses a USB 1.1 controller. Currently running dual boot with XP, all devices work without issues on windows.

The main device i'm trying to get working here is a usb wifi card (Belkin f5d9050v3000). All usb devices work fine on my laptop (ubuntu hh) with no extra issues.

Im starting to think the ubuntu isnt playing nicely with the usb controller (or vice versa)... would appreciate any other ideas or suggestions before replacing the controller.

Any ideas?

---

### Post by mc4man on 2008-04-30
@Gauvenator
generally situation is caused by the over current protection being triggered on the controller circuit, I believe the limit on one root hub is 500mA
@jimoz - can you get any usb to work like keyboard, mouse, printer ?

---

### Post by Gauvenator on 2008-04-30
> **jimoz said:**
> wish that would work for me! im trying to install ubuntu on a friends pc. initially on gg 7.10, just tried hh 8.04 today. USB doesnt work- outputs "read/64 error 110" messages no matter what device is plugged in, sometimes "device not accepting address" messages. Have tried fiddling with the ultra-DMA settings as suggested from other post, have also tried turning ehci_hcd and ohci_hcd on and off also as suggested on another post. Have tried all available usb ports. lsusb will sometimes identify the component, but cannot use the device. Other times lsusb will hang and produce no output. Computer uses a USB 1.1 controller. Currently running dual boot with XP, all devices work without issues on windows.

The main device i'm trying to get working here is a usb wifi card (Belkin f5d9050v3000). All usb devices work fine on my laptop (ubuntu hh) with no extra issues.

Im starting to think the ubuntu isnt playing nicely with the usb controller (or vice versa)... would appreciate any other ideas or suggestions before replacing the controller.

Any ideas?

Perhaps your bios needs to be configured differently?

---

### Post by jimoz on 2008-05-01
Occasionally I can get a USB flash drive to work. Its only worked maybe once or twice, and even then I have to remove, reinsert, repeat, etc. Also tried a USB camera which has same issue. In any event I've only had one device plugged in at a time, and Ive tried all available ports.

Any idea what settings need to be changed in the BIOS? As everything works without issues in XP, I would assume the BIOS settings wouldnt be a problem...

---

### Post by Gauvenator on 2008-05-01
Try unplugging all your usb ports.  Disconnect all internal hubs, and all devices from your built in ports.  Then plug in hubs one at a time until you get the error.  Hopefully you will be able to narrow it down that way.

---

### Post by jimoz on 2008-05-05
I would try disassembling the USB hubs if it was my computer, but, since it isnt, that unfortunately is not an option. I'll try a few more things first and see what happens.

---

### Post by Gauvenator on 2008-05-05
> **jimoz said:**
> I would try disassembling the USB hubs if it was my computer, but, since it isnt, that unfortunately is not an option. I'll try a few more things first and see what happens.

can't you just unplug them temporarily?  No need to take them apart.

Write down where they went :D

---

