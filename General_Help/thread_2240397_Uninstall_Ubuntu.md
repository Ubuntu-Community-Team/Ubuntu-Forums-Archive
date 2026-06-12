---
title: "Uninstall Ubuntu"
date: 2014-08-19
forum: General Help
---

### Post by dave142 on 2014-08-19
Hi guys I am hoping someone with good knowledge can help out here.

I installed Ubuntu along side Windows 8.1, no issues, except for when I pulling the slider back n forth to choose the partition size for ubuntu installation I didn't know which way to pull it for leaving the windows partition with more space and I ended up sliding to far the wrong way (bare in mind there are no labels which side is which) and ended up with hardly any space on the windows side, now I am absolutely sick and fed up with ubuntu and have installed it on my laptop instead, however I cannot reclaim the space or get rid of ubuntu at all. There is no option to uninstall it that I can see and I can't even delete it because I can't see the ubuntu partition to do so.

Can someone tell me is there somewhere within Ubuntu that can help with this or could someone tell me how to get rid of it? I never had this issue before I upgraded to Windows 8.1 from Windows 7.

Thanks to anyone who can help out.

---

### Post by oldfred on 2014-08-19
Always resize Windows from inside Windows. And reboot immediately as it has to run chkdsk to make repairs for its new size.

You will need the Windows boot loader in the MBR. If Ubuntu still works you can easily reinstall a Window type boot loader. Or use your Windows repairCD or flash drive to install a Windows boot loader.
But if you have not booted Windows it may still need the chkdsk before it works, and you cannot do that from Linux.

Post this from either your Ubuntu or a live installer you used to install Ubuntu.
sudo parted -l

You can post the link this gives to make sure Windows at least looks ok, if it gives errors on mounting NTFS partition then that is from it needing chkdsk.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If Windows looks good then you can use Boot-Repairs advanced options to install a Windows boot loader to the MBR. And if Windows boots ok or you can use f8 to get into repair console to fix it, then from Ubuntu live installer use gparted to remove Linux ext4 and swap partitions. Then use Windows to resize its own NTFS partition.

      
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

[http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx)

 How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by QIII on 2014-08-19
Moved to General Help.

---

