---
title: "MokManager and Shim wrong output for Secure Boot State"
date: 2018-06-10
forum: General Help
---

### Post by sbakic on 2018-06-10
Good day guys, I am new here on this forum as well in linux. I got some questions related to Secure Boot, shim, mokutil. 

So I read a little about how SecureBoot works with Linux. I understood that the process of booting linux, in short, is in this way. UEFI (Secure Boot) -> shim loader -> MOK or GRUB2 -> linux kernel. I am stuck with secure boot and trusted keys for proprietary  drivers as nvidia. But this is not only the problem I got two.

1. Problem
I as understood there is shim state for secure boot and I want to have it enabled.
I did next commands.
*$ sudo mokutil --enable-validation* -> reboot set in mok manager boot enabled-> reboot-> no insecure boot text

Everything looked fine but when I check it with:

*$ mokutil --sb-state*
SecureBoot disabled

and even with this command (I found somewhere that it says if first line finishes with 1, shim secure boot is enabled if it's 0 shim secure boot is disabled)

*$ hexdump /sys/firmware/efi/efivars/SecureBoot-8be4df61-93ca-11d2-aa0d-00e098032b8c*
0000000 0006 0000 0000                         
0000005

So problem is that it doesn't show message at boot that it's booting in insecure mode, but when I check through mokutil it says secureboot is disabled. How to fix that?

2. Problem
I need to add PKC#7 trusted key for nvidia drivers I am reading this right now so i I run to any problem i will ask here.

Thanks for you reading. Have a nice day.

---

### Post by mörgæs on 2018-06-11
> **sbakic said:**
> I am stuck with secure boot and trusted keys for proprietary  drivers as nvidia.

I believe it's the other way around. If you disable Restricted Boot in BIOS and install Ubuntu then you should be able to add any driver you like.

---

