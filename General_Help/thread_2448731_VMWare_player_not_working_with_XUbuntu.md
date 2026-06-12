---
title: "VMWare player not working with XUbuntu"
date: 2020-08-12
forum: General Help
---

### Post by ferfykins on 2020-08-12
I get this error upon trying to install XUbuntu thru vmware player (hopefully this makes sense)    "Could not open /dev/vmmon: No such file or directory. Please make sure that the kernel module `vmmon' is loaded."   "Failed to initialize monitor device."

---

### Post by TheFu on 2020-08-12
End users typically use virtualbox for VMs on Linux.
Admins typically use KVM + virt-manager for VMs.

There is a Virtualization subforum here for virtualization questions, btw.

---

### Post by ferfykins on 2020-08-12
Got these errors with virtualbox after installing, trying to setup an instance of xubuntu with it  Kernel driver not installed (rc=-1908) The VirtualBox Linux kernel driver is either not loaded or not set up correctly. Please try setting it up again by executing '/sbin/vboxconfig' as root. If your system has EFI Secure Boot enabled you may also need to sign the kernel modules (vboxdrv, vboxnetflt, vboxnetadp, vboxpci) before you can load them. Please see your Linux system's documentation for more information. where: suplibOsInit what: 3 VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not installed. On linux, open returned ENOENT.    Failed to open a session for the virtual machine xbuntu-1.   The virtual machine 'xbuntu-1' has terminated unexpectedly during startup with exit code 1 (0x1).    Result Code:  NS_ERROR_FAILURE (0x80004005) Component:  MachineWrap Interface:  IMachine {85632c68-b5bb-4316-a900-5eb28d3413df}

---

### Post by TheFu on 2020-08-13
So, if you aren't an expert, having multiple hypervisors installed or partially installed, is bad.  virtualbox is a hypervisor.  VMWare Player is a different hypervisor. Don't attempt to have both installed.

I've never used either VMware PLayer or VirtualBox on a Linux host system. I've played with both on Windows hosts.  I have run many other hypervisors on many other OSes over the decades.

The SecureBoot stuff is all recent due to a problem with key leaks that impacts all systems booting via UEFI. These issues are less than a month old, so it is just bad luck with your timing, I suspect.  Windows systems are also impacted, BTW.

BTW, those errors are pretty clear for what it says needs to be done. Not sure I could do it, since I've never signed a driver before. I use gpg almost daily, but for emails, not trying to convince MSFT that my code should be allowed.  MSFT holds all the keys for a BIOS, BTW.  For $100 (I think that is the cost), we can get a key to sign our drivers .... from MSFT.  When SecureBoot was first pushed, I decided I wouldn't use UEFI booting if there was any other choice. I've been mostly successful at that. Only 1 laptop has UEFI booting here. The other 15 systems all use legacy-BIOS to boot, if they have any BIOS at all.

What should you do? IDK.  What I'd do is, 
a) ensure all remnants of any hypervisor has been removed.  That would be using the **apt remove --purge** command(s).
b) disable SecureBoot, at least for the time being. There is a boot flaw for all systems with SecureBoot enabled anyways, so that it can be bypassed. 
c) put a reminder to enable SecureBoot again in 2-3 months into my calendar. Perhaps by then, everything will be better solved and we will have transitioned more cleanly.
d) download all new ISO files that are older than 2 weeks from the sources again.  Eventually, the old keys will have to be marked as invalid, so all the old Linux distros using old SecureBoot keys will become disallowed.  On systems where new ISOs with new SecureBoot keys aren't available - well, those systems can never enable SecureBoot again. That includes Win7, BTW.

Clear as mud?

---

### Post by ferfykins on 2020-08-22
> **TheFu said:**
> So, if you aren't an expert, having multiple hypervisors installed or partially installed, is bad.  virtualbox is a hypervisor.  VMWare Player is a different hypervisor. Don't attempt to have both installed.  I've never used either VMware PLayer or VirtualBox on a Linux host system. I've played with both on Windows hosts.  I have run many other hypervisors on many other OSes over the decades.  The SecureBoot stuff is all recent due to a problem with key leaks that impacts all systems booting via UEFI. These issues are less than a month old, so it is just bad luck with your timing, I suspect.  Windows systems are also impacted, BTW.  BTW, those errors are pretty clear for what it says needs to be done. Not sure I could do it, since I've never signed a driver before. I use gpg almost daily, but for emails, not trying to convince MSFT that my code should be allowed.  MSFT holds all the keys for a BIOS, BTW.  For $100 (I think that is the cost), we can get a key to sign our drivers .... from MSFT.  When SecureBoot was first pushed, I decided I wouldn't use UEFI booting if there was any other choice. I've been mostly successful at that. Only 1 laptop has UEFI booting here. The other 15 systems all use legacy-BIOS to boot, if they have any BIOS at all.  What should you do? IDK.  What I'd do is,  a) ensure all remnants of any hypervisor has been removed.  That would be using the **apt remove --purge** command(s). b) disable SecureBoot, at least for the time being. There is a boot flaw for all systems with SecureBoot enabled anyways, so that it can be bypassed.  c) put a reminder to enable SecureBoot again in 2-3 months into my calendar. Perhaps by then, everything will be better solved and we will have transitioned more cleanly. d) download all new ISO files that are older than 2 weeks from the sources again.  Eventually, the old keys will have to be marked as invalid, so all the old Linux distros using old SecureBoot keys will become disallowed.  On systems where new ISOs with new SecureBoot keys aren't available - well, those systems can never enable SecureBoot again. That includes Win7, BTW.  Clear as mud?    Thanks, what would be the full command with purge to remove vmware and also virtual box? ty I'm a newb.... sorry

---

### Post by ferfykins on 2020-08-22
i tried:   sudo apt-get remove --purge virtualbox      but got this error:     [sudo] password for ferfykins273:  Reading package lists... Done Building dependency tree        Reading state information... Done Package 'virtualbox' is not installed, so not removed The following packages were automatically installed and are no longer required:   libcrystalhd3 libllvm9 Use 'sudo apt autoremove' to remove them. 0 upgraded, 0 newly installed, 0 to remove and 42 not upgraded. 1 not fully installed or removed. After this operation, 0 B of additional disk space will be used. debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable Setting up virtualbox-6.1 (6.1.12-139181~Ubuntu~eoan) ... debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable dpkg: error processing package virtualbox-6.1 (--configure):  installed virtualbox-6.1 package post-installation script subprocess returned error exit status 1 Errors were encountered while processing:  virtualbox-6.1 E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by kneutron on 2020-08-24
> [COLOR=#000000]/var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable

--There's your problem, use ' **lsof |grep **[/COLOR][COLOR=#000000]**config.dat** ' to find out what process is locking that file, and kill it.  And make sure the virtualbox GUI window is closed.[/COLOR]

---

### Post by TheFu on 2020-08-24
Read the rest of the output above and followed those instructions.

It is most helpful to post all errors and output from a terminal into a "code tag" wrapped entry here. We are used to seeing things in a specific way. Your job is to make helping easy.  "Code tags" .... are just like "quote tags", just with "code" instead. There is a button in the Advanced Editor if you must point-n-click.  I usually just use "quote" tags, then change both sides to "code".  Use the "Preview" button to check it is correct.
Properly used, all columns and tables that appear in the terminal will be displayed exactly the same here. No need to edit at all, beyond pasting and wrapping with the "code" parts.

---

