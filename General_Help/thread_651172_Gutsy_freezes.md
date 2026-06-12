---
title: "Gutsy freezes"
date: 2007-12-27
forum: General Help
---

### Post by shifty2 on 2007-12-27
A few times a day gutsy will just freeze on me. Each freeze has the same pattern - if music is playing that will stop at the same time all windows will freeze but I can still move the mouse. After that the mouse stops and the only way to recover is a hard reboot. I have tried looking in the system log to see if there will be any indication in there of what causes the problem but no luck.

So any ideas? I'm pretty stumped and a few searches has revealed no problems sort of similar to mine. Next step would be a fresh install of gutsy I feel.

Cheers for any help.

---

### Post by cdenley on 2007-12-27
Before you try a fresh install of gutsy, see if you have the same problem while running off the livecd. If you do, then it is either an Ubuntu bug, or a hardware problem, and won't be fixed by a reinstall.

---

### Post by daengbo on 2007-12-27
I see two possibilities:
1) Some application is acting badly and killing X by spinning out of control. This shouldn't be able to happen, but some things like caching in the X server could do it, I guess. To test this one out, next time you start to notice problems, quickly hit ctrl-alt-F1 to get a terminal, log in , and type "top" to see what's happening. Press "q" to exit top. 

If you can't switch to a terminal, try holding Alt and Print Screen down while you type the following letters -- r e i s u b. Don't let go of the Alt-PRTSCR keys until you finish. If your computer reboots, then your kernel didn't oops.

2) Neither of those work and your kernel is oopsing. This is probably a hardware problem. Test your memory. Check your fans for excessive dust and lint which may cause overheating. 

Good luck

---

### Post by Nexusx6 on 2007-12-27
Oddly enough, I have this exact same problem, and was ready to create a post. I haven't been able to predictably reproduce the error; it just happens randomly a few times a day. And like shifty said - the whole system locks up, and if I'm playing music the song will get stuck, mouse freezes, everything locks up. All I can do is hard boot. 

I'll follow your advice daengbo and will watch this thread.

---

### Post by fourdegrees on 2007-12-28
Hi there, 

I've been searching around the forums and this issue most closely matches my own.

In short, I'm getting "random" freezes in Ubuntu 7.10 while playing sound files.

In medium, 
-Gateway M350 laptop with no hardware modifications
-reasonably fresh install ( modifications  to allow MP3, DVD playback, Macromedia Flash plugin for Firefox, gxine, totem-xine, gnash)
-freezes occur only when audio playback is happening (has happened once while streaming online radio, once while watching a video on YouTube, and many times while playing local mp3s in rhythmbox)
-freezes entail total system stoppage (mouse pointer freezes, no keyboard inputs accepted, no response to "caps lock" on/off, no response to x reset hotkey, no respose to alt+prtscrn+r-e-i-s-u-b, and no response even to the built-in bios-controlled screen brightness or volume adjustment keys)

In long,
-here is the current system configuration (lspci)
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)

```
-here is what the freeze looks like (in this particular instance, I had the music running and was just navigating around waiting for the crash)
[[IMG]http://img339.imageshack.us/img339/2126/crash01screenbm2.th.jpg[/IMG]](http://img339.imageshack.us/my.php?image=crash01screenbm2.jpg)
-here is what the next boot attempt looked like
[[IMG]http://img201.imageshack.us/img201/605/crash01fsckue7.th.jpg[/IMG]](http://img201.imageshack.us/my.php?image=crash01fsckue7.jpg)

I'm more than happy to keep taking "screenshots" of what's going on when the crash happens. In this one, I was just about to close Firefox and have just rhythmbox and top running...o well.

Hopefully someone can figure out wth is going on. I installed Kubuntu 7.10, had no end of trouble with the way it handles permissions for installing packages, scrapped it, installed ubuntu 7.10, spent about a day figuring out how to get it to play mp3s and DVD, got everything pretty much up and running (grats btw on ubuntu "just working" ... except for this issue, I've been beyond pleased with it :). 

Also, I'm a total linux noob. Once in awhile I get the itch to play around with linux distros and it doesn't go much further than that, but Gutsy may just keep me away from Windows for good.

---

### Post by josebama on 2007-12-28
I have a similar problem, but my gutsy freezes randomly while the azureus is running, not playing sounds. But all the problems are the same: mouse, keyboard, windows and ctr+imprpetsis+r+e+i+s+u+b doesn't run

I will investigate more, if I find the cause of the problem, I will post here

---

### Post by shifty2 on 2007-12-28
I have thought that azureus could have been the cause of the problem as I have had several freezes when I have just started it. However, I had one earlier today having just started amarok so maybe it is the music that is causing the issues.

I think I will try a clean install later on today and see what impact, if any, that has.

---

### Post by Kristopher on 2007-12-28
This happens to me when i have Virualbox running or Amarok

---

### Post by josebama on 2007-12-28
I have tried a clean install of a Kubuntu Gutsy on my laptop and with only the azureus installed and running, it freezes, now I have the azureus not running and only the amarok and it is still running.

You use the amarok in KDE or in GNOME?

---

### Post by shifty2 on 2007-12-28
I have amarok running in gnome. That could be the issue there I suppose. I have never heard this issue reported before though.

Have done a clean install so will install amarok and see if the issue persists.

---

### Post by josebama on 2007-12-28
it seems that in KDE the amarok doesn't freeze because it is still running after 25 minutes, but the azureus freezes as I have said before

---

### Post by shifty2 on 2007-12-28
Ok, clean install with amarok running. I have set it to play through my music collection so will see if I get a freeze. Fingers crossed I dont...

---

### Post by shifty2 on 2007-12-28
Frozen again with just amarok running. I wonder what it is in amarok that is causing this to happen.

running it in terminal i get the following:
```
adam@adam-laptop:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
DCOPClient::attachInternal. Attach failed Could not open network socket
kbuildsycoca running...
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x80982d8 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x80982d8 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)

