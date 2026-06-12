---
title: "Can't resume from Suspend/Hibernate"
date: 2006-11-12
forum: General Help
---

### Post by touchlikefire on 2006-11-12
[FONT="Tahoma"]I am unable to resume from either suspend or hibernate.  When I suspend to RAM the system goes down to sleep, but when I resume I hear everything go live but the screen.  The screen comes up blank for about ten seconds, and then the monitor says "no signal" and goes into low power mode.  Hibernate does the same, except the screen displays something about "pnp cannot activate 00:0a" followed by "pnp cannot activate 00:0b" and I'm forced to hard reset (I don't remember the exact text).

Also, my computer is capable of suspend to RAM and uses ACPI, verified by a command I was told to enter at the terminal.

I've searched around the forum and internet, but nothing I've come across or tried has had any effect.  I changed some settings in **/etc/default/acpi-support** according to a few threads.  Here is the output:

```
# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

# Save and restore video state?
SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
DOUBLE_CONSOLE_SWITCH=false

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=platform

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
 DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false
```

Can somebody please explain to me how to get Suspend (and hibernate) working?

____________
Dell Dimension 4500 (BIOS A03)
Intel Pentium 4 (2 GHz)
Ubuntu Edgy (6.10)
kernel 2.6.17-10-generic
Nvidia GeForce MX 420 (driver: nvidia?)[/FONT]

---

### Post by kishd on 2006-11-12
Had a similar problem on Edgy. I installed hibernate with synaptic. run hibernate as root and it seems to work better than the built in options.

---

### Post by touchlikefire on 2006-11-13
Okay, I've downloaded "hibernate" (which I think is a bit of an ambiguous name for a program).  Is there a GUI (at least to configure it)?  I perused the terminal output very briefly, but couldn't make much out of it's suggestions.

How should I configure the script to suspend and hibernate my machine?

---

### Post by touchlikefire on 2006-11-14
I tried configuring the "hibernate" script several different ways, but I cannot get it to work.  I am still new to linux, and I don't know what I'm doing (particularly with this script).  Please advise.

Secondly, some news on the built in "suspend" function: I changed some settings in **acpi-support**, and I've gotten the machine to suspend and resume from the *login* screen.  This is not to be confused with actually getting it to work once I'm logged in; it still won't resume once I'm at my desktop, but now it won't suspend in the first place either.  What follows is the modded **acpi-support** file:

```
# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES="networking rt2500 network"

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

# Save and restore video state?
SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
DOUBLE_CONSOLE_SWITCH=false

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=platform

# Comment this out to disable screen locking on resume
#LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
 DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false
```

The reason I blacklisted those modules (which may not even be correct syntax or module names) is because I suspected networking to be an issue resulting from the out put of:
```
prizzle@skunk:~$sudo hibernate
```

I also do not know if I can repeatedly suspend and resume from the login screen, which I only bring up because I've read in other posts that even with suspend working, some people cannot resume more than one time.

How should I proceed to get suspend to work?

---

### Post by joe056 on 2006-12-12
My system does the same thing (it powers up, but it doesn't actually come back on) when I resume from suspend and hibernate.  I get the error message when I return from Suspend mode:

```
pnp: failed to activate device
```

Hope this helps.

---

