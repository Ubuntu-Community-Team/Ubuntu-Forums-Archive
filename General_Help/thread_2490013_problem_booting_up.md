---
title: "problem booting up"
date: 2023-08-18
forum: General Help
---

### Post by jgw on 2023-08-18
I have been having a problem with booting up.  It now takes between 3 minutes and 8 minutes.  I have done part of the boot repair thing but have not done the other stuff. 

I did, however, get a file which is at [https://pastebin.ubuntu.com/p/VyPs3PTTfC/](https://pastebin.ubuntu.com/p/VyPs3PTTfC/)

I didn't want to go any further without some advice as I have never messed with this before.  

I just timed my boot again and it was right around 1 minute so whatever I did seems to have taken care of the booting problem although there is still a black screen for about half of that time so maybe I need to do something else (although I can live with this)

After I get this done I am also going to have to figure out why my system is freezing every time I boot it up.  The screen comes on and, about 5 seconds later it freezes.  This occurs when all hard drives are not running, firefox not running and no startup programs.    I can also move my mouse before freezing occures although its kinda iffy.  Would also appreciate any help on this too.  

Thank you..............

---

### Post by yancek on 2023-08-19
Your sdb1 partition is a BIOS boot partition which is used when you have a Legacy/MBR install on a GPT drive.  Your boot repair output shows sdb2 is an EFI partition with the correct files to boot.  There is no reason to have both partitons.  Disable Legacy/CSM boot in your BIOS and test.  If it boots faster, delete sdb1 partition as it is not used or needed with an EFI install on a GPT drive.

---

### Post by jgw on 2023-08-20
Thank you for the reply!

For the last couple of days I have started from scratch with the offending machine.  My booting is sometimes up to 10 minutes and sometimes about 2 minutes.  Have no idea why.  I do know that its not my hard drives because I have disconnected them and its still llong sometimes.  Here is some stuff to do with the ssd I use for booting (1tb)

I have four things under boot.  There is the ssd that I use for booting and two hard drives.  There is also some kind of usb thing which, I suspect, means that I can use a usb to boot up (usb general boot disk).  I think what you are referring to is the second partition after the one that is actually used for booting (I think). 

the first partition is 1.0mb
cont6ents are unknown
partition type is BIOS Boot

The second partition is 538 mb - 530 mb free (1.4%full)
FAT (32-bit version- - Mounted at /boot/efi
Called "EFI System"

I think you are suggesting I disable one of the above.  I am willing to give that a shot.    Right now I not only have problems with the booting but in general.  My system will no longer show he photos, for no reason I can think of, for instance.  Still reading and trying stuff, none of which are working <sigh>  My mouse pointer has been going nuts but, on this boot that stopped.  (it was flickering and jumping around like crazy).  

Wonders never end!

Thoughts?

---

### Post by jgw on 2023-08-20
Thank you for the reply!

For the last couple of days I have started from scratch with the offending machine.  My booting is sometimes up to 10 minutes and sometimes about 2 minutes.  Have no idea why.  I do know that its not my hard drives because I have disconnected them and its still llong sometimes.  Here is some stuff to do with the ssd I use for booting (1tb)

I have four things under boot.  There is the ssd that I use for booting and two hard drives.  There is also some kind of usb thing which, I suspect, means that I can use a usb to boot up (usb general boot disk).  I think what you are referring to is the second partition after the one that is actually used for booting (I think). 

the first partition is 1.0mb
cont6ents are unknown
partition type is BIOS Boot

The second partition is 538 mb - 530 mb free (1.4%full)
FAT (32-bit version- - Mounted at /boot/efi
Called "EFI System"

I think you are suggesting I disable one of the above.  I am willing to give that a shot.    Right now I not only have problems with the booting but in general.  My system will no longer show he photos, for no reason I can think of, for instance.  Still reading and trying stuff, none of which are working <sigh>  My mouse pointer has been going nuts but, on this boot that stopped.  (it was flickering and jumping around like crazy).  

Wonders never end!

Thoughts?

---

### Post by yancek on 2023-08-21
The boot time will depend upon your hardware to a certain extent.  I have 2 laptops, one with a SATA drive and one with an SSD drive.  The one with the SSD drive boots 4 times faster.  How old/new is this computer?  Post some hardware information if you don't resolve.

You should see an option in your BIOS for Boot.  You will need to explore the various options to see if there is a Legacy/CSM option which you can enable/disable.  You might try looking online for the manual of your specific computer as these options vary with manufacturer.   Some newer computers no longer have an option to boot in Legacy/CSM mode and in that case having that BIOS_boot partition would be meaningless if that is the case with your machine

Your first partition (1 MB.size) is the BIOS_boot partition which is used for Legacy/CSM boot on a GPT drive, the 2nd partition is your EFI boot fiiles.   

> there is still a black screen for about half of that time  

Freezing is a problem but seeing a black screen with the manufacturer and Ubuntu logos is not a problem.  I see that on mine on every boot.

---

### Post by jgw on 2023-08-21
Thank you for the help!

This morning my initial boot was longer than 15 minutes.  I pressed the restart button and it booted up in about one minute.  I continue to wonder why.  I wouldn't bother me if it wasn't changing its way all the time. Here is a report on my system: [https://pastebin.com/UuLSWzQP](https://pastebin.com/UuLSWzQP)

I changed how long it took from 145 to 15 minutes - apologies

---

### Post by yancek on 2023-08-21
Have you gone into the BIOS firmware and disabled Legacy/CSM?  That is the first thing I would do.

>  /dev/sdb3    /    7.09 % (870.9 GiB of 937.3 GiB)

That looks like your / filesystem is almost full with 870Gb on the drive.  Does that look right to you.  If so, go into /var/logs and start deleting some of the older log files.  The system reserves 5% for itself so you are close to that and it soon will stop booting.

I see you have an NVidia graphics card.  I don't use NVidia but my understanding is that if you have done a kernel upgrade, you need to reinstall the driver.

---

### Post by jgw on 2023-08-21
I started using nvidia about 3 days ago so I suspect its ok.  I am not sure what drive you were talking about but if its the ssd it still has 1.0 TB &#8212; 985 GB free (3.8% full) in the main and the others are ok too.  I wonder if that report is wrong.  Wife wants to eat dinner.  Will be back tomorrow.

---

### Post by yancek on 2023-08-22
You still haven't indicated whether you have disabled Legacy/CSM boot in the BIOS which I would suggest as the next step.

---

### Post by MAFoElffen on 2023-08-22
Try these from an Installer LiveUSB, and post the output of within [noparse]```
 
```[/noparse] tags. This is very important that you start posting output and commands with those code tags, and not un-formatted within your posts. That is a Forums policy...
```

[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"  ## Will indicate which boot mode the machine is booted as.
lsblk -e7 -o name,label,size,fstype,model  ## Will tell us the storage devices in the machine
sudo systemd-analyze blame  ## Will break down the boot processes and tell us how long those boot processes are taking.

```
That is the minimum information that we need to recommend a solution for this.

---

### Post by jgw on 2023-08-22
I am ready to disable.  I want to make sure which one:
the first partition is 1.0mb
cont6ents are unknown
partition type is BIOS Boot

The second partition is 538 mb - 530 mb free (1.4%full)
FAT (32-bit version- - Mounted at /boot/efi
Called "EFI System"

I have also sent a picture of the one you think is full.  Its really not (you will see)  That is the largest part of the ssd and ubuntu.  I could also send you pictures of the two from which I should disable one.  I get nervous that I am going to screw up although I should be able to disable one and if its wrong fix it.  I am not sure why there are the two if only one is being used.  Must mean something?

In between times I am putting in stuff that I got rid of when I installed the new ubuntu.  Yesterday I put in KODI to play shows.  I am wondering if I should also put in sonarr or choose another program.

Thank you again for your help..

---

### Post by oldfred on 2023-08-22
Do not post screen shots, post output of commands as suggested in post #10.
And use code tags, easy to add with forum's advanced editor and # icon.

BIOS boot systems using gpt partitioning need the bios-grub partition.
UEFI boot systems need the ESP - efi system partition (FAT32)

You do not need both, but deleting the 1MB bios_grub will not add any space anywhere else.
I used to add both when I first converted to UEFI, so I could easily convert to BIOS. But now only have ESP.

---

### Post by jgw on 2023-08-22
Thank you......

My problem is, obviously, ignorance.  You are waaay ahead of me.  I have been at this for a very long time (60 years easy) but never messed with this kind of stuff. I suspect in addition to ignorance lazy comes to mind.  

I wasn't aware of posting any commands or code without the [code][code] thing.  I know that I have done it in the past if I am dealing with single lines and will mend my ways.  I didn't know it was a rule (but do now!)

I ran the last two lines and have the results should you want them.  The first line, with the brackets failed every way I tried.  Seems that the -d did that (said it was an error)

I have no real idea of what installer liveUSB is.  It looks like it might behave approximately like Startup disk creator which grabs the ubuntu.iso and then turns an ssd or a usb into a new ubuntu machine.  

I ran the last two and can send you the results if you wish.  
I went to https://www.pendrivelinux.com/liveusb-install-live-usb-creator/ and think I can download this thing if you wish.

Thoughts?

---

### Post by jgw on 2023-08-22
I am not sure what to say.  I replied to your response but thought, in part, I was writing to somebody else.  I sent a picture of something to show, exactly, how much room was left.  I am not sure of what commands I could have sent which would have the information I was trying to send.  

I have no idea what to do about the below as I have never messed with this to any degree and I am ignorant about what you are saying.  This is not your fault but mine.  I have no idea, for instanced what gpt partitioning means nor do I understand bios-grub partitioning (other than it exists)  Our discussion was about the fact that my booting was taking waaay too long, and still is, I have done nothing so far. You have, obviously read the whole thing.  I think what you are saying is that making one of the partitions not functional does nothing?

BIOS boot systems using gpt partitioning need the bios-grub partition.
UEFI boot systems need the ESP - efi system partition (FAT32)

---

### Post by oldfred on 2023-08-22
If you go to the link in my signature, and scroll to Acronyms, you can get simple explanations of many terms and links to additional info if interested.
Skip a lot of the info as most is for specific issues, which do not apply to you.

In DOS days (1980's) they used MBR(msdos) partitioning.
With UEFI, gpt is required for Windows & recommended for Linux.

If one or two lines, code tags not really required, but help clarify that it is code. I often use the quote icon on Quick Reply, and manually change quote to code. A good typist/keyboarder can probably type the code tags quicker.

Slow booting may be related to UEFI/BIOS set in one mode, but install in other mode. 
UEFI defaults to UEFI boot per order in UEFI boot menu, if not found, then it tries other boot options.
Deleting either bios_grub or ESP, may break system, if wrong one deleted. Its ok to have both and that would not be a slow boot issue.
If booted in UEFI mode this shows boot options.
```
sudo efibootmgr -v
```

Also settings in fstab can cause slow boot, if system is trying to find a partition that now does not exist. It has to time out.

---

### Post by jgw on 2023-08-22
Thank you for the reply I ran what you said.  I have no idea of what it means.  I have just taken booting for granted and never messed with it.  One can only wonder.  I have found that if my computer, when it was taking a long time if would press the restart button and it finished quickly.  Always thought that was a little strange.
  
greg@videos:~$ sudo efibootmgr -v
[sudo] password for greg: 
EFI variables are not supported on this system.

---

### Post by oldfred on 2023-08-22
You currently then are booting in BIOS/CSM/Legacy boot mode. If you delete the bios_grub partition, you will not be able to boot until  you reinstall grub, probably in UEFI boot mode.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

Still need results from commands in post #10

---

### Post by jgw on 2023-08-26
Here is what you requested: [https://pastebin.com/ijMafK1p](https://pastebin.com/ijMafK1p)  

I decided to re-install my ubuntu as well just to make sure of stuff.  My problems have multiplied.  I have 3 hard drives plus an ssd for my boot and most of my programs.  I thought I would do that to see if anything changed.  It just got worst.  Now only one of my drives will boot.  If I try and boot with them all what I am gifted with is a blank screen with a little blinking white line in the upper left hand side and the rest is empty black.  I have tried swapping out connections, etc. but nothing changed.  I have tested my drives with another system as external drives and all the drives are working just fine.  My current ubuntu is 22.04.04

Now I have tried to run the other drives with the connector what is on the one drive.  I found out that the connector can run any of the three drives so I tried 4 other connectors, none of the others worked.  Now I am going to try the connector using a different motherboard connector and see what happens.

---

### Post by oldfred on 2023-08-26
You posted that your install was in Legacy or BIOS/CSM boot mode.

But if system is less than 10 years old it is UEFI as Microsoft required vendors to install in UEFI mode with gpt partitioning starting with release of Windows 8 in 2012. How you boot install media, UEFI or BIOS is then how it installs. UEFI only wants to install grub boot loader to first drive with Ubiquity installer which has been used with 22.04 and older versions of Ubuntu. First drive is defined by UEFI/BIOS and may not be sda as it is before partitions are mounted in the install. If all sdX, lowest port is often hd0, so you want to make sure SSD is in lowest port. But if you also have NVMe drives that may be first and may disable a port.

If multiple drives, do you only have Ubuntu on one of them? The SSD?
Are drives internal or external?

---

### Post by jgw on 2023-08-26
Thank you............

I was testing to see just what was going on and then nothing worked!  It would not recognize anything, including itself.  I think the motherboard has died.  I have a couple of others so I can put another one in.  I have given up on that machine and apologize for taking your time on a piece of crap.  Oh, can't help but ask - how old is Old Fred? (needn't reply as its none of my business but I couldn't resist).  So, I turned on the second one that I was working with and had problems with.  First I plugged in the ssd and it worked.  Then I plugged in each hard drive, one by one, and they too all worked!  That being the case I am a bit delighted. 

I really hope this the one that's working will continue for a while.  

Thanks again for all your help............Now I'm gonna have to check on the chip in the failed machine to see if its any good or not.  Either way I suspect I should trash to motherboard on principle.  I only have one problem with that one and that's that I gotta start reading how to test the chip.  I might just give up.

---

### Post by oldfred on 2023-08-26
Oldfred is first year baby boomer. :)
Some posting here make me not so old.

---

### Post by jgw on 2023-08-28
I gotcha by a few years - memory is failing, etc.

---

### Post by MAFoElffen on 2023-08-28
I see from this output:
```

greg@greg-System-Product-Name:~$ [ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy" 
[COLOR=#ff0000]Legacy[/COLOR]
greg@greg-System-Product-Name:~$ lsblk -e7 -o name,label,size,fstype,model 
NAME   LABEL     SIZE FSTYPE MODEL
sda            953.9G        [COLOR=#ff0000]SanDisk SDSSDH31024G[/COLOR]  ## This is a fairly fast SATA SSD...
&#9500;&#9472;sda1             1M        ## Reported as type bios_boot
&#9500;&#9472;sda2           513M vfat   
&#9492;&#9472;sda3         953.4G ext4   
sdb             58.6G        UDisk
&#9492;&#9472;sdb1 Blue     58.6G ext4   
sdd              3.6T        WD4000FYYX ## HDD 7200, wiith sustained rate of 171 MB/s
&#9492;&#9472;sdd1 newback   3.6T ext4   
greg@greg-System-Product-Name:~$ sudo systemd-analyze blame 
[sudo] password for greg: 
21.165s plymouth-quit-wait.service
 3.822s NetworkManager-wait-online.service
 2.229s snapd.service
  900ms dev-sda3.device
  734ms dev-loop2.device
  734ms dev-loop1.device
  732ms dev-loop6.device
  731ms dev-loop4.device
  730ms dev-loop3.device
  730ms dev-loop7.device
  728ms dev-loop5.device
  631ms networkd-dispatcher.service
  540ms fwupd.service
  456ms snapd.apparmor.service
  447ms cups.service
  439ms dev-loop0.device
  343ms accounts-daemon.service
  329ms avahi-daemon.service
  322ms bluetooth.service
  316ms grub-common.service
  309ms snapd.seeded.service
  305ms NetworkManager.service
  291ms ModemManager.service
lines 1-23
## Your's probably conitnued on a bit more. See my results below.

```
Your network wait at boot could be sped up by adding "optional: yes" to your netplan yaml file, so it doesn't have to wait for the network devices to be initialized during the boot process. You can disable and mask your modem manager service, as i doubt you are using WWAN for connection.

Here is my laptop to compare:
```

mafoelffen@Mikes-ThinkPad-T520:~$ sudo systemd-analyze blame
16h 25min 19.558s dev-loop3.device
16h 25min 19.552s dev-loop7.device
16h 25min 19.551s dev-loop6.device
16h 25min 19.547s dev-loop2.device
16h 25min 19.539s dev-loop5.device
16h 25min 19.524s dev-loop0.device
16h 25min 19.517s dev-loop1.device
           7.885s dev-loop27.device
           7.065s snapd.service
           6.984s NetworkManager-wait-online.service
           6.418s snap.lxd.activate.service
           2.488s systemd-udev-settle.service
           1.273s uml-utilities.service
           1.239s fwupd-refresh.service
           1.232s ua-timer.service
           1.087s xrdp.service
            719ms systemd-logind.service
            718ms accounts-daemon.service
            710ms bluetooth.service
            701ms zfs-import-cache.service
            699ms cups.service
            631ms udisks2.service
            623ms e2scrub_reap.service
            592ms lightdm.service
            583ms networkd-dispatcher.service
            579ms plymouth-quit-wait.service
            526ms systemd-cryptsetup@swap.service
            515ms switcheroo-control.service
            513ms ModemManager.service
            459ms power-profiles-daemon.service
            434ms smartmontools.service
            368ms libvirtd.service
            285ms apport-autoreport.service
            277ms user@1000.service
            276ms systemd-resolved.service
            265ms zfs-share.service
            233ms snap.canonical-livepatch.canonical-livepatchd.service
            220ms snapd.seeded.service
            214ms fstrim.service
            210ms NetworkManager.service
            205ms systemd-timesyncd.service
            195ms apparmor.service
            191ms snapd.apparmor.service
            178ms apport.service
            173ms upower.service
            167ms polkit.service
            163ms lxc-net.service
            156ms avahi-daemon.service
            152ms lm-sensors.service
            147ms lvm2-monitor.service
            145ms systemd-rfkill.service
            143ms systemd-udev-trigger.service
            133ms ssh.service
            129ms gpu-manager.service
            126ms nmbd.service
            125ms systemd-journald.service
            123ms smbd.service
            119ms thermald.service
            113ms systemd-udevd.service
            113ms update-notifier-download.service
            109ms snap-bare-5.mount
            107ms snap-canonical\x2dlivepatch-229.mount
            105ms snap-canonical\x2dlivepatch-235.mount
            104ms systemd-journal-flush.service
            103ms keyboard-setup.service
            103ms snap-core-15511.mount
            101ms colord.service
             99ms snap-core18-2785.mount
             97ms snap-core18-2790.mount
             96ms snap-core20-1974.mount
             94ms snap-core20-2015.mount
             92ms snap-core22-817.mount
             91ms systemd-fsck@dev-disk-by\x2duuid-281F\x2dB438.service
             91ms snap-core22-858.mount
             90ms xrdp-sesman.service
             89ms ecbd.service
             89ms snap-eclipse-67.mount
             87ms snap-eclipse-69.mount
             85ms rsyslog.service
             84ms snap-firefox-2971.mount
             82ms wpa_supplicant.service
             81ms snap-firefox-3026.mount
             80ms modprobe@chromeos_pstore.service
             79ms dpkg-db-backup.service
             79ms snap-gnome\x2d3\x2d38\x2d2004-143.mount
             78ms systemd-modules-load.service
             77ms snap-gnome\x2d42\x2d2204-120.mount
             75ms zfs-mount.service
             74ms zfs-volume-wait.service
             74ms snap-gnome\x2d42\x2d2204-126.mount
             74ms systemd-machined.service
             71ms snap-gtk\x2dcommon\x2dthemes-1534.mount
             70ms dev-hugepages.mount
             70ms run-rpc_pipefs.mount
             69ms dev-mqueue.mount
             68ms snap-gtk\x2dcommon\x2dthemes-1535.mount
             68ms sys-kernel-debug.mount
             67ms sys-kernel-tracing.mount
             65ms snap-lxd-25112.mount
             62ms snap-lxd-25345.mount
             61ms kmod-static-nodes.service
             60ms snap-snap\x2dstore-638.mount
             57ms snap-snap\x2dstore-959.mount
             56ms modprobe@configfs.service
             54ms snap-snapd-19457.mount
             53ms atd.service
             53ms openvpn.service
             52ms packagekit.service
             52ms modprobe@fuse.service
             50ms kerneloops.service
             48ms snap-snapd\x2ddesktop\x2dintegration-83.mount
             45ms cockpit-motd.service
             43ms binfmt-support.service
             43ms systemd-tmpfiles-setup.service
             37ms systemd-user-sessions.service
             37ms lxc.service
             34ms var-snap-firefox-common-host\x2dhunspell.mount
             33ms systemd-backlight@backlight:acpi_video0.service
             32ms systemd-sysusers.service
             31ms systemd-binfmt.service
             29ms cockpit.socket
             27ms root.mount
             27ms plymouth-start.service
             26ms etc-libvirt.mount
             24ms home.mount
             24ms var-lib-libvirt-images.mount
             23ms grub-common.service
             22ms systemd-random-seed.service
             22ms kpool.mount
             22ms rpcbind.service
             21ms systemd-backlight@backlight:acpi_video1.service
             21ms dev-loop13.device
             21ms qemu-kvm.service
             20ms systemd-tmpfiles-clean.service
             20ms boot.mount
             20ms dpool.mount
             20ms snap-core-15925.mount
             20ms systemd-tmpfiles-setup-dev.service
             20ms dev-loop9.device
             20ms dev-loop10.device
             20ms dev-loop11.device
             20ms dev-loop12.device
             20ms dev-loop8.device
             20ms dev-loop15.device
             19ms systemd-sysctl.service
             19ms hddtemp.service
             19ms libvirt-guests.service
             19ms alsa-restore.service
             19ms dev-loop14.device
             18ms dev-loop18.device
             18ms dev-loop19.device
             18ms snap-snapd-19993.mount
             17ms dev-loop16.device
             16ms dev-loop17.device
             16ms user-runtime-dir@1000.service
             16ms dev-loop20.device
             15ms dev-loop21.device
             15ms proc-sys-fs-binfmt_misc.mount
             15ms dev-loop23.device
             15ms dev-loop22.device
             14ms dev-loop24.device
             14ms home-mafoelffen-Downloads-ISO.mount
             14ms console-setup.service
             14ms plymouth-read-write.service
             14ms systemd-update-utmp.service
             14ms finalrd.service
             13ms rpc-statd-notify.service
             12ms boot-efi.mount
             12ms systemd-remount-fs.service
             11ms dev-mapper-swap.swap
             11ms trousers.service
             11ms dev-loop25.device
             11ms sys-fs-fuse-connections.mount
             10ms motd-news.service
              9ms grub-initrd-fallback.service
              9ms sys-kernel-config.mount
              7ms modprobe@efi_pstore.service
              6ms modprobe@pstore_blk.service
              6ms setvtrgb.service
              6ms libvirtd.socket
              6ms systemd-update-utmp-runlevel.service
              5ms modprobe@drm.service
              5ms modprobe@pstore_zone.service
              4ms rtkit-daemon.service
              4ms boot-grub.mount
              4ms ufw.service
              3ms modprobe@ramoops.service
              3ms zfs-load-module.service
              2ms run-qemu.mount
              2ms snapd.socket
            100us blk-availability.service
lines 139-191/191 (END)
mafoelffen@Mikes-ThinkPad-T520:~$ sudo systemd-analyze
Startup finished in 8.062s (kernel) + 12.469s (userspace) = 20.532s 
graphical.target reached after 12.418s in userspace

```
This laptop above is 13 years old and is UEFI boot.

My recommends align with oldfred's, in that you should set your BIOS to boot into UEFI only and reinstall Grub2.

---

### Post by jgw on 2023-08-29
Thanks for the reply!

I just started anew (gave up)  I now boot, all drives, are working and the boot takes about 2 minutes.

---

