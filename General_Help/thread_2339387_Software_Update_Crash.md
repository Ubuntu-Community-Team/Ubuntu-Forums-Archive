---
title: "Software Update Crash"
date: 2016-10-08
forum: General Help
---

### Post by Quarkrad on 2016-10-08
Running Mate 16.04.  Past few weeks I get the software updater appear in the bottom task bar - when I click on it, to launch on the Desktop, it disappears.  If I try and launch Software Updater via the menus nothing happens.  At the moment I'm launching the terminal and entering sudo apt-get update && sudo apt-get upgrade.  How can I get the auto updater gui to work as normal?  Thanks.

---

### Post by howefield on 2016-10-08
> **Quarkrad said:**
> when I click on it, to launch on the Desktop, it disappears.  If I try and launch Software Updater via the menus nothing happens.

Do you get any errors if you try to launch the update manager via the terminal ?

```
update-manager
```

> At the moment I'm launching the terminal and entering sudo apt-get update && sudo apt-get upgrade.

Which is presumably working ?

---

### Post by Quarkrad on 2016-10-15
That command certainly fixed it - thank you - I can now launch the gui and it shows me updates to download.  However, I have noticed that I longer get any automatic prompts for a download.  The Software & Updates gui is set to *Automatically check for updates: Daily *and *When there are security updates: Display immediately*.  I have to manually launch the gui to see if there are any downloads - today I have 111.0MB including 3 security updates.

---

### Post by RobGoss on 2016-10-15
Normally Ubuntu's updater will let you know updates are available by displaying a notice at the top **right hand** corner on your desktop but for some reason it does not always work. I use a dock like Cairo dock and I have a updater icon at the bottom of the dock it always displays system updates when available and it %100 reliable

---

### Post by Quarkrad on 2016-10-28
I'm still not getting an automatic launch of the software updater - currently I have 101mb of updates to install but the launcher has not launched.

---

### Post by Dennis N on 2016-10-28
> **Quarkrad said:**
> I'm still not getting an automatic launch of the software updater - currently I have 101mb of updates to install but the launcher has not launched.

I do believe there is something wrong with the update checking on 16.04. I have the same problem on 3 different computers and Xubuntu 16.04. Here is what I have in my log after looking at this over a period of time several months ago:

[I]After suspecting a problem with automatic updates, what I did was to refrain from manually updating my system until I saw a the software-updater launch to notify me that there were updates. I waited over a month and there was never a notification. I finally ran apt-get update and there were a load of updates found. I did not run apt-get upgrade at the time, just to see it I would finally be notified. The next day, the software-updater popped up to tell me updates were available.

My preliminary conclusion is that the checking is faulty, but the notification is working. 
[/I]
Since then, the only way to update those 3 OSes is to launch Software Updater manually to check for updates, or use apt or Synaptic Package Manager. There is a complex decision algorithm that is supposed to be followed with automatic updates, but something is not working right.

---

### Post by Quarkrad on 2016-11-07
Still not auto updating (giving me notification).  Is there something on Launchpad I can follow if this is a bug?

---

### Post by ian-weisser on 2016-11-07
A bug report is useful only if you have enough information for a Triager to reproduce the bug.

Have you re-installed update-notifier?
Have you checked that update-notifier works?
Have you looked in /var/crash for update-notifier crash files?
Have you looked in /var/log/syslog for clues? Remember to check yesterday's too - apt's daily update is usually triggered by cron.daily, which also rotates the logs.

---

### Post by oldrocker99 on 2016-11-07
I use Ubuntu MATE 16.04 and have seen bottom panel buttons disappear when clicked on; it's a pain, and there doesn't seem to be any mention on Google. I certainly can live with it. It is a small bug, IMHO.

---

### Post by Dennis N on 2016-11-10
For reference, here is some information relating to the machine of post #6 (and two others with the same problem) running Xubuntu 16.04

Here is some recent documentation of the updater activity:

_Nov 7:_

