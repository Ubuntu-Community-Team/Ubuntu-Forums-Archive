---
title: "Help - &quot;No Bootable Device&quot; out of sudden..."
date: 2017-12-29
forum: General Help
---

### Post by danriel on 2017-12-29
Hello

My Ubuntu was working just fine for months, but today out of sudden it said "No Bootable Device".
I don't understand. Is this a hard-disk failure ? What else could go wrong ?

I tried to repair it with Boot-Repair, it did its best but nothing changed.
Here's the report : [https://paste.ubuntu.com/26280442]("https://paste.ubuntu.com/26280442/")/

So what could I do now ?
Thank you guys!

---

### Post by QIII on 2017-12-29
Hello!

Before going too far, eliminate a common hardware issue from your list of possible causes:  check that the power and data cables are fully and securely connected.

---

### Post by danriel on 2017-12-29
Thanks for your reply. All seems to be ok with the hardware. 
The hard disk is fine too - I used I live Ubuntu system and I can see my files alright after entering the encryption password.

What next ? :)

---

### Post by oldfred on 2017-12-29
Report shows Secure Boot is on, but default boot (Linux HD)  is using grub not shim.
Shimx64.efi is the version of grub for Secure Boot?

You show both an unknown device and Ubuntu using shimx64.efi.

Have you tried with Secure Boot off, or manually selecting the other boot option in UEFI boot menu?
this shows details on UEFI boot options:
sudo efibootmgr -v

---

### Post by danriel on 2017-12-29
> **oldfred said:**
> Report shows Secure Boot is on, but default boot (Linux HD)  is using grub not shim.
Shimx64.efi is the version of grub for Secure Boot?

You show both an unknown device and Ubuntu using shimx64.efi.

Have you tried with Secure Boot off, or manually selecting the other boot option in UEFI boot menu?
this shows details on UEFI boot options:
sudo efibootmgr -v
Thank you ! 

I used **sudo efibootmgr -v** and it showed me the location of **shimx64.efi** . I then selected that file in the Bios and it worked.

Problem solved, computer booting normally. Thanks !!

:guitar:

---

### Post by ajgreeny on 2017-12-29
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

