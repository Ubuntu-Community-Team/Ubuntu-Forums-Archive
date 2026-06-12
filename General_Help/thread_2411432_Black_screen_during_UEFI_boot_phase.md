---
title: "Black screen during UEFI boot phase"
date: 2019-01-30
forum: General Help
---

### Post by retrocade81 on 2019-01-30
Hi I’ve recently installed bionic on my X250 with uefi core i5 5300u, 8gb ram, 240gb ssd the problem I’m having is when I boot I get ether grub splash then the screen goes black for 35 seconds then the Plymouth splash appears. It’s taking over a minute to boot should uefi have a splash or can I add a splash to the uefi boot phase?

Thanks

---

### Post by oldfred on 2019-01-30
Your boot seems a bit slow especially since SSD.
UEFI splash screen is before grub menu. UEFI often has setting to show it or not. But UEFI also has Microsoft required fast boot setting. That assumes no hardware or configuration change, so UEFI immediately starts boot. Normal boot would scan system and write configuration data onto drive for operating system use. Usually then you may only see UEFI screen with full cold boot, not warm reboot.

I often turn off  the setting in grub for quiet splash. Then you see every line scroll by as system boots. That same info is in log file for later use if necessary to resolve issues. While you can turn that off permanently in grub I prefer to only change occasionally by editing grub when booting. Use f8, and on linux line remove the quiet splash. 

What does this show? Mine say 26 sec.
fred@Bionic-Z170N:~$ systemd-analyze
Startup finished in 2.888s (kernel) + 23.164s (userspace) = 26.052s
graphical.target reached after 23.156s in userspace

I have not done much tuning.
I only do clean installs, but use an export of all installed apps from old install to add to new install. Found I years ago added apache & mysql, but not us ing them. Removing them saved one second in boot time.
I also remove snaps.
       [https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb)
boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)

---

### Post by retrocade81 on 2019-01-31
“UPDATE”( I’ve removed snap and watched the post it says system started in 1m07 secs no errors at all either. I wouldn’t mind but the screen is completely black for the entirety of that time the grub splash only shows for 5 seconds then it’s just a black screen covering the boot post screen for 1:07 then Plymouth boot splash for 10 seconds)
Thanks for the reply that’s a bit odd if uefi starts first as I have set a custom grub splash to add some continuity to the whole boot process transition from grub to Plymouth I must admit I’ve always used bios and grub. I’ve never bothered with uefi before so I don’t really know much about it. I’ll do some checks later and report back and I’ll also remove snap as it’s useless to me anyway.

---