```
dmn@Sydney:~$ ls -l /var/lib/apt/periodic/
total 0
-rw-r--r-- 1 root root 0 Apr 26  2016 unattended-upgrades-stamp
-rw-r--r-- 1 root root 0 Nov  7 11:50 update-stamp
-rw-r--r-- 1 root root 0 Sep 25 08:11 update-success-stamp
-rw-r--r-- 1 root root 0 Apr 26  2016 upgrade-stamp

```
Sep 25 was the last refresh of the source lists that I ran, through Synaptic. At that time, there had been no prior notification that updates were available. After which I marked and applied available upgrades. On Nov 7 (above display), over one month later, no updates have been found since Sep 25 (update-success-stamp). And no notifications have been received.

_Nov 10:_

On Nov 10, a warning appeared on the panel (see attachment #1):

and another check shows that sources not updated for 46 days:
```
dmn@Sydney:~$ ls -l /var/lib/apt/periodic
total 0
-rw-r--r-- 1 root root 0 Apr 26  2016 unattended-upgrades-stamp
-rw-r--r-- 1 root root 0 Nov 10 09:35 update-stamp
-rw-r--r-- 1 root root 0 Sep 25 08:11 update-success-stamp
-rw-r--r-- 1 root root 0 Apr 26  2016 upgrade-stamp

```
I then ran apt-get update in the terminal, and update-success stamp shows that sources have been successfully updated:
```
dmn@Sydney:~$ ls -l /var/lib/apt/periodic
total 0
-rw-r--r-- 1 root root 0 Apr 26  2016 unattended-upgrades-stamp
-rw-r--r-- 1 root root 0 Nov 10 09:35 update-stamp
-rw-r--r-- 1 root root 0 Nov 10 12:07 update-success-stamp
-rw-r--r-- 1 root root 0 Apr 26  2016 upgrade-stamp

```
A couple of minutes later, Software Updater launched itself to the panel. Viewing the Software Updater window, it informs me that 340 mB of updates are available.

I then ran the upgrade from the Software Updater window. These successfully complete.

Finally, attachment #2 shows the update settings being used in Software & Updates. The daily checking is clearly not being done.

---

### Post by ian-weisser on 2016-11-10
The easy way: Try reinstalling the 'apt' package.

The troubleshooting way: Start with /etc/cron.daily/apt-compat . That's the daily script that begins the update process. Follow the rabbit down the hole....

---

### Post by Dennis N on 2016-11-16
**/etc/cron.daily/apt-compat** in turn runs **/usr/lib/apt/apt.systemd.daily** which is a much larger script. Possibly the problem is with one of these two scripts. Don't know the scripting language used, so I could not begin to troubleshoot.

---

### Post by ian-weisser on 2016-11-16
Check for clues in /var/log/apt, /var/log/unattended-upgrades, /var/crash, and /var/log/syslog

I see two possibilities; try to eliminate one:
1) apt is broken due to a setting, conflict, or needs to be reinstalled. Evidence of these will show up in the logs as apt starts and then fails.
2) One of the supporting applications or indicators is crashing due to a setting, conflict, or needs to be reinstalled. Evidence of these is indicators vanishing, applications failing to start or vanishing, and 'Internal Error' dialog boxes.

---

### Post by Dennis N on 2016-11-16
I will look into it. Whatever it is, it comes with the OS installation as it affects Xubuntu 16.04 on all 3 of our computers.

---

### Post by Dennis N on 2016-11-16
I can check out the first suggestion only:

In **/var/log/apt**, **history.log** only records apt's install and activity, not update activity. **term.log** is empty, and **term.log.1.gz** records terminal output with manual upgrade using apt (date coincides with history.log record); **term.log.2.gz** the last manual upgrade with apt before that and so on.

**/var/log/unattended-upgrades** last activity is with the original installation on June 9 (not correct - corrected below).

**/var/crash** is an empty directory

