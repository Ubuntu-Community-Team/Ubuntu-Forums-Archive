---
title: "How do I delete Kubuntu?"
date: 2008-02-11
forum: General Help
---

### Post by tlinux on 2008-02-11
I have Kubuntu 7.04 installed in a dual boot setup with Windows XP Home Edition in another partition. I want to delete Kubuntu, remove the partitions, and revert just to Windows. How can I do that?

I'm worried that when I delete Kubuntu, Grub will go too, and I may not be able to log onto Windows. Is that a problem? BTW, Kubuntu is frozen up and I can't get into it to do anything.

Any other help you can offer will be appreciated.

Thank you.

---

### Post by DJRhubarb on 2008-02-11
Hi, I have had this problem too. You will have to go into Windows and open up command prompt, navigate to your C drive and delete it from there.

---

### Post by The Avatar of Time on 2008-02-11
I am not real sure but I would think that you could put in the windows install cd and have it resize the windows partition to take up the whole hard drive. Alternately you may have to insert a linux disc to delete the linux partitions back to free space and then use the windows disc to resize itself. Gparted (GNOME) is alot better than QTparted (KDE) for a partitioner but either should work. They may be able to resize the windows partition as well. If you have trouble booting back in you should be able to use the windows disc to fix it's bootloader. I know Ubuntu can fix GRUB but not positive about the windows disc. And again I'm not 100% sure how you would fix the bootloader so please don't blame me if this doesn't work. When I was running Vista I always just reinstalled if I got tired of linux (I'm linux only now though, just takes some getting used too.). Good luck.

---

### Post by HappyFeet on 2008-02-11
just boot to the windows cd and choose "recovery console". then pick your windows installation.(#1) and then type fixmbr. you will then have your windows boot normal.

---

### Post by corte123 on 2008-02-11
this question has been asked way too much , just do a little research next time . download gparted live cd an delete all the partitions an then reinstall winblows

---

### Post by Neobuntu on 2008-02-11
Run down to One Microsoft Way. Go inside. Turn around and **bend over**.:lolflag:

(Sorry. Couldn't help it. Just a joke people.)

---

### Post by cdaringe on 2008-02-14
Hello,
We are sorry to see you go!  I was wondering if you had tried using wine or VirtualBox to use windows programs.  wine runs executables, and virtualbox runs windows inside of linux! cool stuff.

Anyway, if you have vista, this is your golden ticket.
[http://www.mydigitallife.info/2006/11/27/change-or-resize-partition-ntfs-fat-or-fat32-size-in-windows-vista/](http://www.mydigitallife.info/2006/11/27/change-or-resize-partition-ntfs-fat-or-fat32-size-in-windows-vista/)

If your kubuntu is frozen up, you may need to share a little more detail as to what is causing it, or when...or what you see...etc.

Good luck to ya

---

