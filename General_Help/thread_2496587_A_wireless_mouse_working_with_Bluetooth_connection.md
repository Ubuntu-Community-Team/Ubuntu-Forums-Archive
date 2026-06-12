---
title: "A wireless mouse working with Bluetooth connection, but not working with 2.4G connect"
date: 2024-04-04
forum: General Help
---

### Post by dcpetit on 2024-04-04
I got a new mouse and have been trying to get it to work in the *2.4G connection mode* (and it does not). The mouse works fine with Bluetooth, and it works in both modes when I use it with a Windows (10) machine that has a "mouhid.sys" driver file. **Any help or advice?** If it helps, I'm using Ubuntu 23.10 and the command lsusb gives:
[FONT=courier new]
 ...
Bus 001 Device 011: ID 3151:3020 YICHIP Wireless Device
...[/FONT]
 This vanishes when I turn the mouse off or pull the USB Receiver out of the computer, so I assume it's the wireless mouse.

 It's this mouse: [https://www.amazon.com/Wireless-Bluetooth-Mouse-Rechargeable-Bluetooth5-2/dp/B0BPCW5CS6?th=1]("https://rads.stackoverflow.com/amzn/click/com/B0BPCW5CS6")

---

### Post by him610 on 2024-04-06
@dcpetit, I queried the internet, > what is frequency of bluetooth 
Answer:
> Bluetooth uses short-wavelength UHF radio waves with a frequency of around 2,400,000,000 to 2,485,000,000Hz, which is 2.4 to 2.485GHz. Bluetooth operates at frequencies between 2.402 and 2.480 GHz, or 2.400 and 2.4835 GHz, including guard bands 2 MHz wide at the bottom end and 3.5 MHz wide at the top. This is in the globally unlicensed (but not unregulated) industrial, scientific and medical (ISM) 2.4 GHz short-range radio frequency band.
If you are able to connect your bluetooth devices, you utilizing the 2.4G RF band.

---

### Post by dcpetit on 2024-04-06
I think the 2.4G mode and bluetooth mode on this mouse are different. The 5th picture on the Amazon link shows the two different modes (and it the description is says, " Dual-Mode Mouse(Wireless USB 2.4G+Bluetooth5.2/3.0) "), and shows the range of the bluetooth that this mouse uses. Moreover, on the bottom of the mouse there is a switch which toggles between 2.4G mode, off (mode), and bluetooth mode. The mouse is only working when it's set on bluetooth and connected that way. Thanks for your help! I appreciate your investigations to get this working  :o

---

### Post by him610 on 2024-04-06
Did you also read this in the description....
> Bluetooth Mouse Mode Can Connect One Device Through BT5.2/3.0 and Wireless Mouse Mode Another Device Through a 2.4G USB Receiver....Note:The USB Receiver is Stored Inside The Back of The Mouse
That USB Receiver needs to be plugged into a USB port on your computer.

---

### Post by dcpetit on 2024-04-07
Yeah, I've plugged it in. And Ubuntu seems to recognize it as the list of recognized USBs has "[FONT=courier new]Bus 001 Device 011: ID 3151:3020 YICHIP Wireless Device[/FONT]", which goes away when I pull the USB receiver out. So the issue seems to be at the last possible step as the receiver is in the computer, the mouse is on and the red light at the bottom of the mouse is working great, the computer recognizes the mouse via USB, but the cursor doesn't move when I move the mouse... Thanks in advance!  :-)

---

### Post by glorious-fish on 2024-07-02
I have the same problem with the mouse that can work using Bluetooth or 2.4Ghz receiver and that self-reports as "YICHIP Wireless Device". If I try to use the receiver sometimes my Linux operating system does not recognize it. Usually it helps to disable mouse, pull receiver out, plug it back in and enable mouse again.

In the system journal there are following errors:
> 
[FONT=monospace][COLOR=#000000]Jul 02 07:25:18 laptop-dell kernel: [/COLOR][COLOR=#ff5454]**usbhid 1-2:1.1: can't add hid device: -110**[/COLOR][COLOR=#000000] [/COLOR]
Jul 02 07:25:18 laptop-dell kernel: [COLOR=#ff5454]**usbhid 1-2:1.1: probe with driver usbhid failed with error -110**[/COLOR][COLOR=#000000][/COLOR][/FONT]


---

### Post by agalardo on 2024-08-09
[SIZE=2][/SIZE][SIZE=3]Yesterday I connected the A4Tech fstyler fb10c mouse to Ubuntu 22.04 and Windows 11 after it lost its binding to the black and blue A4Tech dongle RN-30M. They lost each other because the mouse's battery ran out and it was left on for a very long time.
I tied them together according to the instructions for the orange dongle RN-20M.

This is an excursion into my problem. You have the same problem. Your dongle and mouse are not tied to each other. Ubuntu detects device ID 3151:3020 YICHIP Wireless Device, which means the mouse driver is correct.

I haven't used a mouse like yours. But the algorithm for binding a mouse to a dongle is the same for almost all manufacturers. Find instructions for linking your mouse to the dongle.
Dongle - 2.4Hz USB radio adapter.


[FONT=inherit][/FONT][FONT=inherit]Instructions for binding A4Tech mice to dongle RN-20M RN-30M. [https://www.a4tech.com/rn-20m/orange/](https://www.a4tech.com/rn-20m/orange/)[/FONT][/SIZE]

---

### Post by agalardo on 2024-08-09
[SIZE=3]Glorious-fish try these commands (first the system will be made ready for the changes, then the driver for hid will be reinstalled):[/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3]sudo apt update[/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3]sudo apt upgrade[/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3]sudo modprobe -r usbhid; sudo modprobe usbhid[/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3]Then reboot. [/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3]If reinstalling the driver does not help, then run the following commands:[/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3]sudo apt update[/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3]sudo apt upgrade[/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3]sudo ubuntu-drivers autoinstall[/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3]sudo apt update[/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3]sudo apt upgrade[/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3]I hope this helps you. Good luck![/SIZE]

---

