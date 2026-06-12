---
title: "Automatic Check for Updates"
date: 2016-07-11
forum: General Help
---

### Post by Dennis N on 2016-07-11
I may have a problem with automatic update checks. I haven't seen any update notifications on this 16.04 system that I can recall. I have done some updating myself, but not more recent than Jun 17 from history.log.

From what I read here:

[http://serverfault.com/questions/20747/find-last-time-update-was-performed-with-apt-get](http://serverfault.com/questions/20747/find-last-time-update-was-performed-with-apt-get)

**update-success-stamp** shows the last time **apt-get update** was run. 

Output from my Xubuntu 16.04 (done Jul 11):

```
dmn@Sydney:/var/lib/apt/periodic$ ls -l
total 0
-rw-r--r-- 1 root root 0 Apr 26 11:36 unattended-upgrades-stamp
-rw-r--r-- 1 root root 0 Jul 11 08:03 update-stamp
-rw-r--r-- 1 root root 0 Jun 17 08:26 update-success-stamp
-rw-r--r-- 1 root root 0 Apr 26 11:36 upgrade-stamp

```
shows the value is Jun 17 - almost a month ago. If I have "automatically check for updates daily" set in the "Software and Updates" tool, shound this not be changing for these 'daily' checks? I think that Jun 17 value may well be a user-initiated check, not necessarily an automatic check. 

Also, what is the significance of the "update-stamp" and "upgrade-stamp"? I don't find information on those. On this system, Apr 26 is the date the OS was installed.

---

### Post by Dennis N on 2016-07-11
I missed an upgrade done through Synaptic Package Manager on Jun 18:

```
Start-Date: 2016-06-18  05:48:23
Commandline: /usr/sbin/synaptic
Requested-By: dmn (1000)
Upgrade: [list omitted here] 
End-Date: 2016-06-18  05:48:37

```
But this is the last one. Why did update-success-stamp not include this? I would have used the Refresh button on Synaptic to get them.

---

### Post by QDR06VV9 on 2016-07-11
I have 2 installs of 16.04 and one works as expected with unattended-updates and the other one miss's them all.
I have not been able to find any solution to this as of now...but still looking into a fix.
So thanks for posting this Dennis N ;)

---

### Post by sudodus on 2016-07-11
I have the same or similar problem in a system created a couple of weeks before the release of Xenial. (This system is also tweaked a lot.) It was offering updates during a period of time, but now I [have to] update & dist-upgrade manually.

Could there be a difference between systems installed from a released Xenial iso file and systems that are somehow upgraded from previous versions?

---

### Post by Dennis N on 2016-07-11
> Could there be a difference between systems installed from a released Xenial iso file and systems that are somehow upgraded from previous versions?
I don't know the answer, but this was installed from the iso for the final release. Not an in place upgrade.

---

### Post by Dennis N on 2016-07-11
Further investigations.

