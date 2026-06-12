---
title: "System Reboots when resuming from Hibernate"
date: 2019-04-17
forum: General Help
---

### Post by seegee2 on 2019-04-17
I have an old Asus EeePC 1000H that I have installed lubuntu on. After using the lxqt desktop, i decided to switch to xfce4 as my preferred desktop interface.

I have 2Gb of ram, and a swap partition (/dev/sda2) that is exactly 4Gb.



Please forgive any errors in paths, I'm writing this at work, from memory of what I did last night and this morning before I left.

I have activated the swap patition (mkswap, swapon) and added it to fstab (using UUID) and it shows up at boot as working and available. 

cat /sys/power/state says hibernating to "disk" is supported

cat /proc/swaps outputs what it should. swap partition is active, and available.

I have modified the /sys/lib/polkit-1..../com.ubuntu.pkla file and enabled hibernate policies for both upower, and systemd
After doing this, Hibernate now shows up as an option in the shutdown menu in Xfce4. Progress!

I added the "resume=UUID=<uuid of swap partition>" to [COLOR=#242729][FONT=Arial]/etc/initramfs-tools/conf.d/resume[/FONT][/COLOR]
I edited /etc/default/grub and added the line[INDENT]GRUB_CMDLINE_LINUX="resume=UUID=<uuid of swap partition>"[/INDENT]

Updated grub (update-grub), success!

ran sudo update-initramfs -u, which also reports success.

then I reboot the machine.

At this point everything is lined up as it should be according to the SwapFaq, so I select 'Hibernate' from the system shutdown menu. the system locks the screen, there's a flurry of disk activity for several seconds, and then the machine powers off. Ok, so at this point everything seems great.

When I power on the machine, I get the lubuntu splash, which says at the bottom "resuming from /dev/<UUID of swap partition>.... the screen then goes blank for about 2-3 seconds, and then poof. Reboot, and we're back at the BIOS POST, at this point. I see the lubuntu splash screen again, but no mention of resuming anything, and the desktop boots as though it was just a clean startup...

I have taken a look at /var/log/pm-suspend and it doesnt indicate what the issue is... Unless I'm completely missing something.

Where should I look for more insight on what's actually happening, and where the failure is occuring?
I appreciate any help you can offer, (and I'll try to clean up the post a bit once I'm back home beside the laptop)
I understand that Xfce4 uses xfce4-power-manager, and i installed lubuntu and added xfce afterwards. could that be related?

---

