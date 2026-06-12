---
title: "How do I permanently disable autoremove of old kernels?"
date: 2018-07-07
forum: General Help
---

### Post by col48 on 2018-07-07
In the last month or so, Software Update has included removing old kernels alongside its software updates.  I don't want this to happen - ever. I know I can untick it each time, but it is too easy to forget to do so.

After a bad experience where, for a while, I needed to go back several kernels to find a fully functional one I never want to have old kernels removed except when I do it manually using synaptic.

So how can I tell Software Update to leave old kernels alone unless I positively select them for removal?

---

### Post by Bashing-om on 2018-07-07
col48; Hello -

Management of old kernels is a function of unattended-upgrades. There are a number of ways to have the system NOT remove old kernels.
Many of us who completely manage packages manually purge unattended-upgrades - that maybe rather drastic for your use case, A simpler more direct means to disable the removal feature is to edit the autoremove setting in /etc/apt/apt.conf.d/50unattended-upgrades from 'true' to 'false' and uncomment the line if applicable .

It is well worth the time and effort to learn what all the package unattended-upgrades controls.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by monkeybrain20122 on 2018-07-07
Usually you only need go back one kernel, if you need to go back more than one it just mean the previous one wasn't working either and you should have removed it before the current one, so when you do get the current one the working one wouldn't be removed.

---

### Post by col48 on 2018-07-07
@Bashing-om: Thanks for your response.... your simpler option is just what I am looking for, but the file does not seem to have such a line at all.

This is what my 50unattended-upgrades file looks like:

```
// Automatically upgrade packages from these (origin:archive) pairs
Unattended-Upgrade::Allowed-Origins {
	"${distro_id}:${distro_codename}";
	"${distro_id}:${distro_codename}-security";
	// Extended Security Maintenance; doesn't necessarily exist for
	// every release and this system may not have it installed, but if
	// available, the policy for updates is such that unattended-upgrades
	// should also install from here by default.
	"${distro_id}ESM:${distro_codename}";
//	"${distro_id}:${distro_codename}-updates";
//	"${distro_id}:${distro_codename}-proposed";
//	"${distro_id}:${distro_codename}-backports";
};

// List of packages to not update (regexp are supported)
Unattended-Upgrade::Package-Blacklist {
//	"vim";
//	"libc6";
//	"libc6-dev";
//	"libc6-i686";
};

// This option allows you to control if on a unclean dpkg exit
// unattended-upgrades will automatically run 
//   dpkg --force-confold --configure -a
// The default is true, to ensure updates keep getting installed
//Unattended-Upgrade::AutoFixInterruptedDpkg "false";

// Split the upgrade into the smallest possible chunks so that
// they can be interrupted with SIGUSR1. This makes the upgrade
// a bit slower but it has the benefit that shutdown while a upgrade
// is running is possible (with a small delay)
//Unattended-Upgrade::MinimalSteps "true";

// Install all unattended-upgrades when the machine is shuting down
// instead of doing it in the background while the machine is running
// This will (obviously) make shutdown slower
//Unattended-Upgrade::InstallOnShutdown "true";

// Send email to this address for problems or packages upgrades
// If empty or unset then no email is sent, make sure that you
// have a working mail setup on your system. A package that provides
// 'mailx' must be installed. E.g. "user@example.com"
//Unattended-Upgrade::Mail "root";

// Set this value to "true" to get emails only on errors. Default
// is to always send a mail if Unattended-Upgrade::Mail is set
//Unattended-Upgrade::MailOnlyOnError "true";

// Do automatic removal of new unused dependencies after the upgrade
// (equivalent to apt-get autoremove)
//Unattended-Upgrade::Remove-Unused-Dependencies "false";

// Automatically reboot *WITHOUT CONFIRMATION*
//  if the file /var/run/reboot-required is found after the upgrade 
//Unattended-Upgrade::Automatic-Reboot "false";

// If automatic reboot is enabled and needed, reboot at the specific
// time instead of immediately
//  Default: "now"
//Unattended-Upgrade::Automatic-Reboot-Time "02:00";

// Use apt bandwidth limit feature, this example limits the download
// speed to 70kb/sec
//Acquire::http::Dl-Limit "70";

```

Maybe I need to ADD a line???
This file claims to have been last modified in May 2017, but the unwanted behaviour only started a month or two ago.  Odd.

---

