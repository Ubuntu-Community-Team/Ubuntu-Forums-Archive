---
title: "Keyboard and touchpad freeze in Asus 1201HA i8042: Can't reactivate Aux port"
date: 2014-04-08
forum: General Help
---

### Post by leonardo8 on 2014-04-08
[SIZE=2][FONT=arial]Hello, first of all, I was not an user of Ubuntu, I decided to install **Ubuntu 12.04** a few days ago and after solving the audio problem
(the audio was playing fast, a theme of 3 minutes finished in 1). For this I used:
egedit and opened the file /etc/pulse/default.pa and I added in the line 'load-module module-udev-detect'
"tsched=0". So it seemed like this: " load-module module-udev-detect tsched=0". (As this: [https://wiki.debian.org/DebianEeePC/Model/1101HA](https://wiki.debian.org/DebianEeePC/Model/1101HA))
I reboot and the error was gone.
One day after the touchpad stop working, hours after the keyboard neither, but
the keyboard worked sometimes (I reboot 10 times, 1 works).
It doesn't work in session mode and even in recovery mode.
I am using right now with a virtual keyboard and an USB mouse.
I have this error until the session screen:
"i8042: Can't reactivate AUX port"
I tryied "**xinput list**" and I got this:

"*Virtual core pointer                       id=2    [master pointer  (3)]*[/FONT][/SIZE][SIZE=2][FONT=arial]*&#9116;   &#8627; Virtual core XTEST pointer                 id=4    [slave  pointer  (2)] *[/FONT][/SIZE]
[SIZE=2][FONT=arial]*&#9116;   &#8627; Microsoft  Microsoft BasicOptical Mouse v2.0     id=11    [slave  pointer  (2)] *[/FONT][/SIZE]
[SIZE=2][FONT=arial]*&#9123; Virtual core keyboard                      id=3    [master keyboard (2)] *[/FONT][/SIZE]
[SIZE=2][FONT=arial]*    &#8627; Virtual core XTEST keyboard                id=5    [slave  keyboard (3)] *[/FONT][/SIZE]
[SIZE=2][FONT=arial]*    &#8627; Video Bus                                  id=6    [slave  keyboard (3)] *[/FONT][/SIZE]
[SIZE=2][FONT=arial]*    &#8627; Power Button                               id=7    [slave  keyboard (3)] *[/FONT][/SIZE]
[SIZE=2][FONT=arial]*    &#8627; Sleep Button                               id=8    [slave  keyboard (3)] *[/FONT][/SIZE]
[SIZE=2][FONT=arial]*    &#8627; USB2.0 UVC VGA WebCam                      id=9    [slave  keyboard (3)] *[/FONT][/SIZE]
[SIZE=2][FONT=arial]*    &#8627; Eee PC WMI hotkeys                         id=10    [slave  keyboard (3)] * "

I did too the code "**dmesg | grep i8042**":
 
"*[    0.000000] Kernel command line:BOOT_IMAGE=/boot/vmlinuz-3.11.0-19-genericroot=UUID=580b72cf-ffea-4866-b8d4-c7bdfe238709 ro i8042.nomux=1i8042.reset quiet splash vt.handoff=7*[/FONT][/SIZE]
[SIZE=2][FONT=arial]*[    1.390763] i8042: PNP: PS/2Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12 *[/FONT][/SIZE]
[SIZE=2][FONT=arial]*[    1.405137] serio: i8042 KBD port at0x60,0x64 irq 1 *[/FONT][/SIZE]
[SIZE=2][FONT=arial]*[    1.405173] serio: i8042 AUX port at0x60,0x64 irq 12 *[/FONT][/SIZE]
[SIZE=2][FONT=arial]*[    2.633234] i8042: Can't write CTRwhile closing KBD port *[/FONT][/SIZE]
[SIZE=2][FONT=arial]*[    3.147949] i8042: Can't reactivateKBD port *[/FONT][/SIZE]
[SIZE=2][FONT=arial]*[    4.691804] i8042: Can't write CTRwhile closing AUX port *[/FONT][/SIZE]
[SIZE=2][FONT=arial]*[    5.206266] i8042: Can't reactivateAUX port *[/FONT][/SIZE]
[SIZE=2][FONT=arial]*[   14.563860] i8042: Can't write CTRwhile closing AUX port *[/FONT][/SIZE]
[SIZE=2][FONT=arial]*[   15.078688] i8042: Can't reactivateAUX port * " 

That's all I got, keyboard still not working and touchpad neither.
And before I forgot in Details (Configuration) In Graphics it says Unknown and standard.
Thanks a lot.[/FONT][/SIZE]

---