```

Think I should try using amarokapp then and see what that does.

---

### Post by Nexusx6 on 2007-12-28
alt+prntscrn+reisub didn't recover anything, so it looks like even the kernel dies. Found something odd in my log's though. This is from dmesg:
```
[   42.815043] sdb: rw=0, want=976768049, limit=488397168
[   42.815044] attempt to access beyond end of device
[   42.815045] sdb: rw=0, want=976768051, limit=488397168
[   42.815046] attempt to access beyond end of device
[   42.815047] sdb: rw=0, want=976768053, limit=488397168
[   42.815049] attempt to access beyond end of device
[   42.815050] sdb: rw=0, want=976768055, limit=488397168
[   42.815053] attempt to access beyond end of device
[   42.815054] sdb: rw=0, want=976768065, limit=488397168
[   42.815057] attempt to access beyond end of device
[   42.815059] sdb: rw=0, want=976768065, limit=488397168
[   43.344990] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   43.367065] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   43.466765] i2c-adapter i2c-0: nForce2 SMBus adapter at 0xf400
```
It also prints this error for sda as well. I noticed that it said "nForce2 SMBus" at the bottom which is very odd because... I don't have an nForce2 chipset. I have a  680i.. but, my server on the local network that I've been sshing into **does** have an nForce2 board. What it means, I can only guess =/

As for the hard drive errors, I have no idea what thats about, but it's always the part of the logs before the system boot up stuff (from the restart) after the crash happens.

---

### Post by fourdegrees on 2007-12-29
Adding another instance of freeze, I was just playing a DVD with no other applications open except totem-xine. Everything was going peachy for about 5-10 minutes when the system locked up again.

Can anyone tip me off (linux noob) as to where information appears when there is a system lock? Are there specific log files that are being updated almost constantly so that I can review them? Chances are the crash could be related to the absolute most recent thing the system was doing before the crash, but I'm not sure where to look. 

I dug around in var/crash, but that seems more like crash reports generated when an application "dies." I'm more interested in exactly what was going on when the system locked. 

Any help with this issue would be greatly appreciated.

It seems like the consistent factor in the crashes so far is the sound, not video...

---

### Post by wolfear on 2008-01-03
I'm having the "freeze" issues and there doesn't seem to be a common factor.

It'll randomly freeze even if there isn't an application open.

I'm running nvidia so I thought maybe that maybe that was it, but this happens no matter what drivers I use, even after a fresh install.
Just randomly locks and requires a reboot.

My system:
Pentium 3.33ghz Celeron D
2 gig 533mhz ram
Nvidia GeForce 7200
ECS P4M890T-M mobo

I love Ubuntu, but this has gone beyond an annoyance into unusable.

---

### Post by HDave on 2008-01-07
I too am getting the freezes...about every 2 hours.

I was thinking it was compiz or vmware, but reading this thread made me realize I am almost always listening to music via rhythymbox when it happens.  Running now without the music, but with everything else and will report back.

i have an nNvidia GEforce go 7400 card running the restricted drivers.

In case it is the video driver, can everyone please post there GPU specs?

---

### Post by AnthoMacP on 2008-01-07
fourdegrees, I'm having the same problem, during video, any type of audio, even occasionally during emesene signins when sounds are enabled. I'm running an Inspiron 5150 but I've been using ubuntu for years and it was only happening in 7.10.
 It was so frustrating I decided to go back to 7.04. In 7.04 it was fine until December after doing some updates and then it too started freezing. Now back in 7.10, hope someone figures this out, same thing happens either after an upgrade or fresh install.

---

### Post by HDave on 2008-01-07
Just froze up...without Rhythymbox.  So its down to compiz and vmware.

Can confirm that the alt-prtscr R S E I U B didn't work.

---

### Post by michust on 2008-01-07
I think it has nothing to do with playing music or video, Gutsy freezes on one of my systems while I am coping files to a network share (cifs) or to an USB disk.
But the freeze is always the same, only reset helps out.

---

### Post by AnthoMacP on 2008-01-07
> **michust said:**
> I think it has nothing to do with playing music or video, Gutsy freezes on one of my systems while I am coping files to a network share (cifs) or to an USB disk.
But the freeze is always the same, only reset helps out.
I think there's two different bugs going on here as my uptime in ubuntu lasts for weeks w/o freezes then as soon as i start anything media related i get a freeze

---

### Post by DjBeck on 2008-01-07
I have the same problem now in Gutsy, as I had in [Feisty]("http://ubuntuforums.org/showthread.php?t=412125&highlight=freeze")
I doubt that it's hardware related, since I have tried other distriubtions without any problems ... The issue on my system is that everything freezes - including the mouse.

All i want for christmas next year, is a working and stable Ubuntu release installed on my computer :)

---

### Post by wolfear on 2008-01-08
What ever the underlying cause ( or causes), it seems to be fixed in Hardy.

I tried every fix I could find and out of desparation, I finally did an upgrade to Hardy and so far, no freezes.

I get a few minor "hiccups" here and there (primarily when compiling an older program) but seems relatively stable so far and thnakfully, no more lockups.

---

### Post by HDave on 2008-01-08
Turned off compiz fusion and just spend all day with vmware, pidgin, rhythmbox, open office, etc.  and no lock ups.  This hasn't happened ever.  The system even *feels* more stable.

So its no more compiz for me...but I am very happy with the new found stability.  Hopefully will get better in Hardy.

---

### Post by michust on 2008-01-08
> **wolfear said:**
> What ever the underlying cause ( or causes), it seems to be fixed in Hardy.

I tried every fix I could find and out of desparation, I finally did an upgrade to Hardy and so far, no freezes.

I get a few minor "hiccups" here and there (primarily when compiling an older program) but seems relatively stable so far and thnakfully, no more lockups.

To bad hardy does not compile vmware player, and I need a little bit Win$...

---

### Post by trappe on 2008-01-08
I installed a pre-release version of Gutsy on a Dell machine and on a machine that I built and both installs had the same problems with freezing - completely random.  I actually reformatted and reinstalled the released version of Gutsy on both machines and still have the problem.  The display on the machine I built becomes unreadable when it freezes, but the Dell just freezes.  Both require hard reboot to bring back up.  I have yet to do anything but configure shares and other setup (no music or media use yet).

---

### Post by willytheweed on 2008-01-09
Morning, afternoon all,

Yet another noob here getting the freezing problem.
I installed Ubuntu a couple of day ago everything works fine apart from it freezes, again no real pattern to it.
I get 1 error when booting which is " cannot allocate resource to region 3 device"  which i think from all the reading i have done is about the Nvidia graphics card in the pcie slot in my machine.So i think its an issue with the pcie slot and Ubuntu ? Which i havent got a clue on how to fix.

I have tried re-installing the restricted drivers and i dont get as many freezes/lock up now.
Although, it still locks up.
And i still get the error message when booting but it still boots with no other probs other than the lock ups.

So far i dont think anyone has managed to sove this problem, some say its g-card but others are having the same trouble using different G cards.

So far i love Ubuntu and wil be sticking with it, wouldbe great  to be able to use the Os with out having to hard re-boot it 3-4 times a day.

Any comments or thoughts from other having the same problems would be very welcome.

Thankyou

WtW

---

### Post by wolfear on 2008-01-09
> **michust said:**
> To bad hardy does not compile vmware player, and I need a little bit Win$...

Wiill what you need not run under Wine? Wine is working just fine in Hardy.

---

### Post by Paul_G on 2008-01-09
hey guys,

I've just been reading the post, and while I cannot give any real suggestions as to how to fix the problem, I can add another 'problem'.
After a returning home from work and booting up my linux machine to do some work found that it started to freeze, as other have reported with mouse moving but nothing else working.

I haven't been using any of the software listed, have rebooted about 5 times and still the thing freezes after a couple of minutes, hardly enough time to do anything really..

Tis annoying as I can't access the files that I need to work on! grrrrrrr......

---

### Post by HDave on 2008-01-09
Everybody -- if you can still move the mouse then you are not suffering from the same problem as the OP, who, once frozen cannot even do the "RSEIUB" trick.  

For those of you who can move the mouse after the lock-up try the "RSEIUB" trick and see if you can reboot. Then post the relevant portion of your syslog perhaps in another thread such as this one:

[http://ubuntuforums.org/showthread.php?t=629245]("http://ubuntuforums.org/showthread.php?t=629245")

or check out the launchpad bug report here

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/156289]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/156289")

It seems like somebody found a workaround by changing kernels and using some Fiesty stuff...a complex thing to do for a rotating cube...   ;-)

---

### Post by willytheweed on 2008-01-10
When my machine freezes thats it nothing i can do but reboot.

I had a similar problem when trying winblows vista and i went into c-panel and allocated it ( vista) more power, that stopped all the lock ups.  Iam beginning wonder if this is possible in Gutsy?  or could it be that a 450 watt psu is simply not enough for Gutsy to run?  

I know this may seem iam clutching at straws but i really do want to get rid of winblows and start using a proper OS again.

I have tried getting rid of compiz and that made no difference at all.

I have had to go back back to XP  :mad: until this is fixed as it is currently unusable :(

Willy

---

### Post by gspat on 2008-01-10
I too suffer from the lockups, but occasionally (50/50) the machine just reboots.

I had searched and previously found this thread : [http://ubuntuforums.org/showthread.php?t=566422](http://ubuntuforums.org/showthread.php?t=566422) which seems to be part of the issue (bug in IRQ handling in nvidia restricted driver) but the workarounds posted in the thread just don't work for me.

At this point anything at all helpful would be appreciated!

---

### Post by HDave on 2008-01-10
If you have already stopped using compiz, my suggestion would be to stop using the restricted drivers and go back to the one that comes with Gutsy and try that.  I have heard that this has cured some people.

---

### Post by gspat on 2008-01-10
I would, but then I wouldn't be able to play WoW anymore!!!

---

### Post by willytheweed on 2008-01-10
Hi HDave, 

Tried that as well, still the same problems just installed Feisty and have the freeze lock up problems on that as well.

Very frustrating ...

---

### Post by cytg on 2008-01-10
me2 me2 .. i managed to create my own topic on it before stumbling on this one though ...

.. home to disable compiz and perhaps the restricted nvidia driver.

---

### Post by HDave on 2008-01-10
Willy the Weed -- We must have different problems.  Since I disabled compiz fusion, I can't make this laptop lock up no matter what I do.   Does you system work well under windows?  Starting to wonder if you don't have a hardware malfunction...

---

### Post by ed_x on 2008-01-10
HDave, I've got the same problems as you've got. With compiz disabled, it is stable. But with compiz enabled, it crashes very often. I've found it that the frequency of the crashes are dependent of the theme you use. When I select the Mac OS X look-alike theme, you can just sit and wait for it because it only takes a few minutes. But with a Vista (it's fun when connected to a beamer, everybody's amazed of the effects which can't be achieved under windows itself) theme, it can run for hours before crashing. Ofcourse it's not the theme that causes it, but there's something in it that triggers the real problem much faster.

(2.6.22-14 generic, ATI mobility radeon 9600 on Intel Centrino 32bit)

---

### Post by cytg on 2008-01-11
well .. i forgot, i had allready set my windowmanager to metacity, bugger is still locking up.

---

### Post by willytheweed on 2008-01-11
Hello HDave,

Yes the whole thing works like a charm under winblows, no lock ups, no freezes, no problems other than having to run windows :(

Which i hate having to do ....

Feisty has the same problem on my machine too.

I have treid unstalling the device drivers for my Gcard and using ones dloaded from Nvidia still the same problems. tried the compiz thing as well and it made no difference.

Iam determined not to give up totally, but i think this is going to be a long drawn out process.

Thankyou for the help so far.
:) 
Willy

---

### Post by cytg on 2008-01-11
Indeed. This is bad :(

---

### Post by HDave on 2008-01-11
Don't give up yet -- found 3 new leads here.  I was reading up on an old thread in launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58019]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58019")

and it gave me the idea.  Next time the system locks up, see if you can go to another computer and ssh into your locked up machine.  Then look at the x log file and kill the x server.  This will at least confirm/deny that is it X windows freeze and not the whole system.

You will need to enable the ssh service as Ubuntu has it turned off by default for security reasons.

The second thing I learned is that apparently the whole world is aware that ATI and nVidia's drivers causes freezing, due to CPU frequency mistmatch...particularly with SMP (multi-core processors...of which my machine is):

[http://linuxtechie.wordpress.com/2007/10/15/annoying-freezes-caused-by-nvidia-driver/]("http://linuxtechie.wordpress.com/2007/10/15/annoying-freezes-caused-by-nvidia-driver/")

for you ATI guys, I would try to find other folks with your exact card and the freeze are probably with X and are due to your GPU.  Do not fret, if you haven't heard already AMD took the amazing step of open sourcing all of their graphics drivers.

[http://enterpriselinuxlog.blogs.techtarget.com/2007/05/09/amd-will-deliver-open-graphics-drivers/]("http://enterpriselinuxlog.blogs.techtarget.com/2007/05/09/amd-will-deliver-open-graphics-drivers/")

For you nVidia guys, read on...

The third thing I learned is that Nvidia Corp. is aware of the freezing problem and has released a new driver that address the problem of "stability" for series 7 and 8 cards. Folks are reporting this driver solves their freezing issues:

[http://www.nvidia.com/object/linux_display_ia32_169.07.html]("http://www.nvidia.com/object/linux_display_ia32_169.07.html")

Here is some help on how to install the new drivers.

[http://ubuntuforums.org/showthread.php?t=649875]("http://ubuntuforums.org/showthread.php?t=649875")

I'll be moving to the new driver probably next week....

---

### Post by willytheweed on 2008-01-11
Hello HDave,

Many thanks for all the work so far, but iam sorry to say that i have already dload the new drivers from nvidia and got rid of the old ones, installed new from envy and still the problem persists.

:(

i have been busy since i opted for linux, which is great, its getting my brain back into problems solving again in IT which is something i have done for ages.

I used to run freebsd systems years ago but then went of of IT altogether so my brain is rusty .

Iam not ready to give up yet and dont have another machine that i can ssh into the broken one with, so its trial and error for me iam afraid.

Please keep us informed if this does work for you.

All the best 

Willy

---

### Post by Repgahroll on 2008-01-11
Yeah man, i was having the same problem, but now i've installed the kernel 386 instead of the generic one, and then i believe the freezing problem has gone!

Wait just more a little time to confirm that, but i'm using it (has more than one hour) and no crashes at all!

If it crashes too, i'll need to use the Feisty old kernel... have no choice!

I'd tried to use Debian kernels too, but no luck :( Soon i'll try the Hardy one :D :D :D


Thanks

---

### Post by willytheweed on 2008-01-11
Repgahroll

Good stuff lets hope it works, this is the one thing i havent tried ( although i dare say there are others too) so i wait and see with eagerness.

Out of interest, replacing kernels is iam, afraid beyond me at the present, so if this does indeed work for you, any help in how you did this would be VERY VERY welcome.

All the best 

Willy

---

### Post by Repgahroll on 2008-01-11
[B]Thankyou man!

It stills rock-solid here[/B] :D... Just don't forget to install the linux-heades & etc. for your respective kernel if needed.

I just did an "apt-get install linux-386" :D

Thanks :D Sorry my english :(

---

### Post by willytheweed on 2008-01-11
Cool,

I will deffo give that a try.

Your English is fine man no worries.  

:)

Keep us informed .

Willy

---

### Post by erniequintero on 2008-01-11
i think i fix mine since i did this is working just fine. 
first in the kernel parameter i introduce this commands

pci=assign-busses apicmaintimer idle=poll reboot=cold,hard

and then (this was in another post from this website).

Add the following to your /etc/modules:
battery
ac
thermal
processor
acpi-cpufreq
cpufreq-userspace 

by the moment the system is responding just fine without no problems im using the restricted driver for the nvidia and compiz-fusion without no issue. im using a compaq V3000.

---

### Post by Repgahroll on 2008-01-11
Ok man, thanks :D

No worries about it! 'cause the installer will create automatically a GRUB entry for the new kernel, but the old one will still there, if you have some problem, you'll can boot the old kernel and run everything as before :D

Here the first boot in the new kernel had been a little slower than usual, and the system beeps two times, but was just at the first boot... now everything is fine :D

Thankyou :D :D

---

### Post by HDave on 2008-01-11
Repgahroll -- Correct me if I am wrong, but I thought the 386 kernel doesn't not allow SMP (symetric multi-processing).  That is, if you have a dual core, linux will only use one of the cores.

Do a ```
cat /proc/cpuinfo
``` to find out.  It will list attributes for both cores if they are both recognized, else it will show only one.

That said, I have often read the problem with nVidia happens almost exclusively with SMP, so it doesn't suprise me that it would work.  In my case, I need both processors, but I don't need compiz...

willytheweed -- thanks for sharing that the new drivers didn't work for you...saved me a couple hours.

erniequintero  -- your fix sounds interesting, I'll try it out next week when i am back in the office.... perhaps the others here can try it out too...

---

### Post by Repgahroll on 2008-01-11
Oh yeah man... i forgot it :(

Thankyou very much! :D

---

### Post by willytheweed on 2008-01-11
Wow this is great folks, so much help and freindly too.

erniequintero, has any one else tried this with success? 

Its great that this has fixed the problem for you and it gives me ...more stuff to try ....

Keep those suggestions coming folks and we will get there in the end iam sure of it. :)

I too need both processors running on my machine so the 386 kernel isnt really an option for me, but may help others running single core procs.

I will give ernies idea a run and see how i get on and report back.

Have a good weekend all.

Willy

---

### Post by erniequintero on 2008-01-11
if you google this
pci=assign-busses apicmaintimer idle=poll reboot=cold,hard
you will get some blogs with this solution for compaq computers it seems is a problem with the news kernel and its no only for ubuntu also for other distros that have the latest kernel like gutsy but its no a problem with the kernel i think is because hp is using an old bios, the pheonix bios. but well with that line fix the issue for me.

---

### Post by willytheweed on 2008-01-11
Thanks Ernie, 

Is your machine a dula core proc or single?

Willy

---

### Post by erniequintero on 2008-01-11
well its a amd turion Mk36. i think its a single core but some how before this kernel arguments my only way to boot was with noapic and nosmp. but the computer freezes with thoes but with they other my system runs fine and i dont think those disable the smp.

---

### Post by willytheweed on 2008-01-11
Thanks Ernie, 

We will get there.

All the best 

Willy

---

### Post by fourdegrees on 2008-01-12
Hi folks,

Just popping in to say I'm still watching this thread. Couple things...

1.) I'm glad some of the fixes in here are working for people. yay. :)
2.) I'm still testing my system to find out exactly what the heck's going on.
3.) I'm just about positive my issue is related to sound output, not video output.
4.) I'm still frustrated. Having a random freeze in any OS is a huge issue, nearing "show stopper" over here, but I support what ubuntu is about so I'm not giving up just yet...

---

### Post by Repgahroll on 2008-01-12
It's confirmed guys! The '386 kernel' solved the problem here! (i think i'd tested enough to say it):popcorn:

Now, i'm gonna try the Ernie's solution:
> **erniequintero said:**
> pci=assign-busses apicmaintimer idle=poll reboot=cold,hard

Thanks :D

---

### Post by shifty2 on 2008-01-12
Forgot about this thread! 

My computer has stopped freezing on gutsy - not really sure of the reason why though. I think it is due to replacing amarok with exaile but I'm not sure. I'm trying to think of any other changes that I have made to my system that could have resulted in it stopping from freezing,

It does seem that there have been numerous different reasons causing gutsy to freeze, compiz and sound.

---

### Post by s3a on 2008-01-12
I had the same problem...I think it's a compiz-fusion bug because, ever since I disabled it...it never does that anymore!

System->Preferences->Appearance->Visual Effects->None

...so, live without nice effects until the next release...it's only 4 months...

P.S.
The problem will be there on maximum and medium effects...so, turn off completely!

*This has been my experience...if you have it turned off and it happens to you then I will be like shocked because, I really think this is it!*

---

### Post by cytg on 2008-01-12
nope, sorry to say. Allready turned off. :(

---

### Post by Repgahroll on 2008-01-12
Oh man... i was trying the Ernie's solution, but it crashed! :(

I don't know why... everything was looking like OK, i was using it for more than 8 hours without reboot... but it just crashed =/ =|
I'd activated the compiz :D but not only the X had crashed... was a total crash!
I'm using the newest nvidia driver, and at the crash moment i was running a terminal logged as root, amarok(playing music), firefox, openoffice, gimp, mplayer(capturing from webcam), blender, pidgin, synaptic(downloading a package), and finally xsane(scanning a high-resolution image)... i know, i know; probably you'll say the crash ocurred because i was running too many things at the same time, but using the feisty kernel it's OK.

Isn't there a way to use a dual-core processor with the 386 kernel?? :(

Sorry my english guys :(

Thank you all very much!

---

### Post by mandlebaum on 2008-01-13
For those of you with Nvidia cards and AMD64 systems, I think this may have something to do with gutsy's kernel and the current Nvidia drivers that are available in Synaptic  (100.14.19 and earlier).  I was having a similar problem.  While playing video on the web or when playing video games using accelerated graphics the computer would sometimes completely freeze allowing neither mouse or keyboard input.  By using Nvidia's installer to install the very latest Nvidia driver (169.07) I was able to get rid of this problem ( I believe, since I was able to leave a 3D accelerated game running for an hour)

---

### Post by willytheweed on 2008-01-13
"Isn't there a way to use a dual-core processor with the 386 kernel?? "

I hope there is then i will be giving it a go .

Well done to all that now have working systems :)

Well no more playing for me this weekend will have another look at it on monday.



Willy

---

### Post by cytg on 2008-01-17
are you all good ? Im still taking the dive from time to time .... :(

---

### Post by HDave on 2008-01-17
After reading Repgahroll's report that the newest drivers haven't fixed the problem I have punted on this...am totally giving up in total frustration, sorry.   :(  

I am hoping it gets fixed in Hardy.  Nothing left to try....  For me, at least with compiz off I have 100% stability.

BTW -- Sometimes my system doesn't freeze...it literally crashes and powers off!!!  Incredible.  Like others here, I was convinced for a while my problem was sound related.  There is no question that running Rythymbox decreased the amount of time before a lock-up, but with compiz off I can play music all day long with no problem.

---

### Post by megaribi on 2008-01-17
I had (or still have) similar problem. I use Ubuntu 7.10 with a lot of added software. However, GUI locked up quite often, and I can only do Ctrl+Alt+SysRq REISUB. Most commonly it locked during Firefox, OpenArena, GoogleEarth, window fading in Compiz and worst, under DVD writing. If I touched mouse, average uptime of Ubuntu was about 20 minutes, but in idle it can be turned on over weekend.

I tried kernel change to 2.6.24, ACPI=off in boot menu, disabling compiz effects, disabling screen savers but wthout success.

Finally I installed current ATI fglrx driver using Envy, and everything was better.
 "ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]". I did not remark any freeze even if I tortured computer with mentioned programs. 

(I must say, however, that this installation did not success always, in some situations compiz turned screen to white, but after second reboot, everything was OK.)

---

### Post by Peter Wagner on 2008-01-18
thanks for your discussion, now i have something between an image about my topic and chaos about what to do.

I'm a total newcomer to both Linux and Ubuntu (10/2007). Up to now everything was fine, I accepted taht some isolated tasks I'll have to do with my XP partition, but now all the saftey is gone, and I dont know how to admit to my wife that I have to work under Windows because gutsy is freezing after 5, 8, maximum maybe 15 minutes. Which is just enough time to copy files to a flashdisk to have it available on XP.

I dont have to run any software to have a freeze (no reaction at all, mouse doesnt move). I have also removed external hardware (printer, internet, audio), freezing comes like the night - without any doubt. On the logon-screen after rebooting, the system is still stable, but just login in, waiting for the theme, you can be sure that within several minutes no more reaction will be. The parallel XP is running correctly, so hardware is supposed to be OK. 

My system was running perfect until monday morning. After the automatical updates of Mo, Jan 14, it worked two more hours, but beginning with the next restart I am working in the 50-50 mode (50% working, 50% booting) ;-)

What does it mean to run kernel 386, i.e. what am i to do do do this? Isnt it rather a problem o one of the last updates, as I havent added new software neither hardware during the last weeks? The only thing I remember having changed is that I have switched off special screen effects (you call it compiz, i see), just to try whether it increases speed. Initially, the switch was in an undefined state, unless I have set it to "none".

---

### Post by anthonyJC on 2008-01-18
i have a multicore and my experience with my multicore is that this kernel branch cannot do apic on acpi. disabiling apic via kernel  didn't help -so it appears catalyst is smp code; but disabling smp does. one way to disable smp is to use nosmp kernel switch.  the apicmaintimer switch doesn't fix. (--in my later posts it seems likely SATA is clashing with SMP)

---

### Post by cytg on 2008-01-18
I suppose the  uberl33t HyperThreading could put me in the smp-bug risc area ... ill try disabling that.

---

### Post by HDave on 2008-01-18
Peter -- Do not give up...while there is no real fix to this problem, it is still easily eliminated in my opinion, by taking one of two approaches.

Approach 1) Turn off compiz-fusion.  Do this by clicking right on the desktop, select "Change Desktop Background", select the tab that says "Visual Effects" and select "None".

Approach 2) Disable SMP (symmetric multi-processing...i.e. using a dual-core CPU).  Do this by editing your GRUB menu in /boot/grub directory in a file called menu.lst to add the -nosmp to the command line of your boot.  Alternatively you can use syntaptic to install the 386 kernel which will only recognize one cpu core.  After installing the kernel you will probably have to add a line to your GRUB menu.lst to boot with that new kernel you installed.

Please try one or the other and report back, along with you CPU and GPU specs.

---

### Post by willytheweed on 2008-01-18
Afternoon all,

Well another week of freezes and still no solution.

Iam off back to XP until there is a fix for this, i cannot work on a system  that at the moment is so unreliable.  :(

I will continue to monitor it from time to time but i need my dual core chip.

Having installed gutsy ona an old laptop, it runs fine with no freezes at all, but not on my dual core system.

I will keep trying to fix this problem and will report back when and if it gets fixed.

Willy

---

### Post by kevinp on 2008-01-18
I am also having intermittent lockups after upgrading to Gutsy.  What sucks is that I am running a server that runs many network apps and cannot freeze in this manner.  Edgy was very reliable, with uptimes ranging into the 6 month range.

My server is an AMD64 dual core with an ATI Radeon card.  The freezes occur with the kernel 2.6.20  I have now booted with an older kernel 2.6.17 to see how it works.  So far so good.

I tried the acpi=off option with the 2.6.20 kernel but it did not help.  I could try disabling SMP but that would reduce performance so it is not really an option.

It sucks that this freeze occurs.  This defeats the whole point of running Linux on servers as a robust and safe alternative to Windows.

**[COLOR="Red"]Is it safe to run Gutsy with the 2.6.17 kernel?[/COLOR]**

Update: The system has now run on the 2.6.17 kernel for 2.5 days without any freeze.

Second update:  I made the freezes go away by using the following kernel options with the Gutsy default kernel of 2.6.22:
/boot/grub/menu.lst:

```
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/md0 ro quiet nosplash noapic acpi=off pci=nomsi
```

---

### Post by cytg on 2008-01-19
i havent tried the -nosmp yet and it will not be a huge deal to loose hyperthreading, but in a few months ill be in the market for a quad core, and disabling 3 cores to run gutsy will not be an option. 
I will say though that i try out linux every other year or so, and the last few years it havent lasted 2 days as my main desktop os. Ubuntu has been my main desktop OS for over 6 months  now.. so maybe, just maybe in a few more years it will be ready for intolerant nopatient easy-annoyable old farts like myself :)

---

### Post by cytg on 2008-01-19
i also had an issue with VLC last night .. pretty annoying that this sort of stuff can happen. Perhaps ubuntu should consider another level of support and testing.. maybe something like

1. Restore Points (like in XP). This may defeat the purpose and be defective by design, i dont know, the problem should perhaps be attacked at another level.

2. Segmented update profiles. Give users a choice as to what update-segment they will be in, 1,2 or 3. Level 1 gets the updates first, say a few days before everybody else, reports are gathered and if results are acceptable, push to level 2 and repeat. 

3. Building upon suggestion 2. create online database of hardware profiles (with users acceptence) perhaps linked to ubuntuforums, so users with similar hardware constructs will have an easy and direct way to communicate 'issues'.. If this construct was linked directly from the update manager, alot, ALOT, more users would be able to find eachother. and troubleshott issues.

Just saying :)

---

### Post by anthonyJC on 2008-01-19
Fedora 8 seems to be far more stable with just a daily freeze over a fortnight period throughout the following kern's  2.6.23.1-2.6.23.15-137.

---

### Post by kevinp on 2008-01-19
AnthonyJC, do you know what were the fixes in the 2.6.23. kernel?

---

### Post by anthonyJC on 2008-01-20
It's a new branch so it's major changes. BTW I'm using  23.1  .  If you're  trying to pinpoint where the problem is,  it's in the area of ACPI. But it's only showing itself with  SMP. This is only my deduction based on elimination,    with my hardware, on  many distros. I used in 2007.  I never tested changing APIC use, because it's known that these kernel switches were incomplete before October on AMD64.2.6.23.9 reports:
```

