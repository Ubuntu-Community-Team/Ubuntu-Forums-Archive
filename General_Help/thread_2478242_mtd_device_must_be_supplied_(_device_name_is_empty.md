---
title: "mtd device must be supplied ( device name is empty )"
date: 2022-08-20
forum: General Help
---

### Post by drew1121 on 2022-08-20
I recently updated my PC from Xubuntu 20.04 to Xubuntu 22.04 and while it works I have a question about this message that appears at startup. What does this message mean and is it in any way harmful?

---

### Post by oldfred on 2022-08-20
Similar thread. do you have nVidia?

mtd device must be supplied
[https://ubuntuforums.org/showthread.php?t=2476796&page=3](https://ubuntuforums.org/showthread.php?t=2476796&page=3)
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1981622](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1981622)

---

### Post by drew1121 on 2022-08-21
Yes i have nvidia

---

### Post by ajgreeny on 2022-08-21
Don't worry about the message as long as it does not stop your machine from booting.

I have seen this happen for quite a long time now, certainly since installing Xubuntu 22.04, even though I do not use an nvidia graphic card but I get to the usual desktop with no delay so have ignored it.

---

### Post by Claus7 on 2022-08-21
Hello,

> **ajgreeny said:**
> ...but I get to the usual desktop with no delay so have ignored it.

are you sure that it doesn't delay your boot time? Until I see all three lines, too much time has passed (using hdd).

Regards!

---

### Post by yetimon_64 on 2022-08-21
> **Claus7 said:**
> ...are you sure that it doesn't delay your boot time? Until I see all three lines, too much time has passed (using hdd)...
If you feel that it is slowing down the boot then I'd suggest you try the workaround in the bug report link oldfred posted in post #2. If you do check out the bug report workaround make sure you log in to the launchpad site or some of the commands may be masked as an email address.

The issue here (on an nvidia/intel hybrid graphics setup) did tend to spam the boot screen and slowed down my boot slightly so I ran that workaround and all is back to normal here.

---

### Post by Claus7 on 2022-08-21
Hello,

> **yetimon_64 said:**
> If you feel that it is slowing down the boot then I'd suggest you try the workaround in the bug report link oldfred posted in post #2. If you do check out the bug report workaround make sure you log in to the launchpad site or some of the commands may be masked as an email address.

The issue here (on an nvidia/intel hybrid graphics setup) did tend to spam the boot screen and slowed down my boot slightly so I ran that workaround and all is back to normal here.

thank you for your reply. So its not only in my system. I was thinking to do it, yet in many flavours/versions that had this issue, seems to be getting fixed, so I would rather wait a little longer in case this goes away "on its own".

Regards!

---

### Post by VMC on 2022-08-21
Here is the [similar thread ]("https://ubuntuforums.org/showthread.php?t=2476796&page=3&highlight=mtd")Fred was mentioning, also the bug report:
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1981622](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1981622)

---

### Post by ajgreeny on 2022-08-26
> **Claus7 said:**
> Hello,



are you sure that it doesn't delay your boot time? Until I see all three lines, too much time has passed (using hdd).

Regards!
To be honest I am not 100% sure there is not any delay in boot time but I reboot only when necessary so seldom more than weekly, often a lot longer and only when the system tells me it's needed.

However, if there is a delay it is so short that it is not worth bothering with.

---

### Post by Claus7 on 2022-08-27
Hello,

> **ajgreeny said:**
> ...
However, if there is a delay it is so short that it is not worth bothering with.

Lucky for you. I have tried almost every solution proposed by *oldfred*, yet my system boot time has doubled from the days of bionic. It takes time until that message disappears from my screen, yet it boots normally. Every aspect that reduces that time is welcome.

Regards!

---

### Post by kurt18947 on 2022-08-27
If you want to reduce boot time, would installing an SSD in place of your HDD be a possibility? There are benefits to SSD beyond faster boot times. You could use a disk imaging program to expedite switching disks. Once the new drive is in place and confirmed to be reliable, place your existing HDD in a USB hard drive enclosure for backups.

---

### Post by Claus7 on 2022-08-31
Hello,

> **kurt18947 said:**
> If you want to reduce boot time, would installing an SSD in place of your HDD be a possibility? There are benefits to SSD beyond faster boot times. You could use a disk imaging program to expedite switching disks. Once the new drive is in place and confirmed to be reliable, place your existing HDD in a USB hard drive enclosure for backups.

not at the time being. With a fresh installation of kinetic a couple of days ago, this message is not shown any more. II will see what will happen in future upgrades and if this disappears completely as already fixes are under way. It might not affect the boot time at all, and its just that boot time is what it is.

Regards!

---

### Post by oldfred on 2022-08-31
There are a bunch of threads on boot time.
I use Kubuntu which is a bit faster.

Slow Boot --------------------------------
[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)
[https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/](https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/)

[https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster](https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster)

[https://askubuntu.com/questions/1187117/slow-boot-boot-19-10-tried-almost-everything](https://askubuntu.com/questions/1187117/slow-boot-boot-19-10-tried-almost-everything) & 
[https://askubuntu.com/questions/1018576/what-does-networkmanager-wait-online-service-do](https://askubuntu.com/questions/1018576/what-does-networkmanager-wait-online-service-do) & 
[https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service](https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service)

---

### Post by Claus7 on 2022-08-31
Hello *oldfred*,

thank you for your response. If you see above you will see that I have followed most if not all of  your suggestions. I haven't seen an improvement. I also noticed from virtualbox that the boot time was much longer with jammy instead of bionic, so I have accepted that ~2min boot time using an hdd is normal. I do not want to mess with the OP, so I leave it here. I just tried to figure if this message extends boot time and if disappears will reduce it, because in my screen it is displayed for a long time until it disappears in contrast to other users. Just that.

Thanks again,
Regards!

---

