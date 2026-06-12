---
title: "Did update ,now computer will not boot to OS"
date: 2021-08-10
forum: General Help
---

### Post by rapidrob on 2021-08-10
I'm running the latest version of Ubuntu and did the automatic update last night. This morning there was an error shown that the OS had a problem and did I want to report it? I clicked yes and the computer shut down to reboot for the new changes. Now the computer will not boot into the OS fully. I get the name UBUNTU and icon and it loads for several minutes ( normal for this computer) and goes to a black screen with a very slow flashing colon  in the upper left corner. 
No matter how long I let it run, the computer never completes a boot to the full OS.
What Can I do?
Since the computer will not boot I cannot give you the OS version,please don't ask.

---

### Post by Impavidus on 2021-08-10
Can you access the grub menu and boot an older kernel? Or use recovery mode, at the menu choose "resume"? That will load the open source graphics driver, if you normally use a proprietary driver.

---

### Post by rapidrob on 2021-08-10
I reset the motherboard CMOS and re-booted. The "Grub rescue " started but did nothing.

---

### Post by rapidrob on 2021-08-10
The Hard Drive is corrupt. I put in a spare Linux lite HD and the computer is working. No idea as to why it failed..it is new.

---

### Post by rapidrob on 2021-08-10
I was able to open the HD and save my files remotely.. The OS is so  corrupted after the update The HD will have to be erased and formatted  for use again.

---

### Post by Impavidus on 2021-08-11
Upgrades occasionally (it never happened to me) cause a black screen, when something's wrong with the graphics driver. They don't cause a grub rescue prompt. You get one of those when grub cannot find its config file, which happens if it's manually deleted or the partition is destroyed. Not during grub updates; there are safeguards against that. Unless you installed questionable third-party repositories, the hard drive corruption is most likely not caused by the upgrade.

Have you made sure the cable of the hard drive is properly connected?

---

