---
title: "VirtualBox and USB on Gutsy"
date: 2007-11-13
forum: General Help
---

### Post by fantan on 2007-11-13
Dear Members,

I have several partitions on my computer. On the first one is running Feisty with VirtualBox, 
and the VB is seeing USB devices in it without problems.

When I've downloaded an installed from scratch the Gutsy on the second partition and installed the VirtualBox on it, and tried setup the VB, I've got the following error message:

"Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.
Result code: 
0x80004005
Komponents: 
Host
Interface: 
IHost {81729c26-1aec-46f5-b7c0-cc7364738fdb}
Callee: 
IMachine {31f7169f-14da-4c55-8cb6-a3665186e35e}"

The VirtualBox I've installed both on Feisty and Gutsy is non-OSE version, it is working on the Feisty fine.
In the Gutsy host, my USB devices are working fine but VirtualBox doesn't see them at all!

Can anybody help me? What on Earth is the Host USB Proxy Service, where to find, and how to download and install it?
Why the VB is working in Feisty without problems and why the same isn't working in Gutsy?

Please help me!

Thanks for andvance!

fantan

---

### Post by deeptingler on 2007-11-13
Go to the Virtualbox home page and click on the FAQ section where they have some info regarding USB on gutsy.....   Its a known issue they are planning to update. :)

---

### Post by fantan on 2007-11-13
Hi,

Thanks a lot! :)))))

fantan

---

