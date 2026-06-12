---
title: "Almost new install 12.04 64bit, has become like wading through treacle"
date: 2014-04-04
forum: General Help
---

### Post by Windoze Refugee on 2014-04-04
Hi Folks, 
Just a couple of weeks ago I installed a brand new version of 12.04 to my new 64 bit machine.
It ran brialliantly to begin with, but in the last few days it has become so slow as to be almost unusable.
I have also encountered a total error when trying to prefrom a software update and had a couple of complete crashes where the screen has displayed , well, gibberish, and the whole machine had locked up.
Has anyone come up against anythig like this, or have any idea what's going on?
CheersWR

---

### Post by TheFu on 2014-04-04
What 
* do the log files say?
* is using all the CPU?
* is sucking all the RAM?
* is eating all the network?
* is using all the disk I/O?

---

### Post by Windoze Refugee on 2014-04-04
Hi TheFU
Cheers for your input.
Forgive my newbiness, but where can I acquire the info you seek?

---

### Post by oldfred on 2014-04-04
In terminal 

This shows partition use
df -h

This shows what is running and %, use q to exit back to terminal
top

You should have Log File Viewer to view log files
I like to review dmesg as that is boot log and will tell you if something is not loading correctly. It is long and only errrors, warning, or very long time differences in time stamps may be issues. Best not to post entire thing, just parts with issues or questions.

---

### Post by Windoze Refugee on 2014-04-04
HI Fred.OK
 df -h returns the following
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       914G   32G  837G   4% /
udev            1.6G  4.0K  1.6G   1% /dev
tmpfs           314M  920K  313M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.6G  216K  1.6G   1% /run/shm
```

---

### Post by Windoze Refugee on 2014-04-04
this is the dmesg results (partial)
Ive taken out what appeared normal, but I am not very familiar with this 

```
[    0.192784] Trying to unpack rootfs image as initramfs...
[    0.564690] Freeing initrd memory: 17052K (ffff880035ea2000 - ffff880036f49000)

[    0.606175] intel_idle: does not run on family 6 model 15

[    0.606487] GHES: HEST is not enabled!

[    0.818183] PM: Hibernation image not present or could not be loaded.

[    0.827599] EDD information not available.

[    1.071691] sd 2:0:0:0: [sda] Write Protect is off

[    1.071755] scsi 2:0:1:0: Direct-Access     ATA      ST3500630AS      3.AA PQ: 0 ANSI: 5

[    1.072041] sd 2:0:1:0: [sdb] Write Protect is off

[    1.115799] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[    1.352305] ata4.00: unsupported device, disabling
[    1.352308] ata4.00: disabled

[    3.745854] EXT4-fs (sda1): orphan cleanup on readonly fs
[    3.902263] EXT4-fs (sda1): 30 orphan inodes deleted

[   11.669425] [drm] Initialized nouveau 1.1.1 20120801 for 0000:06:00.0 on minor 0
[   12.088832] type=1400 audit(1396635799.759:2): apparmor="STATUS" operation="profile_load" parent=721 profile="unconfined" name="/sbin/dhclient" pid=722 comm="apparmor_parser"
[   12.088842] type=1400 audit(1396635799.759:3): apparmor="STATUS" operation="profile_load" parent=721 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=722 comm="apparmor_parser"
[   12.088849] type=1400 audit(1396635799.759:4): apparmor="STATUS" operation="profile_load" parent=721 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=722 comm="apparmor_parser"
[   12.088994] type=1400 audit(1396635799.759:5): apparmor="STATUS" operation="profile_replace" parent=719 profile="unconfined" name="/sbin/dhclient" pid=720 comm="apparmor_parser"
[   12.089004] type=1400 audit(1396635799.759:6): apparmor="STATUS" operation="profile_replace" parent=719 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=720 comm="apparmor_parser"
[   12.089011] type=1400 audit(1396635799.759:7): apparmor="STATUS" operation="profile_replace" parent=719 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=720 comm="apparmor_parser"
[   12.089505] type=1400 audit(1396635799.759:8): apparmor="STATUS" operation="profile_replace" parent=721 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=722 comm="apparmor_parser"
[   12.089513] type=1400 audit(1396635799.759:9): apparmor="STATUS" operation="profile_replace" parent=721 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=722 comm="apparmor_parser"
[   12.089663] type=1400 audit(1396635799.759:10): apparmor="STATUS" operation="profile_replace" parent=719 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=720 comm="apparmor_parser"
[   12.089670] type=1400 audit(1396635799.759:11): apparmor="STATUS" operation="profile_replace" parent=719 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=720 comm="apparmor_parser"
[   12.680892] init: failsafe main process (864) killed by TERM signal

