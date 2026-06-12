---
title: "Ubuntu 22.10 / Windows 11 error UEFI"
date: 2022-12-03
forum: General Help
---

### Post by franvalles on 2022-12-03
Hello. I'm going to try to write a little because I don't speak English.
I have Windows 11 and Ubuntu 22.10 installed.
I updated BIOS (ASUS) and I have Nvidia RTX 2070.
When updating, an error appears in UEFI recording and constantly restarts ubuntu. I think the TMP blocks UEFI.
Happens when updating Nvidia driver.

How can I solve?

Thanks.

---

### Post by oldfred on 2022-12-04
Do you have UEFI Secure Boot on?
Often easier to have it off when you use proprietary drivers & are a new user.
If one you have to sign (MOK - machine owner key) the proprietary driver yourself.

[https://wiki.ubuntu.com/UEFI/SecureBoot/DKMS](https://wiki.ubuntu.com/UEFI/SecureBoot/DKMS)

---

### Post by grahammechanical on 2022-12-04
> When updating, an error appears in UEFI recording and constantly restarts ubuntu.

What was the error? Do you see it every time you boot? 

> I think the TMP blocks UEFI.

Do you mean the TPM (Trusted Platform Module)?

The purpose of the TPM chip is not to block the UEFI but to give Microsoft Windows the possibility to block untrusted software. 

[https://uk.pcmag.com/components/134144/what-is-a-tpm-and-why-do-i-need-one-for-windows-11](https://uk.pcmag.com/components/134144/what-is-a-tpm-and-why-do-i-need-one-for-windows-11)

Can you load Windows 11? Do you get a Grub boot menu with both Ubuntu and Windows listed in the menu?

Regard

---