### Post by Bashing-om on 2018-07-07
col48; Well ! not -

Will not hurt to give a try to adding to the file . - make a bckup 1st just in case.

what release are you running ?
my 18.10 file:
```

sysop@x1810:~$ cat  /etc/apt/apt.conf.d/50unattended-upgrades
// Automatically upgrade packages from these (origin:archive) pairs
//
// Note that in Ubuntu security updates may pull in new dependencies
// from non-security sources (e.g. chromium). By allowing the release
// pocket these get automatically pulled in.
Unattended-Upgrade::Allowed-Origins {
        "${distro_id}:${distro_codename}";
	"${distro_id}:${distro_codename}-security";
	// Extended Security Maintenance; doesn't necessarily exist for
	// every release and this system may not have it installed, but if
	// available, the policy for updates is such that unattended-upgrades
	// should also install from here by default.
	"${distro_id}ESM:${distro_codename}";
//	"${distro_id}:${distro_codename}-updates";
//	"${distro_id}:${distro_codename}-proposed";
//	"${distro_id}:${distro_codename}-backports";
};

// List of packages to not update (regexp are supported)
Unattended-Upgrade::Package-Blacklist {
//	"vim";
//	"libc6";
//	"libc6-dev";
//	"libc6-i686";
};

// This option will controls whether the development release of Ubuntu will be
// upgraded automatically.
Unattended-Upgrade::DevRelease "false";

// This option allows you to control if on a unclean dpkg exit
// unattended-upgrades will automatically run 
//   dpkg --force-confold --configure -a
// The default is true, to ensure updates keep getting installed
//Unattended-Upgrade::AutoFixInterruptedDpkg "false";

// Split the upgrade into the smallest possible chunks so that
// they can be interrupted with SIGTERM. This makes the upgrade
// a bit slower but it has the benefit that shutdown while a upgrade
// is running is possible (with a small delay)
//Unattended-Upgrade::MinimalSteps "false";

// Install all unattended-upgrades when the machine is shutting down
// instead of doing it in the background while the machine is running
// This will (obviously) make shutdown slower
//Unattended-Upgrade::InstallOnShutdown "true";

// Send email to this address for problems or packages upgrades
// If empty or unset then no email is sent, make sure that you
// have a working mail setup on your system. A package that provides
// 'mailx' must be installed. E.g. "user@example.com"
//Unattended-Upgrade::Mail "root";

// Set this value to "true" to get emails only on errors. Default
// is to always send a mail if Unattended-Upgrade::Mail is set
//Unattended-Upgrade::MailOnlyOnError "true";

// Remove unused automatically installed kernel-related packages
// (kernel images, kernel headers and kernel version locked tools).
//Unattended-Upgrade::Remove-Unused-Kernel-Packages "false";

// Do automatic removal of new unused dependencies after the upgrade
// (equivalent to apt-get autoremove)
//Unattended-Upgrade::Remove-Unused-Dependencies "false";

// Automatically reboot *WITHOUT CONFIRMATION*
//  if the file /var/run/reboot-required is found after the upgrade 
//Unattended-Upgrade::Automatic-Reboot "false";

// If automatic reboot is enabled and needed, reboot at the specific
// time instead of immediately
//  Default: "now"
//Unattended-Upgrade::Automatic-Reboot-Time "02:00";

// Use apt bandwidth limit feature, this example limits the download
// speed to 70kb/sec
//Acquire::http::Dl-Limit "70";

// Enable logging to syslog. Default is False
// Unattended-Upgrade::SyslogEnable "false";

// Specify syslog facility. Default is daemon
// Unattended-Upgrade::SyslogFacility "daemon";

// Download and install upgrades only on AC power
// (i.e. skip or gracefully stop updates on battery)
// Unattended-Upgrade::OnlyOnACPower "true";

// Download and install upgrades only on non-metered connection
// (i.e. skip or gracefully stop updates on a metered connection)
// Unattended-Upgrade::Skip-Updates-On-Metered-Connections "true";
sysop@x1810:~$ 

```

Mind that I do manage packages personally .

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by col48 on 2018-07-07
Since I only wish to update software manually, would it be better to uninstall (=remove in synaptic) the unattended-upgrades package?
I would presumably still be prompted when updates become available.

I'm running 16.04 Xenial.

---

### Post by #&amp;thj^% on 2018-07-07
> **col48 said:**
> Since I only wish to update software manually, would it be better to uninstall (=remove in synaptic) the unattended-upgrades package?

