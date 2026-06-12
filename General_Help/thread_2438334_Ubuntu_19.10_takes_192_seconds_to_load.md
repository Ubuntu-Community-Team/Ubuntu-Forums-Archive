---
title: "Ubuntu 19.10 takes 192 seconds to load"
date: 2020-03-10
forum: General Help
---

### Post by ogola89 on 2020-03-10
I would like to request help with a slowly booting Ubuntu. I have a  HP pavillion laptop with a 250gb ssd with Windows 10 installed, and run  Ubuntu from an external harddrive. I have recently fixed some problems I  had with dual boot in UEFI mode, but now my next problem (which already  existed while I was trying to solve dual-boot problems and is not the  result of whatever I fixed) is that Ubuntu takes about 192 seconds to  load. 


  External harddrive is a seagate backup plus 4tb read/write speed of about 110/120mbps connected with a USB 3.0.


  I am not sure how to fix it, but I have the outputs from systemd-analyze critical-chain and blame, as well as dmesg.


  From dmesg it seems there is some time taken to mount 'sdb8' at  around 43 seconds and possibly the bluetooth delays from 60-140 seconds.  According to the systemd-analyze plot there seems to be a long delay  between sysinit.target and the nss-lookup.target.
  However, I am no expert with this and I am not sure how to interpret  these outputs, and so would request some help in what to do about it.


  Thanks! 

