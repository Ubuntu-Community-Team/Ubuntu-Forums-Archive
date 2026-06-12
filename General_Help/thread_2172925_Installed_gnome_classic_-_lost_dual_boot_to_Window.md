---
title: "Installed gnome classic - lost dual boot to Windows"
date: 2013-09-06
forum: General Help
---

### Post by Barney on 2013-09-06
Installed gnome (no effects); lost dual boot to Windows; GParted does not show any Windows partition..??????  Have I lost my Windows 7 - was critical to read medical reports.

---

### Post by kansasnoob on 2013-09-06
> **Barney said:**
> Installed gnome (no effects); lost dual boot to Windows; GParted does not show any Windows partition..??????  Have I lost my Windows 7 - was critical to read medical reports.

Stop using the newly installed OS immediately! Use only the live media you used to to install Ubuntu and post a new thread here:

[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

Please explain exactly how you installed, what media was used, etc.

Someone may be able to help you recover some of your data using TestDisk and/or PhotoRec.

---

### Post by Barney on 2013-09-06
Some time ago, I followed the yellow brick road from: 12.04 LTS / Precise Classic (No effects) Tweaks and tricks to change to the gnome desktop; and sometime after that I noted that the Windows option was missing when I rebooted.  Both GParted & testdisk show no partitions other than those required for Ubuntu.  Looks like I've lost Windows.  I wish that I had stuck with 10.04.  For me, Ubuntu made a mistake not just improving upon 10.04 LTS - newer, better, and fancier ain't always better; a la Windows moving on from Windows XP Pro.  Can anyone suggest some Ubuntu software that can read DICOM, as on a catheterization disk?

---

### Post by kansasnoob on 2013-09-06
> **Barney said:**
> Some time ago, I followed the yellow brick road from: 12.04 LTS / Precise Classic (No effects) Tweaks and tricks to change to the gnome desktop; and sometime after that I noted that the Windows option was missing when I rebooted.  Both GParted & testdisk show no partitions other than those required for Ubuntu.  Looks like I've lost Windows.  I wish that I had stuck with 10.04.  For me, Ubuntu made a mistake not just improving upon 10.04 LTS - newer, better, and fancier ain't always better; a la Windows moving on from Windows XP Pro.  Can anyone suggest some Ubuntu software that can read DICOM, as on a catheterization disk?

Nothing shown in this thread has to do with re-installation and could not in any way result in data loss or erasing any existing partitions. How did you get to 12.04 from 10.04? We need to know what you mean by "the yellow brick road".

I have no idea what "DICOM, as on a catheterization disk" even refers to :confused:

I can tell you that the longer you use a newly installed OS after overwriting any existing partitions/data the less likely you are to be able to recover any lost data. That's why I suggested what I did in my previous post.

---

### Post by cariboo on 2013-09-06
The only thing I could find on DICOM is [here]("http://medical.nema.org/")

---

### Post by coffeecat on 2013-09-07
@Barney, I've moved your posts, plus the specific replies, to their own thread. The thread you posted to is for support for installing and configuring gnome classic no effects. Your loss of a dual-boot is a separate problem and the request for suggestions for software is not relevant, therefore you are better off in your own thread.

Good luck with getting solutions to the problems you describe.

---

### Post by oldfred on 2013-09-07
For Boot issue we need more information.

 
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Barney on 2013-09-08
For viewing medical data such as catheterization and ct-scan disks, I found Aeskulap Viewer in the  Ubuntu Software Center on both 10.04 and 12.04 - works fine.

---

