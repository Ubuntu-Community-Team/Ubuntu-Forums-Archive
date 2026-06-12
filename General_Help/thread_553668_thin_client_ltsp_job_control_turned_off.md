---
title: "thin client ltsp job control turned off"
date: 2007-09-18
forum: General Help
---

### Post by jmaryinchina on 2007-09-18
I have installed edubuntu from the Desktop CD inside a VMWARE virtual machine.
Then I have configure an LTSP environment in it. 
The scope is to simulate a thin client boot with this server. So i have set up a second VMWARE virtual machine with 128M and diskless.
I have twicked a little the file /etc/ltsp/dhcpd.conf according to the network config of the VMWARE edubuntu server.
My thin client client using PXE, find the kernel and so on. Even the graphical screen showing the progress bar of the loading system appears.

That progress bar stop after 3mm, then 2 minutes after it appears :

[FONT="Courier New"][COLOR="Sienna"]BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)[/COLOR][/FONT]

I guess this as something to do with initramfs process but I really don't know what to do. Nothing in the litterature I found is relevant.

What is strange also, is that the first time I booted the virtual thin client, it has worked showing me graphical login screen (in low color depth) and at trying to log in it just has suddenly crashed.

Hope somebody can give directions.

---

### Post by splintercellguy on 2007-09-18
Try booting with kernel option all_generic_ide? What's the IDE configuration of your virtual devices?

---

### Post by jmaryinchina on 2007-09-18
My virtual machine is configured with the following options concerning ide :

ide1:0.present = "TRUE"
ide1:0.deviceType = "cdrom-raw"
ide1:0.startConnected = "TRUE"
ide1:0.fileName = "auto detect"
ide1:0.autodetect = "TRUE"

What should I modify to  try booting with kernel option all_generic_ide ?

---

