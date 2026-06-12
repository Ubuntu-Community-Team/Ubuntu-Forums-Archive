---
title: "Suspend fails due to xhci driver. Can't get pre-suspend script to work."
date: 2020-06-13
forum: General Help
---

### Post by cynojien on 2020-06-13
I've been unable to get the system to suspend normally for quite sometime. This is due to some sort of kernel bug with the xhci_hcd driver and one of my onboard USB ports.
The driver MUST be unbind'd before suspending or the system will hang (either for ~30 seconds or indefinitely). I tried a few months back and about a year before that as well to get a system-sleep script to work. I have tried the script in both > /usr/lib/systemd/system-sleep/ as well as > /lib/systemd/system-sleep It would seem the later is what systemd actually pulls from. For whatever reason the script would never work. I ended up just making a normal script and running it with pkexec and it works fine but now that gnome has a proper Suspend button I wanted to see if I could finally get this working the "right" way. It would seem nothing has changed.

So here's the script. > #!/bin/bash

if [ "${1}" == "pre" ]; then
    umount -f "/mnt/****"
    sleep 2
    cryptsetup close ****
    sleep 2
    echo -n "0000:03:00.0" > /sys/bus/pci/drivers/xhci_hcd/unbind

elif [ "${1}" == "post" ]; then
    sleep 8
    echo -n "0000:03:00.0" > /sys/bus/pci/drivers/xhci_hcd/bind
    sleep 3
    cryptsetup luksOpen /dev/disk/by-uuid/*****-****-****-****-************ **** --key-file /*********
fi

I've tried also having both the pre and post section just sh to a separate script to no avail. I also attempted to create a service to run just the pre-script and having it wanted by sleep.target. That also had no effect.

Running journalctl -u systemd-suspend.service gets this.
> Jun 13 01:53:04 the-bunts systemd-sleep[23343]: /bin/echo: /bin/echo: cannot execute binary file
Jun 13 01:53:04 the-bunts systemd-sleep[23315]: Suspending system...
or if I try having the seperate pre and post scripts I get this.
> Jun 13 02:03:34 the-bunts systemd[1]: Starting Suspend...
Jun 13 02:03:38 the-bunts systemd-sleep[13059]: Suspending system...
Jun 13 02:04:18 the-bunts systemd-sleep[13059]: Failed to suspend system. System resumed again: Device or resource busy.
Jun 13 02:04:18 the-bunts systemd-sleep[13130]: 0000:03:00.0
Jun 13 02:04:18 the-bunts systemd-sleep[13169]: 0000:03:00.0
Jun 13 02:04:18 the-bunts systemd-sleep[13201]: 0000:03:00.0
Jun 13 02:04:18 the-bunts systemd-sleep[13201]: /dev/sdb:
Jun 13 02:04:18 the-bunts systemd-sleep[13201]:  setting Advanced Power Management level to 0xfe (254)
Jun 13 02:04:18 the-bunts systemd-sleep[13201]:  APM_
Jun 13 02:04:18 the-bunts systemd-sleep[13232]:  APM_
Jun 13 02:04:18 the-bunts systemd-sleep[13232]: /dev/sdc:
Jun 13 02:04:18 the-bunts systemd-sleep[13232]:  setting Advanced Power Management level to 0xfe (254)
Jun 13 02:04:23 the-bunts systemd-sleep[13232]:  APM_level        =
Jun 13 02:04:23 the-bunts systemd[1]: systemd-suspend.service: Main process exited, code=exited, status=1/FAILURE
Jun 13 02:04:23 the-bunts systemd[1]: systemd-suspend.service: Failed with result 'exit-code'.
Jun 13 02:04:23 the-bunts systemd[1]: Failed to start Suspend.

I tried a whole slew of other things last time I tried to get this to work, though that was so long ago that I couldn't fathom to remember.
I'm at a loss guys. Any ideas?

Thanks

---

