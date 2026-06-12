---
title: "Re-initialise Grub or Manually change UUID"
date: 2014-11-10
forum: General Help
---

### Post by netsurfau on 2014-11-10
So, the (seemingly) continuing effort to get my system back working continues.

After getting my last lot of issues sorted out, I had two attempts at a clean install of 14.04 on sd1, using nearly the entire 500Gb as sda.
With both clean installs, random applications just would not load.  Eg; Ubuntu Software Centre wouldn't load on the second install, no
matter how many times I clicked on the icon.

So, instead I decided to copy this properly working partition on to sd1.  This worked fine but, when I reboot and try to access sda, grub
gives an error message about a missing UUID and wont load, forcing another reboot & my having to revert back to this partition.  I have
searched through the grub files and can find no reference to the UUID that it is looking for

While trying to find the manual or help pages for grub, the system tells me that it isn't installed. :confused:

What I need to do now is either, reinitialise grub so it works with the current configuration or manually change the UUID on sda to the
one grub is searching for.

Is either of these possible, and how do I go about doing them.

---

### Post by oldfred on 2014-11-11
I think we need to see details.
If you copied install, you may have duplicate UUIDs.

If you have multiple drives, do not run the auto fix. It just installs one grub to every MBR, and usually you want different grub boot loader or a Windows boot loader in other MBRs.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by netsurfau on 2014-11-11
@oldfred: I'm beginning to wish I could afford to keep you on retainer. :lolflag:

Boot Repair seems to have sort of worked.  I don't get an error when trying to access sda1.
What does happen is, if I select the sda1 partition with a copy of 14.04 on it, I end up logging into sdb5, which is the partition I created
as a working partition to recover my system.  There are no indications during boot up, to explain why this is happening.

As I mentioned in my original post, every time I try performing a clean install of 14,04 on to sda, a number of the pre-installed applications
just refuse to load when selected.  Another issue in itself, which has me somewhat confused.

The Boot Repair log can be found at:  [http://paste.ubuntu.com/8952446/](http://paste.ubuntu.com/8952446/)

Open to any suggestions you may have.

---

### Post by oldfred on 2014-11-12
Your grub.cfg in sda1 uses the UUID of sdb5, so if you boot from sda1 you actually boot sdb5.
Fstab in sda1 also uses sdb5 UUIDs.

If you want to try to use sda1, you need to manually update fstab with correct UUIDs and reinstall grub. After updating fstab, it may be easier to just use Boot-Repair's advanced mode to totally uninstall grub & reinstall.

Often just easier to do a new install to sda.
I do prefer to use smaller system partitions like 20 or 25GB for / (root) and separate /home or data partition(s).

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)

---

### Post by netsurfau on 2014-12-07
G'day Fred,

Sorry for delay in replying, my health is up & down like a yo-yo.

I finally found out the root cause of all my problems with this system.  A slowly dying 500Gb Western Digital hard drive.
I started having funny little problems about 12 months ago, which progressively got worse, and it all came down to a faulty HD.

A couple of days after your last reply, the HD finally died entirely.  I put in a new 500Gb Toshiba drive, gave a clean install, moved
the back-up of my Home directory across & it's been "clear sailing" ever since.

I liked it better when hard drives just died quickly, not like these more modern ones.  A friend had a 1Tb WD drive do the same thing, so
I won't be using that brand of drive ever again.

Thanks again for all your help, it was truly, greatly appreciated.

Hope you have a wonderful Holiday Season with the one's you love.

Luke

---

### Post by Bucky Ball on 2014-12-07
If you are satisfied with the fix, could you please mark thread as solved to help others. See how in the second link in my signature.

Good luck with your health and everything else. ;)

---

