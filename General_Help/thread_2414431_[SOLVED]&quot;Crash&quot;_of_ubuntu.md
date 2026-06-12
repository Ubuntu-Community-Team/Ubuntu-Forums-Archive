---
title: "[SOLVED]&quot;Crash&quot; of ubuntu"
date: 2019-03-10
forum: General Help
---

### Post by emilianocpu on 2019-03-10
Hello everyone, sorry for my English but I need help and in the forum of my language did not know how to help me. I installed ubuntu on my laptop (asus x541ua) initially it worked fine but then soon after the operating system stopped working. He began to give me a black screen with writings that follow one another as in the picture: [http://i66.tinypic.com/2n15oo6.jpg](http://i66.tinypic.com/2n15oo6.jpg). For information the pc with windows works well but does the same with mint and I tried to reinstall it several times. Thank you.

---

### Post by oldfred on 2019-03-10
A lot of Asus models need a boot parameter pci=momsi. Without parameter there are run-away log files filling drive.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Boot-Repair should show if drive is full, but you can quick check from live installer and mounting all your partitions:
Can you boot using recovery mode to terminal? Second or third entry in grub.

       
 # check sizes of 
Partition sizes
df -Th | grep sd| sort
Inodes:
 df -i
cd / or cd /home
sudo du -hc --max-depth=1
Shows just /
sudo du -hx --max-depth=1 / 2> /dev/null

---

### Post by emilianocpu on 2019-03-11
I'm sorry, but I have formatted the PC because I needed it. now when I try to reinstall ubuntu it hangs on this screen without going forward [IMG]http://i66.tinypic.com/262v5vr.jpg[/IMG]

---

### Post by oldfred on 2019-03-11
Probably searching for partitions.
Do you have Windows and then is fast start up on?
Have you updated UEFI and firmware on SSD?

See more details in link in my signature for install steps.

---

### Post by emilianocpu on 2019-03-11
Thanks I'm trying to solve with the guide you indicated to me. However, I have windows and I mounted a ssd instead of a hdd but I do not think I have updated UEFI and firmware on SSD. I have already disabled fast boot. I have a question, how do I run commands during ubuntu installation?

> **emilianocpu said:**
> I'm sorry, but I have formatted the PC because I needed it. now when I try to reinstall ubuntu it hangs on this screen without going forward [IMG]http://i66.tinypic.com/262v5vr.jpg[/IMG]
I completely erased the disk and I managed to get to the next step but it stops there

---

### Post by oldfred on 2019-03-11
Please do not post screenshots or photos in line, attach them.
Easy to attach with Forum's advanced editor and paperclip icon.

Instead of booting into installer, you should be able to boot into run the live version. It is not as fast as from USB flash drive but is functional.
Do you have UEFI Secure Boot on?

---

### Post by emilianocpu on 2019-03-12
Ok i will use the paper clip. Secure boot is disabled, the live version crashes as soon as I try to use it.

---

### Post by oldfred on 2019-03-12
Have you updated UEFI?
Does it have SSD and if so updated firmware?

Some possibly similar Asus:
 Asus X541UV [SOLVED] How to partition my ssd in order to install ubuntu 17.10 / 16.04.4
[https://ubuntuforums.org/showthread.php?t=2392861](https://ubuntuforums.org/showthread.php?t=2392861)
Asus Vivobook S15
[https://ubuntuforums.org/showthread.php?t=2375408](https://ubuntuforums.org/showthread.php?t=2375408)
ASUS VivoMini UN45 UEFI update required to see NVMe drive
[https://ubuntuforums.org/showthread.php?t=2355295](https://ubuntuforums.org/showthread.php?t=2355295)
[https://ubuntuforums.org/showthread.php?t=2402972](https://ubuntuforums.org/showthread.php?t=2402972)

---

### Post by emilianocpu on 2019-03-13
I solved Updating the bios and the ssd firmware. Thank you so much for your help and availability.

---

### Post by oldfred on 2019-03-13
Please change to solved.

---

### Post by emilianocpu on 2019-03-13
Sorry, it worked for a day. Today when I tried to turn it on it started to give the error screen again. The last time before turning it off he gave me the warning in the picture. Translated means: "space in exhaustion on << root file system >> only 365.2 mb of disk space remain"

---

### Post by deadflowr on 2019-03-13
Run either the graphical program "Disk Usage Analyzer" or this simple terminal command
```
sudo du -h --max-depth=1 --exclude=/sys --exclude=/proc --exclude=/dev  / | sort -n
```

These will list where the system is eating space.

Edit: forgot to mention to post back the results, since not everything can be simply deleted.
(Some files might be removable through a variety of different things such as the package management system,
where trying to simply delete those files can have comically disastrous affects)
Posting the results can allow other users to give proper advice on what to do.

---

### Post by oldfred on 2019-03-13
See post #2. Are you using the pci=nomsi boot parameter. 
Otherwise you get the run  away log files filling drive.

---

### Post by emilianocpu on 2019-03-13
> **deadflowr said:**
> Run either the graphical program "Disk Usage Analyzer" or this simple terminal command
```
sudo du -h --max-depth=1 --exclude=/sys --exclude=/proc --exclude=/dev  / | sort -n
```

These will list where the system is eating space.

Edit: forgot to mention to post back the results, since not everything can be simply deleted.
(Some files might be removable through a variety of different things such as the package management system,
where trying to simply delete those files can have comically disastrous affects)
Posting the results can allow other users to give proper advice on what to do.

I also added another photo where you see that / dev / sda2 is full, actually it's almost empty

> **oldfred said:**
> See post #2. Are you using the pci=nomsi boot parameter. 
Otherwise you get the run  away log files filling drive.

I can't figure out where to add pci = nomsi, I enter grub but then I don't know what to do.

---

### Post by oldfred on 2019-03-13
You are showing 200GB in /var which would probably be the run away log file and you need to houseclean that out.

One time boot, you can add boot parameter like you add nomodeset example, links have screenshots:
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by emilianocpu on 2019-03-13
> **oldfred said:**
> You are showing 200GB in /var which would probably be the run away log file and you need to houseclean that out.

One time boot, you can add boot parameter like you add nomodeset example, links have screenshots:
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

I wrote like in the picture but it doesn't work. I didn't understand, should I delete the log file?

---

### Post by emilianocpu on 2019-03-13
Through an ubuntu alive I found these two files that together weigh 209.5 gb. How do I remove them?

---

### Post by oldfred on 2019-03-13
"like" the nomodeset entry process.
The boot parameter you need is pci=nomsi not nomodeset unless you also have nVidia, then you would need both.

You need to delete the log file(s)

If booted at recovery mode or in your system its small LL, not 1 or cap I.
ll /var/log/*.log
sudo rm /var/log/kern.log
sudo rm /var/log/syslog
Be very careful with any command using rm. Any extra space or other typo can destroy system and then you have to reinstall.

---

### Post by emilianocpu on 2019-03-13
This time I think I have solved, i added permanently to the kernel pci = nomsi. Thank you.

---

