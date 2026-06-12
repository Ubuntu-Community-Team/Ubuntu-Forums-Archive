---
title: "Trouble with Monitor when connected to a KVM"
date: 2007-02-27
forum: General Help
---

### Post by Grax on 2007-02-27
I have a Dell PowerEdge SC1425, that I have connected to a KVM.  The OS installed is Ubuntu 6.06.  When I select the computer on the KVM, the monitor flickers and quickly displays the screen, does this a few time and then the monitor goes into sleep mode as if it had nothing to display.

If I unplug the KVM and go directly to the Monitor it works fine.  I know it's not the KVM, as I've tried two different KVMs and different cables.

I had this same issue when installing the OS, when the CD booted into the menu, I couldn't see it until I went around the KVM.

When I boot into XP, the system works fine with the KVM.

What can I do to correct this?  The system works fine when connected to the KVM, I just can't use the console, I have to SSH in.

Any help would be appreciated!

Thanks,

Andrew

---

### Post by tgalati4 on 2007-02-27
I have a 4-way IOGear KVM that I rotate between 2 Dapper machines, Dynebolic or DSL, and Windows XP Pro.  I've never had any problems.  I know that if boot a distro with the monitor switched out, then you will have problems because the hardware detection requires that the monitor be detected. 

In Linux this is normally not a problem because we boot so infrequently.

Can you boot with a direct monitor connection and then switch to KVM and have it work properly?  If so, then that is your work around.  And don't reboot too often.  Also, go into the Monitor On Screen setup and turn off the power saving mode.  Let the software handle it.

It could also be an interrupt problem.  In BIOS, turn off your parallel port, usb ports, serial ports, floppy drive, and Plug N Play Operating system.  Then see if the KVM behavior changes.

Is this a USB-keyboard KVM?  Perhaps the USB hotplug is causing a timeout and you need to tell the Xserver that you are running a USB keyboard (as opposed to PS/2 style)

I'm out of ideas.  (But not beer.)

---

### Post by Grax on 2007-02-28
FYI, I'm not using any X app...  This is in command line only mode.

The KVM is a PS2 setup.

Andrew

---

