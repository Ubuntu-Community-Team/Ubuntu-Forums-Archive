---
title: "Screen Brightness - Lenovo Yoga 2 11, Ubuntu 14.04"
date: 2014-07-20
forum: General Help
---

### Post by mykrob on 2014-07-20
Installed 14.04 on a new Lenovo Yoga 2 11. Got wifi working, got multitouch working on the touchpad.

The only other thing I would **LOVE** to have working is the screen brightness adjustment. Thing is, I had it working at one point, then it stopped. So, here's what I've done so far...

To get the wireless working, I blacklisted the ideapad_laptop module. I wonder if this is what killed the screnn brightness....

I installed a kernel module to allow the multitouch Elan touchpad to work as a touchpad instead of a basic mouse.

For screen brightness, I currently am passing this boot paramter in GRUB:

```
myk@lenovoYoga-PC:~$ cat /proc/cmdline 
BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=c91a0c9a-61ef-4952-8235-1c2dcec2d801 ro acpi_osi=Linux acpi_backlight=vendor quiet splash vt.handoff=7

```

And here's what the video adapter is:

```
myk@lenovoYoga-PC:~$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: ValleyView Gen7
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:105 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:1050(size=8)
myk@lenovoYoga-PC:~$ 

```

Help?

Thanks

---

### Post by varunendra on 2014-07-20
> **mykrob said:**
> To get the wireless working, I blacklisted the ideapad_laptop module. I wonder if this is what killed the screnn brightness....

Could be.., can you unblacklist it again and see if the hotkeys to adjust brightness start working again? Of course try the keys after a reboot after unblacklisting the module.

But in case it is the blacklisting of ideapad_laptop that disabled the hotkey control, I believe the software control should still work. So is the slider in "Brightness and Lock" control panel still able to adjust the brightness? If yes, and IF blacklisting of ideapad_laptop is necessary to enable the wifi, you can create a script and use it with "xbindkeys" program to assign a different set of hotkeys to control the brightness. Something like mentioned here : [http://ubuntuforums.org/showthread.php?t=2179727&p=12813357#post12813357](http://ubuntuforums.org/showthread.php?t=2179727&p=12813357#post12813357)

---

### Post by mykrob on 2014-07-21
@varundra

I'll try loading that module and see what happens. As it stands, with everything as is, the hotkeys actually do work. I can control the volume with them. When I press the hotkey for screen brightness, I get the visual representation, meaning the slider appears, however it only drops one level. So it looks like the keypress is being received, but perhaps the system is "confused" as to how many levels of adjustment are available. 

Will test with the module in a bit and post back.

Thanks

---

### Post by mykrob on 2014-07-21
Loading the ideapad_laptop module kills wifi and does not change the screen brightness issue.

It is receiving the proper event from the keypress, it just isn't doing anything:

```

myk@lenovoYoga-PC:~$ acpi_listen
video/brightnessdown BRTDN 00000087 00000000
video/brightnessdown BRTDN 00000087 00000000
video/brightnessdown BRTDN 00000087 00000000
video/brightnessdown BRTDN 00000087 00000000
video/brightnessdown BRTDN 00000087 00000000
video/brightnessup BRTUP 00000086 00000000
video/brightnessup BRTUP 00000086 00000000
video/brightnessup BRTUP 00000086 00000000
video/brightnessup BRTUP 00000086 00000000
video/brightnessup BRTUP 00000086 00000000

```

May need to try more boot parameters until i hit the right one. Just can't understand why it worked before, unless an update broke something.

---

### Post by mykrob on 2014-07-21
> **varunendra said:**
> Could be.., can you unblacklist it again and see if the hotkeys to adjust brightness start working again? Of course try the keys after a reboot after unblacklisting the module.

But in case it is the blacklisting of ideapad_laptop that disabled the hotkey control, I believe the software control should still work. So is the slider in "Brightness and Lock" control panel still able to adjust the brightness? If yes, and IF blacklisting of ideapad_laptop is necessary to enable the wifi, you can create a script and use it with "xbindkeys" program to assign a different set of hotkeys to control the brightness. Something like mentioned here : [http://ubuntuforums.org/showthread.php?t=2179727&p=12813357#post12813357](http://ubuntuforums.org/showthread.php?t=2179727&p=12813357#post12813357)

realizing i didn't totally answer your question. No, adjusting the slider in the control panel does not do anything.

---

### Post by mykrob on 2014-07-21
Got it resolved. Used the following boot paramter:

```

myk@lenovoYoga-PC:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=c91a0c9a-61ef-4952-8235-1c2dcec2d801 ro quiet splash video.use_native_backlight=1 vt.handoff=7

```

---

### Post by Toz on 2014-07-21
*Removed duplicates.*

Glad to see you got it worked out. The **video.use_native_backlight=1** kernel parameter replaces "acpi_backlight=vendor" kernel parameter in kernel versions 3.13 and greater.

---

### Post by kuckunniwi on 2014-11-05
Was having  same exact problem on a Yoga 2 Pro, Kubuntu 14.04 x64. The *video.use_native_backlight=1* line worked like a charm, thanks!

---

### Post by Deadloks on 2014-12-31
Hello mykrob, I'm relatively new in the wonderful Ubuntu world, and I just bought a Lenovo Yoga 2 11 inches, I have the same problem of brightness that you got.
I read the whole subject and it appears that you succesfully solved it.
However I didn't understand how. When I manage to access to /proc/cmdline to change it with +**video.use_native_backlight=1 **I can't save the file anymore even with sudo.
I tryed with nano / vim / echo builtin...
I know that you got the problem a long time ago but I appreciate if you could be of help because my eyes are bleeding from this brightness.
Sorry if my english is bad (it's not my native language).
thanks.

---

### Post by Toz on 2014-12-31
@Deadloks, welcome.

You need to add a [kernel boot parameter]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") to your system. Instructions at that link,

---