On my laptop now (computer in post #1 is a desktop machine), also uses Xubuntu 16.04 (but installed from the 32-bit iso) I see this:

```
dmn@Kayleigh:/var/lib/apt/periodic$ ls -l
total 0
-rw-r--r-- 1 root root 0 Jul 11 12:52 unattended-upgrades-stamp
-rw-r--r-- 1 root root 0 Jul 11 12:52 update-stamp
-rw-r--r-- 1 root root 0 Jun 24 09:21 update-success-stamp
-rw-r--r-- 1 root root 0 Jul 11 12:52 upgrade-stamp

```
Here when I started up, three files have been updated to the current date and time (Jul 11). On the desktop system in post #1, only one is updated*.

History.log on the laptop shows upgrades were done on 6/2, and 6/24 both user initiated using Synaptic. The latest 6/24 upgrade. timed at 9:22 in history.log, matches the update-success-stamp. In contrast, my desktop Xubuntu 16.04 did not update this time stamp when upgrading with Synaptic. 

[U]Still, there does not appear to be any automatic checking for updates on my laptop either. Otherwise, update-success-stamp should be updated.
[/U]
 
Continuing: 

Question: Is it the checking not being done, OR the notification not being done? Or both? Running apt-get upgrade should inform on that:

```
dmn@Kayleigh:~$ sudo apt-get upgrade
[sudo] password for dmn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-15 linux-headers-4.4.0-15-generic linux-headers-4.4.0-16
  linux-headers-4.4.0-16-generic linux-headers-4.4.0-17
  linux-headers-4.4.0-17-generic linux-image-4.4.0-15-generic
  linux-image-4.4.0-16-generic linux-image-4.4.0-17-generic
  linux-image-extra-4.4.0-15-generic linux-image-extra-4.4.0-16-generic
  linux-image-extra-4.4.0-17-generic
Use 'sudo apt autoremove' to remove them.
[COLOR="#FF0000"]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/COLOR]


```
Note the bottom line: System "knows" of no upgrades to do, hence no notifications would appear.

Continuing. 

Run in terminal apt-get update (but not apt-get upgrade) All repositories are noted as accessible.  

aftermath:

```
dmn@Kayleigh:/var/lib/apt/periodic$ ls -l
total 0
-rw-r--r-- 1 root root 0 Jul 11 12:52 unattended-upgrades-stamp
-rw-r--r-- 1 root root 0 Jul 11 12:52 update-stamp
-rw-r--r-- 1 root root 0 Jul 11 13:18 update-success-stamp
-rw-r--r-- 1 root root 0 Jul 11 12:52 upgrade-stamp

```
_update-success stamp changed, showing apt-get update was just run_.

Now to wait a while and see if I get notified of available updates.

Footnotes:

* this is possibly because the laptop is set to "automatically download and install" security updates - so these may be for unattended upgrades**.

Day 2 (Jul 13) conclusions:

The manual update of Jul 11 triggered a substantial unattended upgrade, automatically and invisibly installed at startup on Jul 12, and a 2nd large upgrade (some 200 mB) for which there was a notification on Jul 13. So the problem is the failure to automatically check, not the failure to notify.* There is an upgrade to Software Updater in the last bunch of upgrades. Next, to observe and see if it might have a fix.

On the other hand, just now, the Software Updater in Ubuntu MATE 16.04 appeared automatically, no manual updates had been run, so it appears to be in working order.

**update 22 Nov 2016** - reinvestigation of this causes me to change my mind. the notifications seem to be failing as well. More in the next post.

**correct - this is the default setting for 16.04 (verified by checking settings in the live usb).

---

### Post by Dennis N on 2016-11-22
Conclusions of a reinvestigation in Nov 2016. Previous posts were made on [another thread]("https://ubuntuforums.org/showthread.php?t=2339387") as responses, continued from [this post]("https://ubuntuforums.org/showthread.php?t=2339387&p=13572942#post13572942")

4 upgradeable packages have somehow been known to the system for 4 days, yet no notification from the updater.

```
dmn@Kayleigh:~$ apt list --upgradeable
Listing... Done
libprocps4/xenial-updates 2:3.3.10-4ubuntu2.2 i386 [upgradable from: 2:3.3.10-4ubuntu2]
procps/xenial-updates 2:3.3.10-4ubuntu2.2 i386 [upgradable from: 2:3.3.10-4ubuntu2]
xserver-common/xenial-updates 2:1.18.4-0ubuntu0.2 all [upgradable from: 2:1.18.4-0ubuntu0.1]
xserver-xorg-core/xenial-updates 2:1.18.4-0ubuntu0.2 i386 [upgradable from: 2:1.18.4-0ubuntu0.1]

```
Being available for upgrade, there should be a notification but there is none.

Using unattended-upgrades can install nothing unless there are identified upgrades it can install automatically, which are any security updates (none in the above list). There are at least 2 security updates right now in the xenial-security repository, as they have already been upgraded on my linux mint 18 xfce system from that repository. It appears no update check is being done by Xubuntu to find them, or they would show up  as upgradeable (above). Once identified, unattended-upgrades should install them if they are there.

_The Conclusions_
So there are two faults with the system: 
1) updates are not being done, even though set to "check for updates daily". 
2) notifications are not being given, even though upgradeable packages are known to apt.

At this point, a manual update should update the list of upgradeable packages, and unattended upgrades is supposed to install the security updates automatically the next time it runs (on startup, but only once a day). I noted this has happened before in post #6 above.

Ran manual update:

New list of upgradeable packages:

