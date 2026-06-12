---
title: "ubuntu 18.04 lts 10 minutes to boot to login"
date: 2018-07-02
forum: General Help
---

### Post by denny-mello on 2018-07-02
This morning there was an update to the kernel from 4.15.0-23-generic to 4.15.0-24-generic. After installing such update I rebooted the system and now it takes around 10 minutes to show the login prompt (before it used to be very fast)

```
&#10140;  ~ systemd-analyze blame
    9min 36.123s plymouth-quit-wait.service
    9min 36.123s plymouth-quit-wait.service
     8min 9.803s snapd.seeded.service
         37.303s snapd.service
          6.186s NetworkManager-wait-online.service
          4.369s udisks2.service
          1.360s dev-sda1.device
          1.016s dev-loop0.device



```

I searched for 'snapd.service' and 'snapd.seeded.service' "slow" but my findings were unsuccessful and not relevant to my case. Do you have any ideas on how could I fix this problem?

---

### Post by oldfred on 2018-07-02
Are you using snaps?
I uninstalled all of them, since not currently using any of them.

          34  snap list
   35  sudo snap remove gnome-logs
   36  sudo snap remove gnome-calulator 
....
      
    46  sudo systemctl stop snapd
   47  snap list
      
    56  ls -l /snap/core
   57  sudo systemctl stop snapd
   58  sudo umount /snap/core/XXXX  # several 
   59  sudo snap remove core

[https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb)

---

### Post by bodhin2 on 2018-07-02
how can i tell what i installed via snap and then would i uninstall via snap?  and then i could reinstall in synaptic?  i have 3 laptops to tweak again then.  thanks.

---

### Post by denny-mello on 2018-07-02
output from journalctl-u snapd.service

when system was working:

```

lug 02 04:07:33 ubuntu18 snapd[703]: snap "gnome-3-26-1604": snap has no updates available
lug 02 04:07:33 ubuntu18 snapd[703]: snap "core18": snap has no updates available
lug 02 04:07:33 ubuntu18 snapd[703]: snap "communitheme": snap has no updates available
lug 02 04:07:33 ubuntu18 snapd[703]: snap "core": snap has no updates available
lug 02 04:07:33 ubuntu18 snapd[703]: 2018/07/02 04:07:33.265803 autorefresh.go:388: auto-refresh: all snaps are up-to-date
lug 02 12:52:00 ubuntu18 snapd[703]: 2018/07/02 12:52:00.881677 storehelpers.go:413: cannot refresh:
lug 02 12:52:00 ubuntu18 snapd[703]: snap "gnome-3-26-1604": snap has no updates available
lug 02 12:52:00 ubuntu18 snapd[703]: snap "core18": snap has no updates available
lug 02 12:52:00 ubuntu18 snapd[703]: snap "communitheme": snap has no updates available
lug 02 12:52:00 ubuntu18 snapd[703]: snap "core": snap has no updates available
lug 02 12:52:00 ubuntu18 snapd[703]: 2018/07/02 12:52:00.882827 autorefresh.go:388: auto-refresh: all snaps are up-to-date
lug 02 12:56:49 ubuntu18 snapd[703]: 2018/07/02 12:56:49.625045 main.go:81: Exiting on terminated signal.
lug 02 12:56:49 ubuntu18 systemd[1]: Stopping Snappy daemon...
lug 02 12:56:49 ubuntu18 systemd[1]: Stopped Snappy daemon.
-- Reboot --

```

after updates i get this:

```

lug 02 12:57:23 ubuntu18 systemd[1]: Starting Snappy daemon...
lug 02 12:58:53 ubuntu18 snapd[775]: AppArmor status: apparmor is enabled and all features are available
lug 02 12:58:53 ubuntu18 systemd[1]: snapd.service: Start operation timed out. Terminating.
lug 02 12:58:53 ubuntu18 systemd[1]: snapd.service: Failed with result 'timeout'.
lug 02 12:58:53 ubuntu18 systemd[1]: Failed to start Snappy daemon.
lug 02 12:58:53 ubuntu18 systemd[1]: snapd.service: Service hold-off time over, scheduling restart.
lug 02 12:58:53 ubuntu18 systemd[1]: snapd.service: Scheduled restart job, restart counter is at 1.
lug 02 12:58:53 ubuntu18 systemd[1]: Stopped Snappy daemon.
lug 02 12:58:53 ubuntu18 systemd[1]: Starting Snappy daemon...
lug 02 12:58:53 ubuntu18 snapd[1110]: AppArmor status: apparmor is enabled and all features are available
lug 02 12:58:54 ubuntu18 snapd[1110]: AppArmor status: apparmor is enabled and all features are available
lug 02 12:58:54 ubuntu18 snapd[1110]: 2018/07/02 12:58:54.224173 daemon.go:343: started snapd/2.33 (series 16; classic) ubuntu/18.04 (amd64) li
lug 02 12:58:54 ubuntu18 systemd[1]: Started Snappy daemon.
-- Reboot --

```

