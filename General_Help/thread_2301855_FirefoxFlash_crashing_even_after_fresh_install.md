---
title: "Firefox/Flash crashing even after fresh install"
date: 2015-11-05
forum: General Help
---

### Post by rebeltaz on 2015-11-05
Firefox started crashing on any page using Flash a couple of days ago. I could disable Flash and Firefox quit crashing, but of course the pages wouldn't load properly. 

I was using 10.04LTS (which worked JUST fine up until this) with the latest Firefox and Flash versions installed. I tried removing all traces of both packages completely and reinstalling fresh but still had the same issue - FF crashed on Flash pages. 

Since I couldn't get Ubuntu to upgrade, in desperation, I bit the bullet and wiped the drive installing Ubuntu MATE 15.xx from a fresh download. Straight out of the box, so to speak, with no additional software/addons installed and no changes made to the default installation, Firefox STILL crashes on any page running Flash! 

I have NEVER had this problem before a couple of days ago. I ran memtest (just to be sure) and that came back clean. I don't know what else it could be! HELP!!!!! (My girlfriend is jonesing for her youtube!) Thanks guys.

---

### Post by buzzingrobot on 2015-11-05
How did you install Flash on Mate?

---

### Post by rebeltaz on 2015-11-05
Well... now that you ask... I actually didn't. I just assumed that it would be installed with Firefox and since I could enable/disable Flash before the fresh install and effect the crashing, and since it is still crashing on the same pages, that it must still be firefox/flash related...

---

### Post by kansasnoob on 2015-11-05
The proper way to install flash in Ubuntu is now to install the package 'flashplugin-installer'. You can check to see if it's installed using apt-cache policy:

```
lance@lance-desktop:~$ **apt-cache policy flashplugin-installer**
flashplugin-installer:
  Installed: 11.2.202.540ubuntu0.14.04.2
  Candidate: 11.2.202.540ubuntu0.14.04.2
  Version table:
 *** 11.2.202.540ubuntu0.14.04.2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/multiverse i386 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/multiverse i386 Packages
        100 /var/lib/dpkg/status
     11.2.202.350ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/multiverse i386 Packages
```

That said I've also encountered repeated Firefox crashes that I believe to be flash related, as you can see in my crash logs:

```
lance@lance-desktop:~$ ls /var/crash
_usr_lib_firefox_firefox.1000.crash
_usr_lib_firefox_plugin-container.1000.crash
_usr_lib_firefox_plugin-container.1000.upload
_usr_lib_firefox_plugin-container.1000.uploaded

```

There should be even more but many times apport says that there is not enough system memory for it to complete the crash logs. Sometimes Firefox freezes, sometimes it crashes, a few times the entire desktop has frozen requiring a hard reset.

But I've now narrowed it down to certain sites - like anything Yahoo! I use Yahoo mail and the flash ads apparently cause it to crash. Same with the Yahoo home page or Yahoo news. So I'm using Thunderbird to view my Yahoo mail and avoiding anything Yahoo for the moment which helps, but I've also encountered problems with NBC and MSNBC.

I'm fairly well convinced that it's due to some poorly built flash content that's the responsibility of whoever is producing ads, but I disabled Adblock recently because it was causing other problems. That said Hulu is working fine with the [hal hack]("http://ubuntuforums.org/showthread.php?t=2290589&p=13339045#post13339045") as is CBS and CBS news.

It's exasperating to be sure :mad:

If this persists beyond a few days I may try playing with [Pipelight]("http://ubuntuforums.org/showthread.php?t=2290589&page=4&p=13345702#post13345702") or even [using the Windows versions]("http://community.linuxmint.com/tutorial/view/2028") of Firefox and flash in Wine just to see what happens.

---

### Post by mörgæs on 2015-11-06
Chrome has a flash player built in by default.

---

### Post by monkeybrain20122 on 2015-11-06
> **kansasnoob said:**
> 
There should be even more but many times apport says that there is not enough system memory for it to complete the crash logs. Sometimes Firefox freezes, sometimes it crashes, a few times the entire desktop has frozen requiring a hard reset.

But I've now narrowed it down to certain sites - like anything Yahoo! I use Yahoo mail and the flash ads apparently cause it to crash. Same with the Yahoo home page or Yahoo news. So I'm using Thunderbird to view my Yahoo mail and avoiding anything Yahoo for the moment which helps, but I've also encountered problems with NBC and MSNBC.

