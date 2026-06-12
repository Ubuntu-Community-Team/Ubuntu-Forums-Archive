---
title: "Windows 11 update"
date: 2021-10-29
forum: General Help
---

### Post by jsamiry on 2021-10-29
Hi,

I am running a dual boot machine with Ubuntu 21.10 and Windows 10.  I still use the Windows when I need to print something off as I can't get my HP2960 working with Ubuntu (despite all the promises).

I try and keep the Windows up-to-date by checking for updates.  I have just received news that Windows 11 is available to download and install.  I need to know what happens should I choose to update Windows.  Will this overwrite the ability to boot into Ubuntu?  Is it easy to recover from this and restore the dual boot ability?

Thanks in anticipation.

jsa

---

### Post by Frogs Hair on 2021-10-29
The windows 11 upgrade is much like the feature upgrades on windows 10 and if you didn't have problems with those you should be ok but, there is no guarantee . If there is an overwrite of some kind, updating grub and boot repair are options. Dual booting now-days should be addressed on system by system basis, there are common elements , but no one size fits all solutions.

Edit: I had no problems with my dual boot, but use separate drives for each OS and boot priority was given to Windows prior to upgrade to Win 11.

---

### Post by grahammechanical on 2021-10-29
You are in the privileged position of being one of the first to run this experiment. After you have run the upgrade you will have more experience with upgrading to Windows 11 when dual booting with Ubuntu than most of us here. Especially me.

What usually happens when any Windows update is run? From Windows 8 and upwards? The usual will usually happen. You will not be able to load Ubuntu. You will have to select Ubuntu through UEFI settings and then if Ubuntu loads run

```
sudo update-grub
```

And see if you then get a Grub boot menu that allows you to load Windows 11. This I would suggest is the very least you must be prepared for. Microsoft developers focus on the experience of Windows users and Microsoft's business model. They give very little thought to what will happen to other operating systems that are installed. Have you read the Windows 11 release notes?

Regards

---

