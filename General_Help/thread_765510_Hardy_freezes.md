---
title: "Hardy freezes"
date: 2008-04-24
forum: General Help
---

### Post by revelationman on 2008-04-24
I have installed it seems everything is fine then bang it just freezes and locks up I have to do a hard reboot. 

Hard reboot is not good for your hard drive  i am not happy about this i am banging my brains out  on a solution

I have the ati 1150  and broadcom  

any suggestion

---

### Post by quadomatic on 2008-04-24
> **revelationman said:**
> I have installed it seems everything is fine then bang it just freezes and locks up I have to do a hard reboot. 

Hard reboot is not good for your hard drive  i am not happy about this i am banging my brains out  on a solution

I have the ati 1150  and broadcom  

any suggestion

This is most definetly related to the har locks issue that was going on with both the Beta and the RC. The theory is that it's related to the wireless drivers. But, this is present on a vast array of wireless devices.

I love Ubuntu, but I'm staying off of it till wireless gets fixed.

---

### Post by revelationman on 2008-04-24
> **quadomatic said:**
> This is most definetly related to the har locks issue that was going on with both the Beta and the RC. The theory is that it's related to the wireless drivers. But, this is present on a vast array of wireless devices.

I love Ubuntu, but I'm staying off of it till wireless gets fixed.


It is very frustrating I do not want to go back to Windows but you cannot hard boot the pc you  will not have a hard drive very long 

i am hoping a developer can shed some light on this hardy is a good built it loads faster then gusty i am willing to stick by but if it freezes again i will have no choice but to look for a different distro

---

### Post by revelationman on 2008-04-25
I have more information from my syslogs

Apr 25 08:02:06 brian-revelationman kernel: [ 6635.421815] Freezing user space processes ... (elapsed 0.00 seconds) done.


Apr 25 08:02:06 brian-revelationman kernel: [ 6635.422743] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.


Apr 25 08:02:09 brian-revelationman NetworkManager: <WARN>  nm_device_802_11_wireless_get_mode(): error getting card mode on wlan0: No such device 

Apr 25 08:02:18 brian-revelationman kernel: [  156.170367] b43-phy0: Broadcom 4311 WLAN found

Apr 25 08:02:18 brian-revelationman pulseaudio[5784]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy

Apr 25 08:08:48 brian-revelationman kernel: [    8.944619] b43-phy0: Broadcom 4311 WLAN found

Apr 25 08:09:45 brian-revelationman gdm[5437]: WARNING: main daemon: Got SIGABRT. Something went very wrong. Going down! 

Apr 25 08:09:46 brian-revelationman avahi-daemon[5066]: Got SIGTERM, quitting.


I found some logs but I just do not know why the system just locks up and freezes 

From what I am reading on Hardy there has been a variety of problems,

I hope someone has some answer on this 

I will reinstall Hardy but if it happens again I might have to find another distribution for this laptop. I have heard that  Suse Linux is certified for this laptop. I hope there is a solution .

---

### Post by revelationman on 2008-04-25
I guess no one has a clue on this one it has frooze up again this the third time this has happened. 

It never frooze with gutsy so it is obvious the issue is with hardy sadly 

As they say someone has dropped the ball back to XP sadly till the bugs are ironed out

---

### Post by newUser1981 on 2008-04-25
I have the same problem! I'm really concerned about my hard disk but don't wane switch back to Vista.

Is there any bug report? Are the Ubuntu guys working on it? Can I help with information? 

Would be cool to know about the progress!

---

### Post by brethren on 2008-04-25
i have the same problem with 8.04 :( for me hardy randomly hangs with the cursor frozen, leaving me no option but to reboot. it was so bad that i couldn't even download the ati drivers (it kept crashing before the download finished)

at the mo i'm back on 7.10;)

---

### Post by dcollamore on 2008-04-26
I'm seeing the exact same issues with the following hardware specs:

Asus A8V motherboard
Athlon X2 3800+ Processor
1024MB Kingston DDR-SDRAM
160GB Seagate 7200.10 SATA HDD
Sony PATA CDRW
ATI Radeon X1950XT AGP
Onboard everything else

RAM, HDD both pass diagnostics, and I'm not seeing stability issues in Gutsy or Windows XP.  Video card and CPU both running cool.  This does not appear to be a hardware problem of any type; it's isolated strictly to my installation of Hardy.  I've wiped/clean slate installed three times, to two different (known good) hard drives.

I'm seeing this with or without restricted ATI driver, with Compiz on or off, and at completely random times.  So far I have not been able to catch any log data or terminal output.  Where should I be looking and what data can I provide to help troubleshoot this?

---

### Post by Mighty_Joe on 2008-04-26
I feel your pain.  I have a system that is rock-solid with 7.04. I use it as a personal web server, so it never gets shut off. I get months of uninterrupted uptime. 
I swapped out the hard drive, installed 8.04 and it freezes within minutes of booting. I can move the mouse, but the desktop is not responsive. CTRL-ALT-Backspace and CTRL-ALT-DEL do nothing. 
There doesn't seem to be any pattern behind the freeze.  It will happen when I'm browsing with Firefox, when I'm reading the logs trying to figure out the previous crash or just sitting there doing nothing.  
I tested and swapped out the RAM so that's not the problem.  Tested the hard  drive and it appears to be fine.

Gigabyte 7ZXE Mobo
AMD Athlon XP 2000+
1024 Mb RAM
ATI Radeon 8500 
250 Gb WD HD
DVD-ROM and DVD-RW

---

### Post by Invader Amoto on 2008-04-26
I was just looking around the forums to see if anyone else has this sort of problem and if they have any idea what it's cause by.
I think the original poster's problem may be different but read through this and see if it matches your problems.

[https://bugs.launchpad.net/ubuntu/+bug/204996]("https://bugs.launchpad.net/ubuntu/+bug/204996")

It's importance is set at high, so they should be working on it. Maybe there will be a fix soon.

---

### Post by dcollamore on 2008-04-26
Thanks for the tip!  I just finished reading through all the comments, and it appears to be describing exactly what I'm seeing.  

For anyone who runs across this, so far it looks like it's a problem with the GENERIC kernel, the SERVER kernel, and possibly the 386 kernel, but it looks like (possibly) the -rt kernel is stable, albeit at a slight performance hit.  This kernel should be in the standard repository, so nothing special needed beyond some apt-getting.  I'm going to give it a shot, I'll report back with what I find out.

---

### Post by dreamsR4living on 2008-04-26
I have the same problem. I am using Ubuntu since Dapper Drake and I have always been amazed with Ubuntu's stability. Within two years Ubuntu did only freeze for two or three times, but with Hardy it seem to happen 2 or 3 times a day.

My Hardware;

Acer Aspire 9302
AMD Turion 64, 2.2 GHZ
1 GB DDR2 Memory
Nvidia GeForce Go 6100 384 MD
Broadcom (BCM43) Wireless

When this problem continues, I will go back to Gutsy too

---

### Post by dcollamore on 2008-04-26
dreamsR4living - Have you tried the -rt kernel? If you open up a terminal window, and type in:

sudo aptitude install linux-image-rt linux-restricted-modules-rt

and hit enter, you can give that a shot.  I have nothing conclusive yet, but it hasn't hard-locked on me either.  It's worth a shot before downgrading to Gutsy.

---

### Post by dreamsR4living on 2008-04-26
>  dreamsR4living - Have you tried the -rt kernel? If you open up a terminal window, and type in:

sudo aptitude install linux-image-rt linux-restricted-modules-rt

and hit enter, you can give that a shot. I have nothing conclusive yet, but it hasn't hard-locked on me either. It's worth a shot before downgrading to Gutsy.

Thanx, I'm going to give it a try for a few days and will report my results later on

---

### Post by dreamsR4living on 2008-04-26
I have installed the RT Kernel, but the problem is still there. Maybe it is not a kernel related problem?

---

### Post by Mighty_Joe on 2008-04-26
Switching to the RT kernel did not solve my problem either.  Tried twice and got hangs within minutes of booting.

---

### Post by dcollamore on 2008-04-26
Hmm...mine (appears) to continue being stable.  I guess I'll have to wait and see.  On a related note, I just did a fresh install on my notebook (Dell Inspiron 8600, vastly different hardware), and it's been stable as a rock.  

This is going to be a real bear to troubleshoot.

---

### Post by rmccabe3701 on 2008-04-26
I installed hardy two days ago the freeze issue is unbearable.  My machine is a 
HP dc7700 2Gb RAM and an nvidia 5200 GeForce FX video card.  

I read on another thread that doing 
```
 sudo apt-get remove powernowd 
```

would help.  It did not.  I tried installing the nvidia driver directly from the nVidia website (not using the restricted driver manager) and this seemed to make things worse, i.e. the system would ALWAYS freeze up within 30-60 seconds of a boot.  So, I rolled back to the generic video driver and no more freezes -- however, this only supports a single monitor.  

So, the problem for me seems to be the incompatibility of Hardy with the nVidia driver (it worked in Gutsy).

Does anyone have any suggestions?

---

### Post by pete0085 on 2008-04-26
I have the same problems.  I installed Ubuntu for the first time 2 days ago and not sure what to do.  Fedora never locked up on me, but was more difficult for me to use as I don't honestly know what I'm doing in Linux.  I'm open to any suggestions???

---

### Post by dcollamore on 2008-04-26
pete0085 - As far as I can see at this point it's not been completely pinned down yet.  This issue seems to occur on vastly different hardware, and hard-crashes the kernel to the point that logging is very vague and inconclusive.  Some people report that it may be related (for them) specifically to their wireless card.  Others that it is related to the closed-source nVidia or ATI video drivers.  

This appears to be a rather serious and somewhat widespread issue, but sadly I do not have the skills or time necessary to completely pin it down.  I'd subscribe to this thread and watch for possibilities.  As soon as I see a real solution (provided someone else hasn't seen it first and posted it) I'll post it.  In the mean time, you can try installing the -rt kernel (see previous message for more details, or feel free to ask for more specifics if you need further help); this seems to be keeping my system stable so far.

I will say, I've used Ubuntu specifically since Hoary Hedgehog (Debian before that), and I've never seen as serious an issue as this in an initial release in all that time.  That concerns me in a LTS release.  I suspect the more "dynamic" development model of the kernel itself may have something to do with it.

---

### Post by rbmorse on 2008-04-26
Yes, it is a serious problem, but it's not a universal problem. 

I have two machines on 32-bit Hardy. One is an Intel D975XBX2 and the other a Gigabyte GA-EP35-DS3R, both with E6600 CPUs and 4Gb of RAM. Neither has the slightest problem and both have been up continuiously since the -16 kernel entered repository. 

So, I don't know what is going on, but whatever it is does not affect everyone.

---

### Post by dcollamore on 2008-04-26
Yes I've seen that as well.  My desktop (Athlon X2, socket 939, VIA chipset) is effected, but my laptop (Inspiron 8600, Intel chipset, Pentium M) is completely stable under extensive load of every type I can throw at it.  There hasn't been (to my knowledge) any commonality noted between effected systems.  It's a real head scratcher.

---

### Post by rmccabe3701 on 2008-04-26
rbmorse: Are you using a Nvidia card?

---

### Post by rmccabe3701 on 2008-04-26
I think I finally resolved the freeze issue for the nVidia driver
The following site says to remove the nvidia_new and nvidia_legacy:

[http://www.nvnews.net/vbulletin/showthread.php?t=112321]("http://www.nvnews.net/vbulletin/showthread.php?t=112321")

I did this and re-installed the nvidia driver from their site.  I have been booted up for about an hour now with the nvidia driver and no freezes :)

(I have been loading my computer trying to get at freeze and nothing)

---

### Post by Mighty_Joe on 2008-04-26
I double-checked Jim March's post [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996/comments/52") on installing the RT kernel and I realized I hadn't changed my grub menu.  I add a delay to the menu, make sure I'm booting the RT kernel, but oddly enough, /proc/version_signiture contains "Ubuntu 2.6.24-4.6-generic".  
I'd expect to see an "rt" rather than "generic".  Can someone who has the RT kernel check?

---

### Post by Seks on 2008-04-26
I am kinda relieved that this is more of a widespread problem than a personal one. It fit's in perfectly with what I have been experiencing. I use a Cnet CWP-854 wireless card and in my case everything locks up after a few minutes of browsing the internet. 

I tried with FF3B5, FF2, and Epiphany, but downloading with the package manager/add-remove/other non-browser interfaces cause no issues. It did this on a fresh install of hardy with javascript and java disabled to make it as simple as possible.

I'm stuck with windows XP until this gets fixed :(

---

### Post by Mighty_Joe on 2008-04-27
My problem may be apic. I started the livecd with the "noapic" option and it didn't crash in the 10 or 15 minutes it was up (a new record for Hardy!).  I'll try the hard drive install later.

---

### Post by brethren on 2008-04-27
> **Mighty_Joe said:**
> ...it didn't crash in the 10 or 15 minutes it was up (a new record for Hardy!)

yeah, my system hangs within 10 mins of being booted.what i want to know is how can a bug this serious slip through.....especially on a stable LTS release?

---

### Post by dcollamore on 2008-04-27
There are references on the bug ([https://bugs.launchpad.net/ubuntu/+bug/204996]("https://bugs.launchpad.net/ubuntu/+bug/204996")) to potential SATA I/O issues being the root cause.  My affected system is running on a SATA HDD, and my laptop, which is not affected, is running an IDE HDD.  Any who's having this trouble NOT running a SATA HDD or optical drive?

---

### Post by Seks on 2008-04-27
> **dcollamore said:**
> There are references on the bug ([https://bugs.launchpad.net/ubuntu/+bug/204996]("https://bugs.launchpad.net/ubuntu/+bug/204996")) to potential SATA I/O issues being the root cause.  My affected system is running on a SATA HDD, and my laptop, which is not affected, is running an IDE HDD.  Any who's having this trouble NOT running a SATA HDD or optical drive?

Yes, I am using SCSI. However I can safely do anything that doesn't involve a browser, like repartitioning hard drives and downloading packages.


Edit: I'm going to try running a windows browser in wine if the connection works. Dunno how many times I can hard reboot with damaging stuff though.

---

### Post by Seks on 2008-04-27
> **Seks said:**
> 
Edit: I'm going to try running a windows browser in wine if the connection works. Dunno how many times I can hard reboot with damaging stuff though.

Nope, also freezes.

---

### Post by olskar on 2008-04-27
> **Seks said:**
> Yes, I am using SCSI. However I can safely do anything that doesn't involve a browser, like repartitioning hard drives and downloading packages.


Edit: I'm going to try running a windows browser in wine if the connection works. Dunno how many times I can hard reboot with damaging stuff though.

I do not know how hard frozen your system is but try to use this when hardrebooting to make it less hard:
[http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/](http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/)

---

### Post by dcollamore on 2008-04-27
In my case the sysrq keys are ineffective; no response whatsoever.

---

### Post by dcollamore on 2008-04-28
Some further information, may be applicable.  My laptop (Inspiron 8600) has now been pounded under every kind of load I can throw at it, with Compiz, closed source nVidia driver (using restricted drivers manager), and wireless connectivity without a single hiccup.  Hardware specs are as follows:

Intel Pentium M 1.7GHz (single core, so no SMP)
Intel 855PM Chipset
768MB Kingston DDR-SDRAM
60GB IDE HDD (no SATA)
nVidia GeForce 5200 Mobile 32MB
Intel 2200BG Wireless

It seems there are quite a few potential devices causing these issues, so I'm going to try running through every possible scenario I can to pin something down here.

I'm going to try running the desktop that's giving me trouble with a non-smp kernel first, then a PATA drive.  I'll also try the laptop with a Broadcom wireless card and an Atheros wireless card. If I get any relevant information I'll report back what I found.  

The -rt kernel played the same game with me finally, so it appears to have the same stability issues, just to a lesser degree on my system.

---

### Post by sharpeg on 2008-04-28
I'm so glad to find I'm not alone!

I've been using Ubunutu on my laptop (an old Dell latitude C610) for several moths now and have grown to love it. I've got Dual boot with XP but only go to XP to do the one or two things Ubuntu can't (e.g. it doesn;t support my lexmark X6570). I've been telling everyone how wonderful it was and was all set to install it on a couple of friends PCs. Then I spent the night on Friday trying to install Hardy and disaster struck. I have a few problems (e.g. can't see my NAS anymore) but the main issue has been the constant 'hangs', something which has never happened before.

My freezes seem to be slightly different to others. The main time I get the problem has been to do with looking for updates to either the system or applications. for example, when I go to Applications>add/remove is says it's out of date and tells me to click the update button. This then sits there for hours on end doing nothing and eventually I have to turn of the PC and start again. 

Having read this thread, I removed my wireless card and reverted to a wired connection, I seem now to be able to work without things locking up. We'll see how long it lasts.

In case anyone ele has the same cause, my wireless connection is via a Belkin wirelss PC card (£20 from PC world).

I have to say that I am very dissapointed with this release and I've spent more time in XP over the past three days than I have in the previsous 3 months!

---

### Post by 00arthuryu on 2008-04-28
my laptop freezes as well with ubuntu 8.04 it never happened with 
but my desktop has an even bigger problem of freezing :( and my desktop doesn't even have wireless :(

---

### Post by Seks on 2008-04-28
The causes seem to vary by person(but often includes a wireless card), but I have only had one crash since I started using opera instead of a Gecko based browser(Firefox,Epiphany,Flock), and then I had a whole bunch of tabs open. It might be a RAM usage issue.

---

### Post by sharpeg on 2008-04-28
Well, it was obviously too good to be true. Everything was fine until I decided to import my music files into rythmbox. My music is storage on a NAS which took me an hour to work out how to connect to it and after a load of spurious password requests it finally connected. I tried several times to import the files (did this just two weeks ago in Gusty with no problems), it complained a few times and on my final attempt locked up and left me having to power down (with the power button) and restart. 

Hey ho!

---

### Post by eric02138 on 2008-04-28
Before getting fed up and reverting to Gutsy, I was seeing the same problem, though my mouse would stop responding before the rest of the system.  I do have a nvidia graphics card - maybe that's the problem?  I don't think it's a memory issue - I've got an Intel Core2 Duo running on 4GB of ram.  But then, I'm just a newbie.

-Eric

---

### Post by rmccabe3701 on 2008-04-28
Hmmm, system froze again ... so I guess it didn't have to do with the nvidia driver (?)  

This is quite annoying ... I'm going to go back to Gutsy.

How long do these things normally take to get resolved?

---

### Post by ezsit on 2008-04-29
> It never frooze with gutsy so it is obvious the issue is with hardy sadly

As they say someone has dropped the ball back to XP sadly till the bugs are ironed out

Why? If Gutsy never froze, why go back to XP? This makes no sense. Go back to Gutsy and stick with Linux. 

BTW, the point release 8.04.1 is due out in July. I am going to wait until then and test Hardy this summer. Until then, Kubuntu 7.10 is humming along without one problem for me. If it ain't broke...

---

### Post by gnaag on 2008-04-29
I have encountered the same issue. In gutsy, it happened with old wireless driver, but only when I was connected via it. In hardy it happens quite offen not depending whether I am connected through wireless or wire. My experiences says that it freezes when I work with: firefox, banshee, gtk games. It doesn't with wine or thunderbird.

---

### Post by marlon89br on 2008-04-29
Same problem here... Using a laptop with Core2Duo T5300, 1GB DDR2, HD SATA 120GB, video card VIA VN896.

It freezes when I use Firefox (random freezing). I don't remember of a freeze withou FF running. But I don't know whether it is a FF problem, I use it almost all the time.. hehehe

I thought it was a problem with my video driver (openchrome)... but the issue is not just with this card.

I hope it to be fixed soon... I feel a little worried with hard reboots.

---

### Post by ksauber on 2008-04-29
errr ... if the rt kernel doesn't work - how do you return to the pervious kernel?

---

### Post by Mighty_Joe on 2008-04-30
> **ksauber said:**
> errr ... if the rt kernel doesn't work - how do you return to the pervious kernel?

When booting, you'll see Grub display a message: "press Esc for menu".  Press Esc and you'll see a list of all the installed kernels.  To change the default choice or to make the menu display every boot, you have to edit /boot/grub/menu.lst.  It's fairly well-documented. Save a copy before you change it!

---

### Post by iopo on 2008-04-30
Hi!
I'm having the same issue. The freeze is quite random but I found out that it always happen after few minutes I'm playing a game called Glest.
At first I thought it was a video card issue but I tried with the proprietary driver, without it, with compiz running, with compiz without running and it still freezes.
By the way, since I can reproduce it, does anyone knows how to get some useful info out of it?
Thanks

specs:
dell inspiron 6000
ati mobility radeon x300
Intel Corporation PRO/Wireless 2915ABG

---

### Post by Mighty_Joe on 2008-04-30
Have a look at [this bug]("https://bugs.launchpad.net/ubuntu/+bug/204996").  If the symptoms sound like what you are seeing, there's a couple of lists of log files that the developers want to see.

---

### Post by ksauber on 2008-05-01
Yeah, found that about 5 minutes after posting the question.   Sigh.

I don't know if this will help anybody else, but **I** stopped having crash/lock-up problem after uninstalling FF3 and installing FF2 (which I prefer anyway).

---

### Post by marlon89br on 2008-05-01
Great... so it might be a problem with Firefox for me too... Yesterday I didn't use it and I had no freeze.
So, let's ask Mozilla for a solution, hehe.

---

### Post by ksauber on 2008-05-01
> **marlon89br said:**
> Great... so it might be a problem with Firefox for me too... Yesterday I didn't use it and I had no freeze.
So, let's ask Mozilla for a solution, hehe.

Sadly, a few minutes after I posted that "solution", the system froze on me.  All I can say at this point is that, _for me_, crashes are far less common  after going to FF2.

My thoughts at this point is that there is a problem with either programs overwriting (corrupting)the system area in memory, or in swap.  

Does somebody know how to disable swap?  At least that could be tested.

My system has 1 GB of ram and uses very little swap space.  That may explain why going to FF2 reduces the problem.  It's a smaller program and would use less memory or swap space. 

Just a thought.

---

### Post by sharpeg on 2008-05-01
I've now unstallled FF3 (wasn't easy - had to try three times!) then installed FF2. Loads of things started working again. I can see my network files/folders, I can check for updates, etc. I've not tried going back to using wireless again yet but will try that shortly and see what happens.

Thanks for the suggestion that it might be FF3.

---

### Post by marlon89br on 2008-05-01
Just installing FF2 didn't work for me. I was using FF2 in a normal page (no plugins required) and I got a freeze again. Now I've uninstalled FF3... Until now it is stable (about 2 hours using it).

---

### Post by landeel on 2008-05-02
HP DV6000 laptop, 1 GB RAM, GeForce 6150. Running with noapic irqpoll noirqdebug, otherwise I can't even get to xorg.
Just upgraded from 7.10 to 8.04 (AMD64). Now my system is freezing. Never happened before with 7.10.
It always freezes when I'm playing SDLMAME. Happened once listening to music with amarok. The cursor freezes and the sound loops. The only thing I can do is power off the system.
I think it's related to NVIDIA drivers and Kernel 2.6.24. I've tried running with NV drivers and it doesn't seem to freeze. Running hardy with Kernel 2.6.22 didn't freeze either.
Sadly I couldn't make NVIDIA drivers work again with kernel 2.6.22, so I'm sticking to XP (argh) until it gets fixed.

---

### Post by dreamsR4living on 2008-05-02
About a week ago I started to use the RT kernel which did also freeze on Ubuntu, but not as often as the regular kernel. I tried things like uninstalling FF3, but none of it really worked.

I was so fed up with the problem that I decided to do a fresh Xubuntu 8.04 install, which doesn't seem to have any problem at all! But it is the first time really working with Xfce. But because I missed compiz-fusion effects, I tried to install them on Xubuntu. 5 minutes after I installed compiz-fusion my sytem froze again. Since I putted compiz with the trash I don't seem to have any problems again.

Probably compiz in combination with the Nvidia drivers is the problem...

So to disable compiz might help to stay in Hardy without freezes, although I agree life is hard without the flashy effects :)

---

### Post by sharpeg on 2008-05-02
Ok. Now an update. The reverting to FF2 seemed to help a little but after a short time things started to slow down and eventually lock up, but mainly when using wireless.

Today, I received my internal wireless card (I have a Dell C610), installed it, reinstalled Hardy and it's like a different machine, even with FF3. I've had a couple of lock-ups but only when installing software or plugins. It usually locks up at the end of the process and after rebooting reports that the installation was complete.

I still have a few issues, bu it is clear that for me, the main issue was the old wireless PC card. I'll persevere with Hardy now to see how stable it stays but may go back to FF2 again to see if that helps.

Thanks to everyone for the comments and ideas about the problems. Without them I would probably be back on XP by now!

Thanks

---

### Post by anarkhy on 2008-05-02
My laptop freezes too, and i have to remove the battery to turn off.

My config

Acer Compaq c700
graphics intel x3100
processor celeron m540
wireless broadcom
2 giga ram


works fine with ubuntu 7.10, with ubuntu 8 i could only install in text mode but then it freezes before i could login.

---

### Post by landeel on 2008-05-02
HP DV6000 laptop, 1 GB RAM, GeForce 6150. Running with noapic irqpoll noirqdebug.

It seems I got my system stable again by downgrading to kernel 2.6.22-14 . This is how I did it:

1- I had kernel 2.6.22-14 previously installed because I have upgraded from 7.10 to 8.04. So I just changed 2.6.22-14 to be the default again in '/boot/grub/menu.1st'.

2- Commented out 'blacklist bcm43xx' from '/etc/modprobe.d/blacklist' , and added 'blacklist b43', so I can get my wireless card to work again with the older kernel.

3- NVIDIA drivers: this was the hardest part to figure out, as everything I've tried before failed miserably. I have manually downloaded 'nvidia-glx-new_100.14.19+2.6.22.4-14.9_amd64.deb' and 'linux-restricted-modules-2.6.22-14-generic_2.6.22.4-14.9_amd64.deb'
Then did a 'sudo dpkg -i --force-all *.deb'. DANGEROUS! It will give a few broken dependencies, so do it at your own risk.

So I have played SDLMAME for a few hours now, and I haven't experienced any more freezes. I hope everything is stable now.
One thing is for sure: I'm not upgrading my kernel anytime soon.

---

### Post by alejandro.mc on 2008-05-03
No news??

I'm really frustrated.

---

### Post by Mighty_Joe on 2008-05-03
> **alejandro.mc said:**
> No news??
I'm really frustrated.

Patience.  Most of the programmers who contribute to Linux are volunteers.  This bug is particularly insidious because nobody has come up with a single test case that reproduces it for all hardware.  
You could always try another distro or even dig into the kernel source yourself ;)

---

### Post by landeel on 2008-05-03
Now I can actually confirm my problem is with kernel 2.6.24 . And it has something to do with NVIDIA drivers.
I just left SDLMAME running for about 7 hours with kernel 2.6.22, and haven't experienced any freezes. With kernel 2.6.24 the whole system will freeze in 3 to 30 minutes of running SDLMAME or any other program that uses OpenGL.

---

### Post by cytg on 2008-05-03
freezes on me too .. though it seems like a direct continuation of
[http://ubuntuforums.org/showthread.php?t=651172&page=17](http://ubuntuforums.org/showthread.php?t=651172&page=17)

But in hardy i've also experienced the not-so-hard lockup(mouse works everything else is frozen) where i can remote ssh in and do whatever .. here X just consumes 99.99% cpu

im on a 3ghz p4 btw, no lappy..

---

### Post by Winsbreaker on 2008-05-03
Ubuntu Hardy freezes, yet the mouse will sometimes work, other times it locks completely. 

IBM T42 Laptop
1.7Ghz Centrino
1 G RAM
80 GB Harddrive

I will note that I use the built in wireless regularly  (or at lease attempt to). I love Ubuntu and am still learning with it, but I can't have a computer that only works for 5 minutes prior to locking up. Everything, from the graphics card to internet works beautiful until the freeze.

---

### Post by landeel on 2008-05-03
Mine locks completely, including the cursor. But my mouse is USB...
Ah, mine never locked with the previous versions.

---

### Post by Seks on 2008-05-03
I just got an update that said it "fixed hang when reading from PCI slot"

could this be it? Lets see... :popcorn:

---

### Post by alejandro.mc on 2008-05-03
I updated my system last night, and since then no lockdowns, so something they send via the update simply worked!

Excellent!

---

### Post by Winsbreaker on 2008-05-04
I had similar issues, yet Hardy is up an running now. Here's how I managed it:

1) Installed 8.04 - locked continuously 
2) Installed 7.10 - locked continuously
3) Reimage of vista - failed
4) Reinstall of 8.04 - hard drive error...? failed to read some blocks
5) Removed all partitions with gparted
6) Fresh install of 8.04
7) Installed prop. ATI driver and updated 

Working beautifully now. 

Also, I'm on a T42 lappy.

---

### Post by Gruss2 on 2008-05-04
I've been having the same problem since installing Hardy...sudden freeze ups everyday, and then I have to do a hard shutdown by holding down the power button.

I'm using an Ethernet connection and my laptop is an IBM ThinkPad A21m model 512 memory...yes, vintage hardware, but Gutsy worked wonderfully for me and has NEVER frozen on me. This Hardy version seems like a stranger and is giving me a bit of a headache. I'll be patient and wait for a fix or update.

---

### Post by Winsbreaker on 2008-05-04
> **Winsbreaker said:**
> I had similar issues, yet Hardy is up an running now. Here's how I managed it:

1) Installed 8.04 - locked continuously 
2) Installed 7.10 - locked continuously
3) Reimage of vista - failed
4) Reinstall of 8.04 - hard drive error...? failed to read some blocks
5) Removed all partitions with gparted
6) Fresh install of 8.04
7) Installed prop. ATI driver and updated 

Working beautifully now. 

Also, I'm on a T42 lappy.