apm: disabled - APM is not SMP safe.

```
so try the noapm switch?

---

### Post by Peter Wagner on 2008-01-20
Dear HDave,

thank you for your nice word of consolation. I'm not desparate, just a little unhappy. After my decision to switch to Linux I have gained some fluency in handling it (and it was really very very fast and almost without conflicts). I have moved files, mails, configurated my new environment, got used to some inconveniences with evolution, found some new friends with XSane and Audacy, but now everything seems gone, during one day and a half.

Special graphic effects I have disabled already before the troubles began, it almost looks that their disabling caused the problems (which is nonsense of course).

Up to now I've tried the -nosmp switch, but without success. The kernel 386 I will try when I'll have some spare time to play with software.

See you soon!
Peter

---

### Post by lathanial on 2008-01-21
This problem sounds like my wifes laptop - HP 510 with a couple of differences. 

First, if I wait a while - 30 seconds to a couple of minutes - it seems to thaw out and start playing again. It does the same whether she uses Rythmbox or Amrok. (Using Itunes under windows works fine).

I initially thought it was related to the audio but now I'm not sure. I've been helping her with GNUcash and she seems to be have the same problem without the music playing. The system locks for a couple of minutes and then start back. I've run TOPS in a terminal while watching for the freeze and I don't see anything unusual though I might n ot recognize it if I saw it. It does seem strange that TOPS seems to keep running in terminal while the music or other app is frozen.

Could someone try running TOPS in a terminal and listen to your music until it hangs (if it's like mine it will happen within 10 minutes) and then wait several minutes to see if it thaws.

Thanks,
lathanial

---

### Post by HDave on 2008-01-21
Folks - On a hunch, I enabled the "backports" repository in Synaptic, and viola there was a new version of compiz fusion available for download.

I installed it and rebooted and am sorry to report that while greatly reduced, the "freezes" are still there.

---

### Post by ninkasi on 2008-01-28
Well, unfortunately I have to report freezes as well.

Video - Intel 945G chipset [so not issue with nvidia etc]
Server only - [so no X]
Intel Core 2 Duo [so not an issue with AMD]

Point of fact, was running with an AMD processor under Gentoo without any issues [eg 6 months+ uptime, only rebooting after kernel updates and changing battery in the UPS]. Changed to Ubuntu (server) and the freezing [kernel panics with caps lock flashing etc] started almost immediately. Running headless so couldn't see anything on a monitor, and nothing reported in the logs.

Changed to the Intel [new motherboard, memory, processor, case, power supply] with same issue.  Only things that stayed the same were the motherboard brand (both gigabyte), hard drives (sata drives) and power source (APC ups). Changed boot to include "acpi=off apm=off nosmp noapic" and that seemed to help... in that instead of locking up somewhere between instantly to within an hour, it now stays up for maybe a day. Actually, adding in the "acpi=off" seemed to make the most difference. The "nosmp" just made some things a bit slower.

For what it's worth....

```

