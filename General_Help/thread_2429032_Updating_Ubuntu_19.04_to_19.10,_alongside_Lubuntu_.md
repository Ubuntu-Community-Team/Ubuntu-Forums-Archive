---
title: "Updating Ubuntu 19.04 to 19.10, alongside Lubuntu LXQt desktop 0.14.1"
date: 2019-10-12
forum: General Help
---

### Post by dee-2019 on 2019-10-12
Hi all,

I am new to Ubuntu Forms. I have Ubuntu 19.04 and plan to upgrade to 19.10 (Eoan Ermine). Due to low spec computer (netbook with 2gb RAM), I installed Lubuntu LXQt desktop 0.14.1(Budgie) and works great and really pleased with how fast and light it is. 
However, my question is what will happen when I upgrade to Ubuntu 19.10, will my LXQt desktop still work? I really don't want to mess this up or loose it, as it work so well. I did increase swap folder also, so that probably helped too. 

But question is will I loose it all when I upgrade to Ubuntu 19.10. Of course, I have to upgrade by Jan 2020, as this release will no longer be supported but might upgrade before then. 

Thanks in advance to anyone who can help me in understanding this. 

:KS

---

### Post by CatKiller on 2019-10-12
When you upgrade from one release to another, mechanically it changes the repository locations to those of the new release and then upgrades every package to the new versions. It's broadly the same as running your normal updates.

However, because so many interdependent packages are being updated all at once, some people have experienced problems; particularly if they've installed a bunch of software from other sources. It's only really the default packages from the default repositories that there is the manpower to test prior to release. I've personally never had problems doing the upgrade, but it's worth taking a backup first, just in case. A fresh install takes about 20 minutes, and restoring from backup probably about the same, so if it all goes pear shaped it's not too big of a deal.

If you installed your desktop environment from the Ubuntu repositories you'll probably be fine. If it's from a PPA you may need to wait till that PPA is updated for Eoan.

---

### Post by dee-2019 on 2019-10-14
Hi there, many thanks for your reply. I won't bother reinstalling at present, as it's working fine, rather was more probably anxious of when I upgrade to Eoan, what would happen with desktop version. Ubuntu 19.04 was installed from iso or usb, as someone helped me install it, but either way I will wait for update of Eoan. Ubuntu was installed for me, and had no problems with it, but just needed a more lightweight desktop, which is why I installed Lubuntu on top, and really don't have any issues with it. It runs very well. I don't want to mess around with installing again, as before when trying to install ubuntu, I messed up the partitions, which is why I got help with getting it installed. I've also go to use my netbook a lot, so if it's causing no problems, I will leave it just as it is. I can switch between desktops also go back to Ubuntu, or uninstall Lubuntu desktop and then reiinstall. I think so long as I know what I'm doing it will be ok. Thanks so much for your help, just saw it today, as didn't get notified of it.

---

