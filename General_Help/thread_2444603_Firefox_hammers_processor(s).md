---
title: "Firefox hammers processor(s)"
date: 2020-06-01
forum: General Help
---

### Post by ChrisOfBristol on 2020-06-01
I've recently come back to my old favourite Ubuntu after using a couple of others during the U***y years. It looks great and is easy to use. However when Firefox is running it usually hammers the processor. If I watch a video (only 480p so not very demanding) or there is a busy webpage it does it. If I stop using Firefox but leave it running, something usually starts and hammers the processor. It isn't really usable because the fan is working at full power/volume. I'm very reluctant to go back to what I was on before so I'd like to fix it. I remember un-installing some stupid indexer that I hadn't asked for a couple of years ago and I can't see anything like that running. Is there something I can disable or remove from the OS, or have I got some strange setting in Firefox?

I can look in System Monitor Processes for anything obvious.

---

### Post by ajgreeny on 2020-06-01
Try adding ublock-origin if you don't  already use it; it can stop a lot of ads which use high-cpu animations and activities and it's  a first add-on addition for me.

---

### Post by CatKiller on 2020-06-01
> **ChrisOfBristol said:**
> If I watch a video (only 480p so not very demanding) or there is a busy webpage it does it.

By default all of the browsers on Linux have hardware-accelerated video decoding disabled. There's a build of Chromium that you can use that has support for it enabled. 

Websites run all kinds of arbitrary code: adverts, trackers, GUI stuff, and so on, and they run it on your machine so it's not them that needs to pay for the electricity. There are any number of extensions that you might choose to use to get them under control, depending on which parts you're most bothered by. All of the standard suggestions are good ones.

---

### Post by daniewicz on 2020-06-01
If you run google chrome is CPU usage better?

---

### Post by Autodave on 2020-06-02
Install *uBlock *like ajgreeny already advised.

---

### Post by poorguy on 2020-06-02
Post some system specs, processor, amount of memory, graphics card or integrated graphics adapter.

I run Ubuntu 20.04 on 2010 / 2013 desktops with a dual core processors and 4.0 GB / 8.0 GB memory with integrated graphics adapters and they run fine.


What other distros were you running before Ubuntu 20.04 and did this problem exist with those distros.

It may be that Gnome3 is to much for the hardware you have so perhaps a distro with a lighter user interface.


I run Ublock Origin and DuckDuckGo Privacy Essentials both work excellent imo.

---

### Post by ChrisOfBristol on 2020-06-02
**@poorguy**

chris@desktop:~$ lscpu
Architecture:                    x86_64
CPU op-mode(s):                  32-bit, 64-bit
Byte Order:                      Little Endian
Address sizes:                   36 bits physical, 48 bits virtual
CPU(s):                          2
On-line CPU(s) list:             0,1
Thread(s) per core:              1
Core(s) per socket:              2
Socket(s):                       1
NUMA node(s):                    1
Vendor ID:                       GenuineIntel
CPU family:                      15
Model:                           6
Model name:                      Intel(R) Pentium(R) D CPU 3.40GHz
Stepping:                        4
CPU MHz:                         2400.000
CPU max MHz:                     3400.0000
CPU min MHz:                     2400.0000
BogoMIPS:                        6783.33
L1d cache:                       32 KiB
L2 cache:                        4 MiB
NUMA node0 CPU(s):               0,1
Vulnerability Itlb multihit:     KVM: Vulnerable
Vulnerability L1tf:              Mitigation; PTE Inversion
Vulnerability Mds:               Vulnerable: Clear CPU buffers attempted, no mic
                                 rocode; SMT disabled
Vulnerability Meltdown:          Mitigation; PTI
Vulnerability Spec store bypass: Vulnerable
Vulnerability Spectre v1:        Mitigation; usercopy/swapgs barriers and __user
                                  pointer sanitization
Vulnerability Spectre v2:        Mitigation; Full generic retpoline, STIBP disab
                                 led, RSB filling
Vulnerability Tsx async abort:   Not affected
Flags:                           fpu vme de pse tsc msr pae mce cx8 apic sep mtr
                                 r pge mca cmov pat pse36 clflush dts acpi mmx f
                                 xsr sse sse2 ss ht tm pbe syscall nx lm constan
                                 t_tsc pebs bts nopl cpuid pni dtes64 monitor ds
                                 _cpl est cid cx16 xtpr pdcm lahf_lm pti