dmesg output:

  [https://gist.github.com/ogola89/d0b768c7f87079c998b7adbdeec86226#file-dmesg_output-txt](https://gist.github.com/ogola89/d0b768c7f87079c998b7adbdeec86226#file-dmesg_output-txt)

systemd critical chain output:
[https://gist.github.com/ogola89/d0b768c7f87079c998b7adbdeec86226#file-systemd_critical_chain-txt](https://gist.github.com/ogola89/d0b768c7f87079c998b7adbdeec86226#file-systemd_critical_chain-txt)

systemd blame output:
[https://gist.github.com/ogola89/d0b768c7f87079c998b7adbdeec86226#file-systemd_blame-txt](https://gist.github.com/ogola89/d0b768c7f87079c998b7adbdeec86226#file-systemd_blame-txt)

systemd plot output:
[https://ibb.co/jHWrcMs](https://ibb.co/jHWrcMs)

---

### Post by TheFu on 2020-03-10
USB3 (or any USB) will be slow. Nothing can fix that.  It is a protocol problem w/ USB storage.  Switch that connection the SATA or eSATA, if you can.
To save other people from following links:

```

         30.065s plymouth-quit-wait.service
         17.912s systemd-journal-flush.service
         12.927s snapd.service
         12.301s networkd-dispatcher.service
         11.463s [email]postgresql@12-main.servic[/email]e
         11.322s dev-sdb8.device
         10.049s udisks2.service
          9.536s NetworkManager-wait-online.service
          8.739s ModemManager.service
          7.873s accounts-daemon.service
          7.333s fwupd.service
          6.821s NetworkManager.service
          6.513s grub-common.service
          6.474s secureboot-db.service
          6.146s e2scrub_reap.service
          5.854s grub-initrd-fallback.service
          5.724s avahi-daemon.service
          5.665s rsyslog.service
          5.600s thermald.service
          5.594s iio-sensor-proxy.service
          5.578s bluetooth.service
```
You don't need plymouth.
You don't need avahi on a well run network.  
You don't need a "modem manager" do you?
You don't need bluetooth. Purge those tools and disable the HW in the BIOS.
Do you really need snaps?  I've purged them from my system. 
```
$ snap
The program 'snap' is currently not installed. You can install it by typing:
sudo apt install snapd
```
Only you can decide whether snaps are useful or not.

If you set the network to use a static IP, on the system, most of the network slowness will be gone. In short, don't use wifi or DHCP.
I'm guessing that sdb8 is the USB connected disk?  It is slow.

Basically, Ubuntu installs and configures a bunch of stuff to "just work" that most people actually don't need or want.  They are following the MSFT model of "maybe someday, someone, using this install, might want X" so they install, configure and run stuff that isn't necessary.

Consider moving "server" things outside the graphical startup dependency chain. Why does apache or postgress have anything to do with a desktop login?  Makes no sense.  Also, trying to run a postgress DB on USB storage is a bad idea.

---

### Post by GhX6GZMB on 2020-03-10
3 minutes to boot from an external USB HDD sounds about right. You'll need to rethink your HW setup.

---

### Post by dragonfly41 on 2020-03-10
I have an external SSD containing Ubuntu 18.04, via USB 3.0 (since I am using docking station for SSD).
Boot time is snappy but I am using rEFInd where I have configured refind.conf to scan external drive first to look for loader.

---

### Post by TheFu on 2020-03-10
fyi, here's the systemd-analyze blame for a **19.10 server** here:```

          2.103s e2scrub_reap.service
          1.505s systemd-udev-settle.service
          1.154s systemd-networkd-wait-online.service
[I]           954ms cloud-config.service
           930ms cloud-init-local.service[/I]
           874ms systemd-journald.service
           860ms systemd-logind.service
           717ms dev-vda2.device
           647ms systemd-timesyncd.service
           [I]583ms cloud-init.service
           428ms cloud-final.service[/I]
           374ms systemd-resolved.service
           358ms blk-availability.service
           344ms networkd-dispatcher.service
           342ms systemd-networkd.service
           312ms keyboard-setup.service
           295ms systemd-journal-flush.service
           270ms apparmor.service
           266ms apport.service
           232ms accounts-daemon.service
           199ms rsyslog.service
           199ms swap.img.swap
           194ms grub-common.service

```

See that cloud-init stuff?  Just removed it here. Saving about  1.8sec from startup now.  Before I dd that, I knew that console access might be needed to fix any issue this caused.  Fortunately, it didn't break anything.  win-win.

Also cleaned up the iscid service.  We don't use any iSCI storage, so that isn't needed.  Doing that removed about 6 lines from the critical-chain dependency list and another second saved.

That's with a SATA SSD, no USB, no GUI, no DHCP. No snaps.  Network is static IP.  Provided just so you can see what's possible on a relatively clean install.

---

### Post by ogola89 on 2020-03-11
Thanks for the replies guys, I appreciate it.

Just a couple of things to note:
I previously had ubuntu installed on a sandisk USB as well, which booted up much quicker - about 20 seconds. I am not asking for an instant boot, but it has increased considerably.

I then got the external HD, installed Ubuntu on it, and it loaded relatively quickly as well. I think the problems came when I then used dd to get the files from the sandisk USB install to the hard drive. My guess is some files may have been duplicated or point to files whose directories have changed (e.g disk locations) and that's what's causing this issue.

As to the fixes mentioned, I am not sure exactly which ones are server ones and which ones are essential. I know it is tedious, but if you have a moment, could you please literally point out which exact ones I should remove to speed things up a bit? I am not so familiar with the nature of each process.

Thanks!

---

### Post by dragonfly41 on 2020-03-11
I am a fan of Stacer which you can install from PPA [from instructions here]("https://github.com/oguzhaninan/Stacer").

Then go to Stacer dashboard > Services and you can very easily choose which should be enabled/disabled.

But this is only one approach.

---

### Post by TheFu on 2020-03-11
> **ogola89 said:**
>  I then got the external HD, installed Ubuntu on it, and it loaded relatively quickly as well. I think the problems came when I then used dd to get the files from the sandisk USB install to the hard drive. My guess is some files may have been duplicated or point to files whose directories have changed (e.g disk locations) and that's what's causing this issue.

As to the fixes mentioned, I am not sure exactly which ones are server ones and which ones are essential. I know it is tedious, but if you have a moment, could you please literally point out which exact ones I should remove to speed things up a bit? I am not so familiar with the nature of each process.

Everyone is different.  What you think is essential,  I think is pure bloat.   It is a judgement call that only you can make.

dd is dumb.  it doesn't know anything about sector alignments. A misaligned spinning disk can create a 30% performance loss.  Check that using **parted**.  Data needs to be placed on the disk at the beginning of sectors, which need to be aligned on natural sector boundaries.  Sectors are either 512b or 4Kb in size.  SMART, hdparm and a few other tools will list the native sector size for a disk.  Google for more background if needed.

---

