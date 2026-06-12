---
title: "Which unused services can I disable on Kubuntu 20 ?"
date: 2022-11-05
forum: General Help
---

### Post by nilovsergey on 2022-11-05
On my Kubuntu 20 I want to disable unused services to increase my OS system performance 
I check current services and if they are active :
```
$ sudo service --status-all
[sudo] password for master: 
 [ + ]  acpid
 [ - ]  alsa-utils
 [ - ]  anacron
 [ - ]  apache-htcacheclean
 [ + ]  apache2
 [ + ]  apparmor
 [ + ]  apport
 [ + ]  avahi-daemon
 [ + ]  bluetooth
 [ - ]  console-setup.sh
 [ + ]  cron
 [ - ]  cryptdisks
 [ - ]  cryptdisks-early
 [ + ]  cups
 [ + ]  cups-browsed
 [ + ]  dbus
 [ + ]  docker
 [ - ]  gdomap
 [ - ]  grub-common
 [ + ]  haveged
 [ + ]  hddtemp
 [ - ]  hwclock.sh
 [ + ]  irqbalance
 [ + ]  kerneloops
 [ - ]  keyboard-setup.sh
 [ + ]  kmod
 [ + ]  lm-sensors
 [ - ]  lvm2
 [ - ]  lvm2-lvmpolld
 [ + ]  mysql
 [ + ]  network-manager
 [ - ]  nfs-common
 [ + ]  nfs-kernel-server
 [ + ]  php8.1-fpm
 [ - ]  plymouth
 [ - ]  plymouth-log
 [ + ]  postgresql
 [ - ]  pppd-dns
 [ + ]  preload
 [ + ]  procps
 [ - ]  pulseaudio-enable-autospawn
 [ + ]  redis-server
 [ + ]  rpcbind
 [ - ]  rsync
 [ + ]  rsyslog
 [ - ]  saned
 [ + ]  sddm
 [ - ]  spice-vdagent
 [ + ]  ssh
 [ + ]  sysstat
 [ + ]  udev
 [ + ]  ufw
 [ + ]  unattended-upgrades
 [ - ]  uuidd
 [ + ]  virtualbox
 [ + ]  whoopsie
 [ - ]  x11-common

```
I suppose that I can disable safely bluetooth, redis-server, postgresql, virtualbox,  docker services.
I have installed them all manually, except bluetooth, which I do not use.
What for the rest of services?
Which of them can be safely disabled? 
Which of them never be  disabled? 
Thanks!

---

### Post by HermanAB on 2022-11-05
Well, Linux is made for experimenting and learning. I could tell you which, but it is way more fun to simply kill the offending processes and see what happens.

---

### Post by nilovsergey on 2022-11-06
That is can be not very fun to disable some service I need for  work...
Have somebody similar expierence ? Please share...

---

### Post by &amp;KyT$0P# on 2022-11-06
I think the reason HermanAB answered that way is that "unused", "can be safely disabled", and "never be disabled" all vary from user to user and even system to system of the same user.  It isn't possible for forum users to know enough about your system and how you use that specific system to say for sure what *you* aren't using on that system and can safely disable on that system.

You could set up a VM of "Kubuntu 20" as closely as possible to the system on which you want to disable stuff, then take a snapshot of the VM and just try disabling services in the now-disposable VM.

---

### Post by ActionParsnip on 2022-11-06
There is no Ubuntu 20. It doesn't exist. Do you mean Ubuntu 20.04 (which is LTS) or do you mean Ubuntu 20.10 which is in prerelease due out in October this year? If you are unsure then you can run
```

lsb_release -a

```
and you will be shown

---

### Post by grahammechanical on 2022-11-06
> I want to disable unused services to increase my OS system performance

All system services are unused until they are used. Some code for each service will reside in memory but it will not use CPU resources until that particular service has to do some work. On Ubuntu we have System Monitor. The Processes tab shows all the processes and which ones are active. There may be a similar utility on Kubuntu. Such as Plasma System Monitor. Ubuntu System Monitor also provides an option to "End Process."

> to increase my OS system performance

What is the problem? A small amount of memory? A less powerful CPU? A less powerful video adapter? A distribution with a less demanding desktop environment may be the answer. Such as Xubuntu or Lubuntu or Ubuntu Mate. 

Regards

---

### Post by nilovsergey on 2022-11-08
As I wrote above I want to increase my OS system performance.
More details about my Laptop and OS :
I have MSI GP70-2PE (GP702PE-426XUA) laptop :
[https://prnt.sc/keAH_wqF18tV](https://prnt.sc/keAH_wqF18tV)
[https://prnt.sc/uCm6oUaZLDbL](https://prnt.sc/uCm6oUaZLDbL)
> 
$  uname -a
Linux master-at-home 5.15.0-41-generic #44~20.04.1-Ubuntu SMP Fri Jun 24 13:27:29 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
$ lsb_release -d; uname -r; uname -i
Description:    Ubuntu 20.04.4 LTS
5.15.0-41-generic
x86_64
$ free
              total        used        free      shared  buff/cache   available
Mem:        8059236     6636260      196608      130344     1226368      998828
Swap:       2104476     1917244      187232
$  kf5-config --version
Qt: 5.12.8
KDE Frameworks: 5.68.0
kf5-config: 1.0

After I disabled some services I mantioned above, like bluetooth, redis-server, postgresql, virtualbox,  docker services
I see really MUCH BETTER system performance. Looks like after I have installed some of these packages I got low
system performance.
Next I wonder about next several services :
> acpid - is a flexible and extensible daemon for delivering ACPI events. When an event occurs, it executes programs to handle the event.
[https://wiki.archlinux.org/title/acpid](https://wiki.archlinux.org/title/acpid)
Not sure if I really need it ?
> apache2 - I just work with php/apache2 - but must it be a service anyway ?
apparmor - is a Linux kernel security module that allows the system administrator to restrict programs' capabilities 
with per-program profiles. Not sure if I really need it, as I am the only person who have access to this laptop
apport - Debugging program crashes without any automated tools has been pretty time consuming and hard for both developers and users. Many program crashes remain unreported or unfixed because:
avahi-daemon - The avahi-daemon Linux service runs on client machines to perform network-based Zeroconf service discovery. Avahi is an implementation of the DNS Service Discovery and Multicast DNS specifications for Zeroconf Networking. User applications receive notice of discovered network services and resources using the Linux D-Bus message passing. The daemon coordinates application efforts in caching replies, helping minimize network traffic.
Do I need have 3 services above enabled ?
Can it be that there is no a lot of sence in checking/disabling any services one by one, but only some of them,
which got a lot of memory and can be disabled?

---

### Post by HermanAB on 2022-11-09
If you would run top, ntop or htop, then you will see which processes are using how much resources and then you can kill them and see if the system works better.  When you reboot, it will all be as before.  To permanently disable a service, you need to do a little
 bit more work.

---

