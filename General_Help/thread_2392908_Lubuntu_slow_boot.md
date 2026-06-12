---
title: "Lubuntu slow boot"
date: 2018-05-27
forum: General Help
---

### Post by trelek on 2018-05-27
Hello.
Last night i decided to install Lubuntu 16 on my old laptop (HP Compaq 2710p) that I'm using when i travel.
Like in the tittle my boot time is very long. I tried the newest version Lubuntu 18 but boot time was around 4 min. After installing Lubuntu 16 its around 2 min. Sometimes it boots faster like now

systemd-analyze:
Startup finished in 16.355s (kernel) + 51.311s (userspace) = 1min 7.666s

systemd-analyze blame:
         22.022s plymouth-read-write.service
         16.376s dev-sda1.device
         11.137s systemd-udevd.service
          6.932s NetworkManager-wait-online.service
          4.362s networking.service
          3.290s NetworkManager.service
          2.229s keyboard-setup.service
          2.173s ModemManager.service
          2.047s thermald.service
          1.983s ufw.service
          1.944s systemd-journald.service
          1.574s udisks2.service
          1.511s systemd-tmpfiles-setup-dev.service
          1.474s accounts-daemon.service
          1.205s upower.service
          1.073s apparmor.service
           946ms dev-hugepages.mount
           944ms dev-mqueue.mount
           890ms gpu-manager.service
           755ms resolvconf.service
           739ms sys-kernel-debug.mount
           586ms lightdm.service
           533ms grub-common.service
           524ms console-setup.service
           499ms dev-disk-by\x2duuid-d80f3a3e\x2d4b4d\x2d462e\x2dabf6\x2df757250b8da6.swap
           435ms plymouth-start.service
           396ms rtkit-daemon.service
           391ms systemd-tmpfiles-setup.service
           384ms tlp.service
           372ms kmod-static-nodes.service
           364ms systemd-modules-load.service
           350ms systemd-update-utmp.service
           342ms systemd-sysctl.service
           281ms polkitd.service
           271ms irqbalance.service
           263ms systemd-udev-trigger.service
           224ms ntp.service
           215ms sys-fs-fuse-connections.mount
           212ms sys-kernel-config.mount
           203ms rsyslog.service
           165ms systemd-logind.service
           161ms systemd-journal-flush.service
           156ms apport.service
           154ms setvtrgb.service
           134ms ondemand.service
            88ms [email]user@1000.servic[/email]e
            71ms pppd-dns.service

So my question is: what can I do to boot it faster?

---

### Post by Autodave on 2018-05-27
Do you know the specs of that laptop?  I found several listed online and none of them are speed demons by any measure (they originally came with Win XP on them). However, I would expect Lubuntu to boot a little quicker that what you are getting right now.

The top speed I see is 1.2 ghz (1.02 standard), RAM at 1 gig, PATA HD.  You may not get much quicker than what you are getting right now.

---

### Post by mörgæs on 2018-05-27
In order to see the hardware, please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it to the command line, run it and post lshw.txt in CODE tags.

---

### Post by SL0ltMJGyh on 2018-05-27
Also, how large is your swap partition? After all you are running on an old laptop with an hdd and swap space will only slow down your machine. Type "swapon --summary" to figure out how much swap space you have set up. 

**Quick swap explanation:** when you're out of memory, Linux sends processes that are hogging memory and not doing anything to swap space- a partition on your hard disk which functions as longer term storage for RAM. Due to this, you will see significantly slower speeds when using swap space. your best bet is to disable it if you haven't already.

**Article on Disabling Swap Space: **[https://askubuntu.com/questions/214805/how-do-i-disable-swap](https://askubuntu.com/questions/214805/how-do-i-disable-swap)

---

