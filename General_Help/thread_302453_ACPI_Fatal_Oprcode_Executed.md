---
title: "ACPI: Fatal Oprcode Executed"
date: 2006-11-18
forum: General Help
---

### Post by tedrogers on 2006-11-18
Hi,

I hope this isn't serious, but on my IBM T22 running Edgy I sometimes get the following error message (I think's it's an error anyway!):

```
Fatal opcode executed
```

This doesn't happen all of the time, just occasionally on booting the system (after the filesystem check) and sometimes on shutdown.

Any ideas? Is it serious? And does it need fixing at all - or is it normal?

Thanks in advance.

---

### Post by bodhi.zazen on 2006-11-25
> **tedrogers said:**
> 

```
Fatal opcode executed
```

This doesn't happen all of the time, just occasionally on booting the system (after the filesystem check) and sometimes on shutdown.

Any ideas? Is it serious? And does it need fixing at all - or is it normal?

Thanks in advance.

I think this has to do with acpi.

[ACPI](http://www.acpi.info/) 

acpi has to do with power management and what will happen if you hit the power button.

There have been a few bug reports with Ubuntu, most of these are in regards to the computer failing to boot. General advise booting with acpi=off Do you know how to do this?

My advice is if everything else is running OK I would leave it. I do not think this is a serious problem.

---

### Post by tedrogers on 2006-11-25
No...I don't know how to run with ACPI off.

Do I need to edit xorg.conf file or something?

I'd like to test it to isolate the problem...although I do use my ACPI on the laptop.

Thanks.

---

### Post by bodhi.zazen on 2006-11-25
In a terminal type:```
gksudo gedit /boot/grub/menu.lst
```

Now COPY your Ubuntu stanzas

In the copied stanzas, change the title to "Ubuntu No ACPI"

At the end of the "kernel (hd0,x)/vmlinuz root=/dev/hdxy vga=791"

Add pci=noacpi to the end of the line, like this:> kernel (hd0,x)/vmlinuz root=/dev/hdxy vga=791 pci=noacpi

Reboot

Now you will see a grub entry for Ubutnu No ACPI; Boot it.

If you have problems, you can always return to your previous Ubuntu boot and re-post...

---

### Post by tedrogers on 2006-11-25
Well...I did it...and no errors so far...will see how it goes.

Cheers.

---

### Post by tedrogers on 2006-11-26
Nope...I stand corrected.

It was ok for a few reboots....but then just now after the fsck check (which seems to happen every other time I boot now - but that's another issue) it just gave me the same old ACPI: Fatal Opcode Error.

This is getting annoying now. :evil:

Any ideas anyone? Why should it happen after the fsck check and not when it boots without drive integrity check?

Thanks.

---

### Post by rouben on 2006-12-15
Perhaps your attempt at killing ACPI was not successful? Would you be willing to try the following: [http://ubuntuforums.org/showthread.php?t=2620](http://ubuntuforums.org/showthread.php?t=2620)

Also FYI, there is a bug related to this issue: [https://bugs.launchpad.net/distros/ubuntu/+source/initrd-tools/+bug/58386](https://bugs.launchpad.net/distros/ubuntu/+source/initrd-tools/+bug/58386)

And a support request as well: [https://answers.launchpad.net/distros/ubuntu/+ticket/2732](https://answers.launchpad.net/distros/ubuntu/+ticket/2732)

Good luck, and let me know how it goes!

---

### Post by tedrogers on 2006-12-15
I tried the thread and it didn't really do much at all....in fact it kinda made things worse as now none of the power features worked like suspend and hibernate....so I put it back to how it was.

Thanks for your help anyway.

---

