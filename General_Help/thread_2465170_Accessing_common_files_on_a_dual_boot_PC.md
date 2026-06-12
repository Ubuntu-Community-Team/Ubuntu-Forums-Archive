---
title: "Accessing common files on a dual boot PC"
date: 2021-07-23
forum: General Help
---

### Post by arthur1337 on 2021-07-23
So i have a PC with a dual boot between Windows 10 and Ubuntu (im really new to linux community ) and i need help is there a way i can access the same files on the hard drive between both OS?
like create a partition which both OS can read and write to?

---

### Post by Impavidus on 2021-07-24
Yes. Make sure there's an NTFS partition separate from your Windows OS partition. Windows will call it D: or E: or something like that. Use /etc/fstab to mount it automatically at some convenient location in Ubuntu. Fast startup must be switched off, or Ubuntu can't use it.

Ubuntu can also access the C: partition, with the Windows OS, but there's significant risk of damaging it, which could render Windows unbootable, so it's better to stay away from that.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by dragonfly41 on 2021-07-24
As above advice, I use a simple NTFS partition named SHARE.
If you use apps which are cross platform - one example being [CherryTree note editor]("https://github.com/giuspen/cherrytree")[ ]("https://www.giuspen.com/cherrytree/")- you can open such cross platform apps files just by double clicking.
Other Ubuntu apps such as LibreOffice can also install into Windows 10.
Yet another approach is to have a Dropbox account for file sharing.

---

### Post by ActionParsnip on 2021-07-24
Then simply mount it using /etc/fstab and you can share data between. Windows cannot access many file systems so this is why you should use NTFS. To accommodate the shortcomings of Windows. Be sure that the data is complete and consistent if you get mount issues. NTFS is proprietary to Microsoft and only they know how it fully works. The NTFS access in Linux is a best effort attempt.

---

### Post by arthur1337 on 2021-07-27
Thanks all of you, it worked!!! 

(Awesome community response damn)

---

