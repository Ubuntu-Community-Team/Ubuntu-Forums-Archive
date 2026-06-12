---
title: "The ash prompt starts after following wiki for custom live cd"
date: 2008-07-02
forum: General Help
---

### Post by rocketman768 on 2008-07-02
I followed the directions here:
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

but when the cd boots, it puts me into the "ash" shell and none of the stuff I put in the filesystem.squashfs file is there. What could have gone wrong?

---

### Post by rocketman768 on 2008-07-02
Bump it up

---

### Post by VMC on 2008-07-02
At what point during that setup does it dump you into a ash terminal?
Were you able to input any of the commands listed. A little more info would help.

---

### Post by rocketman768 on 2008-07-02
> **VMC said:**
> At what point during that setup does it dump you into a ash terminal?
Were you able to input any of the commands listed. A little more info would help.

Alright. I am able to see the "boot:" prompt, at which point I type "live" and press enter. A few of lines of text appear which are...

```
Ready.
[ 0.000000] ACPI: no DMI BIOS year, acpi=force is required to enable ACPI
[ 14.346458] PCI: PIIX3: Enabling Passive Release on 0000:00:01.0
Loading, please wait...

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
```

The prompt then looks like "(initramfs) ". When I do ls, it appears that the filesystem that is loaded into / is the initrd.gz that I specified in the isolinux.cfg. However, I find the file /casper.log which says "Unable to find a medium containing a live filesystem".

Doesn't sound right to me. I mean, in the iso image, /casper/filesystem.squashfs is there and I have verified that it contains the right data.

On another note, "ls /dev" from this ash shell doesn't show my cdrom drive, so I can't manually mount the cdrom and grab the squashfs filesystem from there.

Does that help?

---

### Post by rocketman768 on 2008-07-03
Bump it up.

---

### Post by rocketman768 on 2008-07-03
Solved it. I was testing the image using qemu:

```
qemu -cdrom mylivecd.iso -boot d
```

Turns out that qemu has problems with these live cds (I guess). It wouldn't even boot up the normal 8.04 live cd. I used virtualbox-ose instead, and it works beautifully!

---

