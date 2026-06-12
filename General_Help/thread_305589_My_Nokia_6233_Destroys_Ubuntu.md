---
title: "My Nokia 6233 Destroys Ubuntu"
date: 2006-11-23
forum: General Help
---

### Post by olieviya on 2006-11-23
I have a Nokia 6233 which connects to my lappy (m5550 alienware) via a usb port. My ubuntu installation can locate the phone when connected but if it is removed it will completely freeze the system and no mouse moving or keyboard pressing does any good the only option is a manual turn-off.

Any ideas?

---

### Post by x64Jimbo on 2006-11-23
Can you have the system remove the device via software first, like "eject this device" style? It's typically not a good idea to just unplug peripherals without having the OS disconnect from them first.

---

### Post by olieviya on 2006-11-23
> **x64Jimbo said:**
> Can you have the system remove the device via software first, like "eject this device" style? It's typically not a good idea to just unplug peripherals without having the OS disconnect from them first.

Yeah, so it's basically just that I HAVE to do that, then?


EDIT: It still froze :(

---

### Post by x64Jimbo on 2006-11-23
Do you have an idea about what device name it's getting from the system? Live /dev/nokia or something like that? If so, you might need to manually unmount it, or possibly manually stop the process that is used to interface with the device.

---

### Post by olieviya on 2006-11-24
> **x64Jimbo said:**
> Do you have an idea about what device name it's getting from the system? Live /dev/nokia or something like that? If so, you might need to manually unmount it, or possibly manually stop the process that is used to interface with the device.

Do you mean where it is mounted? it's mounted in /media/THE NAME I GAVE TO MY MICRO SD CARD

Or have I misunderstood?

---

### Post by x64Jimbo on 2006-11-24
I mean the device name. It starts with /dev. 
Is there a kernel module that is used to talk to the device? I think the problem you're seeing is that the kernel module is crashing the kernel when it is disconnected. I think you need to unmount the device then rmmod the module responsible for managing that device.

---

### Post by olieviya on 2006-11-24
> **x64Jimbo said:**
> I mean the device name. It starts with /dev. 
Is there a kernel module that is used to talk to the device? I think the problem you're seeing is that the kernel module is crashing the kernel when it is disconnected. I think you need to unmount the device then rmmod the module responsible for managing that device.

Sorry, you've lost me, can you explain it in an idiot-proof way?
please :)

---

### Post by x64Jimbo on 2006-11-25
Hm. A kernel module is usually a device driver that connects into the linux kernel so that the device may interact with the system. For instance, Atheros chipset wireless cards interface with the kernel through the ath_pci module. To get these cards to work, you have to activate the module in the kernel with "modprobe ath_pci" and remove it with "rmmod ath_pci"
I believe you may have a similar situation. Many times these days the system automatically detects the device and starts the appropriate module for you. I suspect that the kernel module that controls your Nokia's interface with the kernel is malfunctioning at the point of disconnect. If you can find the name of the module that manages your Nokia and rmmod it before unplugging the unit, you will probably stop seeing the freezes.

---

### Post by olieviya on 2006-11-25
> **x64Jimbo said:**
> Hm. A kernel module is usually a device driver that connects into the linux kernel so that the device may interact with the system. For instance, Atheros chipset wireless cards interface with the kernel through the ath_pci module. To get these cards to work, you have to activate the module in the kernel with "modprobe ath_pci" and remove it with "rmmod ath_pci"
I believe you may have a similar situation. Many times these days the system automatically detects the device and starts the appropriate module for you. I suspect that the kernel module that controls your Nokia's interface with the kernel is malfunctioning at the point of disconnect. If you can find the name of the module that manages your Nokia and rmmod it before unplugging the unit, you will probably stop seeing the freezes.

Oh, wow, that was a good explanation. So, how can I find it's name? :)

---

### Post by olieviya on 2006-11-26
Any ideas? Please? 

