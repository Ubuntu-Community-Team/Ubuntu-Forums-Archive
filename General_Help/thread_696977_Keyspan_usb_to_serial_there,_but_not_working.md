---
title: "Keyspan usb to serial there, but not working"
date: 2008-02-14
forum: General Help
---

### Post by tamray on 2008-02-14
I am trying to get my keyspan usa-19qw usb to serial adapter working in minicom. It shows up with lsusb:
Bus 001 Device 006: ID 06cd:0118 Keyspan USA-19QW PDA
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  


dmesg shows:

[10271.604000] usb 1-1: new full speed USB device using uhci_hcd and address 6
[10271.752000] usb 1-1: configuration #1 chosen from 1 choice


grep CONFIG_USB_SERIAL_KEYSPAN /boot/config-2.6.22-14-generic
# CONFIG_USB_SERIAL_KEYSPAN is not set
CONFIG_USB_SERIAL_KEYSPAN_PDA=m

Is there something else I need to turn on or configure in order to get it to work with minicom.?

---

### Post by srankin1826 on 2008-02-14
From the keyspan website:

 Linux Kernel 2.6.x
If you are using a kernel v2.6, Keyspan firmware and drivers are in the 2.6.x. Please note that you may need to recompile your kernel if you did not install the Keyspan drivers when you first installed Linux.

Note:
Linux 2.6 includes full support for Keyspan USB Serial Adapters. In most installs, our drivers (and where needed, firmware) are installed. For most Linux distros (ie Redhat FC6), Keyspan support is enabled by default and your Keyspan USB Serial Adapter will work without you doing anything.

However, certain Linux distros (primarily Ubuntu and Debian) choose to not include a complete install of our drivers and firmware due to philosophical issues with our license text. Although the majority of the Linux community is fine with our license, Ubuntu and Debian require you to install the Keyspan drivers manually. This usually involves downloading the latest Linux kernel for kernel.org and patching or recompiling your kernel to include the complete Keyspan installation. Keyspan does not have instructions for this process at this time. We recommend that you use other distros (such as Redhat). In the future, Keyspan may create documentation to help you in updating Ubuntu and Debian however this documentation is not available at this time.

---

### Post by tamray on 2008-02-14
I went there originally and read the documentation. However, I was not sure if it was up to date, and thought there might have been some changes since Ubuntu finds the adapter, and has a module in the kernel. Seems like it should work then????

---

### Post by wirelessmonkey on 2008-02-14
I had lots of trouble with minicom, try using gtkterm, run it from the command line, and see if it gives you any errors.

---

### Post by tamray on 2008-02-14
Thanks for the recommendation. Still can't get the Keyspan adapter working, but I got another one working, using gtkterm.

---

