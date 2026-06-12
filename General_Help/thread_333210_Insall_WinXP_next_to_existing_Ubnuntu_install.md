---
title: "Insall WinXP next to existing Ubnuntu install?"
date: 2007-01-07
forum: General Help
---

### Post by Mimsy on 2007-01-07
I need to reinstall WinXP on my laptop. I want to do it on a separate partition, and dual-boot, so I can keep my Ubuntu-setup. I have looked at various guide to dual-booting, but they all seem to assume that I am starting out with Windows installed, and adding an Ubuntu partition. If there is a guide somewhere for how to do the reverse, I would love to see it. Please post links to such guides, if you have them.

Thanks,
Mimsy

---

### Post by kd7swh on 2007-01-07
The are a few guides out there I will post one if I can dig it up but until then I will explain why you found what you did.

If you install linux first, and than install windows. Windows replaces your Master Boot Record (MBR) and breaks GRUB in other words you will be unable to boot linux until you repair GRUB (your boot loader). 

This is not fun. Linux does not do this to windows so it is best to do it in that order. 


|looking for a guide|:)

---

### Post by Mimsy on 2007-01-07
Oh. Ouch. Owie. I do *not* want that to happen to my Ubuntu installation. :shock: 

I assume GRUB can be repaired though? I will have to research whether I really need to have a dual-boot now, since I enjoy Ubuntu, and have absolutely no desire to get rid of it. If you find a guide, I'd still like to see it though, since I now want to know jsut exactly what I am getting myself into.

Thanks for the quick reply!

/Mimsy

---

### Post by Bigbluecat on 2007-01-07
This method will restore grub to the MBR of your first drive:

1. Boot from the Live CD

2. Open a Terminal. 

3. Type "sudo grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hdx)" 

5. Type "root (hdx)". Whatever was listed by the above command. This tells grub where to look for menu.lst etc.

6. Type "setup (hd0)". This writes grub to the MBR

7. Type "quit".

8. Restart the system. Remove the bootable CD.

---