**MEMORY 4GB,** but there is a common BIOS bug that means only 3.4GB can be used.

chris@desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)

> What other distros were you running before Ubuntu 20.04 and did this problem exist with those distros.
I tried Mint Cinnamon briefly (too buggy, poor support), Mint MATE (fine), Ubuntu MATE (fine) and then for quite a while Ubuntu Budgie (Great).

>  It may be that Gnome3 is to much for the hardware you have so perhaps a distro with a lighter user interface.
I've heard that Gnome3 is resource hungry and I suspect that is the problem, but I'm reluctant to jump to conclusions without asking the experts.

> I run Ublock Origin and DuckDuckGo Privacy Essentials both work excellent imo.
I've installed both of those at the suggestion of posters on this thread, but they haven't made any difference.

---

### Post by ChrisOfBristol on 2020-06-02
**[COLOR=#000000]@ [/COLOR]**[**[COLOR=#000000]daniewicz[/COLOR]**]("https://ubuntuforums.org/member.php?u=2138650")[COLOR=#000000] Chromium isn't noticeably better.[/COLOR]

---

### Post by poorguy on 2020-06-02
Your amount of memory isn't listed.

I have a** pentium d processor an 820 smithfield **and I also have an **nvidia geforce 210 graphics card** worked great for running **Windows XP **back in the day.

From my experience a few years back my** pentium d processor** and my** nvida geforce 210 graphics card** and **4.0 GB of memory **in my desktop running Ubuntu 14.04 was a somewhat painful experience.

The **pentium d processor just doesn't have the power to run a resource heavy desktop such as Gnome **not to mention that youtube and most browsers eat up a lot of memory.

I'd try a lighter distro  **Lubuntu LXQT 20.04 **or **LXLE** both are excellent choices for under powered computers.

I'm using **Lubuntu LXQT 20.04 **on an old computer listed in this link where you can check out it's specs and it runs great.

[URL="https://ubuntuforums.org/showthread.php?t=2444335"]https://ubuntuforums.org/showthread.php?t=2444335


[/URL]P.S. I'm no expert. :smile:

---

### Post by ChrisOfBristol on 2020-06-02
@poorguy I assumed lscpu would include that. I've added it to the list above.

---

### Post by poorguy on 2020-06-02
> **ChrisOfBristol said:**
> @poorguy I assumed lscpu would include that. I've added it to the list above.

4.0 GB is the minimum for Ubuntu 20.04 .

I'd give LXLE or Lubuntu LXQT 20.04 a test drive and see how it works since you've had some good results with other lower resource demanding distros.


This tells me a light weight distro may be the best solution.

Post #7.
 ***"Mint MATE (fine), Ubuntu MATE (fine) and then for quite a while Ubuntu Budgie (Great)."***

---

### Post by GhX6GZMB on 2020-06-02
Alas, Firefox is a resource hog and has devolved into bloatware with poor memory management (needs a restart every few days to clear memory clogging). I always remove/purge it at once and install Opera instead. No issues.

---

### Post by ChrisOfBristol on 2020-06-02
@poorguy I did try Lubuntu years ago but didn't like either the interface or the basic applications that came with it. However that was quite a while ago, so it could have changed beyond recognition by now! I liked Budgie a lot, so would go back to that if necessary.

I should have checked the recommended system requirements, but they don't change much so I didn't bother. However I'm not convinced that's the problem. I've just played a YouTube video, both processors go to 100%, but the memory usage was only 70% without any swap being used (I have a swap partition even though that's not standard). That was with a few odds and sods loaded but not doing anything. With nothing else loaded (except of course System Monitor) the figures were 90% processor and 60% memory. Could it be related to either using the default display driver instead of the NVDIA one, or using Wayland instead of the default? I'm using Wayland because LibreOffice won't work using the default.

---

### Post by CelticWarrior on 2020-06-02
> Could it be related to either using the default display driver instead of the NVDIA one
Definitely.

> or using Wayland instead of the default
Not at all.

In a nutshell, you need Nvidia proprietary drivers but then Wayland can't be used (yet) so you must troubleshoot the Libreoffice problem.

---

