---
title: "Grub Customizer in 13.10 - Error message"
date: 2014-02-05
forum: General Help
---

### Post by 2CV67 on 2014-02-05
On booting 13.10, I now get this error message:
```
error: can't find command 'gfxmode'.
vga=775 is deprecated. Use set gfxpayload=1280x1024x8, 1280x1027 before linux command instead.
Press any key to continue...
```

Pressing any key or waiting a few seconds results in a normal boot.

Some background:
I have been multi-booting XP & Ubuntu LTS & Ubuntu current version, since 2006 on the same old desktop PC (see signature).
I have been using Grub Customizer since 2012.
Up to last week, I had XP & Ubuntu 12.04LTS & Ubuntu 13.04 with GC 2.5.1 & everything was fine.
This week, I upgraded 13.04 to 13.10 & things were still fine, except I had several superfluous items in my Grub Menu.
I went to GC to thin them out & was surprised that the order in GC was not the same as the order on the menu.
But I managed to remove (hide) the unwanted entries OK.

In SynApt, I seemed to have the latest version of GC (2.5.1) but searching showed I should have version 4 for 13.10.
So I added a new PPA for GC 13.10 & installed GC4.0.4.

Now, when I boot to 13.10, I get the above error message.
Booting to LTS 12.04 (or XP) is OK with no errors.

In etc/default/grub, I see these lines (also visible in GC advanced settings):
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="vga=775 splash"
GRUB_GFXMODE="640x480"
```

In GNU GRUB Manual 2.00, I found:

```
14.3.24 linux

Command: linux file …

    Load a Linux kernel image from file. The rest of the line is passed verbatim as the kernel command-line. Any initrd must be reloaded after using this command (see initrd).

    On x86 systems, the kernel will be booted using the 32-bit boot protocol. Note that this means that the ‘vga=’ boot option will not work; if you want to set a special video mode, you will need to use GRUB commands such as ‘set gfxpayload=1024x768’ or ‘set gfxpayload=keep’ (to keep the same mode as used in GRUB) instead. GRUB can automatically detect some uses of ‘vga=’ and translate them to appropriate settings of ‘gfxpayload’. The linux16 command (see linux16) avoids this restriction. 


14.3.25 linux16

Command: linux16 file …

    Load a Linux kernel image from file in 16-bit mode. The rest of the line is passed verbatim as the kernel command-line. Any initrd must be reloaded after using this command (see initrd16).

    The kernel will be booted using the traditional 16-bit boot protocol. As well as bypassing problems with ‘vga=’ described in linux, this permits booting some other programs that implement the Linux boot protocol for the sake of convenience.

    This command is only available on x86 systems. 
```

I suppose there are plenty of clues there for experts...
Can anybody help me to understand what has gone wrong?
And what to do to fix it?

Many thanks!

---

### Post by 2CV67 on 2014-02-06
Well - I tried Boot Repair.

What it did was purge & reinstall Grub2, also removing Grub Customizer.

After that booting was OK, with no error messages.

I then reinstalled GC to make some minor changes to the Grub Menu.

So far, booting is clean...

---

