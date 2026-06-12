---
title: "Shuts down instead due to idle when box being used"
date: 2007-04-29
forum: General Help
---

### Post by Rob_Quads on 2007-04-29
Previously my machine would go into standby if there was nothing happening on the box. The discs would spin down if they are not busy.

Since upgrading to Fesity a number of times I have been ssh'ed into the machine and then it will just shut it self down. I have also noticed that my ide drives are not going to sleep. Looking at the logs show the following

```

Apr 29 12:10:45 FileServer gnome-power-manager: (convery) Suspending computer because System idle
Apr 29 12:10:45 FileServer gnome-power-manager: (convery) cannot suspend as not allowed from policy
Apr 29 12:10:45 FileServer gnome-power-manager: (convery) suspend failed
Apr 29 12:10:46 FileServer kernel: [  748.476000] ACPI: PCI interrupt for device 0000:00:0a.0 disabled
Apr 29 12:13:34 FileServer kernel: [  750.464000] Disabling non-boot CPUs ...
Apr 29 12:13:34 FileServer kernel: [  750.464000] Stopping tasks ... done.
Apr 29 12:13:34 FileServer kernel: [  750.672000] Shrinking memory...  ^H-^Hdone (0 pages freed)
.....

```

I also find that I cannot wake the machine using a WOL packet which used to work

Below is my /etc/default/acpi-support file

```

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
#ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=standby

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
POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

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

Surely the Gnome manager which is putting the machine into standby would detect I am logged in and working as it did previously?

Also not sure what the message about "not allowed from policy" is all about?

---

