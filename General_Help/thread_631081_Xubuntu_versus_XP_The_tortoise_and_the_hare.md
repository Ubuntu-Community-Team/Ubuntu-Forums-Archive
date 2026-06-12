---
title: "Xubuntu versus XP: The tortoise and the hare"
date: 2007-12-04
forum: General Help
---

### Post by revolutio on 2007-12-04
Here's the conundrum.  I have a dual boot of XP and Xubuntu.  My reasoning behind trying Linux after so many years using Windows was that I knew it to be far more versatile and had heard great tales of its speediness and conservative use of memory.  The tales of speed turned out to be fables.

Xubuntu runs slower than Windows XP in the majority of situations.  A basic problem with my video card was resolved which lead to the functionality of movies.  However too many other problems exist for me to justify starting a myriad of threads.  Given the all encompassing lethargy of this operating system on my computer (I have tried Ubuntu as well) I am working under the assumption that there is a fundamental conflict that is at the root of this problem.

Since I find myself wanting in technical know-how and experience I really can't chip in with any theories.  So I'll just post a partial account of the sluggishness and hope Spring is eternal.

**Thunar** - If a file browser was made with the Crysis engine, I'd still expect it to run faster than Thunar (probably an exaggeration but that is my sentiment).  Other file browsers have suffered similarly and those that were acceptably fast coped with thumbnails, which I am dependent on, poorly or didn't support them at all. Moving files from one folder to another takes nearly as longer than XP did to transfer the same file.

**Exaile** - While I don't want to rag on this particularly versatile music player, the fact remains that iTunes which I wished to escape was speedier and Winamp could beat it without breaking a sweat.  It performs its advertised functions but unbearably slow.  Other music players have performed comparably.

**VLC and MPlayer** - These run movies quite on par with XP, though it hardly justifies a switch.  The codec problems that infuriated me in Windows are mostly gone though.  However skipping around or performing any sort of operations in addition to watching the video cripples the playback and my computer's performance.  While I can watch video on the web using the Mplayer plugin, it is prone to seizing so profoundly that I usually have to kill the browser.

**Evolution** - Just plain slow.  Hadn't tried Thunderbird lately but I don't recall it performing much better.

Also my RAM usage rises steadily by the hour until, before too long, 500 mb is used while idle.

Lastly the start up time for programs (which I had hoped would be where Xubuntu shined) is as slow as or slower than XP.  I can measure the start up time of any program without any meter because counting mentally is quite sufficient.  The system options usually take around a second which I find fine.  Any other program takes at least 3 seconds to start with most around 5 seconds.

Maybe my expectations are too high for me to appreciate Ubuntu and its derivatives. But I'd hoped that my computer could easily handle an OS with such low listed required specs.
Anyway I don't know what else to bemoan so here are my specs.

AMD Athlon 64 3400+
1 Gb pc 3200 RAM
Radeon 9800 Pro
OS running on a Raptor 10,000 rpm 37.5 Gb hard drive
running at 1600x1200

please Help :confused:

---

### Post by Jussi Kukkonen on 2007-12-04
Sorry, no fixes here. Just noting that your machine should run any Ubuntu version without problems (I used a 800MHz machine with 256MB of RAM as my desktop until last month), so there's definitely a problem somewhere.

> Also my RAM usage rises steadily by the hour until, before too long, 500 mb is used while idle.
"Unused memory is wasted memory", in other words what you're seeing is normal: that's how linux memory management works. That memory should be available as soon as some other program wants it.

Things you could do:
* Analyze the slowness in more detail: do the programs seem to be doing something? Using lots of cpu? Excessive disk trashing? Could the slowness be a display problem (screen not updating)?
* check *dmesg* output -- maybe there are error messages related to your hardware

---

### Post by revolutio on 2007-12-04
> **Jussi Kukkonen said:**
> "Unused memory is wasted memory", in other words what you're seeing is normal: that's how linux memory management works. That memory should be available as soon as some other program wants it.
Cool, good to know.  I hadn't been diligent enough to notice if this increase actually coincided with worsening speed

> Things you could do:
* Analyze the slowness in more detail: do the programs seem to be doing something? Using lots of cpu? Excessive disk trashing? Could the slowness be a display problem (screen not updating)?
Alright some details.  CPU usage hits 100% on almost every action.  Though browsing through menus usually only takes about 30%.  The CPU stays at this load until several seconds after the program is loaded.  Obviously during this time, I there is little I can do since any additional actions such as opening another program seem to just add the wait times together. Thunar is the most guilty with my CPU bouncing like a pogo stick between 50% and 100% when just idling with it open.  Also if I try to quit certain programs such as VLC or Exaile they decide to keep running and leave the processor usage at 100%.  Seeing the CPU bar sitting there is my cue to open up the system monitor and kill the process.

