---
title: "USB raid 1"
date: 2007-07-08
forum: General Help
---

### Post by jwdvd on 2007-07-08
Hi folks, im trying to set up raid 1 on 2 250Gb external usb disks.  I know how to set it up no probs, but when i reboot the drives tend to randomly map to a different /dev/sd* and so the raid set fails on boot.  Or, when i test it by powering down a drive, when i power it back up it will, as normal, mount to /dev/sdc1 and as a result the raid will fail.

Is there any way at all to force a usb drive to always map to the same /dev/sd*?

thanks in advance folks.

---

### Post by kidders on 2007-07-09
Hi there,

I know this isn't what you asked, but USB-based RAID1 is really insane. Are you sure there isn't a smarter way of doing whatever it is you want to achieve? Normally I don't like to make these sorts of uninvited comments, but in the case of RAID, I'd prefer to check. I hope you don't mind.

Anyhow, on to your question hehe ...

> **jwdvd said:**
> Is there any way at all to force a usb drive to always map to the same /dev/sd*?Thankfully there is, although I would personally choose a prefix other than "sd", which is considered reserved for system use. One way of achieving the desired result is...
[LIST=1]
[*]Take a look at the contents of /etc/udev/rules.d & notice how your /dev is constructed using these files. **Do not modify pre-existing files in /etc/udev/rules.d**.
[*]Use **udevinfo** to identify something unique about each of your USB devices (eg a manufacturer name, model number, UUID, etc ... even the USB port you intend to plug them into), and make new udev rules.
[*]Design the new rules to set up symlinks to the appropriate /dev/sd[X][n], but call them something distinctive, so there is no possibility your system will ever need the names you choose. Example: /dev/usb/gizmo1p1 (for USB disk #1, partition 1), /dev/usb/gizmo2p1 (for USB disk #2, partition 1), and so on.
[*]Save your custom rules in a new /etc/udev/rules.d file. You can call it almost anything you want, but try to stick to the same rough naming format used by the other rule files Ubuntu preinstalled.
[*]Execute **sudo udevcontrol reload_rules** to save yourself the trouble of rebooting every time you alter your udev ruleset.
[*]Use your custom /dev node names in place of the /dev/sd.... references you currently use.[/LIST]If you're using software RAID, it's worth noting that filesystem UUIDs exist for exactly the situation you've found yourself in. Although there's nothing at all wrong with writing your own udev rules, a simpler approach would be to avoid referencing /dev at all, and use the UUIDs of your RAID component filesystems instead. Obviously, this doesn't really apply to hardware RAID.

---

### Post by jwdvd on 2007-07-09
LOL, yeah i totally know its insane to have usb drive for a raid set, but its a small form factor system im using at the moment and i can oly fit one drive in it (the system drive), so the data drives are sitting in external bays.

cool guide though amd thanks LOADS, will have a look at that right away, cheers again.

---

