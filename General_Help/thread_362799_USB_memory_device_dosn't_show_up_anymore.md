---
title: "USB memory device dosn't show up anymore"
date: 2007-02-16
forum: General Help
---

### Post by sharperguy on 2007-02-16
Hi

Usually with ubuntu I plug in my mp3 player, which shows up as a data device, and it works fine.

But now, for no apparent reason, it isn't showing up.

Anyone got any ideas as to why this might be, and how to solve it?

PS: I ran "ls /dev | grep sd" (because its usually shows  as sda) it wasn't there
I tryed rebooting with it still plugged in and no luck

---

### Post by gradedcheese on 2007-02-16
two things to check:

plug the player in, wait about 15 seconds and run:

```

dmesg | tail

```

This should tell you which /dev was picked for the player, and also any errors that occurred when the kernel recognized it.  You can also do this:

```

ls -al /dev/disk/by-id/

```

this gives you some idea of where the device got mapped (if anywhere)

---

### Post by sharperguy on 2007-02-16
Hmm

This was the output of "dmesg | tail"

```

[17179632.424000] ACPI: Power Button (FF) [PWRF]
[17179632.424000] ACPI: Power Button (CM) [PWRB]
[17179632.424000] ACPI: Sleep Button (CM) [SLPB]
[17179632.616000] ibm_acpi: ec object not found
[17179632.664000] pcc_acpi: loading...
[17179635.556000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17179635.556000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179635.556000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17179637.316000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179637.316000] apm: overridden by ACPI.

```

But I can't really make sense of it :S

---

### Post by gradedcheese on 2007-02-16
hmm, nothing about your device at the end of dmesg.  Try the same thing without tail (ie "dmesg") and scroll upward a little, you should see something about a USB disk.  The rest of my message still applies, namely the /dev/disk/ stuff

---

### Post by sharperguy on 2007-02-17
dmesg dosn't seem to mentoion the device either!

Very strange....

---

### Post by gradedcheese on 2007-02-17
That is indeed rather odd.  Please double check:

1) remove the drive and wait a little
2) clear dmesg by running "sudo dmesg -c"
3) insert the device, clear your terminal ("clear") and wait a little
4) run "dmesg" to see just the new output -- is there any?  does it mention the USB/SCSI device?

---

