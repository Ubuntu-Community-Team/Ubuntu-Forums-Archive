---
title: "Wubi Install/Uninstall"
date: 2008-04-26
forum: General Help
---

### Post by Kemik88 on 2008-04-26
Hello,

The last time I tried Ubuntu (last LTS release) it didn't fulfill all my requirements but since the new LTS release came out I thought I'd give it ago, especially being able to install it and uninstall it to easily.

I downloaded (64bit) and installed it from Windows Vista (32bit), restarted my computer and loaded Ubuntu. It completed its installation process and restarted. I selected Ubuntu from the MBR and it had the scrolling, loading bar as expected but then loaded in to a SSH interface. I restarted again and had the same problem. I noticed however that my RAID setup now stated Status: degraded but bootable. I'm guessing it's because it needs to mess with the hdd to get ext3 format.

I thought, it's not working I'll uninstall and try again. I uninstalled but it went strangely quick. One or two seconds in fact. Restarted my computer to see Ubuntu as an option still in MBR. I expected this to be fixed back to the previous state, especially after all the reviews saying its just like uninstalling a windows program. All I have is a ubuntu-backup directory.

Now, Windows Vista shows two drives, instead of my RAIDed one. Drive F: has the Ubuntu installation, clearly because it has around 15GB less space (14GB actually but I selected 15GB on the install menu).

How can I fix this? I don't want to fix the RAID setup using Intel Matrix Storage Console in case it makes matters worse.

Thanks.

---

### Post by Kemik88 on 2008-04-26
Bump.

I cannot rebuild the RAID array when I have two drives with different amounts of data on and a MBR which still shows an "uninstalled" OS.

---

