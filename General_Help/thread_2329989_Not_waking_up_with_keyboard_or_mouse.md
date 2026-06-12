---
title: "Not waking up with keyboard or mouse"
date: 2016-07-06
forum: General Help
---

### Post by Mopar1973Man on 2016-07-06
I'm trying to get my computer to wake up from suspend using my keyboard or mouse. I've been through the whole acpitool the USB ports are enabled but S4 mode which I think is my hang up and the ports are power down. How do I change to S3? The BIOS setting is disabled for S4 suspend. 
```

michael@michael:~$ acpitool -w
   Device    S-state      Status   Sysfs node
  ---------------------------------------
  1. SBAZ      S4    *disabled  pci:0000:00:14.2
  2. ECIR      S4    *disabled
  3. PS2K      S4    *disabled
  4. PS2M      S4    *disabled
  5. UAR1      S4    *disabled
  6. OHC1      S4    *enabled   pci:0000:00:12.0
  7. EHC1      S4    *enabled   pci:0000:00:12.2
  8. OHC2      S4    *enabled   pci:0000:00:13.0
  9. EHC2      S4    *enabled   pci:0000:00:13.2
  10. OHC3      S4    *disabled
  11. EHC3      S4    *disabled
  12. OHC4      S4    *disabled
  13. XHC0      S4    *enabled   pci:0000:00:10.0
  14. XHC1      S4    *enabled   pci:0000:00:10.1
  15. PE21      S4    *disabled
  16. PE22      S4    *disabled  pci:0000:00:15.2
  17. RLAN      S4    *enabled   pci:0000:03:00.0
  18. PE23      S4    *disabled
  19. PCE2      S4    *disabled
  20. PCE3      S4    *disabled
  21. PCE4      S4    *disabled
  22. PCE5      S4    *disabled
  23. PCE6      S4    *disabled
  24. PCE7      S4    *disabled
  25. PE20      S4    *disabled  pci:0000:00:15.0
  26. P0PC      S4    *disabled  pci:0000:00:14.4

```

---

### Post by Mopar1973Man on 2016-07-09
Anyone? I'm looking for a bit of support on how to handle this and stumped. Please???

---

### Post by egeezer on 2016-07-10
Have you got uswsusp installed and active?  That should let you log in with Enter.

---

### Post by Mopar1973Man on 2016-07-11
This isn't a laptop computer. This is a desktop computer. The keyboard and mouse are powering down for some reason during suspend. I assume it's because the USB are going into S4 suspend where it needs to be S3 to keep some power to the USB ports. So neither device will function once it goes into suspend mode. The only thing that will wake the computer is remote LAN wake up (magic packet) or pressing the power button. So how do I change the USB suspend mode from S4 to S3 so it will have power during suspend mode?

---

### Post by Mopar1973Man on 2016-07-16
Verified some information here... I've checked with my laptop and it got the USB ports set for S3 suspend mode. Now on the desktop it's set for S4 suspend for everything. Some how I've got to get it switched to S3 mode. I've been hunting all over the internet on methods of changing this and still not quite finding a solution. I'm sure there is a few knowledgeable minds here than can help...

---

### Post by QDR06VV9 on 2016-07-16
> **Mopar1973Man said:**
> Verified some information here... I've checked with my laptop and it got the USB ports set for S3 suspend mode. Now on the desktop it's set for S4 suspend for everything. Some how I've got to get it switched to S3 mode. I've been hunting all over the internet on methods of changing this and still not quite finding a solution. I'm sure there is a few knowledgeable minds here than can help...

@Mopar1973Man Try this
```
sudo powernap-action --disable usb_autosuspend
```
But if you don't have powernap installed you can also disable USB Auto Suspend
Just copy paste the following command in terminal and it will disable USB auto suspending.

 ```
   for i in /sys/bus/usb/devices/*/power/autosuspend;
    do echo 2 > $i;
    done
```

---

### Post by Mopar1973Man on 2016-07-16
Again back up one step this is not a laptop this is desktop computer. I only verified the differences between the laptop and desktop.