```
dmn@Kayleigh:~$ apt list --upgradeable
Listing... Done
firefox/xenial-updates,xenial-security 50.0+build2-0ubuntu0.16.04.2 i386 [upgradable from: 49.0.2+build2-0ubuntu0.16.04.2]
firefox-locale-en/xenial-updates,xenial-security 50.0+build2-0ubuntu0.16.04.2 i386 [upgradable from: 49.0.2+build2-0ubuntu0.16.04.2]
imagemagick/xenial-updates,xenial-security 8:6.8.9.9-7ubuntu5.2 i386 [upgradable from: 8:6.8.9.9-7ubuntu5.1]
imagemagick-6.q16/xenial-updates,xenial-security 8:6.8.9.9-7ubuntu5.2 i386 [upgradable from: 8:6.8.9.9-7ubuntu5.1]
imagemagick-common/xenial-updates,xenial-security 8:6.8.9.9-7ubuntu5.2 all [upgradable from: 8:6.8.9.9-7ubuntu5.1]
libmagickcore-6.q16-2/xenial-updates,xenial-security 8:6.8.9.9-7ubuntu5.2 i386 [upgradable from: 8:6.8.9.9-7ubuntu5.1]
libmagickcore-6.q16-2-extra/xenial-updates,xenial-security 8:6.8.9.9-7ubuntu5.2 i386 [upgradable from: 8:6.8.9.9-7ubuntu5.1]
libmagickwand-6.q16-2/xenial-updates,xenial-security 8:6.8.9.9-7ubuntu5.2 i386 [upgradable from: 8:6.8.9.9-7ubuntu5.1]
libprocps4/xenial-updates 2:3.3.10-4ubuntu2.2 i386 [upgradable from: 2:3.3.10-4ubuntu2]
libpulse-mainloop-glib0/xenial-updates 1:8.0-0ubuntu3.1 i386 [upgradable from: 1:8.0-0ubuntu3]
libpulse0/xenial-updates 1:8.0-0ubuntu3.1 i386 [upgradable from: 1:8.0-0ubuntu3]
libpulsedsp/xenial-updates 1:8.0-0ubuntu3.1 i386 [upgradable from: 1:8.0-0ubuntu3]
procps/xenial-updates 2:3.3.10-4ubuntu2.2 i386 [upgradable from: 2:3.3.10-4ubuntu2]
pulseaudio/xenial-updates 1:8.0-0ubuntu3.1 i386 [upgradable from: 1:8.0-0ubuntu3]
pulseaudio-module-x11/xenial-updates 1:8.0-0ubuntu3.1 i386 [upgradable from: 1:8.0-0ubuntu3]
pulseaudio-utils/xenial-updates 1:8.0-0ubuntu3.1 i386 [upgradable from: 1:8.0-0ubuntu3]
tar/xenial-updates,xenial-security 1.28-2.1ubuntu0.1 i386 [upgradable from: 1.28-2.1]
xserver-common/xenial-updates 2:1.18.4-0ubuntu0.2 all [upgradable from: 2:1.18.4-0ubuntu0.1]
xserver-xorg-core/xenial-updates 2:1.18.4-0ubuntu0.2 i386 [upgradable from: 2:1.18.4-0ubuntu0.1]
```

Following this within a minute or so, Software & Updates launched to the panel notifying me of the upgrades. So this now suggests the notification is functional now, but not in all cases apparently - why was there no notification of the original four shown in the first display before now? 

Time stamps before manual update:

```
dmn@Kayleigh:~$ ls -l /var/lib/apt/periodic
total 0
-rw-r--r-- 1 root root 0 Nov 22 05:27 unattended-upgrades-stamp
-rw-r--r-- 1 root root 0 Nov 22 05:27 update-stamp
-rw-r--r-- 1 root root 0 Nov 18 09:36 update-success-stamp
-rw-r--r-- 1 root root 0 Nov 22 05:27 upgrade-stamp
```

After manual update:

```
dmn@Kayleigh:~$ ls -l /var/lib/apt/periodic
total 0
-rw-r--r-- 1 root root 0 Nov 22 05:27 unattended-upgrades-stamp
-rw-r--r-- 1 root root 0 Nov 22 05:27 update-stamp
[COLOR="#FF0000"]**-rw-r--r-- 1 root root 0 Nov 22 07:46 update-success-stamp**[/COLOR]
-rw-r--r-- 1 root root 0 Nov 22 05:27 upgrade-stamp
 
```

Note: Nov 18 update-success stamp was not the result of a manual upgrade. How did it hapen? Whatever, NO notifications came from that. At this point, I have still not run an upgrade for these and won't at this point - I'm waiting to see for sure that the unattended upgrades will install the security updates automatically on next run. The Software Updater notification should come back then for the rest of the updates.

