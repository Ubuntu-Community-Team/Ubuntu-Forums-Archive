---
title: "Internal error - gpu hung"
date: 2013-03-21
forum: General Help
---

### Post by habana on 2013-03-21
On 20 March, crash report errors started to appear typically 20 minutes after turn on. These generate files in var/crash unlike the "false gpu hung" bug already reported. Sometimes the screen freezes, sometimes Firefox doesn't respond. Sometimes the system operates normally. This problem has been noted on "Ask Ubuntu" but closed without resolution as being too localised, whatever that means. This is not a new installation and I have made no major chages to the system other than regular updates.

Syslog reports

```
[ 2460.825149] [drm:i915_hangcheck_hung] ERROR Hangcheck timer elapsed... GPU hung
```

Ubuntu 12.10 64 bit 
Intel Sandybridge integrated graphics 
kernel 3.5.0-26-generic

Any advice on how to proceed would be appreciated

---

### Post by tgalati4 on 2013-03-21
Do you have any temperature monitors for the Intel Integrated Graphics?  It's possible that it's overheating and most Intel chips will just stop when a thermal threshhold is exceeded.  If this is a laptop, take some compressed air (75 psi) not the canned air, and blow out the dust from the air vents.  It might be time to open it up and check the heat paste.  Usually the integrated graphics chip share a heat sink with the main CPU.  Once the paste is replaced, tighten down properly, but don't overtighten or you will break the screws.

---

### Post by habana on 2013-03-22
> **tgalati4 said:**
> Do you have any temperature monitors for the Intel Integrated Graphics?  It's possible that it's overheating and most Intel chips will just stop when a thermal threshhold is exceeded.  If this is a laptop, take some compressed air (75 psi) not the canned air, and blow out the dust from the air vents.  It might be time to open it up and check the heat paste.  Usually the integrated graphics chip share a heat sink with the main CPU.  Once the paste is replaced, tighten down properly, but don't overtighten or you will break the screws.

Thanks for your response. The PC was a new build when I installed 12.10 a few months ago. The mini tower case has a filter on the fan intake - this is clean. I can't monitor GPU temperature but mobo and CPU temperatures are all normal which would not be the case if there was an airflow problem. I assume that your thoughts are based on the 20 minute delay before the first crash? This behaviour was reported on previous Ubuntu versions and was fixed by kernel updates. In this instance it is more likely that a kernel update has caused the problem as I believe there was such an update a few days ago.

I should add that I have Ubuntu installed on a SSD which did cause a similar problem with earlier versions I understand.

---

### Post by anorakgirl on 2013-03-23
Hi,
The exact same problem started happening for me 2-3 days ago, after doing an update.

*ERROR* hangcheck timer elapsed... gpu hung

Ubuntu 12.04 LTS
kernel 3.2.0-39-generic

The machine is unusable, it typically freezes within a few minutes of use.

No idea how to start looking for a solution, please let me know if you get anywhere. 

Thanks,

---

### Post by Bashing-om on 2013-03-23
Do the machines successfully boot an older kernel ?

---

### Post by cappuccino4me on 2013-03-23
Hi,

I have the exact same problem as described by anorakgirl. It started occuring after the last update I made yesterday. However when I boot the previous kernel (3.2.0-38) my machine work fine:

Linux xxx 3.2.0-38-generic #61-Ubuntu SMP Tue Feb 19 12:18:21 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by keithb on 2013-03-23
I am having the same problem I think. I did an update yesterday and then today these error messages keep popping up.

I am using  v12.10 on Lenovo G570 laptop. Everything has been working great until the last update and then all of a sudden these error messages start popping up all over the place.

Not sure how to fix it or if I need to wait for another update to fix the problem.

---

### Post by father_ted on 2013-03-23
i have tried booting to an earlier kernel and it made FA difference.

---

### Post by habana on 2013-03-24
> **father_ted said:**
> i have tried booting to an earlier kernel and it made FA difference.

I have now tried this too - no difference

---

### Post by jturner on 2013-03-24
Hi all -- a me-too, and an observation. I get these GPU hangs (some of which are real, computer-killing hangs) exclusively while running XUL-based applications. Thunderbird is the worst offender, followed closely by Firefox. To confirm that it's not an overheating issue, I've used heavyweight OpenGL apps with shaders to get my machine so hot that it *does* complain about temperature... and this only happens at far, far higher loads than what the XUL apps are generating.

