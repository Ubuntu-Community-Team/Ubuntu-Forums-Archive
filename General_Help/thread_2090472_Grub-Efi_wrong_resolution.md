---
title: "Grub-Efi wrong resolution"
date: 2012-12-02
forum: General Help
---

### Post by Nikki1993 on 2012-12-02
My question, as it comes from the title, related to grub, but it's a different thing.

I re-installed Windows 7 and Ubuntu 12.10 in UEFI mode (before that I was using normal BIOS) and everything went perfectly fine. Both systems load as they should but there is one thing that keeps bothering me. The problem is before I installed both systems in UEFI I used to boot in both system using common grub (non-uefi) and resolution in this grub was correct ( which is 1366x768 ). Right now with grub-efi I have wrong resolution (which is seems to be 640x480).

So my question is can can I safely set grub-resolution using grub config files or issue is related to something else? (for instance graphics card).

I am using Ubuntu 12.10 Intel HD 3000 + Nvidia GT 540M Optimus (I am using bumblebee) Kernel 3.5.0-19-generic all updates installed! I also added ubuntu x-swat ppa for drivers.

Thank you for your help!

---

### Post by oldfred on 2012-12-02
I think grub now tries to use the video mode from your install. Perhaps optimus confuses the issue, but I do not know optimus.

       Use this with your monitor size in /etc/default/grub:
GRUB_GFXMODE=1366x768

Use command line editor grub's on set gfxmode=640x480
and just remove the # as that makes that line a comment.
sudo nano /etc/default/grub
or
gksu gedit /etc/default/grub
# then 
sudo update-grub

I believe you can also use grub customizer.
       Repair grub's video mode and other settings
[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

---

### Post by Nikki1993 on 2012-12-03
Thanks for the reply. 
Regarding optimus video, this is something that is highly unlikely because as I stated before I installed ubuntu (around 5-6 times) and my grub resolution was as it should (even with bumblebee uninstalled and useing normal grub-pc). 
I do have grub-customizer but I wasn't sure is it save to use it with grub-efi. I will give it a try. I'll post my results in a minute.

---

### Post by Nikki1993 on 2012-12-03
Alright so changing GFX mode in grub hasn't changed anything. Resolution still smaller than it should be. Thou interesting fact, when I switch off my laptop the shutdown splash screen resolution is the size of my screen 1366x768 while boot splash + grub is smaller. I did sudo update-grub Any other ideas what I can try?

---

### Post by oldfred on 2012-12-03
I do not know optimus, but when you boot which video mode is it in. Intel or nVidia and can you change that in UEFI/BIOS?

---

### Post by Nikki1993 on 2012-12-03
By default intel graphics card is been used. Again I repeat before I installed Ubuntu and Windows 7 in normal BIOS mode and in this case you put grub into /dev/sda and  I had correct resolution (regardless if I had bumblebee installed or not)
In case of UEFI you have separate UEFI partition where you put the loader, but now I have problem that it does't want to set my resolution.
I cannot disable or change this in BIOS at all.

---

### Post by oldfred on 2012-12-03
The efi partition has just replaced the MBR. When boot repair converts a BIOS install to UEFI install all it does is uninstall grub-pc and install grub-efi. Both use the same grub parameters, and grub.cfg file to load. So unless grub-efi is not loading parameters correctly then it should be the same. 

I have not checked bugs lately but have not seen an efi issue on video resolution.

I just looked:
The only somewhat related is older.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802)

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by Nikki1993 on 2012-12-03
seems like this bug is still present. I bet I need to make a bug report at least.

---