**journalctl** has more detail than syslog, so I used journalctl entries.

```
Nov 16 12:40:59 Zotac anacron[631]: Will run job `cron.daily' in 5 min.
Nov 16 12:45:50 Zotac anacron[631]: Job `cron.daily' started
Nov 16 12:45:50 Zotac anacron[1775]: Updated timestamp for job `cron.daily' to 2016-11-16
Nov 16 12:45:53 Zotac anacron[631]: Job `cron.daily' terminated

```
note: **syslog** only has the last entry.

This indicates the cron job ran and terminated (apparently successfully) in 3 seconds total. No entries in journalctl contain any mention of apt.

Suggestion #2 - no ideas how to investigate these ideas. No error messages or dialogs ever appear.

_correction on unattended-upgrades._ 

These were in effect from original installation date until July 7 (when the update settings were changed to the current ones) and it seems they were working back then according to the log:

```
2016-05-22 07:45:11,592 INFO Initial blacklisted packages: 
2016-05-22 07:45:11,593 INFO Initial whitelisted packages: 
2016-05-22 07:45:11,593 INFO Starting unattended upgrades script
2016-05-22 07:45:11,593 INFO Allowed origins are: ['o=Ubuntu,a=xenial-security']
2016-05-22 07:46:26,542 INFO Packages that will be upgraded: chromium-codecs-ffmpeg-extra firefox firefox-locale-en libarchive13 libexpat1 libksba8 oxideqt-codecs-extra thunderbird thunderbird-locale-en thunderbird-locale-en-us
2016-05-22 07:46:26,543 INFO Writing dpkg log to '/var/log/unattended-upgrades/unattended-upgrades-dpkg.log'
2016-05-22 07:46:43,967 INFO All upgrades installed

```

and history.log

```
Start-Date: 2016-05-22  07:46:27
Commandline: /usr/bin/unattended-upgrade
Upgrade: libksba8:amd64 (1.3.3-1, 1.3.3-1ubuntu0.16.04.1), libarchive13:amd64 (3.1.2-11build1, 3.1.2-11ubuntu0.16.04.1), libexpat1:amd64 (2.1.0-7, 2.1.0-7ubuntu0.16.04.1), thunderbird-locale-en-us:amd64 (1:38.7.2+build1-0ubuntu0.16.04.1, 1:38.8.0+build1-0ubuntu0.16.04.1), firefox-locale-en:amd64 (46.0+build5-0ubuntu0.16.04.2, 46.0.1+build1-0ubuntu0.16.04.2), chromium-codecs-ffmpeg-extra:amd64 (49.0.2623.108-0ubuntu1.1233, 50.0.2661.102-0ubuntu0.16.04.1.1237), oxideqt-codecs-extra:amd64 (1.14.7-0ubuntu1, 1.14.9-0ubuntu0.16.04.1), thunderbird:amd64 (1:38.7.2+build1-0ubuntu0.16.04.1, 1:38.8.0+build1-0ubuntu0.16.04.1), firefox:amd64 (46.0+build5-0ubuntu0.16.04.2, 46.0.1+build1-0ubuntu0.16.04.2), thunderbird-locale-en:amd64 (1:38.7.2+build1-0ubuntu0.16.04.1, 1:38.8.0+build1-0ubuntu0.16.04.1)
End-Date: 2016-05-22  07:46:41
```

So that option looks good. But, are these presented to the user for ok before installation? I would guess they aren't. Probably why I switched to the other option.

---

### Post by Dennis N on 2016-11-16
The 2nd computer with this same problem has just popped up the same "update information outdated" warning as displayed as a thumbnail in post #10.

Realizing now that "unattended upgrades" must have been the default setting when installed (I would not have chosen it), I wonder if the developers deliberately chose that option to use as default because it worked correctly and they knew there were problems with the other choices?

---

### Post by ian-weisser on 2016-11-16
> **Dennis N said:**
> Realizing now that "unattended upgrades" must have been the default setting when installed (I would not have chosen it), I wonder if the developers deliberately chose that option to use as default because it worked correctly and they knew there were problems with the other choices?