:(

---

### Post by x64Jimbo on 2006-11-29
Unfortunately I am neither on your system nor an owner of one of those phones. I don't really have the first clue about what the module might be called. You might look for a support group for that model somewhere. Wish I could have been more help.

---

### Post by drivel on 2006-11-29
Have you install the driver for your cellphone?

---

### Post by x64Jimbo on 2006-11-29
> **drivel said:**
> Have you install the driver for your cellphone?
I believe that has already been established since the device is working until it is plugged in.

---

### Post by olieviya on 2006-11-29
> **drivel said:**
> Have you install the driver for your cellphone?

No, I haven't, where would I be able to find one?


> **x64Jimbo said:**
> I believe that has already been established since the device is working until it is plugged in.

Btw, the phone does not work even when plugged in--if i try to transfer something from the phone onto the pc it'll crash and not transfer the whole thing. Then the whole pc will freeze...

---

### Post by olieviya on 2006-12-04
anybody???

---

### Post by batty_whol on 2006-12-05
On how to identify which kernel module your phone is using.

By using the command 'lsmod' before you plug it in. Take a careful note of what modules are loaded, better yet output to a file:

```
lsmod > /tmp/before.connection
```

Then connect your phone and run:

```
lsmod > /tmp/after.connection
```

Then compare the two files:

```
diff /tmp/before.connection /tmp/after.connection
```

This will display the difference between the two files, and thereby show which modules have been loaded by connecting your phone.

You will then be able to proceed with the 'rmmod' of those modules before disconnecting.

Another thought is to look at the output from 'dmesg' just before and after you connect the phone and see what it says. This may provide some useful info.

Post back with what you find.

Batty:}

---

### Post by olieviya on 2006-12-06
> **batty_whol said:**
> On how to identify which kernel module your phone is using.

By using the command 'lsmod' before you plug it in. Take a careful note of what modules are loaded, better yet output to a file:

```
lsmod > /tmp/before.connection
```

Then connect your phone and run:

```
lsmod > /tmp/after.connection
```

Then compare the two files:

```
diff /tmp/before.connection /tmp/after.connection
```

This will display the difference between the two files, and thereby show which modules have been loaded by connecting your phone.

You will then be able to proceed with the 'rmmod' of those modules before disconnecting.

Another thought is to look at the output from 'dmesg' just before and after you connect the phone and see what it says. This may provide some useful info.

Post back with what you find.

Batty:}

Seeing as I'm completely stuck outside ubuntu from the time being :( [http://ubuntuforums.org/showthread.php?t=303592](http://ubuntuforums.org/showthread.php?t=303592)

I will do it/try it when I can manage to figure out how to get back into ubuntu :(

---

### Post by batty_whol on 2006-12-06
Sorry to hear about your issues. I see Shin is looking after you. Good one!
Best of luck.

Batty:}

---

### Post by olieviya on 2006-12-07
trying it now, sorry for double post :P

---

### Post by olieviya on 2006-12-07
> **batty_whol said:**
> On how to identify which kernel module your phone is using.

By using the command 'lsmod' before you plug it in. Take a careful note of what modules are loaded, better yet output to a file:

```
lsmod > /tmp/before.connection
```

Then connect your phone and run:

```
lsmod > /tmp/after.connection
```

Then compare the two files:

```
diff /tmp/before.connection /tmp/after.connection
```

This will display the difference between the two files, and thereby show which modules have been loaded by connecting your phone.

You will then be able to proceed with the 'rmmod' of those modules before disconnecting.

Another thought is to look at the output from 'dmesg' just before and after you connect the phone and see what it says. This may provide some useful info.

Post back with what you find.

Batty:}

olivia@olivia-laptop:~$ lsmod > /tmp/before.connection
olivia@olivia-laptop:~$ lsmod > /tmp/after.connection
olivia@olivia-laptop:~$ diff /tmp/before.connection /tmp/after.connection
2,3c2,3
< nls_cp437               6912  1 
< vfat                   14720  1 
---
> nls_cp437               6912  2 
> vfat                   14720  2 
48c48
< nls_utf8                3200  2 
---
> nls_utf8                3200  3 
62c62
< usb_storage            75072  1 
---
> usb_storage            75072  2 
91c91
< sd_mod                 22656  6 
---
> sd_mod                 22656  8 
olivia@olivia-laptop:~$

