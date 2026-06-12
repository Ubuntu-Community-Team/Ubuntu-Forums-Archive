---
title: "System does not initialize Ubuntu OS anymore"
date: 2024-03-22
forum: General Help
---

### Post by pedrocedro on 2024-03-22
Hello! I recently installed Windows in a new SSD I bought. I'm using a Lenovo Laptop Ideapad3 which comes with a SSD NVME as default. So I installed Ubuntu on it sucessfully; Last version I was using was 22.04 LTS.
For a few days after Win instalation was succeeded, I was able to use both OS, not in dual mode with grub for example, because if I need to switch OS, I had to change boot settings in BIOS to select the OS I Would like to use.
A Friend told me to execute some lines in the terminal to make grub read all OS in the 2 drivers.
os-prober
sudo grub2_update
And after that, my BIOS was unable to show me "ubuntu" at the boot page anymore, just windows is shown.
I'm able to boot live cd from the pendrive and see all my files, but can't start it normally.
Could anyone help me please, I just tried many step by steps with live cd in videos, or forums.
I appreciate all help, thanks!

---

### Post by tea for one on 2024-03-22
Power off the laptop
Remove the Windows disk
Power on
Access the UEFI settings 
Disable Secure Boot and TPM (or FTPM, PTT and any similar security options)
Save settings and boot

Any luck?

---

### Post by pedrocedro on 2024-03-23
No luck yet, when I did what you said the screen only showed windows boot manager with an error.

---

### Post by tea for one on 2024-03-23
What is the error message?

---

### Post by pedrocedro on 2024-03-23
It was an error due I had unplugged the win ssd. But I could solve this issue. At now I have dual boot with grub back.
What I did was:
- As I was able to boot windows, I began searchig some software to manage boot. Then I found this software "Hasleo EasyUEFI".
In this software I manually added the Ubuntu, selecting what grub file I needed.
Then It worked fine.
I had some issues with kernel but in the grub screen I could boot a kernel that was fine. And thats it, I updated and upgraded everything.
So thats it! Thanks!

---

### Post by yancek on 2024-03-24
The information you posted initially was not really enough for anyone to help except to guess.  You indicate you have 2 physical drives with windows on one and Ubuntu on the other and that to switch boot from one to the other, you had to go into the BIOS.  You did not specifically indicate they were both UEFI or if they were, you had EFI partitions on each drive.  The commands you posted in your initial post would not have caused the problems you indicate.  os-prober simply searches partitions for boot files when it is enabled and the command grub2_update doesn't exist.  It is the stub update-grub which runs grub-mkconfig to update the Grub files (Some Linux systems do use grub2-mkconfig).

In the future it would be helpful for you and others with this problem to run boot repair (link below) and use the Create Bootinfo Summary option and NOT try repairs but post the link you get when boot repair finishes here or at another forum.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thanks for posting the link to the windows software as I wasn't aware of it.  Neosmart had similar software but microsoft refused to allow them to create UEFI software.  Not sure what changed.

[https://neosmart.net/wiki/easybcd/uefi/](https://neosmart.net/wiki/easybcd/uefi/)

Found the neosmart site below so it appears that they also have recovery software for UEFI.

[https://neosmart.net/wiki/fix-uefi-boot/](https://neosmart.net/wiki/fix-uefi-boot/)

---

### Post by dragonfly41 on 2024-03-24
I suggested EasyUEFI here post#12
[https://ubuntuforums.org/showthread.php?t=2496308&page=2](https://ubuntuforums.org/showthread.php?t=2496308&page=2)
but did not post link. Seems that OP found it useful, as did I when first tried.
It gives another option for dualboot users (Windows+Ubuntu) who have screwed up 
and cannot use Boot-Repair (although on reflection running Boot-Repair in a LiveUSB might serve the purpose).

---

### Post by aug7744 on 2024-03-25
In mainboard UEFI settings select the bootmanager in disk having the Ubuntu installation. Try to do it with both 2 disks installed.

---

