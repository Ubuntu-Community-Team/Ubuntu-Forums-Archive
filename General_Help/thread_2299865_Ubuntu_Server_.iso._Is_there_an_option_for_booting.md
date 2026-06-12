---
title: "Ubuntu Server .iso. Is there an option for booting and installation in UEFI?"
date: 2015-10-21
forum: General Help
---

### Post by mikodo on 2015-10-21
Hello everyone,

Like the title.

 There is no option for such with the minimal .iso. It would be great for my next install but, I want to try UEFI with my next Desktop Machine.

Thoughts. A Server install in UEFI. Install minimal Xfce, and load up with  VBox .vdi's including Ubuntu Unity for, watching the transition from  X11 > MIR & Apt > Snappy updates> over the five years from 16.04. Could be fun. :)

Ubuntu Minimal CD   [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[B]
*"Note:*[/B][I] While the minimal iso image is  handy, it isn't useful for installing on UEFI-based systems that you  want to run in UEFI mode. The mini iso lacks the proper files for  booting the computer in UEFI mode. Thus, the computer will boot in BIOS  compatibility mode, and the installation will be in BIOS mode". 
[/I]
Thank you.

---

### Post by Dennis N on 2015-10-21
Do you have the iso to examine? You can tell by looking at the files with archive manager. To be bootable and installable in UEFI mode, there should be a top-level folder EFI included. The attached screen shot is of Ubuntu MATE 14.10 iso. Note the EFI folder.

---

### Post by mikodo on 2015-10-21
Thank you, Dennis.

I apologize. I was reading over in Ubuntu-next ...

No, I don't have the Server .iso. I'll download the newest now.

But, I"ve  never seen the little guy so, can I poke around in it without a gui?

And, it will have to be written to a cd. No usb-boot.

---

### Post by Bucky Ball on 2015-10-21
Did you try doing some research about this online? There's plenty to say you can install the server version in UEFI mode ...

[Here's one]("http://ubuntuforums.org/showthread.php?t=2153123") from a user that could only install the server in UEFI.

PS: A mini.iso install is not a server install. It's a minimal install. Which do you want to do? Either appears to install with UEFI (I know the mini does). The procedure is pretty similar. Get online with an ethernet cable and fire away, making sure you have a good handle on what you're doing first and a plan. :)

---

### Post by v3.xx on 2015-10-21
The server iso fits on a CD.  I use it instead of the mini iso to install a terminal only (just like the mini iso) system.  Select F4 and choose minimal install.  It installs faster than the mini iso.

---

### Post by Dennis N on 2015-10-21
Once you have the iso, just right click on the file and select open with archive manager and you will get a window showing the contents (like the attachment in post #2).

---

### Post by mikodo on 2015-10-21
Thanks again.

EFI.

> **Bucky Ball said:**
> Did you try doing some research about this online? There's plenty to say you can install the server version in UEFI mode ...

[Here's one]("http://ubuntuforums.org/showthread.php?t=2153123") from a user that could only install the server in UEFI.

PS: A mini.iso install is not a server install. It's a minimal install. Which do you want to do? Either appears to install with UEFI (I know the mini does). The procedure is pretty similar. Get online with an ethernet cable and fire away, making sure you have a good handle on what you're doing first and a plan.
No Bucky. I didn't search. :( I know better.

I am a little  confused by that quote I posted in the first post about with the mini  .iso not being able to boot or install in UEFI. But, I believe you. I will  search online.



> **v3.xx said:**
> The server iso fits on a CD.  I use it instead of the mini iso to install a terminal only (just like the mini iso) system.  Select F4 and choose minimal install.  It installs faster than the mini iso.

Thanks, for that!

Whatever turns up, turns up.

It looks positive I can do this.

Thanks.

Alright.

The OP in [this]("http://ubuntuforums.org/showthread.php?t=2188353") thread, ran into this situation when he wanted an UEFI install from the mini .iso. He even linked to the same page I did that, states the mini .iso cannot install to UEFI. It appears the mini.iso is missing the grub-efi package. Oldfred suggests installing the grub-efi package as a solution. Or, as the OP found with Boot-repair, it would uninstall grub-pc and install grub-efi. 

I downloaded the Ubuntu Server 14.04.3 .iso and the Ubuntu 14.04 LTS .iso. Both have the same EFI and Boot folders and entries in each. The Ubuntu mini .iso on the other hand, only has the Boot folder and, it has less in that, than the Boot folders in the other two.

So, I am left to surmise without trying it yet, that I may have less trouble/work using the Ubuntu Server .iso than I might, with the Ubuntu mini .iso to, have a working UEFI firmware (not BIOS) and an UEFI install.

The best I can do.

Thanks, everyone.

---

