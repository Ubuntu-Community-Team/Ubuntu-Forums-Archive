---
title: "Very slow bootup"
date: 2016-09-28
forum: General Help
---

### Post by ardvark on 2016-09-28
Actually the slow boot up really began with 14.04, but a new thing happened when I upgraded to 16.04. It's taking a little over 2 minutes to get to a Login. The POST beep is coming at about 26 seconds partly because my BIOS is doing a funny second start that I've never resolved. Then at about 45 seconds I get this at the top of the screen:

/dev/sda1: clean, 1464115/19013632 files, 21621410/76047616 blocks
This I didn't get with 14.04.

This lasts for almost a minute; at the 1:46 time I get the NVIDIA splash. At 2:25 I finally get the Login screen, then an active desktop at about 3:20.

---

### Post by ajgreeny on 2016-09-28
You can ignore the message ```
/dev/sda1: clean, 1464115/19013632 files, 21621410/76047616 blocks
``` which appears and quickly disappears on all my 16.04 installations both in VirtualBox and hard metal versions.  I don't think it means a full filesystem check has occurred each boot, but is simply a message that the filesystem is clean.

Now to the problem that you should be able to solve in some way; the slow boot-up.

I agree that the time your system takes to boot is far too long, even if you had low resources, but it will be helpful to know your hardware as that will obviously have some effect.

It will also be useful for you to see a text boot by removing the "quiet splash" from the boot stanza by editing that line for a single boot from the grub menu.
Hit "e" at the highlighted menu for your chosen kernel and use the cursor keys to go to those two words and delete them.
For this one boot you will see the text of what is happening which is normally hidden and you may see a moment of lag in the boot sequence which will give you some clues about the cause of your problem.

---

### Post by Hadaka on 2016-09-28
Hi please open a terminal ctrl/alt/t then copy and paste.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```
This will create a file in your "**home**" directory named **wireless-info.txt** please note it is the .txt file, then copy and post that file to aid in diagnostics
of your issue.
thanks.

*note..yes it is mainly for wireless issues,but has alot of other information that will be very usefull.

---

### Post by ardvark on 2016-09-29
Thanks for the quick response, I'm not sure what you mean by "Hit "e" at the highlighted menu for your chosen kernel", I need a little more info on how to do that. The reason I had a question on the "/dev/sda1 clean" is that mine doesn't flash, it stays there for the whole 40 to 50 seconds. Sending some of the otherinfo requested

PC hardware:
Processor: Intel Core I7 CPU 930 @ 2.8GHZX8
Memory:  7.9GIB
Disk: 2.3TB
Base system: Ubuntu 16.04LTS 32bit
Graphics: GeForce 9500GT

---

### Post by ajgreeny on 2016-09-30
Sorry about my unclear suggestion.

"Hit e" means press the "e" on your keyboard to edit the grub menu details, then follow my comments about removing quiet splash from the boot stanza you see.

I fact you may be able to get the same effect (scrolling text) from Esc once the grub menu has disappeared without editing the boot stanza; try it.

---

### Post by ardvark on 2016-10-01
I'm not sure that this makes any sense, but removing "quiet splash" seems to make it boot up about 1 minute faster. It's difficult to get good times since I have to make a change to grub . It looks like with "quiet splash" it's taking around 1:11 minutes to get to the NVIDIA splash screen. Removing "quiet splash" I get there in a little less than 30 seconds. Then another 25 seconds to the Login screen and 45 seconds to a working desktop. As far as the messages scrolling by, none had much of a delay, the longest was modem manager at about 5-8 seconds.

---

### Post by DuckHook on 2016-10-01
Assuming you are using 16.04: please post results of:```
systemd-analyze blame
``````
systemd-analyze critical-chain
``````
journalctl -p err
```
Please don't assume that I am a systemd expert. In fact, I am the furthest thing from. However, I just learned of these new tools recently and they may tell you something about what is hogging your boot times.

---

### Post by ardvark on 2016-10-02
For some reason it won't let me upload the "Journlctl" file, it's just a 2k text file??

Sending that info: [ATTACH]271473[/ATTACH]  [ATTACH]271474[/ATTACH]

---

### Post by ardvark on 2016-10-02
For some reason it worked this time..


[ATTACH]271475[/ATTACH]

---

### Post by DuckHook on 2016-10-03
You have some very ill-behaved services dragging out your boot process to atrocious times. I'm surprised you are not pulling your hair out. The worst is:```
56.154s apt-daily.service
```…followed by the trio of:```
35.051s nmbd.service
35.051s winbind.service
34.700s samba-ad-dc.service
```…which are all related to samba.
Even your network startup is slow:```
15.419s NetworkManager-wait-online.service
11.623s ModemManager.service
```In fact, the remainder of the first few dozen services are all in the seconds range when they really should be in the sub-seconds range for HW of your calibre:```
          7.263s accounts-daemon.service
          6.661s apparmor.service
          6.435s apport.service
          5.959s irqbalance.service
          5.551s ondemand.service
          5.519s networking.service
          5.323s console-kit-log-system-start.service
          5.300s NetworkManager.service
          5.245s systemd-logind.service
          5.210s speech-dispatcher.service
          5.156s rsyslog.service
          5.124s bluetooth.service
          4.662s snapd.firstboot.service
          4.574s timidity.service
          2.417s gpu-manager.service
          2.404s console-setup.service
          2.328s systemd-udevd.service
          2.292s systemd-tmpfiles-setup.service
          2.272s grub-common.service
          1.881s colord.service
          1.847s lightdm.service
          1.761s polkitd.service
          1.755s systemd-tmpfiles-setup-dev.service
          1.548s plymouth-start.service
          1.466s keyboard-setup.service
          1.353s binfmt-support.service
          1.313s avahi-daemon.service
          1.280s systemd-fsck@dev-sdb2.service
          1.275s systemd-journald.service
          1.244s systemd-rfkill.service
          1.101s systemd-modules-load.service
          1.082s systemd-fsck@dev-sdb1.service