[EDIT] - Another strange, possibly unrelated side effect. Since the problem started, the <canvas> object in Firefox has become badly broken. Updates are only painted about once every 8 seconds. Trying to work up a test case.

---

### Post by anorakgirl on 2013-03-24
If it is any help, every time my screen froze I was using chrome to browse the internet, but I don't know if this was a coincidence.

---

### Post by anorakgirl on 2013-03-24
Further update, I followed the advice here [http://ubuntuforums.org/showthread.php?t=2128691](http://ubuntuforums.org/showthread.php?t=2128691) and started up in 3.2.0-37-generic and it seems to be stable so far.

---

### Post by keithb on 2013-03-24
> **keithb said:**
> I am having the same problem I think. I did an update yesterday and then today these error messages keep popping up.

I am using  v12.10 on Lenovo G570 laptop. Everything has been working great until the last update and then all of a sudden these error messages start popping up all over the place.

Not sure how to fix it or if I need to wait for another update to fix the problem.

Okay, not sure what happened. I was having these error messages yesterday and when I ran across this thread it sounded a lot like what I was seeing. The error messages have gone away now. Maybe there was something blocking the air vent?? I don't know. I am a little puzzled. Ubuntu 12.10 on Lenovo G570 laptop.

---

### Post by fouad_jh on 2013-03-25
Hi all

I had the same problem, I was running Ubuntu 11.10, and started having a problem with crashes quite often after updating, then freshly installed Ubuntu 12.04 and had the same problem after updating, apparently kernel 3.5.0-26 where things go wrong, I tried 3.5.0-23 and 3.2.0-39, and seemed ok

For now, I boot into the old kernel versions waiting for a fix on the new kernel compilations.

Fouad

---

### Post by tstuefe on 2013-03-25
I see the same error. Same Syslog entries. Happens since mid of last week (I update almost daily). 

My machine is a thinkpad T520 with integrated Sandy Bridge graphics. The machine works usually flawless, this is the first real problem I have with Ubuntu since a year or so.

Sometimes I also get weird graphic errors: All gnome fonts missing some letters. This makes reading menu entries or window decorations  kind of awkward.

I tried rebooting to an earlier kernel, but this did not solve the problem.

---

### Post by WA4MOE on 2013-03-25
Ditto, major gpu hang, internal error. Repoorted them as I can, however the error continues constatntly. Sometimes it is hard to finish a simple email or read an email without being interrupted by the next "internal error". 
I have the Psensor running with Core 1 and 2 temps at about 47 to 48 C.

...3/27/13  Update: HP ProBook 4530s, 64 bit, installed 12.10 5-6 months ago, crashes showed first about 1 week ago. Used Psensor for temp monitor and it may occur a bit more frequently with higher temp, but not sure. Firefox browser, Thunderbird email, Libre Office, Scribus are major software installed. Attempt to isolate has not given any solid clues at all. 

Errors shown: 

       Poss GPU hang

               usr/shore/apport/apport-gpu-error-intel.py
       Package:
               xserver-xorg-video-intel.2.2.20-9-Oubuntu2
      Problem:
              Crash
              title [sandy bridge-m-gt2]false GPULockup IPHER:  0x4ld00000IPEHR: 0x0b140001
          
              tmp.unity.support.test.0

I may not have copied these messages exactly, please forgive me.

---

### Post by habana on 2013-03-26
> **WA4MOE said:**
> Ditto, major gpu hang, internal error. Repoorted them as I can, however the error continues constatntly. Sometimes it is hard to finish a simple email or read an email without being interrupted by the next "internal error". 
I have the Psensor running with Core 1 and 2 temps at about 47 to 48 C.
Please help.

I use xsensors and have just noted that the reported coretemps are jumping around like a demented kangaroo. top reports very little activity so whatever is causing the gpu hang is presumably affecting lm-sensors.

---

### Post by mmaarr on 2013-03-27
Reporting the exact same behaviour on 12.10 64bit

Some clues:
1. installation from DVD without updates/with all suggested updates - no difference
2. installation on SSD/HDD - no difference
3. ext4/xfs - no difference
4. after showing artifacts (disapearing fonts, random lines, freezed windows) switching by Ctrl-Alt-number and back to Ctrl-Alt-7 - recreates the correct image
5. intensive streaming, downloading, etc.  vs. no activity - no difference
6. not using Chrome - the same
7. not using Firefox - the same
8. scrolling windows content and writing text is apparently the most risky activity - although crash happens also with no user activity

dmesg shows:
[drm:i915_hangcheck_hung] *ERROR* Hangcheck timer elapsed... GPU hung
[ 2707.923920] [drm] Enabling RC6 states: RC6 off, RC6p off, RC6pp off

and also:

WARNING: at /build/buildd/linux-3.5.0/drivers/gpu/drm/i915/intel_pm.c:2505 gen6_enable_rps+0x706/0x710 [i915]()


[EDIT]: Ignoring the kernel upgrade to 3.5.0.26 seems to solve the problem for now.

---

### Post by WA4MOE on 2013-03-27
I have two other machines with the same problem, exibited slightly differently. One is desktop 64 bit, other a used laptop 64 bit, HP G60. The core temps on the HP G60 laptop is very high....95 -103 C....!!! Nothing more to add but it reders all three machines unusable.

---

### Post by fouad_jh on 2013-03-28
> **tstuefe said:**
> I see the same error. Same Syslog entries. Happens since mid of last week (I update almost daily). 

My machine is a thinkpad T520 with integrated Sandy Bridge graphics. The machine works usually flawless, this is the first real problem I have with Ubuntu since a year or so.

Sometimes I also get weird graphic errors: All gnome fonts missing some letters. This makes reading menu entries or window decorations  kind of awkward.

I tried rebooting to an earlier kernel, but this did not solve the problem.

What is the older kernel version?

---

### Post by WA4MOE on 2013-03-30
With regular updates installed in the last 2 days the problem has disapeared. It seems to be solved. How and why is not explained however it is jsut delightful to have no more GPU hangs. Thanks all the volunteers that work so hard to manage the rare problem like this hang. This really is the first time in about 5-6 years that any kind of major problem has shown itself with Ubuntu. 
Thank You developeers and volunteers.
Moses
Waxhaw NC

---

### Post by habana on 2013-03-31
> **WA4MOE said:**
> With regular updates installed in the last 2 days the problem has disapeared. It seems to be solved. How and why is not explained however it is jsut delightful to have no more GPU hangs. Thanks all the volunteers that work so hard to manage the rare problem like this hang. This really is the first time in about 5-6 years that any kind of major problem has shown itself with Ubuntu. 
Thank You developeers and volunteers.
Moses
Waxhaw NC

My system is up to date but there is no change here. I am not marking this thread as solved

---

### Post by never2far on 2013-04-01
I have same problem and it's still present on my laptop too

---

### Post by hiWorld on 2013-04-01
> **WA4MOE said:**
> With regular updates installed in the last 2 days the problem has disapeared. It seems to be solved. How and why is not explained however it is jsut delightful to have no more GPU hangs. Thanks all the volunteers that work so hard to manage the rare problem like this hang. This really is the first time in about 5-6 years that any kind of major problem has shown itself with Ubuntu. 
Thank You developeers and volunteers.
Moses
Waxhaw NC

The exact same problem here - Ubuntu 12.10. I've tried almost everything I found on the Net but nothing helped. Could you please list the updates you've done?

---

### Post by martinfl on 2013-04-01
I have had this problem since the last update as well. I try to read some of the threads about what people are doing. But, I have no freakin idea what they are talking about. I am not without some basic technical skills. But I am relatively new to ubuntu and linux. I really need the type of fix that is closer to a recipe rather than someone telling me to just tear down the engine and rebuild it.

I don't know the protocol as to how things get corrected like this. Will there be an update that addresses it?

This thing is beating me down. I have continued to work around it, but now my system goes it to a hard freeze every now and then.

It seems to be related to the gpu. Would using an external video card solve the problem. If so, I will go out and install one.

---

### Post by mmaarr on 2013-04-02
I had the 'GPU hung' problem on a fresh installation, so I installed the system from a DVD ([http://torrent.ubuntu.com/xubuntu/releases/quantal/release/desktop/xubuntu-12.10-desktop-amd64.iso.torrent](http://torrent.ubuntu.com/xubuntu/releases/quantal/release/desktop/xubuntu-12.10-desktop-amd64.iso.torrent)) once more and then NOT accepted any updates. They show 3.5.0.26 as the stable kernel. I'm staying with 3.5.0.17 and there is no sign of the problem here. I think the same (kernel downgrade) can be achieved without reinstallation.

---

### Post by martinfl on 2013-04-02
> **mmaarr said:**
> I had the 'GPU hung' problem on a fresh installation, so I installed the system from a DVD ([http://torrent.ubuntu.com/xubuntu/releases/quantal/release/desktop/xubuntu-12.10-desktop-amd64.iso.torrent](http://torrent.ubuntu.com/xubuntu/releases/quantal/release/desktop/xubuntu-12.10-desktop-amd64.iso.torrent)) once more and then NOT accepted any updates. They show 3.5.0.26 as the stable kernel. I'm staying with 3.5.0.17 and there is no sign of the problem here. I think the same (kernel downgrade) can be achieved without reinstallation.

I am using 3.5.0.26 and it is definitely not stable. My system generates error messages every few minutes. I wonder if this is an annoyance for a handful of people or is this a problem for a significant number of Ubuntu users?

---

### Post by hiWorld on 2013-04-02
> **mmaarr said:**
> I had the 'GPU hung' problem on a fresh installation, so I installed the system from a DVD ([http://torrent.ubuntu.com/xubuntu/releases/quantal/release/desktop/xubuntu-12.10-desktop-amd64.iso.torrent](http://torrent.ubuntu.com/xubuntu/releases/quantal/release/desktop/xubuntu-12.10-desktop-amd64.iso.torrent)) once more and then NOT accepted any updates. They show 3.5.0.26 as the stable kernel. I'm staying with 3.5.0.17 and there is no sign of the problem here. I think the same (kernel downgrade) can be achieved without reinstallation.

**"Kernel downgrade"** can be made via **Grub**.

 Already tried booting the 3.5.0.17 kernel instead of 3.5.0.26 and seems to be stable so far.  Thanks for the idea (y)

---

### Post by CamPsych on 2013-04-03
@martinfl - check out [http://ubuntuforums.org/showthread.php?t=2127593&page=4](http://ubuntuforums.org/showthread.php?t=2127593&page=4) for a description of problem. I updated kernel to 3.8 and have had no issues since. If you go to [http://www.liberiangeek.net/2013/03/...-ubuntu-12-10/]("http://www.liberiangeek.net/2013/03/linux-kernel-3-8-1-releasedhow-to-install-upgrade-in-ubuntu-12-10/") to download the kernel there are instructions on how to do it. Make sure you follow the instruction on above forum page to pin the kernel. 

Also I have Sandy Bridges arch on my driver, so that needed to be updated - get PPA drivers x-swat and ppa glasen/intel-drivers - I googled them and found them and instructions for them pretty quickly.

---

### Post by martinfl on 2013-04-03
I went the other way. I rolled back to 3.5.0.25 and have not seen the problem since then.

---

### Post by habana on 2013-04-03
> **martinfl said:**
> I went the other way. I rolled back to 3.5.0.25 and have not seen the problem since then.

Unfortunately 3.5.0.25 didn't fix it for me. i have been a Ubuntu user since 7.10 and this is the first bug I've come across. I therefore have no idea if and when it will be fixed. I'm not inclined to update the kernel to 3.8 as 13.04 is only a few weeks away and I can put up with the problem until then. In the mean time I have disabled automatic crash reporting in xdiagnose.

---

### Post by martinfl on 2013-04-03
> **habana said:**
> Unfortunately 3.5.0.25 didn't fix it for me. i have been a Ubuntu user since 7.10 and this is the first bug I've come across. I therefore have no idea if and when it will be fixed. I'm not inclined to update the kernel to 3.8 as 13.04 is only a few weeks away and I can put up with the problem until then. In the mean time I have disabled automatic crash reporting in xdiagnose.

Do we know if it is fixed in 13.04?

---

### Post by habana on 2013-04-04
> **martinfl said:**
> Do we know if it is fixed in 13.04?

I assume it will be tested for known bugs before release. Then of course we may see a new set of bugs!

---

### Post by habana on 2013-04-11
Following the recent kernel update (3.5.0.27), the problem is now much worse. What was just glitches every so often is now a freeze - power reset required. Typical syslog excerpt:

```
Apr 11 18:42:00 computer1 kernel: [ 3038.958432] [drm:intel_crt_detect], CRT detected via hotplug
Apr 11 18:42:03 computer1 kernel: [ 3041.085924] [drm:i915_hangcheck_hung] *ERROR* Hangcheck timer elapsed... GPU hung
Apr 11 18:42:03 computer1 kernel: [ 3041.085981] [drm:i915_error_work_func], resetting chip
Apr 11 18:42:03 computer1 kernel: [ 3041.086088] [drm:i915_reset] *ERROR* GPU hanging too fast, declaring wedged!
Apr 11 18:42:03 computer1 kernel: [ 3041.086089] [drm:i915_reset] *ERROR* Failed to reset chip.
Apr 11 18:42:03 computer1 gnome-session[1498]: WARNING: App 'compiz.desktop' respawning too quickly
Apr 11 18:42:03 computer1 gnome-session[1498]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Apr 11 18:42:03 computer1 kernel: [ 3041.177590] [drm:intel_dp_aux_ch], dp_aux_ch timeout status 0x5143003f
Apr 11 18:42:03 computer1 kernel: [ 3041.184426] [drm:intel_dp_aux_ch], dp_aux_ch timeout status 0x5143003f
Apr 11 18:42:03 computer1 kernel: [ 3041.192408] [drm:intel_dp_aux_ch], dp_aux_ch timeout status 0x5143003f
```

I was very sorry to read that my fail whale had died but it leaves me none the wiser!

---

### Post by ddb on 2013-04-12
I solved the problem using the latest available kernel & headers:

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal

$ uname -a
Linux ThinkPad-X220 3.9.0-030900rc6-generic #201304080035 SMP Mon Apr 8 04:36:25 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Download it from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-rc6-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-rc6-raring/)

And install it via dpkg (i.e. dpkg -i linux-headers* linux-image*)

No more gpu hung for me. I hope this helps you too!

---

### Post by martinfl on 2013-04-12
> **ddb said:**
> I solved the problem using the latest available kernel & headers:

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.10
Release:    12.10
Codename:    quantal

$ uname -a
Linux ThinkPad-X220 3.9.0-030900rc6-generic #201304080035 SMP Mon Apr 8 04:36:25 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Download it from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-rc6-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-rc6-raring/)

And install it via dpkg (i.e. dpkg -i linux-headers* linux-image*)

No more gpu hung for me. I hope this helps you too!

How long has it been installed?

When I installed 3.5.0.27 it worked great for a few days. Maybe one appearance of the bug a day. Then it degraded. Now I can see it pop up frequently and then just disappear for the entire day. I even got relief when I rolled back to .25 for a few days. Then the machine went bonkers.

I still would like to know if anyone experiencing this problem uses an external video card or is this limited to those with motherboard based video?

---

### Post by ddb on 2013-04-12
Two days already and I have two thinkpad x220, both of them working great after this installation. The "gpu hung" problem affects the intel integrated video, so most likely no external video have the same problems.

PS no bug appearance so far

---

### Post by martinfl on 2013-04-12
Anyone have a positive experience with any of the low-end standalone video cards. Reading through those that are certified for Linux, they are all fairly old.

---

### Post by ilyasimenko on 2013-04-17
I have the same problem. I have Lenovo ideapad b580 with pentium b940 CPU without discrete GPU. It started in march after update. The bug is present in Ubuntu 12.10, 12.04.2 and xubuntu 12.10. Kernel version is 3.5.0-27-generic 32 bit.

---

### Post by martinfl on 2013-04-17
I rolled back to 3.5.0-19 and upon restart, got the same error message. Is it a bug in the kernal or is it something else? Had to do a hard restart today after solid freeze.

It seems to get worse as the day rolls on. Although, my machine is never turned off.

Has there been a formal announcement or universal recognition that the software is screwed up and a fix is coming? I am probably going to try an external video card and hope it clears this all up.

---

### Post by martinfl on 2013-04-21
I am wondering if anyone has tried out the 13.04 beta and if it did anything to fix the gpu hang problem?

Also, I am looking for a low end video card that is essentially "plug and play". I don't care about games, etc. I just want something to pop in and work with the standard drivers. I am thinking that this would finally get rid of this annoying problem. The fact that the entire Ubuntu community is not affected means it must be a relatively small group having this problem. I am not holding my breath for a fix. They have a ton of other things to work out with 13.04

---

### Post by plbuster on 2013-04-21
Hi all...
hey...I'm a newbie...but I found out, through a different thread, and I have the same problem...system keeps hanging up...(GPU hung)....

didn't happen when I loaded Ubuntu or ran it for a few weeks...but then...well, updates...
so...there is some update that is broke somewhere....

---

### Post by martinfl on 2013-04-21
> **plbuster said:**
> Hi all...
hey...I'm a newbie...but I found out, through a different thread, and I have the same problem...system keeps hanging up...(GPU hung)....

didn't happen when I loaded Ubuntu or ran it for a few weeks...but then...well, updates...
so...there is some update that is broke somewhere....

I rolled back to 3.5.0.19 and stopped using FireFox (switched to Chrome). Did the problem go away? No, but it is less frequent and I can work. Will I put up with it forever? No, eventually if I cannot solve the problem either through updates or possibly the addition of a video card, I will have to go back to Windows 7. I don't want to, but I would have no choice.

---

### Post by habana on 2013-04-22
> **martinfl said:**
> I rolled back to 3.5.0.19 and stopped using FireFox (switched to Chrome). Did the problem go away? No, but it is less frequent and I can work. Will I put up with it forever? No, eventually if I cannot solve the problem either through updates or possibly the addition of a video card, I will have to go back to Windows 7. I don't want to, but I would have no choice.

Rolling back to an old kernel didn't help me but using Chromium instead of Firefox does seem to result in less crashes - thanks for the hint. If we can stagger along for another week, 13.04 will be released. I can find no mention of this bug on the Raring Ringtail forum.

---

### Post by martinfl on 2013-04-22
> **habana said:**
> Rolling back to an old kernel didn't help me but using Chromium instead of Firefox does seem to result in less crashes - thanks for the hint. If we can stagger along for another week, 13.04 will be released. I can find no mention of this bug on the Raring Ringtail forum.

It is as if the people affected are an insignificant number. I don't know if 13.04 is the answer. Once I upgrade it might be worse.

---

### Post by martinfl on 2013-04-22
Another thing I notice is that I can go all day with no error messages.  The next day I "wake up" the machine and one appears. If for any reason you decide you want to see if this is the same message or look at the details, report it, etc. it will continue to pop up every few seconds until you restart. If I hit cancel it goes away and might not pop up all day.

Wouldn't it be nice if you saw something here from the team that maintains Ubuntu and is responsible for the fixes to write on this thread something like "hey we know about this and we are working on a fix". But we have a free OS and it is not like you can really complain to much.

---

### Post by habana on 2013-04-22
Mu guess is that the Ubuntu team are flat out sorting out problems with 13.04. As this is a recognized bug on Launchpad, I would expect it to be fixed in 13.04.

---

### Post by martinfl on 2013-04-22
> **habana said:**
> Mu guess is that the Ubuntu team are flat out sorting out problems with 13.04. As this is a recognized bug on Launchpad, I would expect it to be fixed in 13.04.

I hope you are correct. I have seen places where they closed the bug report. Other people cannot find it as something they are looking at. 

Right now, with Chrome (a bit nicer than chromium) and rolled back to 3.5.0 -19 I can work without much problem. Saw a problem this morning for a minute and nothing all day. So, I am sitting tight. Maybe one of you intrepid souls will test out 13.04 when it is available.

---

### Post by habana on 2013-04-25
> I hope you are correct. I have seen places where they closed the bug report. Other people cannot find it as something they are looking at.

Right now, with Chrome (a bit nicer than chromium) and rolled back to 3.5.0 -19 I can work without much problem. Saw a problem this morning for a minute and nothing all day. So, I am sitting tight. Maybe one of you intrepid souls will test out 13.04 when it is available. 

Upgraded to 13.04 this morning and all seems to be good so far. Back to using Firefox with no problems. I am now happy but will not mark this problem as solved as obviously it isn't for those still using 12.10.

---

### Post by martinfl on 2013-04-26
I received some updates yesterday and among them was some type of fix for the gpu false hang. But when I read through the reports and documentation, they seem to consider it an annoying false alert. When your system is frozen or stops for 5 to 10 seconds at a time multiple times an hour, it does not feel like a false alert. I am relatively new to Linux and might be misinterpreting it. I am going to wait a little bit. I would really appreciate it if you gave us an update in a week to see if you were still past this problem.

---

### Post by habana on 2013-04-26
> I received some updates yesterday and among them was some type of fix for the gpu false hang. But when I read through the reports and documentation, they seem to consider it an annoying false alert. When your system is frozen or stops for 5 to 10 seconds at a time multiple times an hour, it does not feel like a false alert. I am relatively new to Linux and might be misinterpreting it. I am going to wait a little bit. I would really appreciate it if you gave us an update in a week to see if you were still past this problem. 

I understand there are two separate bugs. One is the the false crash report which has been fixed by a workaround. The other, which you, I and others are/were experiencing, has not yet been fixed.

If I remember (!), I will report back next week to confirm all OK in 13.04

---

### Post by habana on 2013-05-01
> If I remember (!), I will report back next week to confirm all OK in 13.04 

Not quite a week but I am off on holiday for a few days. I can confirm this bug is not present on my machine in 13.04

---

### Post by VisualThoy on 2013-05-14
> **habana said:**
> Not quite a week but I am off on holiday for a few days. I can confirm this bug is not present on my machine in 13.04

I'm using 13.04 and had not had this crash until the upgrade. Now it happens nearly every day.

---

### Post by hongquan1987 on 2013-06-21
> **VisualThoy said:**
> I'm using 13.04 and had not had this crash until the upgrade. Now it happens nearly every day.

Me too :-(

---

### Post by ryanvade on 2013-07-15
13.04, latest intel graphics from x-swats, kernel 3.10.1, bumblebee 3.2.1, and nvidia 319.  Still having this issue. :mad:

---

### Post by Bashing-om on 2013-07-15
et all;

I have not checked lately with launchpad on an updated status, will do so on my morrow.

[INDENT][INDENT]we be look'n
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-07-15
Guys;

Near as I can tell the old bugs referring to; 
"drm:i915_hangcheck_hung" have been closed out, as fixed in upstream. This from the lucid era in respect to the i915 driver for Intel hardware.

Maybe a new bug report should be opened, as it looks as if a number of people are affected (again) ?

[INDENT][INDENT][INDENT]just a thought
[/INDENT][/INDENT][/INDENT]

---

### Post by Pawka on 2013-08-22
13.04, Linux yoda 3.8.0-29-generic. Still the same issue here.

---

### Post by Hamish.MacEwan on 2013-10-05
Hi,

Have the same problem, fortunately it only impairs the graphic X interface.  I can ctrl-alt-Fx and login to a text screen where dmesg reports:

[11527.486513] [drm:i915_hangcheck_hung] *ERROR* Hangcheck timer elapsed... GPU hung
[11527.486517] [drm] capturing error event; look for more information in /debug/dri/0/i915_error_state
[11527.886179] openshot[23160]: segfault at 7f5549ab005c ip 00007f5549ab005c sp 00007f5529d22dc0 error 14 in libmltvorbis.so[7f5549cb6000+3000]

There's nothing there I'm competent to recognise, but the machine isn't hung, but X is.

Attached is the output of sudo cat /sys/kernel/debug/dri/0/i915_error_state.  Well it would be, the 307KB zip seems to break some rule, so I can't sorry.

**Update**: Went back to X, not surprisingly OpenShot was gone.  Alt-K-SysRq got me a screenshot and a restart of X.  Logged in and all good.

---

### Post by zazuge on 2013-10-26
I have the same problem I won't repost the same dmesg and syslog error lines
I have tried to corelate the bug with what upgraded package
for me it only started in Oct 21 2013 (according to syslog) never seen this bug before but i think it happened less frequently even before but i have no trace of that (oldest syslog is Oct 19)
there 2 upgrades that are related to this 
on in 19Oct upgraded:
 procps (3.3.3-2ubuntu5.1,3.3.3-2ubuntu5.2)
 xserver-common (1.13.3-0ubuntu6, 1.13.3-0ubuntu6.2)
 xserver-xorg-core (1.13.3-0ubuntu6, 1.13.3-0ubuntu6.2)
 libprocps0 (3.3.3-2ubuntu5.1, 3.3.3-ubuntu5.2)
 xserver-xorg-intel (2.21.6-0ubuntu4.1, 2.21.6-0ubuntu4.3)
the other on 23 Oct:
 Linux-image-3.8.0-32-generic (3.8.0-32.47, automatic)
 .... etc
these two are th most relevant to the bug
I suspect the xserver-xorg-intel package is the culprit
but the new kernel made things worse (GPU hangs happen more frequently) and when i returned to the older kernel to this point it didn't happen again

---

### Post by zazuge on 2013-11-08
after last upgrade of opengl drivers and other upgrades ( intel driver too maybe) I didn't had this bug
shortly after that I upgraded to 13.10 and I no longer had any GPU hang

---

