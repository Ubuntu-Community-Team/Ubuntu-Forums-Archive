---
title: "Help with ir-keytable recognizing events in trusty"
date: 2014-06-18
forum: General Help
---

### Post by tstack77 on 2014-06-18
I am having problems getting ir-keytable to recognize any events. 

-Dongle shows red incomming light on remote presses, can confirm working with Windows7 xbmc setup with eventghost.
-Tested all usb ports. Read in previous posts that there can be issues with an usb3 port, dongle plugged into usb2 port.

```
$ uname -r
3.13.0-29-generic
```

```
$ dmesg
[    5.530777] Registered IR keymap rc-rc6-mce
[    5.530917] input: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/rc/rc0/input5
[    5.531006] rc0: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/rc/rc0
[    5.545653] IR NEC protocol handler initialized
[    5.555646] IR RC5(x) protocol handler initialized
[    5.560062] IR RC6 protocol handler initialized
[    5.569629] IR JVC protocol handler initialized
[    5.576739] IR Sony protocol handler initialized
[    5.584535] IR SANYO protocol handler initialized
[    5.722519] mceusb 3-2:1.0: Registered Philips eHome Infrared Transceiver with mce emulator interface version 1
[    5.722525] mceusb 3-2:1.0: 2 tx ports (0x0 cabled) and 2 rx sensors (0x0 active)
```

```
$ lsusb
Bus 003 Device 002: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver
```

```
$ sudo /etc/init.d/lirc stop
* Stopping remote control daemon(s): LIRC                               [ OK ] 
$ sudo ir-keytable -c
Old keytable cleared
$ sudo ir-keytable -t
Testing events. Please, press CTRL-C to abort.
```

Nothing happens when any buttons on the remote are tested here. In every tutorial I have found, this step has not been identified as a possible problem. What else can I test?

Thanks

---

### Post by tstack77 on 2014-06-19
After a few more hours of googling I have found a few threads mentioning usb problems with Asus h87 boards, and that I should update the BIOS, turn off WOL, and turn off UEFI boot. Did all those things but I am still unable to get any events recognized.

Does anyone have any solutions beyond returning the motherboard for a different brand?

Thanks again

---

### Post by tstack77 on 2014-06-20
To test the motherboard I installed [openelec]("http://openelec.tv/home/what-is-openelec") (a custom linux distro for xbmc) to a spare flash drive and the ir remote worked out of the box, events recognized in both ir-keytable and lirc. Unfortunately this seems to open up the problem to anything but the motherboard. 

Then, to rule out that I didn't spawn any odd gremlins within my original ubuntu install, I installed lubuntu minimal to a flash drive and only installed ir-keytable. And again, no ir-keytable events recognized when testing.

Are there any remote gurus in the forums here that can point me towards a possible solution/explanation/missing step? I am using the same MCE dongle I have had for years that always worked out of the box, but now won't in trusty x64 with a new socket 1150 h87 mobo and haswell i3. 

I am stumped :confused:

---

