---
title: "Re: Xubuntu Roll Back to 17.04"
date: 2018-02-25
forum: General Help
---

### Post by ukkid35 on 2018-02-25
Unfortunately I upgraded to 17.10.1 without trying the LiveCD first, and I now have an IO-APIC error (with both the upgrade and the LiveCD)

I can boot in to Linux 4.10.0.42 via the grub menu with no problems (seems to mention IO-APIC but continues anyway)

Is there an easy way to boot automatically in to the working install?

Do I have to remove the upgrade, if so how do I do that?

Many thanks

I think the answer is to edit the Grub menu

GRUB_DEFAULT="1>3"

as per [https://unix.stackexchange.com/questions/62733/how-to-correctly-set-up-the-right-grub-2-default-menu-entry](https://unix.stackexchange.com/questions/62733/how-to-correctly-set-up-the-right-grub-2-default-menu-entry)

This should then boot the forth line in the Advanced Options



However, I have now managed to change the boot options for the LiveCD by adding

noapic radeon.modeset=0

as per [https://ubuntuforums.org/showthread.php?t=2283568](https://ubuntuforums.org/showthread.php?t=2283568)

After a worrying looking splash screen the LiveCD boots successfully, so it now makes sense to try to add the same option to the installed system

Any help doing that would be much appreciated

---

### Post by ajgreeny on 2018-02-25
There is no "roll-back" facility to do what you want, and even if there were, it would be pointless as 17.04 has now lost support so would be a security risk.

If you really do want to try a different version you will really have to clean install 16.04, but tell us more about your problem; you say you can boot to 4.10.0-42, but you do not tell us if that was in 17.04 or the new 17.10 installation.

Is the 4.13.0-32 kernel the problem one giving you the IO-APIC error?

---

### Post by ukkid35 on 2018-02-25
Many thanks for your reply

With 17.10 installed I can boot to 4.10.0-42, but 4.13.0-32 gives the IO-APIC error

The Grub menu edit works nicely

Ideally I'd like to add the "noapic radeon.modeset=0" option but how to do that has eluded me so far

I will try the 'Boot Repair' next as per your sig line

"configure GRUB, add kernel options (acpi=off ...)" - sounds like what I need

Tried amending the Grub using Boot Repair by adding "radeon.modeset=0" which is what worked as a boot option for the LiveCD

Then tried a second time using "noapic" which is what the error message recommends

add_kernel_option CHOSEN_KERNEL_OPTION is : noapic

Unfortunately neither allowed the machine to boot

[http://paste.ubuntu.com/p/J8tKcdFGtJ/](http://paste.ubuntu.com/p/J8tKcdFGtJ/)

After rebooting to 4.10.0-42 a few times I lost all video modes other than 800x600

I decided to try booting in to 4.13.0-32, hey presto it worked

So I edited the Grub menu manually

[COLOR=#B8860B]GRUB_CMDLINE_LINUX_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"quiet splash nomodeset radeon mode=0 noapic"

[/COLOR]to[COLOR=#BB4444]

[COLOR=#B8860B]GRUB_CMDLINE_LINUX_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"quiet splash"

[/COLOR][/COLOR]And now I have full video modes back but no ability to boot in to 4.13.0-32

One last attempt by editing the Grub menu manually

[COLOR=#B8860B]GRUB_CMDLINE_LINUX_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"quiet splash"

[/COLOR][COLOR=#000000]to[/COLOR][COLOR=#BB4444]

[COLOR=#B8860B]GRUB_CMDLINE_LINUX_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"quiet splash noapic"

[/COLOR][/COLOR]And now I have full video modes and the ability to boot in to 4.13.0-32

---

### Post by mörgæs on 2018-02-25
Good, but next time please edit the latest post rather than posting five times in a row.

---

