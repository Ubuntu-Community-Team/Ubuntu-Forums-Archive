---
title: "Soft remove usb device"
date: 2016-01-29
forum: General Help
---

### Post by KillerKelvUK on 2016-01-29
NOTE:  This is not a virtualisation question...

So I run several vm's using KVM and some of them I use vfio for PCI passthrough.  One of my vm's is a phone server and I have a PCI card in my machine that connects it to the phone line, the problem is that this PCI card doesn't support INTx remapping and needs a dedicated Interrupt to operate.  However my hardware always puts the PCI card onto an interrupt that a usb port is also using so when I try and start the vm i get an error as the PCI card cannot map the full interrupt blah blah.

Prior to upgrading to 15.10 I was able to soft remove the conflicting usb port (see forum thread [http://ubuntuforums.org/showthread.php?t=2299835&p=13393624#post13393624](http://ubuntuforums.org/showthread.php?t=2299835&p=13393624#post13393624) for more detail) however since upgrading I'm getting an error and strange behaviour.  Before I raise a bug report I was wondering whether the process has changed in 15.10 which is why my solution no longer works?

When attempting to start the VM i get the below error output...

```

dmesg | grep genirq
[417232.321862] genirq: Flags mismatch irq 16. 00000000 (vfio-intx(0000:08:00.0)) vs. 00000080 (ehci_hcd:usb3)
```

```

cat /proc/interrupts | grep 16:
16:         31          0          0          0          0          0          0          0  IR-IO-APIC  16-fasteoi   ehci_hcd:usb3

```

```
root@blackserver:/sys/devices/pci0000:00/0000:00:1a.0/usb3# echo -n 1 > remove
bash: echo: write error: Invalid argument
```

Direct after the above command I get a dmesg output of "usb 3-1: USB disconnect, device number 2", so the command did something but not the same as pre 15.10 and my vm still won't start.

Any pointers appriciated?

---

### Post by KillerKelvUK on 2016-01-30
[COLOR=#111111][FONT=Ubuntu]SOLVED: moved the command back one level...[/FONT][/COLOR]

```
root@blackserver:/sys/devices/pci0000:00/0000:00:1a.0# echo -n 1 > remove
```
[COLOR=#111111][FONT=Ubuntu]
dmesg output now...[/FONT][/COLOR]

```
[65207.355668] ehci-pci 0000:00:1a.0: remove, state 4
[65207.355680] usb usb3: USB disconnect, device number 1
[65207.355682] usb 3-1: USB disconnect, device number 2
[65207.360110] ehci-pci 0000:00:1a.0: USB bus 3 deregistered
[65207.475341] iommu: Removing device 0000:00:1a.0 from group 7
```

[COLOR=#111111][FONT=Ubuntu]No other error messages and the USB controller is no longer listed in lspci or devices shown in lsusb.[/FONT][/COLOR]

---

