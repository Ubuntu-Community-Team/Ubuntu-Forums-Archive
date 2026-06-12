---
title: "computer will not boot--hard drive partition not recognized"
date: 2022-02-03
forum: General Help
---

### Post by stbickerton on 2022-02-03
Hello folks,

I have a version of Ubuntu installed on a 640GB SSD for my Dell laptop.  I am not sure what version--I believe it is 2018 or 2019 when I installed that version of Ubuntu.  Recently, the computer would not boot up.  I pulled the hard drive out and plugged it into another computer that is running Windows 11.  Turns out, that computer will only recognize a 510MB partition and will not recognize the partition that has the Ubuntu OS and all my files installed.  I am at wit's end as I have tens of thousands of photos, hundreds of videos, and numerous documents on that drive.  Is there any way I can get my older computer (the one I normally use with this hard drive) to boot up Ubuntu on that drive and recover everything?

Thanks to all for any advice.

---

### Post by Autodave on 2022-02-03
You are going to have to connect that drive to another Linux machine since Windows does not and cannot read an ext4 file.  You could also boot your machine with an installation disk and then try to access you files that way.

There is a reason why people keep telling other people to make backups!  I have 3 backups: 2 are kept here and one at another location in case that this place would burn to the ground.

---

### Post by oldfred on 2022-02-03
Use your Windows computer to create a new current version live installer flash drive of Ubuntu.
Then use that live installer to review, or repair the SSD install when put back in your laptop.

If old install still a current version you may be able to repair it.
First check drive status with Smart Status to confirm drive is ok.
You can either install Smart Status or it already is in Disks, aka Gnome Disks if using Ubuntu. Or other flavors can install disks.
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
If drive is shown as ok/passed then if current version of Ubuntu you can repair it.

You can add this to live installer & then post report.
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

