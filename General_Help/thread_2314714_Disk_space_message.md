---
title: "Disk space message"
date: 2016-02-23
forum: General Help
---

### Post by mchlmcquown on 2016-02-23
DDSOS  Once again, I am getting this message about clearing disk space (see screen shot) but I'm not sure how to format the instruction in the kernel to get it to work. The last time, I ended up re-installing to clear up the problem but lost files in the process. Now, I have have 14.04 on several machines before this one  (Dell Optiplex 900 series) and never had a space problem before.

---

### Post by grahammechanical on 2016-02-23
If /boot is a folder in the Ubuntu partition then we do not get this situation until the Ubuntu partition is almost full. But when /boot is on a separate partition we do get this problem because of the limited size of the partition.

You may find that you are in a kind of loop. The system wants to upgrade a Linux kernel. It cannot do that because there is not enough space. When you try to create space it may trigger the attempt to install the new kernel before the completion of the process to remove packages. And so the error appears again and  again.

At the grub boot menu select Advanced options for Ubuntu and then select a recovery mode kernel. At the recovery menu select Clean - Try to make free space. That will run to commands - clean & autoremove. And it is autormove that should remove at least one old kernel. Or you can run these commands from a terminal using

```

apt-get autoremove
apt-get clean
```

You may find that running apt-get from a terminal may trigger a new attempt to finish upgrading the kernel & so you may see the same error again.

Regards.

---

### Post by mchlmcquown on 2016-02-23
How do I get to the Grub boot menu?

---

### Post by yancek on 2016-02-23
> How do I get to the Grub boot menu? 		

The image in your first post shows you are booted to the Ubuntu Desktop.  What's changed?   Are you now no longer able to boot?  When you boot the system, you should see various options including the Advanced option mentioned above and select the recovery mode.  If you don't see the menu, hold down the Shift key at the start of the boot process.

---

### Post by mchlmcquown on 2016-02-23
When I turn on the computer, I go to the Ubuntu screen with the travelling dots, then I go directly to the desktop.  I will try your suggestion.

Very frustrating. I held the Shift key down, but Grub appeared on the black screen for an instant and disappeared. Now: one difference in my logon routine is that I opted for encryption, so every time I get to the Ubuntu cover page, I have to enter the encryption password. Then it goes right to the desktop except for every 3rd logon when it asks for my login password. Would any of this be an issue? And how can I get rid of that login password request, since I didn't ask for it?

Well, by poking and prodding, I finally got to grub, and I think I did what had to be done.  We shall see.

Nope. I found Grub, clicked on clean, clicked on  'update boot'  and still getting the original error message. I think you may be right about being in a loop, but how do I get out of it?

---

