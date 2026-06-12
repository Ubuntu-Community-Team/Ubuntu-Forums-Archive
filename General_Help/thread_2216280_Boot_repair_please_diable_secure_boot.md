---
title: "Boot repair please diable secure boot"
date: 2014-04-11
forum: General Help
---

### Post by hemoali on 2014-04-11
Welcome guys ,
i have toashiba laptop with win 8 installed I installed ubuntu 12.4 without diabling secure boot
Ubuntu works very well but now I cannot access win 8
when trying to use boot repair it gives an alert 

Please disable secure boot....

I skipped this alert and continued ahead

now windows in on my boot menu but when choosing it, it says some file cannot be found 
then it's the dead end 

So any suggestions ?

---

### Post by oldfred on 2014-04-11
Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Generally better to have secure boot off. 
Also if you upgrade to 8.1, you will not be able to dual boot with secure boot on from grub menu. Windows changed something and now grub has to be modified.


 Unable to chainload Windows 8 with Secure Boot enabled  Also post #11 on using refind
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)

Windows also may be turning fast boot or secure boot back on with updates, so you may have to periodically reset those to off. It also likes to reset itself as default in boot order.

---

