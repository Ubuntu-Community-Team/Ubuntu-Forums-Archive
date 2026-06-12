---
title: "Ubuntu 24.04 showing Linux Kernel Verification Error (RED X) under Device Security"
date: 2024-10-31
forum: General Help
---

### Post by vw16v on 2024-10-31
Hello, while looking into another issue I'm having I noticed under my Device Security I have the following message. It shows a red X instead of a green check mark for the Linux Kernel Verification.
Here's my release info and kernel build.
```
Distributor ID:    Ubuntu
Description:    Ubuntu 24.04.1 LTS
Release:    24.04
Codename:    noble

uname -a
Linux yoga9i 6.8.0-47-generic #47-Ubuntu SMP PREEMPT_DYNAMIC Fri Sep 27 21:40:26 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux
```

Looking back in the Device Security screen the last time it showed a Green Check mark for  Linux Kernel Verification was as recent as 2024-10-17 when it had a green check mark (and still does).
I am not sure what might of occurred on Oct 18th to cause this to change to Red X with the following message.

"Linux Kernel Verification makes sure that critical system software has not been tampered with. Using Device drivers which are not provided with the system can prevent this security feature from working correctly. This issue could have been caused by an operating system configuration change, or because of malicious software on this system."

Thanks for any input or expertise on this concern.

---

### Post by grahammechanical on 2024-10-31
Until I read your post I have never looked at System Settings>Privacy & Security.

You are not alone. I also have the same message and a warning that secure boot is off and a further warning that my hardware does not pass checks. It is my guess that someone had a good idea to come up with a scheme that put computer hardware security to the test. I also think that very few computer devices would meet the tests devised. Devices are just not designed for security. That is my opinion.

The utility does offer an option to Copy Technical Report. It is copied to the clipboard and can them be pasted into a text editor to be read and saved. There is a link at the end of the report.

[https://fwupd.github.io/libfwupdplugin/hsi.html](https://fwupd.github.io/libfwupdplugin/hsi.html)

There is a lot of reading in this report.

> For instance, a user might say that for home use any hardware the bare minimum security level (HSI:1) is *good enough*. For a work laptop the company IT department might restrict the choice of models to anything meeting the criteria of level HSI:2 or above. A journalist or a security researcher would only buy level HSI:3 and above. The reality is that HSI:4 is going to be more expensive than some unbranded hardware that is rated HSI:0

Regards

---

### Post by vw16v on 2024-10-31
Thanks for the reply and confirmation @grahammechanical. I was thinking it might be due to running Oracle Virtualbox. I just noticed this message with the kernel has been showing up for a long time. It's been showing the Kernel Verification good on and off for as long as I've had Ubuntu installed alongside Windows for a few years. I went from 22.04 to 24.04 a few months ago. I don't necessarily have any reason to think it's anything malicious which is the main reason I posted this. I also generated that report to look into. Also, my secure boot shows good/active here with UEFI Secure boot checked. I'll look into your post to read up! I just like to try and keep my OS as secure as possible.

FYI: My report shows this 0 security level! So, that might be bad huh?
  OS:                                              Ubuntu 24.04.1 LTS
  Security level:                                  HSI:0! (v1.9.24)

The only reason I appear to not be on HSI:1 is because of this fail
  Intel Management Engine Version:               ! Fail (Not Valid)

I'm not sure how much of a difference it would make to try to get this fixed to get to HSI:1 in terms of security. It appears this is all tied to UEFI and BIOS stuff. I should be on the latest BIOS update for my laptop. I might double check that also.

---

### Post by grahammechanical on 2024-10-31
Some of these tests cannot be met by the ordinary user but may be important to a machine being used for security sensitive work. My laptop failed, among other things, with 

> Suspend To RAM:                                ! Fail (Enabled)

Suspend to RAM is feature of the operating system. Hibernation is suspend to disc. Ubuntu does not do that because suspend to disc would use the swap partition but Ubuntu now uses a swap file.

This thread become an interesting discussion. What comes to mind is the security vulnerabilities of Windows XP and how government departments continued using Windows XP even after Microsoft stopped supporting XP.

Tests like this are necessary.

Regards

---

### Post by vw16v on 2024-11-01
Great information on this grahammechanical. I did some more research and found out the Windows Lenovo tool that I used to upgrade my BIOS in the past no longer shows new BIOS. I found two new BIOS on Lenovo's website. One of them has the Intel Management Engine. I'll probably apply that BIOS update first and then run this test again. I'm anticipating that might allow me to get to HSI:1. It might be a little while before I do this since I want to backup my system first.

---

### Post by vw16v on 2024-11-04
Quick update. I installed the latest Intel Management Engine provided by Lenovo using the Windows installation. It went through and now Linux shows me passing the Intel Check. I'm hoping this allows me to get toHSI:1 security level. However, I have re-enable Secure Boot since I turned it off during the update. Per the report>
  Intel Management Engine Version:                 Pass (Valid)
  Intel Management Engine Manufacturing Mode:      Pass (Locked)
  UEFI Secure Boot:                              ! Fail (Not Enabled)
  Firmware Write Protection:                       Pass (Not Enabled)
  TPM Platform Configuration:                      Pass (Valid)
  Intel Management Engine Override:                Pass (Locked)

I'll report back after applying the most current BIOS and re-enabling secure boot, etc.

---

### Post by vw16v on 2024-11-04
I'm very happy to report I'm officially on HSI:1! security level after applying the Lenovo Intel Management Engine update to my laptop. I also flashed to the latest BIOS for good measure.

  Processor:                                       11th Gen Intel(R) Core(TM) i7-1185G7 @ 3.00GHz
  OS:                                              Ubuntu 24.04.1 LTS
  Security level:                                  HSI:1! (v1.9.24)

Happy days!

---

