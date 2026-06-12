---
title: "Clear deleted operating systems from Grub Menu"
date: 2022-07-07
forum: General Help
---

### Post by SUPERFITTER on 2022-07-07
How do I clear deleted operating systems from Grub Menu?  I tried     sudo efibootmgr -b (The system I wanted removed} -B.   
That did not work. 
I tried Boot Repair with a CD, that did not work either.

Thank You

---

### Post by #&amp;thj^% on 2022-07-07
Boot Repair???? any way if I understand you correctly.
I hate it when a PPA is needed, but this one has a good track record.
The link will guide you through it: [https://www.addictivetips.com/ubuntu-linux-tips/remove-broken-grub-boot-entries-on-linux/](https://www.addictivetips.com/ubuntu-linux-tips/remove-broken-grub-boot-entries-on-linux/)

---

### Post by grahammechanical on 2022-07-07
What have you done to remove those unwanted operating systems from your computer? I have often removed unwanted operating systems by deleting the partition they were on and then running

```
sudo update-grub
```

That command detects what OS are on the machine and then re-writes the Grub menu.

Removing unwanted entries from the UEFI settings is another matter. Removing unwanted boot files from the EFI boot partition is also another matter. But you did ask about the Grub menu.

Regards

---

### Post by oldfred on 2022-07-07
You have UEFI & grub as menus.
You already used efibootmgr to remove UEFI entry.

Make sure your existing installs do not use "ubuntu" or "grub" as entries as removing that ESP folder or UEFI entry, may remove you current install's entries.
You may need to remove folder in /EFI/xxxx as grub may both look there, typically for Windows entries, or in every partition for boot files.

I turn off os-prober, and add only the entries  I want into 40_custom.

Do you still have the system you want to delete installed?
Post link to Summary report from Boot-Repair, if you need more detailed info on what to remove.

---

### Post by mIk3_08 on 2022-07-08
> **SUPERFITTER said:**
> How do I clear deleted operating systems from Grub Menu?  I tried     sudo efibootmgr -b (The system I wanted removed} -B.   
That did not work. 
I tried Boot Repair with a CD, that did not work either.

Thank You
In my opinion I prefer to remove the hdd/ssd storage then plug it into another computer system devices then locate which copy that is needed to be remove. Regards and cheers.

---

### Post by dragonfly41 on 2022-07-08
You could try Grub Customizer tool.
I admit that I don't use it but on launching I can right click on elements and perform various operations.

---

### Post by ajgreeny on 2022-07-08
> **dragonfly41 said:**
> You could try Grub Customizer tool.
I admit that I don't use it but on launching I can right click on elements and perform various operations.

I recommend that you **do not use grub-customiser** as it makes many changes to grub that are not easily reversed to get back to the standard.

Boot-repair [boot-info script]("https://help.ubuntu.com/community/Boot-Repair") will tell us a lot more about your system and what is currently installed, and as oldfred says, should give us a lot more detail, allowing better advice.

---

### Post by dragonfly41 on 2022-07-08
> 
I recommend that you do not use grub-customiser as it makes many changes to grub that are not easily reversed to get back to the standard.


If that is the case then I suggest installing rEFInd which (for me) offers the flexibility I want. It does not interfere with the existing GRUB installation.

And if I *were* to attempt try Grub Customiser I would simply backup the /boot directory to restore original boot if experiment fails.

P.S. At very least surely Grub Customiser can be used to *view* the GRUB structure (without editing).

---

### Post by #&amp;thj^% on 2022-07-08
> **ajgreeny said:**
> I recommend that you **do not use grub-customiser** as it makes many changes to grub that are not easily reversed to get back to the standard.

Boot-repair [boot-info script]("https://help.ubuntu.com/community/Boot-Repair") will tell us a lot more about your system and what is currently installed, and as oldfred says, should give us a lot more detail, allowing better advice.

The only problems I see and hear about is on Wayland with grub-customizer: [https://bugs.launchpad.net/ubuntu/+source/backintime/+bug/1713313](https://bugs.launchpad.net/ubuntu/+source/backintime/+bug/1713313)
And Daniel maintains this PPA when needed:grub-customizer 10 weeks ago
Successfully built 

But I do agree in the hands of non-experienced users can be a bit of problem.
Nothing that can't be sorted out though.
FTR: I use the same method that oldfred has suggested:
> I turn off os-prober, and add only the entries I want into 40_custom.

---

### Post by SUPERFITTER on 2022-07-08
I used the Grub Customizer tool and it worked great.  
I do not know if I will have problems with Grub in the future because I used this program? 
I will let you know!

I want to thank all of you for your responses.

---

### Post by #&amp;thj^% on 2022-07-08
You shouldn't have any issues with it, if used just as you did now.
Just don't get creative with it. :D
If it's not broke don't fix it. ;)

---