The slowness isn't a display problem though I have noticed issues simply rendering any sort of movement of windows.  The movement can't be refreshing more than 2 times each second.  Downsizing or closing a window usually makes it go away in 2 or 3 distinct parts taking about 1 second.  XP does this under high load and it was an ugliness I hoped to escape.

To put it simply, there is a delay after every action and this varies in length.  Windows will sometimes come up on time but their contents take quite a few seconds to appear.  Especially in the case of file managers.

> * check *dmesg* output -- maybe there are error messages related to your hardware
Checked, no blatant error messages but I could post the entire output if you think it might help.

Thank you for your prompt response

---

### Post by revolutio on 2007-12-07
:/ guess I'll try installing other distros and report back whether or not it was just a failing of Xubuntu.

DSL, Fluxbuntu, and Hard Puppy are up next.

---

### Post by HermanAB on 2007-12-07
Compare your Ubuntu DNS settings with your Windows DNS settings.  Chances are that you have a lame DNS server as the default in Linux /etc/resolv.conf.

Cheers,

H.

---

### Post by revolutio on 2007-12-13
> **HermanAB said:**
> Compare your Ubuntu DNS settings with your Windows DNS settings.  Chances are that you have a lame DNS server as the default in Linux /etc/resolv.conf.

Cheers,

H.
Forgive my ignorance, but what would my DNS settings have to do with file manager speed?  Or is this a different DNS?

Also the resolv.conf document is blank.

---

### Post by AbtZ on 2007-12-13
I assume weird DNS settings may somehow eat all your systems available processing power. How that happened in a fresh install, is beyond me though.

Have you tried running a 64-bit version of *buntu?

I'm running Ubuntu with similar specs to you, and while I wouldn't say it's faster than XP, it's definately not slower. Apart from that, Ubuntu is also a lot prettier.

---

### Post by yaknowwat on 2007-12-13
most likely something wrong.

on regular ubuntu me usage is on avarage less than 350mb

only time it went higher was on 7zip compression benchmarking on wine and that topped at about 660mb

normal CPU usage for me never reaches more than 15% only in benchmark intense things does it go much higher.

Hardware.

2GB RAM
2.1Ghz 65nm AMD 64 x2

on x86 ubuntu


though I'll admit something is up with Xubuntu I tried to install and it wouldn't install about 10 minutes to load desktop.

