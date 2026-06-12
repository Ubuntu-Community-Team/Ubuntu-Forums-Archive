---
title: "Ubuntu 19.10 Slow to boot"
date: 2019-11-23
forum: General Help
---

### Post by roadrash on 2019-11-23
Hi everyone,  I am a Ubuntu/Linux user of many many years and I recently did a new fresh install of the latest 19.10 and I have been frustraited by a extremely long boot timeof 4 m 50s.  From starting boot from grub sceeen until it gets to the desktop is just over 2 minutes but then it spends another nearly 3 minutes working on somethuing as the hard drive is constantly running for just about another 3 minutes.  During this time it slows any operation considerably so its better to wait for the whole boot process to stop when the drive activity stops.  Once this happens the hard drive remains silent with no further activity until I start using it.  So something is taking a long time after it boots to the desktop.  This also happened in my previous versin of 18.04 too but before this it tool no time at all hardly to boot up so something since then is causing a huge delay and it cant be my installation as each one was a fresh clean install.
This has been the worst boot up time ive ever had and is like going back in time to the days of a Pentium 1.
Does anyone know what could be causing this?

here is output from lshw on this PC.
[https://paste.ubuntu.com/p/qXCY6TgjpN/]("https://paste.ubuntu.com/p/qXCY6TgjpN/")

and here is boot log: [https://paste.ubuntu.com/p/zCJYftDXXg/]("https://paste.ubuntu.com/p/zCJYftDXXg/")

---

### Post by oldfred on 2019-11-23
Your BIOS is from 2011, I might check if any newer available. 
That is just before Microsoft required vendors to use UEFI when Windows 8 was released in 2012. A few vendors started using UEFI with Windows 7 just to test their UEFI configurations.

Slow Boot --------------------------------
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453)
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392)
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)

Post these:
systemd-analyze
systemd-analyze blame #just need top ten or so, use code tags # in Forum's advanced editor

---

### Post by Autodave on 2019-11-23
Why aren't you using 18.04 then?  18.04 is a long term service release (LTS) whereas any release made until the next LTS (20.04) will only be short term.  I learned a loooong time ago to stick with the LTS releases only.

---

### Post by roadrash on 2019-11-23
> **Autodave said:**
> Why aren't you using 18.04 then?  18.04 is a long term service release (LTS) whereas any release made until the next LTS (20.04) will only be short term.  I learned a loooong time ago to stick with the LTS releases only.

I was getting a long boot time with 18.04 also thats why i installed 19.10 to see if it was better

---

### Post by roadrash on 2019-11-23
> **oldfred said:**
> Your BIOS is from 2011, I might check if any newer available. 
That is just before Microsoft required vendors to use UEFI when Windows 8 was released in 2012. A few vendors started using UEFI with Windows 7 just to test their UEFI configurations.

Slow Boot --------------------------------
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453)
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392)
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)

Post these:
systemd-analyze
systemd-analyze blame #just need top ten or so, use code tags # in Forum's advanced editor

here are the results:

> systemd-analyze
Startup finished in 4.518s (kernel) + 1min 24.656s (userspace) = 1min 29.175s 
graphical.target reached after 1min 24.585s in userspace


> systemd-analyze blame
         35.811s plymouth-quit-wait.service
         29.258s snapd.service
         27.019s dev-sdb2.device
         25.948s [email]configure-printer@usb-001-004.servic[/email]e
         25.517s udisks2.service
         25.078s networkd-dispatcher.service
         23.421s ModemManager.service
         17.832s accounts-daemon.service
         16.143s dev-loop10.device
         16.043s dev-loop12.device
         15.829s dev-loop9.device
         15.660s dev-loop13.device
         15.195s dev-loop11.device
         15.011s NetworkManager.service
         14.477s dev-loop0.device
         14.336s plymouth-read-write.service
         14.035s dev-loop7.device
         13.216s dev-loop8.device
         12.683s dev-loop6.device
         11.509s NetworkManager-wait-online.service
         11.440s dev-loop3.device
         11.422s dev-loop2.device
         11.350s dev-loop1.device

---

### Post by oldfred on 2019-11-23
Are you using all the loop/snap devices? A few like them.

Ubuntu keeps adding more snaps, I am somewhat against them especially for anything available as a .deb.
If for some reason you want old software that needs old dependencies or very new software that needs newer dependencies, I see no reason for snaps.

boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)
[https://ubuntuforums.org/showthread.php?t=2409173](https://ubuntuforums.org/showthread.php?t=2409173)
[https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements](https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements)
General snap discussion:
[https://ubuntuforums.org/showthread.php?t=2411218](https://ubuntuforums.org/showthread.php?t=2411218)
[https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb) & 
[https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead](https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead)

---

### Post by roadrash on 2019-11-23
> **oldfred said:**
> Are you using all the loop/snap devices? A few like them.

Ubuntu keeps adding more snaps, I am somewhat against them especially for anything available as a .deb.
If for some reason you want old software that needs old dependencies or very new software that needs newer dependencies, I see no reason for snaps.

boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)
[https://ubuntuforums.org/showthread.php?t=2409173](https://ubuntuforums.org/showthread.php?t=2409173)
[https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements](https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements)
General snap discussion:
[https://ubuntuforums.org/showthread.php?t=2411218](https://ubuntuforums.org/showthread.php?t=2411218)
[https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb) & 
[https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead](https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead)

Wow I didnt realise I was using these snap versions of apps.  I usualy install all my apps via the terminal or using sysnaptic.
here is a list of the snaps I have:
> sudo snap list
Name               Version                     Rev   Tracking  Publisher   Notes
chromium           78.0.3904.108               949   stable    canonical&#10003;  -
core               16-2.42.1                   8039  stable    canonical&#10003;  core
core18             20191030                    1265  stable    canonical&#10003;  base
gnome-3-28-1804    3.28.0-16-g27c9498.27c9498  110   stable/&#8230;  canonical&#10003;  -
gnome-calculator   3.34.1+git1.d34dc842        544   stable/&#8230;  canonical&#10003;  -
gnome-characters   v3.32.1+git2.3367201        367   stable/&#8230;  canonical&#10003;  -
gnome-logs         3.34.0                      81    stable/&#8230;  canonical&#10003;  -
gtk-common-themes  0.1-25-gcc83164             1353  stable/&#8230;  canonical&#10003;  -

di I just remove the snap versions and replace them with ones done via apt or synaptic and what is the scaps called "core2" & "core18" and do I jusr remove these 2 and reinstall them again also.
I updated my bios too.

---

### Post by roadrash on 2019-11-23
OK think I got it from your informatin in your thread here :[https://ubuntuforums.org/showthread.php?t=2409173[](https://ubuntuforums.org/showthread.php?t=2409173[)

Well it sort of worked but its still slow to boot up.

I was unable to remove the packages "core" & core18" but i removed all the others and purged snap.
Then I reinstalled everything I removed but this time did it with apt in the terminal.  The only problem I had was there wasnt a version of google chrome browser that wasnt a snap one and when i installed the one in the repo with apt it reinstated snap again and I had to remove chrome browser again and purge snap again.  The only way I could install a non snap version of chrome browser was to download a .deb from googles website and I installed it using gdebi.
It works ok but there is no desktop icon and I have to launch it from a terminal.
Is there a beter way to do this and what about those 2 remaining packages "core" and "core18" that I am not allowed to remove?

---

### Post by oldfred on 2019-11-23
I use chromium and new version has it as a snap. 
I did find a ppa for it, but did not save it as I still am using 18.04 as main working install.

I just did the full removal of all snaps. First time I removed them one at a time, then found this:
The commands are snap remove gnome-system-monitor (no sudo required), followed by sudo apt install gnome-system-monitor
sudo apt remove --purge snapd
sudo apt purge gnome-software-plugin-snap

I think I did all of these. And newer installs still are slower than when I first built system with SSD and had very fast boot. Back then they were working on improving boot time, but that seems to have gone by the wayside.


turned off NetworkManager-wait
     $ systemctl unmask NetworkManager-wait-online.service
     $ systemctl enable NetworkManager-wait-online.service
Changed systemctl daily timer 
housecleaned systemctl logs
changed from quiet splash to noplymouth, will see boot process rather than Ubuntu logo
sudo apt install libblockdev-crypto2 libblockdev-mdraid2
turned off printer when rebooting
removed snaps

---

### Post by roadrash on 2019-11-24
> **oldfred said:**
> I use chromium and new version has it as a snap. 
I did find a ppa for it, but did not save it as I still am using 18.04 as main working install.

I just did the full removal of all snaps. First time I removed them one at a time, then found this:
The commands are snap remove gnome-system-monitor (no sudo required), followed by sudo apt install gnome-system-monitor
sudo apt remove --purge snapd
sudo apt purge gnome-software-plugin-snap

I think I did all of these. And newer installs still are slower than when I first built system with SSD and had very fast boot. Back then they were working on improving boot time, but that seems to have gone by the wayside.


turned off NetworkManager-wait
     $ systemctl unmask NetworkManager-wait-online.service
     $ systemctl enable NetworkManager-wait-online.service
Changed systemctl daily timer 
housecleaned systemctl logs
changed from quiet splash to noplymouth, will see boot process rather than Ubuntu logo
sudo apt install libblockdev-crypto2 libblockdev-mdraid2
turned off printer when rebooting
removed snaps

Thanks for all the help oldfred but its loking like I either have to put up with it or switch to another distro.  for all this I haven't actually seen any increase in the boot time and maybe only a marginal increase in applications launching.  Oh well I'm sure the devs will be working on something seeing as this is still a recent change over to using snap packages.
cheers anyway

---