I have since 16.04 and up. ;)
> **col48 said:**
> 
I would presumably still be prompted when updates become available.

Nope>>>No Prompts to upgrade.
You will now be responsible solely  to run sudo apt update && sudo apt upgrade yourself.
It might be easiest just to set never with Software Sources via the Screenshot I show

---

### Post by Bashing-om on 2018-07-07
col48; Hummm ..

> 
I would presumably still be prompted when updates become available.


Honestly - I have run development (testing) for so long where I run updates at least twice a day - I just do not recall how auto-updates work .

A thought is to try purging the unattended-upgrades package .. test and if not happy re-install it and re-configure .

[INDENT][INDENT]all a process in learning
[/INDENT][/INDENT]

---

### Post by col48 on 2018-07-07
@Bashing-om & 1fallen:

Thanks both.  I'll explore further in a couple of days.... Life gets in the way!!

I do want to be told about updates, but I don't want old kernels to be purged automatically.  They didn't until recently, so I wonder what changed?

---

### Post by Bashing-om on 2018-07-07
col48; well..

> 
They didn't until recently, so I wonder what changed?


I would hazard a guess that there were updates to the package manager ,,, and the scripts got overwrote .
If ya still have the install media on hand might be good to compare the config files .

[INDENT]inquiring minds want to know
[/INDENT]

---

### Post by #&amp;thj^% on 2018-07-07
> **col48 said:**
> but I don't want old kernels to be purged automatically.  They didn't until recently, so I wonder what changed?

Bashing-om is correct this has been a new feature added in 16.04.
Maybe this will help confuse you even more :) : [https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)
Now I don't mind using the terminal for maintence and removal of packages && kernels. In fact I prefer it. :p
My way of checking of what is  autoremovable: 
```
apt-mark showauto 'linux-image-.*'
```
And I run Manually installed kernels in testing so i also use:
```
apt-mark showmanual 'linux-image-.*'
```
And remove the ones I no longer want.

---