I'm fairly well convinced that it's due to some poorly built flash content that's the responsibility of whoever is producing ads, but I disabled Adblock recently because it was causing other problems. That said Hulu is working fine with the [hal hack]("http://ubuntuforums.org/showthread.php?t=2290589&p=13339045#post13339045") as is CBS and CBS news.



Use an adblocker unless you like flash ads. :)

---

### Post by Bucky Ball on 2015-11-06
Install ubuntu-restricted-extras. That will drag in flash. There may be a Mate equivalent though, like mate-restricted-extras, though, so look for that first. I'm not familiar with Mate so can't confirm that.

The other way is to simply install flashplugin-installer.

---

### Post by rebeltaz on 2015-11-06
I did use flashplugin-installer before I reinstalled the system trying to get that fixed, but when I installed MATE I did click a box that installed the "restricted extras" so that may have done that then. I will check the system tomorrow and make sure.

---

### Post by rebeltaz on 2015-11-06
Yeah... flash is installed under Addons so it must have been installed by the "restricted extras"....

---

### Post by Dennis N on 2015-11-06
If you don't find a solution to the problem with Firefox, or to use while you search for one, you could install Chromium Browser and see if it's newer version of Adobe Flash makes a difference (it is using version 19.x, while Firefox is at version 11.x).

Updating Chromium's flash now uses the **adobe-flashplugin** package; you need to enable the Cannonical Partners in Software Sources to access this package. As a bonus it updates the Firefox-compatable flash as well. A two for one deal.

---

### Post by rebeltaz on 2015-11-06
I did install Chromium on the old system and still had issues (I want to think) but I can try again on the new install... I would really rather not use Chromium though...

---

### Post by matt_symes on 2015-11-06
Hi

I may be way off base here as i try to keep well away from flash as a general rule, but try disabling hardware acceleration in Firefox.

You could also try installing the freshplayerplugin and associated libraries to run pepper flash in Firefox. There are tutorials online and i have some notes of what i did somewhere.

Flash is dying anyway and that can only be a good thing ;)

Kind regards

---

### Post by rebeltaz on 2015-11-06
On my own systems I do have flash disabled, but my gf needs it for youtube. From what I've read, youtube plays through html5 if flash is not present, but her system is old and doing it that way causes stuttering/pausing video. If it weren't for that, I wouldn't be caring about this (non)issue at all! 

I'm willing to try (almost) any ideas.... turning off hardware acceleration didn't have any effect. Still crashes on flash sites. If it matters - [www.Listia.com](www.Listia.com) is the site I am using as a test page since this is the main page she visits so it HAS to work on this page, but youtube does it too.

---

### Post by matt_symes on 2015-11-06
Hi

Did you try disabling hardware acceleration in flash as well as in the browser ?

