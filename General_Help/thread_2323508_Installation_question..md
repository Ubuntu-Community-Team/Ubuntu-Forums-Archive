---
title: "Installation question."
date: 2016-05-05
forum: General Help
---

### Post by nu2this2 on 2016-05-05
Hello,

My wife has a PC with windows 8 installed. Unfortunately it is slow and almost unusable due to malware, spyware and virus infection that Mcafee was unable to prevent. I would like to wipe the hard drive clean and install Ubuntu. Some one told me that there is now way to remove a virus from the HD. He maintains that it will finally destroy the drive . Is this true?

 If I use the Ubuntu installer and instruct to use the entire disc will this allow for a virus and other bad things to be totally removed and replaced with the new operating system?

Thanks for any help.

---

### Post by pfeiffep on 2016-05-05
> Some one told me that there is now way to remove a virus from the HD. He  maintains that it will finally destroy the drive . Is this true?I think your friend has grossly overstated some thing they really misunderstood!

Point your wife's PC to free  [Malware Bytes]("https://www.malwarebytes.org/")  and try to remove any malware

You should consult with your wife about any documents that she requires from her PC and save them.

If you have another PC available please download your Ununtu choice, burn it to USD or DVD. Power down your wife's PC then power up and select either USB or DVD from which to boot. Select try Ubuntu to insure all the hardware works. Once you've tested and are satisfied everything works you may choose install Ubuntu.

Post back with your progress

---

### Post by Portaro on 2016-05-05
Yes , if you install Ubuntu or other distribution on your disk the entire partition go to a new format and the present system is entirely deleted to clean all disk to new format and new install.

Some type of Virus , and malware in general can be extremely strong and resist to many methods to try to remove on a systems so this can be your case .

When you install a new system type in this case GNU/Linux Ubuntu you install a totally different system so for example if the format of partition of disk cant erase or delete some virus and if he continues on disk he cant do anything on new system because is totally diferent . But of course when you install a new system and format the disk the malware is totally deleted on disk and if you need you can install or reinstall windows 8 also without problems, many users suggest on the maintenace of systems and when need a format and new install do it with a step like use an Linux to format the disk to a type of Linx and then continues to a windows boot and reformat and install this.

So , in one word you can install Ubuntu easily, without any problem to your malware for windows and of course you can forget problems with malware in general for GNU/Linux because malware for this type of system is more problematic to maintain so your existence is less than in windows (.exe, bugs on private copyright code etc).

---

### Post by nu2this2 on 2016-05-05
Thanks for the information, that is very encouraging. My wife has nothing on her computer that requires saving, she only uses it for web browsing and email. So if I understand this correctly, I can install Ubuntu alongside windows 8 and since they are different operating systems have no concern that the malware and virus will corrupt the new installation?

My wife is somewhat knowledgeable with the program because, in the past,  she has occasionally used my laptop with Ubuntu 14.04 installed. One more question, can Skype be used with Ubuntu?

Thanks for any input.

---

### Post by yancek on 2016-05-05
A virus in relation to computers is a piece of executable software which does something the user does not want it to do.  Windows executables will not run on any Linux systems.  If your computer has windows 8 installed and you are going to keep it, I would suggest you read through the link below in detail before beginning because windows 8 is almost certainly using UEFI.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Bucky Ball on 2016-05-06
Enable the Canonical Partners repository, update, install Skype from Software Centre/Gnome Software, terminal or Synaptic, whichever you've got and suits you. No need to install from .deb or third-party site. If you have any issues with that, best post another thread to increase your chances of support as not related to your original question. :)

---

### Post by T.J. on 2016-05-06
> **nu2this2 said:**
> Thanks for the information, that is very encouraging. My wife has nothing on her computer that requires saving, she only uses it for web browsing and email. So if I understand this correctly, I can install Ubuntu alongside windows 8 and since they are different operating systems have no concern that the malware and virus will corrupt the new installation?

