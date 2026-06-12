---
title: "My solution to suspend problem"
date: 2008-02-07
forum: General Help
---

### Post by robert114 on 2008-02-07
Until now I haven't been able to put my machine in suspend/sleep for multiple times. The machine just hang the second time. I needed to power off the machine to let it reboot.

My first solution was to install the powersaved application and use the command “sudo powersave -u”. This way I was able to put the machine in sleep. But it had it's glitches, coming back from the sleep mode didn't allways work well and gave me sometimes a very weird graphical screen (can't describe it). But I found out, that the “sudo powersave -u” command removed some modules that are known to give problems by suspending the machine.

I located the troubling modules witch my machine uses and I disabled them before I suspend my machine. And it works like a sweet ... now. I don't shutdown my machine anymore :-)

These are the troubling modules:
usb_storage sbp2 ohci_hcd uhci_hcd stir4200 ohci1394 rt2500 prism54 ath_pci r8169 lt_modem Intel536 Intel537 ndiswrapper

(from: /etc/powersave/sleep)

Let me know if this information is of any use. If you're stille having problems, it's likely I can't help you since I'm not an expert, but I might be able to help you a little bit further...

---

