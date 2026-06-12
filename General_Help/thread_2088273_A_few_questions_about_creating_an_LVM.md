---
title: "A few questions about creating an LVM"
date: 2012-11-26
forum: General Help
---

### Post by Starks on 2012-11-26
My current setup is a 18GB root, 400GB /home, 2GB swap, 80GB Windows.

Is /home automatically separated?

Can I reinstall root without wiping home?

How much space on my 500GB drive should be allocated to the LVM? It'll dual-boot with a Windows 8 partition. This partition will also be the one that both OSes share.

---

### Post by HermanAB on 2012-11-26
No.
Depends.  If you install and ensure that /home is a separate partition, then yes.

---

### Post by oldfred on 2012-11-26
Why do you want LVM?

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

    
I am sure you cannot have Windows in the LVM.

Also best not to share the Windows system partition. Windows does not like too many writes into it and now Windows 8 is always in hibernation. Best to set as read only in Ubuntu and use another shared NTFS data partition.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by Starks on 2012-11-26
It's not that I want to use LVM, but it seems like something interesting to try during my yearly partition table wipe. Partition resizing is an all-night afair with my current set up and it really sucks.

I appreciate the info regarding Windows. I'll probably have to do a separate NTFS partition as you mentioned since data integrity will be important.

I'm a bit confused about whether /boot should be separate or part of the LVM. I don't normally use /boot partitions.

---

### Post by Starks on 2012-11-29
One more bump

---

