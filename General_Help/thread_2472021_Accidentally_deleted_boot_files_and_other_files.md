---
title: "Accidentally deleted boot files and other files"
date: 2022-02-15
forum: General Help
---

### Post by vardn5 on 2022-02-15
I was trying to delete temp files. Successfully deleted everything from /var/tmp. After that i remember going back and deleting contents of /tmp (rm -r *). Then the terminal screen started glitching and got a black screen with some weird characters on top. Since then i was not able to boot either of my OSs. No media available kept on coming. Right now I'm trying to use Boot Repair to solve the issue with a live USB. If anyone has any idea what exactly happened could you please reach out.
Thanks xD

[https://paste.ubuntu.com/p/PDw9RF5hyx/](https://paste.ubuntu.com/p/PDw9RF5hyx/)

---

### Post by kevdog on 2022-02-16
What drives are you using nvme and sda1?  It looks like it's trying to boot of the nvme drive.  Describe your hardware a little bit more.  Is there a windows dual boot that is present?

---

### Post by Impavidus on 2022-02-16
sda is the live disk, nvme0n1 is the internal drive. It's gpt partitioned and the computer is booting in efi mode. For Windows that's a requirement. You have both Windows and Linux installed. There is an efi partition, but it's empty, with neither Windows nor Linux bootloaders. There are two medium-sized Linux partitions. One is empty, the other (nvme0n1p8) appears to have a Linux operating system, but multiple vital files are missing. There is no kernel or /etc/fstab.

I'm not sure what has gone wrong here (maybe a sudo rm -r in the wrong directory?), but I would reinstall.

BTW, that files are temporary doesn't mean they're unimportant. Deleting everything from /tmp will likely crash your session, but it should be fine after logout/login. I don't know about /var/tmp.

---

### Post by HermanAB on 2022-02-16
Hmm, boot with install media and backup your data.  Only then, should you start experimenting to fix it.  Reinstalling is probably the easiest, but you won't learn much from that.

---

### Post by vardn5 on 2022-02-17
I'm using an nvme ssd as my storage device. nvme0n1p1 contains the boot files, nvme0n1p2 had a Win 11 installation, nvme0n1p8 was used for an Ubuntu install in which i deleted some critical files. Since i needed a working system that day itself I left the damaged partition untouched and reinstalled Ubuntu in nvme0n1p9.

---

### Post by vardn5 on 2022-02-17
I have a win11 installation which i am not able to access now as i deleted the win Boot loader also idk how :'( 

I have a working ubuntu install for the time being. Since latest windows boot loader does not support dual booting with Ubuntu, I was using Grub (Which probably got deleted when i deleted the temp files in nvme0n1p8. I am keeping the partition 8 so that I can learn something from it.

I also need to figure out a way to reinstall Win boot loader and add it to Grub.

---

### Post by oldfred on 2022-02-17
Grub only boots working Windows.
That means no chkdsk required and no hibernation. Windows fast start up sets hibernation flag which also prevents grub from booting Windows.
Note that Windows updates may turn fast start up back on.
With UEFI you should always be able to boot Windows directly from UEFI boot menu, same menu you use to select installers or repair flash drives.

You may need your Windows repair flash drive to fix Windows as almost no fixes can be done from Linux.

---

### Post by Quarkrad on 2022-02-18
As @HermanAB said - first thing to do is to, via a live cd session, back all your important data up and then follow instructions above. Depending on how much time you have to learn vs getting your system up and running, these things are often much much quicker to fix by re-installing.

---

