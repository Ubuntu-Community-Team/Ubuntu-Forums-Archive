---
title: "Using scanner needs root permissions"
date: 2013-10-12
forum: General Help
---

### Post by Nick Payne on 2013-10-12
Machine is running 13.04 amd64. I have two USB scanners connected, an Epson 2450 and a Canon 9000F Mark II. If I have both scanners powered on and run vuescan as myself, vuescan only sees and uses the Epson 2450 scanner. If I run vuescan as root, I can see and use both scanners.

sane-find-scanner has the same problem - running ***sane-find-scanner*** only finds the Epson, whereas running ***sudo sane-find-scanner*** finds both the Epson and Canon scanners.

My userid is a member of the scanner group. What do I need to change in order to be able to use either scanner without needing root permissions?

---

### Post by Nick Payne on 2013-10-19
Well, to answer my own question, the solution (for VueScan) was to add a rules file in /etc/udev/rules.d:
```
gksu gedit /etc/udev/rules.d/99-local.rules
```
Add the following content to the file
```
SUBSYSTEM="usb_device", ACTION="add", GOTO="canon_rules_end"

# Canon CanoScan 9000F Mark II
ATTR{idVendor}="04a9", ATTR{idProduct}="190d", SYMLINK+="scan-canon", MODE="0666", OWNER="nick", GROUP="scanner"

LABEL="canon_rules_end"
```
The vendor id and product id are those shown for the scanner by lsusb
```
Bus 002 Device 005: ID 04a9:190d Canon, Inc.
```
I rebooted and VueScan under my userid could see both scanners.

---

### Post by tim-tavares on 2014-01-09
Thanks for the post. I followed your instructions and got my Canon 9000F Mark II and VueScan working on 64bit Kubuntu 13.10. Much appreciated.

---