My wife is somewhat knowledgeable with the program because, in the past,  she has occasionally used my laptop with Ubuntu 14.04 installed. One more question, can Skype be used with Ubuntu?

Thanks for any input.

Good evening!

No, you have no need to worry about a Windows virus affecting Linux.  It is possible, at least in theory, that Windows malware could corrupt the drive's partition table, rendering both Windows and Linux unusable.  However, before you worry about such things, I feel compelled to mention that in my experience (25+ years as a technician/programmer), most people are too concerned about malware and viruses.  Can you get a virus?  Yes, certainly.  However, it is seldom a disaster, and if you take a few common sense steps - such making regular backups and not using an old copy of Internet Explorer, you have very little to worry about.

What most people call malware or a virus will be completely destroyed if you reformat the drive completely after booting the computer from a read only disc, such as a CD or DVD.  In most cases, simply reformatting and reinstalling your operating system is sufficient guarantee that you have disposed of anything unwanted.   

Yes, Skype can be used with Ubuntu - however, the existing version has not been updated by Microsoft for some time, so you may have a few problems, even using the version in the Partners repository.  If you need more details, please post back.

---

### Post by T.J. on 2016-05-06
> **nu2this2 said:**
> Hello,

My wife has a PC with windows 8 installed. Unfortunately it is slow and almost unusable due to malware, spyware and virus infection that Mcafee was unable to prevent. I would like to wipe the hard drive clean and install Ubuntu. Some one told me that there is now way to remove a virus from the HD. He maintains that it will finally destroy the drive . Is this true?



No. It is absolutely not true.  A complete erasure of the disc will destroy any virus or malware, regardless of what it is.  The EXTREMELY RARE exception might be if something gets embedded in the firmware, but an experienced technician can deal with that too.

(Just so you are aware, Mcaffee has an extremely poor track record, so poor that the company's founder is glad to no longer be associated with it. [http://www.reuters.com/article/us-ces-intel-mcafee-idUSBREA060YM20140107](http://www.reuters.com/article/us-ces-intel-mcafee-idUSBREA060YM20140107))

---

### Post by nu2this2 on 2016-05-06
Thanks to all, great feedback!

---

### Post by haplorrhine on 2016-05-06
> **T.J. said:**
> The EXTREMELY RARE exception might be if something gets embedded in the firmware, but an experienced technician can deal with that too.

and with that level of paranoia you might as well replace your [BIOS chip]("https://www.wired.com/2015/03/researchers-uncover-way-hack-bios-undermine-secure-operating-systems/"), [USB adapters]("https://www.wired.com/2014/07/usb-security/"), et cetera.

---

### Post by RobGoss on 2016-05-06
There's a lot of good advice given here and I would have to yes if you decide to install Ubuntu as the only operating system on this machine there should not be any files or viruses transfered over to the Linux os.

Just a quick note, I have a Windows 10 machine and I run Malwarebyte.org to keep my system free of Malware it does a great job removing most if not all item's that may cause a Potential Threat and I use the FREE version

I also follow it up with CCleaner which also removes unwanted files and keeps my system running smooth again another free product.

---

### Post by pfeiffep on 2016-05-06
> **nu2this2 said:**
> Thanks for the information, that is very encouraging. My wife has nothing on her computer that requires saving, she only uses it for web browsing and email. So if I understand this correctly, I can install Ubuntu alongside windows 8 and since they are different operating systems have no concern that the malware and virus will corrupt the new installation?

My wife is somewhat knowledgeable with the program because, in the past,  she has occasionally used my laptop with Ubuntu 14.04 installed. One more question, can Skype be used with Ubuntu?

Thanks for any input.You are correct that malware affecting Windows will **NOT** affect Linux. 
> However if you do plan on installing Ubuntu along side you should** make every effort to clean Windows** since this type of install does NOT wipe the hard drive.

---

