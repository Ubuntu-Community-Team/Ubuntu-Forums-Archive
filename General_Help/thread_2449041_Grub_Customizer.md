---
title: "Grub Customizer"
date: 2020-08-18
forum: General Help
---

### Post by raleigh3 on 2020-08-18
I am trying to use Grub Customizer on grub.cfg.

I want to select which of 2 versions of Ubuntu Mate boot up.

But it is not opening the right one.

The right one is located here.

```
/media/andy/81353260-b5a5-4b72-9fce-432e7c620fdc/boot/grub/grub.cfg

```
How can I get it to open the right one?

---

### Post by oldfred on 2020-08-18
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

With multiple Ubuntu installs, last installed version is the first in boot order. And major updates, may change order depending on which is updated first.
But you can always boot into preferred install and install its grub, so it is first in boot order.
You also can edit 40_custom and copy it to 06_custom with your preferred grub boot stanza.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)

---

### Post by raleigh3 on 2020-08-19
With my installation, the older version is the default boot.

UM 20.04 "broke" my Canon TS9120 scanner.

And based on bug reports, it has broken other hardware as well.

That's why I keep 18.04 around. :-)

Maybe in a future update, the problem will be fixed.

Thanks.

I will look at your links.

---

