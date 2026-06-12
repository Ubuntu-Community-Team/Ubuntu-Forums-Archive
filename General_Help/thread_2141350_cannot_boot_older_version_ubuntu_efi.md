---
title: "cannot boot older version ubuntu efi"
date: 2013-05-02
forum: General Help
---

### Post by creatxr on 2013-05-02
i have a older version ubuntu-gnome installed by uefi.
after i installed new version, i cannot boot into old version.
i try to keep the key 'shift' down when it reboot, but it doesn't display boot menu .
how to?
thanks

---

### Post by ajgreeny on 2013-05-02
Try repeatedly pressing the **Esc** key which is the one I need to press on my UEFI machine.  **Shift** does nothing on my machine either, though this is what I kept pressing in my attempt to boot to an older kernel.

I'm not sure if this is a change due to UEFI and its use of GPT partitions, but it is mentioned in [https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting) and it must be worth a go!

I quote
> If the menu is not normally displayed during boot, hold down the SHIFT key as the computer attempts to boot to display the GRUB 2 menu.

    In certain circumstances, if holding the SHIFT key method does not display the menu pressing the ESC key repeatedly may display the menu. What the circumstances are is not discussed at any point

---

### Post by creatxr on 2013-05-02
thanks. 
i get into grub menu by ESC key.
but now it has only the newest version, it didn't keep the older version anymore,,,
i don't know is i did a mistake when i installed.
i have a partition EFI to boot, systems were installed in other partitions.
i can see that it has only one grubx64.efi

---

### Post by oldfred on 2013-05-02
That is normal, but from grub menu you should be able to boot other installs.

If not try this:
sudo update-grub

UEFI boots from each folder in the efi partition. You may be able to copy & rename folders & reconfigure if you really want separate UEFI entries.

---