This computer does not have powernap installed.

After running your script in terminal... (No change)

```
root@michael:/home/michael# acpitool -w
   Device    S-state      Status   Sysfs node
  ---------------------------------------
  1. SBAZ      S4    *disabled  pci:0000:00:14.2
  2. ECIR      S4    *disabled
  3. PS2K      S4    *disabled
  4. PS2M      S4    *disabled
  5. UAR1      S4    *disabled
  6. OHC1      S4    *enabled   pci:0000:00:12.0
  7. EHC1      S4    *enabled   pci:0000:00:12.2
  8. OHC2      S4    *enabled   pci:0000:00:13.0
  9. EHC2      S4    *enabled   pci:0000:00:13.2
  10. OHC3      S4    *disabled
  11. EHC3      S4    *disabled
  12. OHC4      S4    *disabled
  13. XHC0      S4    *enabled   pci:0000:00:10.0
  14. XHC1      S4    *enabled   pci:0000:00:10.1
  15. PE21      S4    *disabled
  16. PE22      S4    *disabled  pci:0000:00:15.2
  17. RLAN      S4    *enabled   pci:0000:03:00.0
  18. PE23      S4    *disabled
  19. PCE2      S4    *disabled
  20. PCE3      S4    *disabled
  21. PCE4      S4    *disabled
  22. PCE5      S4    *disabled
  23. PCE6      S4    *disabled
  24. PCE7      S4    *disabled
  25. PE20      S4    *disabled  pci:0000:00:15.0
  26. P0PC      S4    *disabled  pci:0000:00:14.4
```

---