---

### Post by ian-weisser on 2016-11-22
Have you checked the logs in /var/log/unattended-upgrades?
Is your cron.daily running without error?

Most of the unattended-upgrade problems that we see here in the forums are caused by an underlying apt problem (out-of-space, conflict, etc).
Rarer u-u problems are caused by conflicting or unexpected user changes to settings in /etc/apt/apt-conf.d/
So far, I haven't seen any problems that are actually caused by the apt or u-u code itself.

If your apt is fine and your settings are fine, then trace the progression of automatic daily apt updates.
Place some logging lines so you know what runs and what doesn't. Make sure the relevant scripts are there, have the right permissions, and are uncorrupted.
Starts in /etc/cron.daily/apt-compat

Handy for troubleshooting and testing: You can run apt and update-notifier and unattended-upgrades as much as you like in one day. It won't break anything.

---

### Post by Dennis N on 2016-11-23
As expected, after the manual update described above in post #7 above, unattended-upgrades today ran in the background within a few seconds of startup, answering my question as to whether these upgrades would be done without presenting them to the user. This is a direct consequence of manually running apt-get update the previous day to find them. 

unattended-upgrades log for this session:
```

2016-11-23 06:06:15,030 INFO Initial blacklisted packages: 
2016-11-23 06:06:15,037 INFO Initial whitelisted packages: 
2016-11-23 06:06:15,038 INFO Starting unattended upgrades script
2016-11-23 06:06:15,038 INFO Allowed origins are: ['o=Ubuntu,a=xenial', 'o=Ubuntu,a=xenial-security']
2016-11-23 06:06:59,583 INFO Packages that will be upgraded: firefox firefox-locale-en imagemagick imagemagick-6.q16 imagemagick-common libmagickcore-6.q16-2 libmagickcore-6.q16-2-extra libmagickwand-6.q16-2 tar
2016-11-23 06:06:59,584 INFO Writing dpkg log to '/var/log/unattended-upgrades/unattended-upgrades-dpkg.log'
2016-11-23 06:07:33,987 INFO All upgrades installed

```

It seems that the check for updates is **not** being done automatically - my setting is to check for updates daily. Here is my 20auto-updates to confirm this:

```
dmn@Kayleigh:/etc/apt/apt.conf.d$ cat 20auto-upgrades 
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Unattended-Upgrade "1";

```
These by the way, are the defaults on the Xubuntu 16.04 system as installed. So an extra setting does not needs to be enabled to use unattended upgrades.

A few minutes thereafter, again as I expected, the Software Updater launched automatically, to notify me of the other updates. These I installed using the software updater. 

_Simplified Sequence of Automatic Events:_
1) Update Check
2) Run Unattended Upgrades > If there are security updates from the update check, install them.
3) If there is other software to install, and the notification frequency set for "other" updates allows, launch software updater notification.

_Here is what needs answering: Why is the daily automatic checking for updates at startup not being done and how to fix it?_ (Also, without the automatic check working, unattended upgrades does nothing and exits.) Many users report having the same problem with Xubuntu 16.04 and Ubuntu MATE 16.04. I suspect it is wide spread. [One recent post]("https://ubuntuforums.org/showthread.php?t=2343944&p=13572969#post13572969") reports that it exists in 16.10 as well.

I searched briefly and located some other reports of this problem. I include them here for reference:

> [https://ubuntuforums.org/showthread.php?t=2325426](https://ubuntuforums.org/showthread.php?t=2325426)
where zzHanks reports: "After I did a clean install of 16.04, I'm not sure if my system is checking for updates automatically."

[https://ubuntuforums.org/showthread.php?t=2335167](https://ubuntuforums.org/showthread.php?t=2335167)
where Kris_M reports: "I seem to recall from 14.04.1 that every time an update was available, a pop-up would appear on the screen. In 16.04.1 it seems that I have to remember to open Ubuntu Software, check if there are updates, and run them."

[https://ubuntuforums.org/showthread.php?t=2339387](https://ubuntuforums.org/showthread.php?t=2339387)
where Quarkrad reports: "However, I have noticed that I longer get any automatic prompts for a download. The Software & Updates gui is set to Automatically check for updates: Daily and When there are security updates: Display immediately. I have to manually launch the gui to see if there are any downloads"; Dennis N reports: "I do believe there is something wrong with the update checking on 16.04. I have the same problem on 3 different computers and Xubuntu 16.04."

[https://ubuntuforums.org/showthread.php?t=2343944](https://ubuntuforums.org/showthread.php?t=2343944)	
where 1fallen reports "It is on my machine (Affected)..And also on Yackkety Mate (16.10)"; Quarkrad reports "I do have a thread Software Update Crash on my issue but so far I haven't solved it - been installing ubuntu since 8.04 using the same (basic/default) settings, this is the first time I've come across this." Quarkrad also reports "Also happening on other friends laptops/Desktops I look after."

[https://ubuntuforums.org/showthread.php?t=2344523](https://ubuntuforums.org/showthread.php?t=2344523)
chaaderf reported: "I installed Xubuntu 16.04 in October, and I've set the Software & Updates to update the system...But this has clearly not worked for me more than once during this time."


---

### Post by ian-weisser on 2016-11-23
Don't confuse a not-checking-for-updates problem with a updates-not-getting-installed problem or a not-getting-notified problem or a Software-Upgrader-crashing problems. Those are all *different problems* and each needs to be investigated and reported separately.

Most of this you already know:
But here it is all in one place, step by step for you to figure out where the problem is.

1) Daily automatic apt updates are triggered by a cron job. /etc/cron/daily/apt-compt .
The script picks a random time during the day to run another script: /usr/lib/apt/apt.systemd.daily
**Troubleshooting:** Check /var/log/syslog and /var/log/syslog.1 for failed cron.daily jobs.
 
2) /usr/lib/apt/apt.system.daily does most of the work, including checking for updates (line 401) .
**Troubleshooting:** Check /var/lib/apt/periodic for an update-stamp.
**Troubleshooting:** Check 'systemctl --list-timers' to see when the daily apt update will run (or should have run).

**Common problem:** Remember that systemd picks a random time during the day - if the system happens to be suspended at that time, the job will run some minutes after resuming. If the random time is late, and your system is already suspended for the night...then the job will run next morning and you will have seemingly missed a day. If one day is randomly late, the next day is randomly early, and the system suspended in between, the 'daily' updates may well be just a few minutes apart.

3) The same script /usr/lib/apt/apt.system.daily runs unattended-upgrade (line 440) to install available upgrades.
**Troubleshooting:** Check /var/lib/apt/periodic for an upgrade-stamp.
**Troubleshooting:** Check /etc/apt/apt.conf.d/20auto-upgrades that unattended-upgrade is enabled ('1').
**Troubleshooting:** Check /var/log/unattended-upgrades/unattended-upgrades.log for apt or dpkg errors that must be fixed manually

**Common Problem:** Unattended-upgrade will fail on any apt or dpkg error (like a version conflict or out-of-space condition) during the process. The errors will be in the unattended-upgrades log. These complex problems must be resolved by the admin (you) before u-u will work.
[B]
Common Problem: [/B]Unattended-upgrade will only install upgrades from the <release>-security repository by default. Some users expect more repositories, like <release>-upgrades or <release>-backports, and are surprised when they see lots us available but uninstalled upgrades. This is easy to change in /etc/apt/apt.conf.d/50unattended-upgrades.

**Common Problem:** Apt and unattended-upgrade does not use *phased updates*, but the GUI application Software Updater does use *phased updates*, so there is often a difference in the list of packages. This difference is both expected and harmless and should be ignored. [Phased Updates]("https://wiki.ubuntu.com/PhasedUpdates") is a system to protect the entire Ubuntu community from a catastrophic upgrade by rolling out the upgrade in *phases*, so the problem can be identified early and reverted. Apt and u-u do not have a setting to use phased updates. S-U does not have a setting to ignore phased updates.

I don't use Update Notifier or Software Updater at all, and long ago uninstalled them, so cannot help troubleshoot those.

---

### Post by Dennis N on 2016-11-23
I do appreciate you taking the time to enumerate these suggestions.

All but one of the troubleshooting suggestions regarding logs and config files has been done and posted about before. See post #1, #6, post #7 and the link to previous posts at the top of post #7. There I have posted unattended-upgrades logs, and there are no errors indicated. I had thought of phased updates, but since the problem of no automatic checks has persisted for periods of a month or more between manual update checks, that should not be a problem. I still have no instance of an automatic check and notify being done since installation. And I have waited long periods of time to see.

The main indication confirming lack of automatic updating is in post #1, where "update-success-stamp" remains unchanged unless a manual update is done. Only then are the sources ever updated.

The three affected computers usually have an uptime of several hours, so the time delay should not matter.

I would note that if no updates are found, then no notifications are done either, so failure to notify may reflect the real problem - lack of automatic checking.

The one suggestion I had not seen was "Check 'systemctl --list-timers' to see when the daily apt update will run". I find this does not work (even with sudo).

```
dmn@Sydney:~$ systemctl --list-timers
systemctl: unrecognized option '--list-timers'

```

I do not plan to investigate this further. I am a mathematics teacher, not familar with the scripting language used, so cannot troubleshoot the scripts.

---

### Post by isoaglib on 2017-04-07
Hello,
I use the Kubuntu version of Ubuntu Xenial (16.04). Both the Package Update with the GUI, and the unattended-upgrade system did never update the apt package list on their own.
My notebook is NOT continually running, and I switch the notebook OFF (i.e. do not use suspend). Thus my notebook is performing a cold boot each day I use it.

Since installation of this Ubuntu version I had always to perform a "sudo apt-get update" in a shell, to perform a manual update of the package list.
As soon as I performed this manual update, the package update GUI ("discover", "muon" ...) indicated availability of updates.
Also the unattended-update system did not update any packages (I tried many configurations).


I detected after a long search with Google the reason for not updating the package list:
The timer for running APT in the file /etc/systemd/system/timers.target.wants/apt-daily.timer uses a very bad setting for my system: "RandomizedDelaySec=12h"
This way, the random time for calling apt was nearly never in the usage time intervall of my system.

I solved this problem with the following settings in **/etc/systemd/system/timers.target.wants/apt-daily.timer**:

```

[Unit]
Description=Daily apt activities
DefaultDependencies=yes
**After=network.target**

[Timer]
#OnCalendar=*-*-* 6,18:00
#RandomizedDelaySec=12h
#AccuracySec=1h
#Persistent=true
[B]OnBootSec=5min
OnUnitActiveSec=1d[/B]

[Install]
WantedBy=timers.target

```

I suggest that the default configuration for a **Desktop GUI** system should not use a random delay of max 12 hours, as this matches only the need of **server installations**, which are running 24 hours.
Maybe the system could automatically detect the average runtime per session, so that the maximum delay could get restricted to this daily usage time.


I hope this information helps other users, who are wondering, why the automatic package update does not work.

Bye,
Achim

---

### Post by Dennis N on 2017-04-07
> I hope this information helps other users, who are wondering, why the automatic package update does not work.

OK, it's worth a try. 

1) mine is originally the same, except missing DefaultDependencies=yes.
2) added that missing line, commented out the 4 lines, and added the 3 bold entries.
3) will see what happens.