after that i removed communitheme i thought maybe it was related to the troubles but still 10 minutes to boot. this are the snaps installed on the system:

```

&#10140;  ~ snap list --all
Name             Version    Rev   Tracking  Developer  Notes
core             16-2.32.6  4571  stable    canonical  core,disabled
core             16-2.32.8  4650  stable    canonical  core,disabled
core             16-2.33    4830  stable    canonical  core
core18           0.1        19    stable    canonical  base
gnome-3-26-1604  3.26.0     64    stable/&#8230;  canonical  -

```


Now wouldn't disable snaps prevent the system from booting? isn't core package required for the system to work properly?

also yes i replaced the snaps calculator and gnome-logs around 1 month ago i think

---

### Post by deadflowr on 2018-07-02
> Now wouldn't disable snaps prevent the system from booting? isn't core package required for the system to work properly?
Not at all
snaps are independent of the system.
core is only required for snaps to work.
Not related to the functions of the system at large.
See monkeybrain20122's thread on this here:
[https://ubuntuforums.org/showthread.php?t=2391341]("https://ubuntuforums.org/showthread.php?t=2391341")

---

### Post by denny-mello on 2018-07-02
I removed snaps completely from the system but didn't fix the slow boot time:

```

&#10140;  ~ systemd-analyze                   
Startup finished in 4.860s (kernel) + 8min 44.251s (userspace) = 8min 49.111s
graphical.target reached after 8min 44.231s in userspace

&#10140;  ~ systemd-analyze blame     8min 36.974s plymouth-quit-wait.service
    5min 21.419s phpsessionclean.service
          6.174s NetworkManager-wait-online.service
          3.331s udisks2.service
           784ms ufw.service
           728ms fwupd.service
           608ms dev-sda1.device
           461ms apparmor.service
           224ms NetworkManager.service
           199ms networkd-dispatcher.service
           191ms systemd-journal-flush.service
           186ms keyboard-setup.service
           183ms plymouth-start.service
           177ms accounts-daemon.service
           163ms grub-common.service
           160ms systemd-hostnamed.service
           156ms ModemManager.service
           147ms apport.service
           146ms sysfsutils.service
           145ms speech-dispatcher.service
           145ms systemd-timesyncd.service
           141ms upower.service
           140ms systemd-resolved.service

```

Is it possible that the kernel upgrade don't like my system? Should i try revert to [COLOR=#000000]4.15.0-23-generic? I have no clue how to proceed and i'm scared of breaking even more things![/COLOR]

---

### Post by oldfred on 2018-07-02
Are you running something using a different than default php?
Or is system an upgrade and something did not get reset?

       PHP7-ubuntu sessionclean searches for "php5" named binary 
[https://bugs.launchpad.net/ubuntu/+source/php-defaults/+bug/1579480](https://bugs.launchpad.net/ubuntu/+source/php-defaults/+bug/1579480)

---

### Post by deadflowr on 2018-07-02
> Is it possible that the kernel upgrade don't like my system? Should i try revert to 4.15.0-23-generic? I have no clue how to proceed and i'm scared of breaking even more things!
Sure.
That's why the system defaults to always keep the last kernel.
So you can boot into it if the new one is iffy.
Reboot and select the old one in the boot menu (under the advanced options menu listing option)
See how it performs versus the  new one.

If you don't see the boot menu, then you may need to access it with either ESC or shift depending on system (legacy BIOS uses shift, newer UEFI uses ESC)
You need to press the key (or better yet tap the key repeatedly so it takes at the right time)
when the very first screen that shows when you start the machine (the one usually showing the name of the machine) goes black.
if that make sense

---

### Post by denny-mello on 2018-07-02
> **oldfred said:**
> Are you running something using a different than default php?
Or is system an upgrade and something did not get reset?


I don't recall installing php packages but I am using the system since april when it was last point beta. Maybe some other application I've installed did change php packages I'm not sure and don't know how to check.

Regarding system upgrades I usually reboot when asked by the system or when there are kernel upgrades.

Ok so I've tried rebooting with kernel .23 and it is very fast! I'm going reboot with the new one and see if that magically fixed everything.

---

### Post by wildmanne39 on 2018-07-02
Hello bodhin2, please start your own thread to ask your question instead of posting in someone else's.

Thanks

---

### Post by denny-mello on 2018-07-02
So it's definitely the new kernel that hangs the system on boot for 10 mintues. After login however everything seems to work : audio and video play fine. Thanks everyone for helping me very much appreciated. Hopefully next kernel upgrade will fix everything! Until then I can boot the old one.

---

### Post by kerry_s on 2018-07-02
move the mouse while it is booting, just swing it side to side or circle as long as it is moving it'll boot right up.

it's a kernel bug. i've seen it in other distros which have been fixed.

---

### Post by waburden-4 on 2018-07-02
I'm having the same issue with the new version 24 kernel but my hang is approx. 4 minutes. I hit the power button on my laptop and got the following display with the last line which seeming to indicate an issue: "Started Gnome Displ;ay Manager.ss finishes up...ce....tem changes.PP link was shut down". By the way, moving the mouse during boot, as was previously suggested, did not work for me.

---

### Post by wildmanne39 on 2018-07-02
Hello waburden-4, please start your own thread so you can get the help you need instead of posting in someone else's.

Thanks

---

### Post by screaminj3sus on 2018-07-02
after all of the other distros that have already ran into this bug, I can't believe this nonsense made it into a ubuntu LTS update.

---

### Post by kazakore on 2018-07-03
> **screaminj3sus said:**
> after all of the other distros that have already ran into this bug, I can't believe this nonsense made it into a ubuntu LTS update.

Unfortunately experience and made this rather easy for me to believe! :(

---

### Post by waburden-4 on 2018-07-03
Done. Never quite sure how to play this. I suppose the reason for this is so that I get a solution notification instead of following someone else's post for one, eh??

---

### Post by Delosari on 2018-07-14
> **waburden-4 said:**
> I'm having the same issue with the new version 24 kernel but my hang is approx. 4 minutes. I hit the power button on my laptop and got the following display with the last line which seeming to indicate an issue: "Started Gnome Displ;ay Manager.ss finishes up...ce....tem changes.PP link was shut down". By the way, moving the mouse during boot, as was previously suggested, did not work for me.
 Please tell me how you solved it. I am having the same issue right now when I am finishing my phd.

I am stuck in the tem changes. pp link was shut down line.

---

### Post by ariskk on 2018-07-14
Hi all, I am having the same issue. It started a few days ago. Tried with .23 kernel and it is fast/normal but .24 kernel the boot gets stuck (I use a combination of ESC / Ctrl-C / Enter to stop snappy from slowing things down but maybe that caused the GUI to not start and I was just spending 2 hours to bring it up again). Anyone knows what is the root cause of this?

---

### Post by Delosari on 2018-07-14
> **ariskk said:**
> Hi all, I am having the same issue. It started a few days ago. Tried with .23 kernel and it is fast/normal but .24 kernel the boot gets stuck (I use a combination of ESC / Ctrl-C / Enter to stop snappy from slowing things down but maybe that caused the GUI to not start and I was just spending 2 hours to bring it up again). Anyone knows what is the root cause of this?

I am trying to understand what is being posted here:

[https://bugs.launchpad.net/ubuntu/+bug/1779827](https://bugs.launchpad.net/ubuntu/+bug/1779827)

I tried the sudo pt-get install haveged but it did not work for me.

How did you install the .23 kernel from the tty?

---

### Post by ariskk on 2018-07-15
I didn't install .23 myself. I just selected it during booting (grub). So I rebooted, selected the "Ubuntu Advanced" options, then I selected .23 .

---

### Post by denny-mello on 2018-07-16
If you guys don't want to roll back to older kernel you can try this fix by user apeitheo2, it worked for me and boot time is back to normal speeds.

[https://ubuntuforums.org/showthread.php?t=2395459&p=13781140#post13781140](https://ubuntuforums.org/showthread.php?t=2395459&p=13781140#post13781140)

---

