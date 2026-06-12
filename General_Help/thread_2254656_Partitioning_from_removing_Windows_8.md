---
title: "Partitioning from removing Windows 8"
date: 2014-11-28
forum: General Help
---

### Post by dagitab on 2014-11-28
Hi, guys.

So my computer used to be on dual boot, Windows 8 and Ubuntu 14.04. My computer is running on SSD, and I'm almost through using up the memory for the linux partition. I removed the Windows partition using OS-uninstaller and now I don't know where it went. :( Help me regain this huhu I really need the memory

---

### Post by Bucky Ball on 2014-11-29
Welcome. Do you mean you need the free disk space? Memory refers to RAM generally. ;)

Can you boot from install media (i.e. a disk or USB)>'Try Ubuntu'>once at a desktop launch Gparted. That will show you what you now have on the drive. Post a screenshot of that here if possible.

Your post is a little unclear, but I am presuming you were wanting to get rid of Windows and now you have you are unsure where the free space has gone? If you wanted to free up space to expand the Ubuntu partition, then expanding the Ubuntu partition should be done when booted from install media, also. The Ubuntu / partition needs to be unmounted to resize it and this is not possible if you are running the hard drive install of Ubuntu. 

;)

---

### Post by Sef on 2014-11-30
For more information about GParted, click [here]("http://gparted.org/").

---

### Post by nerdtron on 2014-11-30
Really unclear. Please provide details on what steps you have done.
This one is really puzzling as it is the first time I heard it.
> I removed the Windows partition using OS-uninstaller

---

### Post by oldfred on 2014-11-30
Os-uninstaller is part of Boot-Repair.
But I thought it just converted booting to which ever install you wanted, but did not delete partitions?

Best to see details. Post link to summary report.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Current version ppa now available.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by nerdtron on 2014-11-30
So Boot-Repair have that feature now. Haven't used it in ages.

---

### Post by oldfred on 2014-11-30
OS-Uninstaller is/was part of the full CD download of the live version. 
Not sure if that also has has been updated to the latest version or not, yet. 
Yann just updated Boot-Repair ppa to have current versions available, but that just downloads the Boot-Repair not the other apps.

---

