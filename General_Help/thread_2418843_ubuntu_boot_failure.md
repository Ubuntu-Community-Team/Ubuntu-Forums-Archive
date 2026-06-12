---
title: "ubuntu boot failure"
date: 2019-05-12
forum: General Help
---

### Post by eclosion on 2019-05-12
1. now
display "missing operating system"
the boot repair info [http://paste.ubuntu.com/p/fG6yJh6W2d/](http://paste.ubuntu.com/p/fG6yJh6W2d/)

2. process
at first, the problem is grub missing, after boot is grub rescue mode. i can't find any grub file from the disk
then i use the boot repair tool([COLOR=#333333][FONT=UbuntuMono]sudo apt-get install -y boot-repair && boot-repair[/FONT][/COLOR]), repair automatically
last it display "missing operating system"

i think i make one more problem, so , anyone any advice is my pleasure

---

### Post by Rubi1200 on 2019-05-12
Hi and welcome to the forums :-)

Was Ubuntu the only operating system on the computer?

Do you have backups of ALL your data?

Is this an older computer with legacy BIOS or a newer one with UEFI?

Thanks.

---

### Post by yancek on 2019-05-12
If you have boot repair, try running it with the Create BootInfo Summary option and paste the link you get when it finishes here and someone should be able to help.

---

### Post by ajgreeny on 2019-05-12
Your boot-repair-info link is not a normal output but it suggests that you are trying to to install Ubuntu as a virtual machine using Virtualbox ; can you confirm that please.

Can you also tell us how you tried to install the system because it looks as if you used a DVD to install it and according to the information there is no Ubuntu OS installed at present.  I am wondering if you ran the Boot-info script in the host OS (which is what?) rather than from the VM you are trying to get running.

Much more clarification is needed if we are to help you further, with as much detail as you can please.

---

