---
title: "Bitlocker prevents me from accessing HD"
date: 2018-07-07
forum: General Help
---

### Post by haramara on 2018-07-07
I am having a dual boot on my system. On my sdd I have a partition for win10 and one for ubuntu 16.04. This works fine so far. Beside I have a HD to store data. The data on the HD should be accessible from both systems.

I can open the HD in win10, but not in linux. Gparted tells me that the file system of the HD is bitlocker and win10 says that it is NTFS (bitlocker encrypted). 

The problem is that I never activated bitlocker in Windows. It is also not possible to disable it, because it was never activated.

I simply don't need to use bitlocker and would be happy to get rid of that trouble.

How can I access my HD when using Linux? What will I have to to within win10 or ubuntu? 

Thank you for your attention!

---

### Post by TheFu on 2018-07-07
> win10 says that it is NTFS (bitlocker encrypted). 

You should use Windows to correct that.
Google found this: [https://www.tenforums.com/antivirus-firewalls-system-security/101145-bitlocker-automatically-enabled-ntfs-partition-how-disable.html](https://www.tenforums.com/antivirus-firewalls-system-security/101145-bitlocker-automatically-enabled-ntfs-partition-how-disable.html)

---

### Post by haramara on 2018-07-08
Thanks for that advise. I tried that already out before and it didn't work.

I found the solution on my own:

Strangely Windows already encrypted my drive while I was setting it up. But since I didn't create a windows account as authentication, the process wasn't completed. I just have normal account and I would have needed to complete the process on my own.

That's what I did. I chose to "activate" encryption for my drives and afterwards I decrypted them both. Now everything works fine again.

---