### Post by poorguy on 2020-06-02
Open the additional drivers and see if you have the option to install the Nvidia driver and and see if that makes any difference nothing to lose by trying and then you would know.

According to this link this is the Nvidia driver (** 340.xx driver) **you need.

[https://www.nvidia.com/en-us/drivers/unix/legacy-gpu/](https://www.nvidia.com/en-us/drivers/unix/legacy-gpu/)

---

### Post by ChrisOfBristol on 2020-06-02
@Poorguy, @CelticWarrior and @ml9104
NVIDIA driver: I should obviously try this (I think I was using it but switched back to try to fix LibreOffice).
Opera: I think I've only ever tried that very briefly once years ago, so it's worth looking at.
Wayland: I don't understand the comment "Wayland can't be used (yet)" as it is an option on my login screen and I'm using it now.
Fixing LibreOffice: I have found a few bugs with very basic functions recently. My experience of posting threads on ask.libreoffice.org is that other posters tell me I'm wrong and sometimes imply I'm stupid - then a few months later someone realises I was right all along - it's easier to change the OS!

---

### Post by ChrisOfBristol on 2020-06-02
NVIDIA driver reduces CPU to 95%. 
Opera reduces it to about 65% which might be good enough. When dormant it's about 10% which is fine.

---

### Post by poorguy on 2020-06-02
> **ChrisOfBristol said:**
> 
Wayland: I don't understand the comment "Wayland can't be used (yet)" as it is an option on my login screen and I'm using it now.

I'll outright tell you I have no clue about Wayland so I'm no help.

> **ChrisOfBristol said:**
> 
Fixing LibreOffice: I have found a few bugs with very basic functions recently. My experience of posting threads on ask.libreoffice.org is that other posters tell me I'm wrong and sometimes imply I'm stupid - then a few months later someone realises I was right all along - it's easier to change the OS!

I've never used ***LibreOffice forum or ask.libreoffice.org  ***so I've no idea how they are and I've haven't had any issues using*** LibreOffice*** but then I only use ***LibreOffice-Writer ***and it seems to work OK for what I use it for.

> **ChrisOfBristol said:**
> 
-it's easier to change the OS!
 
Sometimes it seems that way and I've been there and done that a few times myself however I've always wound up going back and trying to find a solution.

What I've found to help me find a solution is being willing to break my Linux distro and pass or fail I'm going to learn something either way although I've had to reinstall my Linux more than I care to admit but I learn by doing.

I know enough about Linux to stay confused and I'm always learning something from ***Ubuntu Forums.***


***This link has a wealth of information and is an excellent resource imo.***

[https://ubuntuforums.org/showthread.php?t=2130640](https://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by GhX6GZMB on 2020-06-02
@ChrisoB:
Interesting to see metrics on this issue. Thanks for the comeback.

---

### Post by ChrisOfBristol on 2020-06-02
I think swapping to Opera may fix it, so I'll stick with that for a while.Thanks to all  the posters for their advice - and tact! I avoid another {nameless}  forum now because the aim of the posters appears to belittle other users  in order to inflate their own egos. On here by contrast people very tactfully asked for information I should have posted at the beginning, and very tactfully suggested trying another browser - which I should have thought of myself, but I'd just assumed it was a symptom of Gnome3 inefficiency.

---

### Post by Autodave on 2020-06-02
Wayland does not work with nVidia drivers.  If you are going to use nVidia drivers, do not log into Wayland.

---

### Post by ChrisOfBristol on 2020-06-02
@Autodave I was running Wayland when I switched to NVIDIA and nothing happened, so I assumed it was working, however I've just restarted to see whether the Wayland option came up it didn't. It must switch it off automatically so nothing to worry about. I now remember having to stop using NVIDIA to use Wayland to make LibreOffice work. No big deal as the change of driver didn't make a lot of difference to how much CPU Firefox used. Switching to Opera made 7x as much difference.

---

### Post by poorguy on 2020-06-02
> **ChrisOfBristol said:**
> Switching to Opera made 7x as much difference.

I'm curious how much processor and memory is Opera using.

---

### Post by ChrisOfBristol on 2020-06-03
@poorguy Firefox with NVIDIA used 95%, Opera with default used 65%. So NVIDIA saved 5% and Opera 35%, which is 7x as much. That was on YouTube video. On a a recent run of a sound file though, Opera was making a lot of noise (through the processor), so it may not be the answer.

---

### Post by poorguy on 2020-06-03
> **ChrisOfBristol said:**
> @poorguy Firefox with NVIDIA used 95%, Opera with default used 65%. So NVIDIA saved 5% and Opera 35%, which is 7x as much. That was on YouTube video. 
[/QUOTE}
Definitely an improvement and I may have to give Opera another look.

I knew Firefox was becoming more resource heavy and I imagine that Chromium and Google Chrome would be as much also but can't say since I don't use either.

[QUOTE=ChrisOfBristol;13962469]
On a a recent run of a sound file though, Opera was making a lot of noise (through the processor), so it may not be the answer.

I don't quite understand what you mean.
 Are you referring to fan noise such as the processor fan ramping up in speed.

---

### Post by ChrisOfBristol on 2020-06-03
Opera was using a lot of processor power, so the fans were making a lot of noise.

---

### Post by poorguy on 2020-06-03
> **ChrisOfBristol said:**
> Opera was using a lot of processor power, so the fans were making a lot of noise.

I don't know.

I'm still leaning towards the processor being the culprit and can't cut the mustard.

You've tried Ublock Origin and DuckDuckGo Privacy Essentials and that didn't seem to help.

You also never mentioned noticing any scripts trying to run or running in the background which can / will load a processor down.

---

### Post by ChrisOfBristol on 2020-06-03
Where should I look for such scripts?

---

### Post by poorguy on 2020-06-03
> **ChrisOfBristol said:**
> Where should I look for such scripts?

They will have a message appear at the top of the browser telling you a script is trying to run or is running and give you the option to stop it or to allow it to continue.

[https://support.mozilla.org/en-US/kb/warning-unresponsive-script](https://support.mozilla.org/en-US/kb/warning-unresponsive-script)

---

### Post by ChrisOfBristol on 2020-06-03
I tried two ideas from the link, running browser in safe mode made no difference, disabling hardware acceleration about 5% - but that's probably not really significant as I'm not doing a very strict test. You have made a good point though, I had problems with Gumtree a a while ago (maybe Chrome, probably Firefox). It was totally unusable, it seized up with the processor at 100% on Ubuntu Budgie. I think that was script(s) and I assume it is fixed now.

---

### Post by poorguy on 2020-06-03
**Gumtree** is a website that can have a lot of crap trying to load and run which is why I stay away from websites like that and that is what **Ublock Origin** is good for.

---

### Post by GhX6GZMB on 2020-06-03
I have a completely different idea (just thinking out of the box):
Have you opened your machine and physically cleaned the fans? This made an incredible difference on my machine.

---

### Post by poorguy on 2020-06-03
> **ml9104 said:**
> I have a completely different idea (just thinking out of the box):
Have you opened your machine and physically cleaned the fans? This made an incredible difference on my machine.

Good idea **pentium d processors** are know as** flame throwers** because of the** netburst architecture **they are notorious for running hot however can handle the heat from my experience.

---

### Post by ChrisOfBristol on 2020-06-03
I've done a longer test on Opera and the results were CPU 70%, memory 55% (no swap use).
GumTree has its problems, but I can't think of anything better.
Unfortunately Ublock Origin seems to stop Google Maps working. I probably ought to look for something better for this too - but Newton's first law applies.

---

### Post by ChrisOfBristol on 2020-06-03
@ml9104 That sounds like good sense, and it is within my technical ability. Getting the vacuum out too might be beyond it.

---

### Post by poorguy on 2020-06-03
> **ChrisOfBristol said:**
> 
Unfortunately Ublock Origin seems to stop Google Maps working. I probably ought to look for something better for this too - but Newton's first law applies.

I'm using Firefox-ESR browser and Google Maps works fine with Ublock Origin.


You should be able to allow Google Maps in Ublock Origin.

This may help.

[https://www.maketecheasier.com/ultimate-ublock-origin-superusers-guide/](https://www.maketecheasier.com/ultimate-ublock-origin-superusers-guide/)

---

### Post by poorguy on 2020-06-03
> **ChrisOfBristol said:**
> @ml9104 That sounds like good sense, and it is within my technical ability. Getting the vacuum out too might be beyond it.

I use an air compressor and blast my desktops clean with short blasts of air from the inside out.

---

### Post by ChrisOfBristol on 2020-06-04
@ml9104 Cough, splutter, choke! The CPU fan filter and the heatsink were 30-50% clogged up and the output slots were almost blocked up. My computer fan is now just ticking over and even on a video it is hardly audible. Occam's razor. Thanks!  @poorguy Firefox does use a lot of CPU so I will give Opera a good try too, it looks neat.

Thanks for your patience and all the suggestions. I'll abandon the sn*tty S***kE******e for my Ubuntu queries and stick with this site in future.

---

### Post by GhX6GZMB on 2020-06-04
> **ChrisOfBristol said:**
> @ml9104 Cough, splutter, choke! The CPU fan filter and the heatsink were 30-50% clogged up and the output slots were almost blocked up. My computer fan is now just ticking over and even on a video it is hardly audible. Occam's razor.

Hahaha! Sometimes the simplest things evade us. Thanks for the comeback, I'm pleased that this part of the problem is solved.

---

### Post by ChrisOfBristol on 2020-06-04
@mlp104 I consider the whole problem to be solved. It doesn't matter to me if the CPU is being hammered so long as it is doing the job and I can't hear it :)

---

### Post by ajgreeny on 2020-06-04
Great news! 
Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

### Post by ChrisOfBristol on 2020-06-05
@poorguy I'm having a look at Opera and it does look slick and use less processor power. However I have found that it doesn't use tags or at least import and preserve them in case I want to switch to another browser later. Apart from about 20 bookmarks on the toolbar I have only tags, about 500 all in 'Other Bookmarks'. It hasn't even imported those. *[Edit: I've now found them]* I have also found that I can only login to my forum account using Firefox and there is a stupid error on my profile page. The former issues make it unusable for me and the latter although not part of the application make me lose confidence that there is much support for it. Unless I get some clever fix from the Opera forum I'll have to abandon it and maybe come back and have another look in a couple of years' time.

---

### Post by GhX6GZMB on 2020-06-05
Menu > Bookmarks > Import bookmarks and settings. (you can also export the bookmarks).

I'm not certain what you mean by "tags".

The login issue might be because Opera has a built-in adblocker.

---

### Post by ChrisOfBristol on 2020-06-05
Sorry @ml9104 I should have posted that I have since found the bookmarks. I would have to convert all my tags to bookmarks and it would still be clumsy and slow to get at them. 

Used on forums a lot. I only discovered them in Firefox this year. Tags are something you add to a bookmarked page to indicate a subject. The main advantage over bookmarks is that you can have more than one tag. For example if I am translating the phrases for an application I would find it hard to decide whether to bookmark the relevant pages under "application-name" or "language-name", but with tags I can have both. They are also self-maintaining, so if I use a tag that doesn't exist it is automatically created and if I delete all the bookmarks with a tag, that tag is deleted. I have a pull-down menu on the top left of my bookmarks toolbar for them.

---

### Post by GhX6GZMB on 2020-06-05
Ah. Thanks for the explanation, I was not aware of this functionality and have never had a need for it.

This kind of stuff partially explains Firefox' obesity (but not it's miserable memory management).

---

### Post by ChrisOfBristol on 2020-06-06
@ml9104 Lol! I've just remembered that Ubuntu Forums uses tags. Tags for this thread are [20.04]("https://ubuntuforums.org/tags.php?tag=20.04"),                       [firefox]("https://ubuntuforums.org/tags.php?tag=firefox"),                       [processor 100%]("https://ubuntuforums.org/tags.php?tag=processor+100%25")

---

### Post by GhX6GZMB on 2020-06-06
> **ChrisOfBristol said:**
> @ml9104 Lol! I've just remembered that Ubuntu Forums uses tags. Tags for this thread are [20.04]("https://ubuntuforums.org/tags.php?tag=20.04"),                       [firefox]("https://ubuntuforums.org/tags.php?tag=firefox"),                       [processor 100%]("https://ubuntuforums.org/tags.php?tag=processor+100%25")

I'm sure you're right, but I don't see them anywhere.

Correction: just scrolled down to the bottom of this page (which I normally never do). There are indeed some "tags". I'll keep ignoring them, they do not improve my browsing experience.

---

### Post by ChrisOfBristol on 2020-06-06
I've added them to posts on forums but never used them to search for anything on forums. They are at the bottom of the image:

---