This was on. a 196mb RAM, 400Mhz(or higher haven't checked) processor

---

### Post by revolutio on 2007-12-27
Though I've pretty much gone back over to XP I've kept a Xubuntu partition just to tinker with this problem since it is eating at my mind.  Well I was watching the cpu load monitor today when Thunar was open and I noticed it had a pulse. The cpu usage bounces between 25% and 95% load in a perfectly regularly beat (about once a second).  This is when I am not doing anything with Thunar it is just sitting open in the background.  Once again, if anyone has any ideas on the subject let me know, I'd love to honestly be able to move from Windows some day.

---

### Post by tgalati4 on 2007-12-27
Xubuntu should fly on your machine.

Try this, in a terminal

>sudo apt-get install htop

>htop

Report what is taking up your CPU cycles.  Linux is supposed to take back those CPU cycles that Windows constantly steals.

---

### Post by revolutio on 2007-12-28
> **tgalati4 said:**
> Xubuntu should fly on your machine.

Try this, in a terminal

>sudo apt-get install htop

>htop

Report what is taking up your CPU cycles.  Linux is supposed to take back those CPU cycles that Windows constantly steals.
I'm glad to hear confirmation that I am not crazy in thinking Xubuntu shouldn't be nearly so slow.

So I tried out htop with Thunar running.  At any given time 18-40% of my CPU load is being placed on /sbin/mount.ntfs* followed by /usr/lib/gamin/gam_server which holds "steady" at between 11 and 20% CPU load. This is confirming a suspicion I had had which was that Linux wasn't playing nicely with the NTFS partitions I have. I should note that while idle with Thunar it is open to my home folder which is not on an NTFS partition.

So I guess the question is now is can I get Ubuntu to love NTFS and if so how?  And why does it have that steady pulse in CPU usage...

Thanks for the reply.


*more specifically: "/sbin/mount.ntfs /dev/sdb1 /media/sdb1 -o rw,unmask=007,gid=46"

---

### Post by pyronaut on 2007-12-28
i think the issue is with the gam_server i recall a long time ago something like this happeneing. you might want to google this and probabaly end up removing the package. if you are running XFCE then you might have some issues of memory leaks especiialy with the XFCE desktop and XFCE menu-plugin.
      however i would run top and see what that says in terms of processor usage. another thing might be to also to run gnome-system-monitor which is a GUI based monitor and it'll let you knowwhats going on both in terms of memory and CPU

---

### Post by kerry_s on 2007-12-28
i always thought xubuntu did xfce4 like crap, you should try a different distro with xfce4. i have debian xfce4 on 1.2ghz 512ram and it runs like as fast as xp.->
[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso)

for others-> [http://distrowatch.com/](http://distrowatch.com/)

---

### Post by DeadZedz on 2007-12-28
You're just better off with xp on your 500Mb memory PC (just my long-time experience).
wolvix should be faster than xp, maybe also some other slackware based distro.
*buntu or any other Debian based distro doesnt run slower than xp.
Linux can be awkward for a beginner, it may even break down sometimes, some software might not work, hardware support is worse than xp etc.

---

### Post by revolutio on 2007-12-28
Given the issues with gam_server that showed up on htop I tried things that [this thread](http://ubuntuforums.org/showthread.php?t=210329) suggested to no avail.  However killing the gam_server process entirely does seem to drop my processor usage to normal levels and stop the pulse.  I'm not really sure what the consequences of this are but for now there seem to be no problems and the Thunar sluggishness is largely gone.  Is there a way to keep gam_server from running?

---

### Post by Craigus on 2007-12-28
Well, you could remove gamin, but I'm not sure what that would break.

---

### Post by revolutio on 2007-12-28
> **Craigus said:**
> Well, you could remove gamin, but I'm not sure what that would break.
I could do that but then I'd also have to remove xubuntu-desktop, xfdesktop4, thunar, file-roller, python, and my first-born apparently.

---

### Post by kelvin spratt on 2007-12-28
I run Xubuntu 32bit and it is over twice as fast as xp no problems with ntfs, Are you running virtual disc or Hd install. Try the 32bit version use the alternative disc to install,  My computer was  booted up at 6am 27th its now 9.56pm 28th UK time, User memory 136mb of 2gb.I,m only surfing at the moment it was higher earlier today as Was processing when I first start up ram runs at about 90mb. You may have problems with you graphics card that will cause lots of problems. If its using system ram instead of its built in ram. or its not rendering correctly. I used Envy to download and install drivers for my ATI card Envy also does the Nvidia drivers as well. On another note your cpu should max out when opening programs unless its throttled other wise it would take a lifetime to open anything. I don't think you have hardware problems as windows performs Ok, Thunar should be very fast after the first opening after booting should be instant under 1sec well it is on mine, The slowest prog to open for me is OpenOffice that takes 8secs after bootup then under 2secs till next boot up, Fire Fox is 5secs then under 1sec till next boot up, Gimp 6 sec then about 4secs as it always looks for new plug ins, I now this as I helped with a survey with rooty last week Subject speed of light distros, I hope this does help you to make your mind up with your next move. Remember some distros are faster but a lot are very hard on the eyes. Good luck

---

### Post by tgalati4 on 2007-12-29
It's funny how even when Windows isn't running, it's stealing your CPU cycles.  I don't have any NTFS partitions so I haven't experienced this issue.

Linux Mint 4 XFCE (based on Gutsy) does a decent job with XFCE configuration and compositing without compiz.

---

### Post by revolutio on 2007-12-29
My computer is still running quite smoothly and, while I'd love to blame Windows, the problem was inexcusably with Xubuntu, specifically the gam_server application.  It was checking all ntfs drives for changes what must have been a few dozen times every second.  Maybe that searching isn't problematic for ext3 file systems but it flat out couldn't handle ntfs ones efficiently.

I'm hoping that is the the last of this problem.  The gam_server changes I mentioned previously seem to have actually kicked in after a restart so I don't have to disengage the program every time.  I set it so that it only scans once ever 20 seconds.

Next up on the problem lists - why Flash plugins in Firefox are so slow and how do I employ my monitor's rotating function without MagicRotation.

Thanks for all the input everyone.

---

