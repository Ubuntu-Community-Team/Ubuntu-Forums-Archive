---
title: "Backlight message on boot"
date: 2013-05-29
forum: General Help
---

### Post by Barhilton on 2013-05-29
I'm using a Dell XPS 15, 13.04. In order to get my backlight brightness control to work I have to use "acpi_backlight=vendor dell_laptop.backlight=0". But when I boot, I get the message: dell_laptop: '0' invalid parameter for 'backlight', at which my computer then continues to boot and works normally, with the brightness control working. It seems that I can change the '0' to anything, get the same message with the '0' changed to whatever I changed it to, and the brightness control still works. How can I get the message to go away?

---

### Post by Toz on 2013-05-29
What happens if you remove "dell_laptop.backlight=0" from your boot parameters? Do the brightness controls still work? Perhaps the parameter is no longer required or valid.

---

### Post by Barhilton on 2013-05-29
The brightness controls don't work properly without [COLOR=#000000]'dell_laptop.backlight=0'. 'acpi_backlight=vendor' means that if I quickly and repeatedly press the key to change brightness, it eventually lowers, but sometime the down key makes it higher and visa versa, making it difficult to change. Adding '[/COLOR][COLOR=#000000]dell_laptop.backlight=0' makes the controls work perfectly normally.[/COLOR]

---

### Post by Toz on 2013-05-29
Hmmm. Its odd then that it generates that message. The message seems to indicate that the parameter had no effect.

Could I have a look at your dmesg log file?
```
pastebinit /var/log/dmesg
``` 
...and post back the link that is generated.

And you can you also post back the results of:
```
cat /var/log/syslog | grep -i backlight
```

---

### Post by Barhilton on 2013-05-30
[http://paste.ubuntu.com/5716188/](http://paste.ubuntu.com/5716188/)

```
May 29 17:36:09 benjamin-XPS-L501X kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-22-generic root=UUID=df9e5312-fd68-4a0f-99fb-8b6667021bea ro quiet splash acpi_backlight=dell_laptopMay 29 17:36:09 benjamin-XPS-L501X kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-22-generic root=UUID=df9e5312-fd68-4a0f-99fb-8b6667021bea ro quiet splash acpi_backlight=dell_laptop
May 29 17:37:56 benjamin-XPS-L501X kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-22-generic root=UUID=df9e5312-fd68-4a0f-99fb-8b6667021bea ro quiet splash acpi_backlight=vendor backlight=dell_laptop
May 29 17:37:56 benjamin-XPS-L501X kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-22-generic root=UUID=df9e5312-fd68-4a0f-99fb-8b6667021bea ro quiet splash acpi_backlight=vendor backlight=dell_laptop
May 29 17:39:30 benjamin-XPS-L501X kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-22-generic root=UUID=df9e5312-fd68-4a0f-99fb-8b6667021bea ro quiet splash acpi_backlight=vendor dell_laptop.backlight=0
May 29 17:39:30 benjamin-XPS-L501X kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-22-generic root=UUID=df9e5312-fd68-4a0f-99fb-8b6667021bea ro quiet splash acpi_backlight=vendor dell_laptop.backlight=0
May 29 17:39:30 benjamin-XPS-L501X kernel: [   22.204699] dell_laptop: `0' invalid for parameter `backlight'
May 29 18:21:05 benjamin-XPS-L501X kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-22-generic root=UUID=df9e5312-fd68-4a0f-99fb-8b6667021bea ro quiet splash acpi_backlight=vendor dell_laptop.backlight=0
May 29 18:21:05 benjamin-XPS-L501X kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-22-generic root=UUID=df9e5312-fd68-4a0f-99fb-8b6667021bea ro quiet splash acpi_backlight=vendor dell_laptop.backlight=0
May 29 18:21:05 benjamin-XPS-L501X kernel: [   22.595505] dell_laptop: `0' invalid for parameter `backlight'
May 30 10:26:06 benjamin-XPS-L501X kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-22-generic root=UUID=df9e5312-fd68-4a0f-99fb-8b6667021bea ro quiet splash acpi_backlight=vendor dell_laptop.backlight=0
May 30 10:26:06 benjamin-XPS-L501X kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-22-generic root=UUID=df9e5312-fd68-4a0f-99fb-8b6667021bea ro quiet splash acpi_backlight=vendor dell_laptop.backlight=0
May 30 10:26:06 benjamin-XPS-L501X kernel: [   21.679170] dell_laptop: `0' invalid for parameter `backlight'
May 30 10:53:49 benjamin-XPS-L501X kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-22-generic root=UUID=df9e5312-fd68-4a0f-99fb-8b6667021bea ro quiet splash acpi_backlight=vendor dell_laptop.backlight=hiimbarhilton
May 30 10:53:49 benjamin-XPS-L501X kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-22-generic root=UUID=df9e5312-fd68-4a0f-99fb-8b6667021bea ro quiet splash acpi_backlight=vendor dell_laptop.backlight=hiimbarhilton
May 30 10:53:49 benjamin-XPS-L501X kernel: [   21.666765] dell_laptop: `hiimbarhilton' invalid for parameter `backlight'
May 30 10:58:58 benjamin-XPS-L501X kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-22-generic root=UUID=df9e5312-fd68-4a0f-99fb-8b6667021bea ro quiet splash acpi_backlight=vendor dell_laptop.backlight=0
May 30 10:58:58 benjamin-XPS-L501X kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-22-generic root=UUID=df9e5312-fd68-4a0f-99fb-8b6667021bea ro quiet splash acpi_backlight=vendor dell_laptop.backlight=0
May 30 10:58:58 benjamin-XPS-L501X kernel: [   23.050627] dell_laptop: `0' invalid for parameter `backlight'
```

You're right, by the way, that in a sense the parameter has no effect. As you can see above, I tried changing the '0' to 'hiimbarhilton': the brightness controls still worked properly, and I still got the error message, just with 'hiimbarhilton' instead of '0'.

---

### Post by Toz on 2013-05-30
Very interesting that the parameter makes the brightness work even though it seems to be invalid. Not sure what to say.

Guess you could ignore the message or file a bug report about it - your choice.

I also found this in your dmesg:
> [   24.211646] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
A google search indicates that it is a common problem with this laptop, but I have not been able to come across any solutions. I believe this has to something to do with the video and may be the cause of the backlight issues. It maybe best to create a bug report and follow through with that avenue.

---

### Post by Barhilton on 2013-05-30
Yes, I think I'll file a bug. Do you know which package I should report?

---

### Post by Toz on 2013-05-30
> **Barhilton said:**
> Yes, I think I'll file a bug. Do you know which package I should report?

Report it against the linux package:
```
apport-bug linux
```

---

### Post by Barhilton on 2013-05-30
Bug reported at: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1185927](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1185927). Thanks for your help Toz!

---

