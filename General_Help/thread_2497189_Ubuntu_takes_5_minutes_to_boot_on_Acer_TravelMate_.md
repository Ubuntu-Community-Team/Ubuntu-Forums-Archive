---
title: "Ubuntu takes 5 minutes to boot on Acer TravelMate laptop"
date: 2024-04-26
forum: General Help
---

### Post by chrismine on 2024-04-26
[COLOR=#26A269]**chrisjan@chrisjan-TravelMate-7730G**[/COLOR]:[COLOR=#12488B]**~**[/COLOR]$ sudo systemd-analyze blame
5.840s NetworkManager-wait-online.service
4.917s NetworkManager.service
3.516s dev-loop9.device
3.506s dev-loop8.device
3.454s dev-loop10.device
2.474s snapd.seeded.service
2.173s snapd.service
1.944s alsa-restore.service
1.532s apport.service
1.381s gnome-remote-desktop.service
1.279s polkit.service
1.255s power-profiles-daemon.service
1.092s accounts-daemon.service
1.090s dev-mapper-ubuntu\x2d\x2dvg\x2dubuntu\x2d\x2dlv.device
1.027s udisks2.service
 979ms avahi-daemon.service
 972ms rsyslog.service
 909ms apparmor.service
 900ms grub-common.service
 867ms bluetooth.service
 715ms snapd.apparmor.service
 697ms ModemManager.service
 663ms gpu-manager.service
[COLOR=#300A24]lines 1-23
Also commented out plymouth service and gpu manager in grub.
Also got these errors on bootup:
Dependency failed for sssd-nss.soc  SSSD NSSService responder socket
[/COLOR]

---

### Post by ajgreeny on 2024-04-26
I think you will find that your hardware with 4G of low speed ram is too low spec for the sensible, speedy use of the default Gnome desktop version of Ubuntu.

Try again with one of the other DE versions, eg Lubuntu, Xubuntu, Kubuntu, etc etc, all of which are less resource hungry.
Even those will not be blisteringly speedy, though if you added more ram and tried an SSD instead of a spinning disk you might manage better.

---

### Post by chrismine on 2024-04-26
Thank you. When booted it works fine.
I do use an SSD drive.
This machine works well with latest Linux Mint. 
There is something delaying boot I cannot find though.

---

### Post by chrismine on 2024-04-30
I have now tried Lubuntu and Kubuntu on the laptop - also takes along time to boot.
Linux Mint Cinnamon boots normal - havew 5.15 kernel and uses Xorg instead of Wayland - thus the reaon for faster boot I assume.

---

### Post by ActionParsnip on 2024-04-30
If you run:
```

[FONT=var(--ff-mono)]dmesg > ~/Desktop/boot-$(date +"%Y-%m-%d").txt
gedit ~/Desktop/boot-$(date +"%Y-%m-%d").txt
[/FONT]
```[FONT=var(--ff-mono)]

Look through the numbers on the left (This is seconds since the kernel came online) and look for large gaps in time.

Also, make sure you have the latest BIOS on the system[/FONT][/COLOR]

---

### Post by chrismine on 2024-04-30
Thank you.
File attaached . All gibberish to me.
It does seems nouveau driver failure...

Cannot upload file as it exeeds forums size limit.

---

### Post by QIII on 2024-04-30
You may use [https://pastebin.ubuntu.com/](https://pastebin.ubuntu.com/) to post your results and leave a URL.

---

### Post by ActionParsnip on 2024-04-30
> **chrismine said:**
> Thank you.
File attaached . All gibberish to me.
It does seems nouveau driver failure...

Cannot upload file as it exeeds forums size limit.

With that attitude you'll never learn anything

"oh its gibberish so I can't do it"

Look down the left hand side... These are numbers which you will understand. I already explained how these are the numbers of seconds since the kernel came online.

Look for big gaps in time... Something will stick out

---

### Post by chrismine on 2024-04-30
Thanks - sorry - gibberish just meant I don't understand it yet....

Thank you for your patience.

Pastebin link:
[https://pastebin.ubuntu.com/p/5Hk52zTdqZ/](https://pastebin.ubuntu.com/p/5Hk52zTdqZ/)

---

### Post by chrismine on 2024-04-30
Problem probably here:
[   87.015165] rfkill: input handler enabled
[   92.001632] rfkill: input handler disabled
[  112.652090] nouveau 0000:01:00.0: systemd-logind[979]: nv50cal_space: -16
[  113.041138] nouveau 0000:01:00.0: systemd-logind[979]: nv50cal_space: -16
[  201.282824] audit: type=1107 audit(1714471861.953:188): pid=952 uid=101 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.7" pid=4175 label="snap.firefox.firefox" peer_pid=979 peer_label="unconfined"

---

### Post by ActionParsnip on 2024-04-30
> **chrismine said:**
> Problem probably here:
[   87.015165] rfkill: input handler enabled
[   92.001632] rfkill: input handler disabled
[  112.652090] nouveau 0000:01:00.0: systemd-logind[979]: nv50cal_space: -16
[  113.041138] nouveau 0000:01:00.0: systemd-logind[979]: nv50cal_space: -16
[  201.282824] audit: type=1107 audit(1714471861.953:188): pid=952 uid=101 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.7" pid=4175 label="snap.firefox.firefox" peer_pid=979 peer_label="unconfined"

OK what is the output of
```

sudo lshw -C display

```

---

### Post by chrismine on 2024-04-30
*-display                 
       description: VGA compatible controller
       product: G98M [GeForce 9300M GS]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: /dev/fb0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=nouveau latency=0 resolution=1440,900
       resources: irq:26 memory:ce000000-ceffffff memory:d0000000-dfffffff memory:cc000000-cdffffff ioport:2000(size=128) memory:c0000-dffff


May take a while to respond - be working.....thank you.

---

### Post by chrismine on 2024-05-03
Tried Nvidia proprietary drivers verion 470 an 550 - both also takes a long time to boot. Did not bother to fix screen resolution.
Removed both and went back to Noveau driver as it does not make any difference.

Seems the delay lies elsewhere...

---

### Post by oldfred on 2024-05-03
Have you tried a lighter weight flavor?
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

I have Kubuntu which is more of a mid-weight flavor on an external SSD with my core2-duo system from 2006 that only has 1.5GB of RAM. Ubuntu would not even install. Server version installed and I could add lightweight gui. Kbuntu installed, but old HDD was slow. External SSD much better, functional but not speedy.

---

### Post by chrismine on 2024-05-06
I have tried Lubuntu and Kubuntu for a short while. To see if it solves the slow boot problem - it does not.

Ubuntu works well and responsive enough on this laptop with the SSD. 
It's just the slow boot that I try to figure out. The lightweight distro's also boot slowly.

Linux Mint boots normally - have an older kernel and compositor - will probably also happen later when using the newer kernel I assume....

I play with this stuff to try to learn Linux and commands.

Thank you for responding.

---

### Post by oldfred on 2024-05-06
With my Kubuntu install I do a bit of tuning for faster boot. It is Kubuntu but configuration files are mostly the same.
It then boots in about 1/3 of the time.

After most of the tuning
```
fred@z170-noble:~$ systemd-analyze
Startup finished in 4.662s (kernel) + 7.134s (userspace) = 11.796s 
graphical.target reached after 7.102s in userspace.

```
Noble first boot on NVMe drive
```
fred@z170-noble:~$ systemd-analyze
Startup finished in 4.528s (kernel) + 27.254s (userspace) = 31.783s 
graphical.target reached after 27.216s in userspace.

```

turned off NetworkManager-wait with systemctl, 
systemctl disable NetworkManager-wait-online.service
grub - changed from quiet splash to noplymouth, will see boot process rather than Ubuntu logo, 

removed snaps - in noble either I did it in wrong order or they have made it very difficult to fully remove all snaps & files related to snaps.

If UEFI firmware update not supported, newer laptops often are, check at fwupd site if yours is on list.
sudo apt-get purge fwupd

If no Thunderbolt
systemctl status bolt
boltctl list
systemctl mask bolt.service 

Many other suggestions:
[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2496312&p=14183456#post14183456](https://ubuntuforums.org/showthread.php?t=2496312&p=14183456#post14183456)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)

---

### Post by chrismine on 2024-05-12
I accidentally discovered this:
By changing grub to noplymouth as suggested by oldfred I noticed that booting got stuck by discovering/configuring sata devices: Browsed around in BIOS settings and change AHCI to IDE and tis aptop now boot to  a desktop in  49 seconds instead of 5 minutes.

Strange though as it should not be.....methinks....

System analyze shows the correct time lapse though.

One can only see the delay in booting when checking the delay with "noplymouth" enabled n grub.
Will have to make and post a 5 minute long video if anyone interested....

---

### Post by chrismine on 2024-05-12
# System Details Report
---

## Report details
- **Date generated:**                              2024-05-12 23:15:20

## Hardware Information:
- **Hardware Model:**                              Acer TravelMate 7730G
- **Memory:**                                      4.0 GiB
- **Processor:**                                   Intel® Core&#8482;2 Duo P8400  × 2
- **Graphics:**                                    NV98
- **Disk Capacity:**                               448.1 GB

## Software Information:
- **Firmware Version:**                            v2.3821
- **OS Name:**                                     Ubuntu Oracular Oriole (development branch)
- **OS Build:**                                    (null)
- **OS Type:**                                     64-bit
- **GNOME Version:**                               46
- **Windowing System:**                            Wayland
- **Kernel Version:**                              Linux 6.8.0-31-generic

---