Uh, no.

First, your understanding of the unattended-upgrade default setting is mistaken.
The default setting for unattended-upgrades is to download package database updates only. Not to upgrade anything.
In 16.04 and later, a minor addition also runs autoremove...but still doesn't upgrade anything.

Second, you are erroneously assuming that Software Notifier and Software Updater shipped broken. For many millions of installed systems, they work just fine. Including my test systems.

Third, you seem to think that the Ubuntu devs would knowingly ship broken package management (or any other kind of) software. That seems quite doubtful.

---

### Post by Dennis N on 2016-11-17
> The default setting for unattended-upgrades is to download package database updates only. Not to upgrade anything.

OK, I have options for security updates to "Download Automatically" and "Download and Install Automatically". Which one of these corresponds to unattended-upgrades? I had assumed the second one would be it.
 > Third, you seem to think that the Ubuntu devs would knowingly ship broken package management (or any other kind of) software. That seems quite doubtful.
Just to clarify, I didn't say think, I said I wondered. To me, think means to hold an opinion or belief. To wonder is to just raise a question without knowing the answer either way. Software is sometimes released with unfixed bugs. I have several times filed bug reports, and the bugs are not fixed in time for the next release. So there's that.


Thanks and best regards.

---

### Post by Dennis N on 2016-11-17
> The default setting for unattended-upgrades is to download package database updates only. Not to upgrade anything.

OK, I have options for security updates to "Download Automatically" and "Download and Install Automatically". Which one of these corresponds to unattended-upgrades? I had assumed the second one would be it.
 > Third, you seem to think that the Ubuntu devs would knowingly ship broken package management (or any other kind of) software. That seems quite doubtful.
Just to clarify, I didn't say think, I said I wondered. To me, think means to hold an opinion or belief. To wonder is to just raise a question without knowing the answer either way. Software is sometimes released with unfixed bugs. I have several times filed bug reports, and the bugs are not fixed in time for the next release. So there's that.

Thanks and best regards.

Note: Duplicate Post because the first one did not appear for 20-30 min, at which time I reposted.

---

### Post by ian-weisser on 2016-11-17
> **Dennis N said:**
> OK, I have options for security updates to "Download Automatically" and "Download and Install Automatically". Which one of these corresponds to unattended-upgrades? I had assumed the second one would be it.

Unattended upgrades, Software Notifier, Software Updater, and software-properties-gtk are not independent applications. Look at them as optional add-on modules to apt. They *share* settings with apt (in apt.conf.d/), and they rely upon aptdaemon to do the actual package work.
 
The "Download Automatically" and "Download and Install Automatically" translate to settings in /etc/apt/apt.conf.d/, owned by apt and governing apt behavior. Unattended upgrades runs an apt update/upgrade/autoremove headlessly (with a few other protections) whenever it's triggered by the cron job...and the cron settings permit.

What is the content of your /etc/apt/apt.conf.d/20auto-upgrades ?

---

### Post by Dennis N on 2016-11-17
Thanks for answering. 

