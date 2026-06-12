---
title: "Once 'Shutdown ' Laptop 'Reboots'"
date: 2013-02-05
forum: General Help
---

### Post by MrJLepage on 2013-02-05
BACKSTORY:
I recently purchased a Toshiba laptop that came pre-installed with Windows 8; however, I did not like this O/S and decided I would try Ubuntu 12.10.
 
PROBLEM:
When I go to 'Shutdown' or go via terminal and type 'Poweroff' with Ubuntu 12.10 (I've also tried with LinuxMint 13) my laptop will shutdown for 1-3 seconds then turn itself back on when the power adapter is plugged in.
 
Has anyone experienced or heard of this issue?
 
SOLUTION:
A solution I've found, is that if I unplug the laptop before shutting it down, that it will remain powered off.
 
NOTE:
When a Windows O/S has been installed, the laptop powers off while the power adapter is plugged in.
 
Thanks,
 
Mr J Lepage

---

### Post by dino99 on 2013-02-05
Looks like you probably have a bios setting to do so.

---

### Post by MrJLepage on 2013-02-05
> **dino99 said:**
> Looks like you probably have a bios setting to do so.

My BIOS settings have been restored to default yet the problem still persists.

Could you please, elaborate on what BIOS setting you suggest I edit?

---

### Post by Brandel Valico on 2013-02-05
Here is something you can try. I also have a Toshiba Laptop and had the same issue of rebooting after a power down.

Fair warning this did work for me. But I can't promise it will work for you.

Open a terminal and type "sudo gedit /etc/default/grub" minus the "" into the terminal. Then type in your password.

You made need to use this command "sudo nano /etc/default/grub" as an alternate if gedit is not installed on your computer.

In the window that opens you need to add some things to a cmd line

You should see a line that looks like the one below. You need to add the bolded text.

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **i8042.nomux=1 i8042.reset**"


Give it a try and see if it works. if it does then great. If it doesn't then revert the changes.

---

### Post by MrJLepage on 2013-02-09
> **Brandel Valico said:**
> Here is something you can try. I also have a Toshiba Laptop and had the same issue of rebooting after a power down.

Fair warning this did work for me. But I can't promise it will work for you.

Open a terminal and type "sudo gedit /etc/default/grub" minus the "" into the terminal. Then type in your password.

You made need to use this command "sudo nano /etc/default/grub" as an alternate if gedit is not installed on your computer.

In the window that opens you need to add some things to a cmd line

You should see a line that looks like the one below. You need to add the bolded text.

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **i8042.nomux=1 i8042.reset**"


Give it a try and see if it works. if it does then great. If it doesn't then revert the changes.

I just got home and tried this resolution; however, it did not work for me.

Does anyone have any further suggestions?

Thanks,

Mr J Lepage

---

### Post by tgalati4 on 2013-02-09
You need to perform:

```
sudo update-grub
```

to actually write those changes to the grub menu table.  So give it another try.

It's possible that it is a bug in the ACPI for that laptop and an update to BIOS may fix it.

---

### Post by MrJLepage on 2013-02-09
> **tgalati4 said:**
> You need to perform:

```
sudo update-grub
```to actually write those changes to the grub menu table.  So give it another try.

It's possible that it is a bug in the ACPI for that laptop and an update to BIOS may fix it.

I did a sudo update-grub when following the steps.

How would you suggest I update the BIOS?

Thanks,

Mr J Lepage

---