```
If it was just one service that was causing this slowdown, we would have said, "AHA!" and been able to focus on it, but when so many are implicated, it points to a general system-wide issue that has me stumped. I would even suspect hardware: notwithstanding that your system specs are bruisers.

I note that you are using the 32-bit OS, so would encourage you to try a few experiments:

[LIST=1]
[*]Try running Ubuntu *64-bit* from a Live USB/DVD to see if this speeds things up.
[*]Try another flavour&#8213;say, Xubuntu&#8213;but also 64-bit. Measure that boot time too.
[*]Try reseating your RAM.
[*]Check also your HDD cable. Make sure the connection is good and that the cable is rated for SATA 3 (I assume from the power of the rest of your system that you are using SATA3)
[*]When booting from one of the LiveUSBs, try it both with the HDD SATA cable plugged in and not plugged in. Compare the two boot times.
[*]Check that your NIC is seated properly. Also, post the output of```
sudo lspci -vk | grep -iA13 net
``````
ifconfig
```
[/LIST]
As diagnostics go, this is pretty scattershot, but at least it's a start.

---

### Post by ardvark on 2016-10-04
I have made some progress here. I was checking the memory and realized I was missing 4G. Upon reseating and memory testing I now have 12G. Next looking at bios I figured by moving one SATA cable I was able to disable two SATA controllers that are now not needed. Finally I disabled one of my ethernet ports. This really sped up bios bootup. Right now cold boot to login is around 1:30 minutes, login to desktop is about another 25 seconds. Systemd-analyze looks much different, but I don't know if this is now normal or are there still problems.

[ATTACH]271500[/ATTACH]

---

### Post by DuckHook on 2016-10-04
> **ardvark said:**
> I have made some progress here. I was checking the memory and realized I was missing 4G. Upon reseating and memory testing I now have 12G.Is your memory all compatible? That is to say, are they all of identical specs? Also, make sure that you follow the MOBO manufacturer's instructions and seat them in the right slots. 12 GB sounds like you are using either 3 sticks of 4GB or 6 sticks of 2GB. Slot order is very important for best RAM speed.> Next looking at bios I figured by moving one SATA cable I was able to disable two SATA controllers that are now not needed.Unneeded SATA controllers rarely impact boot performance. That said, nothing wrong with disabling them either. Just remember to re-enable them if you add HDDs.> Finally I disabled one of my ethernet ports. This really sped up bios bootup.That was the main culprit right there. Your system was trying to establish a SAMBA connection as well as query for apt updates through that NIC, but it was not connected to anything. By disabling it, or better, yanking it out altogether, you force all network traffic though the connected NIC. As a secondary matter, it shows the importance&#8213;when trying to diagnose a problem&#8213;of posting complete HW info.> Right now cold boot to login is around 1:30 minutes, login to desktop is about another 25 seconds. Systemd-analyze looks much different, but I don't know if this is now normal or are there still problems.Indeed, systemd-analyze is looking much more reasonable. The timings are still pretty high, but your experience is probably like night and day compared to your old bootup. Your system specs are actually quite high-end. You should still be getting better boot times. Far too many services are still taking many seconds to boot when they should be less than a second. For comparison, my system specs are pretty similar to yours and here is my output:```
          8.640s NetworkManager-wait-online.service
          5.178s udev-configure-printer@-devices-pci0000:00-0000:00:1d.0-usb2-2\x2d1-2\x2d1.4.service
           838ms lvm2-monitor.service
           549ms apt-daily.service
           379ms dev-sda3.device
           304ms vboxdrv.service
           240ms ModemManager.service
           210ms mnt-duckhook.mount
           195ms upower.service
           161ms networking.service
           146ms systemd-fsck@dev-disk-by\x2duuid-xxxxxxxx\xxxxxxx\xxxxxxx\xxxxxxx\xxxxxxxxxxxxxxx.service
           138ms accounts-daemon.service
           107ms grub-common.service
           101ms speech-dispatcher.service
            97ms systemd-localed.service
            95ms NetworkManager.service
            94ms systemd-logind.service
            94ms apport.service
            91ms systemd-tmpfiles-setup-dev.service
            84ms irqbalance.service
            78ms lightdm.service
            76ms autofs.service
            70ms ondemand.service
            69ms alsa-restore.service
            66ms apparmor.service
            65ms systemd-udev-trigger.service
            63ms pppd-dns.service
            63ms systemd-user-sessions.service
            63ms systemd-udevd.service
            63ms udisks2.service
            60ms iio-sensor-proxy.service
            54ms gpu-manager.service
            51ms systemd-sysctl.service
            49ms systemd-modules-load.service
            47ms console-setup.service
            46ms systemd-journald.service
            46ms thermald.service
            44ms snapd.firstboot.service
            40ms avahi-daemon.service
            40ms keyboard-setup.service
            30ms colord.service
            29ms systemd-fsck@dev-disk-by\x2duuid-xxxx\xxxxxxx.service
            26ms run-rpc_pipefs.mount
            25ms systemd-tmpfiles-clean.service
            23ms user@1000.service
            18ms polkitd.service
            17ms lm-sensors.service
            16ms dev-disk-by\x2duuid-xxxxxxxx\xxxxxxx\xxxxxxx\xxxxxxx\xxxxxxxxxxxxxxx.swap
            16ms glances.service
            15ms systemd-timesyncd.service
            13ms plymouth-read-write.service
            12ms hddtemp.service
            12ms plymouth-start.service
            10ms rsyslog.service
            10ms systemd-update-utmp.service
             9ms dev-mqueue.mount
             8ms systemd-journal-flush.service
             7ms kmod-static-nodes.service
             7ms sys-kernel-debug.mount
             7ms dev-hugepages.mount
             6ms systemd-hostnamed.service
             6ms systemd-remount-fs.service
             6ms systemd-random-seed.service
             5ms rpcbind.service
             5ms dns-clean.service
             5ms boot-efi.mount
             4ms resolvconf.service
             4ms systemd-update-utmp-runlevel.service
             4ms snapd.boot-ok.service
             3ms ufw.service
             3ms nfs-config.service
             3ms rpc-statd.service
             3ms ureadahead-stop.service
             3ms systemd-tmpfiles-setup.service
             2ms rtkit-daemon.service
             2ms rpc-statd-notify.service
             2ms vboxweb-service.service
             2ms vboxautostart-service.service
             2ms tmp.mount
             2ms rc-local.service
             1ms snapd.socket
             1ms plymouth-quit-wait.service
             1ms vboxballoonctrl-service.service
             1ms setvtrgb.service
             1ms sys-fs-fuse-connections.mount