cat version
Linux version 2.6.22-14-server (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:31:40 UTC 2007

```

```

title           Ubuntu 7.10, kernel 2.6.22-14-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-server root=UUID=386ae7b3-ec48-4b55-b720-24dfeecfc145 ro quiet splash acpi=off apm=off nosmp noapic
initrd          /boot/initrd.img-2.6.22-14-server
quiet

```

```

root@lurch:/boot/grub# cat /proc/cpuinfo |grep model
model           : 15
model name      : Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz

```

```

rphillip@lurch:~$ dmesg|grep -i agp
[   40.404631] Linux agpgart interface v0.102 (c) Dave Jones
[   40.904470] agpgart: Detected an Intel 945G Chipset.
[   40.904882] agpgart: Detected 7932K stolen memory.
[   40.918989] agpgart: AGP aperture is 256M @ 0xc0000000

```

I might try changing to a newer kernel, but otherwise [no offense to a very impressive distro] I suspect I may go back to Gentoo as I personally don't have much time to troubleshoot this....

---

### Post by anthonyJC on 2008-01-28
Ninkasi, when I disabled SMP inadvertantly via disalbing apic on acpi i had no issues. I have had a previous problem with a faulty ups causing my computer to crash and it took a long time to realise it. I guess it could have only been the cells getting old. I haven't been employed as  a system administrator , and only have experience with one UPS, an APC make. But it made me doubt if they are more of a hinderance than a help. I did not  try the apm=off switch. kernel dumps need to be collected. I don't think anyone has the exact cause.

---

### Post by ninkasi on 2008-01-28
Understand the potential issues that a UPS can introduce, but the issues they can reduce/avoid (eg faulty power supplies due to brown outs/surges over time) make them worthwhile in my opinion. APC is a reputable brand, but the cells of any UPS do have a lifespan and need to be replaced eventually - how long they last depending on variables such as load, quality of the grid power, and how often they've been flattened etc. I know people who have been using them for well over five years without changing the batteries, but around 2 to 3 years is a general rule of thumb. Testing it with something like apcupsd every 6 months or so is probably a good idea. Having the UPS automatically shut a server down is another argument that can be harder to justify (yep can avoid corruption of file systems etc, but on the other hand the software installed can introduce issues etc).

Anyhow, probably off the topic now! The interesting thing now is I think I'm able to force a freeze by transferring data from one sata drive to another.... so perhaps it's a memory clash/sata issue as suggested by a few people in some other threads (eg [this]("http://ph.ubuntuforums.com/showpost.php?p=4184014&postcount=536") one)

As you say, may try .23 or .24 and if that does resolve it all well and good - as a linux geek from way back when, mucking around with kernels doesn't frighten me but it is a shame that this issue should be in the general release kernel as it runs against the "just works" philosophy. I know that these things are complex, and issues do crop up that are hard to replicate, but this is happening on a wide variety of platforms including (like mine) on very simple setups (lamp server, no fancy extras, all-in-one motherboard so no nvidia special drives, standard seagate sata drive etc etc)....  

Cheers

---

### Post by ninkasi on 2008-01-29
Upgraded to 2.6.24-r5 and....

Ah well. Was worth a try. 

Stopped responding again whilst transferring a 600K file from one drive to another. Am searching through logs now, but nothing stands out so far.... will try moving the server to somewhere I can hoolk a monitor up to it to but otherwise I'll go back to gentoo and see if the problem persists with a different distro.

---

### Post by anthonyJC on 2008-01-29
I don't know of others experiences but a UPS was causing a freeze when it was not running off battery power. 

The SATA issue is a good possibility because the machine only froze when I used it, not when it was left on over night as a light server. Obviously there's increased disk accesses as Workstation.Also occured in Fedora 7 stock. However this user explictly said he removed ati/nvidia drivers, does not have smp and has SATA. This provides good evidence its SATA [http://ph.ubuntuforums.com/showpost.php?p=3662221&postcount=48](http://ph.ubuntuforums.com/showpost.php?p=3662221&postcount=48).
for eligos, Fedora 8 failed ([http://ph.ubuntuforums.com/showpost.php?p=4116113&postcount=493](http://ph.ubuntuforums.com/showpost.php?p=4116113&postcount=493)), This post [http://ph.ubuntuforums.com/showpost.php?p=3728905&postcount=120](http://ph.ubuntuforums.com/showpost.php?p=3728905&postcount=120) says use of IDE drive reduced probability.

---

### Post by kevinp on 2008-01-29
> **anthonyJC said:**
>  If your trying to pinpoint where the problem is,  it's in the area of ACPI. But it's only showing itself with  SMP. 

I have managed to use the 2.6.22 kernel with acpi=off and the freezes seem to go away.

Thanks for the suggestion!

---

### Post by Subban on 2008-01-29
I've been getting these freezes for a while now too, everything hangs yet the mouse moves, I get around them without a reboot  though by pressing alt+f2 for the run dialog as that still (rather oddly) works, then enter

```
gnome-terminal
```

the terminal will become active when it loads, which is handy as the while the mouse moves it can't click on anything. I then normally have to do a:

```
killall firefox-bin
```

Everything will just go back to normal instantly, until the next lockup. Personally I suspected dodgy Flash in the browser or the nvidia driver, it might not be the Flash because......

If firefox isn't running, then I just kill off what ever other applications I have run and can see in a:

```
ps -A
```

Hope that helps someone and reduces on reboots.

Oh, and for the people doing alt+prt sc+R S E I U B, are you allowing enough time between the keypresses for the kernal to actually complete each stage, about 3 seconds is usually fine for me.

---

### Post by Miroku on 2008-01-30
similar complaint here

gutsy RARELY freezes on me (2x since first install back in october) -- i now have amd64 version. my config is:

intel core 2 duo
nvidia 8300gs
2gb corsair ram

so i had amarok playing music and then i open firefox, and it freezes (mouse + keyboard) and i had to hard reset (which i HATE doing).

there is some sort of connection between amarok and firefox because they have other issues as well (such as amarok complaining of no sound device when firefox has anything media related loaded).

i dont think it will be much of an issue, its just one of the main reasons i switched to linux was to avoid random lock ups and stability -- which ubuntu has provided for almost a year now.

if anyone got some info, pass it along. TIA.

waitin for hardy nowww.

---

### Post by Subban on 2008-01-31
> **Miroku said:**
> 
there is some sort of connection between amarok and firefox because they have other issues as well (such as amarok complaining of no sound device when firefox has anything media related loaded).

I forgot to mention in my post that I don't use amarok as I had seen others comment on it. I do have the problem you mention that sometimes Firefox hogs the sound output thingies, nothing else can play sounds unless I close Firefox, it doesn't happen often though and nothing I can reproduce :S


And same as you, I am also eagerly awaiting Hardy, Gutsy seems to have been the worst release that I ave seen for problems :[

---

### Post by jesushero on 2008-01-31
Same here, but no weird reboot screens.. All is fine with my filesystems. I believe the problem starts when installing any plugins such as mp3 stuff, divx, flash, java, ANYTHING that is not there by default. I think the only definite solution I have found is to not install ANY plugins (which is very stupid since an os should be able to work with plugins built for it).. 

If anyone finds a "working" solution, let us know... 

(btw, it has NEVER crashed on terminal-only, it just crashes when gnome is running! So might be graphics related.)

Do you people use sound-players with visuals (in Windows media player fashion)?? It might be more graphics related than sound related. Not sure though..

---

### Post by Subban on 2008-01-31
> **jesushero said:**
> 
Do you people use sound-players with visuals (in Windows media player fashion)?? It might be more graphics related than sound related. Not sure though..

Exaile or Audacious without any visualisation for me.

---

### Post by ed_x on 2008-01-31
I've downgraded xserver-xorg-video-ati to 1:6.6.3 (from the Ubuntu Feisty repository). It has been running fine so far (one evening on a very frequently crashing laptop)

---

### Post by anthonyJC on 2008-01-31
those getting a freeze with multimedia are getting a specific type of freeze and it has been posted in these forums that it's to do with onboard sound card. disabling it in bios is supposed to help. but of course it's only of use if you have an external card to use as a replacement.

---

### Post by ninkasi on 2008-02-01
Well, not suggesting that people not use ubuntu, but my experience (one laptop and two servers) has been that it is easy to configure, but stability (again, for me) is not as good as I'd hoped. Naturally this could be a result of the sorts of apps I use, or just plain bad luck, but having lockups with a default lamp install - no X, no mp3, basically nothing fancy.... and to have the same issues with effectively two different (AMD and Intel Core 2 Duo) servers makes me think that something has been missed.

If I get the time (three young kids including twins means that free time is scarce) I'll try to troubleshoot this as there is a lot I liked with ubuntu, but in the meantime I've reinstalled gentoo.... and yep, so far no lockups (and currently I'm thrashing the server - doing concurrent compiles plus copying/moving files around).

I'm sure that the issues people have been reporting are most likely the result of a combination of factors ranging from hardware issues, to non-standard apps, to weird bugs. Hopefully they will be addressed soon.

Cheers

---

### Post by kansei on 2008-02-01
I'm having massive issues with freezing. It's not the type of freezing I can tolerate either. xorg server crashing no biggie, but anything that I can't even alt+sysrq+r-e-i-s-u-b out of is a bit of an issue.

I suspect my issue might be filesystem related though.

I was running Hardy Heron on this computer, but since I have a separate /home partition it's easy to change distros all the time so I did. I put gutsy back on. The night before I did that though, I got rid of a legacy ntfs partition that had my music and photos on it. I backed up all 400gb of that (I use FLAC) to my server, then deleted the NTFS partition and extended the reiserfs home partition to fill that gigantic space. The computer will be stable as hell until I use Amarok and listen to music. Then it'll die within a minute or up to 12 hours, a crash hard enough that the above reisub trick does nothing. I'm using Amarok with a local mysql server (was using it with the mysql server running on my dedicated server box too, no difference) if that helps.

I *think* the issue with this computer might be filesystem related. I actually had to rebuild trees on the /home partition before the partition resizing, gparted wouldn't let me resize because fix-fixable couldn't do enough (scary).

My server has a similar issue though. Background on it is that it's used as a mythtv backend server. It does have a frontend for people to watch tv in the basement but that never happens, especially now in the winter when it's cold down there. It has a 3ware escalade SATA raid controller (12 channel) and 3 hauppauge tv tuners (a PVR 500 and a PVR 150). 7 hard drives in hot-swappable bays, not big hard drives though total space is 1.5TB, 960GB usable with the RAID-5. The raid controller says the array is healthy, but on occasion (once a week on average) the server crashes and unplugging it is all I can do.

The problem I'm having is that both of these systems are crashing so hard that the kernel isn't even responding, so of course there are no log entries anywhere that point toward a problem. 

The other computer I  use primarily is a thinkpad with gutsy and I use amarok on it as well and there's never been a problem. It's rock solid stable.

None of this is really the fault of Ubuntu, I feel as though there might be underlying filesystem problems to fix and it's not like Ubuntu pushed me to use reiserfs, that was totally my own choice.

---

### Post by anthonyJC on 2008-02-01
and latops don't typically use SATA ? (I don't know, I haven't seen or really used a new laptop since SATA was introduced) and that's the key difference? So maybe its a combo of SATA+onboard sound card drivers clashing.

---

### Post by kansei on 2008-02-01
> **anthonyJC said:**
> and latops don't typically use SATA ? (I don't know, I haven't seen or really used a new laptop since SATA was introduced) and that's the key difference? So maybe its a combo of SATA+onboard sound card drivers clashing.

the laptop in question is IDE yeah.. but I have plenty of SATA linux boxes that are rock solid stable.

and I have a SATA laptop that is fine but it's running hardy 64-bit

oh and I can reproduce amarok hard crashing the system in like 3 minutes max.

so now I'm just listening to music via vlc and it's kinda lame. Amarok is one of my favourite linux apps (even though I can't stand KDE even a little bit).

I restarted in rescue mode (so that I could unmount /home without fanfare) and ran a reiserfsck check on the volume.. it's fine.

If onboard sound is an issue, this OS shouldn't ship like that. I doubt it though, because I've run gutsy since April or May in testing and never had trouble like this. My server absolutely never crashed running feisty. Guess I'll have to roll back to that.

---

### Post by ninkasi on 2008-02-01
>  None of this is really the fault of Ubuntu

Fully agree. For me I have the crashes with an ext3 file system..... interesting thing is that there still seems to be an issue with my server even after going back to gentoo, and again I am running a *very* basic setup. I wonder if there is something happening with the current kernel and/or sata drivers..... hmmm.....

---

### Post by KD6TZF on 2008-02-01
I'm having similar problems with Gutsy freezing up.  Usually I'm running the music player, evolution, and Firefox.  I have had it freeze up several times today trying to play music, or while using Firefox and opening a video or other sound file.  I tried closing the music player thinking there was a conflict, but firefox still froze up on me.  I have also done a reinstall of Firefox without success in clearing up the problem.  It's getting downright aggravating.  

I keep getting an error message, after trying to force close Firefox that it's still running.  I tried to kill it with the Terminal screen but don't know the right syntax to use to kill it and get it killed.  I then have to do a Hard Boot to free up the system.  Any suggestions on a better way to handle this?

Thanks,

---

### Post by ninkasi on 2008-02-01
> 
I tried to kill it with the Terminal screen but don't know the right syntax to use to kill it and get it killed.  

Sounds like a different issue if you find that you can still do things on your system. Usually a firefox crash is due to things like feral java apps. Anyhow, you can do a "ps -ef|grep fox" and find the process id numbers and then kill each individual one with the "kill" command.... or type "killall -iI firefox"... For info on how to use the commands, just use man eg type "man killall"

Cheers

---

### Post by ed_x on 2008-02-02
Oh bugger, the feisty version of xserver-xorg-video-ati crashes too, I was wrong with my assumption. It did run fine for a while though. I'm running ubuntu on a 32bit intel centrino laptop, IDE harddisk and reiserfs. Crashes are not related to playing music or any other procedure for me, it just crashes under any condition doing general work (also without firefox running).

---

### Post by cytg on 2008-02-03
posting from XP ... this has gotten to a point where its really not usable (coding happily away, freeze, code loss) ... ill keep the ubuntu partition for a month or so and check for updates .. too friggin bad it turned out like this :(

---

### Post by cytg on 2008-02-03
> **anthonyJC said:**
> those getting a freeze with multimedia are getting a specific type of freeze and it has been posted in these forums that it's to do with onboard sound card. disabling it in bios is supposed to help. but of course it's only of use if you have an external card to use as a replacement.

actually my onboard (not laptop) sound will be chewed up pretty often ... ill have to do a lsof to get a list of processes waiting to utilize sound and guess wich one is halting/occupying the device, then kill it.
But at the same time, no sound is not an option either.

---

### Post by ninkasi on 2008-02-04
Really, _really_ starting to think this is something endemic to the latest kernels/drivers. Even though I was having the same issue with two different servers and running ubuntu and gentoo I started to think that maybe it was bad memory.... and then my laptop (ubuntu latest) froze whilst transferring a file to one of the servers (gentoo latest) that in turn froze. Three boxes, two different distros? Nope. Not memory. Not power. I may roll a server all the way back to 2.6.15 that - for me - was stable.

---

### Post by anthonyJC on 2008-02-04
Try (nohz=off | highres=off nohz=off |  highres=off | noapm.) If you have built the machine yourself ensure any DVD/CD drives aren't jumpered to   C (cable select,) since this is unstable even if you only have one drive on the cable.
I filed an ACPI null pointer bug from my machine [https://bugzilla.redhat.com/show_bug.cgi?id=433623](https://bugzilla.redhat.com/show_bug.cgi?id=433623) to redhat.

---

### Post by MoebusNet on 2008-02-04
Just to put in my 2 cents...When my desktop system freezes, neither the keyboard nor the mouse will work. Something I haven't seen mentioned here is the fact that the "Num Lock" and "Scroll Lock" lights above the number pad of my keyboard start flashing about 3 times per second. Many times even Ctrl-Alt REISUB won't do anything, so all that is left is to power off. I have an Nvidia video card but am using the open-source driver "nv". I hope this is of help...

---

### Post by kansei on 2008-02-05
> **MoebusNet said:**
> Just to put in my 2 cents...When my desktop system freezes, neither the keyboard nor the mouse will work. Something I haven't seen mentioned here is the fact that the "Num Lock" and "Scroll Lock" lights above the number pad of my keyboard start flashing about 3 times per second. Many times even Ctrl-Alt REISUB won't do anything, so all that is left is to power off. I have an Nvidia video card but am using the open-source driver "nv". I hope this is of help...

On a dell latitude that means kernel panic. I dunno the status of keyboard lights because my happy hacking keyboard has no lights and my latitude doesn't have this issue :P

I fixed my desktop by switching to Debian testing.

---

### Post by ninkasi on 2008-02-07
Just an FYI to all:

1. When there's a kernel panic, the flashing lights are to alert you on a major issue if you are running a headless (ie no monitor) server and/or the monitor is turned off etc.... it also may not always happen if the server/pc really locks up badly.

2. You can set linux to auto-reboot if there's a kernel panic - this is done by editing /etc/sysctl.conf and uncommenting & changing the kernel.panic line to (say) 5 seconds. Doesn't resolve the issue, but can help reduce the pain. Again, won't always work if it's a BAD freeze, and also is not a good long-term thing as you may end up with a server that is constantly rebooting without your knowledge... 

3. In the same file above you can enable/disable the magic reboot keys with the "kernel.sysrq" line.

4. Oh, and you can also add in "kernel.panic_on_oops = 1" to treat an "oops" event as a panic and so reboot....

In the meantime, haven't had a chance to downgrade to a way older kernel yet.... hopefully this weekend will do so and see if it is being caused by kernel/software or by faulty hardware (and dumb bad luck that I'm now having issues with three different boxes and two different distros)

Cheers

---

### Post by kansei on 2008-02-07
thanks for that info!

in the ubuntu gutsy sysctl.conf there is no kernel.panic line 

so just add: "kernel.panic = 5" as a new line.

I think you can pass panic=5 on the kernel line in grub as well.

It's a decent temporary solution so that the server daily uptime is better (not that is has crashed in the past two weeks, *knock on wood*). Since it's a mythtv server in the basement it's important that if there is failure it at least restarts.

Problem is I don't think kernel.panic=5 will do anything since the crash is so bad the REISUB sysreq trick doesn't even work.

---

### Post by cytg on 2008-02-08
there were a kernel update some days ago .. still freezes

---

### Post by blackvd on 2008-02-08
I just started having this problem yesterday. Gutsy froze on me 5 or 6 times when trying to install Vector Linux in VirtualBox. I just figured it was VirtualBox but today it did it again while running Azureus, Nicotine+,pidgin,gmail notify, and Last.fm(which i think caused it). What's weird is this is the first time I have ever had a Linux distro completely freeze on me, i.e. I could always use alt+ctrl+F1 to stop whatever was locking up my box.

---

### Post by koresko on 2008-02-10
I started seeing random freezes on my Acer 5100 laptop (AMD Turion single processor, ATI onboard graphics with open-source driver (and no compiz).  The freezes typically happen after several hours of uptime.  There is no warning.  This box  was completely stable under Feisty.

So far the only workaround I have tried successfully has been to revert to Feisty's kernel (2.6.20).  I'm sorry to have to do that, though, because I suspect that there are security fixes the old kernel lacks.

The freezes do not seem to be related in any way to what programs are running.  I've seen it happen a number of times when I wasn't playing music or stressing the system, but just letting it sit idle while I did something else (sometimes the screensaver was running, sometimes not).

I thought it might have to do with the WiFi driver (Broadcom Air Force one) but switching between the open-source driver and Windows/ndiswrapper didn't affect it.

Will try disabling the APIC on the kernel command line (by editing the GRUB config file).  If that doesn't solve it, I'll give the i386 kernel a shot.

---

### Post by koresko on 2008-02-10
> **koresko said:**
> I started seeing random freezes on my Acer 5100 laptop (AMD Turion single processor, ATI onboard graphics with open-source driver (and no compiz).  The freezes typically happen after several hours of uptime.  There is no warning.  This box  was completely stable under Feisty.

So far the only workaround I have tried successfully has been to revert to Feisty's kernel (2.6.20).  I'm sorry to have to do that, though, because I suspect that there are security fixes the old kernel lacks.

The freezes do not seem to be related in any way to what programs are running.  I've seen it happen a number of times when I wasn't playing music or stressing the system, but just letting it sit idle while I did something else (sometimes the screensaver was running, sometimes not).

I thought it might have to do with the WiFi driver (Broadcom Air Force one) but switching between the open-source driver and Windows/ndiswrapper didn't affect it.

Will try disabling the APIC on the kernel command line (by editing the GRUB config file).  If that doesn't solve it, I'll give the i386 kernel a shot.

EDIT: I'm posting this using the i386 kernel.  Installing it was easy using Synaptic: I just installed the linux-386 package and rebooted.  The new kernel appeared at the top of the boot menu, but it was not the default, so I had to manually select it.  I changed the file /boot/grub/menu.lst to make it the default (changed the line "default=2" to "default=0".

Will see how this goes.  Disabling ACPI (the other solution that seemed to help some people) is not an attractive option on a laptop.

---

### Post by wolfear on 2008-02-10
> **wolfear said:**
> What ever the underlying cause ( or causes), it seems to be fixed in Hardy.

I tried every fix I could find and out of desparation, I finally did an upgrade to Hardy and so far, no freezes.

I get a few minor "hiccups" here and there (primarily when compiling an older program) but seems relatively stable so far and thnakfully, no more lockups.

Well, had to scrap that theory. The freezes started up again. No idea what  the (complete) underlying issue is, but I guess for me it's partially Nvidia related. I downgraded all the way back to Dapper and freezes started almost immediately after installing Nvidia drivers.
Of course, I also have an install of Gutsy which is not using the Nvidia drivers and it randomly freezes also, but not nearly as bad as the one using Nvidia.

As an aside, this issue also happened to me while checking out the current versions of openSUSE and Mandriva (when using the Nvidia drivers. Mandriva installed them by default, which was kinda cool).

Note: I should have specified: Things got worse after installing the drivers from Nvidia. It still freezes using the open source drivers, just not as often.

---

### Post by koresko on 2008-02-11
> **koresko said:**
> EDIT: I'm posting this using the i386 kernel.  Installing it was easy using Synaptic: I just installed the linux-386 package and rebooted.  The new kernel appeared at the top of the boot menu, but it was not the default, so I had to manually select it.  I changed the file /boot/grub/menu.lst to make it the default (changed the line "default=2" to "default=0".

Will see how this goes.  Disabling ACPI (the other solution that seemed to help some people) is not an attractive option on a laptop.

Edit again: I left the machine running overnight, suspended and resumed it a couple of times, and about 24 hours into the experiment there have been no problems at all.

So it looks like going to the i386 kernel cures the issue.  Hello, kernel maintainers!

Otherwise, I should point out that several other machines I have Gutsy running on (with the generic kernel) have shown none of the bad behavior.  So it seems to be hardware-specific.

---

### Post by koresko on 2008-02-11
> **koresko said:**
> Edit again: I left the machine running overnight, suspended and resumed it a couple of times, and about 24 hours into the experiment there have been no problems at all.

So it looks like going to the i386 kernel cures the issue.  Hello, kernel maintainers!

Otherwise, I should point out that several other machines I have Gutsy running on (with the generic kernel) have shown none of the bad behavior.  So it seems to be hardware-specific.

Edit 3: Wow, just a few minutes after I posted that all was well with the i386 kernel, it froze up on me.  Ugh!

---

### Post by ninkasi on 2008-02-11
> 
I think you can pass panic=5 on the kernel line in grub as well.


Yup. Stacks of things you can put into the kernel boot - a full list is in the documentation sub directory if you have the kernel sources (Documentation/kernel-parameters.txt). "usbcore.blinkenlights=1" is a favourite....

Anyhow, my (was ubuntu, now gentoo) server is happily bouncing like a rubber ball once a day or so, and I'm playing with switches to see if anything reduces/removes the problem. It has only frozen completely (ie unable to reboot) the once in a few days.... which is sort of promising... sigh...

Interesting to see that the number of reports of problems at [kerneloops]("http://www.kerneloops.org/") has really gone up recently. Of course that could be due to more people reporting issues, but still.....

Will report back if/when I resolve this.

Cheers

---

### Post by cytg on 2008-02-12
I got around to messing with the kernel options and added these to the mix

highres=off nohz=off noapm

And im on my second day now with no crash .. and its not like i havent been youtubing etc.. doing the stuff that usually makes it blow up.

So far so good :)  (if only i knew what those kernel options ment !!)

---

### Post by koresko on 2008-02-12
> **cytg said:**
> I got around to messing with the kernel options and added these to the mix

highres=off nohz=off noapm

And im on my second day now with no crash .. and its not like i havent been youtubing etc.. doing the stuff that usually makes it blow up.

So far so good :)  (if only i knew what those kernel options ment !!)

I'm following your suggestion here, running the generic (default) kernel again.  Will post my results in a couple of days is all's well, or sooner if I get another freeze.

Of course, there was another kernel update out today, so if it doesn't freeze it won't be clear whether it was the above parameters or the kernel update that did the trick.

With regard to the meanings of kernel parameters, 'man bootparam' is supposed to tell you.  Unfortunately, the info there looks at least 5 years out of date!

---

### Post by ed_x on 2008-02-13
The kernel update of today was related to a root access issue, so a security update only.

---

### Post by Ecclesia on 2008-02-13
I'm having issues with freezing as well.  This seems to go back to the thread's original issue of sound, but I didn't see anyone else with some of the strangeness I see so I'll note it here.

So far I've only noticed it after running a program playing mp3s.  Totem seemed to be the worst offender, so I got rid of it entirely and switched to mplayer.  I'll see if it continues to crash using mplayer and rhythmbox, I'm guessing it might.  The strange thing here was that the crash would start slowly and build up.  First thing I would notice was that Nautilus wouldn't be able to access files/directories.  It would report that directories didn't exist.  I could access the directories and files using the terminal, however.  Then things in gnome would stop working and slow down tremendously.  If I caught the odd behavior soon I could log out to restart, although the logout window would take a long time to pop up.  If I didn't catch it I'd eventually get to a hard freeze (and came back to my computer once to see the flashing keyboard light kernel panic).

It did crash once while compiz was off, so I don't think that's the issue.

I'm running a fresh install of Gutsy (default kernel) with the NVidia beta drivers (my card will not work without them).  I'm using two sata drives (no ide) both with ext3.  Someone mentioned a file system issue and sata.  Has anyone had these problems using a different file system?  I wouldn't mind a reformat to Reiser if that would solve the problems (I'd be kicking myself though, because I my gut told me to use it from the start and I figured I would go with the defaults).

---

### Post by cytg on 2008-02-13
nope.. just froze .. a little stutter and ... FREEZ


for f's sake allready bbq ******* this sh is ...... AAAAAARGH

---

### Post by cytg on 2008-02-13
allright .. all of you frozen players, what kind of soundhardware are you using ?

i am using some onbord construct ;

     *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0

---

### Post by Ecclesia on 2008-02-13
This is what I get from lspci -v (is that what we're looking for here... I'm kind of a newb)

00:09.0 Audio device: nVidia Corporation Unknown device 07fc (rev a1)
        Subsystem: nVidia Corporation Unknown device 07fc
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at efff8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

There's lots of unknowns on the lspci.  I have a fairly new board EVGA 530/7150.  I had to use linux-backports to get the sound working.  Also I noticed that I have some choices on the sound preferences.  I'm not sure if this is normal (I was using elive on a different machine before this, everything is set up differently and almost everything on my old computer worked out of the box with elive).  Under "Device" I have the choice between:

 HDA NVidia (Alsa mixer)
Realtek ALC883 (OSS mixer)

The HDA choice was default.  I haven't played with these settings.  From the looks of it the HDA probably stands for high def audio and is in surround.  I don't use it, so does this mean I should switch to the Realtek?

After crashing three times yesterday I've had no crashes today, but have also not used the sound at all.  I've mostly used firefox, gimp, and Kompozer with no issues.

---

### Post by Ecclesia on 2008-02-13
Something I forgot to mention:

I have this odd issue where the sound buzzes mildly (sounds like 60 cycle hum) when I do certain things.  Mostly this is when I move the window sliders.  Particularly this is an issue in firefox, but it happens every time I touch a slider.  It's pretty annoying.

---

### Post by dodgingspam on 2008-02-13
My Compaq laptop freezes even when I run only FireFox. It's gotten worse after couple of the latest updates.

---

### Post by ninkasi on 2008-02-14
OK

For me, my server seems to be a lot more stable. My fix - remove a bank of ram. Now, I don't believe that I had/have faulty ram because I had the same issue with a different server and different ram - I suspect that maybe the newer kernel is a little more sensitive of timing issues.....

Anyhow, I'm starting to think that maybe I may be suffering from the [Core2 memory corruption]("http://en.wikipedia.org/wiki/Intel_Core_2_Duo") and associated issues so - for me at least I'm just going to run with half the amount of ram and hope that the kernel will be updated soon to address (no pun intended) the TLB issue.

So - keeping in mind that if your server/workstation is locking up it may be caused by video drivers or hardware issues or a host of other things - but if you are running a Core2 X6800, E6000 or E4000 (I have an E4500) you *might* be suffering from the "improper TLB invalidation" bug. For me, dropping down to a single bank of ram meant that the motherboard was not doing the fancy DDR doubling so in turn I suspect is now less susceptible to memory faults..... probably not totally safe, though. Ah well.

---

### Post by Ecclesia on 2008-02-14
For those of you who are experiencing freezes with sound applications:

I removed Totem, since that had been used at some point before each of my crashes.  I then switched the system from gstreamer to xine.  I have been playing lots of mp3s, sound, and video today and yesterday using mplayer and VLC, no crashes (also Cinelerra, Kino, and Kdenlive - which I like although it crashes way too often). So I went from three system crashes in a couple hours to none in 48.

I might go through many of the music players to see if each of them works without crashing starting with Banshee then Rhythmbox.  For some odd reason Amarok would cause my processor to work like crazy any time I updated the music library, this would continue even after I had completely closed Amarok.  Never had that problem when I started with elive on an old laptop.

I'm not pleased with the sound from this board (whether it's connected or not to the crashes - I don't know).  I might have to throw in a soundblaster or something.

---

### Post by koresko on 2008-02-15
Does your machine still freeze if you play your music off a thumb drive, or off an Internet site?

I'm thinking the freezes might be caused by problems reading the hard disk; playing music means you're doing that continuously.

---

### Post by cytg on 2008-02-15
> **Ecclesia said:**
> For those of you who are experiencing freezes with sound applications:

I removed Totem, since that had been used at some point before each of my crashes.  I then switched the system from gstreamer to xine.  I have been playing lots of mp3s, sound, and video today and yesterday using mplayer and VLC, no crashes (also Cinelerra, Kino, and Kdenlive - which I like although it crashes way too often). So I went from three system crashes in a couple hours to none in 48.

I might go through many of the music players to see if each of them works without crashing starting with Banshee then Rhythmbox.  For some odd reason Amarok would cause my processor to work like crazy any time I updated the music library, this would continue even after I had completely closed Amarok.  Never had that problem when I started with elive on an old laptop.

I'm not pleased with the sound from this board (whether it's connected or not to the crashes - I don't know).  I might have to throw in a soundblaster or something.

I never ever use totem .. always vlc.
and vlc doesnt need to be running .. just firefox and flash.. to crash
actually i had a crash that was only vlc and no flash (firefox was running though, perhaps an ad?)

---

### Post by sparky64 on 2008-02-17
Just recently i have also been suffering complete system lockups.
"no mouse-sound loops-network stops and when it locked just as i sent a file to print only half the doc printed. (when i rebooted the file automatically resent and printed as soon as i logged on.)
This has only started about 3 weeks ago.
I  re-installed system and had a freeze within 1 hour. So i ran mem test for 24 hours with no probs, I then checked my bios and found my custom settings had re-set to standard.
It is part of the features of my board that if you have several sudden shutdowns it resets to default?.(had a lot of power outs due to supply cable fault - Must buy a ups)
So after turning off cool and quiet - And all auto settings for o/clocking memory settings back to manual.(for some reason in auto my ddr400 runs at 333 in d/channel mode.)
I have run for 3 days with no problems."touch wood"
Have also uninstalled powernowd.

---

### Post by ninkasi on 2008-02-18
> **sparky64 said:**
> for some reason in auto my ddr400 runs at 333 in d/channel mode.)
I have run for 3 days with no problems."touch wood"

and after dropping to one stick of ram (unfortunately my cheap board doesn't have many user changeable options eg I can't choose to turn off the dual channel) my server has now been up for 7 days straight.....

---

### Post by jesushero on 2008-02-18
Ok, so here's my research: 

I've been using my machine without the Gnome (no gui at all, just tty) and it never crashes. When using gnome, it seems fairly stable until Java or Flash are put to any use. I have been using SSH with a machine that is very similar to mine, running the Desktop Ubuntu (I'm running Ubuntu Studio) and when the Gnome crashes (the user who is sitting there can't do anything) I can still work on ssh for as long as I like. Top doesn't reveal anything zombified, and killing Xorg or Gnome would not change much. The screen remains frozen and no keyboard or mouse control is available for the local user. However, the only part where ssh is unable to over-ride the crash is the reboot command. When given a sudo reboot now command, the procedure starts "System going for reboot now!!" but stays at that and freezes. The computer does reboot and the local user can use it again, but if the remote user (myself on ssh) does not kill the ssh client that has frozen, the machine will not register with the router and will remain offline. 

So, while the computer is frozen for the local user, the ssh user can see no difference. The CPU works fine, the ram as well, the hard drives, top will show all processes running normally, network speed is normal, programs start and stop efficiently. So I am guessing the whole problem is with the display. Graphics cards maybe? We both have nVidia cards and experience very similar crashes. Every part of the computer can be verified to work apart from the graphics. 

I hope this is some helpful information. If anybody finds the cause of the crashes, let me know!! If anyone can think of a certain test (for a repeatable crashing pattern) I will be more than happy to try it out.

---

### Post by koresko on 2008-02-18
> **jesushero said:**
> Ok, so here's my research: 

<snip>

So, while the computer is frozen for the local user, the ssh user can see no difference. The CPU works fine, the ram as well, the hard drives, top will show all processes running normally, network speed is normal, programs start and stop efficiently. So I am guessing the whole problem is with the display. Graphics cards maybe? We both have nVidia cards and experience very similar crashes. Every part of the computer can be verified to work apart from the graphics. 

I hope this is some helpful information. If anybody finds the cause of the crashes, let me know!! If anyone can think of a certain test (for a repeatable crashing pattern) I will be more than happy to try it out.

<snip>


This problems sounds very different from the complete freezes I used to see (which seem to have been cured by turning off the 'tickless' code in the kernel).  My crashes took the machine down completely - you couldn't even ping it, much less connect via ssh.

My guess is that it's a graphics driver issue.  Are you running the closed-source NVIDIA module, or the open-source one?  I have found the open-source driver to be significantly more reliable, so if you're not running that you might give it a try.

In either case, is it possible to tell what the status of your X-server is, e.g., from /var/log/Xorg.0.log, after a crash?  I assume that your console still shows the (frozen) desktop.  Does ctrl+alt+backspace (zap the X-server) work?  Have you tried turning off features in the X-server (reducing the number of modules it loads)?

Just some stuff to try if you have time and energy.

---

### Post by Ecclesia on 2008-02-18
Well, it sounds like the problem is narrowing down although each person who posts has quite different issues in many ways.

I doubt that I could ssh to my computer after a crash.  Today I had the first crash in three days.  I returned to my computer and found that the num lock and caps lock lights were flashing.  The screensaver was frozen in position.

Today I also tried installing new software.  I tried Miro out (this was used most recently to the crash) as well as Songbird.  I had also, a while back, switched to metacity from emerald to draw the window boarders (I still use Compiz).  Today I was playing with the window borders again, so Emerald might also be an issue (it was running when the machine crashed).  For those who were able to get rid of the crashes by not using Compiz, I wonder if you were using emerald as well (although I'm pretty sure it uses metacity by default with compiz).

If this is connected to video, I'm using the 169 beta drivers, and I think it's either that or Vesa with my card (I have an integrated geforce 7150).  If I could solve this issue by installing a different card I would.  I was thinking about putting an 8600 in anyway.  I'm assuming this would allow me to use the stable drivers (although it sounds as if the beta drivers have been more stable for some people).

---

### Post by cytg on 2008-02-19
> **cytg said:**
> I got around to messing with the kernel options and added these to the mix

highres=off nohz=off noapm

And im on my second day now with no crash .. and its not like i havent been youtubing etc.. doing the stuff that usually makes it blow up.

So far so good :)  (if only i knew what those kernel options ment !!)

I posted this about 6 days ago .. and then a few hours later posted again informing of yet another crash. I then decided to give it a run more (same kernel settings) and havent had a crash since.. so in just over a week i've had just one crash .. thats a major improvement if the statistics hold (or get better ;) .. still holding out for a permafix though ? hehe

---

### Post by HDave on 2008-02-19
For what its worth, part of my freezes where due  to a (now) known issue with TrueCrypt and the Gutsy kernel.  An upgrade to the Hardy kernel has solved this problem for me (2.6.24-7).

(link requires account)
[http://forums.truecrypt.org/viewtopic.php?t=9129]("http://forums.truecrypt.org/viewtopic.php?t=9129")

I am still experiencing frequent lockups with Compiz on and infrequent lockups with Compiz off.  However in my case I am starting to suspect that it is due to cpu overheating.  Most everytime my system freezes conky is reporting my 2GHz dual-core Intel at 67 C or hotter...which I believe is near the upper range.

I am now running throttled back to 1GHz with Compiz on to see what happens.

---

### Post by roaldz on 2008-02-19
Didn´t read all pages, but I think it´s Compiz-related. If I shut down compiz and go into sleep, it will wake up fine. If I leave compiz running, turn into sleep, and then wake it up, it will hang.

Found a litte trick so you don´t have to reboot your kernel:

Do the ALT-SysRQ thing (alt printscr) with R E I (no **S**ync **U**mount re**B**oot) , that will give you a terminal on ALT-F1 (at least is does for me). Then login as root and type this command:
```
telinit 1
```
Then type CTRL+D

Voila:)

Hope it helped, if so, please thank me

Roald

---

### Post by jesushero on 2008-02-19
> **koresko said:**
> This problems sounds very different from the complete freezes I used to see (which seem to have been cured by turning off the 'tickless' code in the kernel).  My crashes took the machine down completely - you couldn't even ping it, much less connect via ssh.

My guess is that it's a graphics driver issue.  Are you running the closed-source NVIDIA module, or the open-source one?  I have found the open-source driver to be significantly more reliable, so if you're not running that you might give it a try.

In either case, is it possible to tell what the status of your X-server is, e.g., from /var/log/Xorg.0.log, after a crash?  I assume that your console still shows the (frozen) desktop.  Does ctrl+alt+backspace (zap the X-server) work?  Have you tried turning off features in the X-server (reducing the number of modules it loads)?

Just some stuff to try if you have time and energy.

I haven't tried connecting to the machine remotely after the crash, although I doubt it would work. If the ssh connection was alive before the crash, it will stay alive and will work perfectly. I have kept ssh connections open for several hours (around 24 hours) by running the top command to keep it from timing out. Once a remote user is successfully logged in, I have never experienced any crash apart from trying the reboot command or the local user shutting it down (in which case it doesn't crash, just disconnects). I'm guessing that theoretically, if the computer freezes for a local user and they just turn the screen off and keep the box running, the ssh could go on for months with the computer totally useless for the local user. We're both running the rt kernel now, which seems to have reduced crashes on the Ubuntu Desktop system, especially audio-software related.

We're both using the Open Source NV drivers. I did use the Nvidia ones for a short while but things were much worse!!! The NV ones are much more stable.

---

### Post by cwgannon on 2008-02-19
I had a similar problem that I resolved using AOSS: AOSS guide at [http://planet-geek.com/archives/003048.html]("http://planet-geek.com/archives/003048.html").

If somebody experiencing this problem could try running the applications most oft associated with the freeze through AOSS (see the guide for instructions; mine were Amarok and Firefox), maybe we'll have some luck.

---

### Post by cytg on 2008-02-19
> **HDave said:**
> For what its worth, part of my freezes where due  to a (now) known issue with TrueCrypt and the Gutsy kernel.  An upgrade to the Hardy kernel has solved this problem for me (2.6.24-7).

(link requires account)
[http://forums.truecrypt.org/viewtopic.php?t=9129]("http://forums.truecrypt.org/viewtopic.php?t=9129")

I am still experiencing frequent lockups with Compiz on and infrequent lockups with Compiz off.  However in my case I am starting to suspect that it is due to cpu overheating.  Most everytime my system freezes conky is reporting my 2GHz dual-core Intel at 67 C or hotter...which I believe is near the upper range.

I am now running throttled back to 1GHz with Compiz on to see what happens.

Funny how every time i post here, right after (or within the hour) ill crash .. so it was again today. Anyway, in reply to this post, i have truecrypt installed but dont use it, i've gone encfs instead due to ... issues with truecrypt.. Maybe thats still whats bugging me?

---

### Post by Ecclesia on 2008-02-19
I just ran into[ this thread http://ubuntuforums.org/showthread.php?t=579586]("http://ubuntuforums.org/showthread.php?t=579586")

It mentions getting lockups on Nvidia 7XXX and some 6XXX cards.  Is anyone having  this problem with an 8XXX?

---

### Post by SmoshySmosh on 2008-02-20
I am getting the same problem when using terminal and Firefox and basically anything... I am using a NVIDIA 8800GTS 640MB

---

### Post by roaldz on 2008-02-20
> **Ecclesia said:**
> I just ran into[ this thread http://ubuntuforums.org/showthread.php?t=579586]("http://ubuntuforums.org/showthread.php?t=579586")

It mentions getting lockups on Nvidia 7XXX and some 6XXX cards.  Is anyone having  this problem with an 8XXX?

Yeah, that could be possible. I have a Nvidia 7600 Go, do you guys have the flashing black screens too? These little things start to annoy me.

---

### Post by anthonyJC on 2008-02-21
I thought I fount a kernel bug and posted it on RedHat bugzilla (see my report from post [http://ubuntuforums.org/showpost.php?p=4268379&postcount=106](http://ubuntuforums.org/showpost.php?p=4268379&postcount=106) ) :-) but a REDHAT KERNEL MAINTAINER has told me it's memory corruption. I ran mem test for eleven hours  prior, so thought there was not a chance it was memory. I've  turned on CRC checking-i left it off because i thought memory corruption would be extremely rare as i don't over clock anything. Unfortunately I don't know what part of the kernel message tells me it's  memory?

---

### Post by HDave on 2008-02-22
Hi Folks -- OP here...

Through the help of the people here and elsewhere I believe I have found the root cause(s) and solved my freezing problem.  Here's the details:

1) The number one cause was found to be a problem with nVidia GPU in combination with SMP.  The "PowerMizer" capability of nVidia shifts the GPU frequency up and down in respose to demand.  For whatever reason, doing this when you have a multi-core CPU causes lock-ups.  nVidia has been working this issue for 18 months with some success, but it still any issue on many cards (including mine).  The work-around is to lock the GPU at max frequency, which raises core temp by a few degrees, but eliminates the freezing.  See this thread for a description of the problem:

[http://www.nvnews.net/vbulletin/showthread.php?p=1565966#post1565966]("http://www.nvnews.net/vbulletin/showthread.php?p=1565966#post1565966")

and this thread for the workaround:

[http://www.nvnews.net/vbulletin/showthread.php?t=96673&page=3]("http://www.nvnews.net/vbulletin/showthread.php?t=96673&page=3")

2) The second cause of lockups a kernel error that truecrypt exposed.  It would freeze the whole system.  The solution was to upgrade Gutsy to the latest kernel 2.6.24-7.  This cause 18 other problems, but at least the freezing was gone.

3) The third cause of lockups was my Deluge bittorrent client.  Apparently if an application maxes out network throughput in a certain way it can cause system lock-ups.  Deluge has put out a fix for this and now it no longer freezes.  I have read that other bittorrent clients still cause freezing though...so be careful.

4) Certain screen savers will lock up my system (i.e. Braid and a few others).  Workaround: disable screensaver.  This is a known suspend problem with the nVidia driver.  See the following bug reports for more info:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/103400]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/103400")
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/101943]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/101943")

I am now running compiz and everything I want without any freezes (for 3 days).  From reading all the posts here, it is clear to me that there are still more causal factors than the 3 I have discovered.  Keep testing, talking, and reporting bugs and sooner or later we'll all get to the bottom of this nasty issue.   

I think it is worth noting that the nvidia bug can only be observed if you hook up a text terminal to your computer that immediate displays dmesg output -- that you can read after your system freezes.  In other words, once your system freezes, it is typically too late to determine the root cause because the error can't get written to the log file unless you are one of the lucky ones who can unfreeze the system via REISUB.  So get creative...

---

### Post by cdean on 2008-02-22
I'm getting mouse freezes, as well, but only when I connect certain USB mass storage devices, such as a Sandisk Ultra II USB/SD card (one of those SD cards with a built-in USB adapter). It's also happened to a Kingston flash drive.

Interestingly, only the mouse freezes. I can still type on my USB keyboard and I can use the OS with the keyboard. Killing X does not fix it, nor does connecting another mouse. The only way I've found to fix it is to reboot. dmesg shows no errors, either.

---

### Post by photismos on 2008-02-22
I'm very new to Linux, but I was having very similar errors....random freezing (even restarts at times) but usually still able to use my mouse, although to no avail since nothing was selectable, and of course the keyboard was completely useless (frozen)...nothing worked. It was happening intermittently, wondered if it was Firefox or my movie player or my NVIDIA driver something I was doing...NOT SO!  

I searched a few threads here and found that editing "/boot/grub/menu.lst" adding just two little words..."noapic nolapic" fixed it COMPLETELY. Since then I've had no freezes at all.

Here's where the those "words" went in the context of my menu.lst, if it helps you to know where to put it:

## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-rt
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-rt root=UUID=56ef75eb-5ce9-4863-a4ee-2d4d2a167847 ro noapic nolapic quiet splash
initrd /boot/initrd.img-2.6.22-14-rt
quiet

...AND that's it. you put it in that "kernel" line and restart. Hope it helps. If it does, would be nice if you confirmed that for others... =) That's what I'm doing...trying to find the original thread(s) I found this solution in to confirm it works! =D ...well, again...hope it helps!

---

### Post by Ayuthia on 2008-02-23
This has been a very interesting thread!  I am currently running and AMD Turion 64-bit chip with an Nvidia 6150 Go on an HP laptop.  Generally, my lockups would occur while booting so I ended up using noapic noirqdebug as my kernel parameters (noapic nolapic worked for me prior to 2.6.17 kernel and with the newer kernels it will cause me to lose my USB ports).

I have heard (but not tried) that the Hardy 32-bit version worked without the noapic option.  I thought that the change had something to do with the AMD chip and dynamic clock ticks but I could be mistaken.  However the fix is not in the 64-bit version.  I think that the work is on the kernel end and not Ubuntu.

HDave's findings seem to be very promising and seem to match up with a lot that I have been seeing also although I have to say that I have not seen the workarounds that he has provided.  The workaround that he posted seems to work for some but there are some reports showing that there are problems cropping up in the 169.07 version.

For those of you that have been experiencing hard lockups, have you been monitoring your chip temps?

I have also seen that flash has caused my laptop to heat up.  Since I am using the 64-bit version, I have to use nspluginwrapper to make flash work.  So when the temps start going up on my laptop for no reason, I usually see that nspluginwrapper (libflashplayer.so) is running and I kill the process.  That usually brings my laptop temps back to normal.

Not for sure if any of this will help any of you or not, but it has been what I have run into during my Linux journey.

---

### Post by spamgoat on 2008-02-23
Not much to say other than I can confirm this problem as I am experiencing it as well.

I'm running a Dell 9300, Intel processor, ATI x300, Ubuntu Gutsy.

I do use Deluge torrent, and I also find the problem is more likely to occur the higher the uptime of my laptop. The 8 day mark seems magic for me.

Finally, as either an oddity or a way for others to confirm they have the same problem i'm having, whenever it happens my internet drops and my gDesklets 'widgets' turn white entirely. That's how I know i'm about to enjoy a system freeze, and start holding hold reset while sobbing profusely.

---

### Post by barboachtraner on 2008-02-23
I installed Ubuntu 7.10 a little over a month ago, and since then on a number of occasions my system has frozen and won't respond to any keyboard or mouse input. The first time this happened I got a totally blank screen trying to reboot, which agitated me. I ended up solving that problem by using the command *sudo dpkg-reconfigure xserver-xorg* in the recovery console, but doing that reset my graphics driver to intel. Using the intel driver in 1280x1024 resolution caused the image on my screen to be off center with empty black space on the right side, so I had previously switched to the i810 driver and switched to it again after dealing with the other problem. The same freeze has happened a few more times since then, including today, and every time it has happened I used  *sudo dpkg-reconfigure xserver-xorg* again for a temporary fix. My graphics card is an Intel 82845G. I figured this problem was somehow related to the graphics driver, since I couldn't think of anything else involved in reconfiguring X that would deal with the blank screen...

I didn't read a lot of this thread, but the first post mentioned the issue being related to sound, whereas I haven't noticed any particular pattern as to when these freezes happen. I don't know if it's related but I didn't want to make a brand new freezing thread when this one was right on the front page.

---

### Post by roaldz on 2008-02-23
> **spamgoat said:**
> Not much to say other than I can confirm this problem as I am experiencing it as well.

I'm running a Dell 9300, Intel processor, ATI x300, Ubuntu Gutsy.

I do use Deluge torrent, and I also find the problem is more likely to occur the higher the uptime of my laptop. The 8 day mark seems magic for me.

Finally, as either an oddity or a way for others to confirm they have the same problem i'm having, whenever it happens my internet drops and my gDesklets 'widgets' turn white entirely. That's how I know i'm about to enjoy a system freeze, and start holding hold reset while sobbing profusely.

Can´t you do a SysRQ REISUB?

---

### Post by spamgoat on 2008-02-23
I've tried numerous times, and I cannot. I cannot ctrl+backspace, I cannot ctrl+alt+Fn, and I can't even reisub. :( Once the 'process' starts, the only way to get out of it is a hard reboot. And get out of it I do want, as the system just freezes (including mouse).

---

### Post by Warprunner on 2008-02-23
> **spamgoat said:**
> Not much to say other than I can confirm this problem as I am experiencing it as well.

I'm running a Dell 9300, Intel processor, ATI x300, Ubuntu Gutsy.

I do use Deluge torrent, and I also find the problem is more likely to occur the higher the uptime of my laptop. The 8 day mark seems magic for me.

Finally, as either an oddity or a way for others to confirm they have the same problem i'm having, whenever it happens my internet drops and my gDesklets 'widgets' turn white entirely. That's how I know i'm about to enjoy a system freeze, and start holding hold reset while sobbing profusely.

I have a NC6320 HP Laptop. Mine was freezing after really screwing everything up with Conky and a number of other things :) But I did it to myself.
After the reload, I decided to enable my WiFi as well. But with Compiz and Conky and the rest...really thought I had it narrowed down to the Emerald themes. 
Nope! Reloaded again and waited for it to freeze. Never did until I enabled the WiFi card. So I will stay hardwired for now.
I really don't want to fool with the wrappers as my Laptop really sits on my desk 99.9% of the time. But that is EXACTLY what was freezing mine. No doubts.
Hope this helps someone scratching their heads.
Warp

---

### Post by hormati on 2008-02-23
I have Gutsy on my desktop machine with the the following specs:
* CPU: E6700 Core 2 Duo 2.66
* Ram: 2GB DDR3
* Motherboard: Gigabyte PS35
* Graphic Card: Nvidia 8400GS
* I use the on-board sound card
* I have a wireless wifi card

I'd had these freezes until I did couple of things:

1- Uninstall powernowd. I don't need it, cpufrequtils would do the job. Unistalling powernowd does not mean I do not have freq scaling. I still can control cpu freq scaling through the gnome panel applet.
 
2- Uninstall NetworkManager. Again, I don't need. This is my home machine, and I  can manually set the wireless connection settings once and i know that I am not going to change it for a long time. So, I don't need NetworkManager.

3- Upgrad to the latest version of Nvidia drivers.

4- Stop using compiz. 

After doing all these, I have not had any freezes for the past 2 weeks. I used to get hard freezes once every 2-3 days(Sometimes more), mostly(but not always) while I was watching flash in firefox. They are definitely gone. 

Since I like compiz so much, I am going to enable it again, and see if that brings the freezes back. :)

Amir

---

### Post by KD6TZF on 2008-03-31
I don't know if this is related or not, and I haven't seen anything posted here about this problem, but in addition to the freeze problem - my Desktop is not being displayed.  The folder is there and using Places, I can access it.  But when I close all my programs instead of seeing a regular background, I get nothing.  Not even the items that are in the Desktop folder.  Just a blank Tan/Orange screen.  Suggestions anyone?

Thanks for listening,

---

### Post by cdean on 2008-03-31
That happens to me whenever I've killed X more than once. Only solution is to kill X again and reboot from the login screen or switch to a console and do ```
sudo reboot
```.

---

### Post by KD6TZF on 2008-03-31
> **cdean said:**
> That happens to me whenever I've killed X more than once. Only solution is to kill X again and reboot from the login screen or switch to a console and do ```
sudo reboot
```.

As someone else has said - been there done that - the problem remains.

Any other suggestions? :confused:

---

### Post by HDave on 2008-03-31
I would open a new thread on this subject as it is a seperate problem from the freezing.  For what its worth, I occasionally (1 times out of 15) boot up to see a black desktop.  I believe this is because Nautilus failed to start or errored-out.  Like the previous guy said...only work-around is to reboot.

No idea what the solution is...perhaps a launchpad bug search is in order...

---

### Post by ikekrull on 2008-04-01
Personally, i've found Ubuntu Gutsy is absolutely unusable with AMD64 based systems. Random crashes, all the time. It might be free and open source, but its rubbish for getting work done.

I bit the bullet and upgraded to Hardy Beta, and while i had to deal with issues that would more than likely leave new users or people who aren't familiar with linux intricacies completely screwed (lets just say the upgrade didn't go perfectly) , I can say that the 2.6.24 kernel is rock stable where 2.6.22 was a horrorshow of lockups and freezes.

Its amazing how fast the anger and frustration disappears once you realise your system is working as it should, but while I was struggling with Gutsy, man did I want to break things.

 Ubuntu devs, please put a big 'NOT SUITABLE FOR MODERN AMD64 HARDWARE' notice on the gutsy download page, you might save a lot of people a lot of grief.

---

### Post by KD6TZF on 2008-04-06
> **HDave said:**
> I would open a new thread on this subject as it is a seperate problem from the freezing.  For what its worth, I occasionally (1 times out of 15) boot up to see a black desktop.  I believe this is because Nautilus failed to start or errored-out.  Like the previous guy said...only work-around is to reboot.

No idea what the solution is...perhaps a launchpad bug search is in order...

I would mark this problem solved if I knew how.  My solution was to restart Nautilus using Alt-F2.  Apparently somewhere in trying to work around the Freeze problem, while Nautilus was shut down, (I didn't do it that I know of) the session was saved without Nautilus running.  Subsequently it was never restarted.  Thanks to all for your comments.

:lolflag:

---

### Post by AlphaMack on 2008-04-10
I'd hate to add a 'me too' to this thread, but the random freezes with Gutsy is driving me up the wall.  I have a brand new Thinkpad R61i with the Intel Pentium dual-core and integrated 965 video.

Gutsy will freeze (unmovable mouse pointer + flashing Caps/Num Lock) with or without Compiz (even with the patched video driver to enable it), with or without a screensaver, with nothing else running, or with several apps open.  There seems to be no pattern to it.  All I know is that after leaving it running all night I wake up the following morning to find it frozen or coming home from work to find it frozen after having rebooted it in the morning.

I'm seriously tempted to downgrade to Feisty or upgrade to Hardy beta.

---

### Post by HDave on 2008-04-10
@alphasubzero949

If you have compiz, and your screensavers disabled and it still locks up, the only other thing I can think of is to try and disable SMP to add another data point.

But triple check to ensure you have compiz and screensavers disabled.

You could also google your graphics card to see if freezing has been reported.  I was at my wits end when I found out that my specific model of nvidia had a problem...thankfully there was a work-around.

---

### Post by AlphaMack on 2008-04-11
After enough fiddling around it's either down to Compiz or the screensavers.  Both seem to be culprits for crashing according to other posts.  I disabled both (blank screen for the 'screensaver') and so far so good.  I'm going to keep my fingers crossed.

Disabling SMP didn't seem to work as the kernel would no longer load, forcing me to drop into a shell and change the GRUB menu.lst back.

---

### Post by cytg on 2008-05-03
figured the weekly freeze or so was worthit until hardy came out.
hardy came out
and hardy freezes like a moth........ at least once pr day.

:(

---

### Post by HDave on 2008-05-03
Ditto here...

I am very sorry to report that Hardy hasn't fixed this problem in the least.

They fixed more than a dozen issues I have been having, but not this one.

For me, I am looking to nVidia at this point.

---

### Post by cytg on 2008-06-21
Figured i owed a feefback here as well ..

I dont know what happend, or rather what update did it, but i suspect an updated nvidia driver.. anyway, freezes are gone, rock solid system :-)

---

