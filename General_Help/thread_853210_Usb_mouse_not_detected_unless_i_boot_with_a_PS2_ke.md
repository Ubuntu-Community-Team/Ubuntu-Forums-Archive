---
title: "Usb mouse not detected unless i boot with a PS/2 keyboard"
date: 2008-07-08
forum: General Help
---

### Post by castaneda on 2008-07-08
I recently changed from XP to Hardy, and it's working great on my system. In celebration of my newfound open source liberty I decided to treat myself with a new USB keyboard to replace my antique PS/2 keyboard from the last century.

This is what happens:

*I boot with USB keyboard and USB mouse: Mouse not responding

*I boot with PS/2 keyboard and USB mouse: Both working. 
 After boot I add the USB keyboard and remove the PS/2 keyboard, and both USB mouse and  USB keyboard is working fine...

This workaround is kind of stupid since it requires me to keep two keyboards around my computer, and my old keyboard looks a bit like a health hazard with 10 years of grime encrusted.

I'm fairly new to Linux, and would appreciate some help with where to start looking for solutions to this.

---

### Post by Erlander on 2008-07-09
On boot up go into bios (probably by pressing the Delete key) and enable USB Keyboard and USB Mouse.

Rob

---

### Post by lisati on 2008-07-09
As previously mentioned, check your BIOS settings.... my desktop has a setting that has "auto detect" as one of its BIOS options for PS/2 mice.

I use a usb mouse & a usb keyboard... When I first stared using Ubuntu I noticed that they'd stop working after a while.... there are workarounds. Feel free to ask if you run into the same problem.

---

### Post by Slow Foxtrot on 2008-11-05
I have discovered that unless I boot with ANY usb mouse plugged in, they are not detected after boot.  I also found that by simply running "lsusb" the module would restart scanning the ports and it works fine after that.  Here are some outputs:

brock@SlowFoxtrot:~$ lsmod | grep hcd
ohci_hcd               28956  0 
ehci_hcd               41996  0 
usbcore               170288  5 usbhid,ndiswrapper,ohci_hcd,ehci_hcd
brock@SlowFoxtrot:~$ lsmod | grep usb
usbhid                 35680  0 
hid                    44992  1 usbhid
usbcore               170288  5 usbhid,ndiswrapper,ohci_hcd,ehci_hcd
brock@SlowFoxtrot:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
brock@SlowFoxtrot:~$ 


So I simply added a command in my session to run "lsusb" at startup and now I can plug in whenever I want.

---

