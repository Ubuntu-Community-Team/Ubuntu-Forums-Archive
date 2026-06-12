---
title: "How to access an encrypted filesystem from another pc"
date: 2023-12-01
forum: General Help
---

### Post by rvt on 2023-12-01
Hi,

I'm trying to recover data from a drive from my laptop which won't boot anymore. The laptop was running Ubuntu 23.10, I wanted encryption and during the install I was forced to pick zfs for this. I pulled out the drive and I'm just trying to mount it as an external drive now. I tried using my other pc which is running mint however zfs complained something was missing from my mint install (which is the latest) so now I'm trying to access these files by just booting this pc with the legacy 23.10 usb installer and trying to mount my hdd from my broken laptop.

I see bpool & rpool in the sidebar, when I click on them I get "filesystem type zfs_member not configured in kernel". Then I run zpool import rpool, and I see everything fine under zfs list, here I even see my home directory which I would like to get to. I also get a new drive pop up in the sidebar, it's only 500Mb, but I mount it and enter my password. It mounts to /media/ubuntu/keystore-rpool, there is a single file called system.key. I still get the same error above when clicking on rpool to mount it. 

Seems like this isn't decrypting properly or this isn't the right way to do it, so at this point I don't really know how proceed to finish this off so I can (hopefully) access everything unencrypted.

thanks!

---

### Post by rvt on 2023-12-01
I followed this more or less and it works fine: 

[https://toabctl.wordpress.com/2023/05/10/mounting-an-encrypted-zfs-filesystem/](https://toabctl.wordpress.com/2023/05/10/mounting-an-encrypted-zfs-filesystem/)

---

### Post by MAFoElffen on 2023-12-01
I do this for my customers... 

It's easier if you have it connected directly to a controller (as you found), rather than using a USN drive caddy... Though I also use a drive caddy that I can plug in 3-1/2, & 2-1/2 HDD's and SSD's. But I have hot swap drive bays that I can plug drive into.

Do you want it fixed, where you can boot it again??? To, me, that makes sense. Dump the data to an external drive for the just in cases before you make changes, the get it working again.

in this post I wrote last night is instructions to unlock and mount the pools: [https://ubuntuforums.org/showthread.php?t=2493026&p=14167407#post14167407](https://ubuntuforums.org/showthread.php?t=2493026&p=14167407#post14167407)

After you mount the pools, I would first rsync anything you want off it...

Then you could reinstall grub and the last kernel, and see if it boots. Then tell me where it ends up from there... There are tricks to get things going again.

---

