---
title: "Known gutsy bugs and workarounds"
date: 2007-10-29
forum: General Help
---

### Post by frodon on 2007-10-29
**Disclaimer : The purpose of this thread is just to list known gutsy bugs and give the corresponding workarounds and launchpad entries. All discussions about the bug itself should go in the thread dedicated to the bug.**

**_No Virtual Terminals in Gutsy_**
- Workaround : [http://ubuntuforums.org/showthread.php?t=582962](http://ubuntuforums.org/showthread.php?t=582962)
- Bug report : [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910)

_**Long login time :**_
- Threads : [http://ubuntuforums.org/showthread.php?t=585635](http://ubuntuforums.org/showthread.php?t=585635) and [http://ubuntuforums.org/showthread.php?t=568995](http://ubuntuforums.org/showthread.php?t=568995)
- Bug Report : [https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/151544](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/151544)

**_OpenOffice crashing_**
- Workaround : [http://ubuntuforums.org/showthread.php?t=584088](http://ubuntuforums.org/showthread.php?t=584088)
- Bug report : [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526)

**_Shutdown or restart hangs in Gutsy_**
- Thread : [http://ubuntuforums.org/showthread.php?t=591229](http://ubuntuforums.org/showthread.php?t=591229)
- Bug report : [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119308](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119308)

**_Do not automount USB key_**
- Workaround : [http://ubuntuforums.org/showthread.php?t=582045](http://ubuntuforums.org/showthread.php?t=582045)
- Bug report : [https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025)

**_Can't rename file in Gutsy's Desktop and Nautilus? See here._**
- Workaround : [http://ubuntuforums.org/showthread.php?t=586819](http://ubuntuforums.org/showthread.php?t=586819)
- Bug report : [https://bugs.launchpad.net/ubuntu/+bug/153233](https://bugs.launchpad.net/ubuntu/+bug/153233)

**_Gutsy Intel HD Audio Controller._**
- Workarounds and bug reports : [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

_**No System Sounds (apart from logon sound) **_
- Workarounds : [http://ubuntuforums.org/showthread.php?t=588708](http://ubuntuforums.org/showthread.php?t=588708)

_**Laptop suspend issues :**_
- Workarounds/Support : [http://ubuntuforums.org/showthread.php?t=588239](http://ubuntuforums.org/showthread.php?t=588239)
- Launchpad entries : [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/149714](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/149714)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/156613](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/156613)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/159286](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/159286)

**_java-fullscreen problem in gutsy_**:
- Workarounds/Support : [http://ubuntuforums.org/showthread.php?t=611242](http://ubuntuforums.org/showthread.php?t=611242)
[http://ubuntuforums.org/showthread.php?t=613616](http://ubuntuforums.org/showthread.php?t=613616)
- Bug report :[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/154613](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/154613)

**_Long boot time from GRUB to GDM login screen (with no Splash)_**:
Workaround : [http://ubuntuforums.org/showthread.php?t=581075](http://ubuntuforums.org/showthread.php?t=581075)

_**flashplugin-nonfree md5 mispatch**_
- Workarounds/Support : [http://ubuntuforums.org/showthread.php?p=3923465](http://ubuntuforums.org/showthread.php?p=3923465)
- Bug report : [https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890](https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890)


Fill free to propose other known gutsy bugs to be listed here but think to provide a link to the workaround and a link to the launchpad entry.

---

### Post by WrathofthePenguin on 2007-10-29
I would disagree with the bug link for the Shutdown problem. That bug is for screen corruption on resume from hibernate/suspend. I believe the correct bug should be:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119308](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119308)

---

### Post by frodon on 2007-10-29
yep, just a mistake creating the post, the bug 119308 was the one i wanted to link.

---

### Post by dcstar on 2007-11-02
This link has the fix for the no System Sounds (apart from logon sound) problem:

[http://ubuntuforums.org/showthread.php?t=588708](http://ubuntuforums.org/showthread.php?t=588708)

Basically you install the **esound** package and all is well......

---

### Post by TheExplorer on 2007-11-05
**An old problem with Ubuntu that can lead to HDD failure.**
There has been lotsa complains from Linux-users concerning the extensive use of their HDDs due to the default configuration of the subsystem power management ACPI script in Ubuntu. There is also a lot of messages about this bug #59695 which has been known  for about a year already. The problem is: this shell-script (/etc/acpi/power.sh) when switching to battery power management (actual for laptops) executes the command «hdparm -B 1» for all devices. In this mode HDD goes into standby 7,000 times per every 100 hours. All this leads to HDD failure. As a workaround users are suggested to create a shell-script «99-hdd-spin-fix.sh», with a line «hdparm -B 255 /dev/sda» and copy it to: /etc/acpi/suspend.d/, /etc/acpi/resume.d/ and /etc/acpi/start.d/. There is also an alternative workaround: install laptop-mode-tools packet and configure the file /etc/laptop-mode/laptop-mode.conf having specified CONTROL_HD_POWERMGMT=1.

---

### Post by njparton on 2007-11-05
What about suspend/hibernate issues/bugs?

I still can't get my gutsy PC to sleep automatically after 30 mins as set in power settings and I'm by no means the only one!

---

### Post by TheExplorer on 2007-11-05
It's still buggy. I just don't use it anymore since feisty when I couldn't continue working after hibernation.

---

### Post by njparton on 2007-11-05
Well I've just switched from AMD64 to i386 Gutsy and suspend works for me now.

I also increased the size of my swap partition from 2048 to 4096MB - coincidence?

---

### Post by Charkel on 2007-11-06
If you do not exit windows correctly the disks might not show up in Ubuntu.

---

### Post by frodon on 2007-11-06
Please, that's not worth posting in this thread if you don't link a support thread (if possible with a workaround) and a bug report.
If you need support you can open a thread, if your purpose is to report a bug the right place is launchpad.

---

### Post by Can+~ on 2007-11-06
There's something that is not quite a bug, but it's annoying.

When I first installed FGLRX using the restricted device manager, it all went fine, then I rebooted, but I didn't knew that I had to do those two commands needed for FGLRX after rebooting:

> sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

So my screen turned black with some colored lines on it. When I did those commands, it went all perfectly normal. Fglrx modified the xorg.conf, but didn't added the resolutions, so I had to add them manually. "1280x1024@60".

My point is, if we want a new user to install fglrx in his system, the restricted device manager should also:
-Run those commands after rebooting, then reboot again.
-Add the correct resolution.

I know FGLRX is developed by ati, but those commands are really something that screw new users, like I was (since I never installed fglrx before).

---

### Post by maybeway36 on 2007-11-08
**_kdesudo makes configuration files with uid root_**
-Workaround: [http://ubuntu.lnix.net/misc/kdesudo_1.1-0ubuntu5_i386.deb]("http://ubuntu.lnix.net/misc/kdesudo_1.1-0ubuntu5_i386.deb")
-Bug report: [https://bugs.launchpad.net/ubuntu/+source/kdesudo/+bug/155032]("https://bugs.launchpad.net/ubuntu/+source/kdesudo/+bug/155032")

---

### Post by Endolith on 2007-11-08
> **TheExplorer said:**
> **An old problem with Ubuntu that can lead to HDD failure.**

Is this true?  How could something that causes hardware failure go unfixed for more than a few days?

---

### Post by frodon on 2007-11-09
> **Endolith said:**
> Is this true?  How could something that causes hardware failure go unfixed for more than a few days?Yes and no, your default config is safe, laptop_mode may not be (but not enabled by default).

Please use other threads for such questions, further off topic post will be moved.

---

### Post by frodon on 2007-11-09
> **maybeway36 said:**
> **_kdesudo makes configuration files with uid root_**
-Workaround: [http://ubuntu.lnix.net/misc/kdesudo_1.1-0ubuntu5_i386.deb]("http://ubuntu.lnix.net/misc/kdesudo_1.1-0ubuntu5_i386.deb")
-Bug report: [https://bugs.launchpad.net/ubuntu/+source/kdesudo/+bug/155032]("https://bugs.launchpad.net/ubuntu/+source/kdesudo/+bug/155032")Thanks a lot :)

When i watch the bug report it says "fix commited", is this really fixed ?

---

### Post by TheExplorer on 2007-11-09
Seems to me that an upgrade itself leads to a holy pile of bugs. The only way out is really reinstall the new version of distro. This advice is especially for noobies as it would reduce silly error reports :)

---

### Post by Endolith on 2007-11-09
> **frodon said:**
> Please use other threads for such questions, further off topic post will be moved.

A post about a known gutsy bug is off-topic?

---

### Post by frodon on 2007-11-09
The purpose of this thread is to list known bugs which have a known workarounds and a known bug reports in order to allow users to fix quickly their system, all discussions about these bugs should go in the concerned threads, not here.

---

### Post by maybeway36 on 2007-11-09
> **frodon said:**
> Thanks a lot :)

When i watch the bug report it says "fix commited", is this really fixed ?

There is a package in gutsy-proposed (2.2) that was released after the one above (5), but 2.2 did not work with running programs as non-root users, while 5 did. Why isn't 5 in proposed? I don't know.

---

### Post by fieldstone on 2007-11-10
There are some major things that are missing from this list - two, in fact, that I've tried and tried to fix but just can't. They're big enough problems that I've given up on Gutsy for now. Both of them appear seemingly at random, but once they do, they seem to be unfixable. I've tried every fix I could find online.

1. NetworkManager drops my interfaces. At some point in every installation of Gutsy I've had so far (and I've installed it about ten times), Network manager starts saying "no network devices detected" when I click on it, and that's the end of it. I've tried reinstalling the packages, editing its conf files - nothing. I eventually had to switch over to Wicd just to get basic GUI wireless support. 

2. This one's much worse. At some point most of the times I've installed Gutsy, Gnome refuses to start and gives me a message about a program using setuid or setgid. Again, I've tried editing  conf files and various other fixes I could find online for this, but it doesn't help at all.

I've been using Ubuntu since Breezy, and Ubuntu was how I learned to use Linux in the first place. At this point, I'm a much more advanced user than the people Ubuntu is aimed at, and if I couldn't fix these bugs, neither could they.  It's also worth pointing out that I  stand behind Ubuntu's mission 100 percent - I think the world needs a user-friendly Linux distribution to blow Windows out of the water.

That being said, Gutsy just isn't production-ready. At all. It apparently suffers from the same issue as Windows Vista - being rushed to market to hit a pre-set release date, without actually being completed, and as a result there are huge glaring bugs that are impossible to fix. I really expected better from Ubuntu ; after all, if Dapper could be delayed for two months so that it could be completely finished and working well, I don't see how Gutsy - the first Ubuntu version to include Compiz by default, which I believe (from my web searching) is what's causing bug # 2 above) wouldn't warrant the same amount of care and caution.

I have high hopes for Hardy, but until then I'll be looking for another distribution whose current version is actually stable and usable.

---

### Post by maybeway36 on 2007-11-11
The release right before an LTS is often the buggiest. I bet Hardy is going to be crazy stable :)

---

### Post by bishop9226 on 2007-11-13
why isnt the firefox hangup issue listed as a known bug?  i mean come on

---

### Post by frodon on 2007-11-13
Because you don't read posts and don't provide workaround links and launchpad entries when posting in this thread.

---

### Post by MikeBenza on 2007-11-13
Cannot suspend on many laptops:

Support (?) thread.  Some workarounds, but not all work: [http://ubuntuforums.org/showthread.php?t=588239](http://ubuntuforums.org/showthread.php?t=588239)

Launchpad (Not sure which to give -- a mod can pick the best one.) [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/159286](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/159286) 
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/156832](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/156832)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/156613](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/156613)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/151857](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/151857)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/149714](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/149714)
...

---

### Post by frodon on 2007-11-14
Thanks MikeBenza for your help, i added your links to the first post.

---

### Post by Sinisterff on 2007-11-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/154613](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/154613) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				There's also a java-fullscreen problem in gutsy that xinerama may be causing: 
[http://ubuntuforums.org/showthread.php?t=611242](http://ubuntuforums.org/showthread.php?t=611242)
[http://ubuntuforums.org/showthread.php?t=613616](http://ubuntuforums.org/showthread.php?t=613616)

Also check the launchpad bug report:
[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/154613](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/154613)

But there are no known workarounds for it yet...

---

### Post by frodon on 2007-11-16
Thanks for your useful feedback Sinisterff, it's now in the first post.

---

### Post by maybeway36 on 2007-11-16
**_Aptitude not handling dependincy autoremoval properly:_**
- Bug report: [https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/128681]("https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/128681")
- Workaround: [http://ubuntuforums.org/showthread.php?t=615196]("http://ubuntuforums.org/showthread.php?t=615196")

---

### Post by maybeway36 on 2007-11-16
Here is the default /etc/apt/apt.conf.d/01autoremove:
```
APT
{
  NeverAutoRemove  
  { 
	"^linux-image.*";  
	"^linux-restricted-modules.*";
	"^linux-ubuntu-modules-.*";
  };

  Never-MarkAuto-Sections
  { 
	"metapackages";
        "restricted/metapackages";
        "universe/metapackages";
        "multiverse/metapackages";
  };
};


```
You need to change it to:
```
APT
{
  NeverAutoRemove  
  { 
	"^linux-image.*";  
	"^linux-restricted-modules.*";
	"^linux-ubuntu-modules-.*";
  };
};


```

---

### Post by frodon on 2007-11-16
You should better open a thread with your workaround and link your thread.
Anyway this is not a gutsy specific bug, the scope of this bug is more wide.

---

### Post by Qinjuehang on 2007-11-17
Blender3D, and some other OpenGL apps get the error

DRM_I830_CMDBUFFER: -22

when switching desktops. There are a lot of matches, so I'm not the only one. I don't know a fix, though. Seems to happen in ATI and Intel cards only. I've been doing hours of research to no avail

---

### Post by Banacek on 2007-11-19
I wanted to delete this but I only see an edit option. Would staff, please, delete this? This post serves no purpose here.

---

### Post by ugm6hr on 2007-11-19
**Long boot time from GRUB to GDM login screen (with no Splash)**
Workaround: [http://ubuntuforums.org/showthread.php?t=581075](http://ubuntuforums.org/showthread.php?t=581075)

Hope this is the kind of thing that you are looking for in this thread - it certainly fixed my Gutsy problem (5 minutes of black screen waiting for GDM to 45 seconds with Splash).

---

### Post by frodon on 2007-11-19
Thanks ugm6hr, i forgot this one in addition the fix is really painless.

Added in first post ;)

---

### Post by Rizado on 2007-11-24
I guess this is sort of a bug, or maybe not a bug but atleast something doesn't work as it should.

In kubuntu right clicking on a archive gives a option to extract using ark, but not rar archives (with rar nonfree installed).
This did work on earlier versions (edgy for sure.) so I guess it's some config file that's not right.

---

### Post by gaurav_anywhere on 2007-11-27
Adobe Reader 8.1.1 doesn't print some secure PDF files correctly on Ubuntu 7.10.  

There is a known bug with GhostScript version "8.61 pre-release" in that it doesn't allow printing to a non PostScript printer from Adobe Reader.  This can be fixed by upgrading to the stable version 8.61 ([http://pages.cs.wisc.edu/~ghost/doc/GPL/gpl861.htm]("http://pages.cs.wisc.edu/~ghost/doc/GPL/gpl861.htm")).

Refer the following bug which is related to this issue:
[https://bugs.launchpad.net/ubuntu/+source/acroread/+bug/145772]("https://bugs.launchpad.net/ubuntu/+source/acroread/+bug/145772")

If you have any questions regarding this issue, please feel free to post your queries and comments on the Adobe Reader User-to-user forums at [http://www.adobeforums.com/cgi-bin/webx/.3bc433df/?@446.joUBhhNQ2RH@]("http://www.adobeforums.com/cgi-bin/webx/.3bc433df/?@446.joUBhhNQ2RH@") or the Official Blog for Adobe Reader at [http://blogs.adobe.com/acroread/]("http://blogs.adobe.com/acroread/") or directly contact gaurav at adobe dot com.

---

### Post by namanbagga on 2007-12-08
This is not quite a bug but is a widespread problem faced by people using old monitors.
If you can't see the usplash screen,the[ fix is here]("http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html")
Sorry if this problem has already been included.I don't mean to post spam on the forum:KS

---

### Post by ugm6hr on 2007-12-28
I found another problem...

**_Error starting GNOME Settings Daemon_**
GNOME bug: [http://bugzilla.gnome.org/show_bug.cgi?id=395488](http://bugzilla.gnome.org/show_bug.cgi?id=395488)
Solution: [http://ubuntuforums.org/showpost.php?p=3776732&postcount=15](http://ubuntuforums.org/showpost.php?p=3776732&postcount=15)

This is a bug in Gnome rather than Gutsy per se, but since it is related to the Gnome version in Gutsy (I think) - I figured it might be relevant (and I have already found 3 threads about the same thing).

---

### Post by gaylapdancer on 2007-12-29
Firefox won't connect to sites:
Type 'about:config' into the address bar (without the quotes).
Type 'ipv6' into the filter bar (without the quotes).
Double-click the only entry left, then restart Firefox.

Synaptic cannot connect to any repositories:
[http://ubuntuforums.org/showpost.php?p=1435629&postcount=15]("http://ubuntuforums.org/showpost.php?p=1435629&postcount=15")
(Thanks handy)

---

### Post by txHarleyMan on 2008-01-04
Hello All,

My wife and I run Gutsy.  I use Gnome and she uses KDE.  When she logs out and I log in, I get errors that say objects in the system tray cannot be found.  Do I want to delete User Switcher, do I want to delete Weather Report .... and so on.  To resolve, I have to reboot.  Just restarting X doesn't fix it.

Has anyone encountered this yet?  I've been looking around and cannot find anything.

Mike

---

### Post by petef0_0 on 2008-01-08
Raid 1 not working correctly is this still a bug in gutsy

Pete

---

### Post by fjgaude on 2008-01-08
> **petef0_0 said:**
> Raid 1 not working correctly is this still a bug in gutsy

Pete

AFAIK, yes, still a bug. Hopefully in the next release in April it will be fixed, Hallelujah.

---

### Post by philinux on 2008-01-09
The bug with flash non free ie the md5sum problem should be included. Lots of threads in beginners forum on this.

One fix is from adobe.
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

Following option1 now gives progress bar and full screen for the first time.

---

### Post by Kzin on 2008-01-10
I'd like ta see this one listed;
[http://ubuntuforums.org/showthread.php?p=3923465](http://ubuntuforums.org/showthread.php?p=3923465)
md5sum error when trying to upgrade/install flash in gutsy.
(This is the firefox fix)
Not really a Gutsy bug, more like Adobe problem or some such, but this thread is a sticky and for a person who needs to go to one place to get up and runnin quick this thread makes a good reference.

---

### Post by frodon on 2008-01-11
I had this issue too however the launchpad bug report says "fix released" so is this fixed or not ?:
[https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890](https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890)

---

### Post by Kzin on 2008-01-11
> **frodon said:**
> I had this issue too however the launchpad bug report says "fix released" so is this fixed or not ?:
[https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890](https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890)

I just did a fresh install yesterday, not fixed.  Its fixed in Hardy Heron apparently, and as the link provided implies it is on hold for Gutsy until they figure out how to get it working with Konqueror and Opera.  =(

---

### Post by frodon on 2008-01-14
Added to first post.

---

### Post by zero-9376 on 2008-01-17
I don't know if this is the right place for this but I didn't know where else to put it so that it might get some attention.
I often have problems with firefox stalling when openning the front page of the ubuntu forums and some other sites although flash sites don't seem to cause this problem for me (use flashblock) so I don't know if this 'workaround' will help with that issue. 
Ussually when my firefox window goes gray I just change to some other app and wait for it to catch back up, a couple of days ago when this happened I accidentally opened firefox and much sooner than usual the original firefox window begain to accept input again. So my little bit of advice is that if the browser is stalling try openning another instance to resolve the issue and get firefox to start responding again.

---

### Post by none-letmebe on 2008-02-22
> **TheExplorer said:**
> **An old problem with Ubuntu that can lead to HDD failure.**
There has been lotsa complains from Linux-users concerning the extensive use of their HDDs due to the default configuration of the subsystem power management ACPI script in Ubuntu. There is also a lot of messages about this bug #59695 which has been known  for about a year already. The problem is: this shell-script (/etc/acpi/power.sh) when switching to battery power management (actual for laptops) executes the command «hdparm -B 1» for all devices. In this mode HDD goes into standby 7,000 times per every 100 hours. All this leads to HDD failure. As a workaround users are suggested to create a shell-script «99-hdd-spin-fix.sh», with a line «hdparm -B 255 /dev/sda» and copy it to: /etc/acpi/suspend.d/, /etc/acpi/resume.d/ and /etc/acpi/start.d/. There is also an alternative workaround: install laptop-mode-tools packet and configure the file /etc/laptop-mode/laptop-mode.conf having specified CONTROL_HD_POWERMGMT=1.

Is this still the default on the latest Ubuntu installs.  I cannot imagine many people wanting to install Ubuntu again after they discover is was responsible for damaging the hard disc.

---

### Post by frodon on 2008-02-22
> **none-letmebe said:**
> Is this still the default on the latest Ubuntu installs.  I cannot imagine many people wanting to install Ubuntu again after they discover is was responsible for damaging the hard disc.This was FUD, this bug was concerning (mainly) the "laptop mode" [COLOR="Red"][SIZE="3"]**_which is not the default ubuntu mode_**[/SIZE][/COLOR] so except if you put your ubuntu system in this mode yourself it is not in laptop mode. In addition the hardware is also a cause of this problem as most of HDDs include hardware protection against this.
Good reading here :
[http://ubuntuforums.org/showpost.php?p=3667508&postcount=2](http://ubuntuforums.org/showpost.php?p=3667508&postcount=2)

---

### Post by odiseo77 on 2008-02-22
Bug: Network Manager has a problem connecting to WPA encrypted wireless networks using the rt2x00 driver (Gutsy's default driver for ralink based wireless cards): [bug at launchpad]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/134962").

Workaround: Either [this one]("http://ubuntuforums.org/showpost.php?p=3588610&postcount=1") or [this one]("http://ubuntuforums.org/showpost.php?p=3595458&postcount=6") should work (I suggest the second one because it was written by me :biggrin:).

---

### Post by revision29 on 2008-03-06
> **fieldstone said:**
> There are some major things that are missing from this list - two, in fact, that I've tried and tried to fix but just can't. They're big enough problems that I've given up on Gutsy for now. Both of them appear seemingly at random, but once they do, they seem to be unfixable. I've tried every fix I could find online.

1. NetworkManager drops my interfaces. At some point in every installation of Gutsy I've had so far (and I've installed it about ten times), Network manager starts saying "no network devices detected" when I click on it, and that's the end of it. I've tried reinstalling the packages, editing its conf files - nothing. I eventually had to switch over to Wicd just to get basic GUI wireless support. 


I am having this same issue and is very annoying.  Also, I don;t know if anyone else is having the same problem (I am too lazy to look at the moment) but there are two rectangles near the top of my screen wherein nothing is being drawn.  In other words there are two black rectangles where there should be color.  Not a LCD dead pixel problem as my primary os does not have this problem.

---

### Post by zds on 2008-03-08
Why isn't this thread part of the discussion of known Gutsy bugs?

[http://ubuntuforums.org/showthread.php?t=587905](http://ubuntuforums.org/showthread.php?t=587905)

This is the random freezing/lock-up issue, and it's a real nightmare for those of us who make the mistake of thinking Gutsy is ready for a production environment (especially one in a remote location).

It's hard to troubleshoot when even a SSH session lasts only ~15 seconds before a hard lock...

---

### Post by ugm6hr on 2008-03-09
> **zds said:**
> Why isn't this thread part of the discussion of known Gutsy bugs?

[http://ubuntuforums.org/showthread.php?t=587905](http://ubuntuforums.org/showthread.php?t=587905)

This is the random freezing/lock-up issue, and it's a real nightmare for those of us who make the mistake of thinking Gutsy is ready for a production environment (especially one in a remote location).

It's hard to troubleshoot when even a SSH session lasts only ~15 seconds before a hard lock...

This thread is for bugs *with known workarounds*.

If you know a fix / solution for a known problem - post both the problem and the fix, and frodon will have a look at adding it.

---

### Post by cacycleworks on 2008-03-11
> **fieldstone said:**
> 1. NetworkManager drops my interfaces. At some point in every installation of Gutsy I've had so far (and I've installed it about ten times), Network manager starts saying "no network devices detected" when I click on it, and that's the end of it. I've tried reinstalling the packages, editing its conf files - nothing. I eventually had to switch over to Wicd just to get basic GUI wireless support.

...

Gutsy just isn't production-ready. At all.

Within the last 10 days, there was an update that ruined (and fixed?) my networking... :|

Machine: Dell D630 intel core duo 
Version: Kubuntu Gutsy x86_64 (was a fresh install when it was released)

Bug: KNetworkManager no longer lists wired interfaces. And also the machine will not connect to an attached LAN. 

Workaround: sudo lshw -C network

This causes the wireless networking icon to changed to the wired one. KNetworkManager now reports "manual mode" and still does not list the wired interface. This cost me a day of lost work, which has the "fuzzy" value of up to $1000 in lost sales for my company. Finding the above command and by chance noticing it miraculously fixed my issue preventing me from performing a fresh install of Fiesty.

More info in this thread: [http://ubuntuforums.org/showthread.php?t=707706](http://ubuntuforums.org/showthread.php?t=707706)

Hoping this helps someone,
Chris

PS - That aforementioned fix: previous to this same update, my Dell could never connect to the Belkin wireless router at my work. I didn't realize this cure until the end of a frazzled day of troubleshooting. So I can at least get on the Net before running the fix.

---

### Post by kml.krk on 2008-03-16
THANKS for this thread. It helped me to solve ALL of my problems - mostly I had issues with audio and video, also with suspending.
Thanks again

---

### Post by rjb26 on 2008-03-20
I had some problems too but I got it solved after looking at this thread.

---

### Post by madcap_magician on 2008-03-20
This may be worth posting for anyone with an HP LaserJet 3020.  It's a really simple fix but it took me a long time to notice the pattern that led to me figuring it out.

[HP 3020 Workaround]("http://ubuntuforums.org/showthread.php?p=4553990#post4553990")

---