### Post by Cavsfan on 2018-07-07
I, like [COLOR=#000000]Bashing-om and [/COLOR][COLOR=#000000]1fallen, prefer to control all of my updates and immediately purge the [/COLOR]unattended-upgrades package.

Also I do all my updates via terminal.

These 2 files will boot into the most current kernel on your system: **/vmlinuz** and **/initrd.img** 
These 2 files will boot into the 2nd most current kernel on your system: **/vmlinuz.old** and **/initrd.img.old**.

There are no other kernel files and the latest installed kernel is the most current one, not the highest numbered one.

Just curious but, why would you want to keep more than 2 kernels?

---

### Post by col48 on 2018-07-10
Backed up the '50' file and added

```
// 2018-07-10 start
// This option will controls whether the development release of Ubuntu will be
// upgraded automatically.
Unattended-Upgrade::DevRelease "false";
// Remove unused automatically installed kernel-related packages
// (kernel images, kernel headers and kernel version locked tools).
Unattended-Upgrade::Remove-Unused-Kernel-Packages "false";
// 2018-07-10 end

```

So we will see what happens.

@Cavsfan:
A while ago the desktop was not communicating with my printer properly after I took the latest kernel. If I chose to boot into one of the previous kernels I still had there was no problem.  There were 3 or 4 releases in fairly quick succession before the problem went away.  I want to be sure I always have a fully working kernel - which there would be a risk of unattended-upgrades killing if I missed unticking the box in the stress of updating a partially working system.

---

### Post by col48 on 2018-07-11
Followup to Post #13.

That made no difference.  Should 'DevRelease' be replaced by something else, given that I am running 16.04?

---

### Post by #&amp;thj^% on 2018-07-11
The line you are looking for is:
```
//Unattended-Upgrade::Remove-Unused-Dependencies "false";
```
and edit it to look like this>>> but read the rest below for understanding what you are now doing.
```
Unattended-Upgrade::Remove-Unused-Dependencies "true";
```
You are now making things very hard and complex for yourself as kernel updates roll in, /boot will fill with kernels risking your chances for future updates and installing packages>>>in other words breaking the package manager. :(
So I strongly advise not doing this.
Also Read carefully:
> Option for Ubuntu 16.04 and newer

Unattended-upgrades version 0.90 supports a new configuration variable that makes it possible to automatically remove only packages that become excessive during a run of unattended-upgrades. It is enabled i.e. "true" by default, so make sure /etc/apt/apt.conf.d/50unattended-upgrades does not contain:

**Unattended-Upgrade::Remove-New-Unused-Dependencies "false"**

The way this is designed, it is important that you let unattended-upgrades handle installion of security updates. Otherwise unattended-uprades will not remove old kernels and you may have to do some manual removing of kernels.

Problems

If your package management is broken, or if regular maintenance above is not working, any of several problems may have occurred. You may be out of storage space, or you may have a package version mismatch, or you may have another problem. 
Wouldn't it be safer to just leave things they way they are intended.(Redundant :))
I find that my wants at times come with heavy Consequences that are not really felt til they kick me in the behind. :(

**EDIT: I just now found some old notes **I have kept from 16.04 on keeping kerenels that I needed in testing via the **"01autoremove-kernels" **and adding them there'
Example for 18.04 I have listed these for "non-removal"
```
[COLOR="#FF0000"]// DO NOT EDIT! File autogenerated by /etc/kernel/postinst.d/apt-auto-removal[/COLOR]
APT::NeverAutoRemove
{
   "^linux-image-4\.15\.0-26-generic$";
   "^linux-image-4\.17\.4-041704-lowlatency$";
   "^linux-headers-4\.15\.0-26-generic$";
   "^linux-headers-4\.17\.4-041704-lowlatency$";
   "^linux-image-extra-4\.15\.0-26-generic$";
   "^linux-image-extra-4\.17\.4-041704-lowlatency$";
   "^linux-modules-4\.15\.0-26-generic$";
   "^linux-modules-4\.17\.4-041704-lowlatency$";
   "^linux-modules-extra-4\.15\.0-26-generic$";
   "^linux-modules-extra-4\.17\.4-041704-lowlatency$";
   "^linux-signed-image-4\.15\.0-26-generic$";
   "^linux-signed-image-4\.17\.4-041704-lowlatency$";
   "^kfreebsd-image-4\.15\.0-26-generic$";
   "^kfreebsd-image-4\.17\.4-041704-lowlatency$";
   "^kfreebsd-headers-4\.15\.0-26-generic$";
   "^kfreebsd-headers-4\.17\.4-041704-lowlatency$";
   "^gnumach-image-4\.15\.0-26-generic$";
   "^gnumach-image-4\.17\.4-041704-lowlatency$";
   "^.*-modules-4\.15\.0-26-generic$";
   "^.*-modules-4\.17\.4-041704-lowlatency$";
   "^.*-kernel-4\.15\.0-26-generic$";
   "^.*-kernel-4\.17\.4-041704-lowlatency$";
   "^linux-backports-modules-.*-4\.15\.0-26-generic$";
   "^linux-backports-modules-.*-4\.17\.4-041704-lowlatency$";
   "^linux-modules-.*-4\.15\.0-26-generic$";
   "^linux-modules-.*-4\.17\.4-041704-lowlatency$";
   "^linux-tools-4\.15\.0-26-generic$";
   "^linux-tools-4\.17\.4-041704-lowlatency$";
   "^linux-cloud-tools-4\.15\.0-26-generic$";
   "^linux-cloud-tools-4\.17\.4-041704-lowlatency$";
};
/* Debug information:
# dpkg list:
iF  linux-image-4.15.0-26-generic                 4.15.0-26.28                                    amd64        Signed kernel image generic
ii  linux-image-generic                           4.15.0.26.28                                    amd64        Generic Linux kernel image
ii  linux-image-unsigned-4.17.4-041704-lowlatency 4.17.4-041704.201807031235                      amd64        Linux kernel image for version 4.17.4 on 64 bit x86 SMP
# list of installed kernel packages:
4.15.0-26-generic 4.15.0-26.28
# list of different kernel versions:
4.15.0-26.28
# Installing kernel: 4.15.0-26.28 (4.15.0-26-generic)
# Running kernel: ignored (4.17.4-041704-lowlatency)
# Last kernel: 4.15.0-26.28
# Previous kernel: 
# Kernel versions list to keep:
4.15.0-26.28
# Kernel packages (version part) to protect:
4\.15\.0-26-generic
4\.17\.4-041704-lowlatency
*/

```
But again this is concidered Advanced users only and come with a **HIGH RISK** for Breakage>>>So again I advise to not muck around with this and leave things as indended

---

### Post by col48 on 2018-07-11
Since I intend to continue my habit of only keeping two proven kernels (ie ones I have had no problem with) and manually removing earlier ones with synaptic, I don't expect my available disk space to diminish very much - it is currently well under 50% full.

I'd be a little more worried about unused dependencies of non-kernel packages.  But not much.  Does unattended-upgrades look after these as well?

I'm puzzled about the name unattended-upgrades.  In my context (not a server, no scheduled unattended maintenance etc) no package including kernels gets updated without my manually granting synaptic permission to do so each time via its GUI.  I can see that other contexts might well want middle-of-the-night unattended updates, but I do not - I like to have some idea what is going on!

---

### Post by #&amp;thj^% on 2018-07-11
> **col48 said:**
> 
I'd be a little more worried about unused dependencies of non-kernel packages.  But not much.  Does unattended-upgrades look after these as well?


Yes it dose IE:"Remove-Unused-Dependencies" this also deals with non related to kernels. and could confuse the Package Manger at some point.
> **col48 said:**
> 
I'm puzzled about the name unattended-upgrades.  In my context (not a server, no scheduled unattended maintenance etc) no package including kernels gets updated without my manually granting synaptic permission to do so each time via its GUI.  I can see that other contexts might well want middle-of-the-night unattended updates, but I do not -**_ I like to have some idea what is going on!_**
Answering this is more or less dual edged. And as best I know.
Well in part yes>>it is one part of all the mechanism's and scripts in place by the Developers and other parts of which is hard coded in the OS itself.
Now I'm no guru on this matter but after more than a decade of testing (And knowledge shared by some Developers) some things just become apparent.
The only sound advice I can offer now is to leave the OS as is>> until you have gained the needed experience and skills to run a more customized user's OS.
Which also leaves you in charge of keeping it secure and stable. (Just my 2 cents)
 (Honestly I'm not trying to sound evasive :) and this will vary from user to user)
Also to add to this:
How to tell when unattended upgrades will run today:

The random time is set by a cron job (/etc/cron.daily/apt.compat), and you can read the random time for today by asking systemd:
```

$ systemctl list-timers apt-daily.timer
NEXT                         LEFT     LAST                         PASSED      UNIT            ACTIVATES
Tue 2017-07-11 01:53:29 CDT  13h left Mon 2017-07-10 11:22:40 CDT  1h 9min ago apt-

```
In this case, you can see that unattended upgrades ran 1 hour and 9 minutes ago.

How to tell which step apt is running right now:

One easy way is to check the unattended-upgrades logfile.
```

$ less /var/log/unattended-upgrades/unattended-upgrades.log
2017-07-10 11:23:00,348 INFO Initial blacklisted packages: 
2017-07-10 11:23:00,349 INFO Initial whitelisted packages: 
2017-07-10 11:23:00,349 INFO Starting unattended upgrades script
2017-07-10 11:23:00,349 INFO Allowed origins are: ['o=Ubuntu,a=zesty-security', 'o=Ubuntu,a=zesty-updates']
2017-07-10 11:23:10,485 INFO Packages that will be upgraded: apport apport-gtk libpoppler-glib8 libpoppler-qt5-1 libpoppler64 poppler-utils python3-apport python3-problem-report
2017-07-10 11:23:10,485 INFO Writing dpkg log to '/var/log/unattended-upgrades/unattended-upgrades-dpkg.log'
2017-07-10 11:24:20,419 INFO All upgrades installed
```

Here you can see the normal daily process, including the 'started' and 'completed' lines, and the list of packages that were about to be upgraded.

If the list of packages is not logged yet, then apt can be safely interrupted. Once the list of packages is logged, DO NOT interrupt apt.
This i picked up from ian-weisser
I hope others will chime in here also.
**BTW I often update my Posts when it pertains to relevant information..**

---

### Post by Cavsfan on 2018-07-11
I do not like anything to be installed without my knowledge, behind my back so to speak. So I immediately purge unattended-upgrades **sudo purge unattended-upgrades**.

I would think even an inexperienced Linux user would not want anything like this either.

So when I see a new kernel getting installed I immediately check my system for how many kernels I have. I added these aliases to ~/.bashrc to make it easy on myself.
```
alias list-kernels='dpkg -l | grep -e "linux-generic" -e "linux-headers" -e "linux-image"'
```
Or this 2nd one is if you have a UEFI system.
```
alias list-kernels='dpkg -l | grep -e "linux-generic" -e "linux-headers" -e "linux-image" -e "linux-libc-dev" -e "linux-modules" -e "linux-signed-generic"'

```Then I just have to type in terminal list-kernels and I will see how many I have.
If there is more than 2 I use this command (alias) now to autoremove the 3 kernel.

```
alias udar='sudo apt --purge autoremove'
```
Then just enter udar in terminal and my password and it does it's thing.
This also purges the config files that go along with whatever is autoremoved. If you do not remove the config files too, then it gets confusing when you look at the output of list-kernels.
It will list old kernels packages with (rc) beside of the them, making it look like they are installed when it just the "residual config" files (what rc stands for) that are still installed.

So, rather than having to take the additional step of deleting the config files, just delete them with the autoremove command.

If you ever want to switch to updating the CLI way, which is the most effective and shows you what is going to happen before it happens, here are the aliases I use:
```
#update aliases
alias ud='sudo apt update && apt list --upgradable'
alias upd='sudo apt upgrade'

```
Then I just enter ud in terminal and if there are updates listed I enter upd afterwards and it gets all of the updates.

That's my 2 cents and I do not know everything either by any stretch of the imagination, just trying to help.

---

### Post by #&amp;thj^% on 2018-07-11
@Cavsfan OP wants to select different kernels that may not be the the last two installed. More of a custom selection that he wants to keep.

---

### Post by Cavsfan on 2018-07-12
> **1fallen said:**
> @Cavsfan OP wants to select different kernels that may not be the the last two installed. More of a custom selection that he wants to keep.

Oh ok.

---

### Post by col48 on 2018-07-13
@Cavsfan
1fallen is exactly right - that's what I want to do.  Partly because there is a [tiny] risk that a new kernel will make my system unusable and its successor may not fix the problem, whereas the effect of a faulty new version of a web browser or an email client won't have such a drastic effect.  So I want to be sure of having a stable kernel and only remove it once I am content from my own experience that a new version is OK.  I typically keep 3 kernels but have plenty of HD space (over 150Gb) spare so am not too concerned if I end up with a couple more.  Actually booting an old kernel is exceedingly rare.

But with that reservation I do want to keep my system up-to-date -- actually doing updates at a moment of my own choosing when I am not running anything else.  I don't want to be competing for CPU, bandwidth, or anything else when the update is under way.

I'd just rather not risk forgetting to untick the box in the list presented by update.  I was happier when it was not offered!

But, @Cavsfan, what you have posted is illuminating.  I thoroughly agree with this:
```
I do not like anything to be installed without my knowledge, behind my back so to speak.

I would think even an inexperienced Linux user would not want anything like this either.
```
I'm moderately experienced - enough to know my limitations, hence the original post.  Ubuntu for 9 years, and a tiny bit of Unix many years ago.

---

### Post by mc4man on 2018-07-14
Why is there the apparent assumption update-manager (Software Updater)  & unattended-upgrades are connected here? 

unattended-upgrades is going to do it's work without any input from you, i.e in this case remove any kernels _already marked _for autoremove.
It would seem update-manager is setting these _already marked_  kernel packages to be removed, though you need to agree to do so.

It's apt that's marking them for autoremoval, if you want to stop that then stop apt from doing so. ( the issue there is most users don't know which of the 3-5 packages would need to be removed if they aren't marked..) It does that via /etc/kernel/postinst.d/apt-auto-removal file.

Best thing to do control all is purge unattended-upgrades package, plus in Software & Updates > updates  set it to "Display immediately" for  security updates & basically just use synaptic to do your updating. Synaptic will list packages marked for autoremove but never automatically do so or auto mark them for removal.

The package that notifies you of updates is update-notifier

---

### Post by col48 on 2018-09-01
```
Best thing to do control all is purge unattended-upgrades package, plus in Software & Updates > updates set it to "Display immediately" for security updates 
```

This does not seem to have made any difference.
I waited until another couple of kernels have appeared and have manually purged those that were extant at the time I purged the package.

I think I'll just put up with having to remain vigilant.

---

### Post by col48 on 2018-09-13
I needed to be more patient.

After [manually] purging the files relating to one more kernel, autoremove of old kernels is no longer offered at every update, even though i (currently) have three installed.

Accordingly marked as solved.

Thanks for every contribution.

---

