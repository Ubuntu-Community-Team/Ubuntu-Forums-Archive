---
title: "nvidia driver causes lock-ups, black flashes, hangs (continued)"
date: 2007-10-18
forum: General Help
---

### Post by hotani on 2007-10-18
This is a continuation of [this thread from the gutsy forum](http://ubuntuforums.org/showthread.php?t=566422) which is now closed. [Another thread](http://ubuntuforums.org/showthread.php?t=398821) in the hardware and laptops section refers to the same issue.

**Problem description**:
In some hardware configurations, using recent versions of the nvidia driver with 7xxx series cards causes random glitches:
1- the screen may flash black for an instant then return
2- the screen will hang with nothing responding but the mouse cursor. This usually lasts about 10-20 seconds, and on returning, the CPU monitor shows 100% activity for the lost time.

Usually the problem will not emerge until after several minutes of use. Once it starts it will continue to worsen until logging out or doing a ctrl+alt+backspace.

**FIX**
Although there is no sure fix for this until nvidia updates the driver, one alternative is to install xgl as outlined below (from [this post](http://ubuntuforums.org/showpost.php?p=3534701&postcount=33) in the previous thread):

> 
Someone on the nV forums pointed out an obvious (in retrospect) workaround for lockups when using nvidia with compiz - use XGL.
After installing the xserver-xgl package (I was pleased to find that no extra setup was required), I've been able to run compiz without any of the flickering, stalling, or lockups I experienced before. The performance is decent too - although I see some tearing, apparently due to no sync-to-vblank, even though I have it enabled. Does anyone knowhow to remedy that? Some effects, like dimming (e.g. System->Quit) is actually faster.
Unfortunately, XGL makes video playback awful. Anyone have a workaround for that?
Oh - and suspend/resume still works


Installing and using XGL:
1- in synaptic, search for "xgl", then install "xserver-xgl"
2- log out and back in again to use

Having experienced this bug first hand, I can report that the XGL fix seems to remedy the problem. There are some drawbacks to this as it causes problems with video playback in some cases.

---

### Post by mrfuzzemz on 2007-10-18
I tried using XGL and  there were indeed no flashes or lockups.  The drawing is not consistent with XGL, though.  I decided to disable XGL after using it for hours and now notice no  issues with AIGLX--Could it be that there is a dependency installed for XGL that fixed the problem?  I will report more as soon as I have used to the system for a few hours/days.

What should really happen is Ubuntu, Dell and others bugging NVidia about this so they fix this issue...  NVidia may be left behind as AMD is to soon open-source ATI drivers.

---

### Post by jlacroix on 2007-10-18
Possible problem with Turbocache?

I have a 7 series Geforce with no problems whatsoever, past or present. I don't have Turbocache on my card, thankfully.

---

### Post by nschembr on 2007-10-18
ubuntu 7.10 gutsy - dist-upgrade
With compiz turned on the nvidia drivers slows down and then produces a black window around any new application.  With compiz turned off no errors.

A quick google search has this issue reported as a memory leak.
hardware
Toshiba p25-s526
p4 3Ghz with ht
1G ram
NV34M [GeForce FX Go5200 64M]

As a side note, this new NVidia driver is not seeing the external display the same way.  Display 1 and 2 are swapped.  The external resolution was not detected correctly.

---

### Post by mrfuzzemz on 2007-10-18
> **jlacroix said:**
> Possible problem with Turbocache?

I have a 7 series Geforce with no problems whatsoever, past or present. I don't have Turbocache on my card, thankfully.

Nope.  Mine is 512MB solid dedicated memory GeForce 7700.  Would be nice if I could somehow *reduce* the amount of memory used to save battery life, but that's asking too much.  I do like Sony VAIO SZ idea with hybrid graphics cards.  You can switch between integrated graphics and the dedicated NVidia graphics for performance/endurance trade offs.  That's off topic, though. Pardon me.

I will post again tonight with progress in installing, but disabling XGL(in hopes of an XGL dependency sorting things out).

---

### Post by jlacroix on 2007-10-18
Is it only the integrated laptop GPU's that are causing this then?

---

### Post by mottipython on 2007-10-18
I have a GeForce 7300 LE that i could not get working with the proprietary drivers, i tried to install older driver but it didn't work.

---

### Post by mrfuzzemz on 2007-10-18
> **mottipython said:**
> I have a GeForce 7300 LE that i could not get working with the proprietary drivers, i tried to install older driver but it didn't work.

The topic of this thread is not problems installing NVidia drivers, but I will point you in the right direction:

If you are having difficulty with Ubuntu's packaged NVidia drivers, download and install Envy.  It will download, install, and configure your driver automatically. You can find that here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by mrfuzzemz on 2007-10-18
Turns out I was just optimistic and wrong.  I've e-mailed NVidia about it and was surprised to get a response within an hour.  Hopefully they'll be able to find a solution to this or release an updated driver.  I would suggest you send your nvdia-bug-report to the linux support e-mail as well by typing:
```

sudo nvidia-bug-report.sh
```

into a terminal and attaching the output file in an e-mail to [linux-bugs@nvidia.com]("mailto:linux-bugs@nvidia.com") explaining your and our situation.

Maybe that way the problem will be more easily realized and identified.

---

### Post by rickggreen on 2007-10-19
The problem has many symptoms, freezes,lockup, etc. The problem happens to [COLOR="Red"]multi-core cpus[/COLOR] and [COLOR="Red"]7XXX cards/GPUs[/COLOR]. Software running at the time has nothing to do with it. Nvidia is aware of the problem and has admitted there is a regresssive bug. Nvidia's solution is to revert to 100.14.09 driver or earlier. Our repros have 9639 and I have been running it now for 10 or so days, no problems. 

This is not just a Gutsy problem, it affects all SMP distros, to users running multi-core CPUs (AMD X2 and Intel DUOs and QUADs) and 7XXX nvidia gpu. Some later run  6XXX GPUs might also be affected.

---

### Post by janbockaert on 2007-10-20
> 

Installing and using XGL:
1- in synaptic, search for "xgl", then install "xserver-xgl"
2- log out and back in again to use

Having experienced this bug first hand, I can report that the XGL fix seems to remedy the problem. There are some drawbacks to this as it causes problems with video playback in some cases.

This is why Opensuse uses XGL when you enable compiz. But other than in Ubuntu, XGL + Nvidia performs without problems on Opensuse.

The bad XGL performance seems to be an Ubuntu problem, and not an XGL-problem.

Something for Hardy?

---

### Post by mrfuzzemz on 2007-10-20
> **rickggreen said:**
> The problem has many symptoms, freezes,lockup, etc. The problem happens to [COLOR="Red"]multi-core cpus[/COLOR] and [COLOR="Red"]7XXX cards/GPUs[/COLOR]. Software running at the time has nothing to do with it. Nvidia is aware of the problem and has admitted there is a regresssive bug. Nvidia's solution is to revert to 100.14.09 driver or earlier. Our repros have 9639 and I have been running it now for 10 or so days, no problems. 

This is not just a Gutsy problem, it affects all SMP distros, to users running multi-core CPUs (AMD X2 and Intel DUOs and QUADs) and 7XXX nvidia gpu. Some later run  6XXX GPUs might also be affected.


I just wanted to let you know that I observe this bug while using the 100.14.09 and 9639 drivers.  I've installed NVidia's latest driver, 100.14.23, released a couple days ago and have been running okay for the past hour.  The change list for the new driver does not mention anything related to this as far as I can tell so I expect some instability soon.

---

### Post by NTolerance on 2007-10-20
> **mrfuzzemz said:**
> I just wanted to let you know that I observe this bug while using the 100.14.09 and 9639 drivers.  I've installed NVidia's latest driver, 100.14.23, released a couple days ago and have been running okay for the past hour.  The change list for the new driver does not mention anything related to this as far as I can tell so I expect some instability soon.

If this new driver helps I'd really like to know how to install it properly so that it integrates with apt and does not break during kernel upgrades.

---

### Post by mrfuzzemz on 2007-10-20
> **NTolerance said:**
> If this new driver helps I'd really like to know how to install it properly so that it integrates with apt and does not break during kernel upgrades.

Well I'm still testing it now.  You will not be able to install it without it breaking during kernel upgrades until ubuntu adds it to the repos.  You can install it easily with envy, I believe.

---

### Post by mrfuzzemz on 2007-10-20
I've now had flashes and hard lock-ups while using the latest driver and even while using this command:
```
while true; do glxinfo >/dev/null; sleep 5; done
```

This means we are still searching for a sure fix to the problem.

---

### Post by emperon on 2007-10-21
A new driver 100.14.23 is availble. I've mailed to Alberot he said he is going to put it envy very soon. For the time being try the following

boot with nosmb option once
then boot normally. This made my freezes occuring less frequently.

Also when you got freezes change your refresh rate to some other value from nvidia-settings and revert it back. This also buys time

---

### Post by mrfuzzemz on 2007-10-21
> **emperon said:**
> A new driver 100.14.23 is availble. I've mailed to Alberot he said he is going to put it envy very soon. For the time being try the following

boot with nosmb option once
then boot normally. This made my freezes occuring less frequently.

Also when you got freezes change your refresh rate to some other value from nvidia-settings and revert it back. This also buys time

100.14.23 is the driver I mentioned testing a few posts back--it is not fixed for the black flash and lock-up issue.  Also, some systems don't allow custom changes in refresh rate.  Gnome allows me to set on 50Hz (which I don't think is what it should be) and NVidia has options for automatic or 60Hz (what I think it should be).  If I set it to 60Hz in NVidia I am for some reason now only able to select 50Hz and 54Hz (not 60Hz).

---

### Post by libos on 2007-10-21
Moving back to version 100.14.09 seems to work for me. I have been running my system with the version of driver for more than 5 hours now. No more lock ups.  :guitar: 

I have a 7300 LE graphics card and before this i have several lock ups in one day.

I can't seems to find a direct instructions on how to get the version 100.14.09 installed with out using the apt-get. Information were everywhere. Finally i manage to install it. Not hard to do. :)

The steps are here:
[http://bsling.blogspot.com/2007/10/installing-different-nvidia-video.html](http://bsling.blogspot.com/2007/10/installing-different-nvidia-video.html)

---

### Post by Wayetender on 2007-10-21
I have this problem... Core 2 Duo, GeForce Go 7900 GS. It started with just black flickers and momentary freezes (could move the mouse but window action lagged for about 10 seconds), and occasional total lockups. But now, it seems every 15 minutes I get a lock up.

I tried xgl, older nvidia driver, just using metacity to no avail. Should I just windows until nvidia releases an updated driver? Very frustrating, I must say..

---

### Post by yostral on 2007-10-21
Odd, I have a Core 2 Duo too, a Geforce Go 7900 GS, gutsy from tribe 1 and with nvidia driver 100.14.19 since it's in the repos, but I've never had any freeze or lockup. :/

But with compiz I'm unable to play a video on the Xv output. I need to use mplayer with the GL output, otherwise I only have pink and black lines on the video.

---

### Post by jazzgossen on 2007-10-23
I have an Asus N6600 and a single-core AMD Athlon XP CPU, and I get hard freezes whenever I use the nvidia driver, either the one provided from the repos and the one provided by Envy. The system freezes after a couple of seconds after I log in, usually in the middle of a screen draw (I get half-filled windows). Using the nv driver, everything works fine. I havent't voluntarily enabled compiz, but I'm not sure whether Ubuntu enables it automatically or not. Is this the same problem you are talking about?

---

### Post by mrfuzzemz on 2007-10-23
> **jazzgossen said:**
> I have an Asus N6600 and a single-core AMD Athlon XP CPU, and I get hard freezes whenever I use the nvidia driver, either the one provided from the repos and the one provided by Envy. The system freezes after a couple of seconds after I log in, usually in the middle of a screen draw (I get half-filled windows). Using the nv driver, everything works fine. I havent't voluntarily enabled compiz, but I'm not sure whether Ubuntu enables it automatically or not. Is this the same problem you are talking about?

You may want to try to disable compiz in Advanced Desktop Effects settings just to be sure that it isn't just compiz crashing your system.

---

### Post by jazzgossen on 2007-10-23
Currently (using the nv driver) if I go to System/Settings/Theme/Visual effects, it says that the effects are disabled. Would they be automatically enabled when I use the nvidia driver instead? If so, is there a console way to disable compiz? Because the computer freezes before I get a chance to change any settings after I log on with the nvidia driver running.

---

### Post by mrfuzzemz on 2007-10-23
> **jazzgossen said:**
> Currently (using the nv driver) if I go to System/Settings/Theme/Visual effects, it says that the effects are disabled. Would they be automatically enabled when I use the nvidia driver instead? If so, is there a console way to disable compiz? Because the computer freezes before I get a chance to change any settings after I log on with the nvidia driver running.

Maybe you could try adding the following to your xorg.conf:

```
Section "Extensions"
Option "Composite" "Disable"
EndSection
```

---

### Post by mbeierl on 2007-10-24
Do others see compiz.real consuming more and more memory with the nvidia drivers?  I can't use my system for more than 4 hours due to some sort of memory leak:

```
Mem:   3096320k total,  3064944k used,    31376k free,     8992k buffers
Swap:  1550264k total,      212k used,  1550052k free,  1031528k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                               
14283 mark      20   0 1273m **1.0g** 403m S    2 33.2   5:07.11 compiz.real                                                            

```

If I kill compiz.real the memory does NOT get freed!  It still shows in use, but no program "owns" that much memory.

If this is a new bug, lmk and I'll open a new thread for it.

---

### Post by pescez on 2007-10-24
hi, i'm into this same trouble, i'm using nvidia 100.14.23 now with AddARGBVisuals, AddARGBGLXVisuals and glx module commented in xorg.conf (to avoid gnome to boot  loading compiz features) and xserver-xgl installed now to be able to use my pc.
Before installing xserver-xgl i used to suffer of flickering and hang-ups unless using nv, but now it seems all right except for one thing that may be easy to solve... but i need your help to succeed!
When i enable compiz the screen becomes totally light-brown (that background ubuntu color) and i can't see anything. But the cube works, the scale effect works and i can even launch programs ...in a blind way :D. it is just all invisible. when i close the session (blind way pressing where i know buttons are) in that half-moment the session takes to close i can see perfectly my desktop that then disappears.
maybe some compiz option to disable? 
please help me... it seems that at least i am one step far from getting my cube back! :D

edit FYI my card is a geforce go 7200 on a dv6000 hp pavilion laptop using a fresh gutsy install

edit2: got back to 100.14.09 everything works fine now but the "black windows bug" so known among nvidia users.

---

### Post by kristjans on 2007-10-27
I reverted to driver 1.0-9755 and it doesn't lock up any more and I also do not get the black window bug on this version (graphics card is Asus nVidia EN6200TC).

[list]
[*][x86](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html)
[*][x86-64](http://www.nvidia.com/object/linux_display_amd64_1.0-9755.html)
[/list]

Sometimes I get some weird permission denied problems with this (1.0-9755) driver. For that, I use this command:
```
chmod 0666 /dev/nvidia* && chown root /dev/nvidia*
```

However, it seems to lose its effect by the time I open the next application. But a temporary fix is better than no fix! :)

---

### Post by hotani on 2007-10-29
I just got the hang using XGL, so apparently that is not a complete fix. I've been running for several days with no problems so hopefully that was an isolated incident.

---

### Post by kr4m on 2007-11-03
just to let you guys know, that I have a single core CPU with a FX 5200 and i also get the screen flashes, so it doesn't look isolated to multicore CPUs

---

### Post by anarchypower on 2007-11-05
Just letting you guys know:
Installing xserver-xgl solved the black flashes on my laptop. My laptop is a dell XPS m1710 with a  Intel Core 2 Duo T7200 and a NVIDIA GeForce Go 7900 GTX. So if anyone has a system like mine, be aware;)

On the other hand I am experiencing some other problems, but I'm not sure if I'm the only one with the problem. I have already created a thread here on the forum but I haven't realy received much answers... 
here's the link:  [http://ubuntuforums.org/showthread.php?p=3712137#post3712137]("http://ubuntuforums.org/showthread.php?p=3712137#post3712137")

Maybe someone has the same problem and found a solution...

---

### Post by NTolerance on 2007-11-12
Anyone have any idea how often the new NVidia drivers show up in the repos?  This bug completely cripples my Ubuntu installation.  I tried using Envy to install the latest NVidia drivers, but this causes the Desktop Effects control panel to get confused.  It runs the restricted drivers manager which tries to install the old, buggy NVidia drivers.

---

### Post by NTolerance on 2007-11-13
> **libos said:**
> Moving back to version 100.14.09 seems to work for me. I have been running my system with the version of driver for more than 5 hours now. No more lock ups.  :guitar: 

I have a 7300 LE graphics card and before this i have several lock ups in one day.

I can't seems to find a direct instructions on how to get the version 100.14.09 installed with out using the apt-get. Information were everywhere. Finally i manage to install it. Not hard to do. :)

The steps are here:
[http://bsling.blogspot.com/2007/10/installing-different-nvidia-video.html](http://bsling.blogspot.com/2007/10/installing-different-nvidia-video.html)

Not sure how I glossed over this earlier, but this sounds like the best solution.  Feisty + Compiz worked beautifully on my 7400 go, so I'm hoping that being able to properly install the older driver will fix this in a clean way.

---

### Post by libos on 2007-11-14
I have been using that workaround/ solution ever since. I will not going to change it anymore. Don't want to fix something that is already fixed.

---

### Post by NTolerance on 2007-11-16
> **libos said:**
> I have been using that workaround/ solution ever since. I will not going to change it anymore. Don't want to fix something that is already fixed.

I did a fresh install of Gutsy, updated everything, then I installed some compiling stuff like build-essential and the kernel headers (not sure if this is really necessary to install the NVidia drivers), then installed the older NVidia driver you posted.  Restricted drivers manager didn't give me any crap when I logged in, so there was no need for me to edit the text file mentioned in your guide.  Desktop Effects initially did freak out and I lost my window borders, but then I just disabled/enabled Desktop Effects and now everything is working great.  No flickering or crashing and it seems that these older NVidia drivers have proper suspend support, which is nice.  Thanks again.

---

### Post by libos on 2007-11-16
Glad the workaround works for you too.

---

### Post by Baptiste on 2007-11-17
It seems that the beta driver of nvidia released yesterday fixes the problem. I didn't try it yet, but here is the changelog :

"Fixed stability problems with some GeForce 6200/7200/7300 GPUs multi-core/SMP systems."

You can get the version 169.04 here : [http://www.nvidia.com/object/linux_display_ia32_169.04.html](http://www.nvidia.com/object/linux_display_ia32_169.04.html)

---

### Post by BoardDWorld on 2007-11-20
> **Baptiste said:**
> It seems that the beta driver of nvidia released yesterday fixes the problem. I didn't try it yet, but here is the changelog :

"Fixed stability problems with some GeForce 6200/7200/7300 GPUs multi-core/SMP systems."

You can get the version 169.04 here : [http://www.nvidia.com/object/linux_display_ia32_169.04.html](http://www.nvidia.com/object/linux_display_ia32_169.04.html)

I have been using it since last night and can confirm that it "doesn't" resolve the issue.

---

### Post by Baptiste on 2007-11-20
Well, it works for me. But they are only beta drivers, maybe it will work for you later.

---

### Post by mrfuzzemz on 2007-11-20
It has locked, flashed and crashed on me for days now.  I've sent a message to NVidia's linux debugger(s) and I think you should all do the same.

---

### Post by Nunu on 2007-11-20
I am running a Nvidia GeForce 7600 GT with 512 meg on my P4 HT desktop with Duel Heads and I also have Compiz installed and have had no issues with it using the NVIDIA-New driver from the Restricted Drivers. Cube is smooth as silk, Window Wobble is fast and smooth, menu animation is brilliant. 

Maybe i am just lucky.

---

### Post by Paul S on 2007-11-20
> **mrfuzzemz said:**
> It has locked, flashed and crashed on me for days now.  I've sent a message to NVidia's linux debugger(s) and I think you should all do the same.

I have a 7300 and it seems fixed here.  Are you sure you installed it correctly.  Check your driver version and see if it's right:

# dmesg | grep NV
[   39.429079] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.04  Wed Nov 14 16:01:30 PST 2007

---

### Post by Baptiste on 2007-11-20
As a matter of fact, I've too a geforce 7300 GO. So, the problem may not be fixed on all the graphic cards.

---

### Post by mrfuzzemz on 2007-11-20
It's certainly 169.04, and I'm running a GeForce Go 7700 512MB.

---

### Post by hotani on 2007-11-30
I got so sick of "Big Desktop" in XGL I turned it off. About 5 minutes into my session I started getting black flashes. Hard to decide which is worse. I suppose having everything show up "in the crack" with big desktop is not quite as bad as hanging every 5 to 10 seconds and being unable to work.

---

### Post by zippy028 on 2007-11-30
I was able to alleviate the lock-ups by installing the 100.14.09ver. driver

See this thread

[http://ubuntuforums.org/showthread.php?t=594196](http://ubuntuforums.org/showthread.php?t=594196)

---

### Post by BoardDWorld on 2007-12-01
The following fixed the screen flashes and system freezes for 30 straight days without problems until I installed the current 169.07 driver using ENVY.
The problem, for those who don't know, is caused by the nVidia PowerMizer (in the nVidia Driver) changing the clock speeds from 2D to 3D. People have been blaming Compiz but Compiz just brings out this flaw in the driver because of the frequent change between the 2D and 3D clocks. The following fix locks your video card to the single 3D clock speed.


The fix below is for the nVidia driver from Ubuntu only(Synaptic or clicking the Restricted Drivers check box etc). 

Open nvidia-kernel-nkc using Terminal with the following command:

```
sudo gedit /etc/modprobe.d/nvidia-kernel-nkc
```

Copy & Paste the following at the bottom in a new line:

```
options nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222"
```

Save the file and restart your PC.


Source:
[http://www.nvnews.net/vbulletin/showthread.php?t=96673&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=96673&page=2)

For those using ENVY to install their drivers or are downloading them from nVidia and installing them manually (there's no point doing it manually, use ENVY) scroll further down the page.

Notes: As said this fix locks the video card to the 3D clock, for some this could cause heat problems and greatly reduce battery life. For myself I don't have heat problems at all. It sits at 58degrees in both the 2D without this fix and at the constant 3D clock speed with this fix. Battery life, when I use it on battery to that extent, is reduced by 10-20 minutes which still gives me over 1 hour. This makes sense as even though it's at the 3D clock it really only starts causing heat/using power when it gets used/stressed, eg playing games. No negative reports have been made on the nvniews forum and I keep pretty frequent tabs on it.

---

### Post by hotani on 2007-12-03
> 
Anyway, so in ubuntu you'd have to add this:
Code:

options nvidia_new NVreg_Mobile=1 NVreg_RegistryDwords="PerfLevelSrc=0x2222"

in /etc/modprobe.d/nvidia-kernel-nkc
Mobile is probably not needed but I like having it to check that the arguments actually worked.


This is NOT a fix. On my system it made no change. 

I am back to using XGL for now, but will soon try downgrading the driver.

---

### Post by hotani on 2007-12-04
I seem to have a somewhat stable, and easy fix. This is what I did yesterday and the system has been running smooth for several hours with no hangs or flashes.

From Synaptic:
1- removed nvidia-glx-new
2- installed nvidia-glx

nvidia-glx does not seem to support desktop effects, but no loss. My system is running stable and that's what matters. Plus there is no more "Big Desktop" mode from using XGL.

---

### Post by BoardDWorld on 2008-01-11
For those using ENVY to install their drivers or are downloading them from nVidia and installing them manually you will need to place the option below:

```
options nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222"
```

Here:

```
sudo gedit /etc/modprobe.d/options
```

For the fix to take effect...

**hotani**, this "will" help anyone "with this problem" which is screen flashes/system locks caused by the video card alternating from 2D to 3D clock speeds. It has no option but to fix the problem as it locks it to the 3D clock speed. If this doesn't help you you have different problem.


Edit: Thought I better to remind everyone to remember to test each time they update their driver to see if the problem is resolved. You can do this by opening options again as above and place a # in front as below then restart your PC.

```
# options nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222"
```

Of course if it's still not fixed just remove the hash...

---

### Post by pescez on 2008-02-19
it seems to have solved the issue for me... thank you so much.
For informations:
Ubuntu gusty gibbon i386 with kernel 2.6.24,
GPU GeForceGo 7200 on HP pavilion dv6146eu laptop,
 Nvidia drivers 169.09

i'm still keeping my eye on temperature to see if and how much it's gonna change.

---

### Post by phenest on 2008-04-11
I only ever had problems with Compiz. Not needing all those nice effects, I switched to Metacity's compositing manager as I needed it for AWN. The flashes stopped until a few days ago. I think since about kernel -12 the flashes started again. Before I upgraded to a 7950 GTX, I had a Quadro 3500 which had the same problem.

---

### Post by phenest on 2008-04-11
> **anarchypower said:**
> Just letting you guys know:
Installing xserver-xgl solved the black flashes on my laptop. My laptop is a dell XPS m1710 with a  Intel Core 2 Duo T7200 and a NVIDIA GeForce Go 7900 GTX. So if anyone has a system like mine, be aware;).

I'm trying this solution. I have a Dell Precision M90 which has the same motherboard as the M1710

---

### Post by eznet on 2008-06-22
Since installing xserver-xgl, I have not seen the 'black flash' or had lockup issues.  I am running a HP dv6000t (Core 2 Duo, nVidia Go 7400).

---

### Post by NTolerance on 2008-07-10
> **eznet said:**
> Since installing xserver-xgl, I have not seen the 'black flash' or had lockup issues.  I am running a HP dv6000t (Core 2 Duo, nVidia Go 7400).

Any disadvantages to running XGL nowadays?  A while back I remember hearing that AIGLX was the way to go.  There doesn't seem to be much hope for NVidia fixing this bug so I'm pretty desperate to make the flashing stop.  Hell, if go to their site you can't even pick the 7400 GO from the list.  Have they dropped support?

---

### Post by eznet on 2008-07-16
> **NTolerance said:**
> Any disadvantages to running XGL nowadays?  A while back I remember hearing that AIGLX was the way to go.  There doesn't seem to be much hope for NVidia fixing this bug so I'm pretty desperate to make the flashing stop.  Hell, if go to their site you can't even pick the 7400 GO from the list.  Have they dropped support?

Yea, there were some major disadvantages and I had to uninstall it...  Things got really buggy after a couple days and the system began crashing as opposed to locking up.  I did however get a solution for my problem and perhaps it will work for you as well.  Like you I was desperate to fix it and asked everywhere I could think.. No responses in the nVidia forum - go figure...  I don't think they every official supported the 7400 GO as it was made for specific laptops...  lame..

A kind chap by the name of kraptor at Launchpad provided me with the solution - overriding that stupid Powermizer feature (on laptops).  Heres what worked for me, let us know if it works for you.

make sure you nvidia-kernel-nkc (in /etc/modprobe.d) has the following:
```
alias char-major-195* nvidia
options nvidia_new NVreg_Mobile=1 NVreg_RegistryDwords="PerfLevelSrc=0x2222"
```
This will max out your video card and prevent it from 'throttling' which is what is causing that blasted flickering - of course, this can decrease you battery charge life.  I think you can change the setting to 1111 or 0000 if you want to slow it down instead of speed it up, but if you are using compiz and such then you will likely want it up instead of down.  Mine is always plugged in, so it really doesn't matter.
Next, make sure all is right in your xorg.conf.  Here is my screen section for reference (this what what I had botched the most):

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24   
    Option "DynamicTwinView" "True"
    Option "RenderAccel" "True"
    Option "TwinView" "True"
    Option "MetaModes" "nvidia-auto-select, nvidia-auto-select"
    Option "TwinViewXineramaInfoOrder" "DFP,CRT"
    Option "NvAGP" "1"
    Option "Coolbits" "1"
    SubSection "Display"
        Depth 24
    EndSubSection
EndSection
```

let me know if this does or doesn't work...

-Matt

---

### Post by NTolerance on 2008-07-16
> **eznet said:**
> Yea, there were some major disadvantages and I had to uninstall it...  Things got really buggy after a couple days and the system began crashing as opposed to locking up.  I did however get a solution for my problem and perhaps it will work for you as well.  Like you I was desperate to fix it and asked everywhere I could think.. No responses in the nVidia forum - go figure...  I don't think they every official supported the 7400 GO as it was made for specific laptops...  lame..

A kind chap by the name of kraptor at Launchpad provided me with the solution - overriding that stupid Powermizer feature (on laptops).  Heres what worked for me, let us know if it works for you.

make sure you nvidia-kernel-nkc (in /etc/modprobe.d) has the following:
```
alias char-major-195* nvidia
options nvidia_new NVreg_Mobile=1 NVreg_RegistryDwords="PerfLevelSrc=0x2222"
```
This will max out your video card and prevent it from 'throttling' which is what is causing that blasted flickering - of course, this can decrease you battery charge life.  I think you can change the setting to 1111 or 0000 if you want to slow it down instead of speed it up, but if you are using compiz and such then you will likely want it up instead of down.  Mine is always plugged in, so it really doesn't matter.
Next, make sure all is right in your xorg.conf.  Here is my screen section for reference (this what what I had botched the most):

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24   
    Option "DynamicTwinView" "True"
    Option "RenderAccel" "True"
    Option "TwinView" "True"
    Option "MetaModes" "nvidia-auto-select, nvidia-auto-select"
    Option "TwinViewXineramaInfoOrder" "DFP,CRT"
    Option "NvAGP" "1"
    Option "Coolbits" "1"
    SubSection "Display"
        Depth 24
    EndSubSection
EndSection
```

let me know if this does or doesn't work...

-Matt

Thanks for the info.  PerfLevelSrc doesn't work on my system though.  nvidia-settings still reports constant clock changing.  Right now I'm using a startup script to set the clockspeed at a pretty low level, yet no matter what I do, nvidia-settings claims the speed is constantly changing.  Can it be trusted?

---

### Post by eznet on 2008-07-16
> **NTolerance said:**
> Thanks for the info.  PerfLevelSrc doesn't work on my system though.  nvidia-settings still reports constant clock changing.  Right now I'm using a startup script to set the clockspeed at a pretty low level, yet no matter what I do, nvidia-settings claims the speed is constantly changing.  Can it be trusted?

Did you try changing your config files with the information I provided?  Before I did the above, PerfLevelSrc was not working on mine either.  If nvidia-settings shows it is still changing and your screen is still flickering then I would imagine that your scripts are not working - mine weren't.  I tried everything that I could find in the way of fixes - to no avail, until doing the above.  

Here is a [link to the Launchpad discussion]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/164589") on the matter (search for 'Kraptor  wrote on 2008-07-06' to skip to the relevant part). According to kraptor, before editing the nvidia-kernel-nck the driver didn't know it was addressing a mobile card.  Adding the  "options nvidia_new NVreg_Mobile=1 NVreg_RegistryDwords="PerfLevelSrc=0x2222"" line lets it know its a mobile card - if you look at the line closely, you can see its setting the NVreg_Mobile nVidia option to '1' or 'True'.  This is what fixed it for me - without this, your system doesn't know it is working with a mobile card - the only cards with Powermizer, therefor the only cards that the PerfLevelSrc options apply to...

---

### Post by NTolerance on 2008-07-17
> **eznet said:**
> Did you try changing your config files with the information I provided?  Before I did the above, PerfLevelSrc was not working on mine either.  If nvidia-settings shows it is still changing and your screen is still flickering then I would imagine that your scripts are not working - mine weren't.  I tried everything that I could find in the way of fixes - to no avail, until doing the above.  

Here is a [link to the Launchpad discussion]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/164589") on the matter (search for 'Kraptor  wrote on 2008-07-06' to skip to the relevant part). According to kraptor, before editing the nvidia-kernel-nck the driver didn't know it was addressing a mobile card.  Adding the  "options nvidia_new NVreg_Mobile=1 NVreg_RegistryDwords="PerfLevelSrc=0x2222"" line lets it know its a mobile card - if you look at the line closely, you can see its setting the NVreg_Mobile nVidia option to '1' or 'True'.  This is what fixed it for me - without this, your system doesn't know it is working with a mobile card - the only cards with Powermizer, therefor the only cards that the PerfLevelSrc options apply to...

Well I'll be damned.  You came through with the necessary detail on this.  The key here is using "nvidia_new" in the modprobe.d file rather than just "nvidia".  The information at the NVidia forums used plain old "nvidia", which apparently is ignored by Ubuntu since in our case it's actually "nvidia_new".  I tried setting it to 0x0000 in an effort to lock it into low-power mode which is fast enough in Compiz for me, but it's still at performance level 2.  That's OK because I can then use coolbits to underclock it.  But the point is that it's not changing the clockspeed anymore.  Thanks!  :)

---

### Post by eznet on 2008-07-18
No problemo NTolerance!  Glad it worked for you - if you were anything like me, I was about the bash my skull in trying to get the flickering and freezing up to stop.  It was driving me bonkers - the more I tried to repress my anger when the screen flickered, the more I noticed I was grinding my clenched teeth when it flashed :twisted:  

No more flickering, no more grinding teeth and all is well in the world of DV6000t/Ubuntu!

---