[   16.841644] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.842359] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.862072] sky2 0000:03:00.0 eth1: enabling interface
[   16.862145] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   16.862851] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   17.094825] audit_printk_skb: 105 callbacks suppressed
[   17.094831] type=1400 audit(1396635804.763:47): apparmor="STATUS" operation="profile_replace" parent=1028 profile="unconfined" name="launchpad_integration" pid=1035 comm="apparmor_parser"
[   17.094847] type=1400 audit(1396635804.763:48): apparmor="STATUS" operation="profile_replace" parent=1028 profile="unconfined" name="sanitized_helper" pid=1035 comm="apparmor_parser"
[   17.094855] type=1400 audit(1396635804.763:49): apparmor="STATUS" operation="profile_replace" parent=1028 profile="unconfined" name="/usr/bin/evince-previewer" pid=1035 comm="apparmor_parser"
[   17.108054] type=1400 audit(1396635804.779:50): apparmor="STATUS" operation="profile_replace" parent=1028 profile="unconfined" name="launchpad_integration" pid=1035 comm="apparmor_parser"
[   17.108064] type=1400 audit(1396635804.779:51): apparmor="STATUS" operation="profile_replace" parent=1028 profile="unconfined" name="sanitized_helper" pid=1035 comm="apparmor_parser"
[   17.108072] type=1400 audit(1396635804.779:52): apparmor="STATUS" operation="profile_replace" parent=1028 profile="unconfined" name="/usr/bin/evince-thumbnailer" pid=1035 comm="apparmor_parser"
[   17.124043] type=1400 audit(1396635804.795:53): apparmor="STATUS" operation="profile_replace" parent=1028 profile="unconfined" name="sanitized_helper" pid=1035 comm="apparmor_parser"
[   17.128863] type=1400 audit(1396635804.799:54): apparmor="STATUS" operation="profile_replace" parent=1028 profile="unconfined" name="sanitized_helper" pid=1035 comm="apparmor_parser"
[   17.128879] type=1400 audit(1396635804.799:55): apparmor="STATUS" operation="profile_replace" parent=1028 profile="unconfined" name="/usr/bin/evince-previewer" pid=1035 comm="apparmor_parser"
[   17.140048] type=1400 audit(1396635804.811:56): apparmor="STATUS" operation="profile_replace" parent=1028 profile="unconfined" name="launchpad_integration" pid=1035 comm="apparmor_parser"
[   20.050842] sky2 0000:03:00.0 eth1: Link is up at 100 Mbps, full duplex, flow control both
[   20.050858] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   55.163753] audit_printk_skb: 54 callbacks suppressed
[   55.163759] type=1400 audit(1396635842.831:75): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2109 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  240.889652] perf samples too long (2516 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[  887.301929] type=1400 audit(1396636674.972:76): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=977 comm="cupsd" pid=977 comm="cupsd" capability=36  capname="block_suspend"
[ 6289.127287] perf samples too long (5003 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
```

---

### Post by Windoze Refugee on 2014-04-04
There was this odd entry n the log file that may be of interest too

Apr  4 20:17:01 jonathan-P5W-DH-Deluxe CRON[2575]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  4 21:07:56 jonathan-P5W-DH-Deluxe kernel: [ 6289.127287] perf samples too long (5003 > 5000), lowering kernel.perf_event_max_sample_rate to 25000

---

### Post by Windoze Refugee on 2014-04-04
Dont know if it helps but these are more entries from the log file, each of which has 'failed' in the line:

Apr  4 19:23:24 jonathan-P5W-DH-Deluxe NetworkManager[995]: <warn> failed to allocate link cache: (-10) Operation not supported

Apr  4 19:23:24 jonathan-P5W-DH-Deluxe NetworkManager[995]: <warn> failed to allocate link cache: (-10) Operation not supported
Apr  4 19:23:36 jonathan-P5W-DH-Deluxe NetworkManager[995]: <warn> DNS: plugin dnsmasq update failed

Apr  4 19:23:48 jonathan-P5W-DH-Deluxe NetworkManager[995]: <info> (eth1): IP6 addrconf timed out or failed.

---

### Post by TheFu on 2014-04-04
> **TheFu said:**
> What 
* do the log files say?
* is using all the CPU?
* is sucking all the RAM?
* is eating all the network?
* is using all the disk I/O?

* [http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)
* top (cpu/ram)
* netstat (networking by port)
* iostat (busy processes are likely the disk users)
* google for other methods.

Having **performance monitoring** setup is helpful, especially on servers. There are 20 different ways to do that. I've been using SysUsage, but will probably switch to something else.

Just saw a bunch of replies ... ah ... network manager.  I don't use it, so can't really help. Sorry.

---

### Post by oldfred on 2014-04-04
I see run-parts is a command to run something, but is that just to check to run cron? Have not delved into details of cron.

But your  timestamps of 30 to 55 to 240 to 887 are indications of something wrong. Not familar with specific errors shown.

It looks like they did a fix in the kernel which may now be in Ubuntu's kernel also to lower system performance but let it keep working. But some underlying issue.
[https://bugzilla.redhat.com/show_bug.cgi?id=1013708](https://bugzilla.redhat.com/show_bug.cgi?id=1013708)
[https://bbs.archlinux.org/viewtopic.php?id=170471](https://bbs.archlinux.org/viewtopic.php?id=170471)
[http://askubuntu.com/questions/402266/why-does-it-take-over-a-minute-for-the-desktop-to-load-after-logging-in](http://askubuntu.com/questions/402266/why-does-it-take-over-a-minute-for-the-desktop-to-load-after-logging-in)

---

### Post by Windoze Refugee on 2014-04-04
hans for tryng anyways TheFu

Thanks for the info Fred, but I have to confess I dont know a) what that really means or b) how to fix it 
:(

Any assistance gratefully received....

---

### Post by oldfred on 2014-04-04
Where is this entry coming from?
Apr  4 20:17:01 jonathan-P5W-DH-Deluxe CRON[2575]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

I do not have any default entries in /etc/cron.hourly. Do you have something in that folder?

---

### Post by TheFu on 2014-04-04
> **Windoze Refugee said:**
> hans for tryng anyways TheFu

Thanks for the info Fred, but I have to confess I dont know a) what that really means or b) how to fix it 
:(

Any assistance gratefully received....

I would _guess_ that networking issues are what is happening.  What did **top** show as the problem?  When DNS issues hit, everything feels slower.  You haven't said - wifi or wired ethernet?

While I can't help with network manager issues, hopefully someone else will.  In a few days if nobody else has jumped in, we can solve this _my way_ - which always works, but isn't as easy for someone knew to UNIX/Linux.

On a new netbook here, I'm using 13.10 with network manager (default). Things are not good. When the GigE wired connection is connected alone, I'm seeing pitiful speeds 12Kb/sec. If I enable with wifi and leave the wired GigE connected, speeds are over 920Mb/sec - like they should be. The wired connection gets higher priority.  If I disable wifi in the GUI, it is back to 12Kb/sec, but if I take the wifi adapter "down" using ifconfig - the GigE connection keeps working at the expected levels.  I don't use wifi much - after doing it professionally for a few years, I know how much it sucks when compared to wired connections.

Anyway - hopefully someone will see what the real issue is and be able to help.  I'm only guessing it is networking - you'll need to look at all the other things my first post suggested to know for sure.

---

### Post by Windoze Refugee on 2014-04-05
> **oldfred said:**
> Where is this entry coming from?
Apr  4 20:17:01 jonathan-P5W-DH-Deluxe CRON[2575]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

I do not have any default entries in /etc/cron.hourly. Do you have something in that folder?

Hi Fred.
I looked in that folder and only found the following

# DO NOT EDIT OR REMOVE
# This file is a simple placeholder to keep dpkg from removing this directory 

Whatever is goiong on its getting worse.
I have a feeling its since I installed some updates earlier on the week, but cant rememebr for sure :(

---

### Post by Windoze Refugee on 2014-04-05
> **TheFu said:**
> I would _guess_ that networking issues are what is happening.  What did **top** show as the problem?  When DNS issues hit, everything feels slower.  You haven't said - wifi or wired ethernet?

While I can't help with network manager issues, hopefully someone else will.  In a few days if nobody else has jumped in, we can solve this _my way_ - which always works, but isn't as easy for someone knew to UNIX/Linux.

On a new netbook here, I'm using 13.10 with network manager (default). Things are not good. When the GigE wired connection is connected alone, I'm seeing pitiful speeds 12Kb/sec. If I enable with wifi and leave the wired GigE connected, speeds are over 920Mb/sec - like they should be. The wired connection gets higher priority.  If I disable wifi in the GUI, it is back to 12Kb/sec, but if I take the wifi adapter "down" using ifconfig - the GigE connection keeps working at the expected levels.  I don't use wifi much - after doing it professionally for a few years, I know how much it sucks when compared to wired connections.

Anyway - hopefully someone will see what the real issue is and be able to help.  I'm only guessing it is networking - you'll need to look at all the other things my first post suggested to know for sure.

HI TheFU

I dont use wifi at all.
My wife is an ES sufferer and so we only have wired connections at home

---

### Post by Windoze Refugee on 2014-04-05
If the issue/s result from a recent update, is there a away to roll it back at all?

---

### Post by 23dornot23d on 2014-04-05
Rollbacks are not available - unless you have something like Timeshift installed .... which is useful ....

You have a lot of disk space so you could if you wanted to install alongside with a fresh install of 12.04
or go for something newer ..... the 14.04 is due out soon *(April 17th) and the 64 bit is running really quickly and smoothly on
my own setup.

There may be things in your original install you want to keep ..... so by installing alongside it - you can
always go back into the one that runs like treacle and sort it at your leisure, as you should be able to run your
system a lot better again in a new fresh install ...... which will become another option at boot up.

Seems  that you have only being running the 64bit for 3 weeks looking at old  threads .... so maybe not so much of a problem to try fresh again
depends if you feel you have a lot to set up - not sure how long it took to set thunderbird up ..... but that
may need doing again in the new install ...... and the camera setup .....

Options .... make it a dual boot system which gives you the chance to go between
the two systems to also compare what might be wrong with one of them in more detail.
Takes around 30 mins to do a install alongside existing ones ..... can takes hours to sort out
problems once something odd has crept into the system - but this can still be sorted - while still
being able to run everything in your second system.

Both systems can be the same version 12.04 64bit ..... and run independantly of one another ....
or you could put something else on like the 14.04 64 bit system when it comes out on the 17th
of this month.

---

### Post by dragonfly41 on 2014-04-05
Looking through your logs clues of 'failed' ... and google searching this pattern ...

```
DNS: plugin dnsmasq update failed
```

suggests you could look at dnsmasq ...

[http://ubuntuforums.org/showthread.php?t=2046605](http://ubuntuforums.org/showthread.php?t=2046605)

Might be worth a try. Admittedly a shot in the dark.

---

### Post by Windoze Refugee on 2014-04-06
HI Folks.
Thanks again fo your input.
Things seem to be appreciably worse when using firefox, espceially opening a new tab/page, as this seems to use up 98% of RAM. Although this also seems to be the case when starting Thunderbird or even checking for new emails.
I'm not averse to upgrading to a later distro if you think it will fix things. The mistake I think I made was install all updates (except the recommendeds - I dont want chrome and I dont use twitter :) )

TheFU - IM strongly leaning towards your fix if you have the time to talk me through it.
But naturally, any other suggestions gratefully received.
Cheers.
WR

---

### Post by Windoze Refugee on 2014-04-07
OK. I had a brainwave. I thought that if I upgraded to the next ubuntu (12.10) all my problems would magically disappear.
Oh how wrong I was!!
Got to the "now you need to reboot to complete" part, rebooted&#8230;and&#8230;
Nothing...
Now it won't boot at all&#8230;
:( 
Any ideas?

---

### Post by oldfred on 2014-04-07
Often an upgrade on top of issues just compound the issues. 
But a clean install can fix issues, if you have /home and all data, configurations & list of installed apps available to reset quickly to you previous configuration.
You can also overinstall without formatting. Some call that a "dirty" install as only new install files get overwritting but your old files stay. Not sure if configuration files are kept or overwritten. Last time I did an upgrade it asked about configuration files but neither use new or save old was always correct.
Still best to still have good backups.

We can see if we can fix booting. But may need full chroot from working kernel into system to resolve issues.
Lets see where you are at.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

