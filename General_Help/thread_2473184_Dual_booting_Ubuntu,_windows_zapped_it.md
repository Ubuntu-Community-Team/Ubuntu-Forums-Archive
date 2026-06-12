---
title: "Dual booting Ubuntu, windows zapped it"
date: 2022-03-26
forum: General Help
---

### Post by supertechno2004 on 2022-03-26
Hi everyone, I was dual booting Ubuntu with windows, and Ubuntu worked great! Until I tried to boot into windows. Upon doing so, windows startup repair automatically started, and saw the new partition Ubuntu had created for itself, and thought there was a problem with my SSD, and began "fixing" the drive problems. Now whenever I try to boot to Ubuntu, it shows the splash screen for ubuntu, then goes to a black screen with a single line of text, "/dev/sda6: clean, 276551/1455328 files, 5544157/5817088 blocks". How can I get Ubuntu back?

---

### Post by yancek on 2022-03-27
What version of windows are you using?  What version of Ubuntu are you using?   Is this a UEFI install or Legay/CSM?

Windows will sometimes turn on Secure Boot in the BIOS firmware so check that.

Not knowing what you did to try to "fix" the problem will make it more difficult to resolve.  If you have an Ubunt DVD or USB with a live system and can connect to the internet, go to the site below and download boot repair using the 2nd option explained on that page and run it using the Create BootInfo Summary option and post the link you get when it finishes here.

 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by supertechno2004 on 2022-03-27
Gotcha. Here is the link it gave me:  [https://paste.ubuntu.com/p/QpHqsNS8KG/](https://paste.ubuntu.com/p/QpHqsNS8KG/)

---

### Post by oldfred on 2022-03-27
Try turning UEFI Secure Boot off.
> SecureBoot enabled but mokutil says: SecureBoot enabled 

You have UEFI hardware, and Windows & Ubuntu installed in UEFI boot mode.
But you somehow have the old BIOS boot loader for Windows in gpt's protective MBR. Just never try to boot in BIOS/legacy mode as it will not work.

Only if you installed Ubuntu in UEFI Secure Boot mode, would it work with Secure Boot on. And if you have nVidia proprietary driver, you have to create your own key with mokutil to verify it is secure. 

Windows may have run an UEFI update which resets some settings to defaults. Review all the settings you originally changed when you installed Ubuntu. One of those it turns on is UEFI Secure boot.

---