[https://helpx.adobe.com/flash-player/kb/video-playback-issues.html#main_Solve_video_playback_issues](https://helpx.adobe.com/flash-player/kb/video-playback-issues.html#main_Solve_video_playback_issues)

That may not explain why chrome is crashing as well but it's worth eliminating.

Have you tried playing a flash video file outside of a browser ?

Kind regards

---

### Post by rebeltaz on 2015-11-06
I didn't know "hardware acceleration" was even a thing in flash, but it's a moot point anyway... I go to that page on her computer and it doesn't show the little icon I am supposed to right-click on because, well... flash is disabled. If I enable flash to try and do it.... you guessed it - the page crashes.

Just so I could say "I did it" I installed chromium-browser - which comes with adobe-flashplugin by default. When I try to run that via the GUI, it tries to open and then just silently crashes. To try and see what is happening, I ran chromium-browser from the command line and it exited with "illegal instruction (core dumped)"...

I swear I can't have normal problems!

Oh... I haven't tried playing a flash file outside of the browser. I assume you mean an swf file? I'll try that now and report back. 

-=[ edit ]=-
umm.... OK... how do I do that outside of the browser?

---

### Post by matt_symes on 2015-11-06
Hi

> **rebeltaz said:**
> I didn't know "hardware acceleration" was even a thing in flash, but it's a moot point anyway... I go to that page on her computer and it doesn't show the little icon I am supposed to right-click on because, well... flash is disabled. If I enable flash to try and do it.... you guessed it - the page crashes.

I'm sorry but i had a little chuckle about this. Sometimes technology can be darned right awkward.

> Just so I could say "I did it" I installed chromium-browser - which comes with adobe-flashplugin by default. When I try to run that via the GUI, it tries to open and then just silently crashes. To try and see what is happening, I ran chromium-browser from the command line and it exited with "illegal instruction (core dumped)"...

Please post the output of these commands.

```
sudo lshw -C processor
```

```
cat /proc/cpuinfo
```

> I swear I can't have normal problems!

Oh... I haven't tried playing a flash file outside of the browser. I assume you mean an swf file? I'll try that now and report back.

I was referring to an flv file.

**EDIT:**

Have you tried gnash ?

```
matthew-laptop:/home/matthew:1 % acse shockwave
browser-plugin-gnash - GNU Shockwave Flash (SWF) player - Plugin for Mozilla and derivatives
gnash - GNU Shockwave Flash (SWF) player
gnash-common - GNU Shockwave Flash (SWF) player - Common files/libraries
gnash-cygnal - GNU Shockwave Flash (SWF) player - Media server
gnash-dbg - GNU Shockwave Flash (SWF) player - Debug symbols
gnash-dev - GNU Shockwave Flash (SWF) player - Development files
gnash-doc - GNU Shockwave Flash (SWF) player - API documentation
....

```

No idea what it's like though.

**EDIT 2:**

What version of flash are you using ? Have you recently had a flash update ? If so, have you tried rolling back to the version that worked for you to see if it works ?

Bear in mind that this is a security risk but it will show if the update (if there was one) is the problem.

**EDIT 3:**

Try this....

Close all browsers.

From the terminal.

```
echo EnableLinuxHWVideoDecode=0 | sudo tee -a /etc/adobe/mms.cfg
```

Enter your password as usual.

Double check the file was created.

```
file /etc/adobe/mms.cfg
```

Open the browser, enable flash and go to a flash site.

Kind regards

---

### Post by rebeltaz on 2015-11-06
```

sudo lshw -C processor

  *-cpu                   
       product: AMD Sempron(tm)   3000+
       vendor: Advanced Micro Devices [AMD]
       physical id: 0
       bus info: cpu@0
       version: 6.10.0
       size: 2GHz
       width: 32 bits
       capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow 3dnowprefetch vmmcall

```

```

cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 6
model		: 10
model name	: AMD Sempron(tm)   3000+
stepping	: 0
cpu MHz		: 1999.679
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow 3dnowprefetch vmmcall
bugs		: fxsave_leak sysret_ss_attrs
bogomips	: 3999.35
clflush size	: 32
cache_alignment	: 32
address sizes	: 34 bits physical, 32 bits virtual
power management: ts

```


OK... I ran an flv file and it played [somewhat] ok through VLC. The trouble with that is that that file, as well as an avi I tested everyone looked like smurfs! I had to enable color-correction and manually correct that and even then I wasn't able to get it perfect...


I haven't tried gnash, but I guess I can.

The flash version is 11.2 r202. I'm not sure when her original system updated, but I would figure that it probably did since that is probably what caused all of this. The problem is that now that I have "upgraded" the OS, how would I rollback to an older version?

The command for mms.cfg didn't work because there isn't an /etc/adobe directory, so I created that directory, reran the command and tried the browser - crashed.

---

### Post by Dennis N on 2015-11-06
> The problem is that now that I have "upgraded" the OS, how would I rollback to an older version?

There is an archive of older versions:

[https://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html#main_Archived_versions](https://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html#main_Archived_versions)

Just copy the older one to the flash player location, replacing the new one.

---

### Post by matt_symes on 2015-11-06
> **rebeltaz said:**
> ```

sudo lshw -C processor

  *-cpu                   
       product: AMD Sempron(tm)   3000+
       vendor: Advanced Micro Devices [AMD]
       physical id: 0
       bus info: cpu@0
       version: 6.10.0
       size: 2GHz
       width: 32 bits
       capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow 3dnowprefetch vmmcall

```

```

cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 6
model		: 10
model name	: AMD Sempron(tm)   3000+
stepping	: 0
cpu MHz		: 1999.679
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow 3dnowprefetch vmmcall
bugs		: fxsave_leak sysret_ss_attrs
bogomips	: 3999.35
clflush size	: 32
cache_alignment	: 32
address sizes	: 34 bits physical, 32 bits virtual
power management: ts

```

That's a dinosaur you have there. From the pedia..

```
Barton (130 nm)

    L1-Cache: 64 + 64 KiB (Data + Instructions)
    L2-Cache: 512 KiB, fullspeed
    MMX, 3DNow!, SSE
    Socket A (EV6)
    Front side bus: 166 MHz &#8211; 200 MHz (FSB 333 &#8211; 400)
    VCore: 1.6 &#8211; 1.65 V
    First release: September 17, 2004
    Clockrate: 2000&#8211;2200 MHz (Sempron 3000+, Sempron 3300+)

```

The illegal instruction error would suggest either a CPU or GPU instruction was called created a processor exception and crashed the browser.

That processor is old and only has a small number processor feature flags. I suspect that the newest version of flash is now calling an instruction that you CPU or GPU does not have; hence the crash.

It would be interesting to know the instruction that crashed the browser and you could find that from the core dump however it would not provide a fix.

As usual, adobe release notes are sh*cough*t.

BTW: Installing flash using the package flashplugin-installer will pull in the newest version of flash.
> 
 WARNING: Installing this Ubuntu package causes the Adobe Flash Player
 plugin to be downloaded from the Adobe website. The distribution licence
 of the Adobe Flash Player plugin is available at [www.adobe.com](www.adobe.com) and
 installing this Ubuntu package implies that you have accepted the terms of
 said licence.

So realistically you looking at installing a previous version of flash from the flash web site. 

However, this is a security risk. I'll say that again just to make my point. This is a security risk !

You could try the shockwave version of flash (the GNU version) but i have not idea whether it cuts the mustard or not. You'll have to try it.

To install an old version of flash you need to use adobe archive. Some links for you.

[https://helpx.adobe.com/flash-player/kb/install-previous-version-flash-player.html](https://helpx.adobe.com/flash-player/kb/install-previous-version-flash-player.html)

[https://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html#Flash%20Player%20archives](https://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html#Flash%20Player%20archives)

You may want to look at...

[https://helpx.adobe.com/flash-player/release-note/release-notes-developer-flash-player.html#main_system_requirements](https://helpx.adobe.com/flash-player/release-note/release-notes-developer-flash-player.html#main_system_requirements)

You also have to uninstall flash from her laptop and then uninstall flashplugin-installer so an update won't trash you hard work as i think this may be hard work.

I don't think you can even download an old version of Ubuntu to get an older version of flash as the installer will pull in the newest version of flash when you try to install it. 

Good luck :)

**EDIT**

If i've missed something, someone will pipe up because the only thing that makes me wonder is that it's also happening in Chrome as well. 

Has the graphics subsystem been upgraded recently ? Did you have to apply colour correction before the crashes ?

Kind regards

---

### Post by rebeltaz on 2015-11-06
I downloaded and installed a flash version two releases back (11.2.202.521) and it still crashes even with that. 

I did not have to apply color correction before I installed the fresh OS install. By graphics subsystem, do you mean hardware? If so, no... there has been no hardware changes in the past three years. 

Let me go try gnash... I'll be back

---

### Post by matt_symes on 2015-11-06
Hi

If gnash does not work....

Have you tried rolling back Firefox itself ?

If that makes no difference and it still crashes then it may be in one of the libraries all these plugins are calling.

Kind regards

---

### Post by rebeltaz on 2015-11-06
I installed gnash and mozilla-plugin-gnash.... when I go to Firefox... it doesn't show up under Addons...

-=[edit]= no I haven't tried rolling back firefox. I'll try that next. Have I mentioned lately how much I HATE "updates"!?!

---

### Post by matt_symes on 2015-11-06
Hi

> **rebeltaz said:**
> I installed gnash and mozilla-plugin-gnash.... when I go to Firefox... it doesn't show up under Addons...

It should show up as shockwave flash (i think :D).

**EDIT:**

You can also try the pepper flash plugin for Firefox.

Here's a link

[http://www.webupd8.org/2015/01/fresh-player-plugin-sees-new-release.html](http://www.webupd8.org/2015/01/fresh-player-plugin-sees-new-release.html)

It's what i'm using.

Kind regards

---

### Post by rebeltaz on 2015-11-06
I forgot to uninstall adobe first.... Uninstalled adobe flash as well as gnash and reinstalled gnash. WORKS!!!! WOO HOO!!!  My girlfriend thanks you!

---

### Post by matt_symes on 2015-11-06
Hi

> **rebeltaz said:**
> I forgot to uninstall adobe first.... Uninstalled adobe flash as well as gnash and reinstalled gnash. WORKS!!!! WOO HOO!!!  My girlfriend thanks you!

You're welcome buddy :)

Kind regards

---

