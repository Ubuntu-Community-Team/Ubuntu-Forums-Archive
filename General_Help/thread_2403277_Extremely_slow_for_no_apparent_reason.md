---
title: "Extremely slow for no apparent reason"
date: 2018-10-09
forum: General Help
---

### Post by koma77 on 2018-10-09
I have a headless server running Ubuntu 18.04.1. I've had this server for years and upgraded to every new Ubuntu release. Now, all of a sudden, my machine is extremely slow and I cannot figure out why.

I have checked the disk status (an SSD), and it reports no errors and self tests pass OK. I have checked that the CPU runs at nominal speed (1.5 GHz), an Intel Atom so it is not lightning fast, but still. I did a dd with 100 MB of /dev/zero, and that write was fast. Network (Ethernet) shows no obvious problems. Nothing special in the system log or in the kernel log. No real load on the system either. There is plenty of free RAM and no swap is being used. It "looks" good, but is really slow.

But still, things like running apt or logging in through ssh takes forever. Booting takes more than 10 minutes. It used to boot within a minute.

How can I track down what is going on?

Here is the output of systemd-analyze blame

```
   18min 52.195s apt-daily.service
   12min 18.923s apt-daily-upgrade.service
         50.289s networking.service
         46.111s dev-sda1.device
         42.989s postfix@-.service
         39.677s networkd-dispatcher.service
         26.157s mysql.service
         22.253s keyboard-setup.service
         14.840s systemd-udev-trigger.service
         11.797s apache2.service
         11.338s accounts-daemon.service
         10.593s apparmor.service
          9.416s systemd-journald.service
          7.802s apport.service
          7.746s wpa_supplicant.service
          7.706s systemd-timesyncd.service
          7.676s grub-common.service
          7.542s systemd-resolved.service
          6.498s systemd-logind.service
          5.964s systemd-rfkill.service
          5.189s saned.service
          4.997s systemd-journal-flush.service
          4.881s ssh.service
          3.442s phpsessionclean.service
          3.046s rsyslog.service
          2.728s polkit.service
          2.138s user@1000.service
          2.081s dev-mqueue.mount
          2.042s dev-hugepages.mount
          1.980s ufw.service
          1.952s systemd-random-seed.service
          1.932s systemd-update-utmp.service
          1.840s systemd-tmpfiles-setup-dev.service
          1.717s systemd-modules-load.service
          1.715s systemd-tmpfiles-setup.service
          1.659s sys-fs-fuse-connections.mount
          1.625s fail2ban.service
          1.612s kmod-static-nodes.service
          1.501s systemd-udevd.service
          1.501s systemd-user-sessions.service
          1.500s systemd-remount-fs.service
          1.418s loadcpufreq.service
          1.395s sys-kernel-debug.mount
          1.385s systemd-sysctl.service
          1.139s pppd-dns.service
          1.079s sys-kernel-config.mount
          1.032s dns-clean.service
          1.015s systemd-tmpfiles-clean.service
           871ms systemd-update-utmp-runlevel.service
           722ms resolvconf.service
           704ms cpufrequtils.service
           657ms resolvconf-pull-resolved.service
           647ms plymouth-read-write.service
           617ms plymouth-quit-wait.service
           556ms plymouth-quit.service
           530ms dev-disk-by\x2duuid-1e9a59ca\x2de080\x2d4554\x2d9e1d\x2d22b073b0d362.swap
           481ms console-setup.service
           452ms apache-htcacheclean.service
           329ms setvtrgb.service
           324ms ureadahead-stop.service
           169ms postfix.service

```

---

### Post by TheFu on 2018-10-09
You can disable apt-daily-service and manually patch.  I manually patch every Saturday morning to avoid interruptions on work days.
[https://askubuntu.com/questions/1038923/do-i-really-need-apt-daily-service-and-apt-daily-upgrade-service](https://askubuntu.com/questions/1038923/do-i-really-need-apt-daily-service-and-apt-daily-upgrade-service) explains:
```
sudo systemctl disable apt-daily.service
sudo systemctl disable apt-daily.timer

sudo systemctl disable apt-daily-upgrade.timer
sudo systemctl disable apt-daily-upgrade.service

```
There are a bunch of other things in the startup that I'd remove too, but if those are important to you, it wouldn't be good. 
 For example, I don't want any FUSE file systems on my servers. FUSE is slow. If the "server" is also a desktop, FUSE might be very important.  I wouldn't have any php on my servers either.

---

### Post by Autodave on 2018-10-09
I would definitely try what TheFu suggested before anything else.  The only thing that I would add is that upgrading from one version to another sometimes creates a lot of issues.  I have always found it to be a lot easier and faster to just do a clean install.  I don't know if that is an option for you or not.  Of course, if you decide to do a clean install, make sure that you have good backups of everything first.

---

### Post by koma77 on 2018-10-09
Thank you for replying - I will definitely disable the apt-daily stuff. 
Something must have happened: it takes 18 minutes to boot, an 18-fold increase.

Is oprofile still around? Or how would you try and find the reason for this kind of issues?

---

### Post by koma77 on 2018-10-09
I ran operf on a "apt update" comman (which took forever). 
Surprisingly enough 50% of the samples from the profiler came from some sort of GPIO-handling:

```
samples  %        image name               app name                 symbol name
2198106  50.2755  kallsyms                 apt                      byt_gpio_irq_handler
```

So, does this perhaps mean that my kernel is busy handling GPIO interrupts? But why?

---

### Post by TheFu on 2018-10-16
Gigabyte motherboard?  If so, which kernel?  Just saw mention of an Ubuntu-specific kernel issue with GPIO on Gigabytes.

---

### Post by koma77 on 2018-10-16
No, this is an Intel NUC motherboard. Thanks for mentioning your find in this thread - appreciate the effort.

---