```As you can see, the only two services taking over one-second are NetworkManager and configuring printer. Everything else is sub-second. My boot time after POST to login screen is about 12 seconds. From login to DE is about 3 seconds. The biggest difference between our two setups is my use of an SSD whereas you use an HDD. But while SSDs do speed up the boot process, they aren't *that* much faster. I would say that you should be getting 30 sec to 45 sec boots after the POST routine (which is a MOBO/BIOS process and has nothing to do with the OS).

You may be happy with these boot times, but if not, then I (still) suggest that:
[LIST=1]

[*]you install a 64-bit OS
[*]try a different flavour of 'buntu.
[*]make sure RAM is in proper slot order.
[/LIST]
[s]Also, please post my requested output. Without good info, we are just stumbling around in the dark.[/s]

Edit:

Please ignore request in strikethrough text above. I did not see that you had already posted this info with the wireless script.

---

### Post by colmax on 2016-10-04
As Duckhook says maybe run 64bit
Could also use X Server instead of Nvidia for your display
In gui go Settings>Software & Updates>Additional Drivers
Cheers

---

### Post by ardvark on 2016-10-05
Thanks DuckHook for the assistance, at this point I think this is mostly a hardware issue. This is a fairly old MOBO , only has SATA II ports, so even if I went to the 64 bit versions I may not get that much of an improvement. The memory cards were all the same type filling all six slots so that should be OK. Disabling the SATA controllers did same some time because bios was looking for equipped ports (at least 10 seconds). The one thing that seems to be taking way to long is /dev/sda1 using 10 seconds. Does that mean it's taking that long to access that HD?

duck hook, banana ball, shanks I've done them all, and way too often!!:sad:

---

### Post by DuckHook on 2016-10-05
> **ardvark said:**
> Thanks DuckHook for the assistance, at this point I think this is mostly a hardware issue. This is a fairly old MOBONot that old if it can run a Core i7.> only has SATA II ports, so even if I went to the 64 bit versions I may not get that much of an improvement.The major improvement would actually be in memory management. With 12 GB, the 64-bit throughput would be faster, but I agree, it wouldn't be much faster.> The one thing that seems to be taking way to long is /dev/sda1 using 10 seconds. Does that mean it's taking that long to access that HD?It means that it's taking that long to even *find* the HDD. Tell you what&#8213;humour me just a bit longer and post the following:```
sudo blkid
``````
cat /etc/fstab
``````
sudo parted -l
``````
df -h
``````
free -h
``````
ifconfig -a
``````
dmesg | egrep -i 'error|warn|fault|fatal|fail'
``````
cat /var/log/syslog | egrep -i 'error|warn|fault|fatal|fail'
```> duck hook, banana ball, shanks I've done them all, and way too often!!:sad: ](*,) It's a crazy, crazy game for sad, sad people, ain't it? :-({|= 

Keep duffin' them balls! :biggrin:

---

### Post by ardvark on 2016-10-06
I did some experimenting here. I cloned my drive to a newer HD (with SATA 3). Moved it to another MOBO with these specs. 
Intel Core I5-3590k @ 3.4GHZ x 4
Memory 16GB
NVIDIA GeForce GTX660
SATA 3 ports

The bootup times were very similar to the other MOBO, which gives me some doubts about hardware. I then took that spare drive and made fresh load of Ubuntu 64bit version. (Is there some reason they call this AMD64 even though it runs on an Intel).  With this drive on the older MOBO I reach Login from a cold start :55 seconds. I did notice that this older bios is taking about 10 seconds longer to get to POST than the newer MOBO. So could it be that since I upgraded from 14.04 to 16.04, something was just not loaded correctly? Now my decision is do I want to go to all the trouble of reloading all the programs and setups just save around 30 seconds startup? And the fact that my Bluetooth connection stopped working on the 64 bit version. I'll put the old HD back in and try those items you just gave me.

---

### Post by DuckHook on 2016-10-06
Only you can decide if the 30 seconds is worth it. If you rarely turn the computer off (like Mrs DuckHook) then a little extra boot time is of no importance.

The truth of the matter is that any further tinkering from this point onwards will likely see only diminishing returns. Modern OSes are heavy-duty beasts and there is only so much that can be done to speed them up. 16.04 uses systemd, which is supposed to boot faster because many boot processes run in parallel. However, it can also actually *slow down* the boot process if dependent processes are not sequenced properly.

Re: amd64

This is a holdover from the way these processors were introduced into the world. AMD came out with a 64-bit chip first, so the convention ever since has been to call the architecture amd64. Nonetheless, the OS runs on both AMD and Intel chips.

I would say that your bluetooth problem settles the matter once and for all. I would rather put up with a longer boot process than try to hunt down yet another wonky problem. Added to that what you mention about redoing all your apps and settings, and you have your answer.

Irrespective of which route you decide on, remember to back up your data.

---

### Post by ardvark on 2016-10-06
Here's what came out:


[ATTACH]271529[/ATTACH]
[ATTACH]271530[/ATTACH]

---

### Post by DuckHook on 2016-10-06
The only thing that looks a little out of the ordinary is the following in dmesg:```
[   19.908051] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
```Otherwise, nothing abnormal that I can see. The dmesg output confirms that sda1 had to be remounted, presumably after failing to mount earlier. This accords with systemd-analyze which also shows an unexpectedly lengthy sda1 mount.

Since everything works, I wouldn't worry about this too much. Chasing it down would improve your boot time a little, but it is clearly not critical since your system resides on sda1 and it does eventually boot successfully.

Not much more I can do for you here, so Good Luck and Happy Ubuntuing.

And keep swinging them clubs!

---

### Post by ardvark on 2016-10-06
Thanks again for your help. I noticed when I had the old HD out it was manufactured in 2007, so it's getting a bit old. Before it really dies I'd better clone it over to a newer one.

---

