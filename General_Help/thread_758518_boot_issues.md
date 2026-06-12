---
title: "/boot issues"
date: 2008-04-18
forum: General Help
---

### Post by ProbablyX on 2008-04-18
Hello!

I installed Kubuntu last night on my old Debian partition setup (reformated).

After having ran an update I noticed that my /boot got full after which I get weird disk errors on boot.

As I could still access my drives from the Kubuntu CD I decided to "ignore" the /boot partition and only use / and /home partitions.

Naturally I completely forgot that my PC will try to boot /boot anyway, as it still exists.

/boot is hdc1 and / is hdc5. Can I make the currently (messed up...) GRUB in hdc1 redirect to the GRUB found in the boot directory in hdc5?

/home os hdc7 which I think is extended and not primary, in case I cant redirect /boot can I erase hdc5 and hdc1, make a new / and keep hdc7 with any nifty tool found on the Kubuntu CD (I cant find qtparted)

Thanks!

---

### Post by AlphaWu on 2008-04-18
U can use Ubuntu LIVE CD to boot your system.Then edit your grub/menu.lst

---

### Post by ProbablyX on 2008-04-18
Hi!

Thanks for replying, the boot CD just boots the "first harddrive" which is /boot =/

---