Thanks for posting!

---

### Post by isoaglib on 2017-04-07
> **Dennis N said:**
> OK, it's worth a try. 

1) mine is originally the same, except missing DefaultDependencies=yes.


Please add then also the line:
```
DefaultDependencies=yes
```

As long as I understand the possible reasons for the problem correct, the failing update of the package list can have two reasons:
[LIST]
[*]too late random time
[*]failing dependencies, when network is not ready to perform communication for "apt-get update"
[/LIST]

You can check the timer with the following call:

```
systemctl list-timers|grep apt
```

This way you can monitor when the update scripts get called.

---

### Post by Dennis N on 2017-04-07
Yes I already added it. Guess it was not clear - that's what I meant by "added that missing line". Thanks. So, at what time after start up should I expect the computer to check for updates now?

---

### Post by isoaglib on 2017-04-07
> **Dennis N said:**
> So, at what time after start up should I expect the computer to check for updates now?

```

OnBootSec=5min
OnUnitActiveSec=1d

```

Five minutes after boot (I hope these five minutes are enough to get always network up and running), and then every day.

With **systemctl list-timers|grep apt** you get the exact timing - open a shell like **konsole** or **xterm** and execute this line after boot. You should then be able to monitor the timing.

---

### Post by Dennis N on 2017-04-08
Thought you would like to know that on the next day after making the suggested changes, the software updater automatically launched to notify me of available updates after about 6 minutes uptime, having presumably checked for updates at 5 minutes as you predicted. This is the first time ever that it has automatically launched without manually checking for updates first. I am very pleased to see this working. Thanks very much for your help!

---