---

### Post by MellonCollie on 2007-01-14
I'm another 6233 user with this problem. :( I'll throw some things into this thread in case someone more knowledgeable can work out what's going on.

```
jmc@omfg:~$ diff /tmp/before.connection /tmp/after.connection
1a2,5
> sg                     37404  0 
> sd_mod                 22656  1 
> usb_storage            75072  1 
> libusual               17040  1 usb_storage
27,28c31,32
< nls_cp437               6912  1 
< vfat                   14720  1 
---
> nls_cp437               6912  2 
> vfat                   14720  2 
30c34
< nls_utf8                3200  3 
---
> nls_utf8                3200  4 
82c86
< usbcore               134912  4 usbhid,ehci_hcd,ohci_hcd
---
> usbcore               134912  6 usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
91c95
< scsi_mod              144648  2 sbp2,libata
---
> scsi_mod              144648  5 sg,sd_mod,usb_storage,sbp2,libata

```


I don't know if the entries from my system log will help, but I'll post them anyway. (The following covers connect/disconnect/freeze)

```
Jan 14 15:29:11 omfg -- MARK --
Jan 14 15:34:01 omfg kernel: [17182285.012000] usb 1-1: new full speed USB device using ohci_hcd and address 4
Jan 14 15:34:01 omfg kernel: [17182285.236000] usb 1-1: configuration #1 chosen from 1 choice
Jan 14 15:34:01 omfg kernel: [17182285.372000] usbcore: registered new driver libusual
Jan 14 15:34:01 omfg kernel: [17182285.416000] Initializing USB Mass Storage driver...
Jan 14 15:34:01 omfg kernel: [17182285.416000] scsi0 : SCSI emulation for USB Mass Storage devices
Jan 14 15:34:01 omfg kernel: [17182285.416000] usbcore: registered new driver usb-storage
Jan 14 15:34:01 omfg kernel: [17182285.416000] USB Mass Storage support registered.
Jan 14 15:34:06 omfg kernel: [17182290.424000]   Vendor: Nokia     Model: Nokia 6233        Rev: 0000
Jan 14 15:34:06 omfg kernel: [17182290.424000]   Type:   Direct-Access                      ANSI SCSI revision: 04
Jan 14 15:34:06 omfg kernel: [17182290.500000] SCSI device sda: 122625 512-byte hdwr sectors (63 MB)
Jan 14 15:34:06 omfg kernel: [17182290.516000] sda: test WP failed, assume Write Enabled
Jan 14 15:34:06 omfg kernel: [17182290.536000] SCSI device sda: 122625 512-byte hdwr sectors (63 MB)
Jan 14 15:34:06 omfg kernel: [17182290.552000] sda: test WP failed, assume Write Enabled
Jan 14 15:34:07 omfg kernel: [17182290.552000]  sda:
Jan 14 15:34:07 omfg kernel: [17182290.684000] sd 0:0:0:0: Attached scsi removable disk sda
Jan 14 15:34:07 omfg kernel: [17182290.696000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan 14 15:34:07 omfg kernel: [17182290.932000] sda: Current: sense key: No Sense
Jan 14 15:34:07 omfg kernel: [17182290.932000]     Additional sense: No additional sense information
Jan 14 15:35:31 omfg kernel: [17182375.428000] usb 1-1: USB disconnect, address 4
Jan 14 15:35:32 omfg kernel: [17182376.236000] usb 1-1: new full speed USB device using ohci_hcd and address 5
Jan 14 15:35:32 omfg kernel: [17182376.452000] usb 1-1: configuration #1 chosen from 1 choice
Jan 14 15:35:33 omfg kernel: [17182376.684000] cdc_acm 1-1:1.1: ttyACM0: USB ACM device
Jan 14 15:35:33 omfg kernel: [17182376.692000] usbcore: registered new driver cdc_acm
Jan 14 15:35:33 omfg kernel: [17182376.692000] drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
Jan 14 15:35:33 omfg kernel: [17182377.224000] usbcore: registered new driver cdc_ether
Jan 14 15:35:33 omfg kernel: [17182377.444000] usb%%d: unregister 'rndis_host' usb-0000:00:02.0-1, RNDIS device
Jan 14 15:35:33 omfg kernel: [17182377.452000] rndis_host: probe of 1-1:1.9 failed with error -110
Jan 14 15:35:33 omfg kernel: [17182377.452000] usbcore: registered new driver rndis_host
Jan 14 15:35:51 omfg kernel: [17182394.580000] usb 1-1: USB disconnect, address 5
Jan 14 15:35:51 omfg kernel: [17182395.388000] usb 1-1: new full speed USB device using ohci_hcd and address 6
Jan 14 15:35:52 omfg kernel: [17182395.604000] usb 1-1: configuration #1 chosen from 1 choice
Jan 14 15:35:52 omfg kernel: [17182395.608000] scsi1 : SCSI emulation for USB Mass Storage devices
Jan 14 15:36:54 omfg syslogd 1.4.1#18ubuntu6: restart.
```