### Post by QDR06VV9 on 2016-07-16
Well that script works on my 2 systems??
And Yes I "KNEW" it was a desktop not a laptop.
So now that we are past that...You may have to use Grub to disable USB Auto Suspend.
Have a look here if you want to: [http://unix.stackexchange.com/questions/91027/how-to-disable-usb-autosuspend-on-kernel-3-7-10-or-above](http://unix.stackexchange.com/questions/91027/how-to-disable-usb-autosuspend-on-kernel-3-7-10-or-above)

---

### Post by Mopar1973Man on 2016-07-17
Sorry about that.. Just the suggestion of using laptop tools I though you confused desktop for laptop. (Passed...)

So now the content of my grub is...

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.autosuspend=-1"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

Then updated grub and rebooted... 

Still acpitool report S4 suspend for all USB port. Still that same as above.

Powertop still reports autosuspend of the USB ports.

```

   Good          Autosuspend for USB device OHCI PCI host controller [usb7]
   Good          Autosuspend for USB device xHCI Host Controller [usb1]
   Good          Autosuspend for USB device xHCI Host Controller [usb2]
   Good          Autosuspend for USB device xHCI Host Controller [usb3]
   Good          Autosuspend for USB device xHCI Host Controller [usb4]
   Good          Autosuspend for USB device EHCI Host Controller [usb5]
   Good          Autosuspend for USB device EHCI Host Controller [usb6]
   Good          Autosuspend for USB device OHCI PCI host controller [usb8]

```

Just for the sake of trying I went over to Asus web site and downloaded and flashed from BIOS version 12.04 to 18.01 still no change. During setup of the new BIOS I verified and made sure the suspend to S4 was disabled. 

Now here is a clue I tried force powertop setting for OFF on the usb port. The results was if the machine suspended it would for just a second or two and instantly wake back up from suspend.

---

### Post by QDR06VV9 on 2016-07-17
> **Mopar1973Man said:**
> Sorry about that.. Just the suggestion of using laptop tools I though you confused desktop for laptop. (Passed...)

So now the content of my grub is...

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.autosuspend=-1"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

Then updated grub and rebooted... 

Still acpitool report S4 suspend for all USB port. Still that same as above.

Powertop still reports autosuspend of the USB ports.

```

   Good          Autosuspend for USB device OHCI PCI host controller [usb7]
   Good          Autosuspend for USB device xHCI Host Controller [usb1]
   Good          Autosuspend for USB device xHCI Host Controller [usb2]
   Good          Autosuspend for USB device xHCI Host Controller [usb3]
   Good          Autosuspend for USB device xHCI Host Controller [usb4]
   Good          Autosuspend for USB device EHCI Host Controller [usb5]
   Good          Autosuspend for USB device EHCI Host Controller [usb6]
   Good          Autosuspend for USB device OHCI PCI host controller [usb8]

```

Just for the sake of trying I went over to Asus web site and downloaded and flashed from BIOS version 12.04 to 18.01 still no change. During setup of the new BIOS I verified and made sure the suspend to S4 was disabled. 

Now here is a clue I tried force powertop setting for OFF on the usb port. The results was if the machine suspended it would for just a second or two and instantly wake back up from suspend.

No Worries:D  The truth is I have been know to skim through posts and miss the mark completely.:(
I have not seen this being so stubborn before ?
And bear with me here you have run 'sudo update-grub'
And Yes I see that you have now so disregard.
Just running that script I had showed you earlier... and by the way that dose not remain persistent with reboots. (Just letting you know that is all)
Lets see if indeed grub is telling us the truth...what is the output of this:
```
cat /sys/module/usbcore/parameters/autosuspend
``` 
Mine shows this...and all is well with Suspend and Wake-ing
```
$ cat /sys/module/usbcore/parameters/autosuspend
2

```
EDIT: Is this happening with the normal timed suspend session or are you using the Keyboard Suspend button?

---

### Post by Mopar1973Man on 2016-07-17
Here you go...

```

michael@michael:~$ cat /sys/module/usbcore/parameters/autosuspend
-1

```

But you had me set -1 for the Grub?

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.autosuspend=-1"

```

So I'll try the 2 instead and see what happens...

---

### Post by Mopar1973Man on 2016-07-17
Ok tried setting of "2" in place and now it will sleep but not a S3 sleep, keyboard will wake the computer but remains in black screen state and unusable. I'm using the suspend command off the upper right of Ubuntu desktop.

Keyboard is a Microsoft Wired Keyboard 400.

---

### Post by QDR06VV9 on 2016-07-18
> **Mopar1973Man said:**
> Here you go...



_**But you had me set -1 for the Grub?**_


So I'll try the 2 instead and see what happens...

I do not recall having you set that to -1  it must have been from the link I had sent you.
I have a friend that has a USB Microsoft Keyboard and Mouse setup he has now told me he has a problem with suspend also...so he dose not allow suspending.(He just turns off the Monitor)
But I am going to borrow his keyboard and mouse to see what I can come up with a little later today.
I will report back here. Stay Tuned.:)
Ah this from Microsoft
>      [h=2]I cannot put my computer to sleep using the Sleep key.[/h]              The Sleep key puts the computer into power management mode  (such as standby, suspend, or hibernation) only if the computer supports  power management and has it enabled. If power management is not  enabled, this key will not work. It cannot be reassigned. For  information about Windows power management settings, see Windows Help.
     
         [h=3]I cannot wake up my computer after pressing the Sleep key.[/h]              You may be able to resume operation by trying one of the following:
 
[LIST]
[*]Press the Sleep key.
[*]Press a standard key on the keyboard.
[*]Move the mouse.
[*]Quickly press the power button on the computer.
[/LIST]
 If you cannot resume computer operation from any of these methods,  you may have encountered a system problem. For more information about  how your computer resumes operation, see the documentation that came  with your computer or contact the computer manufacturer.
 If you are using a Bluetooth® keyboard, the wireless transceiver  might not receive key commands during hibernation. You may be able to  resume from hibernation by pressing the power button on the computer.  For information about Windows power management settings, see Windows  Help.
     
 
I do remember when i was trouble shooting his machine once the below did snap it out of what you have also reported (unresponsive black screen)
Quickly press the power button on the computer.
One more question if you would has this hardware setup you have in place now, ever worked properly with suspend?

---

### Post by Mopar1973Man on 2016-07-18
Neither this motherboard nor the previous motherboard did. So I've changed motherboards changed keyboard/mice I was running a cordless Logictech. What's weird my Mom has the very same keyboard and mouse and suspend works perfect. 

Here is the setting on her machine.

```

michael@rosalie:~$ acpitool -w
   Device    S-state      Status   Sysfs node
  ---------------------------------------
  1. SBAZ      S4    *disabled  pci:0000:00:14.2
  2. ECIR      S4    *disabled
  3. PS2K      S4    *disabled
  4. PS2M      S4    *disabled
  5. UAR1      S4    *disabled  pnp:00:05
  6. OHC1      S4    *enabled   pci:0000:00:12.0
  7. EHC1      S4    *enabled   pci:0000:00:12.2
  8. OHC2      S4    *enabled   pci:0000:00:13.0
  9. EHC2      S4    *enabled   pci:0000:00:13.2
  10. OHC3      S4    *disabled
  11. EHC3      S4    *disabled
  12. OHC4      S4    *disabled
  13. XHC0      S4    *enabled   pci:0000:00:10.0
  14. XHC1      S4    *enabled   pci:0000:00:10.1
  15. PE21      S4    *disabled
  16. PE22      S4    *disabled  pci:0000:00:15.2
  17. RLAN      S4    *enabled   pci:0000:03:00.0
  18. PE23      S4    *disabled
  19. PB21      S4    *disabled
  20. PB22      S4    *disabled
  21. PB31      S4    *disabled
  22. PB32      S4    *disabled
  23. PB33      S4    *disabled
  24. PB34      S4    *disabled
  25. PE20      S4    *disabled  pci:0000:00:15.0
  26. P0PC      S4    *disabled  pci:0000:00:14.4
michael@rosalie:~$ 

``` 

As you see it the very same setting as well but her machine works fine. (Asus A88XM-E). Now you understand why I'm so stumped.

---

### Post by QDR06VV9 on 2016-07-18
As I have said Yes Strange indeed!:confused:
I am beginning to think that there is possibility of a problem with the first Keyboard (Microsoft)
My two systems I have been trying to help you with show:
```
Device    S-state      Status   Sysfs node
  ---------------------------------------
  1. PCE2      S4    *disabled  pci:0000:00:02.0
  2. PCE3      S4    *disabled
  3. PCE4      S4    *disabled  pci:0000:00:04.0
  4. PCE5      S4    *disabled
  5. PCE6      S4    *disabled  pci:0000:00:06.0
  6. PCE7      S4    *disabled  pci:0000:00:07.0
  7. PCE9      S4    *disabled  pci:0000:00:09.0
  8. PCEA      S4    *disabled
  9. PCEB      S4    *disabled
  10. PCEC      S4    *disabled
  11. SBAZ      S4    *disabled  pci:0000:00:14.2
  12. PS2K      S3    *enabled   pnp:00:04
  13. PS2M      S3    *disabled
  14. UAR1      S4    *disabled  pnp:00:05
  15. P0PC      S4    *disabled  pci:0000:00:14.4
  16. AC97      S4    *disabled
  17. MC97      S4    *disabled
  18. USB1      S4    *enabled   pci:0000:00:13.0
  19. USB2      S4    *enabled   pci:0000:00:13.1
  20. USB3      S4    *enabled   pci:0000:00:13.2
  21. USB4      S4    *enabled   pci:0000:00:13.3
  22. USB5      S4    *enabled   pci:0000:00:13.4
  23. EUSB      S4    *enabled   pci:0000:00:13.5
  24. PWRB      S3    *enabled   platform:PNP0C0C:0

inxi -M
Machine:   Mobo: ASUSTeK model: M3A32-MVP DELUXE v: Rev 1.xx
           Bios: American Megatrends v: 2104 date: 07/05/2010
```

And This one I am now Typing with HP Multimedia Keyboard
```
Device    S-state      Status   Sysfs node
  ---------------------------------------
  1. PCE2      S4    *disabled  pci:0000:00:02.0
  2. PCE3      S4    *disabled
  3. PCE4      S4    *disabled
  4. PCE5      S4    *disabled  pci:0000:00:05.0
  5. PCE6      S4    *disabled  pci:0000:00:06.0
  6. PCE7      S4    *disabled
  7. PCE9      S4    *disabled
  8. PCEA      S4    *disabled
  9. PCEB      S4    *disabled
  10. PCEC      S4    *disabled
  11. SBAZ      S4    *disabled
  12. PS2K      S3    *enabled   pnp:00:04
  13. PS2M      S3    *disabled  pnp:00:05
  14. P0PC      S4    *disabled  pci:0000:00:14.4
  15. UHC1      S4    *enabled   pci:0000:00:12.0
  16. UHC2      S4    *enabled   pci:0000:00:12.1
  17. UHC3      S4    *enabled   pci:0000:00:12.2
  18. USB4      S4    *enabled   pci:0000:00:13.0
  19. UHC5      S4    *enabled   pci:0000:00:13.1
  20. UHC6      S4    *enabled   pci:0000:00:13.2
  21. UHC7      S4    *enabled   pci:0000:00:14.5
  22. PWRB      S3    *enabled   platform:PNP0C0C:0
^C
$ inxi -M
Machine:   System: Acer product: Aspire M3300
           Mobo: Acer model: FRS780M
           Bios: American Megatrends v: P03-B0 date: 11/16/2009

```
So I am just as Stumped at this point as you.
Still working on it though.
By the way my mouse is what I do not allow to suspend:
```
**Bad           Autosuspend for USB device USB Receiver [Logitech]**
```

---

### Post by Mopar1973Man on 2016-07-18
I could try swapping keyboards with Mom's computer and see what happens but I doubt it will make much difference. I've still got the cordless Logictech keyboard I can try again.

The biggest problem I see in the USB port are powering down completely so any USB device is shut down and dead. I've been hunting for ways of getting the USB to stay powered up for this purpose.

sudo lshw
 [http://paste.ubuntu.com/19985001/](http://paste.ubuntu.com/19985001/)

```

Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 004: ID 058f:6364 Alcor Micro Corp. AU6477 Card Reader Controller
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 003: ID 045e:0752 Microsoft Corp. Wired Keyboard 400
Bus 007 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1f3a:1007 Onda (unverified) 
Bus 001 Device 002: ID 04a9:26a3 Canon, Inc. MF4100 series
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by QDR06VV9 on 2016-07-19
Hey Good Morning Mopar1973Man
All of the API's that suspend power basically tell the connected device to turn off, but power is still available on pin 1, so simple devices such as these can't be directly controlled programmatically. (Hey a New Word)

Seems like you would or might need to connect it to a Powered USB Hub and control the hub's power. None of the root hubs I have seen seems to be able to support power control.



All though there is a sys entry for this in Linux. From Documentation/usb/power-management.txt:
Read here:[http://www.mjmwired.net/kernel/Documentation/usb/power-management.txt](http://www.mjmwired.net/kernel/Documentation/usb/power-management.txt)

   >  power/level

    This file contains one of three words: "on", "auto",
    or "suspend".  You can write those words to the file
    to change the device's setting.

    "on" means that the device should be resumed and
    autosuspend is not allowed.  (Of course, system
    suspends are still allowed.)

    "auto" is the normal state in which the kernel is
    allowed to autosuspend and autoresume the device.

    "suspend" means that the device should remain
    suspended, and autoresume is not allowed.  (But remote
    wakeup may still be allowed, since it is controlled
    separately by the power/wakeup attribute.)

And this is just me thinking out loud
Something like: Note just an example not to just copy and paste.
```
echo on > /sys/bus/usb/devices/usb5/power/level
```

You may need to play with the autosuspend setting as well. Without telling the kernel to stop trying, it may suspend the port automatically.

Good luck!:)

---

### Post by Mopar1973Man on 2016-07-19
Kind of left at a dead end for now. I could order up a power USB hub and see what happen there or just live with it.  I do appreciate the effort in trying to resolve this weird issue. 

Now if only some can figure out the HDMI sound issue I'm having...
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1598303](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1598303)

... but another thread all in its own...

---

