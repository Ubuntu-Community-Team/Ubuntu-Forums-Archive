---
title: "Mysterious Swap RAM Drive"
date: 2013-03-14
forum: General Help
---

### Post by Trapper on 2013-03-14
Somehow, I have mysteriously acquired an additional swap partition. Actually it's a RAM drive designated for swap and when I do 'free' it shows as an additional 998MB added to my current swap of 4GB. This RAM drive is shown as /dev/zram0 by blkid. Nothing for it shows with fdisk -l. The only items listed for mount in my fstab is / and my normal swap partition. This unwanted and never created (by me) swap mounts at every boot. I have no idea where it came from, how it is getting mounted or why. What else besides fstab would possibly be controlling this? I really, really want to get rid of it.

---

### Post by ManamiVixen on 2013-03-14
[http://superuser.com/questions/460815/mounts-not-present-in-fstab-where-are-they](http://superuser.com/questions/460815/mounts-not-present-in-fstab-where-are-they)
This may help.

Also, try looking for it in /etc/mtab

---

### Post by Trapper on 2013-03-14
> **ManamiVixen said:**
> [http://superuser.com/questions/460815/mounts-not-present-in-fstab-where-are-they](http://superuser.com/questions/460815/mounts-not-present-in-fstab-where-are-they)
This may help.

Also, try looking for it in /etc/mtab

Thanks for your reply. There's definetly nothing referring to it in mtab, The link you provided didn't actually provide much information useful for me. That may be a matter of my lack of understanding but nothing rang an idea bell for me.

---

### Post by LewisTM on 2013-03-14
This looks like a zram setup. Nothing to worry about, it's used to increase memory efficiency by compressing unused data in RAM. Not sure how you got it without installing zram-config. Did you install an exotic or development-stage distro?
Just to make sure, please post the output of
```
swapon -s
```
Cheers!

---

### Post by Trapper on 2013-03-14
> **LewisTM said:**
> This looks like a zram setup. Nothing to worry about, it's used to increase memory efficiency by compressing unused data in RAM. Not sure how you got it without installing zram-config. Did you install an exotic or development-stage distro?
Just to make sure, please post the output of
```
swapon -s
```
Cheers!

No need to provide you with the output of swapon -s now because it's as it should be now. I have been doing some researching regarding zram. I did not have it installed. Just after my last post here I disabled my normal swap in fstab and rebooted. My 'free' then displayed '0' and blkid did not display the zram entry anymore. I enabled my normal swap again in fstab and after reboot I had my normal sized swap space and no zram being mounted.

This zram problem popped up on first boot of my install and I figure it had something to do with the install. However, I have installed the same release on this machine on several occasions and never had it happen before. I am actually using Linux Mint 13, which equates to U12.04.

Interestingly, I attempted to install zram-config just a while ago. The install didn't complete the first attempt. I purged and reinstalled successfully. However, running sudo zram-config gets me nothing but a message that there's no such command.

Whatever, the zram vanished just as mysteriously as it appeared so I will consider this thread solved but I'll still be researching this and if I discover anything that sheds more light I will post it. Thanks for your help!

---

