---
title: "Can't boot into Win7 after memory module replaced (dual boot)"
date: 2017-08-28
forum: General Help
---

### Post by Mylorharbour on 2017-08-28
Hi,
One of the two memory modules failed, intermittently at first, in my PC. I Diagnosed and removed the module and all worked well with just the remaining 4GB module. Win 7 booted fine. I replaced it after a while but now can't boot into Win7 from grub. I see 'Starting Windows' then there's a short pause as soon as the Windows logo starts to appear then the machine reboots. I've run diagnostics off the Win7 install disk but they find nothing wrong. Is this fixable or would I need to reinstall Windows into it's current partition? What would be the best way to do this?

Cheers

---

### Post by oldfred on 2017-08-28
Grub only boots working Windows.
So if Windows needs chkdsk or is hibernated, grub will not boot it.

If BIOS type install on MBR, you may have to temporarily reinstall the Windows boot loader to MBR so you can directly load Windows and try f8 for its repair console & make sure Windows boots ok.
Or use your Windows repair flash drive to repair Windows.

 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by Autodave on 2017-08-28
It is possible that your 2 RAM sticks are not playing nice. Remove the new one and see if if boots OK. If it does, remove that one and install the new one in its place and try. If that also works, put the old one in the second RAM slot and try with both installed.

---

### Post by Mylorharbour on 2017-08-29
Thanks for the replies guys.

Tried autodave's solution first. 
Opened up the PC.....oops, here's a correction to my OP.
I originally had 2x2Gb modules, not 2x4Gb. The 4GB module I bought replaced both, not just the faulty one. They work either singly or in identical pairs so I couldn't just replace the faulty 2GB with a new 4GB. That allowed me to expand to 8Gb later. Replacing the new 4GB with the old working 2GB made no difference. I could still boot into Ubuntu but not into Windows. Ho-hum ......

I'll try oldfred's solution but I'm not sure I understand it yet.

---

### Post by Autodave on 2017-08-29
My answer was the easy one: if it had fixed it. Now, you need to listen to oldfred: he is an expert: he has bailed me out more than once. :-)

---

### Post by Mylorharbour on 2017-08-30
Ok, working through oldfred's solution....

I used boot-repair which results in just ubuntu in the GRUB menu. - Ubuntu boots ok from here.
Next, booted from the Win7 DVD, went to the command prompt and typed in both commands, 
bootrec.exe /fixboot - successful 
bootrec.exe /fixmbr - successful 
Now the PC boots straight into Windows but I get the same issue that I described in the OP.

Seems I'll have to reinstall Windows??

---

### Post by oldfred on 2017-08-30
If now directly booting Windows can you use f8 to get into a repair console?
Have you also run chkdsk?

Do you have boot flag on NTFS primary partition? I do not think you would even get the Windows screen if you did not.
But then do you have all three Windows boot files in the NTFS boot partition? Or two in Boot and third in main NTFS or c: drive.

       Vista/7/8/10 BIOS (with 7, 8 or 10 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe

---

### Post by Mylorharbour on 2017-08-31
Ok, using F8 I got to the Advanced Boot Options screen which allowed me to select 'Safe mode with command prompt' but when selected the PC crashed.

By choosing the Repair Your computer option I did get to a 'System Recovery Options' screen where the last option was 'Command Prompt'. I could then enter chkdsk at a X:\windows\system32> prompt. This is a précis of the output:

File system NTFS
Volume label is Boot
Verifying files, indexes and security descriptors found no problems
Total disk space 3096Kb   (??) Clearly not the Windows partition which is 244Gb

I've since found a command to force chkdsk on C: ,    chkdsk /r C:
That's now running. I'll be back when it's complete

chkdsk shows all ok till it gets to the master file table where it found free space marked as allocated. Same with the volume bitmap. No bad sectors. Windows still crashes same as before.

How do I go about checking the NTFS primary and boot partitions (are these the same?)

---

### Post by Mylorharbour on 2017-08-31
I've just run gparted from an ubuntu install USB stick. There is a boot flag against /dev/sda1 which it shows as the NTFS Windows partition. Gparted doesn't show a 100Mb partition.

---

### Post by oldfred on 2017-08-31
Gparted should show sda1, but if it has issues, gparted will show a red error icon.

Normally Windows does not mount the Boot partition, so not seen. You would have to manually mount it with Windows repair console & run chkdsk on it. You may need to rerun all the other repairs.

Post this from Ubuntu to see your current partitions.
sudo parted -l

---