Okay, I know I'm quoting myself, but I use my laptop as a desktop usually and I plug two USB hubs and a plethora a peripherals, including a external monitor. Well the laptop worked fine on its own, but once i plugged in a monitor, keyboard, mouse and the HP1020 printer it froze within 5 minutes, hopefully it's not the keyboard, mouse and monitor, for woe if it is and back to MS I trudge.:(

---

### Post by jamyskis on 2008-05-04
I'm not sure if this has been mentioned, but my 8.04 was also locking up continuously until I turned off 3D effects...worth a shot?

---

### Post by landeel on 2008-05-04
It seems with kernel 2.6.24 any application that uses libGL will freeze, including the 3D effects.
Disabling 3D effects does reduce the possibility of a freeze, but it doesn't eliminate the problem. The freeze still happens with 3D games, GL screensavers, SDLMAME, anything that uses libGL... Amarok crashed once, and when I checked the dependecies, to my surprise, it does depend on libGL.
With 2.6.22 all works perfectly. No freezes at all.

---

### Post by Ekeluo on 2008-05-04
I seem to have the most convoluted version of this crashing bug thing. I'm typing this from Firefox 3 (which has been running for over 2 hrs now, amarok in background playing), Ran it for several hours yesterday downloading youtube videos via LAN internet (no wireless; hardware switch off). My laptop DOES crash randomly, has done so about 4 times today alone, though it reduced after I set vm_swapiness to 0 and turned off plugins I didn't need in Compiz. When it freezes, cursor moves fine eternally, other processes continue in background (amarok even crossfades to next track) but keyboard does not work and  I have to hard reset. I read at launchpad that it is probably an I/O or kerenl panic problem. Hope it is fixed soon.


P.S how come I didn't get any updates yesterday?

---

### Post by busybrain on 2008-05-04
I have the same problem .

My Ubuntu hardy freezes after 2 minutes of booting.
In my case it seems to be the video card drivers
I disable the restricted software for my Nvdia Geforce 6200 and now it seems to work.  

But I want to use the Visual Effect for my video card witch I cant do without enabling the restricted software .. SUCKS !!!!

---

### Post by bred on 2008-05-04
[COLOR="Purple"]my Hardy freezes too...
it SUCKS GUYS[/COLOR]

---

### Post by Ozor Mox on 2008-05-04
I'm having this problem and I'm almost certain it's related to the Broadcom wireless drivers. The internet disconnects, the system load shoots up to huge numbers, the mouse starts juddering and eventually freezes up entirely. The usual key combinations are totally ineffective, only a hard reboot does the job. This problem did not exist in Gutsy :(

---

### Post by HoMe_CaNiBaL on 2008-05-04
Hi there.

I use Ubuntu since Dapper and i have always problems with freezes. Hardy isn't an exception.

The machine freezes, but i can move my mouse. Freeze at 23.17 ( or 11.17pm) and in syslog i have this

> May  4 22:17:01 homecanibal-desktop /USR/SBIN/CRON[9542]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  4 22:46:50 homecanibal-desktop -- MARK --
May  4 23:06:50 homecanibal-desktop -- MARK --
May  4 23:17:01 homecanibal-desktop /USR/SBIN/CRON[10436]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  4 23:46:50 homecanibal-desktop -- MARK --
May  5 00:06:50 homecanibal-desktop -- MARK --
May  5 00:17:01 homecanibal-desktop /USR/SBIN/CRON[11318]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  5 00:46:50 homecanibal-desktop -- MARK --
May  5 01:06:50 homecanibal-desktop -- MARK --
May  5 01:17:01 homecanibal-desktop /USR/SBIN/CRON[12195]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  5 01:46:50 homecanibal-desktop -- MARK --

And the machine still running until i arrive at home, and hard reset.

What i'm doing wrong?

I have 
P4 2.8 FSB 800
Asus P4C800 DLX
4 x 512Mb DDR400
Aopen 6600GT AGP 128Mb (using nvidia 169 drivers)

Thanks

---

### Post by rmccabe3701 on 2008-05-04
I updated my system yesterday and it seems that the ubuntu team must have solved the lockup issue since I have not had a lockup for over a day ... the problem now is that I have lost all usb functionality.  The system does not find any usb device (flash drive, external hard drive, etc.) It doesn't even show up in /dev

when I do 

```

cat /var/log/syslog

```

I get 

```

...
May  4 21:41:26 rob-desktop kernel: [13067.344518] printk: 1 messages suppressed.
May  4 21:41:26 rob-desktop kernel: [13067.344524] hub 7-0:1.0: connect-debounce failed, port 2 disabled
May  4 21:41:33 rob-desktop kernel: [13074.300333] printk: 2 messages suppressed.
May  4 21:41:33 rob-desktop kernel: [13074.300339] hub 7-0:1.0: connect-debounce failed, port 2 disabled
May  4 21:41:37 rob-desktop kernel: [13078.910989] printk: 1 messages suppressed.
May  4 21:41:37 rob-desktop kernel: [13078.910995] hub 7-0:1.0: connect-debounce failed, port 2 disabled
May  4 21:41:42 rob-desktop kernel: [13083.787938] printk: 1 messages suppressed.
May  4 21:41:42 rob-desktop kernel: [13083.787945] hub 7-0:1.0: connect-debounce failed, port 2 disabled
May  4 21:41:47 rob-desktop kernel: [13088.734658] printk: 1 messages suppressed.
May  4 21:41:47 rob-desktop kernel: [13088.734665] hub 7-0:1.0: connect-debounce failed, port 2 disabled
May  4 21:41:52 rob-desktop kernel: [13093.315552] printk: 1 messages suppressed.
May  4 21:41:52 rob-desktop kernel: [13093.315557] hub 7-0:1.0: connect-debounce failed, port 2 disabled
May  4 21:41:56 rob-desktop kernel: [13098.021377] printk: 1 messages suppressed.
May  4 21:41:56 rob-desktop kernel: [13098.021382] hub 7-0:1.0: connect-debounce failed, port 2 disabled
...

```

---

### Post by richaoj on 2008-05-05
To all those suffering with this problem:  I think that my freezes may be related to using ndiswrapper.  It was a pain to set up on this kernel.  but since i have gone to using b43 instead of ndiswrapper, i have not experienced a freeze up.  we'll see though.  ARGHHH.  I should just go back to gutsy.  never experienced any problems there.

---

### Post by ldt0 on 2008-05-05
Im having random freezes too, on an Acer Aspire 7000 laptop. Having the binary nvidia drivers enables greatly increases the frequency of the crashes, never had more than 5-6 hours of uptime with them. When i disable them i hava managed to get a few days of uptime before a freeze. I have also tried disabling the wireless drivers but they don't seem to affect the issue at all.

The freezes are total, no system response at all and nothing in the system logs. Hope this gets resolved soon or i'm gonna have to go back to Vista. :(

---

### Post by bred on 2008-05-05
[COLOR="Blue"]I think the cause  of freezing is wireless card...
in the mean while I'm going back to gutsy or mandirva[/COLOR]

---

### Post by granjerox on 2008-05-05
My Hardy has crashed also in the last days. Last one, the X server stop working, I switched
to a tty and when I tried to restart gdm the whole system went down and I had to do a hard 
shutdown. I don't know the cause of the hung up, or how to track it. Thats what I've
found in my syslog :
```

May  5 15:40:47 granjerox-laptop dhclient: bound to 129.13.226.191 -- renewal in 2983 seconds.
May  5 15:49:18 granjerox-laptop NetworkManager: <info>  Error getting killswitch power: org.freedesktop.DBus.Error.NoReply - Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken. 
May  5 15:49:21 granjerox-laptop kernel: [25203.977905] BUG: soft lockup - CPU#1 stuck for 11s! [Xorg:24242]
May  5 15:49:22 granjerox-laptop kernel: [25203.977913] 
May  5 15:49:22 granjerox-laptop kernel: [25203.977918] Pid: 24242, comm: Xorg Tainted: P        (2.6.24-17-generic #1)
May  5 15:49:22 granjerox-laptop kernel: [25203.977923] EIP: 0060:[ipv6:_spin_lock+0x7/0x10] EFLAGS: 00003286 CPU: 1
May  5 15:49:22 granjerox-laptop kernel: [25203.977933] EIP is at _spin_lock+0x7/0x10
May  5 15:49:22 granjerox-laptop kernel: [25203.977937] EAX: f8dbb6e8 EBX: 00000000 ECX: f8dbb6c0 EDX: 00000400
May  5 15:49:22 granjerox-laptop kernel: [25203.977941] ESI: f369db40 EDI: 00000000 EBP: f8d5c2a0 ESP: f3779e98
May  5 15:49:22 granjerox-laptop kernel: [25203.977946]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
May  5 15:49:22 granjerox-laptop kernel: [25203.977950] CR0: 8005003b CR2: b7e552c0 CR3: 247d5000 CR4: 00000690
May  5 15:49:22 granjerox-laptop kernel: [25203.977955] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
May  5 15:49:22 granjerox-laptop kernel: [25203.977959] DR6: ffff0ff0 DR7: 00000400
May  5 15:49:22 granjerox-laptop kernel: [25203.977973]  [<f8c5001a>] firegl_open+0x8a/0x210 [fglrx]
May  5 15:49:22 granjerox-laptop kernel: [25203.978093]  [security_inode_permission+0x1c/0x20] security_inode_permission+0x1c/0x20
May  5 15:49:22 granjerox-laptop kernel: [25203.978108]  [<f8c4589f>] ip_firegl_open+0xf/0x20 [fglrx]
May  5 15:49:22 granjerox-laptop kernel: [25203.978215]  [<f8c471d0>] firegl_stub_open+0xb0/0x100 [fglrx]
May  5 15:49:22 granjerox-laptop kernel: [25203.978320]  [kobject_get+0xf/0x20] kobject_get+0xf/0x20
May  5 15:49:22 granjerox-laptop kernel: [25203.978333]  [<f8c47120>] firegl_stub_open+0x0/0x100 [fglrx]
May  5 15:49:22 granjerox-laptop kernel: [25203.978438]  [chrdev_open+0xa3/0x190] chrdev_open+0xa3/0x190
May  5 15:49:22 granjerox-laptop kernel: [25203.978454]  [__dentry_open+0xbf/0x1c0] __dentry_open+0xbf/0x1c0
May  5 15:49:22 granjerox-laptop kernel: [25203.978466]  [nameidata_to_filp+0x35/0x40] nameidata_to_filp+0x35/0x40
May  5 15:49:22 granjerox-laptop kernel: [25203.978475]  [chrdev_open+0x0/0x190] chrdev_open+0x0/0x190
May  5 15:49:22 granjerox-laptop kernel: [25203.978484]  [do_filp_open+0x50/0x60] do_filp_open+0x50/0x60
May  5 15:49:22 granjerox-laptop kernel: [25203.978499]  [sys_chown+0x54/0x70] sys_chown+0x54/0x70
May  5 15:49:22 granjerox-laptop kernel: [25203.978512]  [get_unused_fd_flags+0x52/0xd0] get_unused_fd_flags+0x52/0xd0
May  5 15:49:22 granjerox-laptop kernel: [25203.978525]  [do_sys_open+0x4c/0xe0] do_sys_open+0x4c/0xe0
May  5 15:49:22 granjerox-laptop kernel: [25203.978538]  [sys_open+0x1c/0x20] sys_open+0x1c/0x20
May  5 15:49:22 granjerox-laptop kernel: [25203.978546]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
May  5 15:49:22 granjerox-laptop kernel: [25203.978561]  [unix_dgram_recvmsg+0x110/0x2d0] unix_dgram_recvmsg+0x110/0x2d0
May  5 15:49:22 granjerox-laptop kernel: [25203.978575]  =======================
May  5 15:49:33 granjerox-laptop kernel: [25215.769290] BUG: soft lockup - CPU#1 stuck for 11s! [Xorg:24242]
May  5 15:49:33 granjerox-laptop kernel: [25215.769297] 
May  5 15:49:33 granjerox-laptop kernel: [25215.769302] Pid: 24242, comm: Xorg Tainted: P        (2.6.24-17-generic #1)
May  5 15:49:33 granjerox-laptop kernel: [25215.769307] EIP: 0060:[ipv6:_spin_lock+0x5/0x10] EFLAGS: 00003286 CPU: 1
May  5 15:49:33 granjerox-laptop kernel: [25215.769315] EIP is at _spin_lock+0x5/0x10
May  5 15:49:33 granjerox-laptop kernel: [25215.769319] EAX: f8dbb6e8 EBX: 00000000 ECX: f8dbb6c0 EDX: 00000400
May  5 15:49:33 granjerox-laptop kernel: [25215.769324] ESI: f369db40 EDI: 00000000 EBP: f8d5c2a0 ESP: f3779e98
May  5 15:49:33 granjerox-laptop kernel: [25215.769328]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
May  5 15:49:33 granjerox-laptop kernel: [25215.769332] CR0: 8005003b CR2: b7e552c0 CR3: 247d5000 CR4: 00000690
May  5 15:49:33 granjerox-laptop kernel: [25215.769338] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
May  5 15:49:33 granjerox-laptop kernel: [25215.769344] DR6: ffff0ff0 DR7: 00000400
May  5 15:49:33 granjerox-laptop kernel: [25215.769355]  [<f8c5001a>] firegl_open+0x8a/0x210 [fglrx]
May  5 15:49:33 granjerox-laptop kernel: [25215.769478]  [security_inode_permission+0x1c/0x20] security_inode_permission+0x1c/0x20
May  5 15:49:33 granjerox-laptop kernel: [25215.769495]  [<f8c4589f>] ip_firegl_open+0xf/0x20 [fglrx]
May  5 15:49:33 granjerox-laptop kernel: [25215.769604]  [<f8c471d0>] firegl_stub_open+0xb0/0x100 [fglrx]
May  5 15:49:33 granjerox-laptop kernel: [25215.769713]  [kobject_get+0xf/0x20] kobject_get+0xf/0x20
May  5 15:49:33 granjerox-laptop kernel: [25215.769728]  [<f8c47120>] firegl_stub_open+0x0/0x100 [fglrx]
May  5 15:49:33 granjerox-laptop kernel: [25215.769835]  [chrdev_open+0xa3/0x190] chrdev_open+0xa3/0x190
May  5 15:49:33 granjerox-laptop kernel: [25215.769855]  [__dentry_open+0xbf/0x1c0] __dentry_open+0xbf/0x1c0
May  5 15:49:33 granjerox-laptop kernel: [25215.769870]  [nameidata_to_filp+0x35/0x40] nameidata_to_filp+0x35/0x40
May  5 15:49:33 granjerox-laptop kernel: [25215.769882]  [chrdev_open+0x0/0x190] chrdev_open+0x0/0x190
May  5 15:49:33 granjerox-laptop kernel: [25215.769894]  [do_filp_open+0x50/0x60] do_filp_open+0x50/0x60
May  5 15:49:33 granjerox-laptop kernel: [25215.769914]  [sys_chown+0x54/0x70] sys_chown+0x54/0x70
May  5 15:49:33 granjerox-laptop kernel: [25215.769930]  [get_unused_fd_flags+0x52/0xd0] get_unused_fd_flags+0x52/0xd0
May  5 15:49:33 granjerox-laptop kernel: [25215.769946]  [do_sys_open+0x4c/0xe0] do_sys_open+0x4c/0xe0
May  5 15:49:33 granjerox-laptop kernel: [25215.769963]  [sys_open+0x1c/0x20] sys_open+0x1c/0x20
May  5 15:49:33 granjerox-laptop kernel: [25215.769975]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
May  5 15:49:33 granjerox-laptop kernel: [25215.769993]  [unix_dgram_recvmsg+0x110/0x2d0] unix_dgram_recvmsg+0x110/0x2d0
May  5 15:49:33 granjerox-laptop kernel: [25215.770010]  =======================
May  5 15:49:45 granjerox-laptop kernel: [25227.556681] BUG: soft lockup - CPU#1 stuck for 11s! [Xorg:24242]
May  5 15:49:45 granjerox-laptop kernel: [25227.556688] 
May  5 15:49:45 granjerox-laptop kernel: [25227.556693] Pid: 24242, comm: Xorg Tainted: P        (2.6.24-17-generic #1)
May  5 15:49:45 granjerox-laptop kernel: [25227.556698] EIP: 0060:[ipv6:_spin_lock+0x7/0x10] EFLAGS: 00003286 CPU: 1
May  5 15:49:45 granjerox-laptop kernel: [25227.556706] EIP is at _spin_lock+0x7/0x10
May  5 15:49:45 granjerox-laptop kernel: [25227.556710] EAX: f8dbb6e8 EBX: 00000000 ECX: f8dbb6c0 EDX: 00000400
May  5 15:49:45 granjerox-laptop kernel: [25227.556715] ESI: f369db40 EDI: 00000000 EBP: f8d5c2a0 ESP: f3779e98
May  5 15:49:45 granjerox-laptop kernel: [25227.556719]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
May  5 15:49:45 granjerox-laptop kernel: [25227.556723] CR0: 8005003b CR2: b7e552c0 CR3: 247d5000 CR4: 00000690
May  5 15:49:45 granjerox-laptop kernel: [25227.556729] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
May  5 15:49:45 granjerox-laptop kernel: [25227.556734] DR6: ffff0ff0 DR7: 00000400
May  5 15:49:45 granjerox-laptop kernel: [25227.556746]  [<f8c5001a>] firegl_open+0x8a/0x210 [fglrx]
May  5 15:49:45 granjerox-laptop kernel: [25227.556868]  [security_inode_permission+0x1c/0x20] security_inode_permission+0x1c/0x20
May  5 15:49:45 granjerox-laptop kernel: [25227.556885]  [<f8c4589f>] ip_firegl_open+0xf/0x20 [fglrx]
May  5 15:49:45 granjerox-laptop kernel: [25227.556995]  [<f8c471d0>] firegl_stub_open+0xb0/0x100 [fglrx]
May  5 15:49:45 granjerox-laptop kernel: [25227.557103]  [kobject_get+0xf/0x20] kobject_get+0xf/0x20
May  5 15:49:45 granjerox-laptop kernel: [25227.557118]  [<f8c47120>] firegl_stub_open+0x0/0x100 [fglrx]
May  5 15:49:45 granjerox-laptop kernel: [25227.557225]  [chrdev_open+0xa3/0x190] chrdev_open+0xa3/0x190
May  5 15:49:45 granjerox-laptop kernel: [25227.557244]  [__dentry_open+0xbf/0x1c0] __dentry_open+0xbf/0x1c0
May  5 15:49:45 granjerox-laptop kernel: [25227.557259]  [nameidata_to_filp+0x35/0x40] nameidata_to_filp+0x35/0x40
May  5 15:49:45 granjerox-laptop kernel: [25227.557271]  [chrdev_open+0x0/0x190] chrdev_open+0x0/0x190
May  5 15:49:45 granjerox-laptop kernel: [25227.557283]  [do_filp_open+0x50/0x60] do_filp_open+0x50/0x60
May  5 15:49:45 granjerox-laptop kernel: [25227.557303]  [sys_chown+0x54/0x70] sys_chown+0x54/0x70
May  5 15:49:45 granjerox-laptop kernel: [25227.557319]  [get_unused_fd_flags+0x52/0xd0] get_unused_fd_flags+0x52/0xd0
May  5 15:49:45 granjerox-laptop kernel: [25227.557336]  [do_sys_open+0x4c/0xe0] do_sys_open+0x4c/0xe0
May  5 15:49:45 granjerox-laptop kernel: [25227.557352]  [sys_open+0x1c/0x20] sys_open+0x1c/0x20
May  5 15:49:45 granjerox-laptop kernel: [25227.557364]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
May  5 15:49:45 granjerox-laptop kernel: [25227.557382]  [unix_dgram_recvmsg+0x110/0x2d0] unix_dgram_recvmsg+0x110/0x2d0
May  5 15:49:45 granjerox-laptop kernel: [25227.557400]  =======================
May  5 15:49:57 granjerox-laptop kernel: [25239.348066] BUG: soft lockup - CPU#1 stuck for 11s! [Xorg:24242]
May  5 15:49:57 granjerox-laptop kernel: [25239.348073] 
May  5 15:49:57 granjerox-laptop kernel: [25239.348078] Pid: 24242, comm: Xorg Tainted: P        (2.6.24-17-generic #1)
May  5 15:49:57 granjerox-laptop kernel: [25239.348083] EIP: 0060:[ipv6:_spin_lock+0x7/0x10] EFLAGS: 00003286 CPU: 1
May  5 15:49:57 granjerox-laptop kernel: [25239.348091] EIP is at _spin_lock+0x7/0x10
May  5 15:49:57 granjerox-laptop kernel: [25239.348096] EAX: f8dbb6e8 EBX: 00000000 ECX: f8dbb6c0 EDX: 00000400
May  5 15:49:57 granjerox-laptop kernel: [25239.348100] ESI: f369db40 EDI: 00000000 EBP: f8d5c2a0 ESP: f3779e98
May  5 15:49:57 granjerox-laptop kernel: [25239.348104]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
May  5 15:49:57 granjerox-laptop kernel: [25239.348109] CR0: 8005003b CR2: b7e552c0 CR3: 247d5000 CR4: 00000690
May  5 15:49:57 granjerox-laptop kernel: [25239.348115] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
May  5 15:49:57 granjerox-laptop kernel: [25239.348120] DR6: ffff0ff0 DR7: 00000400
May  5 15:49:57 granjerox-laptop kernel: [25239.348131]  [<f8c5001a>] firegl_open+0x8a/0x210 [fglrx]
May  5 15:49:57 granjerox-laptop kernel: [25239.348253]  [security_inode_permission+0x1c/0x20] security_inode_permission+0x1c/0x20
May  5 15:49:57 granjerox-laptop kernel: [25239.348270]  [<f8c4589f>] ip_firegl_open+0xf/0x20 [fglrx]
May  5 15:49:57 granjerox-laptop kernel: [25239.348380]  [<f8c471d0>] firegl_stub_open+0xb0/0x100 [fglrx]
May  5 15:49:57 granjerox-laptop kernel: [25239.348488]  [kobject_get+0xf/0x20] kobject_get+0xf/0x20
May  5 15:49:57 granjerox-laptop kernel: [25239.348503]  [<f8c47120>] firegl_stub_open+0x0/0x100 [fglrx]
May  5 15:49:57 granjerox-laptop kernel: [25239.348610]  [chrdev_open+0xa3/0x190] chrdev_open+0xa3/0x190
May  5 15:49:57 granjerox-laptop kernel: [25239.348630]  [__dentry_open+0xbf/0x1c0] __dentry_open+0xbf/0x1c0
May  5 15:49:57 granjerox-laptop kernel: [25239.348646]  [nameidata_to_filp+0x35/0x40] nameidata_to_filp+0x35/0x40
May  5 15:49:57 granjerox-laptop kernel: [25239.348657]  [chrdev_open+0x0/0x190] chrdev_open+0x0/0x190
May  5 15:49:57 granjerox-laptop kernel: [25239.348669]  [do_filp_open+0x50/0x60] do_filp_open+0x50/0x60
May  5 15:49:57 granjerox-laptop kernel: [25239.348688]  [sys_chown+0x54/0x70] sys_chown+0x54/0x70
May  5 15:49:57 granjerox-laptop kernel: [25239.348702]  [get_unused_fd_flags+0x52/0xd0] get_unused_fd_flags+0x52/0xd0
May  5 15:49:57 granjerox-laptop kernel: [25239.348718]  [do_sys_open+0x4c/0xe0] do_sys_open+0x4c/0xe0
May  5 15:49:57 granjerox-laptop kernel: [25239.348735]  [sys_open+0x1c/0x20] sys_open+0x1c/0x20
May  5 15:49:57 granjerox-laptop kernel: [25239.348746]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
May  5 15:49:57 granjerox-laptop kernel: [25239.348764]  [unix_dgram_recvmsg+0x110/0x2d0] unix_dgram_recvmsg+0x110/0x2d0
May  5 15:49:57 granjerox-laptop kernel: [25239.348780]  =======================
May  5 15:50:09 granjerox-laptop kernel: [25251.135459] BUG: soft lockup - CPU#1 stuck for 11s! [Xorg:24242]
May  5 15:50:09 granjerox-laptop kernel: [25251.135464] 
May  5 15:50:09 granjerox-laptop kernel: [25251.135469] Pid: 24242, comm: Xorg Tainted: P        (2.6.24-17-generic #1)
May  5 15:50:09 granjerox-laptop kernel: [25251.135474] EIP: 0060:[ipv6:_spin_lock+0x7/0x10] EFLAGS: 00003286 CPU: 1
May  5 15:50:09 granjerox-laptop kernel: [25251.135482] EIP is at _spin_lock+0x7/0x10
May  5 15:50:09 granjerox-laptop kernel: [25251.135487] EAX: f8dbb6e8 EBX: 00000000 ECX: f8dbb6c0 EDX: 00000400
May  5 15:50:09 granjerox-laptop kernel: [25251.135491] ESI: f369db40 EDI: 00000000 EBP: f8d5c2a0 ESP: f3779e98
May  5 15:50:09 granjerox-laptop kernel: [25251.135496]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
May  5 15:50:09 granjerox-laptop kernel: [25251.135500] CR0: 8005003b CR2: b7e552c0 CR3: 247d5000 CR4: 00000690
May  5 15:50:09 granjerox-laptop kernel: [25251.135506] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
May  5 15:50:09 granjerox-laptop kernel: [25251.135512] DR6: ffff0ff0 DR7: 00000400
May  5 15:50:09 granjerox-laptop kernel: [25251.135523]  [<f8c5001a>] firegl_open+0x8a/0x210 [fglrx]
May  5 15:50:09 granjerox-laptop kernel: [25251.135645]  [security_inode_permission+0x1c/0x20] security_inode_permission+0x1c/0x20
May  5 15:50:09 granjerox-laptop kernel: [25251.135662]  [<f8c4589f>] ip_firegl_open+0xf/0x20 [fglrx]
May  5 15:50:09 granjerox-laptop kernel: [25251.135772]  [<f8c471d0>] firegl_stub_open+0xb0/0x100 [fglrx]
May  5 15:50:09 granjerox-laptop kernel: [25251.135880]  [kobject_get+0xf/0x20] kobject_get+0xf/0x20
May  5 15:50:09 granjerox-laptop kernel: [25251.135895]  [<f8c47120>] firegl_stub_open+0x0/0x100 [fglrx]
May  5 15:50:09 granjerox-laptop kernel: [25251.136003]  [chrdev_open+0xa3/0x190] chrdev_open+0xa3/0x190
May  5 15:50:09 granjerox-laptop kernel: [25251.136022]  [__dentry_open+0xbf/0x1c0] __dentry_open+0xbf/0x1c0
May  5 15:50:09 granjerox-laptop kernel: [25251.136038]  [nameidata_to_filp+0x35/0x40] nameidata_to_filp+0x35/0x40
May  5 15:50:09 granjerox-laptop kernel: [25251.136050]  [chrdev_open+0x0/0x190] chrdev_open+0x0/0x190
May  5 15:50:09 granjerox-laptop kernel: [25251.136062]  [do_filp_open+0x50/0x60] do_filp_open+0x50/0x60
May  5 15:50:09 granjerox-laptop kernel: [25251.136081]  [sys_chown+0x54/0x70] sys_chown+0x54/0x70
May  5 15:50:09 granjerox-laptop kernel: [25251.136098]  [get_unused_fd_flags+0x52/0xd0] get_unused_fd_flags+0x52/0xd0
May  5 15:50:09 granjerox-laptop kernel: [25251.136114]  [do_sys_open+0x4c/0xe0] do_sys_open+0x4c/0xe0
May  5 15:50:09 granjerox-laptop kernel: [25251.136131]  [sys_open+0x1c/0x20] sys_open+0x1c/0x20
May  5 15:50:09 granjerox-laptop kernel: [25251.136142]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
May  5 15:50:09 granjerox-laptop kernel: [25251.136161]  [unix_dgram_recvmsg+0x110/0x2d0] unix_dgram_recvmsg+0x110/0x2d0
May  5 15:50:09 granjerox-laptop kernel: [25251.136178]  =======================
May  5 15:51:09 granjerox-laptop syslogd 1.5.0#1ubuntu1: restart.

```I've had also ramdomly crashes of firefox 3 beta 5.

I'm using Ubuntu 2.6.24-17.31-generic in Hardy 8.04

---

### Post by rodrigouroz on 2008-05-05
Hi

I installed Hardy this weekend and started getting this lock-ups. In my case the system totally freezes, no mouse, no activity, no SysqReq, no caps lock num lock. Nothing. The only thing I can do is power off and on again (besides burning it down).

The only thing that I did to "at least up to now" solve the problem was not using the restricted drivers (I have an Nvidia 6100 card) but the free one (nv).

I do have a wireless card (Broadcom 4311) but up to now I didn't have a new lock-up.

Will let you know if this happens to me again with this setup.

---

### Post by landeel on 2008-05-05
Removing the wireless driver didn't help in my case.
Have you noticed many people here with this same problem have alike videocards? GeForce 6100, 6200, 6150 (mine). They all seem to lockup with kernel 2.6.24 and NVIDIA proprietary drivers.

---

### Post by granjerox on 2008-05-06
> **landeel said:**
> Removing the wireless driver didn't help in my case.
Have you noticed many people here with this same problem have alike videocards? GeForce 6100, 6200, 6150 (mine). They all seem to lockup with kernel 2.6.24 and NVIDIA proprietary drivers.

I don't think so, I have ati mobility radeon x1400 with fglrx drivers from repo and wireless
card ipw3945. And my system has also crashed. I have to say that I use compiz fusion too.

---

### Post by AlchemyMan on 2008-05-06
I just downloaded the new updates...so I'll be keeping my fingers crossed. Unfortunately, with my version of the problem, I probably won't be able to tell conclusively for days.

I am running a Compaq Presario Laptop with an ATI Mobility Radeon 9600, and a Broadcom Wireless card, 1.0 gig of ram. I can usually run fine for several hours, but have been getting "partial" freezes much too often (getting to know the EISUB shortcut rather intimately now, whereas in Gutsy I never even had to think about it). My mouse works, and a few processes continue running, but I cannot start up any programs, nor shut down the "usual" way. 

Compiz turns out to not be the issue (though things in general seem to run a teensy bit slower on Hardy than they used to on Gutsy), since I've been running without it the last few days (doing a lot of Blender work, and in my experience Blender and Compiz don't seem to get along on my machine) and have had two such lockups since then, one only a few minutes ago. They seem to occur randomly, though I usually have Firefox running. This last time, however, I didn't. There was nothing really heavy going on, if I recall correctly. I was trying to open up an MP3, I think.

If what has been fixed in the Updates is a PCI slot issue, I suppose that's not what I have wrong. I have pretty much everything running on USB. But once again, I will keep my fingers crossed...

---

### Post by dreamsR4living on 2008-05-06
Even after a new fresh install and installing the new updates Hardy still freezes randomly. 

The bug is reported by several people on launchpad. Please report the bug there too, to help the developers find a solution, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209830](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209830).

---

### Post by jspangler on 2008-05-06
I'm having similar problems too. I posted logs on launchpad. I'm running a Dell inspiron 600m. Freezes when using wireless or wired. FF3 sometimes freezes. Acroread always freezes.

---

