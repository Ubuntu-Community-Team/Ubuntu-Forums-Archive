---
title: "Boot keeps defaulting to Legacy mode"
date: 2023-10-02
forum: General Help
---

### Post by jacatone on 2023-10-02
Installed Ubuntu 23.04 on an old Dell Latitude E6430 laptop. This laptop has both a legacy and uefi mode.Selected the uefi mode to install the os which went without any issue but boot mode keeps defaulting to legacy and giving me an "invalid partition table" error message so I have to go back into the bios and select uefi again. The secure boot has always remain disabled so that's not the problem. Would I fix this by changing the MBR to GPT?

---

### Post by oldfred on 2023-10-02
With Ubuntu you can use gpt (or old MBR) with either UEFI or BIOS boot.
I started using gpt with BIOS in 2010. 
Windows requires gpt for UEFI boot, and Ubuntu really should, but does not.

Partitioning probably is not the issue, but the default boot mode in System settings is.
Check UEFI settings.

Make sure you have latest available UEFI firmware from vendor.

---

### Post by guiverc on 2023-10-03
> **jacatone said:**
> Installed Ubuntu 23.04 on an old Dell Latitude E6430 laptop. This laptop has both a legacy and uefi mode.Selected the uefi mode to install the os which went without any issue but boot mode keeps defaulting to legacy and giving me an "invalid partition table" error message so I have to go back into the bios and select uefi again. The secure boot has always remain disabled so that's not the problem. Would I fix this by changing the MBR to GPT?

I'll give my thoughts, but please note I'm no expert in the various boot modes.

Ubuntu 23.04 Desktop (*if that's what you're using, you don't mention Desktop or Server, but do mention laptop*) is available with 2 ISOs that control which ISO you're using, Ubuntu 23.04 Server uses a third installer.

I am aware that Ubuntu `ubiquity` and `calamares` installers can be tricked to install in an incorrect mode when the ISO is reformatted & written to install media, ie. the installer can be made to always select uEFI when box is *legacy*, or vice-versa, but if the ISO is written correctly (*as documented*) this won't happen. You don't mention what tool you wrote the ISO with, but many tools allow you to reformat the ISO during the write (*using a clone or dd type of write is usually best*).  FYI:  The *legacy* installer for Ubuntu 23.04 Desktop uses `ubiquity`

I can't speak much as to `subiquity` or `ubuntu-desktop-installer` (Ubuntu 23.04 Server, or Ubuntu 23.04 Desktop [*primary ISO*])

ie. I'd check how you wrote the ISO (*whichever 23.04 ISO it **was*) to your install media.

Also if you're asking about Ubuntu 23.04 Desktop; have you tried the alternate ISO which uses the other installer choice?  

If you're using Ubuntu 23.04 Desktop and the ISO using `ubuntu-desktop-installer`, you can also try forcing the upgrade of the installer PRIOR to starting the actual install, as it's capable of being updated.

---

