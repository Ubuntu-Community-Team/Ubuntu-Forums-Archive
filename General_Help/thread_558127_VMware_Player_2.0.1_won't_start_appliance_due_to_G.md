---
title: "VMware Player 2.0.1 won't start appliance due to GPF"
date: 2007-09-23
forum: General Help
---

### Post by secdroid on 2007-09-23
Total VMware noob warning!

Running Dapper.  Installed new VMware player 2.0.1 with success messages throughout.  Downloaded the Damn Small Linux 3.3 and 3.4.3 virtual appliances and both fail in the same way.

VMware showing DSL boot process:
> Boot: dsl vga=normal
Loading Linux24........
Loading minirt24.gz.....
Ready
Uncompressing Linux...  OK, booting the kernel
general protection fault: 0000

VMware log:
> Sep 23 15:37:25.168: mks| MKS could not find key event for 0x25 up
Sep 23 15:37:25.169: mks| MKS could not find key event for 0x25 down
Sep 23 15:37:26.133: mks| Ignoring update request in VGA_Expose (mode change pending).
Sep 23 15:37:39.068: vcpu-0| X86Fault_Warning: vmcore/vmm32/bt/btpriv.c:1444: cs:eip=0x10:0xc02e607f fault=13

The (vendor supplied) vmx file:
> #!/usr/bin/vmware
  # VM Machine Info
  guestOS = "linux"
  displayName = "dsl-3.3"
config.version = "7"
  memsize = "128"

  # CDROM Info
  ide1:0.present = "TRUE"
  ide1:0.fileName = "dsl-3.3.iso"
  ide1:0.deviceType = "cdrom-image"

  #Floppy Info
  floppy0.present = "FALSE"

  #Ethernet Info
  Ethernet0.present = "TRUE"
  ethernet0.addressType = "generated"

  # Audio Settings
  sound.present = "TRUE"
  sound.autodetect = "TRUE"

  # Host USB
  usb.present = "TRUE"

virtualHW.version = "3"
sound.fileName = "-1"
extendedConfigFile = "dsl.vmxf"
virtualHW.productCompatibility = "hosted"
tools.upgrade.policy = "manual"

ethernet0.generatedAddress = "00:0c:29:0f:0b:54"
uuid.location = "56 4d e2 01 9c 1a 7f a7-d3 1a c6 a4 0e 0f 0b 54"
uuid.bios = "56 4d e2 01 9c 1a 7f a7-d3 1a c6 a4 0e 0f 0b 54"
ethernet0.generatedAddressOffset = "0"

I've read the docs, googled, etc and I haven't found any hints on how to debug this sort of thing.  Suggestions, anyone?

---

### Post by secdroid on 2007-09-24
Mea culpa... ;)

I think my problem stems from the fact that I used the.rpm of 2.0.1 and converted it with the "alien" command.  Bad move, given the complexity of the .rpm file in question.  The alien command usually works, at least if the app is simple enough.  VMware player is not simple.  I would have probably been better off if I had started with the tar.gz file.  There were obvious issues using the alien-generated .deb file, but I thought I had fixed them all.  Guess not...

At any rate, removing the app with Synaptic left bits *everywhere* that screwed up the installation of the VMware player from the Ubuntu repository.  So, I manually removed the leftover bits from the system (lots & lots of leftover bits), then did another Synaptic removal, followed by a Synaptic install of the 1.x version from the Ubuntu repository.

Success.  VMware player has loaded Damn Small Linux and it appears to work properly.

If I really need to upgrade from the old player (repository version) to the current version, I'll google for succesful installations by Ubuntu/Debian users.  It is working well enough for me, at least for the present time.

---