I have read about "automatic updates" in the Ubuntu Documentation* to learn more. I gathered we need automatic-upgrades pkg. operational to automatically update the package lists daily (see ** at bottom). I checked the settings in the relevant files mentioned in the Documentation (I assume these are set by settings made in Software & Update's Update Tab?) including the file you asked about:  

```
dmn@Sydney:/etc/apt/apt.conf.d$ cat 10periodic 
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
APT::Periodic::Unattended-Upgrade "0";
```

```
dmn@Sydney:/etc/apt/apt.conf.d$ cat 20auto-upgrades 
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
APT::Periodic::Unattended-Upgrade "0";

```


```
dmn@Sydney:/etc/apt/apt.conf.d$ cat 50unattended-upgrades 
// Automatically upgrade packages from these (origin:archive) pairs
Unattended-Upgrade::Allowed-Origins {
	"${distro_id}:${distro_codename}-security";
//	"${distro_id}:${distro_codename}-updates";
//	"${distro_id}:${distro_codename}-proposed";
//	"${distro_id}:${distro_codename}-backports";
};

```
  
Results are logged in /var/log/unattended-upgrades. 

[U]A problem seems apparent from this log file, which shows it only ran 4 times: Apr 23-26 then the entries stop. These are the four days after the OS installation (Apr 22). 
[/U]
Last Log Entry:

```
2016-04-26 11:36:25,070 INFO Initial blacklisted packages: 
2016-04-26 11:36:25,075 INFO Initial whitelisted packages: 
2016-04-26 11:36:25,075 INFO Starting unattended upgrades script
2016-04-26 11:36:25,075 INFO Allowed origins are: ['o=Ubuntu,a=xenial-security']
2016-04-26 11:36:27,169 INFO No packages found that can be upgraded unattended and no pending auto-removals
```

And Apr 26 corresponds to the time stamp for unattended-upgrades-stamp in /var/lib/apt/periodic:

```
dmn@Sydney:/var/lib/apt/periodic$ ls -l
total 0
-rw-r--r-- 1 root root 0 Apr 26  2016 unattended-upgrades-stamp
-rw-r--r-- 1 root root 0 Nov 17 08:01 update-stamp
-rw-r--r-- 1 root root 0 Nov 10 12:07 update-success-stamp
-rw-r--r-- 1 root root 0 Apr 26  2016 upgrade-stamp
```

So it has not been running since then.

*[https://help.ubuntu.com/lts/serverguide/automatic-updates.html](https://help.ubuntu.com/lts/serverguide/automatic-updates.html)
** later found this is not correct. you don't need unattended upgrades enabled to get automatic checks for updates.

---

### Post by ian-weisser on 2016-11-17
Correct. It hasn't been running since then...because you told your system to operate that way:

> dmn@Sydney:/etc/apt/apt.conf.d$ cat 20auto-upgrades 
APT:: Periodic:: Update-Package-Lists "1";              // Run apt update daily
APT:: Periodic:: Download-Upgradeable-Packages "0";             // Do not download new packages ever
APT:: Periodic:: AutocleanInterval "0";               // Do not clean out the package cache ever
APT:: Periodic:: Unattended-Upgrade "0";             // Do not run unattended-upgrades ever

---

### Post by Dennis N on 2016-11-17
Hmmm...I've never looked at those files in /etc/apt/apt.conf.d before this morning. I suppose playing with the Updates Settings in Software & Updates must have turned this off. 

Anyway, I have located the original (as installed) file in another Xubuntu 16.04 for 20auto-upgrades and using that:

```
dmn@Sydney /etc/apt/apt.conf.d $ cat 20auto-upgrades
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Unattended-Upgrade "1";

```

Now to begin a new test period to see if this really solves the problem of not checking for updates.

---

### Post by Dennis N on 2016-11-18
OK, good news is that unattended-upgrades ran the next day and made a log entry!

```
2016-11-18 08:03:22,604 INFO Initial blacklisted packages: 
2016-11-18 08:03:22,604 INFO Initial whitelisted packages: 
2016-11-18 08:03:22,604 INFO Starting unattended upgrades script
2016-11-18 08:03:22,604 INFO Allowed origins are: ['o=Ubuntu,a=xenial-security']
2016-11-18 08:03:24,731 INFO No packages found that can be upgraded unattended and no pending auto-removals

```

apt-get -s upgrade shows 7 packages elgible for upgrade (I did not run apt-get update first, so this is means the update must have run automatically) These are all from 'xenial-updates' so they are not security updates. I assume from the INFO message in the output above that security updates would upgrade unattended? Does that mean without seeing them first? Not exactly what I wanted.

Waiting for notification of these 'regular' updates. Maybe tomorrow?

_Update_: one hr. after writing this, the aforementioned "update information is outdated" message popped up again on the panel. Didn't the above just update my lists?

---

### Post by Dennis N on 2016-11-21
Currently watching this package:

```
dmn@Kayleigh:~$ apt-cache policy imagemagick
imagemagick:
  Installed: 8:6.8.9.9-7ubuntu5.1
  Candidate: 8:6.8.9.9-7ubuntu5.1
  Version table:
 *** 8:6.8.9.9-7ubuntu5.1 500
        500 http://mirrors.us.kernel.org/ubuntu xenial-updates/main i386 Packages
```

There is a security update in the xenial-security repository to 8:6.8.9.9-7ubuntu5.2. When unattended-upgrades next runs, what we are looking for is if this will be automatically installed or not. Now using the original, default settings for Xubuntu 16.04 for /etc/apt/apt.conf.d/20auto-upgrades which are:

```
dmn@Kayleigh:~$ cat /etc/apt/apt.conf.d/20auto-upgrades 
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Unattended-Upgrade "1";

```

Continued in my own thread: [https://ubuntuforums.org/showthread.php?t=2330407](https://ubuntuforums.org/showthread.php?t=2330407) at post #7.

---

### Post by Quarkrad on 2016-11-30
Software Update (notifier) has appeared twice in my bottom panel (I'm running U Mate) - this was my initial problem, it was never appearing.  Twice now I've clicked on it to launch and it just disappears/crashes.  I have had a look at the command to run it and tried to launch it via the terminal.  According to Edit Menu and looking at the Properties for Software Updater (that in the gui appears under Administration) the run command is** /usr/bin/update-manager**.  When I enter this command in the terminal I get

```
dad@dadubuntu:~$ /usr/bin/update-manager
/usr/bin/update-manager:28: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk
/usr/lib/python3/dist-packages/UpdateManager/UnitySupport.py:29: PyGIWarning: Dbusmenu was imported without specifying a version first. Use gi.require_version('Dbusmenu', '0.4') before import to ensure that the right version gets loaded.
  from gi.repository import Dbusmenu, Unity
/usr/lib/python3/dist-packages/UpdateManager/UnitySupport.py:29: PyGIWarning: Unity was imported without specifying a version first. Use gi.require_version('Unity', '7.0') before import to ensure that the right version gets loaded.
  from gi.repository import Dbusmenu, Unity

```
note.  Software updater does not run if I try and launch it via the gui.

---

### Post by Quarkrad on 2016-12-03
I recently installed Mate 16.04 on a neighbours machine and they are very pleased - they are not particularly computer literate so the simple interface and working in perfect. Last night I was helping them with a Calc spreadsheet and the software update notifier appeared in the lower panel.  I stopped and took the opportunity to explain that when this happens they need to click on it and follow the instructions in the window - i.e. update their pc.  Embarrassingly, when I clicked on it, to launch it, it just disappeared - this happens on my machine as well.  I am happy to use the terminal to update but I do not want to go through this with family/friends.  The pop up update notifier window has worked every time since I came on-board with 8.04 - just seems broken on 16.04.

---

### Post by bedfojo on 2016-12-07
I have similar problems. I reported a bug here: [https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1648237](https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1648237)

---

### Post by ian-weisser on 2016-12-07
How can I reproduce your bug on my testing system to Triage it?
So far, my testing system is working properly. What do I need to change?

---

### Post by bedfojo on 2017-01-21
> **ian-weisser said:**
> How can I reproduce your bug on my testing system to Triage it?
So far, my testing system is working properly. What do I need to change?

I'm not sure what else to suggest. My system is a fresh install of Ubuntu-MATE 16.10. I have set it up as explained in the bug report [https://bugs.launchpad.net/ubuntu-mate/+bug/1648237](https://bugs.launchpad.net/ubuntu-mate/+bug/1648237).

Are there any log files or other info that I could provide? Any debug scripts I could run?

---