### Post by Jare on 2008-05-06
Hi, i have the same symptoms on my Dell C400 laptop ([http://ubuntuforums.org/showthread.php?t=782904](http://ubuntuforums.org/showthread.php?t=782904)). Let's hope there will be a fix soon.

---

### Post by kakyoism on 2008-05-06
same here. 
no pattern at all.
anything could freeze it. 
the only common condition is multitasking
it generally happens when i have multiple processes,
networking, multimedia(especially video), and office applications.

maybe dual core processor could have some fingerprint on it?

---

### Post by Tiago Neves on 2008-05-06
Hi there,

Im from brazil, e I had that same problem, and this was Video Board Driver. 

Pentium 4 D
1gb RAM
ATI video board

but I had this problem in orders, and solved installing drivers with download it from oficial site.

I hope help you

bye

---

### Post by alejandro.mc on 2008-05-08
No news on this thing???

---

### Post by Mighty_Joe on 2008-05-08
> **dreamsR4living said:**
> The bug is reported by several people on launchpad. Please report the bug there too, to help the developers find a solution, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209830](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209830).

Per the [kernel team]("https://bugs.launchpad.net/ubuntu/+bug/204996/comments/192"), if your hardware differs from a bug's original poster, post a new bug. The "freeze" bugs are getting pretty unmanageable with all the "me too" posts. 
If the bug you submit turns out to be a duplicate, the maintainers can mark it as such in the tracker.
Also, when reporting a bug, make sure you include all the [relevant information]("https://wiki.ubuntu.com/KernelTeamBugPolicies").

---

### Post by Seks on 2008-05-10
I found a fix for my configuration. 

- I am using a CNet CWP-854 PCI wireless card out-of-the-box.

- Used wine to install the windows driver from the disk.

- Used Ndiswrapper to use that driver.


And I haven't had a freeze yet. Whatever wireless PCI drivers hardy comes with must have the crucial bug. If anyone has this problem only when using the web, I suggest finding a new driver for your wireless card, regardless of if you can connect already.

---

### Post by alejandro.mc on 2008-05-12
Any news on this..? I'm still having lock ups..

---

### Post by ov1d1u on 2008-05-12
I have a similary problem, too:

First time, I have tried to install Ubuntu Hardy from CD. The installer has started, I have configured the installation, the copying of files started, but the system has freezed at files copying, at 24%.

Ok, I have rebooted my PC, I have restarted the Installer, the files started to copy, and my system freezed again at copying files.

I have tried again: I have re-writed the iso file on a new CD, I have restarted the installer, the files started to copy, and the system freez again at files copying.

After that, I have downloaded the Kubuntu hardy ISO. I have started the installer, the installer started to copy files and my system freezed again.

Finally, I have installed Ubuntu Gutsy and upgraded to Hardy.

But my problem wasn't solved. Every time when the PC read data from a CD or DVD disc, it was freezing. I have tried a lot of fixes, but it doesn't work... while I have changed the CD drive from Secondary IDE cable to primary IDE cable. Now when I'm using CD's I have no problem.

But I have a problem: I want to buy a new HDD drive and I don't have when to connect it, because every kind of drive connected on Secondary IDE make my system to freeze :(

I should mention that this problem doesn't appear when I am using the kernel 2.6.24-14 kernel. I have this problem in kernel 2.6.24-16 and kernel 2.6.24-17.

There is an image of what's happening when my pc freezes, made from tty1
[[IMG]http://img37.picoodle.com/img/img37/4/5/12/t_Ovi021m_d5e9d68.jpg[/IMG]](http://www.picoodle.com/view.php?img=/4/5/12/f_Ovi021m_d5e9d68.jpg&srv=img37)

---

### Post by trent1980 on 2008-05-13
just adding a note ...

Mine ran fine (I've been running 8.04 for over a month) until Friday (May 2nd). I didn't even know there was a forum for a known issue until I started looking today. I lock up randomly every 3 hours or so. Nothing I know seems to trigger it. I do notice that my Rhythmbox stops streaming music and then the lock occurs. I lose the mouse and everything.

My Hardware:
Thinkpad T60
Core 2 2Ghz
1gb RAM
945GM Chipset
Radeon X1400

I have uninstalled FF3 and gone back to FF2. I am also using the ndiswrapper for my wireless driver (which hasn't caused any problems for the last month or more).

---

### Post by trent1980 on 2008-05-13
Well it's not FF3 for me ... it just froze again.

---

### Post by landeel on 2008-05-13
Try Kernel 2.6.22. I bet it will work.

You can get it here:
[http://packages.ubuntu.com/gutsy/base/linux-image-2.6.22-14-generic]("http://packages.ubuntu.com/gutsy/base/linux-image-2.6.22-14-generic")

You can install with 'sudo dpkg -i --force-all file.deb'. It can cause broken dependencies. Do it at your own risk.

---

### Post by ScoobyDoom on 2008-05-14
I'm experiencing the same problem, Ubuntu 8.04 freezes and there's nothing I can do about it, only shut down my laptop and turning it on again.

What's interesting is that it **always** freezes when I try to connect to a wireless network in a certain bar. And it's the only wireless network that seems to cause the lock-up. I've connected to dozens of wireless networks (with all kinds of settings) without a hitch. Also, I have not experienced this problem with Gutsy, only Hardy.

I should note that I have a Dell Vostro 1000 with a Dell Wireless 1395 WLAN mini-card and I use NDISwrapper. I'm going to ask the bar tender what's their router's make and model.

Thanks!

---

### Post by Mighty_Joe on 2008-05-14
Try [Fedora 9]("http://fedoraproject.org/"). I've got about 33 minutes out of this install so far and that triples the uptime I've been seeing with Hardy (I'm posting with it now!). 
Fedora has a newer kernel than Ubuntu  (2.6.25-14.fc9.i686 vs. 2.6.24-4.6-generic) and different patches so that may be why.
Word of warning:  Fedora aims to be a bleeding-edge distro where Ubuntu aims for ease-of-use.  There *will* be bugs.
Furthermore, Fedora tries to be more "Free" than Ubuntu.  They don't support proprietary formats like MP3's or DVD's like Ubuntu does.  
But for me, It Just Works (so far, crossing fingers).

Update: So far so good.  2:20 of uptime

---

### Post by XulluX on 2008-05-15
I have this same issues but also will be on the internet and have Thunderbird open and will get this fuzzy screen and then have to log in again losing what ever I was doing.  I only seems to happen when I'm switch between Thunderbird and Firefox doing work.  I watched a few movies this morning and also setup and used my system as a media server for my PS3 and no locks ups.  But as soon as I was done watching my movie I checked my email in Thunderbird and was referencing something on Google Calendar and boom black fuzzy screen and logged out.
Thunderbird version 2.0.0.14 (20080505)
Firefox/3.0b5

Ubuntu 8.04

Gateway 
Model: Gateway GT5464
2 Western digital ATA 160GB hard drives 
Dual boot with windows Vista
onboad Graphics 

No problems when running 7.10

---

### Post by trent1980 on 2008-05-15
> **landeel said:**
> Try Kernel 2.6.22. I bet it will work.

You can get it here:
[http://packages.ubuntu.com/gutsy/base/linux-image-2.6.22-14-generic]("http://packages.ubuntu.com/gutsy/base/linux-image-2.6.22-14-generic")

You can install with 'sudo dpkg -i --force-all file.deb'. It can cause broken dependencies. Do it at your own risk.

My install of Hardy worked fine for the past 2 months ... just within the last week did it start the freezing thing. So I'm pretty  convinced that either the non beta release or an update got me. 

Anyone else hear anything about this? patch?

---

### Post by GrantsV on 2008-05-15
After weeks of torture, I fixed the freezing thing on 2 pcs with this one line:

sudo apt-get remove powernowd

(cpu scaling program)

Hope this helps!

---

### Post by trent1980 on 2008-05-15
> **GrantsV said:**
> After weeks of torture, I fixed the freezing thing on 2 pcs with this one line:

sudo apt-get remove powernowd

(cpu scaling program)

Hope this helps!

I'll give it a shot ... the random lockup makes me feel like I'm running XP with an ubuntu skin.

Do you know if there was a recent update released for powernowd? It seems weird that it worked fine for 2 months and then started acting up.

---

### Post by cwbar_1 on 2008-05-17
I don't know whether or not this will help anyone or not, but if you happen to be on an HP laptop and are using a USB external mouse, disconnect it.  I have had no lockups in firefox for over 2 days.  My computer has quit  grey-screen lockups. (really just hiccups)  The only real problem now is my thumbs keep tapping the synaptics pad and moving my cursor.

---

### Post by the badger on 2008-05-17
After reading/scanning through the past eleven pages, I'm wondering if anyone is simultaneously experiencing Xorg shutdowns (I don't know if I'm phrasing this right)? As in: Black screen comes up with no apparent instructions -- seems to be doing a shutdown but it doesn't shutdown. I posted about this in [General Help]("http://ubuntuforums.org/showthread.php?t=795756").

I'm trying to ascertain whether this is in some part a hardware problem particular to myself (as symptoms include giltchy sound, video, these random lockups, and even more random crashes) or if it's just the growing pains of a young heron.

---

### Post by rmccabe3701 on 2008-05-18
cwbar_1:  I have to agree with you: the problem seems to be with usb.  A few weeks ago I randomly tried disabling all usb capabilities by commenting out the line

> 
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0 


in /etc/fstab. I have not had any lockups since then!  Obviously, I have no usb capabilities, however.  I will attempt to compile a new kernel (perhaps the 2.6.22 version ?) and will get back to you.

---

### Post by rgagnon1967 on 2008-05-19
> **GrantsV said:**
> After weeks of torture, I fixed the freezing thing on 2 pcs with this one line:

sudo apt-get remove powernowd

(cpu scaling program)

Hope this helps!
Did not work for me, my PC froze three days after having removed the powernowd package.

I have been having this freezing problem since Gutsy. Upgrading to Hardy did not change a thing.

Gigabyte DS3P
Intel Core 2 Duo 6750
NVidia GeForce 8600 GT with restricted driver
Firewire external disk
USB scanner (HP ScanJet 4100C)
USB Laser printer (Samsung ML-1710)

Can I do something to help?

---

### Post by pfvasconcellos on 2008-05-19
> **GrantsV said:**
> After weeks of torture, I fixed the freezing thing on 2 pcs with this one line:

sudo apt-get remove powernowd

(cpu scaling program)

Hope this helps!


Works for me. On a HP Pavillion dv6230BR. Tks!

---

### Post by HoMe_CaNiBaL on 2008-05-19
Hi...

I have been post in this thread ([here](http://ubuntuforums.org/showpost.php?p=4883399&postcount=75)) that my ubuntu freezes.

I remove powernowd and the machina works about 5days without freeze, but after install a few things and a few restarts, the machine start freeze again!

It work everything, transmission continue downloading, and receive mails, etc etc, but the image...freeze. I can move my mouse, but i can't reset X, or do anything with the keyboard!

Suggestions.

---

### Post by dreamsR4living on 2008-05-22
I just got this e-mail as I am getting e-mail notifications about the Hardy Freezes bug report on Lanchpad;

> Thanks for testing and the feedback.  It seems this issue is resolved for you with the upcoming 2.6.25 Intrepid kernel.  Since you are the original bug reporter, I'm going to mark this bug as Fix Released
against Intrepid.  It would be good to also try to isolate the patch
which could possibly be backported to Hardy.  However, this may prove
difficult for the developers to isolate since they have differing
hardware.  How comfortable would you be at performing a git-bisect?
It's obviously not something we expect you to do but I could try to walk
you through the appropriate steps.

The new Intrepid Ibex 8.10 kernel 2.6.25 could be a solution, read this page for more info; [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/204996/comments/192](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/204996/comments/192)

---

### Post by trent1980 on 2008-05-22
> **GrantsV said:**
> After weeks of torture, I fixed the freezing thing on 2 pcs with this one line:

sudo apt-get remove powernowd

(cpu scaling program)

Hope this helps!

I'm 4 days now without a lock up / freeze. Thanks --

ThinkPad T60

---

### Post by Mighty_Joe on 2008-05-22
> **dreamsR4living said:**
> 
The new Intrepid Ibex 8.10 kernel 2.6.25 could be a solution, read this page for more info; [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/204996/comments/192](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/204996/comments/192)

Are you going to persue the git-bisect that Leann mentions [here?]("https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/204996/comments/223")  You'd be doing all us "freezers" a big favor if the developers could identify the critical differences between the Hardy and Intrepid kernels that fix this bug.  
I'm going to see if I can get some free time to test the Intrepid kernel as well.

---

### Post by Art R Big on 2008-05-22
Hi,

I thought I should add my observation as I hope there will be a solution soon. I am not a computer programmer and manages to use GNU/Linux by using the Graphic User Interface only. This strange freeze that happens is a new thing and has manifested itself after I wiped my drive and installed a new multiboot system with Hardy Heron the final version of PCLinuxOs 2007 and the latest PCLinux mini 2008. All the installed operating systems now has the GUI freeze problem apart from the Windows Xp partition so it is unlikely to be a hardware problem.

My previous multiboot (Ubuntu PCLinuxOs Vector) system did not have this freeze problem and my PCLinuxOs was working fine until I decided to be a good boy and do a synaptic security update that introduced the GUI freeze problem (everything stops responding, can still move the mouse and sometimes the system starts responding again after a minute and sometimes not). Hardy Heron is Ubuntu coming close to perfection, even the brown theme now works, shame about the bug I hope our suffering will be short lived.

Art R Big

---

### Post by Mighty_Joe on 2008-05-23
> **dreamsR4living said:**
> 
The new Intrepid Ibex 8.10 kernel 2.6.25 could be a solution, read this page for more info; [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/204996/comments/192](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/204996/comments/192)

This works for me.  I installed the 2.6.25 kernel and I've got 6 hours of uptime (compared to less than 10 minutes with the Hardy 2.6.24 kernel).
Fedora 9, which I had success with also, comes with the 2.6.25 kernel as well.

---

### Post by newUser1981 on 2008-05-24
hey there, i wanna try the 2.6.25 too! But I don't know how to install the restricted modules. 

So how can I install the restricted kernel modules for 2.6.25?

---

### Post by alejandro.mc on 2008-05-25
Any progress with this bug?

Disabling or uninstalling that "powernowd" will have any consequences (i mean is there a risk to doing this). I'm asking this since some seem to have solved the issue doing so.

Thanks!

---

### Post by Mighty_Joe on 2008-05-25
> **newUser1981 said:**
> 
So how can I install the restricted kernel modules for 2.6.25?

It should be something like:
```
sudo apt-get install linux-restricted-modules-<kernel version>
```

You can do
```
apt-cache search linux-restricted 
```
to see what's available.

---

### Post by earther on 2008-05-26
I've scanned through this thread and it looks like I'm not the only one!  I am testing Hardy in two environments - an old Dell Dimension and in Virtual Box.

The old Dell suffers the worst lockups.  No wireless (still on dialup), no fancy video card (an old nVidia Riva), PS/2 keyboard and mouse (no USB).  40GB drive, older P3 and about 500MB RAM.  I am using acpi=force otherwise it won't poweroff at shutdown.  FF2 or FF3 didn't seem to make a difference (though FF3 is a real PITA for other reasons).

In Virtual Box on my smoking new machine things are better but still occasional freezes.  Still using PS/2 keyboard and mouse and dialup. nVidia 8400GS, 2GB RAM, Core2 Duo 2.66Ghz.  Compiz is enabled on the Gutsy host but not in VB (don't know if that's even possible).  Again FF2 or 3 doesn't seem to make a diff.

Most often things will lock up when I try to drag and drop a file.

Hope that helps to eliminate some of the suggested culprits - USB, wireless, video drivers etc.

---

### Post by dreamsR4living on 2008-05-26
> So how can I install the restricted kernel modules for 2.6.25?

Go to System -> Administration -> Software Sources. Under Ubuntu Software check Proprietary drivers for devices (restricted). Then go to the second tab "Third-Party Software" and add the following two lines and make sure they are checked;

> deb [http://ppa.launchpad.net/kernel-ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ubuntu) hardy main

> deb-src [http://ppa.launchpad.net/kernel-ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ubuntu) hardy main

In terminal run;

> sudo apt-get update

And to install the new kernel;

> sudo apt-get install linux-image-2.6.25-1-generic

I tried the 2.6.25 kernel today but it doesn't work for me as it stops loading Ubuntu half way when I start up my computer.

I would suggest to just try it and if it doesn't work for you, just boot back into your old kernel and;

> sudo apt-get remove linux-image-2.6.25-1-generic

Please report your findings back to this thread.

---

### Post by hal_bg on 2008-05-26
I have Dell C400 laptop.
I have installed 2.6.25 from ppa and my lockups ceased, but I have a problem with my audio. Skype, Flash etc... are not producing any sounds and skype reports problem with audio device, but some applications are able to produce some sounds but no control on the volume.

Any idea what might be wrong?

---

### Post by newUser1981 on 2008-05-27
> **dreamsR4living said:**
> Go to System -> Administration -> Software Sources. Under Ubuntu Software check Proprietary drivers for devices (restricted). Then go to the second tab "Third-Party Software" and add the following two lines and make sure they are checked;





In terminal run;



And to install the new kernel;



I tried the 2.6.25 kernel today but it doesn't work for me as it stops loading Ubuntu half way when I start up my computer.

I would suggest to just try it and if it doesn't work for you, just boot back into your old kernel and;



Please report your findings back to this thread.



Hey thanks for the help. I had no problem to start the 2.6.25 kernel but I still can't install the **restricted modules**! 

I can't find a package like "linux-restricted-modules-2.6.24-17-generic" for the 2.6.25 and so i can't use my wireless (madwifi) and graphic card (fglrx)!

Any idea where i can get the **restricted-modules** for the kernel 2.6.25?

---

### Post by weaver4 on 2008-05-31
Does not look like 2.6.25-1-generic is available anymore.

---

### Post by redbob on 2008-05-31
Hi, Guys!
I was following this issue, cause I've got three computers running Hardy. One of them began to freeze gdm, so taskbar hides and nothing more function, except Ctrl-Alt-1, to enter CLI. My problem was solved when I figured out with my home partition with just 1% of idle space. I know that it must not be the same case of yours, but the message I found in syslog whas that: SIGABRT

---

### Post by marksmarks on 2008-06-01
Please forgive me if I've posted this in the wrong place, or posted the obvious.  I'm still in the dark about some of what happens "under the hood" in Linux.  

  I loved Ubuntu 7.04.  Then I did a fresh install of Ubuntu Hardy 8.04 and that's when the problems started. A occasional lock up caps/scroll leds blinking.


I applied all updates yesterday (May 31) to my fresh 8.04 install (installed in April).

Then, today June 1, I had to reboot my 8.04 box 7 times before I could get a working desktop. 

1)Sometimes I got just a mouse pointer on a blank brown desktop.

2)Sometimes hung playing back the successful login 
music ta-da-ta-  da-da-da-da-da-da-da... same note over and over.

3)Sometimes the desktop, top and bottom tool bars would appear, then disappear, then reappear....

4)Switching to console #1 I saw a screen full of saw stuff like;

[237.618943] [<e09e4071] __ext3__get__inode__loct0x241/0x360 [ext3]
.
.
.
CODE 24 14 9C 58 0F 1F....
.
.
.
[237.624198] ___[end trace 080e2d8bab609cba]...

  Thinking about giving up on Ubuntu!  
Previous version of Ubuntu ran without problems on this same computer.  Will 7.04 be supported until 8.04 is stable?

PS: On the 8th boot I finally got Ubuntu 8.04 to run and am posting this from it.

---

### Post by forty4 on 2008-06-01
> **alejandro.mc said:**
> Any progress with this bug?

Disabling or uninstalling that "powernowd" will have any consequences (i mean is there a risk to doing this). I'm asking this since some seem to have solved the issue doing so.

Thanks!

The only thing it would really affect is when your running on battery your cpu wont scale down possibly resulting in less battery time.  Also the cpu is scaled down to keep the heat down.

---

### Post by kevdog on 2008-06-01
Its still freezing on me -- I think its a kernel issue.  I have an Acer - intel integrated graphics card (no nvidia), and run madwifi (no ndiswrapper).  System totally locks up.  I couldn't boot into rt kernel -- however possibly LUKS has something to do with it!

---

### Post by dreamsR4living on 2008-06-02
> Thinking about giving up on Ubuntu!

I was thinking about leaving Ubuntu too, trying several other Linux distro's, finding out that Debian Lenny and the new PCLinuxOS have the same problems. The lockups are not just an Ubuntu problem, they are a general 2.6.24 Kernel problem, which will likely not be solved until the 2.6.25 comes out for Ubuntu (Ubuntu 8.10). Finally I went back to Ubuntu Gutsy, which is of course working great as before and seems to be the best solution.

> Previous version of Ubuntu ran without problems on this same computer. Will 7.04 be supported until 8.04 is stable?

I guess Ubuntu 7.04 will be supported until October 2008, so that's long enough. You can also think about upgrading to 7.10 which is the same as 7.04,  it only has some new features (compiz-fusion working out of the box), will be supported until April 2009 and is also lockup free as it uses the 2.6.22 kernel.

---

### Post by tomsen_san on 2008-06-02
> **dreamsR4living said:**
> ... Finally I went back to Ubuntu Gutsy, which is of course working great as before and seems to be the best solution.


I am at the same point now. What's the easiest way to get back to 7.10? Just grab an ISO image and install over? I'm tired of these damn freezes! Working is impossible for now ...

---

### Post by dreamsR4living on 2008-06-02
> What's the easiest way to get back to 7.10? Just grab an ISO image and install over? I'm tired of these damn freezes! Working is impossible for now ...

That's what I did, it seems to be the easiest way to me and you will surely start with a fresh, new and freezeless system :-)

---

### Post by brethren on 2008-06-02
> **dreamsR4living said:**
> The lockups are not just an Ubuntu problem, they are a general 2.6.24 Kernel problem


i had no other choice but to find another distro and i can tell you the latest fedora 9 doesn't suffer from crashes

---

### Post by kevdog on 2008-06-02
Im skeptical, but Ive just kept my Ubuntu box on for 24 hours (not using it, just letting it sit there), after removing the powernowd application -- and so far no crashes.  I'm scared to start using the machine -- might wake up the shutdown ghosts.  Who ya going to call.....

---

### Post by kevdog on 2008-06-03
Gd -- system just froze again when I opened pidgin.  This is really annoying!!!

---

### Post by dreamsR4living on 2008-06-04
> Does not look like 2.6.25-1-generic is available anymore.

That's true, that's because Intrepid Ibex now switched from the 2.6.25 to the 2.6.26 kernel. I don't know how to make either of those working as I am now using Gutsy again until Intrepid stable comes out in October. Suggestions anyone? Please post them.

---

### Post by alejandro.mc on 2008-06-04
So this isn't going to be fixed? Should I go back to gutsy a prepare for a long winter (in Buenos Aires is winter) without the latest Ubuntu? It's not fair..

Bye!

---

### Post by dreamsR4living on 2008-06-05
> So this isn't going to be fixed? Should I go back to gutsy a prepare for a long winter (in Buenos Aires is winter) without the latest Ubuntu? It's not fair..

Bye!

There is a chance the freezes will be fixed when Ubuntu 8.04.1 comes out at July 10th. Otherwise it will indeed not be fixed until October. So the best options are to indeed switch back to Gutsy or to abandon Ubuntu until October and use Fedora 9 instead, which has all the features Hardy has. 

The most other new Linux distro's use the (problematic) 2.6.24 kernel, including Debian Lenny, PCLinuxOS and the new OpenSuse, coming out June 19th.

---

### Post by Mighty_Joe on 2008-06-05
[QUOTE=dreamsR4living;5119130]. . .use Fedora 9 instead, which has all the features Hardy has. 
[QUOTE]

I'm not sure what "features" you mean.  Fedora 9 is using the 2.6.25 which apparently fixes the kernel freeze problem ([works for me]("https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/227882")).  That's a good thing.
Fedora, however, has a different philosphy than Ubuntu when it comes to open-source.  Where Ubuntu tries to make it easy to use things like MP3's and DVD's, which are protected in some countries by patents and legal measures, Fedora aims for only open and free programs and media, so it may take some work to get such things working with it.
Ubuntu also tries to be a stable desktop, where Fedora aims to be bleeding edge, so it may be a little more buggy, though by all accounts it is an excellent distribution.

---

### Post by GrantsV on 2008-06-05
Ok I'm back hanging again.  Powernowd worked a treat for a while but now its freezing.  What is going on?  PC works perfect in Windows...

---

### Post by dreamsR4living on 2008-06-05
> I'm not sure what "features" you mean.

I mean Gnome 2.22 and access to newer software like available in Hardy.

---

### Post by ChaOConnor on 2008-06-06
I'm trying to install Hardy on my tc1100, but I have to use the linux-image-2.6.25-1-generic kernel to get wacom working, and now that's gone.  Any suggestions?

---

### Post by JollyGreenDragon on 2008-06-07
I've been experiencing.. abnormal freezing.  As in, I can still move my mouse, but everything else is locked up tight.  Numlock/keyboard is frozen, etc.

Is anyone else experiencing this kind of freezing, or is it of the "typical" sort?

Also - running latest nVidia drivers, no wireless card and I tend to experience this when doing things in Firefox.

---

### Post by doktormiod on 2008-06-08
Hi, i posted this in another thread but i think this one maybe more appropriate so i'll just copy this:

Hi, I experienced this lockups too and i've tried every solution i found on this forum but none of them solve the problem. I read that this can be 2.6.24 kernel problem so finally i compile 2.6.25 and for a day or so everything seemed to work fine. Eventually I wanted to run compiz therefore I had to install fglrx. I installed the latest version from ati, run compiz --replace and a few seconds after my system froze on 2.6.25 kernel! To confirm that it's not kernel issue I installed some older gutsy kernel (2.6.22) and after some time it also froze :/. When i was using this kernel on gutsy it never locked up so here's what i think - It's not kernel issue and not compiz couse my system freezes when compiz is off too. It seems that proprietary driver for readeons is the problem becouse my freezes started after i installed it. Compiz and things like that could be kind of a trigger for real issue.

So why freezes happens to nvidia users too? ATI/Nvidia released buggy drivers simultanously? I don't think so :/

---

### Post by landeel on 2008-06-08
Well, I'm an NVIDIA user, and downgrading to kernel 2.6.22 really fixed my problem.

---

### Post by amdlintuxos on 2008-06-09
> **doktormiod said:**
> It seems that proprietary driver for readeons is the problem becouse my freezes started after i installed it. Compiz and things like that could be kind of a trigger for real issue.

**[COLOR="DarkGreen"]and NVIDIA driver issue too i guess.[/COLOR]**
> **landeel said:**
> Well, I'm an NVIDIA user, and downgrading to kernel 2.6.22 really fixed my problem.
**[COLOR="DarkGreen"]I guess after 2.6.22 instalation u have reinstalled NVIDIA driver too, or as minimum used other X.org (with different option).This also could give affect on stability(not only kernel)[/COLOR]**

****
[B][COLOR="DarkGreen"]As for me 
Mysistem works quet stable, than freez heppens ones.
Usually i have 3-5 freezes in a week, no so many, but never the less it's irritating me [/COLOR][/B]
.
[COLOR="Green"][B]How i return mystability?
i did 2 steps
1) i switch off my second core in BIOS (i don't think is that a reason of unstable work,i did this in any case, my tsk was get stable work on 2.6.24 and Compiz(3d should be working))
2) i renewed my NVIDIA driver (after that in order to get proper resolution, i reconfigured X.org, and put 2 additional string in order to avoid metacity's gone)
After that system works stable approx. 1.5 week
Today i'm going to switch on my second core in CPU
If system will stay stable, it definetaly something was wrong with NVIDIA driver or it's X.org configuration[/B][/COLOR]

---

### Post by Gruss2 on 2008-06-13
Has the freeze bug been definitely solved yet?  Because I continue to have them daily....even three or four times a day.  I would like a definite solution to this problem, because this has been going on for a long time now unsolved.

---

### Post by jmmL on 2008-06-13
I have this same problem and I've had it since Gutsy.
I just had a freeze 12 minutes after logging-on, and i can't find a pattern to it at all. Usually the freeze happens after a few hours.

At first I wondered if it was FF, but its frozen without that. It's also frozen on a completely fresh, vanilla install of Hardy without any updates, no nVidia proprietary driver (i have a 7900GS) and none of the compiz effects turned on.

First i lose my mouse cursor, but still have the keyboard. I can open up top, but nothing seems to be amiss there. When i try to do a ctrl+alt+f2 (or any of the f keys) everything locks up, and is only fixable with a hard reset.

Here are my specs;

AMD Athlon 64 X2 6000+
2GB Corsair ValueRAM
ASUS M2N-SLi Deluxe
Palit 7900GS 512MB
Creative X-Fi XtremeAudio

The system is a desktop, and I don't have any wireless cards

---

### Post by zach_denver on 2008-06-16
Hi guys, this is my first post here. I'm also a linux-novice, so bear with me.

My computer freezes about once every 2-days under Hardy; never had a problem under Gutsy. I'm running a Belkin (Broadcom Chipset) card and had to do a lot of command-line monkeying around to get it to work. (It installed much easier in Gutsy, all I had to do was install the restricted driver -- this is not an option in Hardy).

I do have a suggestion that may help some people concerned with doing a "hard-restart" -- on my machine, if I simply remove the PCMCIA card the machine melts (i.e. no longer frozen).  Hope that helps.

I just removed powernow (my computer doesn't have it, anyway), hopefully that will help.

My machine:

Sony Vaio PCG-fx210 (laptop)
ATI Rage Mobility Graphics
384 RAM
Ubuntu - 8.0.4
FF-3

Regards,

Zach

ps - thanks to everyone that has contributed to ubuntu, it is amazing

---

### Post by kevdog on 2008-06-16
According to launchpad, this bug has not been fixed thus yet!

---

### Post by zach_denver on 2008-06-20
> **zach_denver said:**
> 

I just removed powernow (my computer doesn't have it, anyway), hopefully that will help.


Nope, still freezes.

---

### Post by Michael Schmidt on 2008-06-20
Same problem here, total lock up of mouse (USB) and keyboard (PS/2 port).  Gutsy ran fine but Hardy (with all newest updates) freezes occasionally, twice this morning.  My system is Asus P4S8X mobo, 1 Gig ram, hard disk on SCSI, GeForce 5200 video, attached to Belkin 54g router.  The freezes happened 1) with evolution when I was viewing an e-mail with multiple images and went to delete it and 2) with text editor when I was rapidly opening and closing documents.  Several other applications have run without a hitch - Word Processor, Firefox (even with Zotero), Pan, PostgreSQL.

Hope this info helps and the bug gets fixed.  Except for this, Hardy is great!

---

### Post by cytg on 2008-06-21
Just wanted to pitch back in with my good news, crashes are gone.. rock solid stable system.
I dont know wich update did it, but i suspect it was an updated nvidia driver.

---

### Post by Mach1US on 2008-06-21
I have the same  problem since i upgraded to HH this monday.
It was working seamlessly until the upgrade.
I'm running 2.6.24-19-generic and it is still doing it.
I have noticed that it happens when the HD-indicator-light is flashing, at first i thought my HD was going but when i booted in XP it was fine so Hardy was definitely at fault.
One more thing i can add that i can kind of control it by stopping my mouse or track pad.
When it start to jam i just let go of my touchpad and it it starts working after a second or two but any time i try to continue it freezes permanently .

---

### Post by francesco44 on 2008-06-22
HARDY FREEZES.....

HELLO CANONICAL FOLKS.....DO YOU HEAR.... OR SHOULD WE SAY IT LOUDLY!


I  experienced that also.....it is absolutely IMPOSSIBLE to use that version 8,04 in ANY professional situation


PLEASE CORRECT IT FAST

Our recognition for a very nice system...WAITING TO BE USED PROFESSIONALY

Francesco44

---

### Post by dentaku65 on 2008-06-22
I've noted on one of my machine that the kernel 2.6.24-19-generic was causing random crash (I think a combination of video-screensaver + ff3 in background); I switched back to kernel 2.6.24-18-generic and now is perfect. I suggest to do not install -19 kernel (and to comment out the hardy proposed repos).

---

### Post by Mach1US on 2008-06-23
Still when running 2.6.24-18-generic or todays kernel update i'm getting freezes.

---

### Post by doubtintom on 2008-06-23
I've also been getting freezes with Hardy, several a day. And with every kernel release since 8.04 came out.  I thought it had to do with running VirtualBox. Eventually I gave up on that, but the freezes kept coming.

I read on one thread or other about this "ugly" workaround, which I tried today. 

sudo echo 1 > /proc/sys/vm/block_dump; cat /proc/kmsg; echo 0 > /proc/sys/vm/block_dump

By golly, it works, even thought it sucks down my processor something awful.  Better than freezing, but it is not a workable solution beyond learning "something" about the problem. I can even run VirtualBox without freezes. What does this suggest?

I always try to do REISUB, and I know how to do it, but it never does anything after one of these freezes. I have to hit the reset button.

Usually after such a freeze, upon restart ext3 invariably has to deal with 1 or more orphaned inodes. Obviously some file was open but didn't have time to close itself properly.

I luv my Heron, but I hope it can become more hardy real soon.

hopeful,
Tom

AMD Athlon 64 X2 Dual Core 4800+, 4GB RAM, WD Caviar 320 GB SATA, A8N32 SLI Deluxe, KDE 3.5.x, 2.6.24-19.28-generic updated today, Nvidia GeForce 6600, nvidia-glx-new driver

---

### Post by bred on 2008-06-23
[COLOR="Navy"]hi guys,

the only thing that solved my freeze of Hardy was **NOT TO USE** *wireless USB card*... 

tried different things to 'repair' and no change at all...[/COLOR]

---

### Post by bred on 2008-06-23
[COLOR="DarkRed"]I found this thread, 

hope will help someone

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/219810]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/219810")



c yah[/COLOR]

---

### Post by dentaku65 on 2008-06-24
mmm... the freeze it happens with -18 kernel too :-(
btw on my 3 machine only the one with AMD processor is going in freeze mode, the two intel notebooks works fine.... maybe the problem is there...

---

### Post by Mach1US on 2008-06-24
I have an Intel CPU but it freezes too , but i tried to work without my Wi-Fi (build in) card which is intel 2200BG miniPCI which is communicating with a kernel through USB bus on the motherboard which in turn makes it a USB related device.
I have been useing my wired (RJ45 to a Broadcom Gigabit card ) and a Verizon EVDO WAN card for work in the field and seems to be stable today so this may have been a problem , i'll report back on the findings.

---

### Post by Michael Schmidt on 2008-06-24
It appears the 6/23/08 updates solved the freeze problem on my computer, as well as a screen saver flicker annoyance :)

More generally, I want to thank the Linux, Ubuntu, and other related groups for their hard work.  Excellent software for free, and super responsiveness to users - what more could you ask for?

---

### Post by dentaku65 on 2008-06-24
Workaround to fix this freeze issue (in my case worked or at least did not freeze)

Install the kernel -18 and boot with that

open /etc/apt/sources.list and comment out all the lines pointing to hardy-proposed repos


Then do
```
sudo apt-get update
```
```
sudo apt-get clean
```

remove -19 kernel
```
sudo apt-get --purge remove linux-image-2.6.24-19-generic

```
then remove one or all of these packages
```
sudo apt-get remove clamav* samba samba-common winbind
```

reinstall the packages you remomoved previously
```
sudo apt-get install clamav* samba samba-common winbind
```

Uninstall FF3, keep your profile for the next release and install FF2
```
sudo mv ~/.mozilla ~/.mozilla.ff3
```
```
sudo apt-get remove firefox-3.0
```
```
sudo apt-get install firefox-2
```


Hope this helps

---

### Post by houstonbofh on 2008-06-24
I have been with Ubuntu since Breezy Badger, and I have never seen a distribution this consistently unstable.  Out of 40 systems, I have only installed Hardy on 2, and I have nightmares and freezes on both.  I dread the windows going gray and wonder if they will come back.  Regular hard locks with flashing keyboard lights...  And now the desktop crashes on each login, but I can ssh in all day.  Makes for a wonderful media PC...  So far, the only workaround that works is going back to Gutsy.

---

### Post by kboy on 2008-06-25
everyone suggests a different solution!!!
the problem is the same so shouldn't there be one solution to fix the freezes???

---

### Post by dentaku65 on 2008-06-25
> **kboy said:**
> everyone suggests a different solution!!!
the problem is the same so shouldn't there be one solution to fix the freezes???

kboy, you're quite ok; but I just post my workaround above, not more not less... in my case unistalling the latest hardy-proposed packages and ff3 works.

---

### Post by Gruss2 on 2008-06-25
> **dentaku65 said:**
> kboy, you're quite ok; but I just post my workaround above, not more not less... in my case unistalling the latest hardy-proposed packages and ff3 works.

If your solution does indeed work, it's a shame Fire Fox 3 has to be uninstall, because this is the best version of Fire Fox. Also, Ubuntu upgrade developers should be more vocal in these forums, especially since it was their updates/upgrades that caused this problem. Hearing various solutions doesn't help, especially for those who are newbies to Ubuntu.

---

### Post by bred on 2008-06-25
[COLOR="Blue"]does anybody tried **dentaku65**'s solution?[/COLOR]

---

### Post by nanotube on 2008-06-26
> **Gruss2 said:**
> If your solution does indeed work, it's a shame Fire Fox 3 has to be uninstall, because this is the best version of Fire Fox. Also, Ubuntu upgrade developers should be more vocal in these forums, especially since it was their updates/upgrades that caused this problem. Hearing various solutions doesn't help, especially for those who are newbies to Ubuntu.

if the repos version of firefox3 is crashy, but you still want firefox3, try using ubuntuzilla to install the mozilla build of ff3. 
[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)
and see if that fixes things.

another thing you can try: move your firefox profile out of the way, and start with a fresh profile.

---

### Post by dentaku65 on 2008-06-26
> **nanotube said:**
> if the repos version of firefox3 is crashy, but you still want firefox3, try using ubuntuzilla to install the mozilla build of ff3. 
[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)
and see if that fixes things.

another thing you can try: move your firefox profile out of the way, and start with a fresh profile.

Nanotube, no way, I verify that FF3 even if is present but not used (using FF2 instead) the machine freeze. Did not tried ubuntuzilla version.

---

### Post by dentaku65 on 2008-06-26
> **Gruss2 said:**
> If your solution does indeed work, it's a shame Fire Fox 3 has to be uninstall, because this is the best version of Fire Fox. Also, Ubuntu upgrade developers should be more vocal in these forums, especially since it was their updates/upgrades that caused this problem. Hearing various solutions doesn't help, especially for those who are newbies to Ubuntu.

I agree that is not ok this kind of situation for Ubuntu. For what I post above, after almost two days of not-freeze machine I pretty sure that the issue is caused by FF3, but the problem is that this freeze is not happening on all machines (in my case only one machine on four) and maybe this is the problem for the analysis.

---

### Post by radtek on 2008-06-27
Well, just to pitch my 2 cents... With edgy I ran my PC 24/7 with constant use for over a year with maybe 3 **voluntary reboots**. Not one single lockup, freeze or hang. Try that XP!

I installed 7.10 on my lappy and **while using[COLOR="Red"] FF[/COLOR]** I began to experience lockups as described, prompting a ctrl+alt+bksp to log out. Every so often it would need a hard reboot. I installed gutsy on my PC and bang! same problem. Way different hardware so it has to be software.

As soon as I could I installed hardy hoping the problem would be gone. After about two months of constant daily updates [COLOR="Red"]firefox[/COLOR] began fouling up my system again. Logging out seems to help but I think this is a poor approach. 

I really talk up linux and Ubuntu in particular, but maybe Canonical should slow down the release schedule because this is really unimpressive.
I don't feel right about introducing a newbie to linux and then see them suffer the same problems they are trying to escape.

I'm still a devoted linux/ubuntu user so I'm in it for the long run and I love open-source. Let's keep up the good work folks.

---

### Post by neoAnderson on 2008-06-27
For those of you who were trying to move on to openSUSE - I myself came from openSUSE to Ubuntu because it constantly used to freeze on my laptop for no apparent reason.

I have an HP Pavilion dv6375us, 2 GB RAM, nVidia GeForce Go 7400, 160GB HDD - and openSUSE 10.3 did NOT like my laptop. So I moved over to Gutsy - and I was a happy man for a while. Until Hardy. Unbelievable. Every time I boot into Hardy it freezes randomly and I have to do a hard boot. Not to mention that there's loads of updates almost every other day and the kernels are changing like anything.

Not quite the same as it used to be with Gutsy.

---

### Post by Dethecus on 2008-06-27
I have a problem with Ubuntu crashing on one particular machine, has done it in every version I've tried since 6.04. Only recently have I been able to track it down, seems that when it happens the whole screen freezes but I can remotely log in via SSH and when I run the 'top' command Xorg is chewing up 99% cpu. So I can kill Xorg and it unfreezes the computer but it boots me back to the gdm login screen. Whilst it is frozen all other functions seem to work, my torrents continue to download & I can access shares from it fine.

---

### Post by oligray on 2008-06-27
happened to me.. yesterday. but its the first time and i dont think it is linked.. lol

---

### Post by ryjo on 2008-06-27
> **neoAnderson said:**
> For those of you who were trying to move on to openSUSE - I myself came from openSUSE to Ubuntu because it constantly used to freeze on my laptop for no apparent reason.

I have an HP Pavilion dv6375us, 2 GB RAM, nVidia GeForce Go 7400, 160GB HDD - and openSUSE 10.3 did NOT like my laptop. So I moved over to Gutsy - and I was a happy man for a while. Until Hardy. Unbelievable. Every time I boot into Hardy it freezes randomly and I have to do a hard boot. Not to mention that there's loads of updates almost every other day and the kernels are changing like anything.

Not quite the same as it used to be with Gutsy.

I have used ubuntu very successfully on laptop and desktop machines since Dapper, and as others in this thread have emphasized: THANKS to the developers!

I have had mixed experience with Hardy.  Freezes make it unusable on my Linux Certified LC2464 laptop, and I found that Fedora Core 9 freezes in the same way on this machine.  On the other hand, Hardy works very well on my System76 Darter laptop (aside from a power management glitch).

---

### Post by enchesss on 2008-06-27
just out of curiosity - this problem was solved when using a seperate hard drive. mystified as to why. may be somethig different about the way hardy formats a previos ntfs partition? becuase previous versions did not have hte problem.

---

### Post by gingi on 2008-06-27
My experience:
My friend is using Hardy on her PC, with a LevelOne Wireless card.
When I instaled Ndiswrapper - the PC froze during boot every time.
When I removed Ndiswrapper and tried the native zd1211rw driver - the PC froze a second after I tried to connect to the internet.
On a whim I installed Wicd instead of network-manager, and it has been working for three days now.

---

### Post by Dethecus on 2008-06-28
Some more detail to add to my previous post, I have Ubuntu running on two machines as well as running a Windows XP machine. The problem computer is an AMD Sempron 2800+ with a Radeon 9200SE graphics card, I have tried it with SCSI hard drives and several different IDE drives without a change, ran memory tests, re-installed, tried different distro's they all seem to hang randomly on that machine. I'm thinking it's to do with my graphics card as Xorg is the process that hangs it and it is also too old for the fglrx driver... So I'll try a different graphics card and see what happens :)

---

### Post by Ziggy114 on 2008-06-28
I've had the same problem of completely random freezing - it doesn't seem to matter what I'm doing, and there is no set time period after a boot before it freezes. Completely random. I had this problem with Gutsy as well, and I was hoping that with the release of Hardy this would go away. No such luck. In Gutsy I tried a bunch of different things related to the video card, (using fglrx, ATI's proprietary driver, running Xorg) but nothing seemed to have any effect.

I read previously that this might be a problem with wireless drivers? I'm on a desktop, but due to its location relative to the router, I can't cable it in... so I bought an Atheros based wireless card. Any suggestions?

MB: ASUS P4P800 Deluxe
CPU: Intel P4 @ 3.2 GHz
RAM: 2.50 GB
Video: ATI Radeon 9700 Pro
WiFi: D-Link WDA-2320 (Atheros chipset)

---

### Post by GhettoYhetti on 2008-06-29
I did not run into this problem until I replaced my video card.

Old: nVidia MX 440 AGP 64MB using the restricted drivers

New: nVidia 6800 GT 256MB using nVidia proprietary drivers

Poof!  Let the freeze parade begin.

---

### Post by morbid_bean on 2008-06-29
Its because of this problem we all are having is going to be the reason my hard drive dies, i know it.:(

---

### Post by dentaku65 on 2008-06-29
Well, I found what is the problem of freeze in my case.
The problem is the hot temperature (in Italy is very hot in the last two weeks and my freezes are started 2 weeks ago); so I checked the temperature of my hardware components and I seen my CPU at 77° degrees and thats why machine freeze (maximum supported temperature is 70°). Fortunately in the BIOS I'm able to lowering the CPU clock from 200MHZ to 100MHZ, put the speeding fan continuously and every 1/2 seconds.
For now the machine is ok, not freezing anymore.
Please consider my post about the workaround posted while ago not useful for freeze situation.

---

### Post by External on 2008-06-29
> **Gruss2 said:**
> If your solution does indeed work, it's a shame Fire Fox 3 has to be uninstall, because this is the best version of Fire Fox. Also, Ubuntu upgrade developers should be more vocal in these forums, especially since it was their updates/upgrades that caused this problem. Hearing various solutions doesn't help, especially for those who are newbies to Ubuntu.


I've been experiencing the same freezes ever since i switched to Hardy from Gutsy and it's driving me nuts. Being blessed with a hardware config that is affected I am still waiting for a solution just as everybody else and the time has probably come for me to switch back to Gutsy, for the time being at least, until the problem is fixed. But.

Ubuntu developers are as vocal in these forums as they like to be, and I find it rather strange that you "criticize" them for not being present calming people. Yes, it is "their updates" that cause the problem, but **it is their work that "caused" Linux, and in turn Ubuntu in the first place** and I doubt we have the right to expect them to solve our problems in an instant as if Ubuntu was a commercial program, which we know it isn't. Moreover, as for me I've gotten much more help with any of my problems from the Ubuntu community than I would have ever gotten had I had problems with any dreaded Windows release. Patience and respect are our tasks while we are waiting for our problems to be solved. (Also if you want to help, consult developers @ launchpad.)

Please refer to "Linux is NOT Windows" especially Problem #7: That FOSS thing. [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by kevdog on 2008-06-29
I think it is a kernel issue rather than an Ubuntu issue from what I have read -- so blame Linus and not the Ubuntu developers.

---

### Post by External on 2008-06-29
> **kevdog said:**
> I think it is a kernel issue rather than an Ubuntu issue from what I have read -- so blame Linus and not the Ubuntu developers.

I thought it has already been confirmed a Kernel issue; with so many totally unrelated hardware configs affected: different video cards, drivers, wifi.. It must also be the reason why we get kernel updates ever so often: this wasn't the case with Gutsy, or was it?

Linus writes approx. 2% of the Kernel codes still, so he might not be the one to blame, but it's possible he didn't take his medication the day they "released" the version Ubuntu 8.10 is built on. (His "joke", not mine..)

---

### Post by Gruss2 on 2008-06-29
> **External said:**
> 
Ubuntu developers are as vocal in these forums as they like to be, and I find it rather strange that you "criticize" them for not being present calming people. Yes, it is "their updates" that cause the problem, but **it is their work that "caused" Linux, and in turn Ubuntu in the first place** and I doubt we have the right to expect them to solve our problems in an instant as if Ubuntu was a commercial program, which we know it isn't. Moreover, as for me I've gotten much more help with any of my problems from the Ubuntu community than I would have ever gotten had I had problems with any dreaded Windows release. Patience and respect are our tasks while we are waiting for our problems to be solved. (Also if you want to help, consult developers @ launchpad.)


You say the Ubuntu developers are vocal in these forums. Well I haven't read a thread where one posted mentioning or acknowledging this is a kernel issue and are currently working on a fix. For many Ubuntu users, just this communication would have been enough for us. At least there would have been acknowledgment of a problem. Instead, there was only communication going on in the forum between other Ubuntu users having same problems trying to figure out a solution to an "unknown problem". And to make things worst, there were too many solutions that weren't really solutions for most of the Ubuntu users who were having this problem. Therefore, this led to much confusion and many false solutions. Like I said before, when the developers knew this was a kernel issue, they should have **_immediately_** at least let the Ubuntu forum moderators know this. The moderators could have then posted an alert at the top of the Ubuntu forum page, letting all Ubuntu users know who visited the forum searching for a fix, that this is a known kernel issue and a fix is in the works. Because after weeks, we are now just discovering there really isn't anything we can do but wait for the fix or go back to Gutsy.

---

### Post by External on 2008-06-29
> **Gruss2 said:**
> You say the Ubuntu developers are vocal in these forums. Well I haven't read a thread where one posted mentioning or acknowledging this is a kernel issue and are currently working on a fix. For many Ubuntu users, just this communication would have been enough for us. At least there would have been acknowledgment of a problem. Instead, there was only communication going on in the forum between other Ubuntu users having same problems trying to figure out a solution to an "unknown problem". And to make things worst, there were too many solutions that weren't really solutions for most of the Ubuntu users who were having this problem. Therefore, this led to much confusion and many false solutions. Like I said before, when the developers knew this was a kernel issue, they should have **_immediately_** at least let the Ubuntu forum moderators know this. The moderators could have then posted an alert at the top of the Ubuntu forum page, letting all Ubuntu users know who visited the forum searching for a fix, that this is a known kernel issue and a fix is in the works. Because after weeks, we are now just discovering there really isn't anything we can do but wait for the fix or go back to Gutsy.


I never said developers were vocal on these forums, I said they were as vocal as they wished to be (at least this is what I meant). You may or may not have searched for a solution for our unexplained freezes elsewhere and found that several bug reports were submitted weeks ago to [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu), and as far as I know developers are working on the problem.
My only statement was to call attention to the fact that developers are not to be cursed but to be respected, they created what we are experiencing problems with and they are the ones who are gonna fix it. It is way beyond their capacity and it is not their job to search for each and every possible thread on these forums (there are many linking to the same problem and you have the same situation on launchpad) and inform everybody what the problem might be. Their job is to fix the problem, which they must be working on given the unusual frequency of kernel updates we get.

If you want to help them and report a problem so they can work on it, post a bug report on lauchpad, and do not wait for them to find out whether or not you have encountered a problem. This would be nonsense. For our information, several bug reports have been filed relating to the problem to my best knowledge and they are marked high priority. My point is: this is not a developers' forum. This is a users' forum, where users help users and if developers turn up it is solely because they felt like visiting, not because they are "finally doing their job". They have their own forum, where you can help them help you. Go there and see where they are at fixing our problems. If however we'd rather not do that, AND if we ourselves don't know programming languages, AND if we haven't helped them submitting a bug report and assisted them to find the bug by sending in additional info to lauchpad AND since Ubuntu is not a commercial program where we'd be paying for assistance, we cannot but be patient and be grateful once the problem is fixed.

---

### Post by yotam on 2008-06-30
Mounting partitions with the 'noatime' option via /etc/fstab setting 
significantly reduces disk access.

---

### Post by External on 2008-07-01
I found this at launchpad: [https://bugs.launchpad.net/ubuntu/+bug/227882/comments/9](https://bugs.launchpad.net/ubuntu/+bug/227882/comments/9), as a reply to bug 227882, description of which is available at [https://bugs.launchpad.net/ubuntu/+bug/227882](https://bugs.launchpad.net/ubuntu/+bug/227882).

I'm inclined to completely agree with the poster and according to his post many Hardy users are affected by the bug, **it IS indeed a kernel issue ** (meaning that either the kernel is faulty or its interference with Hardy updates is problematic), because  kernel 2.6.25 apparently fixes the problem, and update to .25 in Hardy is deliberately avoided by policy. I wonder what policy forbids such an update, does anyone know?

Anyhow, as it is also pointed out, too many Ubuntu users are staying away from Hardy for fear of experiencing freezes, and whatever policy forbids an update is not strategic. I sadly note that to my best knowledge Fedora 9, for instance features kernel 2.6.25. So shall we switch or go back to Gutsy - that is the question.:(:(

---

### Post by Mighty_Joe on 2008-07-01
> **External said:**
> I found this at launchpad: [https://bugs.launchpad.net/ubuntu/+bug/227882/comments/9](https://bugs.launchpad.net/ubuntu/+bug/227882/comments/9), as a reply to bug 227882, description of which is available at [https://bugs.launchpad.net/ubuntu/+bug/227882](https://bugs.launchpad.net/ubuntu/+bug/227882).

That's my bug.  I'm pretty sure the problem I'm having is kernel-related, as detailed in the bug description. 
I installed [Intrepid Ibex Alpha 1]("http://www.ubuntu.com/testing/intrepid/alpha1") last night and so far it's working fine (12 hours of uptime as opposed to 10 minutes with Hardy).  
Now I just have to wait until October for Ibex to be released. . .

---

### Post by kevdog on 2008-07-01
Developers do communicate but they are found more often in launchpad than in the forums.  If you have or experience a bug, report it in launchpad and you will more than likely receive at least a response or acknowledgement.

---

### Post by External on 2008-07-01
> **Mighty_Joe said:**
> That's my bug.  I'm pretty sure the problem I'm having is kernel-related, as detailed in the bug description. 
I installed [Intrepid Ibex Alpha 1]("http://www.ubuntu.com/testing/intrepid/alpha1") last night and so far it's working fine (12 hours of uptime as opposed to 10 minutes with Hardy).  
Now I just have to wait until October for Ibex to be released. . .


Hi Joe,

I do hope you/we get some response for the bug, as well as sergio callegari's post, who pretty much seems to have summed up what is known so far and I'm really curious about what a developer thinks about his points.
Having to wait for a next release is not a solution for most of the community (even though there's not much we can do I suppose), especially given Hardy's state of being the current LTS. I'm also a bit worried about using Ibex on a "mission critical" system, however thanks for reporting on it, I might give it a shot myself.

------------------------
_For all who do hard resets ever so often, don't forget to try to "Raise The Elephant" to reboot your Linux before you kill your hard disk :_

**ALT+CTRL+SysRq + R S E I U B **[i.e. "Raising Skinny Elephants Is Utterly Boring", the letters typed slowly after one another.] This always works.

---

### Post by carl_pr on 2008-07-01
> **Mighty_Joe said:**
> I feel your pain.  I have a system that is rock-solid with 7.04. I use it as a personal web server, so it never gets shut off. I get months of uninterrupted uptime. 
I swapped out the hard drive, installed 8.04 and it freezes within minutes of booting. I can move the mouse, but the desktop is not responsive. CTRL-ALT-Backspace and CTRL-ALT-DEL do nothing. 
There doesn't seem to be any pattern behind the freeze.  It will happen when I'm browsing with Firefox, when I'm reading the logs trying to figure out the previous crash or just sitting there doing nothing.  
I tested and swapped out the RAM so that's not the problem.  Tested the hard  drive and it appears to be fine.

Gigabyte 7ZXE Mobo
AMD Athlon XP 2000+
1024 Mb RAM
ATI Radeon 8500 
250 Gb WD HD
DVD-ROM and DVD-RW


this is the same problem i been having. Here in the forums someone told me to use ctrl alt backspace and it work at least so i dotn have to hard reboot but anything else doesnt work. Just the mouse cursor

---

### Post by Mighty_Joe on 2008-07-01
> **External said:**
> 
I do hope you/we get some response for the bug, as well as sergio callegari's post, who pretty much seems to have summed up what is known so far and I'm really curious about what a developer thinks about his points.

I'm not holding my breath.  Since the [original bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996") has been marked "fixed in Intrepid", my bug is still marked "new" and Intrepid apparently fixes the issue, my bug will probably be swept under the rug before a developer addresses Sergio's comments.  
I'll do some more testing with Intrepid just to make sure, then go back to 7.04 until October.

---

### Post by carl_pr on 2008-07-01
so i guess i installed a buggy OS, ooo great. People options is uninstalling, downgrade to ubuntu 7 or other distros.

---

### Post by Mighty_Joe on 2008-07-01
> **carl_pr said:**
> so i guess i installed a buggy OS, ooo great. People options is uninstalling, downgrade to ubuntu 7 or other distros.

If ctrl-alt-backspace worked for you, you do not have the same problem I have.  ctrl-alt-backspace restarts XWindows, so your system was stable, it was just XWindows that took a dump. 
I suggest you do some research in the forum and [launchpad ]("https://bugs.launchpad.net/")and try to identify your problem before you start talking about a remedy.

---

### Post by Brando569 on 2008-07-01
im glad to see that it isnt my pc thats screwing up or maybe it was. when i first installed hardy it would freeze instantly, i flashed the firmware on my dvd drive and then it seemed to install fine. my freezes woulnt happen instantly usually after 16+ hours of being up. 

I experience two types of freezes: most of them are soft freezes where all i have to do is ctrl+alt+backspace and im good to go. it seems that with these freezes its only graphical because if i have audio playing i can still hear it but nothing moves.the other freezes, which happen less often, are hard freezes where the only thing i can do is press the reset button.

im using a custom compiled 2.6.25-9 kernel and my pc has been up for 14 hours and 22 minutes with no problems, although i still have insane memory usage. out of my 2,015mb i only have 90mb free and thats with barely anything open! firefox 3 is taking up 133mb and superkaramba is taking up maybe 75mb but the rest are all programs/processes that were installed by default!

---

### Post by Mighty_Joe on 2008-07-01
> **Brando569 said:**
> although i still have insane memory usage. out of my 2,015mb i only have 90mb free and thats with barely anything open! 

Be aware that Linux considers [unused memory useless memory]("http://gentoo-wiki.com/FAQ_Linux_Memory_Management"), so memory usage will always seem maxed out.

---

### Post by dentaku65 on 2008-07-01
Maybe is very well known, but you can use the combination keys (if works) to do a soft reboot instead of hard reboot when freeze occurs, so press:
ALT+R.Syst(Stamp)
then with the above keys pressed, type:
R E I S U B

The system should do a soft restart (in my case when I was affected by freeze situation the X server not always want to quit with "reisub" instruction)

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by External on 2008-07-01
> **dentaku65 said:**
> Maybe is very well known, but you can use the combination keys (if works) to do a soft reboot instead of hard reboot when freeze occurs, so press:
ALT+R.Syst(Stamp)
then with the above keys pressed, type:
R E I S U B 


I suggested the same a few posts back at the top of this page. Probably the best way to preserve your hard drive and avoid hard resets if all else fails..

---

### Post by External on 2008-07-01
> **Mighty_Joe said:**
> I'm not holding my breath.  Since the [original bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996") has been marked "fixed in Intrepid", my bug is still marked "new" and Intrepid apparently fixes the issue, my bug will probably be swept under the rug before a developer addresses Sergio's comments.  
I'll do some more testing with Intrepid just to make sure, then go back to 7.04 until October.

Hmm.. Can they just let this go and not address the issue in an LTS release? I mean if it were a usual short-term one it might go unaddressed without turning too many people away from Ubuntu, but I'm afraid it would be a very bad strategy to force people to either use 7.10, that is past or 8.10, which is still future and let the problem go unsolved. Do you happen to know about the policy forbidding the "official" upgrade to kernel version 2.6.25 in Hardy Sergio mentioned?

---

### Post by Mighty_Joe on 2008-07-01
> **External said:**
>  Do you happen to know about the policy forbidding the "official" upgrade to kernel version 2.6.25 in Hardy Sergio mentioned?

His post was the first I'd heard about it, but I don't follow the development of Ubuntu closely.  I'm just a "user".
My wild-assed guess would be that the Ubuntu kernel patches are non-trivial to develop, and changing the kernel version would be disruptive to the rest of the code base that depends on the kernel having a particular feature set.

---

### Post by External on 2008-07-02
Damn...this sucks. Thanks though.
I'm just wondering how many people I managed to convince to use Ubuntu - I just hope none of them runs into the problem we're having.

---

### Post by External on 2008-07-02
By the way is there any special reason for you going back to Gutsy and not sticking with Intrepid? Is it still too..."developmental"?:) I'll most probably give it a shot on the weekend or before but I'm not sure if it would be wiser not to experiment and install good old Gutsy instead.

---

### Post by Gatemaze on 2008-07-02
> **External said:**
> Hi Joe,

I do hope you/we get some response for the bug, as well as sergio callegari's post, who pretty much seems to have summed up what is known so far


Can you provide a link to Sergio's post please?

---

### Post by doubtintom on 2008-07-02
I found a solution that's been working for me for 22 hours or so. It involves compiling yourself a 2.6.25 kernel.

See [http://ubuntuforums.org/showpost.php?p=5306136&postcount=679]("http://ubuntuforums.org/showpost.php?p=5306136&postcount=679")

Tom

---

### Post by Mighty_Joe on 2008-07-02
> **External said:**
> By the way is there any special reason for you going back to Gutsy and not sticking with Intrepid? Is it still too..."developmental"?:) 

Gutsy?  Shoot.  I'm still using Feisty!
Apparently with Ibex, you won't get [security updates]("http://ubuntuforums.org/showpost.php?p=5298616&postcount=671") (I don't know if that's good info, just passing it along).  
As for Intrepid, I finally got gnome-desktop installed and tried using it for a few hours.  It's more stable for me than Hardy but I still get the occasional lockup. It seems to be related to certain web sites.  Yahoo Mail in particular locks my computer after a minute or two.  I avoid that site and Intrepid seems fine.

---

### Post by Mighty_Joe on 2008-07-02
> **Gatemaze said:**
> Can you provide a link to Sergio's post please?

External is referring to Sergio's post [here]("https://bugs.launchpad.net/ubuntu/+bug/227882/comments/9")

---

### Post by kevdog on 2008-07-02
Ahh --- so the lockup issue is still not solved -- telling me going to certain websites causes the system to lockup = bug not fixed!

---

### Post by External on 2008-07-02
Thanks Joe for linking the post.

Since Sergio's post pretty much sums up what this thread is about and what can be known at this point and since others might be interested as well, I hereby copy it here.
The link to Mighty_Joe's bugreport on launchpad (including the following post): [https://bugs.launchpad.net/ubuntu/+bug/227882](https://bugs.launchpad.net/ubuntu/+bug/227882)


 > **sergio.callegari wrote on 2008-06-27**: (permalink)

In the end I resorted to experiment myself with vanilla 2.6.25.9.

Spent a night compiling it and the nvidia stuff.

It works without any problems and it is stable.

Hence:

- either 2.6.24 was a very poor choice for Hardy because the upstream 2.6.24 is the cause of the random hard lockups;
- or the upstream 2.6.24 is fine and the ubuntu patches break it.

In either case I believe that this situation is getting weird:

1) Everybody at this point knows that the hardy kernels cause random freezes to many users;
2) Everybody knows that these freezes are subtle as they may happen every few hours, so after having set up a system it is impossible to say for sure whether it is affected by the bug or not without many hours of testing
3) Everybody is just avoiding upgrades from gutsy to hardy just because of that. Note that even if the risk of being hit by the bug is low (say 1%) there is a multiplicative effect here - 50% of potential users will stay away from hardy just because of the risk, just as in insurances where if some accident statistically hits 1% of population, more than 50% decides to make an insurance.
4) The solution of the problem is known since vanilla 2.6.25 fixes the bug.
5) But Ubuntu in 2 months (33% of the release cycle time of hardy itself) has deliberately released no fix since
- it is forbidden by the policy to release 2.6.25 for hardy
- no one seems to know how to patch 2.6.24 to make it behave correctly like 2.6.25

So the policy seems to work very very bad here: backporting the fix to 2.6.24 seems much much more troublesome than releasing a 2.6.25.
Looks like the sense of "long term support" is that the policy will enable support to arrive only in the long term.

The only solution to this apparent deadlock is that some Ubuntu kernel developer feels like to autonomously deliver a 2.6.25 with ubuntu modules and restricted drivers via the ppa channel, so we can bypass the policy and have a fixed and reasonably maintained kernel for hardy. 

---

### Post by External on 2008-07-02
> **Mighty_Joe said:**
> Gutsy?  Shoot.  I'm still using Feisty!

:) So there's still gonna be a version update after all.
 
> As for Intrepid, I finally got gnome-desktop installed and tried using it for a few hours.  It's more stable for me than Hardy but I still get the occasional lockup. It seems to be related to certain web sites.  Yahoo Mail in particular locks my computer after a minute or two.  I avoid that site and Intrepid seems fine.

Yeah, that's not good news, does it mean that there are still interferences even with the 2.6.25 kernel and the Ubuntu patches? Experimenting with Intrepid is out of the question for me then... Thank you for reporting.

---

### Post by Gatemaze on 2008-07-02
> 
- it is forbidden by the policy to release 2.6.25 for hardy
- no one seems to know how to patch 2.6.24 to make it behave correctly like 2.6.25

Hmmm, that's a bit worrying... I hope there will be a stable and reliable 2.6.24.x kernel which will bring back confidence to Ubuntu Heron as it is a LTS release, an important feature for the choice of some people (including myself) in choosing a distro.

---

### Post by External on 2008-07-02
Yep, very true. From the "hardcore" Linux developer's point of view it does not matter how many people use Linux and that I totally understand. However, as far as I know it IS Canonical's aim to popularize and "promote" (obviously not in the "financial" sense of the word) Ubuntu as a stable, reliable alternative. It IS Mark Shuttleworth's concern to encourage people to use Linux as a free, great OS. And as such, unfortunately, this bug is a true blow on Ubuntu, and a layman as myself would wonder whether policy could be overruled for strategic considerations in cases like this.

So apparently at this point all a Hardy user (affected by the bug) can do is

 1. Revert to Gutsy.
 2. Backport kernel 2.6.25 to Hardy (probably not for noobs, but if one is interested there is the Autokernel, I'm not sure if it's still developed though: [http://ubuntuforums.org/showthread.php?p=1293943](http://ubuntuforums.org/showthread.php?p=1293943), or the way **doubtintom** suggested a few posts back: [http://ubuntuforums.org/showpost.php?p=5306176&postcount=205](http://ubuntuforums.org/showpost.php?p=5306176&postcount=205))
 3. Use kernel 2.6.22 (Gutsy's version) in Hardy [is probably worth a try]
 4. Run forward to Intrepid (PROVIDED that it does not contain the bug, which it does seem to contain acc. to Mighty_Joe's experiences)
 5. Wait (and develop a nervous breakdown BUT get pretty strong by "Raising Skinny Elephants" all the time)
 6. Choose another distro (and leave this wonderful community)

Take your vote. (Or else it gets taken automatically as no.5.)

------------------------------------------------------------------

In case anyone is interested in **Ubuntu's kernel backporting policy**, I found this **informal** thread: [http://ubuntuforums.org/showthread.php?t=294066](http://ubuntuforums.org/showthread.php?t=294066)

The essence of the thread is this:

> 
[posted by **jdong (admin)**]
There is nothing preventing a bugfix or a newer driver from being backported to the existing kernel version.

Newer kernels add their own bugs, not to mention compatibility problems. It takes 3rd party driver vendors quite some time to catch up to the latest version of the kernel. On a system with these types of drivers, you'd be
(1) ticked that they require a recompile after updating the kernel
(2) MUCH MORE ticked that they no longer compile after updating the kernel, and you need to google for patches, if there is one yet!

This kind of thing happens quite frequently on distributions that update their kernel versions, such as Fedora or Gentoo (though Gentoo users install their 3rd party drivers through the Portage system and are much more prepared to deal with such issues as they arise)

-------------------------------
[Thanks **Gatemaze** for thanking me!:)]

---

### Post by csddavies on 2008-07-02
sudo /etc/init.d/gdm stop

Fixed my problem.  I probably shouldn't be running the gui anyway on my server, so it's not a big deal to turn it off.  Been running for days without a freeze.  Before this I was freezing every 8 or so hours.

---

### Post by kevdog on 2008-07-03
I'm not sure if 2.6.25 is the answer?  Isn't this the version contained in Ibex and its still locking up?

---

### Post by External on 2008-07-03
We don't have a statistically significant amount of feedbacks I suppose, only 2: according to one Intrepid (using 2.6.25) locks up, but it might not be the kernel itself, since another report says that backporting 2.6.25 to Hardy works without problems and is stable. See the post quoted here: [http://ubuntuforums.org/showpost.php?p=5306610&postcount=209](http://ubuntuforums.org/showpost.php?p=5306610&postcount=209)

---

### Post by kevdog on 2008-07-03
Ive read that, but it didnt really tell one how to backport the 2.6.25 kernel to Hardy

---

### Post by External on 2008-07-03
Have you read **doubtintom**'s method I referred to in post #212?

---

### Post by Mighty_Joe on 2008-07-03
> **kevdog said:**
> Ahh --- so the lockup issue is still not solved -- telling me going to certain websites causes the system to lockup = bug not fixed!

I think my lockups in Intrepid are a different problem.  
Hardy hangs up within [ten minutes of booting]("https://bugs.launchpad.net/ubuntu/+bug/227882") no matter what I'm doing.  Including doing nothing.
Intrepid runs fine unless I hit certain web sites. If I avoid those web sites, no lockup. This makes me think it's a firefox/plugin/network problem.
Just so we're all on the same sheet of music, the kernel in Intrepid is 2.6.26.  They changed the version about a month ago.  [These instructions]("http://ubuntuforums.org/showpost.php?p=5047838&postcount=119") were gleaned from [this earlier bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996/comments/192").  I used them to put the 2.6.25 kernel in Hardy.  I don't know if they still work.

---

### Post by Redsandro on 2008-07-03
> **Seks said:**
> The causes seem to vary by person(but often includes a wireless card), but I have only had one crash since I started using opera instead of a Gecko based browser(Firefox,Epiphany,Flock), and then I had a whole bunch of tabs open. It might be a RAM usage issue.

Whenever I start Opera 9.5 on Xubuntu 8.04 on a PIII 800MHz + Geforce2 MX200 with no tabs open, I don't even get the chance to open tabs and waste memory. Just bang, screen freezes.

I can still move the mouse, but all other graphics on screen freeze. No alt+tabbing, no ctrl+alt+TTY, nothing.

Firefox works fine but I hate that browser.

---

### Post by jamesdcarroll on 2008-07-03
When I started my machine today there were a bunch of updates and I'm hoping that they will fix the freeze problem. My system says that its 'up to date', but is there someplace that I can see more detail to verify?

Crossing my fingers...


Thanks,

---

### Post by External on 2008-07-03
What exactly would you like to verify? That your system is up-to-date? I'm afraid you'll have to believe the Update Manager if it says so.
But unfortunately whatever today's updates fixed they didn't provide remedy for our bug. My machine froze right before I managed to write this post...

---

### Post by External on 2008-07-03
> **Mighty_Joe said:**
> 
Intrepid runs fine unless I hit certain web sites. If I avoid those web sites, no lockup. This makes me think it's a firefox/plugin/network problem.

Can a FFox/plugin problem lockup a computer so you cannot use Ctrl+Alt+BackSpace? Or can you restart that way when experiencing freezes visiting those sites?

> Just so we're all on the same sheet of music, the kernel in Intrepid is 2.6.26.  They changed the version about a month ago.  [These instructions]("http://ubuntuforums.org/showpost.php?p=5047838&postcount=119") were gleaned from [this earlier bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996/comments/192").  I used them to put the 2.6.25 kernel in Hardy.  I don't know if they still work.

So it is the new Intrepid kernel you tried. Any lockups with the 2.6.25 backported to Hardy?

---

### Post by jamesdcarroll on 2008-07-03
> **External said:**
> What exactly would you like to verify? That your system is up-to-date? I'm afraid you'll have to believe the Update Manager if it says so.
But unfortunately whatever today's updates fixed they didn't provide remedy for our bug. My machine froze right before I managed to write this post...

Well, I've followed this thread pretty closely and done the best I can to follow what's going on. There were 42 (I think) updates that they said were needed and I guess I made a mistake in updating too quickly. Now that I seem to be better (though I've had one hard freeze, including the mouse; before the mouse would move) I was hoping to go back and spend more time reading the descriptions of the updates and what they were fixing.

---

### Post by csddavies on 2008-07-04
Tried 2.6.25.  Worked for about 12 hours.  My screen says 5:04AM.  Mouse frozen.  Raising Skinny Elephants trick doesn't do anything.  Have to hit reset button on computer.  I wish they'd get this fixed.  It makes it unusable as a server.

---

### Post by kevdog on 2008-07-04
So I think we can safely say that the 2.6.25 kernel **[SIZE="4"]does not[/SIZE]** resolve the lockup issue ---  I guess its going to be gutsy for a while.

---

### Post by External on 2008-07-04
> **csddavies said:**
> Tried 2.6.25.  Worked for about 12 hours.

You mean you backported it to Hardy?

---

### Post by Redsandro on 2008-07-04
Sorry - freezes do occur randomly. Not only with the Opera 9.5 browser, but starting that browser definitely make the freeze come sooner.

Here's something interesting: When the freeze occurs, I can still login using ssh on a remote computer! Can someone verify?

---

### Post by levis lover on 2008-07-04
having the same problem..
only mouse works and nothing else..
what should we do now?
go back to Gutsy or anybody wants to suggest another distro ?

i am thinking of moving to mandriva 2007

---

### Post by External on 2008-07-04
***What are you guys having lockups with?*** Hardy or Intrepid or Hardy with 2.6.25??

If you want to try another distro I heard quite good things about Fedora 9. It's said to be stable, reliable and setting wifi is a breeze as I heard, which used to be its most trivial hardship.

---

### Post by jamesdcarroll on 2008-07-04
I'm probably jinxing myself, but I've been stable since the updates came out yesterday.  I'm gonna keep my fingers crossed....

---

### Post by Tallo on 2008-07-05
Same problem here on my Acer Aspire 9302 laptop. 8.04 freezes up randomly, at different times running different applications. SysRq key commands won't respond. Only a hard reboot works.

I've tried 2.6.25.9 and a 2.6.26 build, disabling powernowd, disabling wireless drivers and switching to wired and moving from the 32-bit to the 64-bit release.

I've gone back to 7.04 for now (7.10 freezes at boot time for me)...

AMD Turion 64 MK-38, nVidia GeForce Go 6100, Broadcom wireless card.

---

### Post by External on 2008-07-05
> **kevdog said:**
> So I think we can safely say that the 2.6.25 kernel does not resolve the lockup issue ---  I guess its going to be gutsy for a while.

It's probably going to be Gutsy for a while but no, I'm afraid we can NOT **safely** say that 2.6.25 doesn't resolve the issue - we lack sufficient feedback and many recent posters are either reporting what has been known from the 1st page of this thread or they are reporting the failure of 2.6.25 in Hardy, we do not know.

Still, I have read other posts of people elsewhere who used 2.6.25.9 from kernel.org and it eliminated the problem. (e.g. [http://lwn.net/Articles/287840/](http://lwn.net/Articles/287840/)) And even if people are STILL experiencing freezes, it might be attributed to tons of things, unless we have **significant** number of feedbacks.

---

### Post by External on 2008-07-05
> **Tallo said:**
> I've tried 2.6.25.9 and a 2.6.26 build, disabling powernowd, disabling wireless drivers and switching to wired and moving from the 32-bit to the 64-bit release.

Does it mean you first backported 2.6.25.9 to Hardy, then did the same with 2.6.26 and still you get freezes?

---

### Post by Tallo on 2008-07-05
> **External said:**
> Does it mean you first backported 2.6.25.9 to Hardy, then did the same with 2.6.26 and still you get freezes?

I tried 2.6.25.9 in Hardy, with a little help from AutoKernel. It ran fine, until it randomly froze while I was busy downloading something through the Update Manager. I tried 2.6.26 in 8.10 alpha 1.

---

### Post by External on 2008-07-05
Were any other programs running when you experienced the lockup, like FFox, Ooo, or whatever? Did you go on testing 2.6.25.9 after the first freeze occured?

Anyhow, it's not good news...

---

### Post by jonah1980 on 2008-07-05
i'm sick of this and this is why i used fedora for a year or so. i thought now coming back to ubuntu it would be fixed by now. i've had this problem since edgy,feisty used to lock up and now hardy too.

my system is pretty normal, nvidia, amd64, winfast motherboard, 4gb ram.

i used to post about this frustration a lot and then got fed up and went onto fedora 8, now i'm tempted at fedora sulphur 9 now seen it's still happening with heron.

i can use the system for hours before it freezes or ten minutes, it's dead random. people used to blame nvidia, then amd64, now seems wireless is being questioned...

i always thought linux was supposed to be more stable...

---

### Post by brethren on 2008-07-06
> **External said:**
> ***What are you guys having lockups with?*** Hardy or Intrepid or Hardy with 2.6.25??

If you want to try another distro I heard quite good things about Fedora 9. It's said to be stable, reliable and setting wifi is a breeze as I heard, which used to be its most trivial hardship.

well i downloaded hardy on release day and straight away it was freezing...it was so bad that i couldn't get any work done. so i decided to try different distros

mandriva - buggy, kept filling my home folder with random garbage files
opensuse - a pain to set up my wifi...needs some sort of firmware
fedora 9 - perfect:) never freezes and wifi is as easy to set up as it is in ubuntu

i recommend anybody who is having freezing problems to try fedora 9 as it's quite obvious after all these months that the freezing bug isn't going away!

---

### Post by tizo_rh on 2008-07-07
So, jamesdcarroll, did the freeze problem go away?

I have no freeze problems in my Hardy Heron. However, I am installing a new (old pentium III 1 GHz) machine, having a wireless PCI card with rtl8185 chip. This chip, does not work out of the box in Hardy. I have tried a lot of things: compiling different drivers, using ndiswrapper, etc. I have success using the card with some of those tests, but when it works, the freeze issue appear.

So, in my case, I am sure is related to wireless. I will try Fedora 9, and Ubuntu Intrepid Ibex (8.10, alpha release), to see which is the behavior. I could try another things, as use another kernel, but I need the PC to be easy to update, as is not for me. Maybe I'll try with another wireless card too. I'll post my results here.

---

### Post by Mighty_Joe on 2008-07-07
> **External said:**
> Can a FFox/plugin problem lockup a computer so you cannot use Ctrl+Alt+BackSpace? Or can you restart that way when experiencing freezes visiting those sites?

It's just wild speculation on my part.  It certainly doesn't fit the symptoms of the original bug report. And no, Ctrl+Alt+BackSpace doesn't work with the FF freeze on Intrepid in my case. 

> **External said:**
> 
So it is the new Intrepid kernel you tried. Any lockups with the 2.6.25 backported to Hardy?

When I was testing Hardy with 2.6.25, I considered uptime past 10 minutes a win. I didn't try to get hours of use out of it like I'm trying with Intrepid.

---

### Post by Mighty_Joe on 2008-07-07
> **External said:**
> If you want to try another distro I heard quite good things about Fedora 9. 

One caveat about Fedora is that they take a strict approach to ["free software"]("http://www.gnu.org/philosophy/free-sw.html") so getting software that requires a license or EULA (MP3's, DVD's, Windows media, Java) to work in Fedora will take extra effort on your part.
One of the nice things about Ubuntu is they do the grunt work for you in that area.

---

### Post by External on 2008-07-07
> **brethren said:**
> [...] so i decided to try different distros

mandriva - buggy, kept filling my home folder with random garbage files
opensuse - a pain to set up my wifi...needs some sort of firmware
fedora 9 - perfect:) never freezes and wifi is as easy to set up as it is in ubuntu


We all thank you for the info; I've been considering distros other than Fedora (and unfortunately Ubuntu), but this I guess will save a lot of time.


> **Mighty_Joe said:**
> One caveat about Fedora is that they take a strict approach to ["free software"]("http://www.gnu.org/philosophy/free-sw.html") so getting software that requires a license or EULA (MP3's, DVD's, Windows media, Java) to work in Fedora will take extra effort on your part.
One of the nice things about Ubuntu is they do the grunt work for you in that area.

Umm...I thought Fedora was less concerned with exclusively incorporating FOSS stuff, given that Skype, for instance, can be installed directly from the Fedora 9 install DVD to my best knowledge. One of the reasons I have avoided trying Fedora was precisely its "accepting" policy towards proprietary, though free software. Was I wrong?
Also, given the fact that you can't even play an mp3 or a dvd directly after installing Ubuntu suggests to me that it employs just the same (or a more restrictive) policy as regards closed source software.

As regards new kernels tried with Hardy - this is all the more worrying, and as such, I already have 2 live Fedora CD images waiting for me on my hard disk...

---

### Post by Mighty_Joe on 2008-07-07
> **External said:**
> One of the reasons I have avoided trying Fedora was precisely its "accepting" policy towards proprietary, though free software. Was I wrong?


I only know what I read in [the FAQ's]("http://fedoraproject.org/wiki/FAQ#Why_doesn.27t_Fedora_include_support_for_proprietary_formats_like_MP3_or_MPEG.3F").  There are, of course, workarounds available.  
Ubuntu [makes it easier]("https://help.ubuntu.com/community/RestrictedFormats") on the end user.  Whenever I have tried to play an MP3 on a fresh install, there's just a click-through to install the codec.
Maybe you are thinking of the closed-source code Red Hat contributed to Fedora, like [Anaconda]("http://fedoraproject.org/wiki/Anaconda"), the installer?  That appears to open source now.  I don't know if there's anything else in Fedora that's still Red Hat's protected property.

---

### Post by External on 2008-07-07
> **Mighty_Joe said:**
> I only know what I read in [the FAQ's]("http://fedoraproject.org/wiki/FAQ#Why_doesn.27t_Fedora_include_support_for_proprietary_formats_like_MP3_or_MPEG.3F").  There are, of course, workarounds available.  
Ubuntu [makes it easier]("https://help.ubuntu.com/community/RestrictedFormats") on the end user. 

After some preliminary research this seems to be true: the Fedora FAQ is a bit like a politician's monologue: it says the same things over and over again (1 followed 3 links to no avail) and does everything but pointing you to the right direction. What's worse is Fedora doesn't seem to offer full ATI 3D card support, and neither does ATI provide a driver for Fedora.
Damn this Ubuntu bug...:(

---

### Post by brethren on 2008-07-08
yeah fedora 9 doesn't support the proprietary ati driver (though there is a workaround, cehck fedoraforums) as for being hard to set up mp3, de-css etc well it's not that difficult. its just a matter of adding an extra repository (livna) which includes all the stuff that isn't o.s.i. friendly.

anyway for anybody who wants to try fedora this guide will really help:)
[http://www.my-guides.net/en/content/view/103/26/](http://www.my-guides.net/en/content/view/103/26/)

---

### Post by offchance on 2008-07-08
> **Mighty_Joe said:**
> I feel your pain.  I have a system that is rock-solid with 7.04. I use it as a personal web server, so it never gets shut off. I get months of uninterrupted uptime. 
I swapped out the hard drive, installed 8.04 and it freezes within minutes of booting. I can move the mouse, but the desktop is not responsive. CTRL-ALT-Backspace and CTRL-ALT-DEL do nothing. 

same here, with amd64/broadcom. when I use wireless it will usually freeze in this way after a few hours. I'm using gutsy and I'm nervous about upgrading to hardy since, as you said, there was no problem whatsoever in feisty.

---

### Post by francesco44 on 2008-07-08
I do not know why but the "freeze" problem I experienced many times some days ago seems know to be fixed. Maybe with the latest patches....I am happy because I love Hardy:

If I experience the freeze problem again i will write it on this thread. I Hardy is stable,,,I will also signal it.

With a prudent thanks and Viva and Hurrah for Feisty:)

Francesco44

---

### Post by smuggler on 2008-07-08
Just installed 2.6.25 kernel on Hardy, but it didn't help. System is still freezing randomly. 
I thought it's an nvidia problem, because I've never seen freezes with nv driver before, but for the first time after booting with new kernel it froze with nv. Damn.

Using Nvidia Go 6100. Going to read logs once more.

---

### Post by GeneM on 2008-07-08
Well I had the freezing problem for a while and the then some updates seemed to fix it.  But that only lasted for about 10 days or so and then back to freezing, sometimes as ofter as every half hour.  Finally I got desperate and started trying lots of things.  The one that finally worked for me was to turn "acpi" off in the kernel.  I did this by editing the menu.lst file.  So, in a terminal change to the grub directory

```
cd  /boot/grub
```make a backup of the file you are going to change

```
sudo cp menu.lst menu.lst.original
```and then edit the file

```
sudo  gedit  menu.lst
```Find the first line that looks something like this( this is my setup and yours will not be exactly like it )

```
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=9388eda3-4707-4943-80c7-c57a25467d5c ro splash acpi=off
```and add the "acpi=off" like in the line above.  If you are not sure which kernel is booting, add the "acpi=off" to the end of every line that starts with the word "kernel".    Save the file and reboot.  If you see the grub menu make sure the line with the acpi=off is highlighted(up and down arrow keys) and then hit the b key to boot.  If you are able to run without any freezes you need to make this change permanent.  As it is the changed menu.lst may not survive some upgrades.

```
cd /boot/grub
sudo gedit menu.lst
```Now find the section that looks something like this
```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash acpi=off

```and add the "acpi=off" to end of the "# defoptions= " line like I have done above.  Again you line may have other stuff, leave it there, just add the "acpi=off" to the end of the line if it is not already there.    [SIZE=3][COLOR=Red]**DO NOT**[/COLOR][/SIZE] remove any of the # signs in the file.  If you want to add comments of your own to the file, make sure you start the line with **[SIZE=3][COLOR=Red]TWO[/COLOR][/SIZE]** of the # signs.

Good luck,
Gene

---

### Post by smuggler on 2008-07-09
Frozen again with nv and 2.6.25, and there's just nothing in logs to track this problem. Gonna try GeneM's method, or I guess it will be 7.04 for a while :\

---

### Post by smuggler on 2008-07-09
Yay, looks like it helped under 2.6.25 with nv driver. Gonna test it with 2.6.24 though.

---

### Post by dahias on 2008-07-09
the problem is firefox 3. (likely)

i also was suffering from this problem and couldnt find anything in the logs. i had the feeling that it has something to do with firefox 3. 
for more then two weeks now i've been using firefox 2 and epiphany (without uninstalling ff3) and there was no single freeze  all the time ! 
i don't think its a nvidia thing because i use a intel gma945 with open source drivers. 

today i started again to use ff3 - if the freezes return i will post them to you.

---

### Post by smuggler on 2008-07-09
It's not a firefox (well, probably for some people it is, but not for me).
Turning acpi support off helped (just tested it with 2.6.24 kernel and nvidia driver), but I'm using laptop, and without it I can't monitor my battery status.

---

### Post by smuggler on 2008-07-09
This would be usefull: [https://help.ubuntu.com/community/DebuggingIRQProblems](https://help.ubuntu.com/community/DebuggingIRQProblems)

---

### Post by Mighty_Joe on 2008-07-09
> **dahias said:**
> the problem is firefox 3. (likely)


You would do well to read this thread and the bugs it references.  It is nearly certain that the bug we are talking about is a 2.4.24 kernel bug.  There are problems with Firefox 3, but as far as I know, they have solutions posted elsewhere in this forum.

---

### Post by kevdog on 2008-07-09
Its not strictly a FF3 problem.  I thought this to be the case and downgraded to FF2.  The machine still randomly freezes.  Its also not strictly a wireless card issue, since my machine has frozen without its wireless device even connected.  Others have claimed a video card issue -- however from my own experience (built in Intel graphics) it can't be just an ATI/NVIDIA issue.  Its hard to know if its just one kernel error, or compilation of a bunch of small errors, each different given different hardware at hand.

---

### Post by smuggler on 2008-07-09
Turned off acpi.
Running kernel 2.6.25, nvidia drivers, Firefox 3 and glx without any freezes for two hours already.
2.6.25 freezes with both nv and nvidia drivers when I'm using acpi. Same for 2.6.24 kernel.

So in my case it's an acpi problem, I guess. Tried using other options from [https://help.ubuntu.com/community/DebuggingIRQProblems](https://help.ubuntu.com/community/DebuggingIRQProblems), but only turning off whole acpi support helps.
Going to try 7.10 or 8.10 perhaps...

---

### Post by External on 2008-07-09
Um...Am I right to assume that by turning off acpi, one loses the chance to use their wireless? I'm using an Acer laptop and I can't use wireless unless I install "acer acpi" that is supposed to turn on the device - an obvious prerequisite to utilizing a wireless driver.


> **Mighty_Joe said:**
> You would do well to read this thread and the bugs it references.  It is nearly certain that the bug we are talking about is a 2.4.24 kernel bug.

We're going in rounds, perhaps a sticky would be a good idea to sum up what is thought to be true based on the posts and the quoted links...? (Yeah, I know probably it would be better if developers summed up what is ***known*** to be true instead of us trying to summarize what we *suppose* to be true..)

---

### Post by Mighty_Joe on 2008-07-10
> **External said:**
> 
We're going in rounds, perhaps a sticky would be a good idea to sum up what is thought to be true based on the posts and the quoted links...? 

Yea.  This topic is beginning to resemble the [LOCKUP WARNING]("http://ubuntuforums.org/showthread.php?t=768200") thread and the [infamous Bug 204996]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996").
What would be ideal is a wizard that would point people to the most likely culprit and threads/bugs discussing it.  For example, I don't have NVIDIA or wireless, so that rules out those two possibilities.  I wonder if the [ubuntu wiki]("https://wiki.ubuntu.com/") could be employed for such a thing.
BTW, expect [Intrepid Ibex Alpha 2]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-July/000445.html") today.  It will include a live cd which will simplify testing (for my purposes, anyway).  It will appear [here]("http://www.ubuntu.com/testing") when released.

---

### Post by smuggler on 2008-07-11
Turning PowerNow function through BIOS helped, no more freezes.

---

### Post by External on 2008-07-11
> **Mighty_Joe said:**
> 
I wonder if the [ubuntu wiki]("https://wiki.ubuntu.com/") could be employed for such a thing.

Good idea, I'd be willing to contribute if I weren't a noob, but I guess an expert could have better ideas of what might cause the problem and could offer possible workarounds. Also, by devoting some attention to it at the wiki pages of Hardy, the bug would be at least more "acknowledged" in the sense that it wouldn't be swept away with "fix released", technically meaning that it "might not be present in Intrepid".

> BTW, expect Intrepid Ibex Alpha 2 today. It will include a live cd which will simplify testing (for my purposes, anyway).

I was just wondering whether anyone has tested Hardy 1.1. Does it still contain the bug? Otherwise thanks for the info, if all else fails I will test Intrepid Alpha 2. (Especially since the Fedora 9 Live CD froze upon me 3 times in a row yesterday. Is it the stars I was born under..?)

---

### Post by knightmuzic on 2008-07-11
I'm glad I'm not the only one who's having problems.

My upgrade to 8.04 results in it freezing **right at the login screen**. And yes, I use an nVidia card (the machine itself is a Compaq Presario 6000 with AMD Athlon). 

Is there any way to downgrade using a live CD (of the earlier Ubuntu versions I have) until this is resolved? Or hopefully, a new live CD with the fixed version of 8.04 is released soon?

Yeah, I'm still rather noob-ish, even though I've gone through at least two upgrades. I haven't a damn clue how to tweak my BIOS, or whatever. But the previous Ubuntu versions I've used worked like a dream. Gutsy was great. Hardy? Not so much, if this is any indication of the future.

---

### Post by oxman on 2008-07-12
Just for the record:

Hardy Heron

Asus motherboard with nvidia bridge
AMD 64 Dual Core Opteron 175
Nvidia 7900GTO
Audigy 2 Soundblaster

 Consistently LOCKS UP HARD randomly on various desktop functions and nautilus window manipulations. Ctrl, Alt +backspace does not escape.  F1-no escape. Mouse continues to function but screen is unresponsive to mouse selections. Power down hard and reboot is the only escape. 

No sound available.

---

### Post by landeel on 2008-07-12
@knightmuzic:

V6000's and DV6000's have a BIOS bug that freeze the kernel. I know because I have one.

You should use this kernel parameters to boot:
noapic irqpoll noirqdebug

If it doesn't work, try booting with the kernel from the previous version. The 2.6.24 kernel makes my V6000 freeze anyway, so I had to downgrade to 2.6.22 .

---

### Post by External on 2008-07-12
> **knightmuzic said:**
> Is there any way to downgrade using a live CD (of the earlier Ubuntu versions I have) until this is resolved? Or hopefully, a new live CD with the fixed version of 8.04 is released soon?


You can "downgrade" by reinstalling Gutsy, if you still have the CD, or else you can easily download it from the Ubuntu archives. I "usually" so it by repartitioning my hard drive using the Gparted partitioner integrated with the Live CD (that is, I delete the former Ubuntu partitions, incl. the swap part., then I restart the partitioner and do pretty much everything the automated way.) You might find it easier to do the whole thing if you don't dual boot as I do. If you need more help, just ask.

> **oxman said:**
> No sound available.

Same here, but sound only disappeared after a few days/weeks.

> **landeel said:**
> If it doesn't work, try booting with the kernel from the previous version. The 2.6.24 kernel makes my V6000 freeze anyway, so I had to downgrade to 2.6.22 .

Was just wondering, which is the easiest way to "downgrade" Hardy to kernel version 2.6.22? Do you still get updates then?

---

### Post by herdivet on 2008-07-12
[QUOTE=oxman;5370551]Just for the record:


 Consistently LOCKS UP HARD randomly on various desktop functions and nautilus window manipulations. Ctrl, Alt +backspace does not escape.  F1-no escape. Mouse continues to function but screen is unresponsive to mouse selections. Power down hard and reboot is the only escape. 


To reboot in a slightly less down-and-dirty way, you can hold <ALT> <CTL> <SYSRQ> and while holding them press R E I S U B.  When you press the B, the system will reboot.  (Some say use the mnemonic Raising Elephants Is So Utterly Boring, I just remember BUSIER backwards.)  For a discussion on what this does, and why you can check out 
[http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/](http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/)

Of course I'd rather they just fix the d&%$ lockups...

Make that keystroke sequence <ALT> <SYSRQ>  no need to complicate it even more with <CTL>...

---

### Post by Mighty_Joe on 2008-07-12
> **External said:**
> I was just wondering whether anyone has tested Hardy 1.1. 

I just gave the 8.04.1 live cd a try.  Got about 5 minutes into it before it froze.  
I tried both Fedora 9 and Intrepid Ibex as hard disk installs.  Both are stable sitting still (Hardy isn't).  Both will lock up randomly while I browse the web.  I've seen a lot of people having problems with pulseaudio and Flash.  Supposedly KDE doesn't have that problem, but Synaptic in Ibex took a crap and I booted back to 7.04.
No silver bullet, I'm afraid.

---

### Post by MedellinManDem on 2008-07-12
Mine has frozen on two occasions since yesterday.

1) After erasing a large number of files from a new partition then trying to access the deleted items folder...

2) When it just tried to change the permissions on the same said ext3 partition while trying to edit my fstab as per the following thread: [http://ubuntuforums.org/showthread.php?t=698864&highlight=figure+ext3](http://ubuntuforums.org/showthread.php?t=698864&highlight=figure+ext3)

Anyone have any idea why?

---

### Post by PadreSol on 2008-07-12
I even tried <ALT> <CTL> <SYSRQ>.  Amazingly it did nothing. I had to power off and power on. Once it came back up the <ALT> <CTL> <SYSRQ> events were logged.

Had a lockup just a little while ago.  This time no keyboard input. I was able to reboot using the mouse.

---

### Post by MedellinManDem on 2008-07-12
> **PadreSol said:**
> I even tried <ALT> <CTL> <SYSRQ>.  Amazingly it did nothing. I had to power off and power on. Once it came back up the <ALT> <CTL> <SYSRQ> events were logged.

Had a lockup just a little while ago.  This time no keyboard input. I was able to reboot using the mouse.

This Alt, Ctrl, Sysrq command...does it only work when the computer has frozen? It has no effect on either of my computers when pressed in normal time.

---

### Post by PadreSol on 2008-07-13
I urge you to do the following:

wget [http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.25.11.tar.bz2](http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.25.11.tar.bz2)
bunzip2 linux-2.6.25.11.tar.bz2
cd linux-2.6.25.11/Documentation
less sysrq.txt

Also, this to everyone, it's always a good idea to have the kernel source around to look through the docs in "your-kernel-version/Documentation"

Some of it's out-dated but much is very useful.

For example the part about echo commands to /proc/sysrq-trigger

---

### Post by knightmuzic on 2008-07-13
> **landeel said:**
> @knightmuzic:

V6000's and DV6000's have a BIOS bug that freeze the kernel. I know because I have one.

You should use this kernel parameters to boot:
noapic irqpoll noirqdebug
How exactly do I change the parameters? That's not something I've ever done before.

---

### Post by External on 2008-07-13
> **Mighty_Joe said:**
> I tried both Fedora 9 and Intrepid Ibex as hard disk installs.  Both are stable sitting still (Hardy isn't).  Both will lock up randomly while I browse the web.

Funny, that. Wish my 8.04 installation was that stable; I suspect it's a boredom thing: Hardy is more likely to freeze when left alone... You mentioned some websites that regularly cause lockups, does it also happen when you use a browser different from FFox? Anyhow, as it is I might not experiment with Fedora either...

> I've seen a lot of people having problems with pulseaudio and Flash.

Flash? First I was experimenting with Gnash in the spirit of the open source religion. Haven't been able to intentionally reproduce such lockups ever since, and that was in the Gutsy-Ages!


> No silver bullet, I'm afraid.

Well, given the coherency of this thread lacking the aforementioned sticky, even if there was, we would shoot it around, aimlessly...

---

### Post by External on 2008-07-13
> **MedellinManDem said:**
> This Alt, Ctrl, Sysrq command...does it only work when the computer has frozen? It has no effect on either of my computers when pressed in normal time.

Well, I don't suppose a series of such commands could secretly watch and know whether you're pushing those buttons because your machine froze, or just for the hell of it. In short: a command is a command is a command; it should (and mostly does) work no matter when it is given.

---

### Post by bone2006 on 2008-07-13
I'm having these problems with mythbuntu 8.04
I tried a fresh install and didn't do a single update, used the safe generic video drivers and my system still freezes.  I'm not sure if it's hardware, but after seeing all these posts I kind of wonder.

Mine always happens when I'm compiling software, I can recreate the problem each time

---

### Post by paulnn on 2008-07-14
I'm also having intermittent, infrequent system crashes. I can't see any common denominator, its been happening since I installed Hardy, but infrequently (like once every 2 days). The one difference between my crash and most of those described is that I can always kill X and logout with crtl alt <-, but as soon as i log in it just freezes. I press the power button, and with an immediate sys beep it powers down (no need to hold button).

---

### Post by trent1980 on 2008-07-15
> **rmccabe3701 said:**
> I installed hardy two days ago the freeze issue is unbearable.  My machine is a 
HP dc7700 2Gb RAM and an nvidia 5200 GeForce FX video card.  

I read on another thread that doing 
```
 sudo apt-get remove powernowd 
```

would help.  It did not.  I tried installing the nvidia driver directly from the nVidia website (not using the restricted driver manager) and this seemed to make things worse, i.e. the system would ALWAYS freeze up within 30-60 seconds of a boot.  So, I rolled back to the generic video driver and no more freezes -- however, this only supports a single monitor.  

So, the problem for me seems to be the incompatibility of Hardy with the nVidia driver (it worked in Gutsy).

Does anyone have any suggestions?

My ibm was locking up but stopped after I uninstalled powernowd that I got from this thread. It ran great for about a month but last week it started again.

Any new ideas?

---

### Post by bone2006 on 2008-07-15
My Mythbuntu 8.04 frooze on me sooo many times and I just installed it on another system for a friend and it frooze on him.  

There's a serious problem with 8.04 and crashing/freezing...........

I'm going back to 7.10 on those systems that are crashing.

---

### Post by Seks on 2008-07-15
When I first installed, it would freeze up after a minute of using firefox (non-gecko browsers like opera lasted a little longer). Big webpages contributed, and even more if they had flash.

I installed the original driver for my wireless card through ndiswrapper, and now the freezes only happen after about a day of uptime. Sometimes I can move my mouse and can CTRL+ALT+BACKSPACE or CTRL+SYSRQ+R-E-I-S-U-B out, but usually the mouse can't move and I have to hard reboot. Neither of which allow sound to continue. The first scenario is probably a compiz or nautilus issue, and happens rarely.

---

### Post by oxman on 2008-07-16
> **herdivet said:**
> 

To reboot in a slightly less down-and-dirty way, you can hold <ALT> <CTL> <SYSRQ> and while holding them press R E I S U B.  When you press the B, the system will reboot.  (Some say use the mnemonic Raising Elephants Is So Utterly Boring, I just remember BUSIER backwards.)  For a discussion on what this does, and why you can check out 
[http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/](http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/)

Of course I'd rather they just fix the d&%$ lockups...

Make that keystroke sequence <ALT> <SYSRQ>  no need to complicate it even more with <CTL>...
Thanks for the heads up. I'll give it a shot ASAP. In the meantime I've reinstalled GUTSY.

---

### Post by landeel on 2008-07-17
@ knightmuzic
about DV6000 's:

Edit your /boot/grub/menu.lst, you will see something like that:
> kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=050e5163-c747-462e-9fe8-31127188f1ef ro quiet splash

Just change it to add the parameters like that:
> kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=050e5163-c747-462e-9fe8-31127188f1ef ro quiet splash noapic irqpoll noirqdebug

This will only work if the system is already installed on HD. Otherwise, you will have to install using this procedure:
[http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops]("http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops")

But still kernel 2.6.24 freezes sometimes, specially on NVIDIA drivers + OpenGL. I recommend downgrading the kernel to 2.6.22.

---

### Post by benji.ijneb on 2008-07-18
I'm on a dell latitude c400/ it freezes every 15 or so minutes, but only if the usb mouse in unplugged, so generally it's ok. However, it does mean that it is very dificult to use this pc while on the move. (admittedly this is nowhere near as bad as it is for some of you...)

I'm very confused about some of the feedback some people have given. can anyone tell me for certain if this problem is fixed in intrepid? Thanks!

---

### Post by hocvol1 on 2008-07-19
I am very new to Ubuntu and this is my first post to these forums. I have two elderly Dell machines running Hardy 8.04, both running wireless and one of them experiences a complete freeze seemingly randomly every other day while browsing FF3.  The freeze is accompanied by the keyboard flashing cap locks and scroll lock keys.  A hard shutdown is necessary to break the freeze.

One machine, which is running OK without a freeze, is an 8 year old P3 Dell with a maxed 512meg RAM, a nvidia TNT video card,  and 866mzh CPU. It is a wirless connection using a Linksys WRT54G.

The second machine, which freezes, is a newer P4 Dell 4500 with a 2.26gig CPU and 768meg RAM.  I was given this machine a few days ago and installed Ubuntu. I don't know what the video card is but using either the generic video driver or nvidia provided, freezes nevertheless. It also has a wireless Linksys WRT54G.

I do not have enough command of Linux to give much further discussion but offer to those who may come up with a fix.  For the moment I am at my older Dell and although slow, it works.  Peace

---

### Post by Solomoriah on 2008-07-19
I'm seeing a lockup that happens when someone logs out; this is my home computer (Fedora Core at work) and we are using the Switch User feature.  When it locks, the screen is black (PM mode) and the keyboard is unresponsive; however, though I haven't been able to verify it yet, I think the system is still "working."

I read that the proprietary ATI drivers might cause a similar issue, so I reverted to the open source driver, but the problem persists.

Intel DP35DPM mainboard, Core2 Quad 2.4 GHz, Diamond video with an ATI Radeon chip (sorry, I forget which one), 2 GB RAM.

---

### Post by External on 2008-07-20
> **benji.ijneb said:**
> I'm very confused about some of the feedback some people have given. can anyone tell me for certain if this problem is fixed in intrepid? Thanks!

This is what is known to be the case at the moment:
[http://ubuntuforums.org/showpost.php?p=5308402&postcount=212](http://ubuntuforums.org/showpost.php?p=5308402&postcount=212)
(present thread, post 212)

As it seems from the posts of pple having tried Intrepid, the issue remains to be fixed in that release as well, and there does not seem to be much chance that the bug would be fixed in Hardy anytime soon, given that it's been 3 months since they couldn't deal with it. The bug is known to be a 2.6.24 kernel issue, and in Hardy developers officially cannot make an update to 2.6.25 (the one Intrepid is built on), which also seems to be buggy for those affected by this bug.

---

### Post by benji.ijneb on 2008-07-20
> **External said:**
> This is what is known to be the case at the moment:
[http://ubuntuforums.org/showpost.php?p=5308402&postcount=212](http://ubuntuforums.org/showpost.php?p=5308402&postcount=212)
(present thread, post 212)

As it seems from the posts of pple having tried Intrepid, the issue remains to be fixed in that release as well, and there does not seem to be much chance that the bug would be fixed in Hardy anytime soon, given that it's been 3 months since they couldn't deal with it. The bug is known to be a 2.6.24 kernel issue, and in Hardy developers officially cannot make an update to 2.6.25 (the one Intrepid is built on), which also seems to be buggy for those affected by this bug.

perhaps it would be possible to put a poll in this thread about what people have used that fixes the problem? I have installed LXDE as a second to GNOME - it fixes all the problems for me (when i'm running it). It's not as feature-full as GNOME, but still pretty damn nice...

So, yeah. a poll would be really helpful for some people

---

### Post by Mighty_Joe on 2008-07-21
> **benji.ijneb said:**
> So, yeah. a poll would be really helpful for some people

The poll is [right here]("http://ubuntuforums.org/showthread.php?t=846120").

---

### Post by Redsandro on 2008-07-21
Some people mention it's a frozen kernel. But please note you can still do anything through **ssh** (including a clean reboot). Can I restart my frozen desktop manager through ssh? I am eager to try that. Not very neat, but would safe me rebooting time.

---

### Post by trent1980 on 2008-07-21
Just for the record. Mine completely locks up to where my only option is a power cycle. I'm back on my XP partition until next year. This is ridiculous.

---

### Post by daniel7860 on 2008-07-21
my comp freezes when i play games in wine, like AOM titans and Counter strike.
i just have to play for a few minutes then it freezes. 
using different audio drivers in wineconfig doesn't work.

It sometimes freezes during normal use but that happenes rarely.


I am using ATI Mobility radeon X300
On a 1.6Ghz  Dell Inspiron 9300

---

### Post by Solomoriah on 2008-07-21
The only freezes I've seen appear to happen when the VT changes, generally when I use the "switch user" feature.  I thought it was related to my proprietary ATI drivers, but I disabled them and rebooted and still experienced the problem.

I've forbidden my wife and daughter from using "switch user" and the problem has abated.  Just logging out and back in doesn't seem to cause a freeze, unless someone has already switched users.

---

### Post by External on 2008-07-22
> **Redsandro said:**
> Some people mention it's a frozen kernel. But please note you can still do anything through **ssh** (including a clean reboot). Can I restart my frozen desktop manager through ssh? I am eager to try that. Not very neat, but would safe me rebooting time.


People more experienced than us (or me at least) suggested it's a kernel issue, because:

1. It affects a lot of users with completely independent hardware configs; the problem very probably is not related to whether you have an ATI, Nvidia or any integrated video card, what Wifi card you have and the like: very different machines might be affected.
2. None of the "solutions" worked for everyone.
3. The freeze occurs absolutely randomly, irrespective of what applications you are using and how long you've been using them for.
4. It's NOT simply X, that freezes, since for most people only the "elephant-raising" method works, or worse, only a hard reboot; a Ctrl+Alt+Backspace / Ctrl+Alt+Del does not.
5. Restoring kernel 2.6.22 in Hardy seems to solve the problem for all who tried it, if I remember well.

It was not simply suggested that the kernel itself freezes, the statement was that it's either a kernel flaw, or Ubuntu patches somehow break the kernel in Hardy making it unreliable and unusable and a distro that frightens users away from upgrading/switching to.

---

### Post by External on 2008-07-22
> **Mighty_Joe said:**
> The poll is [right here]("http://ubuntuforums.org/showthread.php?t=846120").

I'm not completely sure whether this is what the original post requested; this can be a useful poll, but does not collect the info on what users tried fixing the insecurity in Hardy - and succeeded. I suppose the idea was kind of like the sticky proposed, so that newcomers don't need to read through approx.30 pages of uplifting bu!!sh!t from those of us who have been wandering in the dark for longer than some others.

---

### Post by oxman on 2008-07-23
> **External said:**
> 
It was not simply suggested that the kernel itself freezes, the statement was that it's either a kernel flaw, or Ubuntu patches somehow break the kernel in Hardy making it unreliable and unusable and a distro that frightens users away from upgrading/switching to.

Thank you for the informative reply External. Do you have any idea what is being done about the lock ups? Please keep us posted if you are tracking this. Is there another thread that is tracking this issue without all of the flack?

---

### Post by mikedemario17 on 2008-07-23
yeah i had 7.10 and it ran just fine then i upgraded...and every 2 min. my fire fox freezes and i have to wait out 1 min. then it starts working again...wtf.....im going to go back to 7.10

---

### Post by External on 2008-07-23
> **oxman said:**
> Thank you for the informative reply External. Do you have any idea what is being done about the lock ups? Please keep us posted if you are tracking this. Is there another thread that is tracking this issue without all of the flack?

You're welcome. I have switched back to Gutsy, since I don't have the luxury of giving up my work altogether for testing a distro version that doesn't seem to be working for me. However, here's what I personally learned.

Here ([http://lwn.net/Articles/287840/](http://lwn.net/Articles/287840/)) is the most informative thread about the bug I've found. As it seems from the posts, the debugging process has been terminated by developers saying that in Intrepid the problem is not present any more. (According to some posters around here this is not true; i.e. the bug is present) This is less than nice, given that the bug was filed for Hardy and not Intrepid, Hardy is the LTS, and even if it wasn't I wouldn't sympathize with this present policy.


The one above also refers to a bunch of other threads (some of the really long ones, like ours) here at Ubuntu forums, eg. [http://ohioloco.ubuntuforums.org/showthread.php?t=768200](http://ohioloco.ubuntuforums.org/showthread.php?t=768200)

This is the original bug reported in March, Hardy pre-release era: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996)

This is MightyJoe's repost of the bug @ launchpad:
[https://bugs.launchpad.net/ubuntu/+bug/227882](https://bugs.launchpad.net/ubuntu/+bug/227882)

Sergio Callegari's _very_ informative post: [https://bugs.launchpad.net/ubuntu/+bug/227882/comments/9](https://bugs.launchpad.net/ubuntu/+bug/227882/comments/9)

In a nutshell this is all I know at this point. Please do mind that I'm only a 'clueless noob' and there must be many more experienced pple who can make more sense out of all this lockup issue as well as the reason why it's been so very inefficiently treated. However if I get any new info, I'll post it here.

---

### Post by theDentist on 2008-07-23
I've got Hardy on one of my computers and it has never frozen (yet!!).  My gut feeling is that it will have something to do with the graphic card drivers.  Anybody noticed if any difference between nVidia and Ati.  nVidia has always been my preference as Linux seems to work better with it. Have you installed the drivers to get all the eye candy effects or are you running the generic ones.  It may be worth playing around with them. But on the other hand I may be talking a load of Rubbish!! 


Peter

---

### Post by SonWon on 2008-07-23
I turned off Compiz and now my laptop has stopped freezing.

---

### Post by Solomoriah on 2008-07-23
My freezes happen when changing VTs.  I'd like to try downgrading to the 2.6.22 version... can anyone give me a rundown of the procedure?  I know how to do it on Fedora but this is my first "real" Ubuntu system.

---

### Post by infocom on 2008-07-25
> Restoring kernel 2.6.22 in Hardy seems to solve the problem for all who tried it

Anyone know how to do this? Thanks

---

### Post by Mighty_Joe on 2008-07-25
For those of you who believe you are suffering from the same [random kernel freeze]("https://bugs.launchpad.net/ubuntu/+bug/227882") that I get, Ubuntu Intrepid Alpha 3 is available for testing in live cd form [here]("http://www.ubuntu.com/testing/intrepid/alpha3").  Note the caveats.  This is an Alpha release.  There will be bugs.  If you have problems with Intrepid, report them in the [Intrepid Testing Forum]("http://ubuntuforums.org/forumdisplay.php?f=346").
My system is much more stable with Intrepid, though I still get an occasional lockup which appears to be related to web browsing (possibly related to the well-known [pulseaudio]("http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio+hang") bugs?).   
I'm downloading the Intrepid Kubuntu Alpha 3 right now (which does not use pulseaudio) so I should have that factor ruled in or out soon.

Ugh.  It appears that the Kubuntu Live-CD is [unusable]("http://ubuntuforums.org/showthread.php?p=5455878").

---

### Post by Solomoriah on 2008-07-25
I figured it out.  You have to add the gutsy repos to Synaptic.  The hard part was finding the correct apt lines.

It did resolve my problems... but only at the cost of Compiz (which doesn't work, and had to be removed).  Scrolling, window movements, etc. became very jerky.

I reverted back to the Hardy kernel, and tested the "switch users" functionality, and so far (knock on wood) it's working.  No idea why.

---

### Post by Solomoriah on 2008-07-25
Oh, and I did reinstall Compiz.

---

### Post by External on 2008-07-25
> **Solomoriah said:**
> I figured it out.  You have to add the gutsy repos to Synaptic.  The hard part was finding the correct apt lines.

Could you please post the relevant lines so that others can try downgrading to 2.6.22 easily and we can have a more representative number of people trying Hardy with the old kernel?

> It did resolve my problems... but only at the cost of Compiz (which doesn't work, and had to be removed).  Scrolling, window movements, etc. became very jerky.

Actually, that's kind of a mystery; window movements used to be / are still jerky for me in Gutsy too, even though I installed the Ati 8.4 driver and glxgears showed a high number of FPS (around 4000Fps, if I remember well). Compiz is a mystery for me altogether...

---

### Post by Solomoriah on 2008-07-25
It's actually pretty simple:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse

(all on one line) should do it for you.

But believe me, it's a pain in the butt working out the issues.  Save yourself some trouble, if you try this... proactively remove Compiz when you install the "old" kernel.  Don't wait until you restart.

Use the Grub interface to choose the old kernel (you don't have to remove the newer kernel(s) from your system to try this).

But now, the question is, was it the kernel, or Compiz, or something else entirely?

---

### Post by SonWon on 2008-07-25
For me, all I did was disable Compiz.

---

### Post by landeel on 2008-07-25
At least for me the problem is the kernel. And then anything that uses OpenGL / NVIDIA will probably make my system hardlock, even with Compiz uninstalled. It can take a minute, or many hours, no pattern here.

But I'm using kernel 2.6.22-14 and running stable as a rock! :guitar:

---

### Post by Solomoriah on 2008-07-25
> **SonWon said:**
> For me, all I did was disable Compiz.
Did that fix your lockups, then?

... so far, so good for me, 2.6.24-19 kernel, proprietary ATI driver and Compiz and it's all still working.  Knock on wood...

---

### Post by Solomoriah on 2008-07-26
Gah.  Well, so much for that.

I don't think my problem belongs in this thread any longer.  Let me elaborate:

One user logs in, then switches to another user without logging out.  I can switch back and forth, log one or the other out, log in yet another user, all just fine (though evidently I can only have two at a time logged in?) but, as soon as the *last* user logs out, GDM loses its mind.  No mouse pointer, spotty keyboard focus, and that last user who logged out is still shown as logged in on the face-browser list... and if I manage to get a username and password typed in, GDM grays the password field and apparently locks up.  But the system as a whole isn't locked, since pushing the power button results in what appears to be a normal shutdown.

Possibly I need a new thread for this one.

---

### Post by csddavies on 2008-07-26
I tried rolling back to Gutsy.  It froze too even though it ran without incident for 4 months pre-Hardy.  Now I'm booting in "recovery" mode and just running text mode and starting up apache and mysql and it's been running for 4 days with no problems.  I guess I'll live this way until Intrepid or someone figures out what is going on.

---

### Post by kidux on 2008-07-27
> **csddavies said:**
> I tried rolling back to Gutsy.  It froze too even though it ran without incident for 4 months pre-Hardy.  Now I'm booting in "recovery" mode and just running text mode and starting up apache and mysql and it's been running for 4 days with no problems.  I guess I'll live this way until Intrepid or someone figures out what is going on.

Odds are you're still using the kernel that installed/updated in Hardy, and therein lies the problem. My suggestion would be to either downgrade/upgrade (the Intrepid shipped kernel doesn't have the problems, supposedly) the kernel, or do a clean install of Gutsy. Either way a custom compiled Intrepid shipped kernel is probably the best bet.

---

### Post by External on 2008-07-27
> **Solomoriah said:**
> It's actually pretty simple:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse

Is this the actual command line?

> Possibly I need a new thread for this one.

Probably you'd be better off filing a bug report at launchpad after making sure no one else has already done that.

---

### Post by Solomoriah on 2008-07-27
That's the apt line to add to Synaptic.  I actually added four lines, one for each:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse

I'm a bit of a newbie when it comes to apt/Synaptic.  Most of my experience has been with Fedora Core.

I found this bug report on launchpad.net:

[https://bugs.launchpad.net/ubuntu/hardy/+source/gdm/+bug/118605](https://bugs.launchpad.net/ubuntu/hardy/+source/gdm/+bug/118605)

... which describes the exact bug that I'm experiencing; however, at present the only suggested fix is for kubuntu.  I'm a GNOME fan, myself.

---

### Post by MedellinManDem on 2008-07-27
I'm no longer having problems. Haven't been for ages. I'm surprised other can't say the same.

---

### Post by Mighty_Joe on 2008-07-30
I've got new hope for Intrepid.
As I mentioned [earlier]("http://ubuntuforums.org/showpost.php?p=5455355&postcount=300"), Intrepid is more stable than Hardy on my hardware, but I still get lockups.  On a whim I swapped out my ATI Radeon 8500 for an ATI Rage 128 (yea, it's old, but it's all I have) and lo and behold, 2.5 hours of uptime (and serious use) without a hiccup.  
There may be a bug in the [open source Radeon driver]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/141551") that's causing my problem with Intrepid. 
I tried installing the fglrx driver, but I screwed X up bad so I can't comment on it.
Again, if you have [this problem]("https://bugs.launchpad.net/ubuntu/+bug/227882"), I encourage you to try the [Intrepid Live CD]("http://cdimage.ubuntu.com/releases/intrepid/alpha-3/")

---

### Post by SonWon on 2008-07-30
Hmmm, I have an ATI 9600 in a laptop maybe the Compiz lockups is related to my video card and Compiz combination?

---

### Post by Mighty_Joe on 2008-07-30
> **SonWon said:**
> Hmmm, I have an ATI 9600 in a laptop maybe the Compiz lockups is related to my video card and Compiz combination?

Read the [bug I referenced earlier]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/141551") and see if it matches your symptoms.  It doesn't sound like it.

---

### Post by SonWon on 2008-07-30
Your right, my freezes were hard.  Usually when using FireFox and turning off Compiz fixed them.

---

### Post by Mighty_Joe on 2008-07-30
> **Mighty_Joe said:**
> I've got new hope for Intrepid.


I've got new hope for Hardy.  Again, on a whim I popped in the Rage 128, booted the Hardy 8.04.1 live cd and used it like I normally do, listening to MP3's and browsing the web.  It's been working for 80 minutes. That beats my previous Hardy uptime record by over an hour.  I'm posting from it now.  So is my problem a balky ATI card, bad open-source driver, or screwy kernel?

---

### Post by Solomoriah on 2008-07-30
Hmm.  I have a Radeon card, but I can borrow an Nvidia GeForce... might try that.

---

### Post by hocvol1 on 2008-07-31
Well it seems that I may have found my answer as to why my machine freezes up after 15 minutes or so.  It always occurred when using Firefox and I am using the latest version as well.  I simply went to Opera.  After 1.5 hours use everthing works just fine.  We'll see. :-)

After about 4 hours got the freeze while watching a news clip in Opera. :(  Oh well, that's progress, sorta.

---

### Post by tizo_rh on 2008-07-31
At least my problem, is not related to display card, or memory, or sound, or wireless. 

I have tested several fresh installs Hardy with different disks, different memory modules, on board display and AGP card, wireless and wired connection, with and without CDROM, on board sound, and no sound and it always freezes. The only common hardware in the different installs, were the motherboard and the processor (soyo sy-7isa / Intel Pentium III). The freezes occurs generally (but not always) when navigating in pages with flash animations, but I have also tried with adobe flash, gnash, and swfdec, and firefox and seamonkey, having in all the cases the same problem. I have also tested xubuntu, and gutsy ubuntu and xubuntu, but the symptoms were the same.

Moreover, I have other running PC with hardy, without any problem (chaintech ct-skt600 / AMD Sempron(tm) 2200+), and have installed xubuntu in another one (asus p2b-l / Intel Pentium II), with some of the hardware that I have tested in the problematic PC, without any problem too.

So, I am pretty sure, that in my case, the problem is related to the motherboard.

---

### Post by Mighty_Joe on 2008-08-01
> **tizo_rh said:**
> So, I am pretty sure, that in my case, the problem is related to the motherboard.

There's two common elements in your story: the motherboard and Hardy.  Even with my [suspect video card]("http://ubuntuforums.org/showpost.php?p=5491044&postcount=314") I find [Intrepid to be more stable than Hardy]("http://ubuntuforums.org/showpost.php?p=5297758&postcount=189").
Try [Intrepid Alpha 3]("http://cdimage.ubuntu.com/releases/intrepid/alpha-3/") and let us know.
Any chance you have an ATI Radeon?

---

### Post by tizo_rh on 2008-08-01
Actually, the only common element is the motherboard (and the processor). As I have said, I have tried with Gusty too.

I don't have an ATI card, and I have tried with both, the onboard card, and a Nvidia TNT2.

---

### Post by Mighty_Joe on 2008-08-01
> **tizo_rh said:**
> I don't have an ATI card, and I have tried with both, the onboard card, and a Nvidia TNT2.

What is your onboard video chipset?  If it's Nvida, it may be using the same driver.

---

### Post by tizo_rh on 2008-08-01
> **Mighty_Joe said:**
> What is your onboard video chipset?  If it's Nvida, it may be using the same driver.

Nop, it is an Intel. Moreover, I have installed the Nvidia TNT2 card in other PC, and Hardy works perfectly with it!

---

### Post by Mighty_Joe on 2008-08-01
> **tizo_rh said:**
> Nop, it is an Intel. 

So much for that theory.
Have you tried [Feisty Fawn]("http://releases.ubuntu.com/7.04/")?  My hardware has months of uptime with Feisty without a problem. If I weren't constantly taking it down to test Hardy and Intrepid, that is.

---

### Post by Skalman5 on 2008-08-02
Trying Hardy for the second time now (i thought the freezing issue was fixed, so i installed it again.. Doh!!) When i used it when it was newly released i had serius problems with the computer freezing and the only thing that worked was an hard shutdown (pressing the powerbutton). Nothing that i tried worked and it all ended up in me reinstalling 7.10.

Stupid as i were i installed it again and still the same problems occur.

_Hardy freezes for me when:_
Evolution mail is finished downloading new mails
Randomly when i press TAB, BACKSPACE or more rarely other tangents
Other applications: for example browsing the network.
When the screensaver starts

It's very irritating not getting a log/crashreport from these freezes (it would make it alot more easy to fix)

I must say that it's far better this time so some improvent must have been done since april but still an unacceptable high "freezing frequency" for any linux system.

---

### Post by Mighty_Joe on 2008-08-02
> **Skalman5 said:**
> Trying Hardy for the second time now 

Do you still have an [ati video card?]("http://ubuntuforums.org/showpost.php?p=3758199&postcount=234")  If so what driver are you using?  Can you try swapping it out?  I have a Radeon 8500 and use the open source driver.  If I swap it out, my [hardy problems]("http://ubuntuforums.org/showpost.php?p=5492647&postcount=318") disappear.

---

### Post by Skalman5 on 2008-08-02
> **Mighty_Joe said:**
> Do you still have an [ati video card?]("http://ubuntuforums.org/showpost.php?p=3758199&postcount=234")  If so what driver are you using?  Can you try swapping it out?  I have a Radeon 8500 and use the open source driver.  If I swap it out, my [hardy problems]("http://ubuntuforums.org/showpost.php?p=5492647&postcount=318") disappear.

Thanks for your quick answer!

ATI-card yes (ATI mobility radeon X700). Latest ATI-drivers 8.7 installed. 

When i used the opensource drivers in 7.10 i experienced great loss in prestanda compared to the resricted ones. Have that been changed in Hardy?

---

### Post by mgmiller on 2008-08-03
I have a very stable install of Hardy that never gave me freezing problems.  Suddenly, I get hard lockups with no mouse or keyboard that require the reset button on my tower to restart.  

After looking through this forum, the list of suspects was:
compiz
powernowd
cool n' quite settings in BIOS
acpi=off added to kernel line
trying an earlier kernel

None of these worked.  

I then remembered I had purchased a new 1000w Tripplite UPS that uses a USB cable to monitor the state of the UPS.  When I unplugged the USB cable from the Tripplite, all the system freezes stopped and my stability returned.

I have entered a bug report here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/254309](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/254309)

---

### Post by Mighty_Joe on 2008-08-03
@mgmiller: That's just crazy talk. ;)

> **Skalman5 said:**
> ATI-card yes (ATI mobility radeon X700). 

So you have a laptop?  No chance of swapping that card out, eh?
I don't know about the performance of the ATI open-source drivers in Hardy.  Can't get Hardy to run long enough to test it!

---

### Post by mgmiller on 2008-08-03
Mighty_Joe said:
> @mgmiller: That's just crazy talk. :wink:

To which I respond:
Crazy you say?....Bwhaaahahahah!  I'll show you crazy...:lolflag:


Actually, many people have found that changes in acpi, powernowd, cool n' quite settings in BIOS, acpi=off added to kernel line and now my USB monitoring of the UPS all involve gnome-power-manager in some way.

I believe there is a bug in that package somewhere, hence my bug report.

---

### Post by Michael Schmidt on 2008-08-04
I have also been having intermittent Hardy hard freezes.  Since the most recent updates from Ubuntu (8/4/08) it seems they have gotten more "reliable" in that it freezes within 20 minutes when I am playing Web Sudoku via FireFox 3.  I have an ATI X1300 video card and, after reading several posts, decided to disable the proprietary driver (System>Administration>Hardware Drivers, then reboot).  My system has now been running for several hours without a freeze, so I think this has solved the problem, at least for my system.  Others may find this solution helpful.  The only down-side is that I am not able to access the full capabilities of my video card, but I can live with that.  Perhaps some day the problem will finally be solved.

---

### Post by kufio on 2008-08-04
> **Michael Schmidt said:**
> I have also been having intermittent Hardy hard freezes.  Since the most recent updates from Ubuntu (8/4/08) it seems they have gotten more "reliable" in that it freezes within 20 minutes when I am playing Web Sudoku via FireFox 3.  I have an ATI X1300 video card and, after reading several posts, decided to disable the proprietary driver (System>Administration>Hardware Drivers, then reboot).  My system has now been running for several hours without a freeze, so I think this has solved the problem, at least for my system.  Others may find this solution helpful.  The only down-side is that I am not able to access the full capabilities of my video card, but I can live with that.  Perhaps some day the problem will finally be solved.

I also had freezes in my pc when I was running Nvidia propietary drivers, but the moment I disabled the driver, I had no more lock-ups/freezes. 
Does anyone another way of getting 3d acceleration on my Nvidia GeForce 7200 GS?

---

### Post by andso on 2008-08-05
is there anybody who have tried this?
edit the file /etc/hosts and modify the first line :
127.0.0.1 localhost **name-machine**
127.0.1.1 name-machine

---

### Post by Michael Schmidt on 2008-08-05
From reading this thread, it appears that there may be a variety of causes for these freezes.  Teasing these out is going to be tough.  Could it be that the proprietary video drivers are often to blame and, therefore, a worthwhile place to focus debugging efforts?

---

### Post by Mighty_Joe on 2008-08-05
> **Michael Schmidt said:**
> Could it be that the proprietary video drivers are often to blame. . .

I have a counter-example [right here]("http://ubuntuforums.org/showpost.php?p=5491044&postcount=314").  The open-source driver is locking up on me.
If you have a test case that is reproducible, by all means, [report it]("http://www.ubuntu.com/community/reportproblem").

---

### Post by michael2012 on 2008-08-05
My system is an old HP desktop and FF wired -- so the hang up may be more problematic than a wireless networking glitch. I think maybe I should downgrade until HH is fixed. M

---

### Post by mgmiller on 2008-08-06
I still think the one unifying theme here is gnome-power-manager.  All I had to so was unplug a USB cable to get a nice stable Hardy back.  Can anyone else try uninstalling gnome-power-manager and see if it makes a difference?

---

### Post by Solomoriah on 2008-08-06
Removing gnome-power-manager removes gnome-session and ubuntu-desktop.  Doesn't sound like a good idea, on the face of it.

---

### Post by Mighty_Joe on 2008-08-06
> **mgmiller said:**
> I still think the one unifying theme here is gnome-power-manager.  

I am running Kubuntu on a desktop.  No gnome power manager here.

---

### Post by MedellinManDem on 2008-08-06
This has started again for me. 

Using programs like emesene, thunderbird, openoffice and firefox together is a no-no.

---

### Post by Vorian Grey on 2008-08-06
I have been running fine for weeks but Hardy started this with me as well.

---

### Post by Michael Schmidt on 2008-08-06
So, folks are getting freezes with (among other things) proprietary as well as open-source video drivers, and that some are able to resolve these freezes by changing drivers.  For me, disabling the proprietary ATI driver has completely resolved the problem.  The common theme for some of us is that the video drivers are not playing nice, so is that being addressed?

I'm still a Linux fan.  As a former Windows user, I'm accustomed to things not working right!

---

### Post by Mighty_Joe on 2008-08-06
> **Michael Schmidt said:**
>  The common theme for some of us is that the video drivers are not playing nice, so is that being addressed?


Your guess is as good as mine.  There's not a lot of feedback on the bugs I've been following.  I'm pretty sure I'm seeing [this bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/141551") because if I turn off DRI my system's stable running Hardy.

---

### Post by mgmiller on 2008-08-06
> **Mighty_Joe said:**
> I am running Kubuntu on a desktop.  No gnome power manager here.

For you it would be kde-guidance-powermanager

I wonder what the similarities between the kde and gnome versions of this package are?

---

### Post by Vorian Grey on 2008-08-06
> **Michael Schmidt said:**
>  The common theme for some of us is that the video drivers are not playing nice, so is that being addressed?


I kind of doubt it. These kind of issues have been going on in Linux forever. Plus, Ubuntu just uses the drivers. They don't develop them.

---

### Post by Mighty_Joe on 2008-08-07
I'm nearly certain that my hangs are a result of ATI Radeon driver issues.  If I turn off DRI in xorg.conf I get hours of uptime in both Intrepid and Hardy with no hangs.  
This may be what's going on in [Bug 141551]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/141551") or [150863]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/150863").
Give it a try.  If it works for you, post [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/227806").

---

### Post by smuggler on 2008-08-07
This problem has different sources. And in my case, I can't even boot into Interpid Alpha3, it freezes right after X start.
Also, some people mentioned freezes when trying to boot Gutsy. Can we call it another symptom? Tallo, have you tried booting with acpi=off option?

Using MSI S430 laptop.

---

### Post by oxman on 2008-08-07
Nope. No ATI here. My guess is a nexus between X and the kernel. If i rebooted using the safe mode then rebooted normally I bypassed the problem... for a while.

:)

Come on guys. Fix it. I hate operating in a crippled mode. I love FOSS but this is the pits. Sloppy, sloppy, sloppy. This is just what the Debian folks were hoping to avoid. I liken it to the microsofting of linux.

Not ungrateful, just realist.

---

### Post by ibuclaw on 2008-08-07
> **oxman said:**
> Nope. No ATI here. My guess is a nexus between X and the kernel. If i rebooted using the safe mode then rebooted normally I bypassed the problem... for a while.

:)

Come on guys. Fix it. I hate operating in a crippled mode. I love FOSS but this is the pits. Sloppy, sloppy, sloppy. This is just what the Debian folks were hoping to avoid. I liken it to the microsofting of linux.

Not ungrateful, just realist.
As realist as you mean in you intentions, it just isn't possible, what you are asking for.

As long as proprietary drivers continue to plague the Linux kernel, there will be no end of troubles. Simple as.

> 
Closed source drivers or modules for the Linux are harmful, undesirable and have been repeatedly found to be detrimental to Linux users, businesses and the greater Linux ecosystem. They negate the openness, stability, flexibility and maintainability of the Linux development model and shut their users off from the expertise of the Linux community.


Recently last month, around 140 kernel hackers actually signed a petition to help weed out/make life harder for proprietary drivers.

The 2.6.25 kernel was a big start when they pulled out several hooks to the kernel that no one was using (except Nvidia).
Nvidia have just about turned that situation around and have barely fixed the problem in the 2.6.26 kernel. But I think that this idea should be pressed on harder by the dev team.

We will not make our software work for the proprietary companies hardware. They will either open their hardware up or be forced to continually struggle/build to support us.

Regards
Iain

---

### Post by PadreSol on 2008-08-07
> **tinivole said:**
> 
Recently last month, around 140 kernel hackers actually signed a petition to help weed out/make life harder for proprietary drivers.

The 2.6.25 kernel was a big start when they pulled out several hooks to the kernel that no one was using (except Nvidia).
Nvidia have just about turned that situation around and have barely fixed the problem in the 2.6.26 kernel. But I think that this idea should be pressed on harder by the dev team.

We will not make our software work for the proprietary companies hardware. They will either open their hardware up or be forced to continually struggle/build to support us.

Regards
Iain

Wow I hadn't heard about that.  Well it's good news to me. 

You seem to be following this a bit.  

How far has that other graphics card gotten that was going to be part open source?

Do you know if there's a list somewhere that guides us toward good graphics cards to use with linux?

---

### Post by PadreSol on 2008-08-08
Not to hijack the thread, just to follow up on the thread two before this one.

Tow projects for making an open source VGA  card
[http://www.projectvga.org/](http://www.projectvga.org/)
[http://wiki.opengraphics.org/tiki-index.php](http://wiki.opengraphics.org/tiki-index.php)

But still not ready for purchase apparently, unless you like to hack FPGAs.

---

### Post by oxman on 2008-08-09
I have been using some version of linux since 1995 without too much difficulty with regard to proprietary drivers. I'm glad that some of these issues are being addressed.

I have been following the open graphics  project  since its inception. I happy  that is happening.
 
I agree with your premise of not catering to the corporations. 

But it should not be that users are left with having to struggle to get their systems to work. It puts a very bad name on linux. It is no different than the abuses of M$ if you disregard your user base. Simply put, that is not what the term "Ubuntu" means. 
I used dapper for the years and patiently waited for the next LTS version. My confidence in the linux community is such that I unhesitatingly installed hardy. Now neither dapper or hardy are working properly and I am limping along until there is a solution. Are you saying my confidence was misplaced?

---

### Post by dragonboss on 2008-08-09
so what there's no fix to this bug i mean cime on... If this goes on then ubuntu will be no differnt than win and my xp hasnt frizen since i installed it along side ubuntu but ubuntu has frozen randomly several times somebody please please please hurry up and fix this thing! Just cos of wireless and this freezing problem i havent been able to fully detach myself from windows despite the way i detest the os.:mad:

---

### Post by Charlie Wilkes on 2008-08-09
> **oxman said:**
> 
I agree with your premise of not catering to the corporations. 

But it should not be that users are left with having to struggle to get their systems to work. It puts a very bad name on linux. It is no different than the abuses of M$ if you disregard your user base. Simply put, that is not what the term "Ubuntu" means. 


Interesting.  I agree, but I question whether the user base is sending a clear message about what is most important.

What I noticed in the reviews of hardy were points like "now you can change screen resolution without rebooting, a long overdue feature that Windows has had for years..."

Refinements like that are fine, but how important are they next to quality and stability under a wide range of conditions?  

I've also seen a number of video clips on youtube of rotating cubes, etc.  The implied message is "flashier than Aeroglas."  I assume the people who put these presentations together are part of the user base, and they are expressing what they think is important, at least at that moment.

Part of the problem may be that what is really most important is not what is most interesting and in fact is invisible to users because it consists of all the things that don't go wrong...

---

### Post by Michael Schmidt on 2008-08-12
I thought I had this problem resolved on my system (ATI X1300 video card running on nonproprietary driver, Hardy Heron).  I had several days without a freeze.  However, since I installed the latest updates, the freezes have returned.

---

### Post by carusoswi on 2008-08-13
Hardy freezes on my system, too.  Never had this problem in any version of Ubuntu until I installed 8.04.  I have not the time to read every single post in this thread, but I hope someone is addressing this problem.

Caruso

---

### Post by Solomoriah on 2008-08-13
The bad news is, it's probably more than one problem...

My particular problem, the user switch hang, seems to be associated with a problem with the Xorg server running away.  I found this out by opening a SSH connection to the computer first, then blowing it up.

When I get time, I plan to SSH in again, blow it up, and then strace the runaway.  Perhaps I'll learn something.

---

### Post by zieglerj on 2008-08-15
Ok I have all the symptoms described here. I have a wireless card and Nvidia dual monitor card. I tried the switching to the rt kernel solution and could get my video card to run with it. Now, after switching back to the most recent kernel I can't even get back into my Hardware Drivers to turn on my driver.

---

### Post by utnubuuser on 2008-08-15
Ditto -  Hardy Freezing solid,  might be Firefox, I've only experienced the problem while in Firefox.

AMD 32bit chipset

I've also wondered it it was one of the updates, because I've had Hardy Heron on my Thinkpad X31 since Beta2 (and all subsequent releases), and never had this problem.  now, with all the updates current, an occasional freeze up.  On the laptop it just becomes unresponsive to commands, while the cursor is still movable, but on the desktop with the AMD chip it freezes solid.

Also, 7.04 runs rock-solid on the same hardware.

Wouldn't care if it wasn't so dangerous for the hard drive
Hardy's pretty sweet  -- And I will not be going back to any other distro.

Has Anybody got this problem when using the newer 8.04.1 iso, or is it only the 8.04?

---

### Post by utnubuuser on 2008-08-15
FSF has a list

---

### Post by Ethyrdude on 2008-08-15
I'm thinking of dropping Ubuntu, there are just too many crashes.  I am going to try one more thing, to do an nvidia card driver upgrade the debian way, yes the driver is tainted but who cares if it works.  I use the same driver on my other computer without issue so here goes nothing...oh yes, the other computer is running Debian but Ubuntu isn't that different is it, besides how can you break something already broken.

Ok, don't do the Debian way, it's not pretty, what I ended up doing is blowing away all the crude and doing a fresh install, have been doing some experimenting and might have messed things up so will try a fresh install first.

More info - after doing a fresh install, I also decided to run KDE, yes, I know, I prefer Gnome too but for the sake of experimentation - with Debian I had lots of Gnome issues too and I ended up just dropping it.  Besides, it's not even the complete OS, it's only a desktop manager.  I'm also having issues with Xfce.

---

### Post by superarmy on 2008-08-16
All issues I've had have been during Firefox, it randomly freezes upon pressing buttons, or whilst enabling flash.

---

### Post by Ethyrdude on 2008-08-16
If the issue is with firefox, try a different browser, if this stops the crashes then at least you know it's the browser.  Firefox was created from Mozilla but they do have subtle differences, try that first and see if you have the same problem, if you do then it may be one of the plug-ins or something more system wide.  The only problem I've had with firefox is that it stops responding if I switch to another desktop using the scroll wheel with some of the more intense compiz settings enabled.  However it doesn't cause a complete system crash, I can just close down firefox and restart it.

---

### Post by SonWon on 2008-08-16
> All issues I've had have been during Firefox, it randomly freezes upon pressing buttons, or whilst enabling flash.

I had the same issue until I turned off Compiz (Visual Effects).  Right click on the desktop and select Change Desktop Background.  Visual Effect tab and then select None.

---

### Post by Ethyrdude on 2008-08-16
Kind of makes me wonder if Compiz is the actual culprit.  I'm going to leave the bells and whistle off for a couple of days and see what happens, I'll load some of the more intense 3D games and play them all weekend and see what happens, I know, it a big sacrifice, it's a rough job but somebody has to do it. :popcorn:

---

### Post by Solomoriah on 2008-08-16
If it's Firefox, or Compiz... really, it's the kernel or the video drivers.  To freeze the system you have to screw up the kernel somehow.

---

### Post by Ethyrdude on 2008-08-16
I have Compiz installed but I've been been running kde and using konqueror for my browser, I don't have any browser plug-ins installed but I haven't really done much surfing today just playing 3D games.  Haven't had a single solitary freeze or even so much as any error message (Alsa can be nasty at times too).  Of course it's still too early to point fingers, everybody wants a quick fix but it's not always possible.  As for my earlier comment about dropping Ubuntu, I guess in a way I have in favor of Kubuntu but KDE isn't completely bug free either.

And yes, it could still be the video card driver or kernel, may be worthwhile doing a custom build but of course, once you go that route, you'll find that everytime there is a new patch or release, it's time to build a new kernel and I would rather just be playing a game than sitting there doing another kernel compile.

---

### Post by SonWon on 2008-08-16
I think we are just reporting what we have tried and what works.  For some it is one thing for others another.  Perhaps there is a common program that touches all of these areas.

---

### Post by zieglerj on 2008-08-16
I may have found a solution!

I followed this how to: [http://ubuntuforums.org/showthread.php?t=797270](http://ubuntuforums.org/showthread.php?t=797270)
substituting :
sudo init 3
sudo sh NVIDIA*

where it says to type:

sudo sh NVID[tab]

and haven't had a single freeze up all day while running multiple windows on four different desktops with extra compiz effects and widgets. Not only have I not had a freeze-up, my system has been running smoother than it has since I installed my video card. 

Just for the record I'm running a AMD 64 bit Athlon 2Ghtz, 4 gb ddr2 ram, with wireless data card modem and a nVidia e-Geforce 6200 dual display. 

Before this my system was completely freezing two - three times a day even if I only had a couple of windows open.

---

### Post by mcgarry83 on 2008-08-17
I have a laptop and a desktop both running Hardy. Both have the freeze problem. Here is what I have found. On my laptop, 95% of the time my computer freezes when using my PCMCIA-to-USB 2.0 adapter (My laptop only has usb 1.0). I use it for transferring large amounts of data to my MP3 player. It works fine for a while, then it locks up and I have to hard reset. I also have a usb wifi adapter (Netgear wg111v2, which has its on problems). It causes the freeze when using the PCMCIA adapter as well, but not when using the usb 1.0 ports. So if I dont use the PCMCIA card, I dont get freezes on the laptop. 

The desktop however, freezes for no apparent reason and randomly. Sometimes using firefox, sometimes not.

Im lost, I just hope Intrepid is more stable.

---

### Post by Ethyrdude on 2008-08-17
I think this is going to be one of those things where what works for one won't always work for another.  I smurfed the net all this morning with Firefox, installed all the plug-ins, well maybe not java but if it asked for it I installed it and I had no problems.  I know compiz is probably in there doing it's thing, don't know, don't have the manager installed for it, so whatever is running is doing fine.  I know I don't have a lot of bells and whistles set up but that's okay, I'd rather have a stable OS than a lot of special FX.

Also ran all the games that caused problems earlier, glest was one and it seems to run well although I can't play it worth a ... but that's a topic for another area.  Sauerbrauten runs good also, no lockups so I think my problems seem to be gone, if anything rears it's ugly head later I'll post it but otherwise, for me at least, the solution seems to be to lay off the Desktop Plugins.  Oh yes, I did make one minor change to xorg.cong, I fixed the problem with the wrong resolution being displayed but I doubt if that had any affect on this as my monitor indicated before that everything was running correctly.  Good luck and later peeps.

Edit, One item that I forgot to mention, might be nothing but I'm going to throw it in just in case.  I set up the video card driver the same as my first install last week and that was by using the Hardware Drivers Manager, but now when I reboot, as X kicks in I get the nVidia Splash Screen, which wasn't showing up on my first install.  I thought it funny at first to not see it but as this is my first time using Ubuntu or Kubuntu, whatever, I thought that perhaps a different nVidia driver was being used, perhaps something stripped down without the splash screen.  It's nice to see that it's still being used, doesn't add any functionality but it does indicate that the card is working properly.

---

### Post by zieglerj on 2008-08-17
I spoke too soon. While the driver I downloaded from Nvidia does work great, Hardy froze up just after I finished writing the above post. 
Now I am in the process of trying using the rt kernel as was sugested by another poster.

---

### Post by Ethyrdude on 2008-08-17
I just had my first game crash in three days but it was a recoverable error without having to reboot.  I was then able to go back in the game and start that level over, this time I made it past the same point and went on to the next level.  The game was Sauerbraten, and it locked up just after I killed something, this might have been a sound issue, I was able to see other desktops but I couldn't switch to another, had to ctrl, alt, backspace to restart the X server but this is progress, the last time this happened I had to do a hard reset.  Continuing to do more research.

Edit:  I just realized (I have forgotten too much) but kde uses kwin, and doesn't use compiz at all, I wonder what would happen if I switched back into the gnome desktop, even with a fresh install.  Hmm, worth a shot, I really want to try and solve this, if I start getting lockups I might try installing metacity and see if gnome behaves better with it. (If possible)  Hopefully zieglerj is having some luck with his efforts.

---

### Post by oxman on 2008-08-17
I'm still on track and watching closely. Keep up the good posts.

---

### Post by Mighty_Joe on 2008-08-18
> **SonWon said:**
> I think we are just reporting what we have tried and what works.  For some it is one thing for others another.  Perhaps there is a common program that touches all of these areas.

I've been following this topic closely since page 1. There seem to be several different bugs at work. Mine seems to be my [ATI video card or driver]("https://bugs.launchpad.net/ubuntu/+bug/227882").   zieglerj above seems to have a similar problem but he has NVIDIA card.  
What people should be doing is filing reports in [launchpad]("https://bugs.launchpad.net/ubuntu").  The developers can then collect those with similar hardware into groups of duplicate reports and get a better idea as to what's going on.

---

### Post by zieglerj on 2008-08-18
So far, since my last post I've made it 24 hours testing my system with some heavy usage and no freezes. I think switching to the rt kernel may have been the key, that a long with manualy installing the nvidia drivers.

---

### Post by DellX200user on 2008-08-18
I gave up!!!

I'll go back to another Linux distribution I had running before.

I hope everyone with HARD FREEZING CRASHES finds an answer quickly.

---

### Post by SonWon on 2008-08-18
My vga= line is commented out already?

---

### Post by Mighty_Joe on 2008-08-19
vga=xxx sets the video mode for [framebuffer]("http://en.wikipedia.org/wiki/Linux_framebuffer"). If you think it's a problem, you may want to turn off framebuffer support in X: [link]("http://www.xfree86.org/4.3.0/fbdev.4.html")
There's a number of [kernel options]("https://help.ubuntu.com/community/BootOptions") that can be set.  I have a second computer that has problems with Hardy, but seems to be more stable if I turn off ACPI and change the PCI mode.

---

### Post by zieglerj on 2008-08-19
48 hours and no freezes.

---

### Post by AJFonseca on 2008-08-19
Hi, guys,
I´m having almost the same problem... I got a Toshiba A215 laptop with (sorry the bad words) Windows Vista. I´d installed the xubuntu and ubuntu and both of them freezes all the time, in special when in Thunderbird composer.
Does any one have an idea on what can be doing this?
Please... I cannot keep using Vista or I´ll need a big hammer to smash my new laptop... And I don´t want to do it...

---

### Post by zieglerj on 2008-08-19
Do you have a nvidia or ATI video card?

---

### Post by AJFonseca on 2008-08-20
> **zieglerj said:**
> Do you have a nvidia or ATI video card?

Yes, I do. ATI X1200.

---

### Post by zieglerj on 2008-08-20
I was having this problem with a nvidia card and I've noticed scaning the forums that a lot of the problems caused by a nvidia card are shared by ATI.
The steps I took might help you but you'll have to adapt it to ati (usually by substituting "ati" for "nvidia" in the commands). 

What I did was:
First switch to the rt kernel by typing:

sudo aptitude install linux-image-rt linux-restricted-modules-rt

That in and of itself might do it for you but I also manually installed the drivers from the NVIDIA site. Even if it turns out not to have been necessary I'll never regret it. It's improved my cards performance greatly so if ATI is at all similar you'll probably want to manually install your drivers. 
The linux ATI drivers can be found @: 

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

Just select your hardware. The linux X86 section is for i386 the linux x86_64 is for 64bit. 

Here's where it gets hairy though. I'm not sure exactly on the installation. I'll post the way I did it with my NVIDIA card but like I said above you'll have to adapt it for ATI, maybe some of the other posters on this forum will have some pointers?
Anyway the instructions I followed are:

Move the driver you downloaded into your home folder. 
Then type in terminal:

sudo apt-get remove --purge nvidia*
sudo apt-get install linux-headers-$(uname -r) libc-dev build-essential

Now copy down the next commands because we are about to drop to the command prompt interface then type:

sudo /etc/init.d/gdm stop

hold alt+F1
enter in your username and password then type:

sudo init 3
sudo sh NVIDIA*

this should open the installer program for the nvidia drivers. Follow the instructions it gives you and at the end let it reconfigure your xorg.conf.
Once completed type:

sudo /etc/init.d/gdm start

After all of this I haven't had any freezes in about three days now. 
I'm running a 2ghtz AMD anthalon 64bit, 4gb ddr2 ram, with a e-GeForce 6200 NVIDIA.

---

### Post by aikiwolfie on 2008-08-20
I just got this prblem for the first time while using Pidgin Internet Messenger with my Yahoo account. Linux has never fozen on me like this ever!

---

### Post by Xizorbg on 2008-08-21
Hello All-

Not a noob - just wondering exactly where do we stand here?  Are there any specific dmesg commands or logs that can help better delineate the source of the freezes?

Thanks,
X

---

### Post by oxman on 2008-08-23
So far I have not been able to track down the essential problem or the solution. If you do please post here.

---

### Post by kamiar on 2008-08-24
I choose Gutsy, Hardy freezes are not tolerable! X-(

---

### Post by atrapine on 2008-08-24
Had pretty much same problem fresh install of hardy on Athlon XP 2000+ and Nvidia Crush IGP. After I updated Firefox all has been well sinse? They really should have left Firefox 3 Betta out of hardy.

---

### Post by Xizorbg on 2008-08-26
Hey All-

Hopefully not speaking too soon.

This very helpful thread gave me some hope:

[http://techxplorer.com/2008/04/23/fixing-random-freezes-in-ubuntu-804/](http://techxplorer.com/2008/04/23/fixing-random-freezes-in-ubuntu-804/)

I am running an AMD 64 w/ an older GeForce 4 Ti 4200 chipset w/ 2.6.24-19-server kernel.  Helping....for now.

Good luck and thanks to Techexplorer.

:guitar:

-X

---

### Post by Mach1US on 2008-08-26
Don't want to speak too soon but since last kernel update all is GOOOOD \\:D/
Even while running both at the same time full blown XP sp3 via VMware and Hardy.

---

### Post by alejandro.mc on 2008-08-29
Still no solution? If anyone knows something it will be appreciated.

Too bad, is the only problem I've ever encountered.

Cheers!

---

### Post by XxLeekxX on 2008-08-29
When I make fresh install of Hardy.  I install the broadcom driver this way:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

and then after, I manual install the radeon driver using this method:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Once i finish installing the ati driver and restart my comp, it just freezes.  I suspect this is because I installed 8.8 catalyst.  Someone told me it causes more problems.  I'll try 8.7 once I'm home from work.

---

### Post by josvanr on 2008-09-04
also having random lockup problems on my pb easynote bg 46 notebook. Happens
about once a day now. But I've only been experiencing these lockups since
10 days now, not before that. I update regularly, so don't know exactly which packages have been replaced since the lockups began.. No progress yet with this problem?

josvanr

---

### Post by Mighty_Joe on 2008-09-05
> **josvanr said:**
>  No progress yet with this problem

As has been noted many times [this thread]("http://ubuntuforums.org/showpost.php?p=5613170&postcount=377"), there are probably many bugs at work here.  The best thing to do at this point is either search [launchpad]("https://bugs.launchpad.net/ubuntu") for a bug that matches your symptoms and add a "me too" post or file a new report yourself. 
[Intrepid Ibex Alpha 4]("http://www.ubuntu.com/testing") (Alpha 5 any day now) is available for testing as well.

---

### Post by alejandro.mc on 2008-09-06
I'm not a programmer. But criteria dictates that if non of this random lockups occured in Gutsy, then what should be reviewed is everything that was modified to make Hardy, at least anything that may be causing it.

Second, what is the nature of this lockup? how is it that it can freeze the whole system, without leaving a possibility to access terminal or even to move the mouse, and worst of all how is it that it doesn't leave a log of what happened? how can this occur and not leave any trace in the system?

I've posted already in launchpad, thanks anyway, let's hope this doesn't last forever. Although it's true Intrepid is almost out (alpha), that doesn't mean the problem is going away. At some point it may appear again and we'll start another thread with the same people repeating the same posts.

Thanks, bye!!

---

### Post by zieglerj on 2008-09-06
I'm sure that the problem is in the video drivers. At least for NVIDIA users and the issues with ATI seem very similar. I've been weeks without a single lock-up after making the changes described here:

[http://ubuntuforums.org/showthread.php?t=892181](http://ubuntuforums.org/showthread.php?t=892181)

Not only have I been without freezes but alot of problems I was having with AWN and Compiz cleared up.

---

### Post by dad311 on 2008-09-07
Im also having lockups, but not so much random ones.

If I use Simple Backup, I get a TOTAL LOCKUP.
If I use Lemonrip, I get a TOTAL LOCKUP.


AMD64 FX-55,ASUS A8N5X, Nivdia 7600 GS, 2gig memory


What a pain.

---

### Post by francesco44 on 2008-09-07
I just performed all the updates, coming from holidays....After 20 minutes first total lockup freeze,hard reboot.....after 50 minutes....again.

I should stress two or three things:

1-I work on a thinkpad X30 without any customisation,

2-I made a fresh install 

3-Ubuntu is the only OS on my hard disk

Can anyone imagine something more "normal", more "regular". As many of us I have no time left to hunt a bug in the Amazon forest. I do not understand why the developpers cannot find the bug (or the bugs).If this happens to many of us...with very common computers, freshly and commonly set up....this has probably happened to someone at Canonical....so they have probably a machine with these phenomenas they can use as bench test.

For me all this is both impossible to understand,

Fortunately, I have other machines under OSX or windows(wich I dislike).

Hope is what is left to us!:confused:

---

### Post by sordello on 2008-09-08
I can see that my problem is a common one. There has been many different problems on this thread - it appears so anyway. I know where the problem starts on my computer but am still looking for a resolution. If I am using the ethernet cable plugged in the port on the laptop there is no problem at all- absolutly rock solid! If try to use the Wifi PCMCIA card it will completely freeze intermittantly. No warning or particular pattern... the mouse movement will stop and there is no response on the keyboard. I can only hold the power button until it shuts off.

The last time I saw a problem like this was while using my old Toshiba Satillite Pro machines with a NT type OS - win 2k or XP - while running a EVDO card. It took months to solve and turned out that the problem was caused by the EVDO ping times being too long and not being able to resolve the MTU.

I am sure it is not the same problem with the new machine but looks exactly the same. This is kind of frustrating - one machine works perfectly and the other will not.

Problem Computer: Toshiba L15-S104, celeron 1.3 ghz, 512mb ram, 60gb drive... problems with the D-link DWL-G650 PCMCIA Wifi - Madwifi version 
Kernel: 2.6.24-19 generic
GNOME: 2.22.3

Good Computer: ASUS EEEPC 701, Intel mobil CPU 900mhz, 512 mb ram, 16gb SSD
Working great with the preinstalled Atheros Madwifi using eeebuntu
Kernel:2.6.24-19-eeepc
GNOME: 2.22.3

I am off to search for answers... checking back later. Have fun... Bruce

---

### Post by alek01 on 2008-09-08
Hi,
My ASUS S96S freezes as well on Hardy. But it seems it ONLY FREEZES when the NVIDIA 8600gs Driver is insatlled. HOwever, that doesn't solve my problem 'cause I need the dual screen which requires the Nvdia card "on". Plus Although I've switched t o Ubuntu more than 2 years ago, I've never had crashing probems before. I simply cannot work with an aleatory system. I've seen and tried the fix from ZIEGLERJ but to no avail.
Any research done by Canonical on this? I will need to switch to an other Distri if I cannot reliably work.

Thank you,

Alain

---

### Post by keithieopia on 2008-09-08
Believe it or not this isn't just a Ubuntu issue, here's my post and research I've included on some other forums:
----------------------------------------------------------------------
OK, I'm posting this in hopes of getting a definite answer to this problem that's effecting A LOT of users. Not only is it annoying, but the developers seem to be whitewashing the issue... I found 4 related bug reports with the same symptoms in Ubuntu's launchpad, and 2 in Debian. I didn't even check Fedora, because it's obvious it's not related to a specific distribution.

_Symptoms_
When using any memory intensive program, such as Firefox 3, VLC, gnash, etc. the operating system complete freezes. It will not respond to keyboard, mouse, or SysRq commands; the screen just shows what was on it prior to the freeze. Waiting also is fruitless, the freeze was still present after 32 hours. The crash doesn't occur when the computer is completely idle with just Gnome or KDE running. The crashes seem to happen quicker when using Firefox 3, however the issue still happens with VLC and Firefox 2, so it's not related to these programs.

_Affected Systems_
I've confirmed this error is present in up-to-date installations of Fedora 9, Ubuntu Hardy Heron, Arch Linux, and Debian Lenny. Also, the same bug and behavior is present on the following computers (tested with all of the above distributions): Compaq Presario SR1303WM Desktop, Compaq 730us Laptop, and a Dell Dimension 2400.

_Possible Resolutions Used_
On all these systems, the memory has been tested with Memtest86+ and has passed with no errors. Also the boot parameters nolapic, noapic, acpi=off, noapm do not help the issue, as all of them have been tried alone and together, in all possible combinations.

Furthermore, I've run a system monitor and there is not a process eating 100% of the memory, up until the freeze everything appears normal. Furthermore, disabling powernowd or completely uninstalling it does not help (suggested in other forums)

Using the radeon, nv, nvidia, or fglrx XOrg drivers with their respective cards does not fix the issue (3 different ATI and NVidia where tested, for a total of 6 different cards). When using the vesa driver, the lockup still occurred, but the system was willing to accept a ctrl-alt-backspace to restart the XOrg server, the same freezing occurred.

The error is present in the 2.6.24 kernels and up, however I don't think it's kernel related as there's nothing useful in the log. The problems started with updates to the distributions around June - July. Prior to those months, all systems where working fine including those with proprietary nvidia and ati drivers.

Lastly, there are no useful messages in the system log and attempting to SSH into the frozen computer is not possible (SSH was installed properly and running). KDE and Gnome also produce the same freezing.

_Reproducing the Freeze_
For some reason certain webpages cause the freeze more often then others in Firefox 3. I've found [this page]("http://sites.target.com/site/en/corporate/page.jsp?contentId=PRD03-002477"), to cause it almost always. As stated above, this is not the only webpage and Firefox 3 is not the only program that causes the error.

_Possible Source_
I'm thinking it's some small package that nobody's thought to check, as there are no errors in the system log (Kernel, XOrg, etc) or anything. **It's not related to a graphics card** as many seem to conclude, due to all the drivers reproducing similar errors and the fact that the systems where working fine up until new updates where released.

Let's try to figure this out, it's definitely a major bug and a lot of people are turning from Linux due to it.

---

### Post by timllehner on 2008-09-08
I am experiencing some of the same problems.

65 bit Hardy

When I transfer largish files (100megs+) my USB keyboard and mouse lock up. Programs are still running but anything USB locks up. The file transfer wont complete and mouse and keyboard or unresponsive.
otherwise the system seems fine. I tried using a PS/2 keyboard and mouse and they don't lock up but the file transfer will still fail.

-T

---

### Post by keithieopia on 2008-09-08
> **timllehner said:**
> When I transfer largish files (100megs+)

This also causes the error, which is what I met by "memory intensive programs". It seems anything that takes up a good portion of the processor to do causes the lockup. 

I also added a [bug report to launchpad]("https://bugs.launchpad.net/ubuntu/+bug/267836") with my finding, as many users have commented erroneously that it must be a power manager or a proprietary display driver. If your issue is fixed by adding acpi=off, noapic to the boot parameters OR by changing your display driver, you have a different bug not related to this. Please feel free to comment on my bug report if you're experiencing the same issues I describe.

---

### Post by sordello on 2008-09-08
> **sordello said:**
> I can see that my problem is a common one. There has been many different problems on this thread - it appears so anyway. I know where the problem starts on my computer but am still looking for a resolution. If I am using the ethernet cable plugged in the port on the laptop there is no problem at all- absolutly rock solid! If try to use the Wifi PCMCIA card it will completely freeze intermittantly. No warning or particular pattern... the mouse movement will stop and there is no response on the keyboard. I can only hold the power button until it shuts off.

The last time I saw a problem like this was while using my old Toshiba Satillite Pro machines with a NT type OS - win 2k or XP - while running a EVDO card. It took months to solve and turned out that the problem was caused by the EVDO ping times being too long and not being able to resolve the MTU.

I am sure it is not the same problem with the new machine but looks exactly the same. This is kind of frustrating - one machine works perfectly and the other will not.

Problem Computer: Toshiba L15-S104, celeron 1.3 ghz, 512mb ram, 60gb drive... problems with the D-link DWL-G650 PCMCIA Wifi - Madwifi version 
Kernel: 2.6.24-19 generic
GNOME: 2.22.3

Good Computer: ASUS EEEPC 701, Intel mobil CPU 900mhz, 512 mb ram, 16gb SSD
Working great with the preinstalled Atheros Madwifi using eeebuntu
Kernel:2.6.24-19-eeepc
GNOME: 2.22.3

I am off to search for answers... checking back later. Have fun... Bruce


Actually I discovered  :lolflag: just froze up with the wifi in use while typing this message... short story is that noapic is not my problem. Never a problem on the wired Ethernet!

---

### Post by keithieopia on 2008-09-08
> **sordello said:**
> Actually I discovered  :lolflag: just froze up with the wifi in use while typing this message... short story is that noapic is not my problem. Never a problem on the wired Ethernet!

Mine still has problems with or without a wired connection. There's a bug report about ndiswrapper in lauchpad you should try to find.

---

### Post by timllehner on 2008-09-08
> **keithieopia said:**
> This also causes the error, which is what I met by "memory intensive programs". It seems anything that takes up a good portion of the processor to do causes the lockup. 

I also added a [bug report to launchpad]("https://bugs.launchpad.net/ubuntu/+bug/267836") with my finding, as many users have commented erroneously that it must be a power manager or a proprietary display driver. If your issue is fixed by adding acpi=off, noapic to the boot parameters OR by changing your display driver, you have a different bug not related to this. Please feel free to comment on my bug report if you're experiencing the same issues I describe.

Actually mine ONLY does it with USB. Or at least thats the only time I have encountered it. Never had any issue with any other program and I've done some pretty cpu and memory intensive tasks. If I keep a system monitor running in the background when it locks up I can see other processes still running and the CPU and memory working as per usual.If I can move 5+ gigs around on the HD and no probs, but move 500 megs from a usb and I'm toast. I can be up for days at a time but as soon as I try and transfer to or from USB.....

-T

---

### Post by keithieopia on 2008-09-08
Defiantly sounds like [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996"), good news for you is that it's been fixed in intrepid. 

With so many issues causing freezing in Hardy, I wonder if there was some industrial-sabotage by Micro$oft cohorts. :)

---

### Post by alek01 on 2008-09-08
Thank you for the info. However, I need to use my computer until Intrepid's release in nearly 2 months time. I simply cannot continue with Hardy. So, do I "downgrade to 7.10 or to something else? Plus, I do not have that much time for experimentation and O.S. tweaking these days. Stability comes before features.
Thank you again,
Al'

---

### Post by sengines on 2008-09-08
I am having exactly the same "freezing issues" as a lot of you on Hardy Heron 64bit. I really do think it's the kernel.

I have compiled drivers for my nvidia 6800 card and it froze after using memory intesive programs, I've tried the linux-restricted-modules as well and have had the same thing happen.

Since I have 8gigs of memory on this computer I don't want a 32bit system. Right now I am using etch but I prefer a non-freezing 100% working Hardy Heron install, someone really needs to get on this before more people jump ship being LTS and all, I think Intrepid Ibex should be the LTS since I'm sure they will have a change of kernel and a few othe things for Hardy.

I tried downgrading to ubuntu gutsy but the darn thing gives me an error. I used ubuntu minimal cd 64bit gutsy, it does not detect my hard drive (this happens on the 64bit version for me) works fine for 32bit.

If anyone can point me to a how-to for the issue I'm having with Gutsy 64 not installing, Ubuntu Gutsy boots into initramfs, I would really appreciate that since I can install anything except Gutsy 64 via cli.

---

### Post by keithieopia on 2008-09-08
I've found a semi-fix, no crashes... *yet*. Try doing this and see if it helps. Edit your XOrg.conf and add the following options to the driver section (doesn't matter if it's nvidia or ati):

```

Option "VideoOverlay" "on"
Option "TexturedVideo" "on"
Option "AGPMode" "8"

```

Now, reboot and see if you have 3D graphics (using a opengl screensaver is the quickest and best test) and see if it crashes/freezes. If it does crash or the graphics are "choppy", change the option AGPMode down to 4, restart X (alt-ctrl-backspace) and do the same test. If it's still "choppy" or it's freezing change AGPMode to 2 and restart X. 

This fix does make you're graphics performance a little less polished, but nevertheless seems to stop the freezing while allowing you to still use OpenGL and 3D rendering. I'm willing to make that small sacrifice for better stability.

If it works for you it's [this bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/133192"). The bug effects users of NVidia and ATI cards regardless of what driver is being used (vesa, etc). It seems that on a good portion of these cards, XOrg has problems setting the Speed of your AGP port; or at least that's what I interpreted the problem to be. 

If all else fails, mention it didn't work. I know how I felt with all this freezing and I'll stick around to see if I can still help.

---

### Post by mempman on 2008-09-08
The simplest solution is to roll back to a prior version of the kernel, if you have it installed.  When I upgraded to 2.6.24-19, I did so from 2.6.24-16.  Since the crashing has started, I have been using 2.6.24-16 without any problems.  This can be easily done by selecting the proper kernel version from grub during boot.

---

### Post by Mighty_Joe on 2008-09-09
> **keithieopia said:**
> It seems that on a good portion of these cards, XOrg has problems setting the Speed of your AGP port; or at least that's what I interpreted the problem to be. 

I saw [this post]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/141551/comments/39") about the same Xorg issue in another bug.  I think they may be onto something as my computer *appears* to work with [DRI shut off]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/227806/comments/7").  I'll have to test it when I get some free time. . .

---

### Post by janberk on 2008-09-09
Hehe... I've downgraded to Gutsy and no lock ups at all :D. And it's still good ;).

---

### Post by keithieopia on 2008-09-09
Well my fix seems to slow the frequency of freezing, but they're still occurring. 

I saw that bug report too, when I shut DRI off it did little to nothing for me :( I'm contemplating downgrading the kernel first to see if the error is present, and if it still is, downgraded completely to gusty.

For those of you that are having this issue still, PLEASE add it [to the bug report I created]("https://bugs.launchpad.net/ubuntu/+bug/267836"). Generally developers don't look in the forums, so to get their attention you have to go to their world of bug reports.

---

### Post by sengines on 2008-09-09
> **mempman said:**
> The simplest solution is to roll back to a prior version of the kernel, if you have it installed.  When I upgraded to 2.6.24-19, I did so from 2.6.24-16.  Since the crashing has started, I have been using 2.6.24-16 without any problems.  This can be easily done by selecting the proper kernel version from grub during boot.

This definitely took care of the problem, I've been hammering the computer all night and morning and no freezes or crashes. I am running ubuntu hardy 64bit 2.6.24-16-generic kernel, might want to change kernels instead of downgrading to gutsy.

Thanks for the tip.

---

### Post by Robin T Cox on 2008-09-09
As a very satisfied Gutsy user, I tried Hardy and had the same freeze problem as everyone else on this thread. Mine is a modest setup: Pentium III Coppermine plus Nvidia MX4000 graphics card. And I'm running 3 hard disk drives, one of which has Gutsy to itself.

I installed Hardy to the 10 GB first partition of my second (40GB) hard disk, but alas it kept freezing whilst Gutsy has kept soldiering on without any problems whatever. And when the freezes happen the logs never give any clue, and you can only regain control via the Alt-SysRq REISUB key combination - which, incidentally, throws my BIOS out of sync, so that it thinks I only have 1 hard disk until I completely power off the machine.

So I'm also convinced that it's some obscure kernel bug.

The more so, since I decided, in the end, to give Hardy on my second hard disk drive up as a bad job, and try Debian Lenny. Lenny is about to be released as the new stable Debian, and as it uses a later kernel than Hardy's 2.6.24 it seemed worthwhile investigating. Well, in its first incarnation it also used 2.6.24, and - surprise, surprise - it seemed to freeze too with that kernel. But then, after an update, it started to use 2.6.25, and the freezing stopped. Now it uses 2.6.26, and is as solid and reliable as Gutsy.

Kernel 2.6.24 is bad news for some of us, as the Hardy developers appear to have known all along.

[http://lwn.net/Articles/287829/]("http://lwn.net/Articles/287829/")

---

### Post by Mighty_Joe on 2008-09-09
> **keithieopia said:**
> I saw that bug report too, when I shut DRI off it did little to nothing for me :( 

It sounds like you and I are experiencing two different bugs.  I see you tried SSH'ing into a locked box and couldn't.  I can log into my computer when it's locked up and observe Xorg using 99% CPU.
Have you tried the Intrepid Alpha releases?  The kernel Intrepid uses is supposedly much-improved.

---

### Post by keithieopia on 2008-09-09
> **Mighty_Joe said:**
> It sounds like you and I are experiencing two different bugs.  I see you tried SSH'ing into a locked box and couldn't.  I can log into my computer when it's locked up and observe Xorg using 99% CPU.
Have you tried the Intrepid Alpha releases?  The kernel Intrepid uses is supposedly much-improved.

I was beginning to think that also, I think one of them is the AGPMode bug and another is a generic one. I've downgraded the kernel to 2.6.24-16 (still hardy though) and will see if it freezes. Then I'll try Intrepid's and see which one's more stable. 

Thank you though for confirming my suspicions that have been lurking in my head while I'm trying to figure this one out.

---

### Post by timllehner on 2008-09-09
I did a fresh install of Hardy so when I hit escape during grub I don't get any other kernel options.

Could someone explain how to roll back to 2.6.24-16 for someone pretty new to linux?

Thanks
T

---

### Post by keithieopia on 2008-09-09
> **timllehner said:**
> I did a fresh install of Hardy so when I hit escape during grub I don't get any other kernel options.

Could someone explain how to roll back to 2.6.24-16 for someone pretty new to linux?

Thanks
T

Type in a terminal:
```

sudo apt-get install linux-image-2.6.24-16-generic linux-ubuntu-modules-2.6.24-16-generic

```

It should add the necessary kernel to your grub boot menu automatically. Optionally you could then edit /boot/grub/menu.lst and remove the lines that link to the newer kernel and set the default to boot to the old one.

---

### Post by oxman on 2008-09-09
> **mempman said:**
> The simplest solution is to roll back to a prior version of the kernel, if you have it installed.  When I upgraded to 2.6.24-19, I did so from 2.6.24-16.  Since the crashing has started, I have been using 2.6.24-16 without any problems.  This can be easily done by selecting the proper kernel version from grub during boot.

This has not worked for me at all.

---

### Post by mempman on 2008-09-09
> **oxman said:**
> This has not worked for me at all.

How did you install ubuntu hardy heron (assuming you are running Hardy)?  Best way to go about this is by checking your /boot/grub/menu.lst file and seeing if there are any other linux kernel options.  Please post you /boot/grub/menu.lst file.


If that doesn't work, you can do what is recommended above:

> 
sudo apt-get install linux-image-2.6.24-16-generic linux-ubuntu-modules-2.6.24-16-generic


---

### Post by timllehner on 2008-09-09
I got the kernel installed and booted. However it did not solve my problem. Once again on the initiation of a USB file transfer my mouse and keyboard locked up on me. Debating if I should install a gust partition to try and rule out a hardware problem or try and figure out how to install Intrepids kernel.

-T

---

### Post by Mighty_Joe on 2008-09-10
I'm having really good results with [this solution]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/141551/comments/39").  I had Hardy up all night (9 hours!) with a conservative AGPMode = 2 and I've been using it for an hour with AGPMode = 4.  
Have a look at the [original bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/141551") and if it sounds familiar, you may have your solution.

---

### Post by sengines on 2008-09-10
> **mempman said:**
> How did you install ubuntu hardy heron (assuming you are running Hardy)?  Best way to go about this is by checking your /boot/grub/menu.lst file and seeing if there are any other linux kernel options.  Please post you /boot/grub/menu.lst file.

If that doesn't work, you can do what is recommended above:

I am running hardy heron amd64 and using the 2.6.24-16-generic kernel.
I got a lock-up today again everything froze except my mouse.

There must be more than just the kernel wrong with Hardy, I hope these bugs are squashed soon since I've been spending most of my time debugging.

---

### Post by alek01 on 2008-09-10
Thank you for the info. As I have no time these days, and need my computer running,I solved this problem by doing a fresh install of Ubuntu "Mint" flavor with Kernel 2.6.24.16-generic. The installation of the Nvidia driver was not as straight forward as they claimm, but now I have everything running with heavy 3D (full compiz on dual screen and no freeze at all. The machine's been "on" for 36 hours non-stop and works like a charm. Mint is a themetized version of Ubuntu with full Ubuntu ressources. I'll have an other look at Ubuntu "proper" when Intrepid comes out.
Good by for now

---

### Post by edb66083 on 2008-09-13
I finally got my Hardy working. I did a fresh install and added the 'noapic' to the boot parameter. I found this info at this page --> [Debugging IRQ Problems]("https://help.ubuntu.com/community/DebuggingIRQProblems")

It's been working great ever since.

---

### Post by johntc23 on 2008-09-14
I had thought the system freeze requiring hard reboot was tied to my older graphic card. After replacing card and reloading 8.04 system ran for several hours. Now it's freezing about every two hours, logs show nothing unusual happened. Last freeze I was in forums & opened system monitor total lockup. Still looking for answers, when it works I love it

---

### Post by clydehutson on 2008-09-14
I had been experiencing similar problems with Hardy, been through all the forums to no avail. Then the batteries in my M$ optical mouse went flat. Couldn't find any good replacements so I just plugged in a "normal" PS2 mouse and the problem went away. It wasn't the flat batteries because I charged up some good NIMH ones and reinstalled M$ mouse and problem was back. Can't explain it but been running perfectly for over a month now.

---

### Post by clayts450 on 2008-09-14
The last week has been hell on earth for my old faithful Thinkpad T22 running 8.04

First I was getting peculiar behaviour in Firefox (constant security messages) which rendered the browser unusable. Luckily I had Opera installed too, but I'm not a great fan of it to be honest.

This afternoon, I completely reinstalled Firefox and for a while everything was going swimmingly. 

However, my joy was shortlived - now I get a situation where the mouse and keyboard lock up after less than 30 minutes of use. And, sadly, it's not just restricted to Firefox - I wasn't even using it and the system locked up - hard reboot the only fix.

I checked obvious things like my RAM was inserted correctly, and booted into Windows for the first time in ages tonight - no lock ups, so it isn't hardware related.

I tried booting into 2.6.24-16 rather than -19, but it made no difference whatsoever.

I'm in the process of rethinking by Ubuntu installation - I love it to bits, but if an OS doesn't operate, what's the point ?

Why is it just this week that it's gone peculiar on me ? Answers on a postcard please....

---

### Post by johntc23 on 2008-09-14
Today when Hardy finally was installed 3 reboots it's working well. From the forum I'm encouraged that it's not only my system. Still can't find anything in the logs indicating a smoking gun. Maybe I'm overlooking the obvious. Any Ideas?

---

### Post by johntc23 on 2008-09-14
Hardy ran about 2 hours until attempting to open screen saver which froze system. Hard reboot twice and it's back up. Never tried gerty but if it doesn't do this I may be tempted

---

### Post by clayts450 on 2008-09-15
I have now tried switching to Xubuntu as I wondered whether the problem was simply my old Thinkpad T22 running at the outer edges of working fine in Ubuntu (384MB RAM, 900MHz processor), and indeed it is a lot more reliable **but** the freezing and locking up still happens....just not so quickly.

Bizarre,

---

### Post by mssg131187 on 2008-09-15
I'm having a problem with gutsy, i dont know why but all of a sudden it started freezing and now its doing it regularly like 5 or 6 times a day.  I've tried everything, but no success so now I'm just going to switch it to windows xp, atleast it never gave me this kind of problem.  So probably won't come to this site again, good bye ubuntu users, dissapointing end after 8 months of use...

---

### Post by pablopanama27 on 2008-09-15
I started Ubuntu as my first linux distro 1.5 months ago, and every now and then it freezes. I-ve done about everything. I have a biostar motherboard with standards audio and video and p4 with 512+265 ram. 160hd1, and 350gb hd2. no bluetooth or wireless on this desktop.

Today it froze 5 times. Restarting over and over is gonna kill my drives.
I-m using right know the cd to run ubuntu from it and save my docs from hd1 to hd2 in the meantime im downloading suse in my laptop to burn a dvd and go from there. Its sad. It may be the more popular distro right now but its definetely not the more stable one. I don-t wanna go to windows so i-ll try suse and if it works well, i guess i wont be coming back to ubuntu. Last time it froze in 5 minutes, didnt even give a chance to backup. I-ll be using it this way until suse downloads (4.x gb) . Ive noted from this forum i-m not the only one. Good Luck.

---

### Post by oxman on 2008-09-15
Well, I've been fooling around with this way too long. I'm about ready to either go back to Fedora or Dapper ;)

One thing I am noticing is that my xorg.conf file is unlike any I have seen in all of my linux years. I suspect that a new system has been intoduced without proper testing. I would like to see some of your xorg.conf files posted. I'm using a dapper box to post this. My "real computer" has been dead in the water for some time due to hardy.

---

### Post by BC7333 on 2008-09-16
> **Mighty_Joe said:**
> I'm having really good results with [this solution]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/141551/comments/39").  I had Hardy up all night (9 hours!) with a conservative AGPMode = 2 and I've been using it for an hour with AGPMode = 4.  
Have a look at the [original bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/141551") and if it sounds familiar, you may have your solution.

Might give this a try.. heck I've tried everything else in the world, even Intrepid for a couple of months with the same random hangs.

[   48.965715] agpgart: Detected an Intel 945GM Chipset.
[   48.967933] agpgart: Detected 7932K stolen memory.
[   48.988937] agpgart: AGP aperture is 256M @ 0xd0000000

is something that has been nagging in the back of my head for some while now.

I reverted from Intrepid with fresh Hardy install, updated, got the same hangs then did the following that has been somewhat successful with only occasional freezes so far:

used ndiswrapper and blacklisted ipv6 for my intel pro 3945 wireless card.

In admin services turned off apmd since it could not read my bios anyway or wasn't supported in my laptop.

2.6.24-21-generic

Disappointed that the logs show absolutely nothing..

I would like to find out more about this 'stolen memory' stuff..

Other interesting items in dmesg:

[   24.654488] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   24.654497] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   24.655697] PCI: Transparent bridge - 0000:00:1e.0

and

[   24.765594] Switched to high resolution mode on CPU 0
[   24.765794] Switched to high resolution mode on CPU 1
[   24.778579] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   24.778587] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   24.778594] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   24.778601] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   24.778608] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   24.778615] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   24.778622] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
[   24.778629] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   24.778647] system 00:05: iomem range 0xfed00000-0xfed003ff could not be reserved
[   24.778661] system 00:07: ioport range 0x680-0x69f has been reserved
[   24.778667] system 00:07: ioport range 0x800-0x80f has been reserved
[   24.778674] system 00:07: ioport range 0x1000-0x107f has been reserved
[   24.778680] system 00:07: ioport range 0x1180-0x11bf has been reserved
[   24.778686] system 00:07: ioport range 0x1640-0x164f has been reserved
[   24.778698] system 00:08: ioport range 0x6a0-0x6af has been reserved
[   24.778704] system 00:08: ioport range 0x6b0-0x6ff has been reserved
[   24.809595] PCI: Bridge: 0000:00:1c.0

---

### Post by Mighty_Joe on 2008-09-16
> **oxman said:**
> Well, I've been fooling around with this way too long. I'm about ready to either go back to Fedora or Dapper ;)

Don't get your hopes up.  I had the [same problem]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/227882") with Fedora 9.
And yea, that xorg.conf is pretty sparse.  I guess they expect everything to Just Work.  It doesn't on my hardware, but [flip the right switch]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/141551/comments/39") and you may be [in luck]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/141551/comments/40") like me.

---

### Post by Mighty_Joe on 2008-09-16
> **BC7333 said:**
> Might give this a try.. heck I've tried everything else in the world, even Intrepid for a couple of months with the same random hangs.


If it works (and this goes anyone else who [tries it]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/141551/comments/39")) don't forget to post your hardware and settings in the [original bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/141551").  The more feedback they get on this issue the closer they'll be to fixing it.

---

### Post by BC7333 on 2008-09-16
> **Mighty_Joe said:**
> If it works (and this goes anyone else who [tries it]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/141551/comments/39")) don't forget to post your hardware and settings in the [original bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/141551").  The more feedback they get on this issue the closer they'll be to fixing it.

It didn't :(

---

### Post by BC7333 on 2008-09-16
> **Mighty_Joe said:**
> Don't get your hopes up.  I had the [same problem]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/227882") with Fedora 9.
And yea, that xorg.conf is pretty sparse.  I guess they expect everything to Just Work.  It doesn't on my hardware, but [flip the right switch]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/141551/comments/39") and you may be [in luck]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/141551/comments/40") like me.

I am trying this at the moment, basically trying to tweak my bios accordingly.  Looks promising so far. Has been a few hours without a crash.

I also reinstalled the driver for intel pro 3945 abg using ndiswrapper since the kernel upgraded yesterday.  Thought it might be a good idea to do so.

---

### Post by oxman on 2008-09-17
> **Mighty_Joe said:**
> If it works (and this goes anyone else who [tries it]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/141551/comments/39")) don't forget to post your hardware and settings in the [original bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/141551").  The more feedback they get on this issue the closer they'll be to fixing it.

Didn't work for me either. I'm using a NvidiA 7900 GTO in a dual core opteron box (Nv bridge on the MB)

I do have a question about PnP. I have always installed linux with PnP turned off in the bios. Does anyone else do this? Those who don't. Any problems?

---

### Post by BC7333 on 2008-09-17
> **BC7333 said:**
> I am trying this at the moment, basically trying to tweak my bios accordingly.  Looks promising so far. Has been a few hours without a crash.

I also reinstalled the driver for intel pro 3945 abg using ndiswrapper since the kernel upgraded yesterday.  Thought it might be a good idea to do so.

Between AGPMode = 2 and tweaking bios a bit I'm having *some* but not perfect success..

One thing I did notice though, after I blacklisted iwl3945 driver, it froze up very frequently again..  dropped the blacklist and things stabilized..  I wonder how this could be related..

I'm using ndiswrapper for my intel pro 3945 instead of the native kernel driver which would also freeze up frequently.. Guess I will now have to try the native driver and AGPMode = 2 and see how things work.

In any case is a very strange and elusive bug, somewhat comforted that others have similar problems but sure wish we could finally kill it.

---

### Post by Mighty_Joe on 2008-09-17
> **oxman said:**
> Didn't work for me either. 

Crap.  That's my best guess.  

> **oxman said:**
>  Those who don't. Any problems?

I have the Plug and Play OS switch ON in my computer's BIOS.  Other than the aforementioned AGPMode problem, nothing.

---

### Post by morissette on 2008-09-17
So yeah im going to asusme since there are like 500 pages ere it still hasnt been fixed here is everythign i got from my system if anyone has any new ideas or found anything that might work.

Specs:
ASUS M2N-MX SE+ Motherboard
AMD Athlon 64 X2 Dual-Core Processor 6000+ AM2
AMD Socket AM2 Standard Cooling Fan
4GB DDR-2 800MHZ PC-6400
320 GB SATA2 7200rpm 16mb CACHE
320 GB SATA2 7200rpm 16mb CACHE
LG 20x DVD-RW DL
nVIDIA Ge-Force 6100

this is from my lsdev

Device            DMA   IRQ  I/O Ports
------------------------------------------------
0000:00:01.0                 0900-09ff
0000:00:01.1                 0600-063f 0700-073f 0e00-0e3f
0000:00:06.0                 0170-0177 01f0-01f7 0376-0376 03f6-03f6 ffa0-ffaf
0000:00:07.0                 e480-e487
0000:00:08.0                 d880-d88f dc00-dc03 e000-e007 e080-e083 e400-e407
acpi                      9 
ACPI                           0500-0503   0504-0505   0508-050b   0510-0515   0520-0527   08a0-08af
cascade             4     2 
dma                          0080-008f
dma1                         0000-001f
dma2                         00c0-00df
eth0                    220 
forcedeth                      e480-e487
fpu                          00f0-00ff
i8042                  1 12 
Intel                    10 
keyboard                     0060-006f
libata                14 15    0170-0177   01f0-01f7   0376-0376   03f6-03f6   d880-d88f   dc00-dc03   e000-e007   e080-e083   e400-e407   ffa0-ffaf
nForce2_smbus                  0600-063f   0700-073f
nvidia                   11 
ohci_hcd:usb1             5 
parport0                  7  0378-037a
PCI                          0cf8-0cff
pic1                         0020-0021
pic2                         00a0-00a1
pnp                          0230-023f 0290-029f 04d0-04d1 0500-057f 0580-05ff 0800-080f 0880-08ff   0900-097f   0980-09ff 0a00-0a0f 0a10-0a1f 0a30-0a37 0d00-0d7f 0d80-0dff 2000-207f 2080-20ff
rtc                       8  0070-0077
serial                       03f8-03ff
timer                     0 
timer0                       0040-0043
timer1                       0050-0053
vga+                         03c0-03df
XT-PIC-XT                 4 




my lsusb

Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 002 Device 001: ID 0000:0000 



And yes you've guessed it I crash like every 20 minutes so if someone could help me :)

And i have a kernel log at [http://members.cox.net/xxcrzy4youxx/kernlog.odt](http://members.cox.net/xxcrzy4youxx/kernlog.odt)

---

### Post by johntc23 on 2008-09-17
does your system take up to 3 reboots to load? other times loads perfectly in one? Can you tell me what to enter to get system to give hardware data such as you have listed here. Yeh just learning. Thanks for any help you could offer

---

### Post by morissette on 2008-09-17
the most ive had to do was 2 times. type lsdev in terminal for the devices and lsusb for usb devices.

---

### Post by oxman on 2008-09-18
> **morissette said:**
> So yeah im going to asusme since there are like 500 pages ere it still hasnt been fixed here is everythign i got from my system if anyone has any new ideas or found anything that might work.

Specs:
ASUS M2N-MX SE+ Motherboard
AMD Athlon 64 X2 Dual-Core Processor 6000+ AM2
AMD Socket AM2 Standard Cooling Fan
4GB DDR-2 800MHZ PC-6400
320 GB SATA2 7200rpm 16mb CACHE
320 GB SATA2 7200rpm 16mb CACHE
LG 20x DVD-RW DL
nVIDIA Ge-Force 6100


And i have a kernel log at [http://members.cox.net/xxcrzy4youxx/kernlog.odt](http://members.cox.net/xxcrzy4youxx/kernlog.odt)

Very interesting. I am using an asus MB also with two sata drives and an nvidia card.. You are the closest animal species to me. That's encouraging to me...I think :)

---

### Post by morissette on 2008-09-18
well i do my best unfortunately linux disagrees.

---

### Post by mgmiller on 2008-09-18
I also have an Asus mobo and 2 SATA drives using a single core AMD 64 3200+ cpu.  The only time my system freezes is if I plug in the USB cable from my UPS that reports the state of its battery.  With that in, it can freeze anywhere from 5 mins to a day.  Without it, the system has stayed totally stable.  I am running 32 bit Hardy, upgraded from....see my sig below, upgraded a lot.  

Anyway, I have noticed that xorg.conf has been rewritten a lot for Hardy.  Things that used to be in one section are moved to others now.  I have included the relevant portions ( I have omitted keyboard, mouse, wacom, etc.) of my xorg.conf file  I am using nvidia video and have compiz turned on without problems.

```
Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection
Section "Monitor"
    Identifier     "VX2235wm"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "VX2235wm"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    Option         "NvAgp" "2"
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1600x1200" "1440x1440" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "1600x1200" "1440x1440" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "1600x1200" "1440x1440" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "1600x1200" "1440x1440" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1600x1200" "1440x1440" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1600x1200" "1440x1440" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


```Notice that a lot of options that used to be in Section "Device" are now in Section "Screen".  

There is no mention of DRI anywhere in the file.  

Also, notice the AGP mode command for an Nvidia card at least  is "NvAgp" "2" rather than "AGPMode = 2"

Hope this helps someone.

---

### Post by Mighty_Joe on 2008-09-18
> **johntc23 said:**
> does your system take up to 3 reboots to load?

I ran into [this bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/229799") that describes boot failures when searching for a solution to my problem.  Try switching off DRI in xorg.conf:

```

Section "Module"
        . . .
        Disable "dri"
EndSection

```

If that fixes it, then it is likely an AGPMode problem as described in the last post in that bug.

---

### Post by morissette on 2008-09-20
finally got somehting i left the house and left it in TERMINAl and got

```
[21731.773035] Call Trace:
[21731.773061] [<f888b75c>] ehci_urb_done+0x5c/0xb0 [ehci_hcd]
[21731.773084] [<f888c53f>] qh_completions+0x24f/0x430 [echi_hcd]
[21731.773109] [<f888d0ae> ehci_work+0x51e/0x810 [ehci_hcd]
[21731.773132] [<c031b438>] mutex_lock+0x8/0x20
[21731.773149] [<c01bc2c2>] inotify_inode_queue_event+0x4a/0xf0
Then some more numbers with
ehci_irq+0x158/0x1c0 [ehci_hcd]
Usb_hcd_irq+0x2b/0x60 [usbcore]
Handle_irq_event+0x30/0x60
Handle_level_irq+0x7c/0xf0
Do_irq+0x3b/0x70
Sys_read+0x41/0x70
Common_interupt+0x23/0x30
Code: c6 8b f8 8b 74 24 04 83 c4 08 e9 79 dd a7 c7 89 f6 8d bc 27 00 00 
00 00 53 b8 6c c6 8b f8 89 d3 e8 12 dc a7 c7 8b 43 18 8b 53 14 <89> 42 
04 89 10 8d 43 14 89 43 14 89 43 18 b8 01 00 00 00 86 05
EIP: [<f889e793>] usb_hcd_unlink_urb_from_ep+0x13/0x30 [usbcore] SS: ESP 
0068:f45ede84
Kernel panic - not syncing: fatal exception in interrupt
```

can someone decipher this for me

---

### Post by oxman on 2008-09-22
That might be worth posting in a bug report.

---

### Post by alejandro.mc on 2008-09-22
Does someone have a solution for this random lockups???

It's been months now..

---

### Post by Mighty_Joe on 2008-09-24
> **alejandro.mc said:**
> Does someone have a solution for this random lockups???


I've said it [before]("http://ubuntuforums.org/showpost.php?p=5613170&postcount=377") and I'll say it again: there are probably many bugs at work here.  There isn't going to be a one-size-fits-all fix.
The best thing to do at this point is either search [launchpad]("https://bugs.launchpad.net/ubuntu") for a bug that matches your symptoms and add a "me too" post or file a new report yourself. 
[Intrepid Ibex Alpha]("http://www.ubuntu.com/testing")  is available for testing as well.

---

### Post by oxman on 2008-09-24
Just a heads up.

I did reinstall Dapper. Wow! It was so sweet and easy. 

Not to be contentious: I'm sorry, but posting a bug at [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu) isn't going to suffice Mighty Joe. What about us poor slobs that are on 24 baud rate dialup? We are unable to do the testing etc. Posting is important I agree but nothing is flowing down stream to us from there as far as an explaination and that does need to happen.

As far as there being multiple bugs, I tend to disagree. Sudden multiple problems from a new release just smacks of a single big problem. 

Watching and waiting... the grateful ox.

---

### Post by Mighty_Joe on 2008-09-25
Let's be contentious.  Liven up this thread a bit :)

> **oxman said:**
>  I'm sorry, but posting a bug at [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu) isn't going to suffice Mighty Joe. What about us poor slobs that are on 24 baud rate dialup? 

Dialup!?!? You poor guy. 
Seriously, tho, posting a bug in launchpad doesn't take any more bandwidth than posting here.  While you probably can't download each Live CD you can still contribute. The dev's don't follow the forums.  They do follow launchpad.  

> **oxman said:**
> 
As far as there being multiple bugs, I tend to disagree. 

I used to think Hardy Hangs were one big bug, but experience has proven me wrong.
You tried [my fix here]("http://ubuntuforums.org/showpost.php?p=5805820&postcount=445") and it didn't work for you.  I've been using Hardy for a week and haven't seen a hang.  I think that points to two different problems.

---

### Post by dad311 on 2008-09-25
After months of Hardy lockups I finally fixed my issue.  I purchased a new cheap motherboard (Foxconn NF4UK8AA-8EKRS $37.00@geeks.com).  Used my same CPU,memory and Nvidia card.  My old ASUS A8N5X MB would run everything linux dist perfectly, expect Hardy.  I could not rip DVDs or gzip files without an lockup.

Now Im ripping and gzipping that the SAME time.

---

### Post by Glucklich on 2008-09-25
Ultimately I'm suffering chronically from this issue. It wasn't a very big deal, once or twice occasionally. But the past week, it's becoming unsustainable. Like the original poster said, I'm not comfortable with resetting my laptop every time that happens, because sometimes a simple Ctrl+Alt+Backspace isn't enough. And I work very hard, fortunately it never happened during work but I can only wish it never will. Don't get me wrong, I love Linux and I would be very sad if I had to leave it but I really need to know if something is being done about this.
Sometimes the monitor just goes blank, sometimes it becomes gradually blank, sometimes it just freezes with what I was doing on it(sometimes I'm able to control the mouse and do the Ctrl+Alt+Backspace but sometimes I can't control the mouse and that's when I need to reset the system). Anyway, if this are not symptoms of the same issue please let me know.

---

### Post by smackenzie on 2008-09-26
I have a tower (HP Media Centre m1070n) and experienced intermittent lockups with Hardy about 3-4 times per week.  I was also unable to do Ctrl-Alt-Delete etc.

Though I use ethernet for my connection, I discovered that the tower also had a wireless card.  I changed wlan0 to "down" and now the machine runs for weeks on end with no issues.

Just one line in the terminal:

```
sudo ifconfig wlan0 down
```

---

### Post by deepaksubu on 2008-09-27
Just was about to fall in love with Ubuntu and then the FREEZE occured.
Hate these freezes...occur at the most important times...nothing works...no keyboard...no mouse...nothing.

last thing that i will try is to disable the wireless as suggested above...

otherwise am going back to XP.

---

### Post by danip on 2008-09-27
I am not sure if my problem is the same as what people are talking about, I just recently installed hardy on my old dell, its about 8 years old now, but whenever I try and hit the log out/reset/shut down button up in the top right corner hardy locks up.  I can still move the mouse around but nothing else works.  This problem only happens when I hit that button, I then have to do a hard reset.  Any suggestions?

---

### Post by mjoethvitnir on 2008-09-30
I'm not sure why but removing powernowd seems to have fixed my freezing problems. I've been going over two days now without a reboot and ordinarily that would never happen. I'm using an nvidia 7950GT graphics card with the 173 drivers installed via synaptic (nvidia-glx-new-envy).

> **rmccabe3701 said:**
> I installed hardy two days ago the freeze issue is unbearable.  My machine is a 
HP dc7700 2Gb RAM and an nvidia 5200 GeForce FX video card.  

I read on another thread that doing 
```
 sudo apt-get remove powernowd 
```

would help.  It did not.  I tried installing the nvidia driver directly from the nVidia website (not using the restricted driver manager) and this seemed to make things worse, i.e. the system would ALWAYS freeze up within 30-60 seconds of a boot.  So, I rolled back to the generic video driver and no more freezes -- however, this only supports a single monitor.  

So, the problem for me seems to be the incompatibility of Hardy with the nVidia driver (it worked in Gutsy).

Does anyone have any suggestions?

---

### Post by cent on 2008-10-07
I have the same problem. I've manage to switch in to the terminal right before the PC crashed.

here's what it printed out:

[[IMG]http://img142.imageshack.us/images/thpix.gif[/IMG]]("http://g.imageshack.us/thpix.php")[[IMG]http://img142.imageshack.us/img142/276/img0513modifiedingimpimkf7.th.jpg[/IMG]]("http://img142.imageshack.us/my.php?image=img0513modifiedingimpimkf7.jpg")

---

### Post by oxman on 2008-10-07
> **cent said:**
> I have the same problem. I've manage to switch in to the terminal right before the PC crashed.

here's what it printed out:

[[IMG]http://img142.imageshack.us/images/thpix.gif[/IMG]]("http://g.imageshack.us/thpix.php")[[IMG]http://img142.imageshack.us/img142/276/img0513modifiedingimpimkf7.th.jpg[/IMG]]("http://img142.imageshack.us/my.php?image=img0513modifiedingimpimkf7.jpg")

Have you filed a bug report at launchpad?

---

### Post by seijuuroo23 on 2008-10-07
I've been using Ubuntu for 1 year now and so far I was satisfied with my Gutsy install on my old Toshiba Satellite A60 laptop.
So when I bought a new computer last week, the first thing I did was to make a dual boot with of course the latest Ubuntu release, Hardy Heron. And then like everyone of you, I experienced this Hardy freeze stuff, it's really a bother.Random freezes occured VERY often, sometimes after a few second, maximum time was 1h or so... After 3 days searching for the answer, trying this and that, (powernowd, wireless, etc..) I gave up... on Hardy of course!
What's the point? 
I just upgraded to Intrepid (beta version) which is supposed to come out at the end of this month. And guess what? Everything is solved! My computer has been running for a few hour now, without a single freeze! It even solved other little problems I had with compiz (not relevant here, but still...)

So cheer up guys, The freeze problem has found a solution: it's moving to Intrepid! 

In my opinion, if everyone's freezing problem goes away by upgrading to Intrepid, they should just make it a lts instead of Hardy... Guess the developers won't do that but hey, that's just me talking... I'm definitely not going to upgrade when the post Intrepid version comes out!!
I'm just writing this because I wish someone had told me this yesterday when I was seriously thinking about ... putting up with Vista for a while and give up temporarily on my Ubuntu experience. 
Hope this helps some people out there. Don't forget Intrepid is not in its final version yet, so be careful if you decide to upgrade!

I'll be coming back at you in a few days to confirm if the freezes are definitely gone or not.


btw, my laptop:

Compaq Presario CQ50 105ef (cheap one!)
AMD Sempron SI40
Geforce 8200
2GB Ram

---

### Post by oxman on 2008-10-08
Thanks for the up beat report [seijuuroo]("http://ubuntuforums.org/member.php?u=679140") . That is good news. Keep us posted will you?

---

### Post by Skalman5 on 2008-10-08
> **seijuuroo23 said:**
> I've been using Ubuntu for 1 year now and so far I was satisfied with my Gutsy install on my old Toshiba Satellite A60 laptop.
So when I bought a new computer last week, the first thing I did was to make a dual boot with of course the latest Ubuntu release, Hardy Heron. And then like everyone of you, I experienced this Hardy freeze stuff, it's really a bother.Random freezes occured VERY often, sometimes after a few second, maximum time was 1h or so... After 3 days searching for the answer, trying this and that, (powernowd, wireless, etc..) I gave up... on Hardy of course!
What's the point? 
I just upgraded to Intrepid (beta version) which is supposed to come out at the end of this month. And guess what? Everything is solved! My computer has been running for a few hour now, without a single freeze! It even solved other little problems I had with compiz (not relevant here, but still...)

So cheer up guys, The freeze problem has found a solution: it's moving to Intrepid! 

In my opinion, if everyone's freezing problem goes away by upgrading to Intrepid, they should just make it a lts instead of Hardy... Guess the developers won't do that but hey, that's just me talking... I'm definitely not going to upgrade when the post Intrepid version comes out!!
I'm just writing this because I wish someone had told me this yesterday when I was seriously thinking about ... putting up with Vista for a while and give up temporarily on my Ubuntu experience. 
Hope this helps some people out there. Don't forget Intrepid is not in its final version yet, so be careful if you decide to upgrade!

I'll be coming back at you in a few days to confirm if the freezes are definitely gone or not.


btw, my laptop:

Compaq Presario CQ50 105ef (cheap one!)
AMD Sempron SI40
Geforce 8200
2GB Ram

I was ready to agree with you that Intrepid itself would solve this freezing issue until Today..

Upgraded from hardy to intrepid (alpha 4 i think) a few weeks ago solved the freezing's for me on behalf of the graphics (ati-drivers is not currently compatible with Xorg 7.4).

Yesterday (2008-10-07) i updated my system through the Update manager and today when i started my computer the freezes were back.

Same as before:
When evolution finished downloaded mail = Total system freeze
Pressing TAB = Total system freeze
Pressing CAPS LOCK= Total system freeze
Repeatingly pressing BACKSPACE = Total system freeze

The nightmare is back! :mad:

---

### Post by seijuuroo23 on 2008-10-08
I guess our freeze problem doesn't come from the same source then. If you do nothing at all, does it still freeze after a period of time? Because that's what happened with me.
I have all the latest updates for Intrepid, and the freezes are still not coming back. 
But just in case, I think I'll save an image of my partition in its actual state; you never know...

---

### Post by patrickballeux on 2008-10-08
I had these kind of problems on my old Averatec laptop.  Generally, a lock-up means a conflict betweed two devices for the same IRQ.

The solution in my laptop was to add on the boot line: "acpi=noirq"


Open (as root) the "/boot/grub/menu.lst" file, find the boot line that ends with "splash" and add this option.

I don't know if it will work, but it's worth a try.

Good luck!

---

### Post by seijuuroo23 on 2008-10-08
I guess life isn't perfect...
After a few updates, the freezes are still not coming back but... I've been experiencing some graphical bugs when compiz is enabled and I feel it's kind of slower. 
But still no freeze.

---

### Post by Skalman5 on 2008-10-11
Finally solved my freezing issue!

It had something to do with my pcspeaker.

[COLOR="Blue"][https://bugs.launchpad.net/ubuntu/+bug/224606]("https://bugs.launchpad.net/ubuntu/+bug/224606")[/COLOR]

Blacklisting the pcspeaker solved it for me:

```
sudo gedit /etc/modprobe.d/blacklist
```

Blacklist the pcspeaker in the end of the file:

```
#Blacklist PC-Speaker
blacklist pcspkr
```

Press save and reboot. :KS

---

### Post by chrismate on 2008-10-21
Downloaded the latest version of Hardy (8.04), 2.6.24-21, 3  or 4 days ago and all my freezing problems have completely disappeared.

---

### Post by euchrid33 on 2008-10-21
I had no problems with the original release of Hardy, but the point release (8.0.4.1) gave me freezes exactly as described here, always when I was using the wireless.  I've just installed the -rt kernel as recommended earlier, and it's fixed it beautifully.  Ubuntu's performance isn't as fast as it used to be, but I'll take that over freezes and hard restarts any day.

Now to try out 8.10...

---

### Post by houstonbofh on 2008-10-24
I had the freezing problem so bad that I needed an entirely new vocabulary!  Fixed it by a dist upgrade to Intrepid.  No other changes, and no freezes since.  Way to pick an LTS kernel...

---

### Post by adam_kimber on 2008-10-24
> **Skalman5 said:**
> The nightmare is back! :mad:

Welcome to my world. Hardy locked up repeatedly, so does Intrepid. :( 

> **houstonbofh said:**
>  Way to pick an LTS kernel...

Totally. LTS = stable in my book. Hardy is probably the worst ubuntu I have used.

Going to try Lenny to see if I get problems there.

---

### Post by ds3 on 2008-10-24
I'm using an AMD64 setup with Hardy. I had freezing problems earlier but uninstalled Compiz and they went away. However, when the kernel upgraded to 2.6.24.14-21 a few days ago and the xorg driver updated with it, they suddenly reappeared. I'm primarily seeing the problem when playing videos in fullscreen with Kaffeine, which previously was the most stable video option. However, I've also seen it using VLC. Any suggestions (other than just reverting to 2.6.24.13-19)?

Thanks.

---

### Post by adam_kimber on 2008-10-29
> **euchrid33 said:**
> I had no problems with the original release of Hardy, but the point release (8.0.4.1) gave me freezes exactly as described here, always when I was using the wireless.  I've just installed the -rt kernel as recommended earlier, and it's fixed it beautifully.  Ubuntu's performance isn't as fast as it used to be, but I'll take that over freezes and hard restarts any day.

Now to try out 8.10...

I concur. My freezing only started after 8.04.1. I do not use wireless but nVidia, which seems to be one of the culprits. I upgraded to 8.10, Intrepid and the freezes went away, until recently when some updates trashed it again. Going to install again and then see if it runs stable for a week without updates then I know that the culprit (for me) is in one of those updates. :P Process of elimination continues.

---

### Post by euchrid33 on 2008-10-29
> **adam_kimber said:**
> I upgraded to 8.10, Intrepid and the freezes went away, until recently when some updates trashed it again. Going to install again and then see if it runs stable for a week without updates then I know that the culprit (for me) is in one of those updates. :P Process of elimination continues.

I'm sorry to hear that.   I've upgraded to Intrepid and all the freezes have vanished.  If you do work out which update it is that causes the freeze please post it, though I fear that it'll be different for different systems :(

---

### Post by DozeyUK on 2008-10-29
I had the random freezing problem for ages before...ended up giving up and using Windows XP for ages.  However, my motherboard recently died and I had to get a new one (and got a new processor / ram as well).  And...NO MORE CRASHES.  I used Hardy for a few days without problem and then recently installed (fresh) Intrepid and that works perfectly as well!

My previous motherboard was an Asus A8N-E with an AMD X2 4800+ CPU and 2gb RAM.  Maybe it was some issue with the dodgy nforce chip or something?  I know that version of nforce wasn't the best...Although Ubuntu used to work fine on Gutsy and below...

Anyway, my new Intel based motherboard seems to have solved the problem.  Nothing I did on the previous one would fix the issue...it really was a total screwup system that I had to totally abandon.  Windows XP saved me for a while, but now I can thankfully use Ubuntu again for most things!

Does anyone NOT have an nforce setup with this problem?

---

### Post by euchrid33 on 2008-10-29
> **DozeyUK said:**
> I had the random freezing problem for ages before...ended up giving up and using Windows XP for ages.  However, my motherboard recently died and I had to get a new one (and got a new processor / ram as well).  And...NO MORE CRASHES.  I used Hardy for a few days without problem and then recently installed (fresh) Intrepid and that works perfectly as well!

My previous motherboard was an Asus A8N-E with an AMD X2 4800+ CPU and 2gb RAM.  Maybe it was some issue with the dodgy nforce chip or something?  I know that version of nforce wasn't the best...Although Ubuntu used to work fine on Gutsy and below...

Anyway, my new Intel based motherboard seems to have solved the problem.  Nothing I did on the previous one would fix the issue...it really was a total screwup system that I had to totally abandon.  Windows XP saved me for a while, but now I can thankfully use Ubuntu again for most things!

Does anyone NOT have an nforce setup with this problem?

You haven't changed wireless cards?  That seems to be the issue with most people.  Did the old mobo have an onboard graphics card?  Some people have suggested that the graphics card is also likely to be responsible.

---

### Post by DozeyUK on 2008-10-29
> **euchrid33 said:**
> You haven't changed wireless cards?  That seems to be the issue with most people.  Did the old mobo have an onboard graphics card?  Some people have suggested that the graphics card is also likely to be responsible.

I NEVER USED a wireless card :)  It's not an issue with Wireless at all :)  The old mobo didn't have onboard graphics either...It's definitely not the graphics card either as I'm using the same one now.

I'm pretty sure it's Nforce based motherboards as I've gone back about 20 pages and all I can see (where people have posted specs) they all have nforce based ones...mostly all Asus as well!

---

### Post by euchrid33 on 2008-10-29
> **DozeyUK said:**
> I'm pretty sure it's Nforce based motherboards as I've gone back about 20 pages and all I can see (where people have posted specs) they all have nforce based ones...mostly all Asus as well!

Huh, that's interesting.  I think that you might be right.  I'm not at my Ubuntu machine now, but I'd be curious to see who manufactured the mobo.  I'll check it out when I get home.

---

### Post by 2CV67 on 2008-10-29
I have hard freezes with caps lock & scroll lock flashing (as [http://ubuntuforums.org/showthread.php?t=832383](http://ubuntuforums.org/showthread.php?t=832383)).

According to Belarc Advisor, my (Acer T120) motherboard is E22M which does not seem to be Asus, does it?

---

### Post by Mighty_Joe on 2008-10-29
> **DozeyUK said:**
> I'm pretty sure it's Nforce based motherboards as I've gone back about 20 pages and all I can see (where people have posted specs) they all have nforce based ones...mostly all Asus as well!

Not quite.  I have a [Gigabyte 7ZXE Mobo with a VIA chipset]("https://bugs.launchpad.net/ubuntu/+bug/227882").  
There's more than one problem here.  Mine seems to be a [bad AGPMode in Xorg]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/141551").  I have yet to see anyone else use the same fix successfully, and several in this thread have tried.

---

### Post by MurphyWalker on 2008-10-29
Hi all.
I'm running Ubuntu 8.04.1 Hardy on an Acer Ferrari 3200, AMD64 Athlon, ATI Mob Radeon 9700, 1G RAM and Broadcom Wireless. FF3.

I noticed the system going to freeze randomely after installed xserver-xgl (plus libglitz-glx1 and libglitz1).

Performances went awfully down.

Particularly, the freeze happend when opening new tabs in FF3.

Seems to be solved removing xserver-xgl (plus libglitz-glx1 and libglitz1).

Performances araised but no more able to use ATI graphic accelerator.

It's ok: i don't have to go back to XP.

Hope this helps.

[edit]
Forgot to say that the screensaver went also back to work

---

### Post by oxman on 2008-10-29
weird double post. sorry

---

### Post by oxman on 2008-10-29
> **DozeyUK said:**
> 
My previous motherboard was an Asus A8N-E with an AMD X2 4800+ CPU and 2gb RAM.  Maybe it was some issue with the dodgy nforce chip or something?  I know that version of nforce wasn't the best...Although Ubuntu used to work fine on Gutsy and below...
Does anyone NOT have an nforce setup with this problem?

I really think you are on the money with this. I have the Asus A8N, AMD X2 opteron chip with 2 gigs of ram and yes the nforce chip is in the mix. Now suposedly the legacy 96 nvidia driver addresses this but it hasn't. 
Still, this is a relatively new board that runs as smooth as silk on Dapper....and I don't want to give it up yet.

I have a new hp lappy with an intel chip, nvidia car and 4 gigs of ram and it runs quite nicely on hardy.

I put in a bug report but I am still not getting results. I haven't updated to intrepid yet.

Will someone please iron this out!

---

### Post by pingwo on 2008-10-31
I do hope that at last I got this sorted. It's been a while and no nasty OS freezes on my desktop. What I have done is to install differen network manager. It was noticed that freezes on my Dell with AMD Athlon 64 X2 5000+ 2.6 Ghz always were happening when it was trying to attach to wireless network. The NM-applet - Network manager has many bugs (0.6.x ver)
I have installed WICD ([http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)) to solve my problem. WICD installation removes dodgy nm-applet for you..  so no worries.

---

### Post by Ahmed Kotb on 2008-11-02
i have been following this thread from a while coz my hardy freezez quite often...and no solution except hard reboot

i have just installed intrepid..
and i have noticed that it is a lot better and faster and there was no hangs like hardy...

However :( it freezes with me twice :
the first one ..it freezes while the screen saver was on..and i was only downloading a file..
the second one : i was watching a wmv movie on vlc...

so is it the same hangs problem of hardy ?? ( hardy was a disaster and iam afraid that 8.10 do the same )

specifications >>
mobo: MSI 865gvm3-v
processor: 3.06 GHZ celeron D
ram : 1X512 infineon ddr1 ram 400 mhz
vga : fx5200

it is desktop computer and i dont use any wireless adaptors..

hope this bug get fixed soon,
thanks

---

### Post by crunchyblack on 2008-11-04
> **seijuuroo23 said:**
> 


So cheer up guys, The freeze problem has found a solution: it's moving to Intrepid! 



Guess what genius, just because the problem went away for you doesn't mean it's a solution.  Search the forums for "intrepid freezing" and see how well your solution worked.  I'll even give you the answer without all the work: Your solution sucks almost as much as ubuntu, GOOD GAME.

By the way, If I open up a terminal and spam the TAB button it freezes EVERYTIME without fail. Retarded. Goin back to windows. It's been a year with not even a ******* response from this usless development team.

---

### Post by Ahmed Kotb on 2008-11-05
the hangs happens now more often in 8.10 and that is really annoying...

i have disabled compiz and there was no hangs till no but iam not sure that this cured the problem....

i also have noticed that the last lines in log files are the same after each hang..

```
syslog>>
Nov  6 01:05:41 ahmed-pc kernel: [  132.044008] eth0: no IPv6 routers present

user.log>>>
Nov  6 01:03:59 ahmed-pc pulseaudio[5422]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov  6 01:03:59 ahmed-pc pulseaudio[5424]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov  6 01:03:59 ahmed-pc pulseaudio[5424]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov  6 01:03:59 ahmed-pc pulseaudio[5424]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Nov  6 01:03:59 ahmed-pc pulseaudio[5424]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Nov  6 01:03:59 ahmed-pc pulseaudio[5424]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 48000 Hz.
Nov  6 01:03:59 ahmed-pc pulseaudio[5424]: alsa-util.c: Cannot find fallback mixer control "Mic".
Nov  6 01:04:23 ahmed-pc pulseaudio[5424]: module-x11-xsmp.c: X11 session manager not running.
Nov  6 01:04:23 ahmed-pc pulseaudio[5424]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Nov  6 01:05:31 ahmed-pc hp: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Nov  6 01:05:31 ahmed-pc python: io/hpmud/pp.c 627: unable to read device-id ret=-1

kern.log >>
Nov  6 01:05:41 ahmed-pc kernel: [  132.044008] eth0: no IPv6 routers present
```

i really hope some one fix (or at least discover ) a definite reason for this annoying hangs

---

### Post by Mighty_Joe on 2008-11-07
> **Ahmed Kotb said:**
> 
Nov  6 01:03:59 ahmed-pc pulseaudio[5422]: ltdl-bind-now.c: Failed to find original dlopen loader.


I've seen [problems with pulseaudio]("http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio+hang") reported, though I don't know if it would cause a complete freeze.  An easy way to rule it out would be to boot up a Kubuntu or Xubuntu live cd and see if it hangs.  They don't use pulseaudio, so if those distros hang, your problem is elsewhere.

---

### Post by crunchyblack on 2008-11-12
> **keithieopia said:**
> Believe it or not this isn't just a Ubuntu issue, here's my post and research I've included on some other forums:
----------------------------------------------------------------------
OK, I'm posting this in hopes of getting a definite answer to this problem that's effecting A LOT of users. Not only is it annoying, but the developers seem to be whitewashing the issue... I found 4 related bug reports with the same symptoms in Ubuntu's launchpad, and 2 in Debian. I didn't even check Fedora, because it's obvious it's not related to a specific distribution.

_Symptoms_
When using any memory intensive program, such as Firefox 3, VLC, gnash, etc. the operating system complete freezes. It will not respond to keyboard, mouse, or SysRq commands; the screen just shows what was on it prior to the freeze. Waiting also is fruitless, the freeze was still present after 32 hours. The crash doesn't occur when the computer is completely idle with just Gnome or KDE running. The crashes seem to happen quicker when using Firefox 3, however the issue still happens with VLC and Firefox 2, so it's not related to these programs.

_Affected Systems_
I've confirmed this error is present in up-to-date installations of Fedora 9, Ubuntu Hardy Heron, Arch Linux, and Debian Lenny. Also, the same bug and behavior is present on the following computers (tested with all of the above distributions): Compaq Presario SR1303WM Desktop, Compaq 730us Laptop, and a Dell Dimension 2400.

_Possible Resolutions Used_
On all these systems, the memory has been tested with Memtest86+ and has passed with no errors. Also the boot parameters nolapic, noapic, acpi=off, noapm do not help the issue, as all of them have been tried alone and together, in all possible combinations.

Furthermore, I've run a system monitor and there is not a process eating 100% of the memory, up until the freeze everything appears normal. Furthermore, disabling powernowd or completely uninstalling it does not help (suggested in other forums)

Using the radeon, nv, nvidia, or fglrx XOrg drivers with their respective cards does not fix the issue (3 different ATI and NVidia where tested, for a total of 6 different cards). When using the vesa driver, the lockup still occurred, but the system was willing to accept a ctrl-alt-backspace to restart the XOrg server, the same freezing occurred.

The error is present in the 2.6.24 kernels and up, however I don't think it's kernel related as there's nothing useful in the log. The problems started with updates to the distributions around June - July. Prior to those months, all systems where working fine including those with proprietary nvidia and ati drivers.

Lastly, there are no useful messages in the system log and attempting to SSH into the frozen computer is not possible (SSH was installed properly and running). KDE and Gnome also produce the same freezing.

_Reproducing the Freeze_
For some reason certain webpages cause the freeze more often then others in Firefox 3. I've found [this page]("http://sites.target.com/site/en/corporate/page.jsp?contentId=PRD03-002477"), to cause it almost always. As stated above, this is not the only webpage and Firefox 3 is not the only program that causes the error.

_Possible Source_
I'm thinking it's some small package that nobody's thought to check, as there are no errors in the system log (Kernel, XOrg, etc) or anything. **It's not related to a graphics card** as many seem to conclude, due to all the drivers reproducing similar errors and the fact that the systems where working fine up until new updates where released.

Let's try to figure this out, it's definitely a major bug and a lot of people are turning from Linux due to it.

Best post yet, great summary. I have yet to make any progress on this issue, I'm keeping posted though.

---

### Post by crunchyblack on 2008-11-12
> **oxman said:**
> Well, I've been fooling around with this way too long. I'm about ready to either go back to Fedora or Dapper ;)

One thing I am noticing is that my xorg.conf file is unlike any I have seen in all of my linux years. I suspect that a new system has been intoduced without proper testing. I would like to see some of your xorg.conf files posted. I'm using a dapper box to post this. My "real computer" has been dead in the water for some time due to hardy.

Ox how can you use a version of ubuntu even though it's "reached the end of it's life"??

---

### Post by oxman on 2008-11-12
It isn't easy ;) crunchyblack! But I have been able to use dapper to accomplish basic tasks without too much difficulty. I have done considerable amounts of work of various venues using dapper.

The problem arises when I need a new application that dapper won't upgrade to. That's what caused by problem in the first place. In this case I was hoping to use open source software for GPS applications, 3D mesh modeling by interfacing with the GPS software, rendering and animating. Dapper can do most of that but the GPS software required the latest versions of some libs. I've been crippled ever since as far as my project goes.

I've been running hardy on my laptop without any problems but my pc is the one with the real rendering power and it will not run hardy without hard lockups. I'm hoping to try intrepid soon to see what it will do.

---

### Post by Dirius on 2008-11-13
Hello together!
I am experiencing the same problem, freeze about twice per day now and the problems seems to become worse over time. It is hard for us to admit but I think everything looks like we are experiencing a Linux virus, and a serious one.

_Hardware used_
New Thinkpad X60 (Intel Core Duo CPU T2400, Mobile Intel (R) 945 Express) *No problems until beginning of October despite all updates also during June-July *. I therefore do not believe that the problem came through updates.

Sorry for that but I think we have to seriously consider this being a Linux virus.

---

### Post by Solomoriah on 2008-11-13
Virus?  In the absence of other evidence, it's a bit of a stretch.

---

### Post by oxman on 2008-11-13
> **Dirius said:**
> 
Sorry for that but I think we have to seriously consider this being a Linux virus.

Very unlikely that this is  a virus in the classical sense of the word. I have used the same CD to install and did the same updates that I did on my pc on my laptop without any problems.  I think it is a combination of hardware and software that is the problem.

---

### Post by Ahmed Kotb on 2008-11-15
just for the record..in Intrepid the hangs(that require hard reboot) are very rare unlike hardy...
also after configuring compiz to use "loose bindings" i didnt have any hangs at all :) ..

---

### Post by oxman on 2008-11-15
> **Ahmed Kotb said:**
> Intrepid the hangs(that require hard reboot) are very rare  ..
Good news. Can you post your hardware specs so I can compare them to mine?

---

### Post by Ahmed Kotb on 2008-11-16
> **oxman said:**
> Good news. Can you post your hardware specs so I can compare them to mine?

iam sorry but the freezes still happens :(
i didnt write the previous post till i was sure that there was no hangs (1 week without any freeze) but at the same day i had 2 freezes !!!

my humble computer specs.. 
----------------------------
mobo: MSI 865gvm3-v
processor: 3.06 GHZ celeron D
ram : 512 infineon ddr1 ram 400 mhz
vga : asus (nvidia) fx5200
HDD : 160 GB Samsung sata drive
---------------------------------------------------------------
i noticed also that the freezes in intrepid always happen in certain cases(not random like hardy)..when i try to display a movie from a ntfs partition it is guaranteed that i will have a freeze after 5 min..but when i choose loose bindings hangs become very rare..(happened only once)
also at the same day i had a freeze while browsing [www.stackoverflow.com](www.stackoverflow.com)

hope this information could help

---

### Post by oxman on 2008-11-16
> **Ahmed Kotb said:**
> 
vga : asus (nvidia) fx5200


I noticed that a lot of the hardware specs that have lockups have asus involved. That bums me out since i have an asus motherboard and a nvidia video card.

---

### Post by Dirius on 2008-11-17
Doesn't seem to be Asus specific. IBM Lenovo Thinkpad X60 and X61 users had the same. See this for the 61: [http://ubuntuforums.org/showthread.php?t=969621](http://ubuntuforums.org/showthread.php?t=969621)

---

### Post by Ahmed Kotb on 2008-11-18
yes i think it is not an asus problem...
iam not an expert but i think this is a SATA hdd problem for the following reasons :

the kern.log always have those lines:

```
Nov 18 17:51:46 ahmed-pc kernel: [  763.032342] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Nov 18 17:51:46 ahmed-pc kernel: [  763.033000] sd 0:0:0:0: [sda] Write Protect is off
Nov 18 17:51:46 ahmed-pc kernel: [  763.033008] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov 18 17:51:46 ahmed-pc kernel: [  763.033968] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 18 17:51:46 ahmed-pc kernel: [  763.064393] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Nov 18 17:51:46 ahmed-pc kernel: [  763.064409] ata1.00: BMDMA stat 0x26
Nov 18 17:51:46 ahmed-pc kernel: [  763.064416] ata1.00: cmd 35/00:e0:ea:1e:54/00:02:12:00:00/e0 tag 0 dma 376832 out
Nov 18 17:51:46 ahmed-pc kernel: [  763.064418]          res 51/84:21:a9:21:54/84:00:12:00:00/e0 Emask 0x30 (host bus error)
Nov 18 17:51:46 ahmed-pc kernel: [  763.064422] ata1.00: status: { DRDY ERR }
Nov 18 17:51:46 ahmed-pc kernel: [  763.064424] ata1.00: error: { ICRC ABRT }
Nov 18 17:51:46 ahmed-pc kernel: [  763.064437] ata1: soft resetting link
Nov 18 17:51:46 ahmed-pc kernel: [  763.236384] ata1.00: configured for UDMA/100
Nov 18 17:51:46 ahmed-pc kernel: [  763.236409] ata1: EH complete 
```

those lines tend to repeat till the system totally freezes...also the hd lamp is on when the pc hangs,,which indicates IO operations..

also the udma2 is old and my sata hdd supports udma6.


i found those links talking about this problem..
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285595](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285595)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217920](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217920)

also a suggested solution for intrepid is to disable hpet (boot with hpet=disable) which is supposed to prevent hard locks..i have tested it and no hard-reboot hangs occured only soft lockups..

hope that could help...

---

### Post by oxman on 2008-11-18
> **Ahmed Kotb said:**
> 

hope that could help...

Encouraging. Thank you.

---

### Post by wincen on 2008-11-19
I"m using Ubuntu 8.04 and was experiencing a lot of freeze ups too.  The worst thing was the computer did not respond to ctrl+alt+backspace so I would have to power my laptop off.

My freezes occurred while using multimedia, especially while websurfing.  I did not look in my log files... so I can't verify this for sure, but I think I have have reduced them if not gotten rid of them. 

I got rid of the totem-mozilla (i think that's the package) plugin and replaced it with mplayer.  I also do not use Totem to play any media, i use VLC for everything.  I don't know if the problem is with totem, or maybe gstreamer, but so far so good.  I'll cross my fingers for the time being.  hope this may help other people.

fyi, if you want the latest version of vlc in 8.04 add the following to the end of your /etc/apt/sources.list file
```
## VLC Player
deb http://ppa.launchpad.net/c-korn/ubuntu hardy main #VLC Player
```

If you just want something stable I'd stick to 7.04 as that version was wonderful for me.... it's just a bit dated now.

---

### Post by Ahmed Kotb on 2008-11-20
this might be a workaround but i will still be afraid to use ubuntu in any serious work...
also vlc hangs with me..

another thing is the use of udma2 which is really so slow..

how can i force the system to use udma6 ???

---

### Post by Dirius on 2008-11-25
OK, still about three freezes per day, independent of activity. Becomes a serious problem of lost work.

---

### Post by Hudy on 2008-11-29
Boy, there are so many lockups happening to so many people with so many (seemingly) different causes that I just chose this thread to post my own experiences.

T60p, 2007-ad1, "core duo", ATI FireGL 5250 (X1400-like), 4 GB ram (2 Crucial 2GB, 200-pin SODIMM, DDR2 PC2-5300 memory module CT516999) - but this laptop only sees 3GB.

Ubuntu Hardy "8.04.1".  fglrx info:

xorg-driver-fglrx-dev 2:8.532-0ubuntu1
fglrx-kernel-source 2:8.532-0ubuntu1
xorg-driver-fglrx/hardy uptodate 1:7.1.0-8-3+2.6.24.14-22.53
fglrx-modaliases 2:8.532-0ubuntu1

In the past week or so, I've had a half-dozen or so lockups every day.  I simply cannot work this way.  Totally unpredictable - disk was active or inactive, wireless (AR5212) and wired (e1000) turned on or off in all combinations, made no difference.

I wrote a disk reader using DD, and read all the partitions on both disks, while monitoring hdd temps using another script.  I did this twice, overnight, and had no issues - though disk temps in the main bay got a bit high (122F) that's not unacceptable.

Then I ran memtest from the grub boot menu for about 36 hours.  14 passes, zero errors.

Oddly enough (distressingly so...), since running those diagnostics, and rebooting, I have not had a lockup. Duration has been about 25 hours as I write this.

Moving Target: there was a new kernel update delivered after I ran the above diagnostics: I'm now running 2.6.24-22.  The change list showed nothing that should/could have affected this problem or the symptoms.

Also odd is the fact that for a few weeks now, I cannot reboot the machine - it hangs while displaying the logo.  All I can do is power off & power back on - so I'm going to update the BIOS, which again has no relevant fixes - but what I'm thinking is that the linux kernel or a device driver somehow 'hosed up' the CMOS area of the BIOS.

Hey, it's worth a shot.  I'll report back after I've done this.

I wonder if this is like so many others in this 50-page thread - unique root causes with a common, horrific symptom: an unusable linux.  

/Bill

---

### Post by ryclegman on 2008-12-02
Hello,

Iv been having similar problems. Yesterday i was downloading something from the internet and it froze completely, my lights on my keyboard just flashed ect. I rebooted and went back to firefox and it crashed again because the file stated to download again. So another reboot and by now im pissed, so i let it do it again so i could see my system log with the error. I found this, not sure if it was to blame, but here it is....

> Dec 1 15:45:14 ryan-desktop avahi-daemon[5252]: Withdrawing address record for ******** on wlan0.
Dec 1 15:45:14 ryan-desktop avahi-daemon[5252]: Leaving mDNS multicast group on interface wlan0.IPv4 with address *********.
Dec 1 15:45:14 ryan-desktop avahi-daemon[5252]: Interface wlan0.IPv4 no longer relevant for mDNS.
Dec 1 15:45:14 ryan-desktop avahi-daemon[5252]: Withdrawing address record for fe80::218:f8ff:fe2d:f0f4 on wlan0.
Dec 1 15:45:14 ryan-desktop avahi-daemon[5252]: Joining mDNS multicast group on interface wlan0.IPv4 with address ************.
Dec 1 15:45:14 ryan-desktop avahi-daemon[5252]: New relevant interface wlan0.IPv4 for mDNS.
Dec 1 15:45:14 ryan-desktop avahi-daemon[5252]: Registering new address record for ******** on wlan0.IPv4.
Dec 1 15:45:15 ryan-desktop NetworkManager: <info> Clearing nscd hosts cache.
Dec 1 15:45:15 ryan-desktop NetworkManager: <WARN> nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))

Im not sure if this is to blame but thats it...

He are my specs**

500 gig sata HD Western Digital
4 gigs of DDR2 ram
64 bit intel core 2 quad
MSI mother board
MSI Nvidia 9600 gt

---

### Post by ryclegman on 2008-12-04
I figured it out its a wireless issue, and i used [https://help.ubuntu.com/community/Wi...er/Ndiswrapper](https://help.ubuntu.com/community/Wi...er/Ndiswrapper) .... We will see if it works
!!!

---

### Post by ryclegman on 2008-12-05
well reverting back to hardy wont do anything.... My method did connect the hardware, but never would actually allow access to the internet. THE problem is the WIRELESS DRIVER! linksys does not provide linux drivers

---

### Post by ryclegman on 2008-12-05
i switched to Linux mint and i haven't had any more problems!
__________________

---

### Post by Dirius on 2008-12-06
OK, the problem is getting to a degree that it is not possible any more to work with Ubuntu. Both yesterday and today it froze 10-15 times.

I have no idea whatsoever to do and it seems that the only remedy is to switch back to Windows. This is really hard after having used Ubuntu passionately for a long time. But after our discussions for months have let to nothing I do not really see a solution.

Is 8.10 a solution?

---

### Post by ryclegman on 2008-12-06
Im soryy but definatly not. after i upgraded i downloaded my updates and freeze ha ha. Yha and i have had 1 freeze with mint. hopefully they will be a bit more helpful. My guess is that it has to do with the wireless driver? what wireless card do you have?

---

### Post by 2CV67 on 2008-12-07
There are dozens of threads on this subject, with hundreds, if not thousands, of frustrated users. (Many now non-users...)

It has been going on for a year & there is no sign of a root cause, let alone a solution.

It concerns all flavors of Ubuntu & lots of other distributions.

Is it not time there was a  centralised task-force to fix this, before it sinks Linux for good?

I can workaround my problems by backports but could never recommend Linux to anybody else until this is fixed.

Come on guys !!!

---

### Post by mgmiller on 2008-12-07
I have 6 computers currently running 32 bit Ubuntu.  4 of them are on 8.04.1 and 2 are on 8.10.  They are a mix of 32 bit and 64 bit single and multi core cpus.  All are AMD, a mix of onboard SIS video, and discrete nvidia and ati cards both AGP and PCIe.  All of them use various Asus mobo's.  

My freezing experience is limited to 1 machine that would freeze variably from minutes apart to a day or so.  I traced this down to the usb connection to my UPS.  If it was plugged in, I would have freezes, if I unplugged it, no problems at all.  This was an Asus A8V deluxe mobo that I have learned is famous for USB weirdness.  Since changing that machine to an Asus M3N78 Pro, I have no problems with the UPS plugged in or any other freezing problems of any kind.  I have moved the old A8V deluxe to another area without UPS and it continues to chug along reliably.

The one common piece of hardware missing from all my machines is a wireless adapter.  I only use 100 MB or gigabit wired connections on all of them.

The wireless adapters seem to be a common thread here and across various distros.  It might be helpful if people with and without freezing but with wireless cards chime in with the chipset of the card and if it freezes or not.  Maybe that can pin it down a little better.  Maybe also wheather or not the ndis wrapper is used.

I also hold my breath when I recommend Linux to someone who depends on a wireless connection.  I hope this gets nailed down soon.  This has been going on for far too long.

---

### Post by 2CV67 on 2008-12-07
> **mgmiller said:**
> The wireless adapters seem to be a common thread here and across various distros.  It might be helpful if people with and without freezing but with wireless cards chime in with the chipset of the card and if it freezes or not.  Maybe that can pin it down a little better.  Maybe also wheather or not the ndis wrapper is used.

I am a frequent freezer (until backports) with Edimax 7128g RT2561 PCI card but no ndisWrapper.

---

### Post by Seks on 2008-12-07
I've upgraded to 8.10 and I still get crashes occasionally, I use nDisWrapper and compiz which are my two main suspects.

I get:
Complete lock ups where I can't even move the mouse. (no reisubing)
Lock ups where I can only use the mouse. (sometimes I can reisub)
And sometimes it just restarts spontaneously. (this is rare)

---

### Post by ryclegman on 2008-12-07
yha upgradig wont do a thing. 

Iv put numerous tries into all these thoughts. And I believe it has to do with wirless. if this happens to anyone who doesn't use wireless let me know. I have a hard time believing it has to do with nvidia, which has been brought up.

---

### Post by smolty on 2008-12-07
Currently have 8.10 on my desktop (no wireless) and a laptop (with wireless). I haven't had any probs with the laptop but I haven't really being using it so hard to say if this is sorted. My desktop freezes though. Can be 2-3 times a day or not at all for a week. V annoying. Any one know how to remove wireless related system files or do you think this is unlikely to change anything if I'm running on a wired connection anyway?? My graphics are ATI on both so no nvidia. I think both have asus motherboards though, desktop for definite.

---

### Post by oxman on 2008-12-07
I have installed 8.04.1 in two machines.

#1 Asus A8N, opteron 175, 2 gigs ram, nvidia 7900 gto, 1 ide hard drive and two sata drives, NO WIRELESS :

constant and continual lockups


#2 HP dv6000 series  laptop, 4 gigs ram, intel celeron, nvidia graphics card WIRELESS included:

I have not had a single lockup on this machine and I use the wireless many times. It is not a wireless problem for me.

I used the same install disk on both machines.

Someone on this thread challenged me to do a bug report. I did it. I recommend the same to all disgruntled users. I think the devs rarely read these threads but they do read the bug reports.

---

### Post by mgmiller on 2008-12-07
> #1 Asus A8N, opteron 175, 2 gigs ram, nvidia 7900 gto, 1 ide hard drive and two sata drives, NO WIRELESS :

constant and continual lockups

The A8N is the nvidia chipset version of the A8v that gave me problems.  Try unplugging all external USB devices except for mouse and keyboard and see what happens.   Also have the mouse and KB plugged into the mobo connectors closest to the Ps2 port.  
Perhaps try using the USB to Ps2 adapters for the mouse & KB to elliminate USB altogether for purposes of this test.

I suspect  all the socket 939 A8 series mobos had USB problems.
Some people had to disable USB in bios and use pci USB cards.
My mobo had many incompatibility problems with pci USB cards also.

---

### Post by vratnica on 2008-12-08
Here my case, perhaps it can shed some light on this mistery

I have acer laptop TravelMate 4101LMi with Intel Pentium Processor and ATI Mobility Radeon X600

First I installed 8.04 inside my XP, and it worked fine, but than because of my ignorance I uninstalled my wireless driver and since I didnt know how to fix that problem I installed Ubuntu again, but this time 8.10 and on its own partitions. And voila- the [COLOR="Red"]FREEZE[/COLOR] problems.

Usually I get them when I open some web page with flash content in it, although flash plugins didnt work, or when I am using Synaptic or installing something via deb packages

After several tries to find out where is the problem, I decide to try once more with 8.04. and again inside the Windows. And now again everything is working perfectly well.

So at the moment I would rather wait for the fix of the problem ( I still have my 8.10 installed on the comp), in meanwhile I use 8.04

---

### Post by ryclegman on 2008-12-08
> **oxman said:**
> I have installed 8.04.1 in two machines.

#1 Asus A8N, opteron 175, 2 gigs ram, nvidia 7900 gto, 1 ide hard drive and two sata drives, NO WIRELESS :

constant and continual lockups


#2 HP dv6000 series  laptop, 4 gigs ram, intel celeron, nvidia graphics card WIRELESS included:

I have not had a single lockup on this machine and I use the wireless many times. It is not a wireless problem for me.

I used the same install disk on both machines.

Someone on this thread challenged me to do a bug report. I did it. I recommend the same to all disgruntled users. I think the devs rarely read these threads but they do read the bug reports.
 Ic ..... what driver are you using for your Ethernet?  I just have a huge hunch it has to do with an internet issue...

---

### Post by ryclegman on 2008-12-08
> **mgmiller said:**
> The A8N is the nvidia chipset version of the A8v that gave me problems.  Try unplugging all external USB devices except for mouse and keyboard and see what happens.   Also have the mouse and KB plugged into the mobo connectors closest to the Ps2 port.  
Perhaps try using the USB to Ps2 adapters for the mouse & KB to elliminate USB altogether for purposes of this test.

I suspect  all the socket 939 A8 series mobos had USB problems.
Some people had to disable USB in bios and use pci USB cards.
My mobo had many incompatibility problems with pci USB cards also.

When my system crashes it happens with and without usb ports being used. And i use a pci linksys ralink.

---

### Post by ryclegman on 2008-12-08
> **vratnica said:**
> Here my case, perhaps it can shed some light on this mistery

I have acer laptop TravelMate 4101LMi with Intel Pentium Processor and ATI Mobility Radeon X600

First I installed 8.04 inside my XP, and it worked fine, but than because of my ignorance I uninstalled my wireless driver and since I didnt know how to fix that problem I installed Ubuntu again, but this time 8.10 and on its own partitions. And voila- the [COLOR="Red"]FREEZE[/COLOR] problems.

Usually I get them when I open some web page with flash content in it, although flash plugins didnt work, or when I am using Synaptic or installing something via deb packages

After several tries to find out where is the problem, I decide to try once more with 8.04. and again inside the Windows. And now again everything is working perfectly well.

So at the moment I would rather wait for the fix of the problem ( I still have my 8.10 installed on the comp), in meanwhile I use 8.04
Iv put numerous hours into this problem and still surprised to see no fix. Since then i have switched to Linux mint and iv had a lot better experience! Iv maybe had 1-2 freezes since my installation about 2 weeks ago. I used to have 2-3 a day with ubuntu! Weird i know. Im really happy with mint too!

---

### Post by oxman on 2008-12-08
[quote=mgmiller]The A8N is the nvidia chipset version of the A8v that gave me problems.  
I suspect  all the socket 939 A8 series mobos had USB problems.
[/quote]

I ran dapper on my system and never had a USB problem at all.


[quote=ryclegman]
 Ic ..... what driver are you using for your Ethernet?  I just have a huge hunch it has to do with an internet issue... 	  	
[/quote]

I have had no problems with Ethernet when I use it. But most of the time I am on dialup ;) and still had the hangs. (I live way out in the boonies)

I have used wireless and ethernet on my laptop using hardy without any hangs whatsoever.

---

### Post by smolty on 2008-12-10
Just found this:

 [http://halffull.org/2008/10/25/how-to-fix-an-ubuntu-crash/](http://halffull.org/2008/10/25/how-to-fix-an-ubuntu-crash/)

Has anyone tried this yet? I'm giving it a go so I will keep you informed!

I know its not exactly the same problem but sounds very similar. Another ASUS motherboard though. Anyone getting crashes without using ASUS?

---

### Post by jimv on 2008-12-10
I had freezing issues when Hardy when I was using it.  The solution I found was using the Realtime Kernel instead of the Generic one.

To do that, just open a terminal and run this command:

sudo apt-get install linux-rt

---

### Post by demosthene1 on 2008-12-10
Hardy was  freezing for me also but I think I fixed my problem.

I use an hfield Wi-Fire usb adapter. It is automatically recognized by Ubuntu and works great. But then occasionally on connecting my computer would freeze and need a hard reboot. This would happen with Network manager and Wicd. I now use the old RutilT program to manage my wifi and haven't had the problem since.

---

### Post by smolty on 2008-12-15
> **smolty said:**
> Just found this:

 [http://halffull.org/2008/10/25/how-to-fix-an-ubuntu-crash/](http://halffull.org/2008/10/25/how-to-fix-an-ubuntu-crash/)

Has anyone tried this yet? I'm giving it a go so I will keep you informed!

I know its not exactly the same problem but sounds very similar. Another ASUS motherboard though. Anyone getting crashes without using ASUS?

I hope I'm not speaking too soon but 5 days on and a total of 0 crashes!!I think the longest I have been is a full week without so this may just be luck that I haven't had any. Previous to me finding the tutorial I was having crashes every day, often 2 or 3 of them. I don't know if anyone has followed the tutorial and had different results to mine though. Fingers crossed this is a fix.

---

### Post by Cope57 on 2008-12-15
Don't you wish that all the people who sincerely want to help you could agree with each other?

---

### Post by vratnica on 2008-12-17
Solution for me was: Downgrade from 8.10 to 8.04

and I dont want to test some new solutions cause this works fine

---

### Post by smolty on 2008-12-18
>  Originally Posted by smolty  View Post
Just found this:

[http://halffull.org/2008/10/25/how-t...-ubuntu-crash/](http://halffull.org/2008/10/25/how-t...-ubuntu-crash/)

Has anyone tried this yet? I'm giving it a go so I will keep you informed!
> **smolty said:**
> I hope I'm not speaking too soon but 5 days on and a total of 0 crashes!!I think the longest I have been is a full week without so this may just be luck that I haven't had any. Previous to me finding the tutorial I was having crashes every day, often 2 or 3 of them. I don't know if anyone has followed the tutorial and had different results to mine though. Fingers crossed this is a fix.

I spoke too soon!!!! I'm still freezing! This is the most annoying thing.

---

### Post by exsencon on 2008-12-20
Wow, hardy seems to be really hard!
I was thinking about upgrading from Gutsy 7.10 which is working very well on my Dell laptop 1501 in multiboot with WinXP,OpenSuse 10.2,Dreamlinux and Slax.
The Gutsy grub bootloader commands in the MBR and I can choose which OS to boot.
Harddisk 120GB, 2GB RAM, ATI Radeon graphics, Broadcom 1390 wireless card.
Everything working fine except for a wireless glitch once in a while but easy to get back, no freezes.
Reading through all those posts about Hardy, I'll stick with gutsy for a while and wait for the next one.

---

### Post by DrMilo on 2008-12-21
This is crazy but it seems that the vast majority of my freezes happen on Saturday night! I'm going to try the powernowd thing, can't hurt.

---

### Post by DrMilo on 2008-12-24
> **DrMilo said:**
> This is crazy but it seems that the vast majority of my freezes happen on Saturday night! I'm going to try the powernowd thing, can't hurt.

Nope! 2 freezes since!

---

### Post by DrMilo on 2008-12-24
> **DrMilo said:**
> Nope! 2 freezes since!

I'm going to kill all the power daemons and what happens.

---

### Post by FAJALOU on 2009-01-14
DrMillo,
    How did it go???? 
I know that I have errors too, but I also have two wifi cards, so that could be an issue.  I also know that I turned of guifications (using pidgin-libnotify instead) and Animations in CCSM and I don't freeze up as much, let alone have a slow computer from the graphics :lolflag: .   But I would like to know results; see if it helped. Thanks.

---

### Post by DrMilo on 2009-02-09
> **FAJALOU said:**
> DrMillo,
    How did it go???? 
I know that I have errors too, but I also have two wifi cards, so that could be an issue.  I also know that I turned of guifications (using pidgin-libnotify instead) and Animations in CCSM and I don't freeze up as much, let alone have a slow computer from the graphics :lolflag: .   But I would like to know results; see if it helped. Thanks.

Hey there! Sorry I didn't check this sooner. No nothing improved. 

Now I know very little but it seems like I get a cluster of freezes after each kernel upgrade. There was an upgrade last week and I've had 3 hard locks since.

---

### Post by Seftel on 2009-02-11
My notebook running Hardy only freezes when I have heavy traffic on the W/LAN.  With wireless turned off and using the Ethernet port, it is stable.  Does anyone know if this has ever been reported as a bug?

---

### Post by Ahmed Kotb on 2009-03-05
the freezes that was reported in this thread has many different reasons...any way mine was due an i/o problems ( i get alot of sata errors then the system just hangs...)..after a long time i discovered that my psu is the reason when i replaced it,  I didn't get the sata errors and my system didnt crash since then,,,
hope that could help...

---

### Post by tmun52 on 2009-03-05
I've noticed that my system freezes whenever I download proprietary drivers for my ATI Radeon HD 3650 card, even after 4 fresh installs of 8.10 intrepid.  Anyone care to help solve this problem?

---

### Post by smolty on 2009-05-02
If you're using Hardy or Intrepid then you need to disable desktop effects. All my freezes stopped once I changed my visual settings to 'no effects'. Been using 9.04 since its release day with effects set to normal and not had one freeze so maybe this is something that has been fixed.

---

### Post by DrMilo on 2009-05-21
It's pretty conclusive now that it was my video card. I bought and installed a new one, mine was years old, and no freezes since. I shouldn't be so cheap!

---

### Post by oxman on 2009-05-21
> **Ahmed Kotb said:**
> the freezes that was reported in this thread has many different reasons...any way mine was due an i/o problems ( i get alot of sata errors then the system just hangs...)..after a long time i discovered that my psu is the reason when i replaced it,  I didn't get the sata errors and my system didnt crash since then,,,
hope that could help...

What were you using and what did you replace it with?

---

### Post by oxman on 2009-05-21
> **DrMilo said:**
> It's pretty conclusive now that it was my video card. I bought and installed a new one, mine was years old, and no freezes since. I shouldn't be so cheap!

What were you using and what did you replace it with?

---

### Post by DrMilo on 2009-05-22
> **oxman said:**
> What were you using and what did you replace it with?

Haven't a clue what I had but I got this:

[http://tinyurl.com/pet27b](http://tinyurl.com/pet27b)

---

### Post by DrMilo on 2009-06-17
Got 2 freezes, first since my previous post, on Monday Still an improvement but there's no pattern to it at all.

---