---

### Post by olieviya on 2007-01-14
> **MellonCollie said:**
> I'm another 6233 user with this problem. :( I'll throw some things into this thread in case someone more knowledgeable can work out what's going on.

```
jmc@omfg:~$ diff /tmp/before.connection /tmp/after.connection
1a2,5
> sg                     37404  0 
> sd_mod                 22656  1 
> usb_storage            75072  1 
> libusual               17040  1 usb_storage
27,28c31,32
< nls_cp437               6912  1 
< vfat                   14720  1 
---
> nls_cp437               6912  2 
> vfat                   14720  2 
30c34
< nls_utf8                3200  3 
---
> nls_utf8                3200  4 
82c86
< usbcore               134912  4 usbhid,ehci_hcd,ohci_hcd
---
> usbcore               134912  6 usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
91c95
< scsi_mod              144648  2 sbp2,libata
---
> scsi_mod              144648  5 sg,sd_mod,usb_storage,sbp2,libata

```


I don't know if the entries from my system log will help, but I'll post them anyway. (The following covers connect/disconnect/freeze)

```
Jan 14 15:29:11 omfg -- MARK --
Jan 14 15:34:01 omfg kernel: [17182285.012000] usb 1-1: new full speed USB device using ohci_hcd and address 4
Jan 14 15:34:01 omfg kernel: [17182285.236000] usb 1-1: configuration #1 chosen from 1 choice
Jan 14 15:34:01 omfg kernel: [17182285.372000] usbcore: registered new driver libusual
Jan 14 15:34:01 omfg kernel: [17182285.416000] Initializing USB Mass Storage driver...
Jan 14 15:34:01 omfg kernel: [17182285.416000] scsi0 : SCSI emulation for USB Mass Storage devices
Jan 14 15:34:01 omfg kernel: [17182285.416000] usbcore: registered new driver usb-storage
Jan 14 15:34:01 omfg kernel: [17182285.416000] USB Mass Storage support registered.
Jan 14 15:34:06 omfg kernel: [17182290.424000]   Vendor: Nokia     Model: Nokia 6233        Rev: 0000
Jan 14 15:34:06 omfg kernel: [17182290.424000]   Type:   Direct-Access                      ANSI SCSI revision: 04
Jan 14 15:34:06 omfg kernel: [17182290.500000] SCSI device sda: 122625 512-byte hdwr sectors (63 MB)
Jan 14 15:34:06 omfg kernel: [17182290.516000] sda: test WP failed, assume Write Enabled
Jan 14 15:34:06 omfg kernel: [17182290.536000] SCSI device sda: 122625 512-byte hdwr sectors (63 MB)
Jan 14 15:34:06 omfg kernel: [17182290.552000] sda: test WP failed, assume Write Enabled
Jan 14 15:34:07 omfg kernel: [17182290.552000]  sda:
Jan 14 15:34:07 omfg kernel: [17182290.684000] sd 0:0:0:0: Attached scsi removable disk sda
Jan 14 15:34:07 omfg kernel: [17182290.696000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan 14 15:34:07 omfg kernel: [17182290.932000] sda: Current: sense key: No Sense
Jan 14 15:34:07 omfg kernel: [17182290.932000]     Additional sense: No additional sense information
Jan 14 15:35:31 omfg kernel: [17182375.428000] usb 1-1: USB disconnect, address 4
Jan 14 15:35:32 omfg kernel: [17182376.236000] usb 1-1: new full speed USB device using ohci_hcd and address 5
Jan 14 15:35:32 omfg kernel: [17182376.452000] usb 1-1: configuration #1 chosen from 1 choice
Jan 14 15:35:33 omfg kernel: [17182376.684000] cdc_acm 1-1:1.1: ttyACM0: USB ACM device
Jan 14 15:35:33 omfg kernel: [17182376.692000] usbcore: registered new driver cdc_acm
Jan 14 15:35:33 omfg kernel: [17182376.692000] drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
Jan 14 15:35:33 omfg kernel: [17182377.224000] usbcore: registered new driver cdc_ether
Jan 14 15:35:33 omfg kernel: [17182377.444000] usb%%d: unregister 'rndis_host' usb-0000:00:02.0-1, RNDIS device
Jan 14 15:35:33 omfg kernel: [17182377.452000] rndis_host: probe of 1-1:1.9 failed with error -110
Jan 14 15:35:33 omfg kernel: [17182377.452000] usbcore: registered new driver rndis_host
Jan 14 15:35:51 omfg kernel: [17182394.580000] usb 1-1: USB disconnect, address 5
Jan 14 15:35:51 omfg kernel: [17182395.388000] usb 1-1: new full speed USB device using ohci_hcd and address 6
Jan 14 15:35:52 omfg kernel: [17182395.604000] usb 1-1: configuration #1 chosen from 1 choice
Jan 14 15:35:52 omfg kernel: [17182395.608000] scsi1 : SCSI emulation for USB Mass Storage devices
Jan 14 15:36:54 omfg syslogd 1.4.1#18ubuntu6: restart.
```

