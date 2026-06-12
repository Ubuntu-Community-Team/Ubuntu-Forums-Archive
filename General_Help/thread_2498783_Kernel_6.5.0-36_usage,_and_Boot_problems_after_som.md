---
title: "Kernel 6.5.0-36 usage, and Boot problems after some times usage"
date: 2024-06-27
forum: General Help
---

### Post by megsoconnor on 2024-06-27
i have update my kernet to 6.8.0-36 with success, the boot work and system was ok during 1 month. after some times and minors auto-updates, unexpectedly, i am encoutering now a boot problem. It start from fail safe mode, and saying execute journalctl.

journal ctl says: unable to parse boot descriptor '+'.
i dont know what happened. where must i seek the problem ? in /boot/config ?
trying to boot get system to loop at repair mode.

The 6.8.0-35 kernel continue to work perfectly.

- Boot-repair do nothing
- Purge kernel and reinstalling it do nothing
- FileSytem check do nothing

what do you need to have an idear or a solution for that ?

---

### Post by yancek on 2024-06-27
Are you an expert on the Grub bootloader?  I'm guessing not.  Did you read the home page at the boot repair site which tells users who download the software to use the Create BootInfo Summary option and post the link to the output here or at another forum for advice.  You haven't posted the link??  Did you use that option?

---

### Post by currentshaft on 2024-06-27
Boot to the working kernel version and try:

sudo apt install --reinstall $(dpkg --list | grep linux-generic | awk '{print $2}')

---

### Post by megsoconnor on 2024-06-28
**story:**
- loosing window boot capacity 4 months ago
- loosing  kubuntu boot 

**what i have done to stabilize the boot at working kernel:**
there was a dual boot with windows11.
- trying to reinstall kernel ...
- Clear and destroying windows partitions i do not use from a couple of month now. no need to keep a spyware system on my UC.
- Removing old kernel manually ( dpkg -l / apt remove ) ( there was -21 to -31 remains ,  i also removing -36)
- Removing Grub/grub.cfg bad remain configs into it
- Removing /boot/efi/efi/windows and old not used EFIs persitent data.

**but:**
The system is still booting in a 2 minutes long times. that is not normal,
there are those efi entries:

> 
[FONT=monospace][COLOR=#000000]BootOrder: 0003,0001 [/COLOR]
Boot0001* neon  VenHw(xxxxxxxxx-xxxx-xxxx-xxxx-c5385e6c00cb) 
Boot0003* Ubuntu        HD(1,GPT,xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx,0x800,0xee000)/File(\EFI\UBUNTU\SHIMX64.EFI) 
[/FONT]

hmm, neon haven't valid start entry, can't activate it. can i i'll clear it from bootmgr ?

**DSMEG**
> [FONT=monospace][COLOR=#000000][     0.036828] kernel: Kernel command line:  BOOT_IMAGE=/vmlinuz-6.8.0-35-generic  root=UUID=xxxxxxxxxxxxxxxxxxxxxxxxxx ro quiet splash  vt.handoff=7 [/COLOR]
[    0.036883] kernel: Unknown kernel command line parameters  "splash BOOT_IMAGE=/vmlinuz-6.8.0-35-generic", will be passed to user  space.[/FONT]



**Yancek: ***"Are you an expert on the Grub bootloader?I'm guessing not."* [IMG]https://ubuntuforums.org/images/smilies/icon_sad.gif[/IMG] Oo... if i request help, it is evident i am not an expert in latest grub usage, you don't have to be a genius to figure it out... this affirmation wasn't pertinent at all. if you need this log , you just have to tell me you want it. And not justify your superiority in this way. it's childish. I haven't doing this online log because i don't know if there is pertinent info for you into it. And it is not recommended right now to expose boot infos to the world when it is not requested and important. be nice and don't help me. Let other constructive guys try in. if not, i"ll resolve my problem by myself with much more times and research as always. Unfortunately with all modifications i manually made on the boot this log no longer be interesting for you.

[B]CurrentShaft: 
[/B]thanks, purging package destroyed all Linux-generic entries, [FONT=monospace][COLOR=#000000]"dpkg --list | grep linux-generic[/COLOR]"[/FONT] return nothing. too late XD. i had try to reinstall it before make a clean in efi and kernels. any way you are rigth, after all the cleanup, reinstall the generic package resolve the tricks.... thanks

---

### Post by megsoconnor on 2024-06-28
Solved

---

### Post by ActionParsnip on 2024-06-28
Please mark as solved

---

### Post by megsoconnor on 2024-06-29
i think it was a malware or an attack... that is not possible.... i never experiment a so unstable boot with linux just in a minor kernel update. experimenting today the same thing summoning again...
- the first boot work perfectly -36
- the second boot work badely -36, and Impossible to repair with repair boot mode : menu is doing nothing and keyboard do not responding correctly. never see that before. what the hell is that.
- the -35 still working with a long time boot.

to resolve this pb again :
- maj boot-repair
- execute a purge of grub, and a reinstall.
- well done for today.....

pictures of boot loader have changed to ubuntu but it is not important for boot success.

---

### Post by dragonfly41 on 2024-06-29
I have an added tip. If as it seems you have Windows 11 installed install free trial version of
 [https://www.easyuefi.com/index-us.html](https://www.easyuefi.com/index-us.html)
This will give another perspective.
Whether you want to pay after the trial is up to you. I rarely go into Windows.
I use rEFInd in multi booting, myself.

---

