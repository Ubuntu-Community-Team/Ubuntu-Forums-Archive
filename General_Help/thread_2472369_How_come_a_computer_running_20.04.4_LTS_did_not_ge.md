---
title: "How come a computer running 20.04.4 LTS did not get the latest kernel ?"
date: 2022-02-25
forum: General Help
---

### Post by georgesgiralt on 2022-02-25
Hello Guys,
I own two computer (a desktop, the culprit here, and a laptop). Both run Ubuntu 20.04.4 LTS with all updates applied. 
The laptop has the 5.13 kernel, proper Gnome version and tutti quanti.
The desktop, on the other hand has all but the kernel which is stuck to 5.4.0-100. And I wonder why ? 
Both machines have an Nvidia card with proprietary driver, the desktop has an old Asus mobo with an Intel 4th gen proc, and no exotic hardware. So I'm puzzled. 
So I'll enjoy hearing from you. 
Thank in advance for your help. 
Have a bright day.

---

### Post by Bashing-om on 2022-02-25
Hello georgesgiralt

The Ubuntu LTS enablement stacks provide newer kernel and X support for existing LTS releases, see 
               [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Depending on when and the .iso that you used to install is what the kernel series is.
A 20.04/1 installs are the 5.4 series - with the .2 release is the 20.10 stack .

-hope this helps-

---

### Post by georgesgiralt on 2022-02-25
Thank you for your answer. 
None where installed from an ISO. Both where updated from 18.04 (and 16.04 previously...) So both should have the same kernel. One has been updated at every kernel change. The other not. I wonder why and how could I change to have the latest kernel.

---

### Post by rsteinmetz70112 on 2022-02-25
I think it matters when you upgraded as well. A later upgrade will get a later version of the release.

---

### Post by georgesgiralt on 2022-02-25
I doubt that. On my laptop, the oldest kernel is linux-image-5.4.0-29-generic and the newest is linux-headers-5.13.0-30-generic. 
On the desktop, linux-image-4.15.0-29-generic for the oldest and linux-image-5.4.0-99-generic. 
So the laptop has been updated and the desktop also. My question is why one had been stopped from getting the latest versions ?

---

### Post by Impavidus on 2022-02-25
New kernels are pulled in by updates to the kernel metapackages. On one system, you must have the package linux-generic installed, which pulls in kernels of the 5.4 series, currently at 5.4.0-100; on the other system, you must have linux-generic-hwe-20.04, which pulls in the hwe kernels, currently at 5.13.0-30. If your hardware isn't very recent (and it doesn't look like that), there's no reason to run the 5.13 kernel. The 5.4 kernel is more stable, but that doesn't mean the 5.13 kernels are bad. It just means that you get a completely new kernel every 6 months and occasionally those break thing (in particular in combination with proprietary drivers).

A release upgrade from a previous release of Ubuntu would normally put you on the GA kernels (that is, the 5.4 series). I don't know what could have happened to put you on the hwe kernels, apart from a fresh install or you asking the package manager to install it.

---

### Post by georgesgiralt on 2022-02-25
I'm surprised one computer has HWE and the other not. I thought that HWE was "on the path" for LTS releases. I thought that during it's lifecycle, an LTS release received an HWE stack of update to be on par with the other non LTS releases. Now, you get me more confused saying that I may have specified an installation of an HWE stack ? Could it have been installed as part of a proprietary driver install (say Nvidia ) ? 
The plot thickens....

---

### Post by grahammechanical on 2022-02-25
This is how I understand things:

If we install Ubuntu 20.04.0 or 20.04.1 we get the 5.4 kernel which is supported for the full 5 years of the LTS release (April 2025). Some users prefer the situation to be like that. If we install Ubuntu 20.04.2 or later we get a later kernel that only has about 6 months support and is then automatically upgraded to the next kernel to be released.

The 5.13 kernel is not supported until April 2025. So, we upgrade to 22.04.0 a few months after it is released. I further understand that if we are running Ubuntu 20.04 with the 5.4 kernel then at some point we will be invited to install the 20.04 Hardware Enablement Stack (HWE). Decline that invitation and we remain on the 5.4 kernel. Accept the invitation and we move on to 5.8 kernel and then 5.11 kernel and 5.13 kernel.

I am guessing that in this user's case the desktop machine has not had the HWE stack installed but the laptop has had it installed or the version installed on the laptop was Ubuntu 20.04.2 or later.

Regards

---

### Post by TheFu on 2022-02-25
My experience is that HWE kernels don't get installed, until I actually run the specific commands to make that happen.

---

### Post by georgesgiralt on 2022-02-27
I've done some forensic analysis. 
I've found that the first "HWE" occurrence in the apt logs came with the install of a meta-package for hardware support for my laptop. Precisely : oem-sutton.simon-meta:amd64 and oem-sutton.simon-camille-meta:amd64
So maybe this explains the hwe kernels ? 
Anyway, as this problem is not causing any harm, I'll leave this as it is. The desktop has an old mobo and no driver problem and the laptop has less problem with the OEM support but still a lot of ACPI problems. Lenovo has a lot on it's plate fixing them and seems not involved solving them.
Thanks a lot to all of you for your help. It explained a lot to me.

---

### Post by Bashing-om on 2022-02-27
georgesgiralt; Hello 

while off topic of this thread - 
for ACPI problems you will find:
[http://iam.tj/prototype/enhancements/Windows-acpi_osi.html](http://iam.tj/prototype/enhancements/Windows-acpi_osi.html)
most instructive. The DSDT change may do a world of good,

[INDENT][INDENT]good things can happen
[/INDENT][/INDENT]

---

### Post by georgesgiralt on 2022-03-01
Thank you, Bashing-om for your pointer. 
I knew the acpi-osi parameter having used it a long time ago on a laptop but had long forgotten it. I've played with it but the dmesg acpi output lost only 5 lines, dropping from 368 to 363... The battery charge threshold and or charge command is still non functional and the Bluetooth card sometimes off at boot or return from sleep is still here...  
I'm somewhat sick of those computer manufacturers stating that their machines are "fully supporting Linux" and having half of it not working.... I think we should make some pressure on Insyde for them to correct their firmware .... 
As per the initial problem, I'll let the kernel versions where they are. On the laptop it may be useful and on the desktop, the actual kernel is sufficient. We'll see when 22.04 comes out ! 
Have a nice and bright day !

---