Nothing has been done as far as I know :(

---

### Post by kbozen on 2007-03-01
I have the same problem with my Nokia 6233

Under Dapper the USB data Transfer Mode worked without Problem, 
Now with Edgy I have exactly the same behavior as olieviya.
After I try to copy a file from my Nokia Micro-SD Card to my Ubuntu Home Ubuntu freeze.

---

### Post by olieviya on 2007-03-06
> **kbozen said:**
> I have the same problem with my Nokia 6233

Under Dapper the USB data Transfer Mode worked without Problem, 
Now with Edgy I have exactly the same behavior as olieviya.
After I try to copy a file from my Nokia Micro-SD Card to my Ubuntu Home Ubuntu freeze.

Have you managed to find out anything?

---

### Post by rrwo on 2007-04-04
I have the same problem with Edgy. I plug my Nokia 6233 in on USB, and I can browse the card, but as soon as I try to read any files, the system crashes completely. All I can do is forcibly reboot using the power button.

---

### Post by rrwo on 2007-04-04
I've reported a bug for Ubuntu [102965]("https://bugs.launchpad.net/ubuntu/+bug/102965").

---

### Post by rrwo on 2007-04-19
Interesting. I found that sometimes when I plug the phone into a Mac with OS/X, it crashes Finder too.

It has an older firmware, and Nokia suggested upgrading it.  (Since I don't have a Windows machine, then suggested going to a mobile phone shop.)

---

### Post by rrwo on 2007-04-21
This problem appears to be fixed after upgrading to Feisty.

(The upgrade has caused me various other unrelated problems though...)

---

### Post by olieviya on 2007-08-10
> **rrwo said:**
> This problem appears to be fixed after upgrading to Feisty.

(The upgrade has caused me various other unrelated problems though...)

Mine doesn't crash any more but it doesn't transfer any data and it randomly disconnects itself!

---

### Post by b0uncyfr0 on 2007-08-24
Same here. My 6233 works fine fine but when i start transferrings naything it eventually drops and reports STALLED. I thought this problem would have been fixed in feisty, but apparently not.

---

### Post by olieviya on 2007-09-14
> **b0uncyfr0 said:**
> Same here. My 6233 works fine fine but when i start transferrings naything it eventually drops and reports STALLED. I thought this problem would have been fixed in feisty, but apparently not.

Have you actually managed to transfer something or does it just crash when you do?

---

### Post by olieviya on 2007-09-18
*bump*

My output (after a 5 min delay is):

```
olivia@Lappy:/media/My Stuff$ cp * ~
cp: reading `Crappy(255).jpg': Input/output error
cp: cannot stat `Crappy(256).jpg': No such file or directory
cp: cannot stat `Crappy(257).jpg': No such file or directory
cp: cannot stat `Crappy(258).jpg': No such file or directory
cp: cannot stat `Crappy(260).jpg': No such file or directory
cp: cannot stat `Crappy(261).jpg': No such file or directory
cp: cannot stat `Crappy(262).jpg': No such file or directory
cp: cannot stat `Crappy(264).jpg': No such file or directory
cp: cannot stat `Crappy(266).jpg': No such file or directory
cp: cannot stat `Crappy(267).jpg': No such file or directory
cp: cannot stat `Crappy(268).jpg': No such file or directory
cp: cannot stat `Crappy(269).jpg': No such file or directory
cp: cannot stat `Crappy(270).jpg': No such file or directory
cp: cannot stat `Crappy(271).jpg': No such file or directory
cp: cannot stat `Crappy(272).jpg': No such file or directory
cp: cannot stat `Crappy(274).jpg': No such file or directory
cp: cannot stat `Crappy(276).jpg': No such file or directory
cp: cannot stat `Crappy(277)000.jpg': No such file or directory
cp: cannot stat `Crappy(277).jpg': No such file or directory
cp: cannot stat `Crappy(279).jpg': No such file or directory
cp: cannot stat `Crappy(280).jpg': No such file or directory
cp: cannot stat `Crappy(281).jpg': No such file or directory
cp: cannot stat `Crappy(282).jpg': No such file or directory
cp: cannot stat `Crappy(283).jpg': No such file or directory
cp: cannot stat `Crappy(284).jpg': No such file or directory
cp: cannot stat `Crappy(285).jpg': No such file or directory
cp: cannot stat `Flip-Flops.mp3': No such file or directory
cp: cannot stat `Images': No such file or directory
cp: cannot stat `More crap(023).3gp': No such file or directory
cp: cannot stat `More crap(026).3gp': No such file or directory
cp: cannot stat `More crap(027).3gp': No such file or directory
cp: cannot stat `Music': No such file or directory
cp: cannot stat `Themes': No such file or directory
cp: cannot stat `Video Clips': No such file or directory

```

I get an "unsafe devide removal" warning and then it's unmounted all by itself. (works fine in m$):confused::confused:

---

### Post by olieviya on 2007-09-21
B U M P


Anybody know of any progress?

:(

---

### Post by olieviya on 2007-10-18
> **b0uncyfr0 said:**
> Same here. My 6233 works fine fine but when i start transferrings naything it eventually drops and reports STALLED. I thought this problem would have been fixed in feisty, but apparently not.

Tried it in 7.10 anybody? Will try it now..... seems to NOT be working any more than before, if anybody does get any more progress please do tell. :mad:

---

