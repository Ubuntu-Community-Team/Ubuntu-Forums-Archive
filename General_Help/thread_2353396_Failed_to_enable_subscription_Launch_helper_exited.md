---
title: "Failed to enable subscription: Launch helper exited..."
date: 2017-02-21
forum: General Help
---

### Post by javierdl on 2017-02-21
... with unknown return code 1

I have a dual boot system with Windows 10 and Ubuntu 16.04. Each on a different drive.
I had been using both without a problem. Yesterday during the day I switched to Windows, then at night I tried to switch to Ubuntu but although it would seem to load everything as usual, when trying to enter into an account, it would return me back to the same page where you choose your account and enter your credentials.
Then I rebooted and tried the next choice in line, but that's when I got this error: 
```
"Failed to enable subscription: Launch helper exited with unknown return code 1. Failed to fully start up daemon: Input/output error"
```

Then I rebooted in Safemode, and tried "dpkg" (repair broken packages). And rebooted to normal. But the problem persisted.
I rebooted in Safemode again, and tried "fsck" (check all file systems). And rebooted to normal. But the problem persisted.
I didn't see a choice to boot from previous versions. See the attached image file to see my choices.

I thought of restoring previous backups with Backups, but, how to target the location where Ubuntu is, as opposed to the USB drive?
Or is there a better way?

Thanks guys,

JDL

---

### Post by javierdl on 2017-02-22
I just ran Boot Repair Disk.
It said it successfully repaired the booting files.
However, the problem still persists (...[COLOR=#000000]when trying to enter into an account, it would return me back to the same page where you choose your account and enter your credentials.[/COLOR]).

I had this problem before, I seem to recall it was advised to change the permissions, but I have to scour my records and previous posts to confirm that and see how exactly do it.

---

### Post by javierdl on 2017-02-23
I[COLOR=#242729][FONT=Arial] booted up, this time I chose the 2nd option: Ubuntu Advanced Options. Then I saw the list of the previous versions, I chose the previous one (1 back), and it logged in just fine!!! 
Now, I asked this: Should I expect it to do it again on its own? Or should I be taking additional steps to ensure it'll login fine next time?[/FONT][/COLOR][COLOR=#242729][FONT=Arial] 
And I was advised to: [/FONT][/COLOR][COLOR=#242729][FONT=Arial]run [/FONT][/COLOR]update-grub[COLOR=#242729][FONT=Arial], so that your previous version appears as the default. 
I did, but instead of asking me what kernel version to choose it just did some updating (I guess):
[/FONT][/COLOR]```
sudo update-grub
[sudo] password for javier: 
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.10.0-041000-generic
Found initrd image: /boot/initrd.img-4.10.0-041000-generic
Found linux image: /boot/vmlinuz-4.9.11-040911-generic
Found initrd image: /boot/initrd.img-4.9.11-040911-generic
Found linux image: /boot/vmlinuz-4.9.10-040910-generic
Found initrd image: /boot/initrd.img-4.9.10-040910-generic
Found linux image: /boot/vmlinuz-4.9.9-040909-generic
Found initrd image: /boot/initrd.img-4.9.9-040909-generic
Found linux image: /boot/vmlinuz-4.9.8-040908-generic
Found initrd image: /boot/initrd.img-4.9.8-040908-generic
Found linux image: /boot/vmlinuz-4.9.7-040907-generic
Found initrd image: /boot/initrd.img-4.9.7-040907-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done


```[COLOR=#242729][FONT=Arial]

I hope this is all moving in the right direction...[/FONT][/COLOR]

---

### Post by javierdl on 2017-03-02
Well, that lasted only for so long :(
Until I changed graphics drivers. 
After I did that I rebooted, only to find that everything was over sized, but most importantly, that Ubuntu would not let me in. It did load everything first, all the GUI loaded too. Ubuntu was there just waiting for me to enter my password. But once I did, Ubuntu would check it and let me in for only 1 second, then kicked me out. Just like before.
The over sized screen is no longer a problem. I have tried a few things, like from the Advanced Options / Recovery Mode (when booting): dpkg (to repair broken packages), and fsck (check all file systems). And the Boot Repair Disk. They all seemed to have done something, but not enough to fix this logging problem.
I know I can always reinstall Ubuntu. But I just can't believe that there is nothing that can be done before going to that extent.

Thanks for reading guys,

JDL

---

### Post by javierdl on 2017-03-02
AFH from Superuser.com was kind enough to suggest this: 
[I]"Try to open a "root X-session", from Alt-F8, or other Alt-Fn, from a normal boot, log in as root, and use the command-line user maintenance functions: Alt-F7 will bring back the GUI. If this doesn't work, try something like apt-get -f upgrade and reboot. If this works for you, then the GUI tools, such as synaptic, will be available. You can use it to find and reinstall packages, such as login, though it's only a GUI front-end to apt-getand some of the other apt* utilities. I find it a lot easier than Software Boutique."

[/I]So, I'll be trying this soon.

JDL

---

