---
title: "[SOLVED] Accidentally uninstalled linux kernel"
date: 2008-07-04
forum: General Help
---

### Post by MaxSommerfeld on 2008-07-04
Hi everybody!

I have uninstalled the initramfs-tools package today which caused some other packages to be uninstalled, among them the linux-kernel-generic and other essential packages.

When I am now trying to boot, GRUB shows Ubuntu but if I select it, I see ERROR 15: file not found. Which is not really a surprise.

I know that I made a really dumb mistake. It would be really great if someone could tell me how I can make the system work again.

I am quite desperate at the moment so thanks in advance for any help you can give me! -Max

---

### Post by Frozsyn on 2008-07-04
I think you can boot with the Installation CD
Then use use the terminal to chroot your HDD system and do what you have to do in it.
Let's suppose you have installed everything in the /dev/hda partition

The chroot stage:
```
sudo mount /dev/hda /mnt
sudo mount --bind /dev /mnt/dev
sudo mount -t proc /proc /mnt/proc
sudo chroot /mnt

```

The reinstallation stage:
```
sudo aptitude install initramfs-tools
```

---

### Post by drs305 on 2008-07-04
> **MaxSommerfeld said:**
> 
When I am now trying to boot, GRUB shows Ubuntu but if I select it, I see ERROR 15: file not found. Which is not really a surprise.


On your grub menu do you have more than one kernel option displayed? If so, choose another kernel. Background: When you automatically delete a kernel with synaptic it automatically edits the menu.lst. However, if you only had one kernel displayed I don't know what it does. 

If you don't have another kernel on the menu, but you think you have other, older kernels still installed on your computer, you can press 'e' as the grub menu appears to edit the choices. From there you can edit the kernel to choose from. If you don't know which ones you have, write down the current entry and then try decreasing (or increasing) the kernel number without changing anything else on the line. 

Another reason to keep at least two kernels on your computer ;-)

---

### Post by MaxSommerfeld on 2008-07-05
Thanks Frozsyn! I've thus managed to reinstall the kernel. But I had to manually install all the packages that (I think) have been removed together with initramfs-tools (if you think a list of them would help in any way just let me know!).

Ubuntu is now starting again when I choose it in GRUB. My username and password are also accepted but after I've signed up the screen remains blank (ubuntu brown with mouse coursor). 

I assume this has something to do with the error messages I received when installing the packages hal, gnome-session, gnome-power-manager etc.
It seems that the configuration of the package hal failed. Among others, I receive this error message: 
```
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I hope you can help me with this, too. Thanks again!

---

### Post by Frozsyn on 2008-07-09
I didn't understand if you know the list of packages that have been uninstalled.
- If you know the list, you can reinstall them easily using aptitude/apt or whatever you usually use.
- If you don't know the list, you can manage to get it by looking the log file in /var/log/apt/term.log. You can search the date in the file (format YYYY-MM-DD) and look at every action done or search the word "Removing" to get every removed packages.

I hope this helps.

---

### Post by MaxSommerfeld on 2008-07-10
Hi! 
I've backed up and reinstalled Ubuntu. Although this is not what I'd call a solution I will mark this thread solved. But nevertheless, thank you!

---

