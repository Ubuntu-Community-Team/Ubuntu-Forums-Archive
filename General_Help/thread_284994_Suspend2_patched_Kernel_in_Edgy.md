---
title: "Suspend2 patched Kernel in Edgy"
date: 2006-10-26
forum: General Help
---

### Post by Treviño on 2006-10-26
I'm posting here to continue the closed thread from &#8220;old&#8221; edgy forum section: [http://ubuntuforums.org/showthread.php?t=272508](http://ubuntuforums.org/showthread.php?t=272508)

As I said I'd like to open a repository with suspend2 i386 kernels for edgy, to make kernels I'll start from the linux-source-2.6.17 debian source package (I said this to answer to *David Corrales*)...
I've just done this for my self under dapper (ehm I used a dapper system powered by a patched edgy kernel :D)

Anyway I'm a little titubant about the *linux-restricted-modules* packages :-k... I mean, if I continue using the same kernel version (not in deb file, obiouvsly) *maybe* it isn't needed to build these packages too :rolleyes:, becouse the ones from standard ubuntu repositories should works...
So, I'm asking to those where using the old dapper suspend2-kernel repository... Did you used restricted modules? If you did, did they work?

THanks!

---

EDIT: Packages are at [http://3v1n0.tuxfamily.org/dists/edgy/suspend2/index.html](http://3v1n0.tuxfamily.org/dists/edgy/suspend2/index.html)

---

### Post by Hobbes on 2006-10-26
I hope you don't have to update restricted-modules, b/c if you do then I couldn't use it, since I need custom restricted-modules to use nvidia beta drivers.

Thanks for your work, Im subscribing to this thread and hope to try out suspend2 once you get it all worked out :)

---

### Post by Sayonara123 on 2006-10-27
I'm still using the suspend2 Patched Kernel for Dapper. I would like to upgrade to the new release, but suspend2 is a must for me. The old style suspend does not properly work on my laptop but suspend2 is working great! :)

@Treviño
I've read in the other suspend2 thread, you are looking for additional space for hosting. How much resources (space, traffic) do you think you would need? I may provide you a space on my server for hosting/mirroring your project. :)

---

### Post by Treviño on 2006-10-27
Thanks for supporting... If you want a 2.6.17 kernel patched for dapper I've one, I could send it to you...

About hosting.... I must ask to tuxfamily if they can upgrade my space, btw I think I'd need about ~20Mb for each image (that are just 386 - if wanted (?) - and generic in edgy), ~10Mb for the headers and if you want them, about 40mb for linux-source.

So about 90mb...

---

### Post by Sayonara123 on 2006-10-27
> **Treviño said:**
> Thanks for supporting... If you want a 2.6.17 kernel patched for dapper I've one, I could send it to you...


Thank you, but I would prefer a suspend2 patched kernel for edgy. ;)

90MB are no problem for me for hosting. I also have enough traffic, I can provide. So, if you should have a problem with your hoster, or need a mirror, just let me know. :)

---

### Post by jbinto on 2006-10-27
Looking forward to it. I find it rather ironic that now with the improvements in booting via upstart, booting cold is faster by a few seconds than resuming from hibernate in swsusp.

I have to admit, I thought for sure Edgy would use suspend2. That's quite unfortunate.

Thanks for your contribution, I'd not know where to begin -- the debian way of the kernel is foreign to a gentoo native such as myself.

---

### Post by Sayonara123 on 2006-10-27
I'm also impressed how fast the new release boot up, but suspend still has a big advantage. I don't need to log in to start the desktop and I have everything back again like I left it. ;)

---

### Post by lorimer on 2006-10-27
I am just converting from gentoo to Ubuntu Edgy.  So far so good, but swsusp2 would be quite the nice feature to add.  I don't claim to know Ubuntu, but coming from gentoo I have compiled my fair share of kernels.  Let me know if there is anything I can do to help with this.

---

### Post by Edulix on 2006-10-28
I'd like also to get suspend2 for ubuntu. for the time there are no packages available... can you please tell us what are the steps to download, compile and get it working in edgy? :D

---

### Post by reacocard on 2006-10-28
Fantastic to hear someone is going to do this. In the meantime, could you post instructions for compiling a kernel w/ suspend2? Thanks.

---

### Post by David Corrales on 2006-10-29
Treviño, they closed the board right after I posted :(
I read a bit more about suspend2 and it indeed has a new program to suspend-to-ram.
I really need something reliable when suspending to ram while using the fglrx driver in my laptop. It's a waste of resources to shutdown completely, then booting back up again.

---

### Post by petr.fischer on 2006-10-30
Sigh... is there any news about "unofficial" edgy apt repository with kernel and support packages (scripts, usplash) with suspend2 stuff compiled in? Thanks for info.

---

### Post by reacocard on 2006-10-30
> **petr.fischer said:**
> Sigh... is there any news about "unofficial" edgy apt repository with kernel and support packages (scripts, usplash) with suspend2 stuff compiled in? Thanks for info.

Not yet. If I could figure it out, I'd do it, but idk how to apply the patch.

---

### Post by Treviño on 2006-10-30
Sorry about "sleeping time" :P, btw the past night I've compiled the suspend2 patched kernel... It works well, btw I've to upgrade some scripts based on those from dapper repository.

The only problem I got is that the userui_usplash doesn't work in my edgy (maybe becouse I use usplash 1024x768 ? :o Who knows...)!
Anyway that's only a visualization problem, the system suspends well; btw fbsplash and standard text works!

The latest thing... I've not tested suspension to ram (how to make it via command line? :o)

See you later; I hope to post the debs in few hours, btw I don't know if  I've enough space for the -386 kernel too... I'll start with the -generic (also if I've compiled both)

Bye!

---

### Post by petr.fischer on 2006-10-30
Very good news! Thanks for this work - I am really anxious now :)

---

### Post by Rui Pais on 2006-10-30
> **Treviño said:**
> ...
The only problem I got is that the userui_usplash doesn't work in my edgy (maybe becouse I use usplash 1024x768 ? :o Who knows...)!
Anyway that's only a visualization problem, the system suspends well; btw fbsplash and standard text works!
Same here. But i'm still fighting  with fbsplash. Mine it's not working... 
> 
The latest thing... I've not tested suspension to ram (how to make it via command line? :o)

change hibernate conf file to:
PowerdownMethod 3

or create a copy of conf file with PowerdownMethod 3 and name it something like hibernate.sleep and do:
```
sudo hibernate -F /etc/hibernate/hibernate.sleep
```
(there should exist an appropriate file already, ram.conf, on recent versions of hibernate, but i still use my old one...)

Btw did suspend-to-ram work with your generic kernel? 
For some mysterious reason for me no 2.6.17 kernel for me worked till now. 2.6.18 only work on suspend-to-disc and 2.6.16 work fine but are, strangely, very hard to compile on edgy...

---

### Post by Treviño on 2006-10-30
Regarding fbsplash method, it works well here... I've made also some splashes for Ubuntu/Kubuntu some time ago... If I finish them I'll upload...
> **Rui Pais said:**
> Same here. But i'm still fighting  with fbsplash. Mine it's not working... 

change hibernate conf file to:
PowerdownMethod 3

or create a copy of conf file with PowerdownMethod 3 and name it something like hibernate.sleep and do:
```
sudo hibernate -F /etc/hibernate/hibernate.sleep
```(there should exist an appropriate file already, ram.conf, on recent versions of hibernate, but i still use my old one...)

Btw did suspend-to-ram work with your generic kernel? 
For some mysterious reason for me no 2.6.17 kernel for me worked till now. 2.6.18 only work on suspend-to-disc and 2.6.16 work fine but are, strangely, very hard to compile on edgy...
Thanks for the tip... I always made the suspend on Disk :)
Here it works really well... 

It suspends normally (I mean... It shows the normal suspension process, like saving data, atomic copy and so on - is this rigth?), then when I press the power-on button (or any other keyboard button) I get immediately back my desktop :)

---

### Post by reacocard on 2006-10-30
Great to hear you've made progress! I look forward to having this.

Is there any chance of getting instructions on how to do this? I'd like to tweak my kernel settings a bit from the default, but I can't figure out how to apply this patch. :-k

---

### Post by Treviño on 2006-10-30
It's quite easy.... I've started to write here how to do it but, unfortunately I've lost what I've written :(... Now I've no more time, so if it isn't a problem for you I'll place an how-to in next days...

---

### Post by reacocard on 2006-10-30
> **Treviño said:**
> It's quite easy.... I've started to write here how to do it but, unfortunately I've lost what I've written :(... Now I've no more time, so if it isn't a problem for you I'll place an how-to in next days...

That's fine. I can wait.

---

### Post by Treviño on 2006-10-30
I've news about usplash... As I said before, edgy usplashes themes doesn't work with suspend_usplash ui, so I've thought that this could be due to the new usplash 0.4 used in edgy... So I tried to load a dapper usplash file and it works...
So, actually I'll add to the usplash_userui some &#8220;old&#8221; themes, waiting for a patch for suspend2-userui to support new themes...

---

### Post by mariner09 on 2006-10-30
Have you posted anything yet?

If so, where?

---

### Post by lighty14 on 2006-10-30
Turns out I'm fairly rusty on patching kernel sources. I have the kernel sources downloaded, and I have the suspend2 patch, however, I am unable to run patch successfully. If someone has some insight, that'd be great.

I just want to be able to suspend and hibernate please!!!:mrgreen:

---

### Post by Sayonara123 on 2006-10-31
@Treviño 

do you already have some files for us, we can try out? I can't wait to test it out. :D
Remember, if you need webspace for your files, I can provide. :)

---

### Post by Rui Pais on 2006-10-31
> **Treviño said:**
> Regarding fbsplash method, it works well here... I've made also some splashes for Ubuntu/Kubuntu some time ago... If I finish them I'll upload...
yes i made some for me too that i use in dapper and they load fine, manually. 
My edgy simply don't load them at system startup... out of curiosity, which splashutils are you using? (i tried the ones i use in dapper, and the latest for debian, but both failed)
> Thanks for the tip... I always made the suspend on Disk :)
Here it works really well... 

It suspends normally (I mean... It shows the normal suspension process, like saving data, atomic copy and so on - is this rigth?), then when I press the power-on button (or any other keyboard button) I get immediately back my desktop :)
eh eh  it's nice isn't it? Once one get used to suspend-to-ram it quickly becomes a must. 
There are ,unfortunately, known bugs for certain hardware configuration that make new versions wakeup immediately (with no user interference and with no log info) after the sleep process... my bad luck i'm hit by that :( i must stay with 2.6.16 (or go with 2.6.18 and get only suspend-to-disk). I'm hoping the issue be solved one of this days...


[QUOTE=lighty14]Turns out I'm fairly rusty on patching kernel sources. I have the kernel sources downloaded, and I have the suspend2 patch, however, I am unable to run patch successfully. If someone has some insight, that'd be great.[/QUOTE]

the usually problem that cause patchs fail are wrong source version to be patched. They must much precisely. 
You could try to get a kernel source from kernel.org with no minor version (2.6.18 and not 2.6.18.1) and get the equivalent patch from [here]("http://www.suspend2.net/downloads/all/").

Or get some pre-patched sources that only requires compilation like [emission]("http://evolution-mission.org/viewforum.php?f=8&st=0&sk=t&sd=d&start=0") or [beyond]("http://iphitus.loudas.com/beyond.php"). They work very nicely, are usually faster then ubuntu defaults and have other nice patchs like vesafb to use fbsplah.

---

### Post by Treviño on 2006-10-31
Hello, sorry for making you wait so much, but I want make too much things together :)

I hope to post the files in few times, but I've problems with space :o
[Sayonara123]("http://ubuntuforums.org/member.php?u=184911"), thanks for the offer... I'm evaluating it... I'm just waiting tuxfamily for an answer (I'd prefer to keep my repositories together... :))
-------- EDIT: tuxfamily gave me 1Gb of space (I had 100mb at the beginning, then 250mb), so... I think it's enough :)

I've just to finish some "userui-themes" packages and all should be done...

---

### Post by QuinnStorm on 2006-11-01
Hey, just figured I'd weigh in, I have a new laptop here, works absolutely great with the default edgy stuff, but swsusp is so slow, I'd love to get suspend2 working.  Oh, and here's the bragging bit...I don't have to turn off beryl to suspend/resume, it works perfectly.  Oh how I love the dev for the i810 drivers. (915gm family here)

---

### Post by Treviño on 2006-11-02
Sure... Beryl works ok with suspend2 :)

---

### Post by petr.fischer on 2006-11-02
@Trevino

Have you got any "show stoppers" to publish kernel and support packages on tuxfamily? Any planned release date? :) Thanks very much for information (notebook usage without hibernation sucks).

---

### Post by Treviño on 2006-11-02
I'm very sorry for making you wait so much, but time is really little...
I got much space in tuxfamily so I can upload there, the only problem is time for finishing some scripts and packages...

Anyway both the -general and the -386 kernels I've made are working fine.

I think that next releases will be quicker!

---

### Post by anandi on 2006-11-03
Just discovered this thread. I would love to get suspend2 working on my R50 running Dapper.

Waiting for the release :)

---

### Post by mariner09 on 2006-11-06
Trevino,

If you aren't ready to post your results because of bugs, could you at least post some how-to for those of us that are too anxious?

---

### Post by Whoopie on 2006-11-07
Hi,

have a look at his page: [http://3v1n0.tuxfamily.org/dists/edgy/suspend2/](http://3v1n0.tuxfamily.org/dists/edgy/suspend2/)

Best regards,
Whoopie

PS: Treviño, could you update to latest suspend2: [http://www.suspend2.net/downloads/all/suspend2-2.2.8.2-for-ubuntu-2.6.17-10.33.patch.bz2](http://www.suspend2.net/downloads/all/suspend2-2.2.8.2-for-ubuntu-2.6.17-10.33.patch.bz2)

---

### Post by Ago12 on 2006-11-07
> **Whoopie said:**
> Hi,

have a look at his page: [http://3v1n0.tuxfamily.org/dists/edgy/suspend2/](http://3v1n0.tuxfamily.org/dists/edgy/suspend2/)

Best regards,
Whoopie

PS: Treviño, could you update to latest suspend2: [http://www.suspend2.net/downloads/all/suspend2-2.2.8.2-for-ubuntu-2.6.17-10.33.patch.bz2](http://www.suspend2.net/downloads/all/suspend2-2.2.8.2-for-ubuntu-2.6.17-10.33.patch.bz2)

I'm running these packages since one or two days.

But, it doesn't seem to do anything: I can't even suspend :(

Could you give me some tips?

:)

---

### Post by Rui Pais on 2006-11-07
> **Ago12 said:**
> ...
But, it doesn't seem to do anything: I can't even suspend :(

Could you give me some tips?

Have you read [this]("http://www.suspend2.net/HOWTO")? it says ***all***.


Basic is just:
add to your grub boot entry:
> resume2=swap:/dev/hdXXX
(hdXX must, of course, be replaced by your swap partition letter and number)

check default hibernate options at /etc/hibernate/*.conf. Main is hibernate.conf, that usually call the others. 
Details on each option [here]("http://www.suspend2.net/HOWTO-4.html").

and run:
```
sudo hibernate 
```
for default, or:
```
sudo hibernate -F /etc/hibernate/<script_you_want>.conf
```

hth

---

### Post by Treviño on 2006-11-07
They are up from some days, but not complete... So please, _**use for testing**_ but don't share too much the word (yet :P)

To suspend use but you need a kernel option as written above...
Remember you need at least a swap space big as your ram is... Anyway you can also suspend to file; read suspend2 docs!

```
sudo hibernate
```
or
```
sudo hibernate.ram
```

>  PS: Treviño, could you update to latest suspend2: [http://www.suspend2.net/downloads/al...0.33.patch.bz2]("http://www.suspend2.net/downloads/all/suspend2-2.2.8.2-for-ubuntu-2.6.17-10.33.patch.bz2")
Newer patches than the 2.2.7.6 aren't working well in the ubuntu kernel (I get many errors while patching, also for missing files... Not only for hanks); so we continue with this!

There are no great improvements in newer versions, isn't it? :o

---

### Post by Ago12 on 2006-11-07
> **Rui Pais said:**
> Have you read [this]("http://www.suspend2.net/HOWTO")? it says ***all***.


Basic is just:
add to your grub boot entry:

(hdXX must, of course, be replaced by your swap partition letter and number)

check default hibernate options at /etc/hibernate/*.conf. Main is hibernate.conf, that usually call the others. 
Details on each option [here]("http://www.suspend2.net/HOWTO-4.html").

and run:
```
sudo hibernate 
```
for default, or:
```
sudo hibernate -F /etc/hibernate/<script_you_want>.conf
```

hth

Thank you very much, I'm gonna try that :)

Edit: Wow, works nice!

Thanks Tr3vin0 :)

---

### Post by mariner09 on 2006-11-08
Trevino,

Well done.

So much better than the default swsusp.

Thank You!

---

### Post by petr.fischer on 2006-11-08
my feedback: suspend to ram nor hibernate to disk still don't work on HP notebook nx8220... bad notebook, bad ACPI maybe... :(

---

### Post by Treviño on 2006-11-08
Mhmhm... Suspend to ram is more difficult... But what about suspend 2 disk; it must work... :o

Generally I've seen that on first reboot with new kernel and new cpu command line suspension to disk didn't work... While on next reboots it works great... Simply retry...
Then if it continue not working look at files /var/log/hibernate.log and /sys/power/suspend2/debug_info (they need "sudo" to be seen)

Bye!

---

### Post by Ago12 on 2006-11-08
With a little more trying, i've found two or three things that are not very cool:

- I have to restart bluetooth daemon after each hibernation to get my BT mouse working (BTW, I think I should configure the scripts to avoid that... RTFM, rhaaa!)

- After hibernate, I can't cap my procs anymore with the Gnome applet. They seem to be all the time in "performance" mode

- The first time it hibernates, it looks nice. After, it shows big cabalistics things on the screen. That's not annoying, unless the fact that it isn't very sexy :p

- The last time I tried, I coudn't access to a tty anymore, nor comeback to X (the same artefacts than above, you know...)

- Network manager waits a long time before scanning the wifi network, and most of the time I have to ifdown/ifup (don't know if it helps)


Otherwise, I'm happy :p

I'm sure it could get better if it was officially adopted by Ubuntu :(


Edit: I'm using Beryl

---

### Post by Treviño on 2006-11-08
Sure... Anyway you can fix some things simply edit your /etc/hibernate/*.conf files...
For example, you can stop and restart processes/network-interfaces on hibernation-resume...

The only problem I really get is that the touchpad doesn't work totally on resume... That's a common bug, but no way to fix that... :(
This didn't help me: [http://lists.suspend2.net/lurker/message/20051030.205916.e40c3563.en.html](http://lists.suspend2.net/lurker/message/20051030.205916.e40c3563.en.html)

---

### Post by mariner09 on 2006-11-09
Trevino,

For what it's worth, on an IBM T41, your kernel and scripts, by default, worked great.

NetworkManager gave me no trouble and it's all good.

Again, well done...

---

### Post by petr.fischer on 2006-11-09
> **Treviño said:**
> Mhmhm... Suspend to ram is more difficult... But what about suspend 2 disk; it must work... :o

Generally I've seen that on first reboot with new kernel and new cpu command line suspension to disk didn't work... While on next reboots it works great... Simply retry...
Then if it continue not working look at files /var/log/hibernate.log and /sys/power/suspend2/debug_info (they need "sudo" to be seen)

Bye!

After hibernate to disk, normal boot start__s...

/var/log/hibernate.log
```

Starting suspend at Pá lis 10 01:25:33 CET 2006
hibernate: [01] Executing CheckLastResume ... 
hibernate: [01] Executing CheckRunlevel ... 
hibernate: [01] Executing LockFileGet ... 
hibernate: [01] Executing NewKernelFileCheck ... 
hibernate: [10] Executing EnsureSwsusp2Capable ... 
hibernate: [11] Executing XHacksSuspendHook1 ... 
hibernate: [59] Executing RemountXFSBootRO ... 
hibernate: [89] Executing SaveKernelModprobe ... 
hibernate: [91] Executing ModulesUnloadBlacklist ... 
hibernate: [95] Executing XHacksSuspendHook2 ... 
hibernate: [97] Executing ChangeToSwsuspVT ... 
hibernate: [98] Executing FullSpeedCPUSuspend ... 
hibernate: [98] Executing CheckRunlevel ... 
hibernate: [98] Executing Swsusp2ConfigSet ... 
hibernate: [99] Executing DoSwsusp2 ... 
hibernate: Activating suspend ...

```

/sys/power/suspend2/debug_info
```

Suspend2 debugging info:
- SUSPEND core   : 2.2.7.6
- Kernel Version : 2.6.17-10-generic
- Compiler vers. : 4.1
- Attempt number : 0
- Parameters     : 0 16384 0 0 0 0
- Overall expected compression percentage: 0.
- Compressor is 'lzf'.
- Swapwriter inactive.
- Filewriter inactive.
- No I/O speed stats available.
- Extra pages    : 0 used/500.

```

pf

---

### Post by petr.fischer on 2006-11-09
...and I have troubles with repository:

# apt-get install suspend2
...
Get:1 [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy/suspend2 initramfs-tools-suspend2 0.4-3v1ubuntu0 [1942B]
Get:2 [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy/suspend2 suspend2-userui-usplash 0.6.4-5-3v1ubuntu0 [89.8kB]
Get:3 [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy/suspend2 suspend2 2.2.7.6-3v1ubuntu0 [3456B]
Fetched 91.7kB in 0s (159kB/s)
Failed to fetch [http://3v1n0.tuxfamily.org/pool/edgy/suspend2/suspend2_2.2.7.6-3v1ubuntu0_all.deb](http://3v1n0.tuxfamily.org/pool/edgy/suspend2/suspend2_2.2.7.6-3v1ubuntu0_all.deb)  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

----

"Size mismatch"? Thanks, pf

---

### Post by Treviño on 2006-11-10
Sorry... As I said this repo is still in WIP state, so there are some things that could not work...
Anyway that's simply a metapackage... So you can avoid to install it (until I'll say to do that :))

Bye

PS: Beryl has no problems with hibernation

---

### Post by Ago12 on 2006-11-14
Hey, I don't want to speed you too much, but when do you think your repo and package will be stable, because I want to spread them but ATM it is not ready :/

---

### Post by Treviño on 2006-11-14
I can't really know exactly becouse on those days I had many unexpected  problems (not with suspend2...)

The things I've to finish are few...
However, how does it work with you (and other users)? Feedbacks are welcome!

And another things... Isn't there anyone that is using suspend2 with AIGLX and radeon drivers? I'm testing it, but resuming isn't always working...

---

### Post by Ago12 on 2006-11-14
It works almost fine here...

Actually, I haven't found a way to let the cpu freq scaling come back, and sometimes NetworkManager doesn't scan (well, almost every time). So, if I suspend at school and wake up at home, most of the time I have to reboot :(

If it is the same Network, no problem :)

---

### Post by petr.fischer on 2006-11-14
Ago12 - if you right click on NetworkManager icon (in gnome-panel), there are checkboxes for enabling/disabling network and wireless network - try to uncheck (disable given interface), wait a second and check (enable interf.), wait some seconds and scanning is back (this worked for me on dapper)

Trevino - my hibernate status -> still don't work (normal boot after hibernation)

---

### Post by noamr on 2006-11-14
Hello,

I installed the package suspend2, and tried sudo hibernate. The screen got blank for a few seconds, and then came up again, with this message in the terminal:

hibernate: Suspend reported the following errors:
 - Suspend was aborted (see dmesg).
 - No swapspace was available. Try swapon?

I also tried sudo hibernate-ram, and the computer seemed to go to sleep ok, but couldn't resume (I got a blank screen with a blinking cursor). :(

Thanks for your work,
Noam

---

### Post by petr.fischer on 2006-11-14
@noamr - what is wrong with your swap partition? try command:
# swapon -a

@trevino - same "suspend to ram" status as "noamr" reported

@for all - please report notebook type too

---

### Post by noamr on 2006-11-14
@petr.fischer - the result is this:
> swapon -a
swapon: /dev/disk/by-uuid/5d137683-09cc-49ad-aa16-5bea6f78a5b5: Invalid argument

That's the entry from /etc/fstab:
UUID=5d137683-09cc-49ad-aa16-5bea6f78a5b5 none swap sw 0 0

I don't know about anything wrong with the swap partition - the computer seems to be working fine.

Thanks,
Noam

---

### Post by petr.fischer on 2006-11-14
@noamr - I have exactly same problems with swap after upgrade from dapper to edgy - you can solve swap problem with these steps:

send me output from these two commands (run commands as root):
1) # cat /etc/fstab
2) # fdisk -l

---

### Post by Treviño on 2006-11-14
Edgy uses another way to call the partitons, bwt it didn't work for me...
So, I had to put back in my /etc/fstab the static way for example:

After the edgy update I had:
```
# /dev/hda2 -- converted during upgrade to edgy
UUID=3f99f00f-563a-4fee-970c-6a31da36b101 none swap sw 0 0
```
Simply I commented the latest line and I put it to:
```
# /dev/hda2 -- converted during upgrade to edgy
#UUID=3f99f00f-563a-4fee-970c-6a31da36b101 none swap sw 0 0
/dev/hda2 none swap sw 0 0
```
Then a simple
```
sudo swapoff -a & sudo swapon -a
```
fixed my swap issue...

**noamr**, please report here your "dmesg" output (just the final part in which there's something about suspend2).

---

### Post by Rui Pais on 2006-11-14
> **Treviño said:**
> Edgy uses another way to call the partitons, bwt it didn't work for me...
So, I had to put back in my /etc/fstab the static way for example:

After the edgy update I had:
```
# /dev/hda2 -- converted during upgrade to edgy
UUID=3f99f00f-563a-4fee-970c-6a31da36b101 none swap sw 0 0
```
Simply I commented the latest line and I put it to:
```
# /dev/hda2 -- converted during upgrade to edgy
#UUID=3f99f00f-563a-4fee-970c-6a31da36b101 none swap sw 0 0
/dev/hda2 none swap sw 0 0
```
Edgy installer sometimes seems to make wrong UUIDs...

Instead of doing a static reference on fstab use 
```
vol_id /dev/hda2
```
to get the correct UUID for the partition.

(or is vol_id -u ?... )

---

### Post by noamr on 2006-11-14
Hi,

I changed the UUID to /dev/hda5 in /etc/fstab, and hibernate worked. I had to reboot - "swapon -a" complained about "/dev/hda5 invalid argument" or something like that and probably didn't do anything. hibernate-ram still gets stuck on power up.

Here's the dmesg output from before the change:

[17184626.528000] Suspend2 2.2.7.6: Initiating a software suspend cycle.
[17184628.536000] Freezing cpus ...
[17184629.204000] You need some storage available to be able to suspend.
[17184629.236000] Suspend2 debugging info:
[17184629.236000] - SUSPEND core   : 2.2.7.6
[17184629.236000] - Kernel Version : 2.6.17-10-generic
[17184629.236000] - Compiler vers. : 4.1
[17184629.236000] - Attempt number : 2
[17184629.236000] - Parameters     : 5 16400 0 1 0 0
[17184629.236000] - Overall expected compression percentage: 0.
[17184629.236000] - Compressor is 'lzf'.
[17184629.236000] - Swapwriter active.
[17184629.236000]   Swap available for image: 0 pages.
[17184629.236000] - Filewriter inactive.
[17184629.236000] - No I/O speed stats available.
[17184629.236000] - Extra pages    : 0 used/500.
[17184629.240000] Thawing cpus ...
[17184629.296000] ACPI: Power Button (FF) [PWRF]
[17184629.296000] ACPI: Lid Switch [LID]
[17184629.296000] ACPI: Sleep Button (CM) [SLPB]
[17184629.672000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[17184629.688000] input: TPPS/2 IBM TrackPoint as /class/input/input5

By the way, the graphical progress bar doesn't show up - on hibernate shutdown it isn't displayed at all, and on hibernate power up it is displayed for a few seconds and then gets ruined until the computer is up again. I don't mind it very much, it's just if you want to know.

Thanks!
Noam

---

### Post by Treviño on 2006-11-14
Regarding the bar... Are you using usplash I think... Try to set it to fbslash (from /etc/hibernate/ *.conf files... )

---

### Post by noamr on 2006-11-15
I've downloaded the fbslpash package and changed /etc/hibernate/suspend2.conf to use it, but it didn't work. Perhaps it's related to the message "can't open file /dev/fb0" I get?

---

### Post by Treviño on 2006-11-15
Mh... Could be...

what do you get doing lsmod|grep fb ?

Anyway, have you tried to run it as test (running the bin file) or when hibernating?

---

### Post by lighty14 on 2006-11-15
Well, I installed your sources on my new laptop. Suspend to disk works PERFECT. However, I've had some issues with suspend to ram. The suspend works fine, and even the resume; however, after all is said and done, my Network Monitor applet breaks, it no longer shows my wireless connection. However, I am able to manually configure it in Network settings. However, there is no way to get Network Monitor to recognize the wireless without a reboot.

Oh I forgot about one other issue: sound doesn't work after hibernate or suspend, though this might be fixable with a little module loading and unloading in the scripts.

---

### Post by petr.fischer on 2006-11-15
@lighty14 - read the last message on page 5 and try it (works for me on dapper)

---

### Post by lighty14 on 2006-11-15
Network Manager doesn't even show  the wireless device, even if I try killing it and starting a new process, so it can't be disabled.

---

### Post by Treviño on 2006-11-15
Maybe it's a module problem... try to remove it and then reload

---

### Post by mariner09 on 2006-11-16
For the fbsplash not working, add VGA=791 to /boot/grub/menu.lst in the defoptions line.  Run sudo update-grub.  Worked for me.

For wireless, play with modules and network services.  I stop NetworkManager at suspend.  When I resume, it won't launch until I disable networking and then enable it.

Trevino, have you seen any of your packages change the permissions on /etc/resolv.conf from 644 to 600?

This happens every so often and I can't nail down the culprit.

Also, your wpasupplicant package installs /usr/sbin/wpa_supplicant and NM expects to find /sbin/wpa_supplicant.

---

### Post by madchicken on 2006-11-16
After installing the suspend2 kernel, I can hibernate my system, but I can't resume: the system simply start up as usual, with the difference that it can't activate the swap partition. I have to restart again the laptop to have swap working again.
Anyone with the same problem?

Thank you very much.

---

### Post by u-foka on 2006-11-16
I'm have this problem too. But i haven't got any solutions yet :S

---

### Post by madchicken on 2006-11-16
Can be this problem related to lvm?

---

### Post by Ago12 on 2006-11-16
> **lighty14 said:**
> Network Manager doesn't even show  the wireless device, even if I try killing it and starting a new process, so it can't be disabled.
Try 

sudo /etc/init.d/dbus restart

It's ugly, but it works :)


Almost OT: Trevino: You really need to repackage or at least remove the wpasupplicant package from your edgy repo, it doesn't work at all :/

---

### Post by noamr on 2006-11-16
> **Treviño said:**
> Mh... Could be...

what do you get doing lsmod|grep fb ?

Anyway, have you tried to run it as test (running the bin file) or when hibernating?

This is the output of lsmod | grep fb

fbcon                  41504  0
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
vesafb                  9244  0

I've tried to run the executable as test, and it distorted the screen and blocked all input...

I also tried to add vga=791 to grub's menu, and it didn't help...

But hibernation works great!

Noam

---

### Post by petr.fischer on 2006-11-20
@madchicken - I have same problem as you - without lvm.

---

### Post by reacocard on 2006-11-27
I installed these packages and they're working excellently, even with Aiglx/Beryl. Only thing that doesn't work is the usplash progress bar, which isn't a big deal.

Keep up the good work! :KS

---

### Post by Treviño on 2006-11-27
An update... Repository have changed address... Look here for new links:
[http://3v1n0.tuxfamily.org/dists/edgy/suspend2/](http://3v1n0.tuxfamily.org/dists/edgy/suspend2/)

---

### Post by Ago12 on 2006-11-27
Yep, but the suspend2 package is still broken :p

(OT: have you fixes the wpasupplicant package? It upsets me not to be able to upgrade it :/ )

---

### Post by reacocard on 2006-11-27
> **Ago12 said:**
> Yep, but the suspend2 package is still broken :p


It's broken in the repo, but if you download it manually it works fine.

---

### Post by Ago12 on 2006-11-28
Sure, but I don't ad a repo to download the debs manually, if you see what I mean ;)

---

### Post by petr.fischer on 2006-11-28
what is the problem with suspend2 package in the repo? - I installed suspend2 package manually and it is infinite loop in practise - ubuntu update manager says that update is available for suspend2 package, but error occurs while download part (Size mismatch error)

---

### Post by Treviño on 2006-11-29
I know that, but I can't find time to finish this work :(

Sorry for that... Btw I've updated the initram package, did you download it?
It should fix some syntax problems in the ininitram scripts there was before...

---

### Post by petr.fischer on 2006-11-30
@trevino - yes, I updated now - but there is next problem maybe - when updating initram* scripts, my old initrd.img-2.6.15-23-686 were regenerated (initrd.img-2.6.17-10-generic is completely untouched) - is it a bug? thanks!

---

### Post by Treviño on 2006-11-30
Mh... could be... :P
That's the only kernel it has updated?
I've added update-initramfs -u to postinst/rm scripts... Maybe should I use another option?

---

### Post by petr.fischer on 2006-12-01
@trevino - yes, old 2.6.15 initrd is the only updated one - I removed this old kernel and reinstalled your updated initramfs* package - now, actual kernel initrd is updated and I have good news - hibernation (suspend to disk) works (!) on my notebook - Trevino, thanks for this work. 

problem with update-initramfs: look at man page and option -k (and uname -r) - this is the way IMHO

---

### Post by Ago12 on 2006-12-02
Hum, my clock time is completly messed up...


I wonder if it is not related to the new initfram package...

Do you have the same problem?

---

### Post by lakicsv on 2006-12-02
I have installed the debs from your webpage, and just wanted
to say THANK YOU!

Everything works fine, the splash screen did not work first,but the vga=791 option (this thread) solved it, after reboot it worked fine. My wireless network is coming back after 15-20 sec of resume (I use knetworkmanager). 

The only significant problem was the lack of sound after resume. But if I do a

```
sudo /etc/init.d/alsa-utils restart
```the sound is back...

So now I just need to add an
 ```
OnSuspend 01 /etc/init.d/alsa-utils stop
```and an 
 ```
OnResume 99 /etc/init.d/alsa-utils start
```to my /etc/hibernate/suspend2.conf, and problem solved...

Now if someone would tell me how to get sudo not asking a password after I give the hibernate command...I have tried visudo, and edit my conf as the Suspen2 Howto suggested, but sudo still asks me for a password...

A final question. Is there a kubuntu specific splash theme with the progress bar etc., because at the moment it is just brown and says ubuntu :p...

---

### Post by reacocard on 2006-12-02
> **lakicsv said:**
> ... Now if someone would tell me how to get sudo not asking a password after I give the hibernate command...I have tried visudo, and edit my conf as the Suspen2 Howto suggested, but sudo still asks me for a password...

If you installed the new acpi-support package from Trevino's repo (should have been automatic), then you can just choose 'hibernate' from the normal shutdown options to use suspend2. It's automatically integrated!

---

### Post by petr.fischer on 2006-12-03
next problem: gnome-power-manager is confused after dehibernation (batery/cable status don't work)...

---

### Post by fettuohi on 2006-12-06
Has anybody gotten this to work with the nvidia drivers?

Kind Regards

André

---

### Post by Treviño on 2006-12-06
My Experiences:
- It works great with ATi's fglrx if you've set them correctly... 
- Good with radeon open source drivers (if you're not using a composite manager)...
- There are problems while resuming with Ati and the radeon open source driver with AiGLX running (or better if you've opened in the current session a coposite manager like compiz or beryl; no problems otherwise)
- No experiences with Nvidia :P

Bye ;)

---

### Post by fettuohi on 2006-12-09
Anybody else? I can hibernate in text mode and in graphical mode it works also but when resuming the session I end up with a black screen after the bar has loaded :(. 

Regards

André

---

### Post by therobbot on 2006-12-10
Hi,

I second the question about the Kubuntu-specific splash. Other than this it works like a charm for me!

Tobias

---

### Post by Ago12 on 2006-12-11
[https://launchpad.net/distros/ubuntu/+search?text=suspend2](https://launchpad.net/distros/ubuntu/+search?text=suspend2)

Official packages in feisty? Yihaaa §§§

---

### Post by reacocard on 2006-12-11
> **Ago12 said:**
> [https://launchpad.net/distros/ubuntu/+search?text=suspend2](https://launchpad.net/distros/ubuntu/+search?text=suspend2)

Official packages in feisty? Yihaaa §§§

Sorry to disappoint you, but no. The kernel still will not include suspend2 support.  There are packages for hibernate and suspend2-userui in edgy too:

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=suspend2&searchon=names&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=suspend2&searchon=names&subword=1&version=edgy&release=all)
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=hibernate&searchon=names&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=hibernate&searchon=names&subword=1&version=edgy&release=all)

---

### Post by Ago12 on 2006-12-12
Oh crap! :'(

I hope too much :/

---

### Post by blk_jack on 2006-12-12
Tried to install it on my amd64 machine and there were missing 64bit packages that prevented the installation.

It sounds like you've got a great thing going here and I was wondering when/if you'll have those missing packages for amd64?

Thanks! 8)

---

### Post by fettuohi on 2006-12-12
> **therobbot said:**
> Hi,

I second the question about the Kubuntu-specific splash. Other than this it works like a charm for me!

Tobias

What graphics driver are you using?

Regards

André

---

### Post by jasonxh on 2006-12-12
Thanks for the great work, Treviño.

However on my laptop none of the three ui modes works.](*,) I'm using a IBM T60, X1300, with fglrx driver from restricted modules. I first tried it under Xgl session, then switch back to normal gnome session. Neither gives me any ui at all but a scratchy screen.

I've also tried testing the ui's with -t, but it showed nothing on screen, and each time I ran the test, my keyboard just went out of order!:evil: 

Having such bad luck with ui, everything else works fine.:) So at least I can enjoy the much more stable suspend feature from suspend2.

Hope to hear some suggestions from anybody.

---

### Post by therobbot on 2006-12-13
I'm using the standard ati open source drivers. But why is this relevant? I'd just like to have a Kubuntu (i.e. blue) splash screen instead of the brown Ubuntu one.

Tobias

---

### Post by Ago12 on 2006-12-13
There is a new edgy kernel in the repo (10.34), will you patch it again Trevino?

:)

---

### Post by Treviño on 2006-12-14
Thobias, you should use another uplash/fbsplash package, anyway that's the only thing I've to finish in my work :/

Btw, I've just patched and packaged the new kernel against suspend2 2.2.9... I've just to test it and to upload (and I've a slow connection actually :/)... I was thinking to apply also others patch (first of all the new drm modules from git, which gave me a good performance improvement under AiGLX and ati OSS drivers...)

Let me know if you want other specific things (native support, or anything else)...

Regarding feisty support, I've no news about... Anyway one of my hope was to create also an "unstable" repo in which putting the stable+1 kernel release (feisty in this case) patched with suspend2 but compiled under the stable release (edgy, now).
Let me know if anyone whould like it... It has only the problem that I need to repack also all the restricted modules :/

BYE!

---

### Post by Ago12 on 2006-12-14
Hum, I'm compiling the 2.6.19 kernel right now, since I had a problem with the 2.6.29-1 (no rule for the ieee driver).

So I've tweaked a litlle bit the options, and next I'll search for new patches (the drm modules may be interesting ;) )

---

### Post by Treviño on 2006-12-14
If you're using the latest kernel I think that the modules are quite updated, btw the code for them is available in the freedesktop git (section /mesa/drm/linux-core)

Bye ;)

---

### Post by Ago12 on 2006-12-15
Thanks! :)

I'm still compiling it atm, I can't make the ipw3945 work :o

But I've just found a patch.

Don't know if it works yet, but it applies well :)

If it can help you, here it is: [http://www.rit.edu/~rmh3093/ipw3945-1.1.2_for_2.6.19.patch](http://www.rit.edu/~rmh3093/ipw3945-1.1.2_for_2.6.19.patch)

:)

---

### Post by danielluo on 2006-12-15
try put "vga=791" in the boot option of grub.

---

### Post by jasonxh on 2006-12-15
> **jasonxh said:**
> Thanks for the great work, Treviño.

However on my laptop none of the three ui modes works.](*,) I'm using a IBM T60, X1300, with fglrx driver from restricted modules. I first tried it under Xgl session, then switch back to normal gnome session. Neither gives me any ui at all but a scratchy screen.

I've also tried testing the ui's with -t, but it showed nothing on screen, and each time I ran the test, my keyboard just went out of order!:evil: 

Having such bad luck with ui, everything else works fine.:) So at least I can enjoy the much more stable suspend feature from suspend2.

Hope to hear some suggestions from anybody.

No one has met this problem?:confused: 

Another thing is I just updated to the newly out kernel by Treviño, i.e. -10.34. The /sys/power/suspend2 is gone with this new kernel. Is it a problem?

Thanks guys.

---

### Post by jasonxh on 2006-12-15
> **danielluo said:**
> try put "vga=791" in the boot option of grub.

Were you replying my post, danielluo? Adding "vga=791" gives me a blank screen rather than the old scratchy one, but still no ui yet. I think the real problem is how my keyboard got messed up after running the ui. And I also find that I can't press escape to stop hibernation (of course I've set that option in conf), which I guess has sth to do with the keyboard matter.

A newbie's life is so hard...:(

---

### Post by Treviño on 2006-12-15
I didn't update the kernel yet... That's the ubuntu official kernel...
My kernels will be out in few hours I hope; but I have to test them well before :P

Regarding the fglrx have you read this: [http://wiki.cchtml.com/index.php/Suspend2](http://wiki.cchtml.com/index.php/Suspend2)

---

### Post by jasonxh on 2006-12-15
Sorry for the mistake :)

Yes I have already read it and set it to 15000. Maybe when I have time I will try a system reinstall ...

---

### Post by riven0 on 2006-12-15
Trevino, just wanted to say thanks for the suspend2 patch. I just did it on a thinkpad and it worked great with the 2.6.19 kernel. Now I just close the lid and it immediately goes into hibernation without a problem. :D

---

### Post by Treviño on 2006-12-16
Good :)

I'm uploading the new kernels, btw I've a low speed connection now so I'll need much time; btw I'm posting here the patch again the ubuntu kernel sources (the pre-patched ones) for people who want to patch the kernel by himself: [suspend2-2.2.9-for-2.6.17.1-10.34-ubuntu.patch.gz]("http://download.tuxfamily.org/3v1deb/pool/edgy/suspend2/suspend2-2.2.9-for-2.6.17.1-10.34-ubuntu.patch.gz")

---

### Post by Ago12 on 2006-12-18
One question Trevino: how have you done to get suspend int the initram?

Which howto have you followed for this? Thanks!

---

### Post by mariner09 on 2006-12-18
Trevino,

I just upgraded to your recent kernel debs for Edgy with Suspend2 and I get this in the process while generating initrds:

/usr/share/initramfs-tools/hooks/suspend2ui_hook: line 26: syntax error near unexpected token `elif'
/usr/share/initramfs-tools/hooks/suspend2ui_hook: line 26: `elif [ -x /usr/bin/suspend2ui_fbsplash ];'

I haven't suspended yet, but does this look like a problem?

Shannon

---

### Post by Ago12 on 2006-12-18
if you don't wan't to take a risk, just try:

sudo suspend -v0 --dry-run 

If there's no output it should be fine
:]

---

### Post by nmincone on 2006-12-18
Hibernate worked with standard settings on a hp nx9010 running 6.10 Edgy. I never had any success with resume from suspend/hibernation before, but shortly afterwards a lockup. I believe due to a driver with my Linksys PCMCIA card or wireless logitech mouse maybe???? Anyone have a working set of .conf files I can work off of before I go through a lot of trial and error???
Suspend to RAM is still an issue with this patch though- it goes down but won't wake, I'll experiment with some config settings and report any success.

---

### Post by Treviño on 2006-12-18
Finally I finished to upload the new debs... You can find them here: [http://download.tuxfamily.org/3v1deb/pool/edgy/suspend2/](http://download.tuxfamily.org/3v1deb/pool/edgy/suspend2/)

Wait a few for the repository update ;) 

EDIT: the r***epository is now updated***, simply apt-get update and distupgrade your Ubuntu! ^_^

---

### Post by detyabozhye on 2007-01-09
Thanks man! Works awesome (with a few tweaks here and there, using nVidia)

---

### Post by glenndavy on 2007-01-12
bump

---

### Post by Choad on 2007-01-14
ok im very interested to try this but i have a few questions

what exactly do i need to install? i sumbled upon [http://3v1n0.tuxfamily.org/dists/edgy/suspend2/](http://3v1n0.tuxfamily.org/dists/edgy/suspend2/) that, and then found this thread, but i cant find a howto detailing what i need to instsll, except old how-to's about compiling from source.

also, if it goes wrong, can i revert back? (not that there is much point seeming as this method of suspend doesnt work)

i have a geforce go 7600... are there any special steps i need to take to avoid bugs in the binary driver?

thanks

---

### Post by Choad on 2007-01-14
ok i just added the repos and did a dist-upgrade

havent tested suspend yet, but it has no nvidia kernel module, and it has no dual core (SMP) support

how am i going to get nvidia, SMP and suspend2 in to the same kernel.... im going to have to build one arent i?

daunting prospect...

---

### Post by Choad on 2007-01-14
alllllsoo

i get an error message/warning on starting

missing or invalid location (resume2= parameter) please fix this and rerun lilo (or equivilent) before suspending

or something to that effect.... 

edit: it just carries on booting tho, it doesnt stop anything

---

### Post by Rui Pais on 2007-01-14
> **Choad said:**
> alllllsoo

i get an error message/warning on starting

missing or invalid location "resume2=" please fix this and rerun lilo (or equivilent) before resume

or something to that effect.... i dont have that good a memory

edit: it just carries on booting tho, it doesnt stop anything

add to /boot/grub/menu.lst, at the line of your kernel:
```
resume2=swap:/dev/<your_swap_part_number>
```

btw, you must be check something incorrectly because these kernel have SMP enabled.

EDIT: if you have problem with nvidia module, add a line with:
nvidia 
to /etc/hibernate/blacklisted-modules.

---

### Post by Choad on 2007-01-14
apparently my swap is

/dev/sda5

so is that what i should put there?

---

### Post by Rui Pais on 2007-01-14
yes, 
in that add to the end of kernel line:
```
resume2=/dev/sda5
```

---

### Post by Choad on 2007-01-14
OMG

it worked

pure sexual geeky satisfaction

SMP, nvidia and suspend

THANKYOU to all who made this happen (including Rui Pais and the person hosting the repo)

---

### Post by reacocard on 2007-01-14
Trevino, would you mind posting that tutorial for creating these kernels (and other packages) sometime? I'll need it when I upgrade to feisty in a couple months.

---

### Post by rj686 on 2007-01-14
> **reacocard said:**
> Trevino, would you mind posting that tutorial for creating these kernels (and other packages) sometime? I'll need it when I upgrade to feisty in a couple months.
Yeah that would be awesome if you could post a how to :)

---

### Post by rj686 on 2007-01-15
Nevermind the tutorial, works fine, i jsut had to re-install my sound card :(. What are all the conmmans for this?

---

### Post by dare2dreamer on 2007-01-22
I installed Trevino's suspend2 packages on my Toshiba Portege 3500. It seems to suspend without issue, but when it comes out of suspend I get the following error:

```
Jan 21 14:34:27 localhost kernel: [17180503.144000] cpufreq: resume failed to assert current frequency is what timing core thinks it is.
```

on a black text screen, with a locked keyboard/os.

Any ideas?

---

### Post by nuclear_eclipse on 2007-01-27
I have a Dell XPS m140 laptop, with the Intel 915 video card.  I have to use the 915resolution package to get the proper video resolution on my screen (1280x800), and I can resume from hibernation just fine.  However, after resuming, my screen resolution has dropped to 1024x768, and I can't change it back.  Performing a fresh reboot on the system fixes the issue, but that sort of defeats the purpose.  Any suggestions?  Thanks.

---

### Post by nuclear_eclipse on 2007-01-27
Quick addition:  I just realized that the system actually thinks it's in 1280x800, but the screen is only display the top left 1024x768 pixels, centered on the screen as if it were in 1024x768 mode.  Hope that helps.  Thanks.

---

### Post by glenndavy on 2007-01-27
hey there newclear.... have you tried setting the resolution in /etc/default/915resolution? - ive gota hunch that will resolve your issue for you

---

### Post by nuclear_eclipse on 2007-01-27
I didn't have it set before, but I set the MODE=5c, which corresponds to the 1280x800x32 setting, but it still won't reinitialize the monitor correctly.  The system still thinks and uses 1280x800 resolution, and the right and bottom are cut off from the 1024x768 that the laptop is actually displaying....

---

### Post by reacocard on 2007-01-27
> **nuclear_eclipse said:**
> I have a Dell XPS m140 laptop, with the Intel 915 video card.  I have to use the 915resolution package to get the proper video resolution on my screen (1280x800), and I can resume from hibernation just fine.  However, after resuming, my screen resolution has dropped to 1024x768, and I can't change it back.  Performing a fresh reboot on the system fixes the issue, but that sort of defeats the purpose.  Any suggestions?  Thanks.

Try this:

Do a
```
gksudo gedit /etc/hibernate/common.conf
```
and change
```
# Runi915resolution yes
```
to
```
Runi915resolution yes
```

---

### Post by nuclear_eclipse on 2007-01-27
Thank you, that fixed the resolution issue.  Now I'm having problems getting the laptop to work using Suspend instead of Hibernate. If you have any suggestions for that, I'd appreciate it, but seeing that most people have probelms with suspending in Linux,  I'm not too worried if I'm stuck with Hibernation, that's still better than restarting all the time.

---

### Post by energiya on 2007-01-27
I really have to ask... did anyone managed to get suspend2 to work (using nvidia card) ?
Mine goes to hibernate and resumes only when I kill X, and suspend to ram doesn't run anymore :(

---

### Post by reacocard on 2007-01-27
> **nuclear_eclipse said:**
> Thank you, that fixed the resolution issue.  Now I'm having problems getting the laptop to work using Suspend instead of Hibernate. If you have any suggestions for that, I'd appreciate it, but seeing that most people have probelms with suspending in Linux,  I'm not too worried if I'm stuck with Hibernation, that's still better than restarting all the time.

Is it the same problem? If so, try editing /etc/default/acpi-support and uncommenting the line  that says "ACPI_USE_HIBERNATE_FOR_STR=true".

---

### Post by detyabozhye on 2007-01-27
> **energiya said:**
> I really have to ask... did anyone managed to get suspend2 to work (using nvidia card) ?
Mine goes to hibernate and resumes only when I kill X, and suspend to ram doesn't run anymore :(

Try adding:
```
    Option         "NvAgp" "1"
```
in the "Device" Section

---

### Post by mcarro on 2007-01-27
Hello everybody.  I am having problems when resuming from hibernation --- maybe one out of 7 or 8 times the screen stays locked and with some pattern of dark blue stripes.  The computer itself is not locked, as it answers to the keyboard (I can reboot with Ctr-Alt-Del).

I am using a ThinkPad T40, 512Mb, with ubuntu 6.10 and using gnome.  My video card is a ATI Radeon Mobility M9000, and I am using the XOrg radeon driver (**not** the closed-source fglrx).

I have located in the dmesg trace the difference between successful and unsuccessful resumptions.  A successful resumption has, at the end of the trace, the following lines:

[17384436.188000] Thawing cpus ...
[17384437.604000] ACPI: Power Button (FF) [PWRF]
[17384437.604000] ACPI: Lid Switch [LID]
[17384437.604000] ACPI: Sleep Button (CM) [SLPB]
[17384438.004000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0
[17384438.004000] serio: Synaptics pass-through port at isa0060/serio1/input0
[17384438.044000] input: SynPS/2 Synaptics TouchPad as /class/input/input20
[17384443.072000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[17384443.324000] input: TPPS/2 IBM TrackPoint as /class/input/input21
[17384445.160000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17384445.160000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17384445.160000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17384445.160000] [drm] Loading R200 Microcode

while unsucsessful resumptions would stop at line [17384443.324000] (this one appears).   The output of Suspend2 debug info is:

Suspend2 debugging info:
- SUSPEND core   : 2.2.9
- Kernel Version : 2.6.17-10-generic
- Compiler vers. : 4.1
- Attempt number : 5
- Parameters     : 0 81936 0 1 0 0
- Overall expected compression percentage: 0.
- Compressor is 'lzf'.
  Compressed 391749632 bytes into 227459056 (41 percent compression).
- SwapAllocator active.
  Swap available for image: 463184 pages.
- FileAllocator inactive.
- I/O speed: Write 52 MB/s, Read 53 MB/s.
- Extra pages    : -118 used/500.

and I am adding here the active options in suspend2.conf and common.conf   I will, of course, be most grateful for all and any help!



-------------------- suspend2.conf -------------------- 

### suspend2 (for Software Suspend 2)
UseSuspend2 yes
Reboot no
EnableEscape yes
DefaultConsoleLevel 1
Compressor lzf
Encryptor none
# ImageSizeLimit 200

# PowerdownMethod 5

# ProcSetting expected_compression 50

# FilewriterLocation /suspend_file 1000
# VerifyFilewriterResume2 yes

ProcSetting userui_program /usr/bin/suspend2ui_text

FullSpeedCPU yes

# From
# [http://lists.suspend2.net/lurker/message/20061211.215057.46bc7855.en.html](http://lists.suspend2.net/lurker/message/20061211.215057.46bc7855.en.html)
ProcSetting full_pageset2 1

Include common.conf

-------------------- common.conf -------------------- 

Verbosity 3
LogFile /var/log/hibernate.log
LogVerbosity 4
LogTimestamp yes
# AlwaysForce yes
# AlwaysKill yes
# HibernateVT 15
Distribution debian
# XDisplay :0


SaveClock restore-only

# IncompatibleDevices /dev/dsp /dev/video*

# DisableWriteCacheOn /dev/hda


### filesystems
Unmount /windows
Mount /windows

IbmAcpi yes
# Runi915resolution yes
FullSpeedCPU yes

# UnloadModules snd_via82cxxx usb-ohci
UnloadBlacklistedModules yes
LoadModules auto

### xhacks
SwitchToTextMode yes
UseDummyXServer yes

------------------------------------------------------------

---

### Post by Treviño on 2007-02-05
Hi people, considering that the 2.6.20 kernel (with great new things) has been released I decided to ***compile the feisty kernel*** (actually based on that version) _**patched with suspend2**_ (2.2.9.3), but all of this under edgy!

So, I think that both feisty users and edgy ones will be able to use it! :)
Maybe, I should also recompile the restricted-modules if anyone need them, so I don't really know when I'll be able to submit my new kernels to a new "-unstable" repository, but I hope soon... :P

Simply let me know if you're interested in these new kernels ;)

---

### Post by glenndavy on 2007-02-05
i'm excited :-)

---

### Post by Choad on 2007-02-05
ok i wonder if anyone here can help me

i did have suspend working, *quite* reliably a while ago, but now - nothing

i think it has something to do with mouse drivers... which is a bit wierd.

```

Feb  5 13:52:57 richard-laptop gnome-power-manager: (richard) Suspending computer because the DBUS method Suspend() was invoked
Feb  5 13:53:00 richard-laptop kernel: [17181244.352000] ACPI: Power Button (FF) [PWRF]
Feb  5 13:53:00 richard-laptop kernel: [17181244.352000] ACPI: Lid Switch [LID]
Feb  5 13:53:00 richard-laptop kernel: [17181244.352000] ACPI: Sleep Button (CM) [SLPB]
Feb  5 13:53:00 richard-laptop kernel: [17181244.352000] ACPI: Power Button (CM) [PWRB]
Feb  5 13:53:00 richard-laptop gnome-power-manager: (richard) Resuming computer
Feb  5 13:53:01 richard-laptop kernel: [17181244.952000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x92a0b1, caps: 0xa04713/0x200000
Feb  5 13:53:01 richard-laptop kernel: [17181244.984000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
```

and my xorg.conf (mousey bits)
```
Section "InputDevice"
	Identifier	"Synaptics Mouse"
	Driver		"synaptics"
	Option		"CorePointer
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
	Option		"HorizScrollDelta"	"0"
        Option		"SHMConfig"    		"true"
EndSection

Section "InputDevice"
        Identifier  "USB Mouse"
        Driver      "mouse"
        Option      "Protocol"         "Auto"
        Option      "Device"           "/dev/input/mice"
        Option      "ZAxisMapping"     "4 5"
        Option      "Emulate3Buttons"  "false"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Synaptics Mouse" 		"CorePointer"
	InputDevice	"USB Mouse"			"AlwaysCore"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection
```

anyone got any ideas?

the suspend2.conf is left default afaik.

---

### Post by reacocard on 2007-02-05
> **Treviño said:**
> Hi people, considering that the 2.6.20 kernel (with great new things) has been released I decided to ***compile the feisty kernel*** (actually based on that version) _**patched with suspend2**_ (2.2.9.3), but all of this under edgy!

So, I think that both feisty users and edgy ones will be able to use it! :)
Maybe, I should also recompile the restricted-modules if anyone need them, so I don't really know when I'll be able to submit my new kernels to a new "-unstable" repository, but I hope soon... :P

Simply let me know if you're interested in these new kernels ;)

Definitely interested.  Always fun to try something new. :D

---

### Post by mcarro on 2007-02-05
> **Choad said:**
> ok i wonder if anyone here can help me

i did have suspend working, *quite* reliably a while ago, but now - nothing

i think it has something to do with mouse drivers... which is a bit wierd.


Choad,

your resumption stops exactly where mine does (in the cases where it does not resume, that is).  I was blaming the agpgart module instead.

However, for some reason there was no failed hibernation since I posted the message.  I am calling the hibernation command through the script posted below (no intermediate gnome power-manager - I wanted to be in control of what is exactly being done).  The script also keeps track of what has happened during the hibernation/resumption.  Hope this is of any help.

```
#/bin/bash

WHERE=/var/tmp/hibernate/hibernate-$$.txt

do_command() {
echo >> $WHERE
echo >> $WHERE
echo BEGIN $* >> $WHERE
echo >> $WHERE

$* >> $WHERE 2>&1 

echo >> $WHERE
echo END $* >> $WHERE
echo >> $WHERE
}

touch $WHERE

do_command date 
do_command lsmod
do_command dmesg
do_command cat /etc/hibernate/common.conf
do_command cat /etc/hibernate/suspend2.conf
do_command cat /sys/power/suspend2/debug_info
do_command sudo /usr/sbin/hibernate -v4
do_command date
do_command cat /sys/power/suspend2/last_result
do_command dmesg
do_command lsmod


```

---

### Post by Ago12 on 2007-02-06
Good news, since I've switched to Feisty ;)

I need the restricted drivers for my wireless card, sadly :(

---

### Post by Treviño on 2007-02-06
Ok... I've built and packaged the new kernels (-generic, -386 and -lowlatency) they're working really fine here (great speed improvement)...

Suspension here works; resuming too... Btw I'm using the ATi Open Source drivers with AiGLX, after resuming I get a blank screen and an huge cpu usage... However switching to tty1 and then tty7 (Ctrl+alt+Fx) I can see again my resumed desktop!

Anyway I always have the CPU at 100% and it's used by the "dash" process ran by hibernate script... I've to see if I find a fix or a workaround for this because in my situation I can't use the PC at all (because I can't kill that process...).

I'll leave 

I've to ask to tuxfamily more space since I've to host also the restricted modules (the official ones should work), and all will be working ;).

Just few infos about my suspend2 situation:
> Suspend2 debugging info:
- Suspend core   : 2.2.9.3
- Kernel Version : 2.6.20-6-generic
- Compiler vers. : 4.1
- Attempt number : 0
- Parameters     : 0 81920 0 0 0 0
- Overall expected compression percentage: 0.
- Compressor is 'lzf'.
- SwapAllocator active.
  Swap available for image: 391582 pages.
- FileAllocator inactive.
- No I/O speed stats available.
- Extra pages    : 0 used/500.

---

### Post by dare2dreamer on 2007-02-06
So clarify something for me, will feisty ship with suspend2 support?

---

### Post by Treviño on 2007-02-06
> **dare2dreamer said:**
> So clarify something for me, will feisty ship with suspend2 support?
No, feisty uses normal suspend.. I've patched its sources with suspend2 patches...

Ah, I forgot to mention that I used suspend 2.2.9.3 patch for kernel 2.6.20-rc4, there are no problems while patching, but it doesn't compile if you don't add an #include <linux/sched.h> to ./include/linux/freezer.h

About the hibernate freezing problem I talked about *maybe* I've found a fix... I'll let you know soon ;)

---

### Post by Treviño on 2007-02-06
I'm glad to announce that I've fixed all the suspension/resume bugs I found (thanks to [this patch]("http://thread.gmane.org/gmane.linux.swsusp.devel/10338/focus=5731")) and now suspension/resuming works like a charm (also with AiGLX + ATi :P)!

I got also another Gb for my repository so I only have to finish my repo packages before of uploading them...

Considering I've not a feisty, maybe there will be some "bugs" with newer packages, so I'll wait your reports...

---

### Post by Ago12 on 2007-02-07
I'm ready to test on Feisty :p

Thanks :)

---

### Post by mcarro on 2007-02-07
> **Treviño said:**
> No, feisty uses normal suspend.. I've patched its sources with suspend2 patches...

Does anyone know what are the chances of suspend2 being adopted in the mainstream kernel?  I recall having read some time ago about positive comments coming from one of the kernel maintainers.

---

### Post by Treviño on 2007-02-07
Well... I don't really know which are accepted on main stream, btw reading latest changelog it doesn't seem so "next the door", in fact now is under developing again the module version of suspend2.
With no doubt swsuspend2 works better than the actual kernel suspend way, but it has many bugs yet...

> Reinstated support for building Suspend2 as modules. Requires an
  initrd/ramfs if you want to be able to resume! This is back in partly
  because I don't expect Suspend2 to be seriously considered for merging
  any time soon. If that happens, it will almost certainly go in without
  module support, because of the large number of exported symbols needed.
  That said, I like module support for embedded systems, as well as for
  my own development use.

For people who want to test the new kernels, I'm *still* uploading some debs here: [http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/](http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/)

So, try them and let me know, but that is not a repo *yet*...

---

### Post by shizeon on 2007-02-08
Hi Trevino,
  I've been using your edgy suspend2 kernel and following this thread.  Thanks for everything!  I decided to take a jump in to your new 2.6.20 kernel debs today and have it up and running.   Suspend and resume are working great.  I'm also using AiGLX and Radeon drivers with Beryl.  I used all your deb's, but grabbed the linux-restricted-modules from this link if anyone else is looking for them:

[http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/linux-restricted-modules-2.6.20-6-generic_2.6.20.1-6.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/linux-restricted-modules-2.6.20-6-generic_2.6.20.1-6.4_i386.deb)

The only issue I've seen is I am having a problem with compiling  VMWare workstation's vmmon modules using the vmware-config.pl script.  Still trying to track that down, but I know it's not related to your suspend patches.  I think it might be due to no 2.6.20 support in workstation.

```

In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;compat_exit&#8217;

```

EDIT:  Followed advise from [http://www.vmware.com/community/thread.jspa?threadID=65982&tstart=30](http://www.vmware.com/community/thread.jspa?threadID=65982&tstart=30) and got vmware working.

Thanks again!

---

### Post by Ago12 on 2007-02-08
suspend2-user-ui packages don't want to install here, since suspend2 package is missing :(

(Feisty)

---

### Post by shizeon on 2007-02-09
I ran in to a similar issue and basically just grabbed the existing 2.6.17 edgy Suspend2 packages from Trevino's site (which is just a meta package I think), then installed the new 2.6.20 ones over the top.  I'm in a slight dependency hell issue now as the package manager wants to downgrade all of these packages as part of the update process.  I'm just going to be patient for now to see if we get a repo out of these that fixes it all :)

---

### Post by Ago12 on 2007-02-09
Hum, yeah, of course, but I can't install the 2.6.17 kernel (on wich suspend2 depends), since it depends inself on packages that have been upgraded since Feisty (hal, among others, I think)

---

### Post by shizeon on 2007-02-10
I didn't have that issue, but I also have both kernels still installed (just in case). Tell dpkg to ignore that dependency and you should be on your way.  Suspend2 package is just a meta package, so everything should work.  In fact, I just removed the Suspend2 package myself and ran the command below to stop update manager from complaining.

```

sudo dpkg --ignore-depends=suspend2 -i suspend2* 

```

Just dawned on me from your previous post, you are running Feisty.  If I read Trevino's threads right, his packages mentioned in the last couple posts are the feisty kernel, but compiled for Edgy.

---

### Post by Ago12 on 2007-02-10
Ok, I got it, but I have to choose between having 4 broken packages and one broken package :/

It should be pretty easy to repackage it with the good dependencies, but I really do have problems with packaging :D

---

### Post by Treviño on 2007-02-10
I'll fix it soon... Btw about the restricted modules you've used** shizeon**, aren't they the same I've hosted? :o

---

### Post by shizeon on 2007-02-11
Hi Trevino, something had a dependency for the linux-restricted-modules-common_2.6.20.1-6.4_all.deb (I think it was your restricted modules deb).  I didn't find that  one at [http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/](http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/) when I was playing around.  Thanks again.

---

### Post by Ago12 on 2007-02-12
> **Treviño said:**
> I'll fix it soon... Btw about the restricted modules you've used** shizeon**, aren't they the same I've hosted? :o

Thanks a lot Trevi :)

---

### Post by Treviño on 2007-02-12
> **shizeon said:**
> Hi Trevino, something had a dependency for the linux-restricted-modules-common_2.6.20.1-6.4_all.deb (I think it was your restricted modules deb).  I didn't find that  one at [http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/](http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/) when I was playing around.  Thanks again.Ok, thank you for reporting... I'll add the package soon, but that seems to beo only a *meta*-package :P

Btw, it seems there's a [new ubuntu kernel release]("http://packages.ubuntu.com/edgy/base/linux-image-2.6.17-11-generic") to be patched and repackaged... I'll do the work on next days... Until then stay with latest patched kernel (if you don't use the feisty one :P)

---

### Post by Treviño on 2007-02-16
I've updated the standard **Edgy kernels**, now you can update and getting back your suspend2 :)

---

### Post by Ago12 on 2007-02-16
Trevi, go Feisty, go! [/evil]

:D

---

### Post by loko on 2007-02-16
trevino, i want to install suspend2 but it will downgrade to kernel 2.6.17-10, i have your kernel 2.6.17-11 installed, where is the problem?

btw. some other things: suspend.ram - command not found, did understand your post wrong?

and the other thing is that i have my swap on /dev/hda6 but it is encrypted so it is linked to /dev/mapper/cryptswap

i think i should insert  resume2=swap:/dev/mapper/cryptswap?

i see this tip in the terminal:
> You will then need to either reboot
after doing so or set it manually (this time only) using:
    echo swap:/dev/hdaX > /sys/power/suspend2/resume2
hibernate: Aborting.



if i try this, i get:

> user@user-laptop:~$ sudo echo swap:/dev/mapper/swap > /sys/power/suspend2/resume2
bash: /sys/power/suspend2/resume2: Permission denied


i know i should enter this in grub, but i am not sure, so i want to test it first temporarily.

is there a solution for this?

---

### Post by reacocard on 2007-02-16
> **loko said:**
> trevino, i want to install suspend2 but it will downgrade to kernel 2.6.17-10, i have your kernel 2.6.17-11 installed, where is the problem?

btw. some other things: suspend.ram - command not found, did understand your post wrong?

and the other thing is that i have my swap on /dev/hda6 but it is encrypted so it is linked to /dev/mapper/cryptswap

i think i should insert  resume2=swap:/dev/mapper/cryptswap?

i see this tip in the terminal:



if i try this, i get:



i know i should enter this in grub, but i am not sure, so i want to test it first temporarily.

is there a solution for this?

try
```

sudo -s -H
echo swap:/dev/mapper/swap > /sys/power/suspend2/resume2

```
for some reason, sudo and redirects don't like each other much, so it's easier to just become root and then enter the command.

---

### Post by loko on 2007-02-17
thanks reacocard,

the tip with the sudo -s -H worked, i didn't get any error message then.

it hibernates, but didn't awake, the OS was booted like normal.

i've looked into the howto, because my swap is encrypted with dm-crypt (cryptsetup),

but i didn't understand what exactly i have to modify/edit etc.

can somebody help me with that please?

Also hibernat-ram didn't work, the screen gets black, in the upper left corner there is blinking a white cursor and thats all.

---

### Post by reacocard on 2007-02-17
> **loko said:**
> thanks reacocard,

the tip with the sudo -s -H worked, i didn't get any error message then.

it hibernates, but didn't awake, the OS was booted like normal.

i've looked into the howto, because my swap is encrypted with dm-crypt (cryptsetup),

but i didn't understand what exactly i have to modify/edit etc.

can somebody help me with that please?

Also hibernat-ram didn't work, the screen gets black, in the upper left corner there is blinking a white cursor and thats all.

Well, the normal way to add the resume partition is to edit this line in your /boot/grub/menu.lst:
```
# defoptions=quiet splash
```
so that it looks like this:
```
# defoptions=quiet splash resume2=swap:/dev/hdaX
```
where /dev/hdaX is your swap partition. In your case, this probably needs to be /dev/mapper/cryptswap or /dev/hda6.

If this method fails, you could try using the filewriter instead.

---

### Post by Erwin123 on 2007-02-18
> **blk_jack said:**
> Tried to install it on my amd64 machine and there were missing 64bit packages that prevented the installation.

It sounds like you've got a great thing going here and I was wondering when/if you'll have those missing packages for amd64?

Thanks! 8)

This messages hasn't been replied for two month now...  ):P 

Are there any 64bit binaries of suspend2 planned for edgy? Is there a severe difference to 32bit? Should I try to compile them myself, or is this a hopeless venture?

Erwin

---

### Post by loko on 2007-02-19
i cannot get it to work with dm-crypt encrypted swap.

neither resume2=swap:/dev/hda4, or /dev/mapper/swap did it.

So can somebody help me with this?

EDIT: I realized that i cannot use suspend2 with dm-crypt when the key for the encrypted swap is generated randomly.

So i have to use filewriter, but at this point i stuck, i don't know how to set this up.

---

### Post by reacocard on 2007-02-19
> **loko said:**
> i cannot get it to work with dm-crypt encrypted swap.

neither resume2=swap:/dev/hda4, or /dev/mapper/swap did it.

So can somebody help me with this?

EDIT: I realized that i cannot use suspend2 with dm-crypt when the key for the encrypted swap is generated randomly.

So i have to use filewriter, but at this point i stuck, i don't know how to set this up.

Here: [http://www.suspend2.net/HOWTO-2.html#ss2.5](http://www.suspend2.net/HOWTO-2.html#ss2.5)
It appears you enable it in /etc/hibernate/suspend2.conf, then run
```
sudo hibernate --no-suspend
```
then use the output of
```
cat /sys/power/suspend2/resume2
```
instead of swap:/dev/hdaX in your kernel parameters.

---

### Post by Treviño on 2007-02-19
**loko**, why did you have to downgrade? I've uploaded newer packages few days ago... You should have the same version that is released by Ubuntu devs...

**Ago12**, I'd like to do that, but it whould make harder for me packaging for edgy users...

**Erwin123**, in my repo you find also the source files, download them and have fun your self... Unfortunately I've no 64bit hardware... :/

---

### Post by loko on 2007-02-20
> **Treviño said:**
> **loko**, why did you have to downgrade? I've uploaded newer packages few days ago... You should have the same version that is released by Ubuntu devs...

@Treviño: 

First, if i want to install the 'suspend2-metapackage' or the 'suspend2-userui...' synaptic also wants to install linux-image-2.6.17-10-generic and some other stuff, but this is curious because i have your 'linux-image-2.6.17-11-generic' installed. So why it will downgrade?

Maybe the dependencies of this package are wrong?

Second, 

i realized that i cannot use hibernate to swap when the swap is encrypted by a randomly generated number.
So i want to use filewriter.

But you did not put it into the kernel, is it possible to do that?

Here is a short error-message:

> user@user-laptop:~$ sudo hibernate --no-suspend
hibernate: WARNING: Filewriter location given, but kernel does not have filewriter
hibernate: support. Ignoring.


---

### Post by Ago12 on 2007-02-20
> **Treviño said:**
> **loko**, why did you have to downgrade? I've uploaded newer packages few days ago... You should have the same version that is released by Ubuntu devs...

**Ago12**, I'd like to do that, but it whould make harder for me packaging for edgy users...

**Erwin123**, in my repo you find also the source files, download them and have fun your self... Unfortunately I've no 64bit hardware... :/

Arf :)

Anyway, the stock Ubuntu kernel now hibernates on my lappy.

However, I have to run "hibernate" as root, and it's not as fast as suspend2 :p

---

### Post by Ago12 on 2007-02-20
Only one thing: that would be nice to write a nice howto with all the details. This way, anybody could do it (on wichever kernel, on 64bits, etc...) and set its own optimizations.

It would be soo hellful! :)

Even if I know it's a hard work...

Even if you write it in Italiano :p

---

### Post by Treviño on 2007-02-20
Ok, ok... But it isn't so hard... I'll post it in my blog, then I'll translate it for this forums, but wait few days :)

---

### Post by Erwin123 on 2007-02-20
@Trevino

I didn't want to compile the packages myself, especially not the kernel... But I'll give it a try. What do a have to do? A naive start failed:

> >apt-get -b source suspend2
Reading package lists... Done
Building dependency tree
Reading state information... Done
Need to get 3444B of source archives.
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/suspend2 suspend2 2.2.9+3v1ubuntu0 (dsc)
  404 Not Found
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/suspend2 suspend2 2.2.9+3v1ubuntu0 (tar)
  404 Not Found
Failed to fetch [http://download.tuxfamily.org/3v1deb/pool/edgy/suspend2/suspend2_2.2.9+3v1ubuntu0.dsc](http://download.tuxfamily.org/3v1deb/pool/edgy/suspend2/suspend2_2.2.9+3v1ubuntu0.dsc)  404 Not Found
Failed to fetch [http://download.tuxfamily.org/3v1deb/pool/edgy/suspend2/suspend2_2.2.9+3v1ubuntu0.tar.gz](http://download.tuxfamily.org/3v1deb/pool/edgy/suspend2/suspend2_2.2.9+3v1ubuntu0.tar.gz)  404 Not Found
E: Failed to fetch some archives.


---

### Post by Ago12 on 2007-02-20
Oh cool, thanks Trevi :)

I've never been able to package the restircted modules (I used to symlink them, not that cool).
Plus, I'd like to know how you package the scripts and so on  :)

If you d'on't mind, I'll translate your howto to French (and I'll give you the credits, of course :p)


Thaks thanks thanks :)

---

### Post by pelago on 2007-02-24
Hi, this seems to be the most active thread for suspend2 issues in Ubuntu so if I may I'd like to ask some questions in here.

I used to have suspend2 working well in dapper using the compiled kernels from [http://www.ucc.asn.au/~dagobah/dapper-kernels/](http://www.ucc.asn.au/~dagobah/dapper-kernels/) which was fine until Ubuntu updated the kernel and dagobah didn't update the repo. I've got no experience in compiling kernels so I'm interested in your work to get it working again. I'd be very interested to read your howto if you can write one.

In the meantime, I was reading on [http://www.suspend2.net/](http://www.suspend2.net/) that soon suspend2 will be able to be compiled as modules. Does this mean that we can use the main Ubuntu-supplied kernel and just download a smaller module from you to get suspend to work? If so this would be good for you as it would mean you could save hosting disk space, and it would be good for me as I would feel slightly more secure using the official Ubuntu kernel (although I realise that running any third-party kernel modules is theoretically insecure).

Also, would compiling as modules mean that if Ubuntu updated the kernel because of a security problem, I wouldn't have to wait until you updated your repo too, as the existing module version would still work on the updated kernel?

---

### Post by reacocard on 2007-02-24
> **pelago said:**
> Hi, this seems to be the most active thread for suspend2 issues in Ubuntu so if I may I'd like to ask some questions in here.

I used to have suspend2 working well in dapper using the compiled kernels from [http://www.ucc.asn.au/~dagobah/dapper-kernels/](http://www.ucc.asn.au/~dagobah/dapper-kernels/) which was fine until Ubuntu updated the kernel and dagobah didn't update the repo. I've got no experience in compiling kernels so I'm interested in your work to get it working again. I'd be very interested to read your howto if you can write one.

In the meantime, I was reading on [http://www.suspend2.net/](http://www.suspend2.net/) that soon suspend2 will be able to be compiled as modules. Does this mean that we can use the main Ubuntu-supplied kernel and just download a smaller module from you to get suspend to work? If so this would be good for you as it would mean you could save hosting disk space, and it would be good for me as I would feel slightly more secure using the official Ubuntu kernel (although I realise that running any third-party kernel modules is theoretically insecure).

Also, would compiling as modules mean that if Ubuntu updated the kernel because of a security problem, I wouldn't have to wait until you updated your repo too, as the existing module version would still work on the updated kernel?

With modules, you probably would be able to use the stock Ubuntu kernel, but when the kernel updated, you still have to get a version of the modules compiled for the new kernel. However, recreating such modules should be much easier and faster than updating the whole kernel, so updates would likely come faster.

---

### Post by Treviño on 2007-02-24
I read about the module support days ago, but I was wondering how could I compile just the module seen that there aren't stand-alone sources, so to get a suspend2 module compiled I'd need to compile all the kernel itself...

So, is it really a good choice?

---

### Post by reacocard on 2007-02-24
> **Treviño said:**
> I read about the module support days ago, but I was wondering how could I compile just the module seen that there aren't stand-alone sources, so to get a suspend2 module compiled I'd need to compile all the kernel itself...

So, is it really a good choice?

Depends on how well it works. It'd be nice to just have to compile the modules alone though, someone should suggest that to the suspend2 devs.

---

### Post by pelago on 2007-02-25
I don't know how you go about compiling it as a module - maybe the support isn't actually there yet as the announcement said it was coming soon. reacocard says that a new module will need to be compiled if a new kernel comes out - I wonder if that depends how big a jump the new kernel is? For example, if Ubuntu upgraded from 2.6.15-22 to 2.6.15-23 then it's still a 2.6.15 kernel and so the module might still work, I think. Only if the kernel upgraded from 2.6.15 to 2.6.16, say, would we need a new module.

Another advantage of releasing suspend2 as modules, if such a thing is possible, is that some people might already have custom kernels for other reasons (e.g. low latency) rather than stock Ubuntu kernels. Being able to just 'slot in' your module would be great, if it was possible.

---

### Post by Ago12 on 2007-02-25
It would be great if we could compile it with module-assisatant or something similar.

BTW, where is the annoncement?

---

### Post by reacocard on 2007-02-25
> **pelago said:**
> I don't know how you go about compiling it as a module - maybe the support isn't actually there yet as the announcement said it was coming soon. reacocard says that a new module will need to be compiled if a new kernel comes out - I wonder if that depends how big a jump the new kernel is? For example, if Ubuntu upgraded from 2.6.15-22 to 2.6.15-23 then it's still a 2.6.15 kernel and so the module might still work, I think. Only if the kernel upgraded from 2.6.15 to 2.6.16, say, would we need a new module.

Unfortunately, no. I have to recompile the kqemu module every time there is a new kernel, same thing happens for vmware modles and graphics drivers. Any new version == new module.
> Another advantage of releasing suspend2 as modules, if such a thing is possible, is that some people might already have custom kernels for other reasons (e.g. low latency) rather than stock Ubuntu kernels. Being able to just 'slot in' your module would be great, if it was possible.
Probably wouldn't work, for the same reason as above, but I might be wrong. Just enabling low latency or something like that might be a small enough change that it wouldn't be necessary to recompile the modules.

---

### Post by mcarro on 2007-02-25
> **reacocard said:**
> Unfortunately, no. I have to recompile the kqemu module every time there is a new kernel, same thing happens for vmware modles and graphics drivers. Any new version == new module.

However, compiling a module is (in my experience, at least, with pwc.ko -- correct me if I am wrong) much easier than compiling a whole kernel, as it only needs the kernel headers.  So many users will be able to compile it themselves painlessly.

---

### Post by reacocard on 2007-02-25
> **mcarro said:**
> However, compiling a module is (in my experience, at least, with pwc.ko -- correct me if I am wrong) much easier than compiling a whole kernel, as it only needs the kernel headers.  So many users will be able to compile it themselves painlessly.

Exactly. It takes, what, 5 min. & 3 commands to recompile a module? Considerably less than for the whole kernel.

On another note, if it can be compiled as modules, there's no longer any reason why it couldn't be included in Ubuntu. The devs are against compiling it into the main kernel, but having the modules available in a separate package in universe would probably go over very well.

---

### Post by pelago on 2007-02-26
> **Ago12 said:**
> It would be great if we could compile it with module-assisatant or something similar.

BTW, where is the annoncement?
The module announcement is on [http://www.suspend2.net/](http://www.suspend2.net/) under "28 December 2006: What's coming soon." Also see the HOWTO at [http://www.suspend2.net/HOWTO-7.html#ss7.1](http://www.suspend2.net/HOWTO-7.html#ss7.1) but ignore the FAQ at [http://www.suspend2.net/FAQ-4.html#ss4.5](http://www.suspend2.net/FAQ-4.html#ss4.5) which is out of date. What I can't seem to find is any instructions on how to compile it as modules, even in the mailing list, although maybe the instructions are in a README in the download itself, as I haven't looked there.

It's a shame if a new module would need to be released even for minor kernel upgrades or kernel variations - I didn't realise it was that sensitive. But it would still be a smaller package to distribute, even if you did have to recompile it every time. I like the idea that it could be included in an official Ubuntu repository too, although that might take a bit of work.

---

### Post by reacocard on 2007-02-26
> **pelago said:**
> The module announcement is on [http://www.suspend2.net/](http://www.suspend2.net/) under "28 December 2006: What's coming soon." Also see the HOWTO at [http://www.suspend2.net/HOWTO-7.html#ss7.1](http://www.suspend2.net/HOWTO-7.html#ss7.1) but ignore the FAQ at [http://www.suspend2.net/FAQ-4.html#ss4.5](http://www.suspend2.net/FAQ-4.html#ss4.5) which is out of date. What I can't seem to find is any instructions on how to compile it as modules, even in the mailing list, although maybe the instructions are in a README in the download itself, as I haven't looked there.

Note the 'coming soon' in the announcement's title. The module method hasn't been released yet.

> It's a shame if a new module would need to be released even for minor kernel upgrades or kernel variations - I didn't realise it was that sensitive. But it would still be a smaller package to distribute, even if you did have to recompile it every time. I like the idea that it could be included in an official Ubuntu repository too, although that might take a bit of work.
Exactly. It's too late for feisty, but we can do a 3rd party repo for feisty and look to getting it in Ubuntu for feisty+1 or +2.

---

### Post by harty83 on 2007-02-27
I installed everything from the edgy/suspend2 repository (I think) to get suspend2 going.  I added "resume=swap:/dev/sda3" to the kernel line in grub.  When I run the hibernate script, my system acts as if it hibernated.  But when I turn the computer back on, it starts up as if I had shutdown my computer rather than hibernate.  

Any ideas what I did or didn't do?

Also, the patched kernel seemed to kill my intel hda sound card; my system wouldn't recognize it.  I tried to manually reinstall them using the latest alsa drivers but that didn't seem to work either (when it did with the official releases). Is there something I'm missing with that too?
**Edit: ** I fixed the sound so never mind with that.

Thanks!

---

### Post by reacocard on 2007-02-27
> **harty83 said:**
> ... I added "resume=swap:/dev/sda3" to the kernel line ...

It should be resume2, not resume.

---

### Post by harty83 on 2007-02-27
> **reacocard said:**
> It should be resume2, not resume.

Oops, that was a typo.  I did have resume2.

---

### Post by reacocard on 2007-02-27
> **harty83 said:**
> Oops, that was a typo.  I did have resume2.

Can you attach your grub.conf?

---

### Post by harty83 on 2007-02-27
Actually, I think I got it working now.  I downgraded to the officials and uninstalled all suspend2 stuff.  Then upgraded again, reinstalled, set resume2=swap:/dev/sda3 in my grub config and bam it works!  Weird...guess something just didn't get configured right during the install?

When I hibernate, I get an error message about not finding "/dev/fb0" but it doesn't seem to affect anything.  Is this normal?

Thanks for your quick replies!

---

### Post by reacocard on 2007-02-28
> **harty83 said:**
> Actually, I think I got it working now.  I downgraded to the officials and uninstalled all suspend2 stuff.  Then upgraded again, reinstalled, set resume2=swap:/dev/sda3 in my grub config and bam it works!  Weird...guess something just didn't get configured right during the install?

When I hibernate, I get an error message about not finding "/dev/fb0" but it doesn't seem to affect anything.  Is this normal?

Thanks for your quick replies!

Not normal that I know of, but it's probably just trying to use fbsplash and failing. Just switch to the text-mode ui and that message will probably go away (and you'll get a progress meter too!)

---

### Post by Treviño on 2007-03-03
Hi, I'd like to know which kind of kernels are you using, I mean I think that most (all) of you are using the *-generic kernel; should I continue compiling the *-386 kernel (default only for pre-pentium2 machines, and maybe without a decent acpi at all) and the *-lowlatency one?

I don't really know if that extra spent time (just by my CPU), is really usefull for some one... :o

---

### Post by shizeon on 2007-03-03
Using the generic one here.

---

### Post by reacocard on 2007-03-03
I use -386, since its rather faster on my machine. Beryl jumped from <20fps to ~30fps in cube mode from just this change. It's probably because I have a single-core system, so the SMP support in -generic slows it down. However, if you would post that compiling HOWTO sometime, I wouldn't mind maintaining the -386 series on my own.

---

### Post by mcarro on 2007-03-04
> **reacocard said:**
> I use -386, since its rather faster on my machine. Beryl jumped from <20fps to ~30fps in cube mode from just this change. It's probably because I have a single-core system, so the SMP support in -generic slows it down. However, if you would post that compiling HOWTO sometime, I wouldn't mind maintaining the -386 series on my own.

I am using the -generic in a single-core system too, because I read somewhere that that was going to be the defaul stock kernel.  However, I did not suspect that this would introduce such a slowdown.  May this be beryl-specific?  (I am not using beryl, but I may consider switching to it at some point).

---

### Post by Treviño on 2007-03-04
Mh, ok... I'll keep compiling the 386 kernel, but the lowlatency I think is not much used (just by musicians but I think thare are not many here :P)

---

### Post by reacocard on 2007-03-04
> **Treviño said:**
> Mh, ok... I'll keep compiling the 386 kernel, but the lowlatency I think is not much used (just by musicians but I think thare are not many here :P)

Thanks. Are you ever going to post that HOWTO? I'd like to actually have time to compile the kernel a couple times before feisty.

---

### Post by Treviño on 2007-03-04
I'm doing that, but I'd like to post something of much generic so I've to find some easy workarounds :P

---

### Post by Ago12 on 2007-03-05
O//

---

### Post by therobbot on 2007-03-05
Hi,

first of all thanks a lot for making this package. Most of the time it works really well. However I have a strange problem. 

Sometimes it freezes while displaying the message

"Seeking to free XX MB of memory"

It seems that sometimes it freezes if the amount is very high. But sometimes it also freezes when just trying to seek 10 MB and sometimes it works even though it frees about 50 MB. I also don't quite understand why it does that since my swap space is 1GB and my RAM only 512 MB. Also sometimes it freezes even though I didn't do any memory-intensive work.

By "freezing" I mean that it stops suspending, returns to KDE, the mouse isn't working anymore, everything else is really slow and when I try to shut the PC down it goes down but isn't able to turn the mainboard off anymore.

Do you have any idea what I could do about this? I'd be extremely thankful for any help. 

The strange thing is: last week I used Beryl and during this time the problem was exactly the other way round: it always suspended but on resume the screen stayed black.

Tobias

Kubuntu 6.10
AMD Athlon 2400+
Radeon 9600, 256MB
512MB main memory

---

### Post by Treviño on 2007-03-05
Well, about first issue, I'd recommend to increase your swap space, in fact also if your ram fits the swap space, most of times your swap is used (use *free -h* to see) and maybe more than 512mb, so all the memory data doesn't fit the swap space...

Then, about the black screen on resuming when using Beryl, if you're using AiGLX [this is the cause]("http://lists.suspend2.net/lurker/message/20070212.175119.9fba4357.en.html"), and so the easiest way to fix (if you don't want repackage xorg 7.1 your own) is [upgrade to Xorg 7.2]("http://ubuntuforums.org/showthread.php?t=373087") as shown here.

If you're using fglrx, instead, [read here]("http://wiki.cchtml.com/index.php/Suspend2").

Bye

---

### Post by therobbot on 2007-03-05
Hi,

thanks for the quick reply. I just created a swap space with 3GB. I'll see if it will occur anymore. 

About the Aiglx bug... this sounds reasonable. However, I tried your Xorg 7.2 packages on a test partition and got some weird behaviour. But at the moment I don't plan to use it permanently anyway since even with 7.2, my computer only feels smooth if I switch to 16 bit so I guess I'll wait till I have a new PC and 3D-Desktops are less buggy before switching...

But thanks anyway. 

Tobias

---

### Post by Treviño on 2007-03-05
Ok, so try to patch the xorg-core your self if you want... It's quite easy

---

### Post by dcerdil on 2007-03-06
OK I have this chicken and egg problem. I downloaded suspend2 packages and installed them. 

I don't have a swap partition, so following the FAQ here: [http://www.suspend2.net/HOWTO-2.html#ss2.5](http://www.suspend2.net/HOWTO-2.html#ss2.5), I set up a hibernate file with dd, specified the file in /etc/hibernate/suspend2.conf, and then ran 

hibernate --no-suspend

to specify the file in /sys/power/suspend2/resume2

but I am getting the following error:

# hibernate --no-suspend
hibernate: WARNING: Filewriter location given, but kernel does not have filewriter
hibernate: support. Ignoring.
You haven't specified a resume2= parameter on your kernel command line

Your GRUB or LILO config should have something like resume2=swap:/dev/hdaX
where /dev/hdaX is your swap partition. You will then need to either reboot
after doing so or set it manually (this time only) using:
    echo swap:/dev/hdaX > /sys/power/suspend2/resume2
hibernate: Aborting.
# 

Well, how is it that I need to know the name of the file to specify the name of the file to know the name of the file??? 

Obviously I am missing the point, but where?

TIA.

---

### Post by Treviño on 2007-03-06
I'm not sure about it but you should however put a command line parameter to load your kernel, maybe is something like resume2=file:/your/swap/file

*EDIT*: I was partially wrong, I've found more infos in [this wiki]("http://gentoo-wiki.com/HOWTO_Software_Suspend_v2#Using_File_Writer"), follow that instructions and let's know if they work as advertised ;)

---

### Post by dcerdil on 2007-03-08
Well, the URL I gave above also talks about the same thing. 

Here is the problem stated again, with a bit more detail:

I created a swap file for hibernation at root, so my swap file is called /hibernate-file, of size 2GB (my physical memory size)

NOW, to tell grub which file to read hibernation data from, I need to somehow know that 0xXXXXX magic string to specify as "resume2" parameter in grub's menu.lst

To do that, I should run "hibernate --no-suspend", right? That's my understanding of those two HOWTO sites. 

SO, when I do "hibernate --no-suspend", supposedly something will show up in /sys/power/suspend2/resume2 in the form "file:/dev/sda4:0xXXXXXX", which would be a handle to my "/hibernate-file". I will copy that string to menu.lst in grub, and voila! Everything will be perfect.

I can't just make some numbers and hope that it will refer to my /hibernate-file. Somebody (read: a program) should tell me the magic string handle to my /hibernate-file. 

According to the HOWTOs, that somebody is the command "hibernate --no-suspend"

BUT when I run "hibernate --no-suspend", instead of writing my magic string to /sys/power/suspend2/resume2, it complains that I haven't specified anything in "resume2" parameter in grub!

Argh!

---

### Post by reacocard on 2007-03-08
> **dcerdil said:**
> Well, the URL I gave above also talks about the same thing. 

Here is the problem stated again, with a bit more detail:

I created a swap file for hibernation at root, so my swap file is called /hibernate-file, of size 2GB (my physical memory size)

NOW, to tell grub which file to read hibernation data from, I need to somehow know that 0xXXXXX magic string to specify as "resume2" parameter in grub's menu.lst

To do that, I should run "hibernate --no-suspend", right? That's my understanding of those two HOWTO sites. 

SO, when I do "hibernate --no-suspend", supposedly something will show up in /sys/power/suspend2/resume2 in the form "file:/dev/sda4:0xXXXXXX", which would be a handle to my "/hibernate-file". I will copy that string to menu.lst in grub, and voila! Everything will be perfect.

I can't just make some numbers and hope that it will refer to my /hibernate-file. Somebody (read: a program) should tell me the magic string handle to my /hibernate-file. 

According to the HOWTOs, that somebody is the command "hibernate --no-suspend"

BUT when I run "hibernate --no-suspend", instead of writing my magic string to /sys/power/suspend2/resume2, it complains that I haven't specified anything in "resume2" parameter in grub!

Argh!

Did you set FilewriterLocation correctly in /etc/hibernate/suspend2.conf? If you did, try setting the VerifyFilewriterResume2 parameter to no.

---

### Post by Treviño on 2007-03-08
Try to run as

*hibernate --force --no-suspend*

---

### Post by dcerdil on 2007-03-08
Here is my suspend2.conf stanza:

## For filewriter:
FilewriterLocation /hibernate-image 2048
VerifyFilewriterResume2 no

here is my hibernate file:

erdil@daydreamer:~$ ls -lah /hibernate-image 
-rw-r--r-- 1 root root 2.0G 2007-03-06 19:34 /hibernate-image

I tried both (setting Verify... to no, and using --force). Neither one works:

erdil@daydreamer:~$ sudo hibernate --no-suspend
hibernate: WARNING: Filewriter location given, but kernel does not have filewriter
hibernate: support. Ignoring.
You haven't specified a resume2= parameter on your kernel command line

Your GRUB or LILO config should have something like resume2=swap:/dev/hdaX
where /dev/hdaX is your swap partition. You will then need to either reboot
after doing so or set it manually (this time only) using:
    echo swap:/dev/hdaX > /sys/power/suspend2/resume2
hibernate: Aborting.
erdil@daydreamer:~$ more /sys/power/suspend2/resume2 

erdil@daydreamer:~$ sudo hibernate --no-suspend --force
hibernate: WARNING: Filewriter location given, but kernel does not have filewriter
hibernate: support. Ignoring.
You haven't specified a resume2= parameter on your kernel command line

Your GRUB or LILO config should have something like resume2=swap:/dev/hdaX
where /dev/hdaX is your swap partition. You will then need to either reboot
after doing so or set it manually (this time only) using:
    echo swap:/dev/hdaX > /sys/power/suspend2/resume2
hibernate: Aborting.
erdil@daydreamer:~$

---

### Post by cookfromfrozen on 2007-03-08
Treviño, if it is not too much trouble, could you please provide instructions on exactly how you built this kernel and with what .config file?

I am trying to build my own kernel, and it mostly works, but I figure I am doing something wrong somewhere because cryptsetup breaks, but on your kernel, and every other "custom" kernel I've tried, it works, so it must be something I am doing wrong.

I would highly appreciate any sort of guide etc. on how you went about compiling this kernel.  I've used guides on the Internet, but there must be something I'm doing wrong to compile a kernel specifically for Ubuntu.

Apologies that this is not related to suspend2, but any help would be appreciated.

---

### Post by ecoxmit on 2007-03-08
I am having the same problems documented here regarding NetworkManager after resuming. Can anybody post the particular fix they have used to correct this?

---

### Post by Ago12 on 2007-03-09
sudo /etc/dbus-1/event.d/25NetworkManager restart

And I've seen one day a post on this forum to automagicaly do it, using init scripts.

But I don't want to mess them up atm, since I'm using Feisty: maybe they will fix it, so I'm waiting ;)

---

### Post by reacocard on 2007-03-11
> **Ago12 said:**
> sudo /etc/dbus-1/event.d/25NetworkManager restart

And I've seen one day a post on this forum to automagicaly do it, using init scripts.

But I don't want to mess them up atm, since I'm using Feisty: maybe they will fix it, so I'm waiting ;)

Just add
```
### Restart Network Manager to get new wireless listings
OnSuspend 40 /etc/dbus-1/event.d/25NetworkManager stop
OnResume 40 /etc/dbus-1/event.d/25NetworkManager start
```
to /etc/hibernate/common.conf, no init script needed.

---

### Post by cookfromfrozen on 2007-03-14
> **cookfromfrozen said:**
> Treviño, if it is not too much trouble, could you please provide instructions on exactly how you built this kernel and with what .config file?

I am trying to build my own kernel, and it mostly works, but I figure I am doing something wrong somewhere because cryptsetup breaks, but on your kernel, and every other "custom" kernel I've tried, it works, so it must be something I am doing wrong.

I would highly appreciate any sort of guide etc. on how you went about compiling this kernel.  I've used guides on the Internet, but there must be something I'm doing wrong to compile a kernel specifically for Ubuntu.

Apologies that this is not related to suspend2, but any help would be appreciated.
Could really use any help with this.

---

### Post by wpoeyer on 2007-03-14
Suspend to ram and disk works ok on my Laptop, the only problem wihtout solution as far as i know and find is resuming.
When i resume my cpu frequency scaling is not working anymore, it seems to be locked at the higest speed.

Maybe somebody know a solution?

---

### Post by reacocard on 2007-03-14
> **wpoeyer said:**
> Suspend to ram and disk works ok on my Laptop, the only problem wihtout solution as far as i know and find is resuming.
When i resume my cpu frequency scaling is not working anymore, it seems to be locked at the higest speed.

Maybe somebody know a solution?

Is that all the time, or just if you hibernate on AC, and then resume on Battery? If so, you'll just have to prod acpi into checking the AC adaptor state each time you resume, by adding this to /etc/hibernate/common.conf:
```
### Force ACPI to check AC adaptor state
OnResume 20 /etc/acpi/power.sh
```

If that isn't it/doesn't work, try this in a console and see if it works:
```
sudo cpufreq-set -g ondemand
```

---

### Post by mintcoffee on 2007-03-15
Hi all,

I'm using the suspend2 kernel from this thread, and I have a core 2 duo. It seems like only one of the CPUs (CPU1) is being reactivated when I resume. CPU0 does not even have the /sys/devices/system/cpu/cpu0/online file at all.

Anyone have any solutions to this problem?

Thanks,
Steven

---

### Post by harty83 on 2007-03-15
All was working well for a long time but then all of a sudden, I cannot hibernate or suspend.  It just resume immediately without hibernating or suspending.  I can't find anything in the logs to indicate why.

Is anyone else having this problem?  Does anyone know what could possibly be causing this?

Thanks!
Alan

---

### Post by Treviño on 2007-03-15
Read dmesg output or /etc/log/hibernate.log

---

### Post by harty83 on 2007-03-15
> **Treviño said:**
> Read dmesg output or /etc/log/hibernate.log

I already have and there is absolutely nothing regarding why the problem.  There isn't anything for today in my hibernate.log file and no obvious issues in dmesg.  I opened the system log, hibernated (which does not work) then look at the logs.  Nothing new is added.

---

### Post by reacocard on 2007-03-15
> **harty83 said:**
> I already have and there is absolutely nothing regarding why the problem.  There isn't anything for today in my hibernate.log file and no obvious issues in dmesg.  I opened the system log, hibernated (which does not work) then look at the logs.  Nothing new is added.

Does doing
```
sudo hibernate -v3
```
in a terminal give you anything helpful?

---

### Post by harty83 on 2007-03-15
> **reacocard said:**
> Does doing
```
sudo hibernate -v3
```
in a terminal give you anything helpful?

That told me I had a nasty little mistype in my common.conf file.  Fixed that and all works again!

Thanks!

---

### Post by WolfEng on 2007-03-21
Has anybody found a solution for the frequency scaling not working anymore?? I can use hibernate with no problem but the first time i used it my cpu0 blocked at 100% scaling, not having reboot or anything, i used hibernate again, and my cpu1 got also blocked. 
I read i may have something to do with the acpi not being able to read its configuration file. Is there a way to fix this??? Thanks in advance!!

---

### Post by reacocard on 2007-03-22
> **WolfEng said:**
> Has anybody found a solution for the frequency scaling not working anymore?? I can use hibernate with no problem but the first time i used it my cpu0 blocked at 100% scaling, not having reboot or anything, i used hibernate again, and my cpu1 got also blocked. 
I read i may have something to do with the acpi not being able to read its configuration file. Is there a way to fix this??? Thanks in advance!!

Try doing
```
sudo /etc/init.d/acpid restart
```
after this happens. If that solves it, you'll just have to add that to your hibernate script configuration.

---

### Post by mintcoffee on 2007-03-22
> **WolfEng said:**
> Has anybody found a solution for the frequency scaling not working anymore?? I can use hibernate with no problem but the first time i used it my cpu0 blocked at 100% scaling, not having reboot or anything, i used hibernate again, and my cpu1 got also blocked. 
I read i may have something to do with the acpi not being able to read its configuration file. Is there a way to fix this??? Thanks in advance!!

What CPU do you have? I have an Intel T7200 and I had the same issue. I ended up compiling the 2.6.20 kernel, and most of my problems have gone away.

The ACPI daemon seemed to be functioning fine for me.

---

### Post by Treviño on 2007-03-23
If you want you can test the 2.6.20.x packages I've built some time ago for testing: [http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/](http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/)

I'm using those and are working great ;)

---

### Post by pelago on 2007-03-24
> **dcerdil said:**
> OK I have this chicken and egg problem. I downloaded suspend2 packages and installed them. 

I don't have a swap partition, so following the FAQ here: [http://www.suspend2.net/HOWTO-2.html#ss2.5](http://www.suspend2.net/HOWTO-2.html#ss2.5), I set up a hibernate file with dd, specified the file in /etc/hibernate/suspend2.conf, and then ran 

hibernate --no-suspend

to specify the file in /sys/power/suspend2/resume2

but I am getting the following error:

# hibernate --no-suspend
hibernate: WARNING: Filewriter location given, but kernel does not have filewriter
hibernate: support. Ignoring.
You haven't specified a resume2= parameter on your kernel command line

Your GRUB or LILO config should have something like resume2=swap:/dev/hdaX
where /dev/hdaX is your swap partition. You will then need to either reboot
after doing so or set it manually (this time only) using:
    echo swap:/dev/hdaX > /sys/power/suspend2/resume2
hibernate: Aborting.
# 

Well, how is it that I need to know the name of the file to specify the name of the file to know the name of the file??? 

Obviously I am missing the point, but where?

TIA.

dcerdil, you may have fixed this already or given up, but for the benefit of the archive I think I know the solution to your problem.

I too was trying to use the filewriter instead of the swapwriter. It turns out that version 2.2.9 of the suspend2 patch changed /sys/power/suspend2/filewriter/ folder to /sys/power/suspend2/file/. However the hibernate script is still looking in the old location. You need to edit /usr/share/hibernate/scriptlets.d/suspend2 and change the line:

[ -d "$SWSUSP_ROOT/filewriter/" ] && FILEWRITER_ROOT="$SWSUSP_ROOT/filewriter"

to

[ -d "$SWSUSP_ROOT/file/" ] && FILEWRITER_ROOT="$SWSUSP_ROOT/file"

---

### Post by harty83 on 2007-03-24
> **Treviño said:**
> If you want you can test the 2.6.20.x packages I've built some time ago for testing: [http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/](http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/)

I'm using those and are working great ;)

Hey Trevino, would I add that to my repositories for feisty and upgrade?  Would they work in Feisty without the acpi and hibernate updates you had in edgy?

Thanks!
Alan

---

### Post by Treviño on 2007-03-25
It isn't a repo (yet), simply install the packages manually...

---

### Post by WolfEng on 2007-03-26
Hi guys, sorry about the late response, i had some malfunctions with my hdd and had to replace it, thanks for the advices. And i'm about to check the options.

> **reacocard said:**
> Try doing
```
sudo /etc/init.d/acpid restart
```
after this happens. If that solves it, you'll just have to add that to your hibernate script configuration.

I'm about to try this option, and i hope this work cuz this one seem to be the simplest!!
I'll post the results XD

> **mintcoffee said:**
> What CPU do you have? I have an Intel T7200 and I had the same issue. I ended up compiling the 2.6.20 kernel, and most of my problems have gone away.

The ACPI daemon seemed to be functioning fine for me.

I'm running on a DELL inspiron 6400, duocore (single cpu 2 cores). This one seems to be rather complicated for a noob XD, but if the first doesn't work nor the one from treviño, I guess i'll have to learn to compile a kernel, do you have any link to a tutorial???. Anyway thanks!! 

> **Treviño said:**
> If you want you can test the 2.6.20.x packages I've built some time ago for testing: [http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/](http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/)

I'm using those and are working great ;)

So, how do I install these???? JAJAJA, sorry i'm still going through the noob learning process. Could you give me some hits?? THNX!!

-------------------------------------------------------------------------------------------------------------------------------

Well, i guess that's it, now i'm gonna try out the options. I'll post any results, C y'all

---

### Post by harty83 on 2007-03-26
> **Treviño said:**
> It isn't a repo (yet), simply install the packages manually...

Thanks!  I did and it seems to work.  I was wondering, I see that you have the suspend2 useruri's under the feisty folder but they require suspend2 which is not listed.  If I try to install suspend2 from the edgy folder, it  fails because of a dependency on an older version of acpi than one included in feisty.  Are you going to upload a feisty suspend2 package?

Thanks!
Alan

---

### Post by WolfEng on 2007-03-27
Hi again!, acpid restart didn't work =( the scaling kept at 100%, thanks anyway!
And by the way treviño, i ment hints not hits XD.

---

### Post by Treviño on 2007-03-28
> **harty83 said:**
> Thanks!  I did and it seems to work.  I was wondering, I see that you have the suspend2 useruri's under the feisty folder but they require suspend2 which is not listed.  If I try to install suspend2 from the edgy folder, it  fails because of a dependency on an older version of acpi than one included in feisty.  Are you going to upload a feisty suspend2 package?

Thanks!
Alan
Actually I'm not running feisty in any way so I'll make a feisty repo when it will be stable...

---

### Post by mintcoffee on 2007-03-28
> **WolfEng said:**
> Hi again!, acpid restart didn't work =( the scaling kept at 100%, thanks anyway!
And by the way treviño, i ment hints not hits XD.

Try the 2.6.20 kernel at Treviño's repository: [http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/](http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/)

I believe you should download the following files:

```

linux-image-2.6.20-6-generic_2.6.20-6.11+suspend2.2.2.9.3+3v1ubuntu0_i386.deb
linux-restricted-modules-2.6.20-6-generic_2.6.20.1-6.4_i386.deb 
linux-headers-2.6.20-6-generic_2.6.20-6.11+suspend2.2.2.9.3+3v1ubuntu0_i386.deb 

```

To install type the following commands:
```

sudo dpkg -i linux-image-2.6.20-6-generic_2.6.20-6.11+suspend2.2.2.9.3+3v1ubuntu0_i386.deb
sudo dpkg -i linux-restricted-modules-2.6.20-6-generic_2.6.20.1-6.4_i386.deb 
sudo dpkg -i linux-headers-2.6.20-6-generic_2.6.20-6.11+suspend2.2.2.9.3+3v1ubuntu0_i386.deb 

```

I hope that should fix the problem!

Steven

---

### Post by Treviño on 2007-03-29
It's also needed upgrading the suspend2-userui* packages

---

### Post by defishguy on 2007-04-10
Thank you Trevino for your hard work.  I've had a EUREKA moment with my laptop and the suspend2 patched kernels.  

I have an Acer Aspire 5100 with an ATI 200M graphics system running Edgy.  I use the fglrx drivers, Beryl, and XGL and after trial and error over weeks, I finally have reliable suspend service, in fact it's been extremely reliable despite the fact that I use the XGL session almost exclusively.

Your mileage may vary, but in the hopes that it will help others I'm posting my acpi-support file because it is the only file that I've edited.


Good luck!

---

### Post by Treviño on 2007-04-13
> **defishguy said:**
> Thank you Trevino for your hard work.  I've had a EUREKA moment with my laptop and the suspend2 patched kernels.  

I have an Acer Aspire 5100 with an ATI 200M graphics system running Edgy.  I use the fglrx drivers, Beryl, and XGL and after trial and error over weeks, I finally have reliable suspend service, in fact it's been extremely reliable despite the fact that I use the XGL session almost exclusively.

Your mileage may vary, but in the hopes that it will help others I'm posting my acpi-support file because it is the only file that I've edited.


Good luck!

Cool, I post  a diff of what you've changed for making it applying with an easy way to all:
```
--- /etc/default/acpi-support   2006-11-04 04:07:11.000000000 +0100
+++ /tmp/acpi-support.txt       2007-04-13 11:58:50.000000000 +0200
@@ -45,10 +45,10 @@
 POST_VIDEO=true

 # Save and restore video state?
-# SAVE_VIDEO_PCI_STATE=true
+#  SAVE_VIDEO_PCI_STATE=true

 # Should we switch the screen off with DPMS on suspend?
-USE_DPMS=true
+USE_DPMS=false

 # Use Radeontool to switch the screen off? Seems to be needed on some machines
 # RADEON_LIGHT=true
@@ -74,7 +74,7 @@

 # Add services to this list to stop them before suspend and restart them in
 # the resume process.
-STOP_SERVICES="mysql "
+STOP_SERVICES="mysql beryl-xgl xgl bluetooth"

 # Restart Infra Red services on resume - off by default as it crashes some
 # machines
@@ -82,4 +82,4 @@

 # Switch to laptop-mode on battery power - off by default as it causes odd
 # hangs on some machines
-ENABLE_LAPTOP_MODE=true
+ENABLE_LAPTOP_MODE=false
```

---

### Post by detyabozhye on 2007-04-20
Ooh, can we have Feisty repos now? :D

---

### Post by reacocard on 2007-04-20
> **detyabozhye said:**
> Ooh, can we have Feisty repos now? :D

I sure hope Trevino does that. If he doesn't I'll give it a shot myself. I may anyway, just to learn how. :D

---

### Post by therobbot on 2007-04-20
Yeah, it's stable now, isn't it? (Actually it has been for quite a while, just wasn't called so)

Tobias

---

### Post by Treviño on 2007-04-22
Yeah...!
I'm just compiling new feisty kernels... Wait few hours (days) and they'll be online ;)

---

### Post by detyabozhye on 2007-04-23
yay! ^_^

---

### Post by reacocard on 2007-04-23
> **Treviño said:**
> Yeah...!
I'm just compiling new feisty kernels... Wait few hours (days) and they'll be online ;)

Awesome! I'd still love to have that guide sometime (you know, the one you promised [last October]("http://ubuntuforums.org/showpost.php?p=1691096&postcount=19") ;-)  ). I've been trying to compile my own but for some reason I can't get my wifi (ipw2200) to work afterwards. I think the firmware isn't installing right. :(

---

### Post by Treviño on 2007-04-23
> **reacocard said:**
> Awesome! I'd still love to have that guide sometime (you know, the one you promised [last October]("http://ubuntuforums.org/showpost.php?p=1691096&postcount=19") ;-)  ). I've been trying to compile my own but for some reason I can't get my wifi (ipw2200) to work afterwards. I think the firmware isn't installing right. :(
You're absolutely right but you know... I try to do many things and I generally prefer to produce useful things than document them (in fact I do also many things that I can't share at all sometimes, due to lack of time...); this is a my fault... Another motivation is that I whould have liked to publish something of more general (I mean, not only for suspend2) but this make things harder (to keep the procedure simple) and so I stopped to write my stub...

However I think that when I'll announce officially the feisty repo I'll attach also a guide...

BTW **packages for feisty** are *uploading* now...: Unfortunately I've a low bandwidth in those days so I hope they'll be online ASAP. 
The repo info are at:
 - [http://3v1n0.tuxfamily.org/dists/feisty/suspend2/](http://3v1n0.tuxfamily.org/dists/feisty/suspend2/)
Packages:
 - [http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/](http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/)

Now I'll leave it to my uploading script and I go to bed, so I hope that all will be online when I'll be asleep again ;)

Let me know how they work, in my system they're really good and also suspend2ui_usplash works again with new feisty usplash themes!!!

Bye

---

### Post by reacocard on 2007-04-23
> **Treviño said:**
> You're absolutely right but you know... I try to do many things and I generally prefer to produce useful things than document them (in fact I do also many things that I can't share at all sometimes, due to lack of time...); this is a my fault... Another motivation is that I whould have liked to publish something of more general (I mean, not only for suspend2) but this make things harder (to keep the procedure simple) and so I stopped to write my stub...

However I think that when I'll announce officially the feisty repo I'll attach also a guide... 

Yeah, I often have that problem. Sometimes it just seems harder to write a guide than to actually *do* it.

> BTW **packages for feisty** are *uploading* now...: Unfortunately I've a low bandwidth in those days so I hope they'll be online ASAP. 
The repo info are at:
 - [http://3v1n0.tuxfamily.org/dists/feisty/suspend2/](http://3v1n0.tuxfamily.org/dists/feisty/suspend2/)
Packages:
 - [http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/](http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/)

Now I'll leave it to my uploading script and I go to bed, so I hope that all will be online when I'll be asleep again ;)

Let me know how they work, in my system they're really good and also suspend2ui_usplash works again with new feisty usplash themes!!!

Sweet! Can't wait. Still not up here, so I guess it'll have to wait til morning. Thanks again for all your hard work!

EDIT: They're up! Downloading now. Can't wait. :D

EDITv2: Installed perfectly, works great! Kudos to you on yet another awesome job!

---

### Post by Ago12 on 2007-04-24
Thanks!

... Downloading ...

---

### Post by detyabozhye on 2007-04-24
Thankies. ^_^

Edit: No restricted modules yet I guess, no nVidia for me. Other than that they work perfectly.

---

### Post by Treviño on 2007-04-24
> **detyabozhye said:**
> Thankies. ^_^

Edit: No restricted modules yet I guess, no nVidia for me. Other than that they work perfectly.
As it was for edgy, it's not needed to rebuild the restricted modules since my kernels are installed on the same dir where there's the official one, so linux-restricted-modules from ubuntu will work with this repo, as always! :)

Ah, I forgot to mention that this time I didn't upload the source packages for kernel (I mean .dsc + .orig.tar.gz + .diff.gz) since as always there's the package *linux-source-2.6.20* (it's not exactly the same, but  they're however the sources, so there are no license problems), that you use to recompile a custom kernel...
About, *suspen2-patch*, this time patching-time has been less (you'd say "more" in real world :D) funny for me since i didn't have to regenerate a patchfile for feisty kernel, but I simply used this official patch: [suspend2-2.2.9.12-for-ubuntu-feisty.patch.bz2]("http://www.suspend2.net/downloads/all/suspend2-2.2.9.12-for-ubuntu-feisty.patch.bz2")

PS: is there anyone that can test the filewriter suspension? Just to see if my patches (they're on .diff file) to hibenate work...

---

### Post by Ago12 on 2007-04-24
It looks like it works.

BUT, I need to find the line I had found about xorg.con to avoid a blank screen at resume with an Intel card...

---

### Post by Ago12 on 2007-04-24
Got it!
[http://www.thinkwiki.org/wiki/Problem_with_display_remaining_black_after_resume#Solution_for_ThinkPads_with_Intel_Extreme_Graphics_2](http://www.thinkwiki.org/wiki/Problem_with_display_remaining_black_after_resume#Solution_for_ThinkPads_with_Intel_Extreme_Graphics_2)

---

### Post by detyabozhye on 2007-04-24
> **Treviño said:**
> As it was for edgy, it's not needed to rebuild the restricted modules since my kernels are installed on the same dir where there's the official one, so linux-restricted-modules from ubuntu will work with this repo, as always! :)

Hmm, the nVidia drivers don't want to work for some reason though when I'm running this kernel.

---

### Post by mariner09 on 2007-04-24
I installed your kernel updates and now the madwifi drivers don't load, they give me symbol errors.

This happened after a fresh feisty install this evening and then directly upgrading to your kernel. 

I'll make sure my restricted package matches your kernel, but there might be an issue here....

---

### Post by mariner09 on 2007-04-24
After further investigation, it looks like the current ubuntu kernel has a subversion of .14 while your kernel has a .27 subversion.  This could certainly explain the symbol errors and some of the other issues being seen with restricted drivers.

---

### Post by detyabozhye on 2007-04-25
No, the stock Feisty generic kernel is .27

---

### Post by mariner09 on 2007-04-25
Then there's really something wrong here....

I was able to get ath_pci to load by compiling madwifi, but if the kernels are the same and Trevino's packages are just overlays to the existing code, then these errors should not be happening.

---

### Post by schmolch on 2007-04-25
If you run a Kernel with suspend2, will gnome use it automatically then?

---

### Post by reacocard on 2007-04-25
> **schmolch said:**
> If you run a Kernel with suspend2, will gnome use it automatically then?

Yep. The patched acpi-support package handles that.

---

### Post by Treviño on 2007-04-26
> **mariner09 said:**
> After further investigation, it looks like the current ubuntu kernel has a subversion of .14 while your kernel has a .27 subversion.  This could certainly explain the symbol errors and some of the other issues being seen with restricted drivers.
Well, as said the version is the same of the official kernel, however I've no restricted hardware to test, so I can't check these restricted modules...

However, if this issue is confirmed I could upload also patched restricted modules to my repo; simply test again and report! ;)

---

### Post by mariner09 on 2007-04-26
I'd be happy to help as soon as you get the deb added to your repo....

---

### Post by knn on 2007-04-27
> **Treviño said:**
> Well, as said the version is the same of the official kernel, however I've no restricted hardware to test, so I can't check these restricted modules...

However, if this issue is confirmed I could upload also patched restricted modules to my repo; simply test again and report! ;)

After installing your packages (feisty 2.6.20.15), modprobe nvidia results in this error message: FATAL: Error running install command for nvidia
dmesg outputs this:
```

[ 1038.246655] nvidia: disagrees about version of symbol pci_enable_device
[ 1038.246667] nvidia: Unknown symbol pci_enable_device
[ 1038.246804] nvidia: disagrees about version of symbol agp_bind_memory
[ 1038.246808] nvidia: Unknown symbol agp_bind_memory
[ 1038.246826] nvidia: disagrees about version of symbol pci_choose_state
[ 1038.246829] nvidia: Unknown symbol pci_choose_state
[ 1038.246857] nvidia: disagrees about version of symbol pci_dev_put
[ 1038.246860] nvidia: Unknown symbol pci_dev_put
[ 1038.246877] nvidia: disagrees about version of symbol pci_get_device
[ 1038.246880] nvidia: Unknown symbol pci_get_device
[ 1038.246915] nvidia: disagrees about version of symbol agp_enable
[ 1038.246917] nvidia: Unknown symbol agp_enable
[ 1038.246935] nvidia: disagrees about version of symbol __pci_register_driver
[ 1038.246938] nvidia: Unknown symbol __pci_register_driver
[ 1038.246995] nvidia: disagrees about version of symbol pci_bus_write_config_byte
[ 1038.246998] nvidia: Unknown symbol pci_bus_write_config_byte
[ 1038.247049] nvidia: disagrees about version of symbol pci_unregister_driver
[ 1038.247052] nvidia: Unknown symbol pci_unregister_driver
[ 1038.247085] nvidia: disagrees about version of symbol agp_backend_acquire
[ 1038.247088] nvidia: Unknown symbol agp_backend_acquire
[ 1038.247173] nvidia: disagrees about version of symbol pci_bus_read_config_dword
[ 1038.247176] nvidia: Unknown symbol pci_bus_read_config_dword
[ 1038.247192] nvidia: disagrees about version of symbol pci_bus_read_config_word
[ 1038.247195] nvidia: Unknown symbol pci_bus_read_config_word
[ 1038.247238] nvidia: disagrees about version of symbol i2c_del_adapter
[ 1038.247241] nvidia: Unknown symbol i2c_del_adapter
[ 1038.247291] nvidia: disagrees about version of symbol agp_free_memory
[ 1038.247294] nvidia: Unknown symbol agp_free_memory
[ 1038.247321] nvidia: disagrees about version of symbol pci_bus_write_config_dword
[ 1038.247325] nvidia: Unknown symbol pci_bus_write_config_dword
[ 1038.247401] nvidia: disagrees about version of symbol agp_allocate_memory
[ 1038.247404] nvidia: Unknown symbol agp_allocate_memory
[ 1038.247422] nvidia: disagrees about version of symbol pci_set_master
[ 1038.247425] nvidia: Unknown symbol pci_set_master
[ 1038.247460] nvidia: disagrees about version of symbol agp_unbind_memory
[ 1038.247463] nvidia: Unknown symbol agp_unbind_memory
[ 1038.247509] nvidia: disagrees about version of symbol i2c_add_adapter
[ 1038.247512] nvidia: Unknown symbol i2c_add_adapter
[ 1038.247560] nvidia: disagrees about version of symbol pci_bus_write_config_word
[ 1038.247563] nvidia: Unknown symbol pci_bus_write_config_word
[ 1038.247602] nvidia: disagrees about version of symbol pci_get_class
[ 1038.247604] nvidia: Unknown symbol pci_get_class
[ 1038.247645] nvidia: disagrees about version of symbol agp_copy_info
[ 1038.247648] nvidia: Unknown symbol agp_copy_info
[ 1038.247719] nvidia: disagrees about version of symbol agp_backend_release
[ 1038.247722] nvidia: Unknown symbol agp_backend_release
[ 1038.247743] nvidia: disagrees about version of symbol pci_bus_read_config_byte
[ 1038.247746] nvidia: Unknown symbol pci_bus_read_config_byte

```

Seems to be a version conflict. Any ideas?

Edit: forcing the nvidia module to load (modprobe --ignore-install --force nvidia) works, and 3d works too.

Edit2: Neither suspend to ram nor hibernate works :( , so I guess I'll reinstall the standard kernel

---

### Post by shizeon on 2007-04-27
Hi Trevino,
  Do you have any plans/desire to do a 2.6.21 kernel release?  I haven't seen anything on the official ubuntu sites for support yet, but am really anxious to check out how the new dynticks updates effect my battery life.   This is probably a bit premature since you just released the new feisty suspend2 kernel and 2.6.21 is only a few days old, but I had to ask :)  

Thanks again for your work!
- Sean

---

### Post by damiencc on 2007-04-28
I confirm the subversion mismatch:

for instance, in the process of loading ath_pci

[ 1005.904000] wlan_tkip: disagrees about version of symbol skb_under_panic

then it is enough to modprobe -f the many modules that ath_pci needs, and wifi works. Nevertheless, it would be good to correct this slight mistake.

Hibernate works perfectly, thanks.

Just an additional suggestion: could you compile the kernel with USB SUSPEND off, so that scanners work again ? This option is used in the standard 7.04 kernel because it makes it possible for more people to hibernate, but who cares with suspend2?

---

### Post by fettuohi on 2007-04-28
> **damiencc said:**
> I confirm the subversion mismatch:

for instance, in the process of loading ath_pci

[ 1005.904000] wlan_tkip: disagrees about version of symbol skb_under_panic

then it is enough to modprobe -f the many modules that ath_pci needs, and wifi works. Nevertheless, it would be good to correct this slight mistake.

Hibernate works perfectly, thanks.

Just an additional suggestion: could you compile the kernel with USB SUSPEND off, so that scanners work again ? This option is used in the standard 7.04 kernel because it makes it possible for more people to hibernate, but who cares with suspend2?

Same problem here also for me after upgrade, wlan0, ath0 and virtualbox modules can't be loaded anymore.

Regards

André

---

### Post by harty83 on 2007-04-28
Occasionally after hibernating, my system resumes with a read-only filesystem.  Of course nothing works until I do a reboot.  Any ideas on this one?

---

### Post by fettuohi on 2007-04-28
> **Treviño said:**
> Well, as said the version is the same of the official kernel, however I've no restricted hardware to test, so I can't check these restricted modules...

However, if this issue is confirmed I could upload also patched restricted modules to my repo; simply test again and report! ;)

It's just not only the restricted modules that give this error, but also modules from other packages like virtual box.

Regards

André

---

### Post by reacocard on 2007-04-28
> **fettuohi said:**
> It's just not only the restricted modules that give this error, but also modules from other packages like virtual box.

Regards

André

The virtualbox modules just need to be recompiled against the new kernel. The same thing will happen with any kernel module.  In the case of virtualbox, you'll probably just have to reinstall virtualbox. I installed virtualbox after I installed these kernels and it works fine.

---

### Post by fettuohi on 2007-04-29
> **reacocard said:**
> The virtualbox modules just need to be recompiled against the new kernel. The same thing will happen with any kernel module.  In the case of virtualbox, you'll probably just have to reinstall virtualbox. I installed virtualbox after I installed these kernels and it works fine.

I did that and I still get the error with the version mismatch.

Regards

André

---

### Post by Treviño on 2007-04-30
Hi all, in these past days I've been really few hours at home and less at PC so I haven't checked better what's was wrong, however I've gave a look to the patch I've applied to check how they could have made this mismatch, while it hasn't ever happened before...

Before of posting restricted debs to my repo (that are really many MBs) I'd like to test if I could fix in another way this issue, that I don't think it's completely related to me...
I mean, I've used the same sources used for compiling the official ubuntu kernel, and the suspend2 patch doesn't change any version code...

So, I'll try to post again this kernel compiled against new suspend2 patch (2.2.9.13) and then I'll take a decision....

Bye!

---

### Post by harty83 on 2007-05-03
I am having two problems:

One:  when I resume from hibernation, my cpus are clocked at max (1.73) and will not change with a reboot.  This is bad because it sucks my battery life of my laptop.  What do you think is happening and how can I fix it?

Two: often my ipw3945 module is not loading on resume.  I have to manually modprobe it.  It is listed as remain in   I have LoadModulesFromFile /etc/modules in my common.conf and added ipw3945 to my modules file.  I also have MODULES_WHITELIST="ipw3945" in my /etc/default/acpi-default.  Any clue?

Thanks!
Alan

---

### Post by pixelmonkey on 2007-05-03
I've managed to compile a 2.6.20 kernel from the Ubuntu kernel-dev git repository with the suspend2.2.9.13 patch applied.  I've also managed to compile the linux-restricted-modules package and build it, but I had to disable the ATI FGLRX driver since it was giving me build errors.  (Fine on my machine -- don't use fglrx anyway, I use Nvidia and ipw3945 mainly).

Everything seems to be working merrily on my machine.  I of course had to install the hibernate script, suspend2_userui, and patch the initramfs manually with a script that invokes suspend2's do_suspend, but otherwise everything works as expected.

I am not, however, particularly adept with these Ubuntu packaging tools.  I could certainly post up the debs that worked for me, but I'd rather coordinate with Trevino to make a more "solid" release.

If there is popular demand for them, however, I will post these debs up.  Some outstanding issues:

   * I use the default ABI version which the kernel scripts create, which is 15-ref.  This may not be preferable, but does allow you to have both kernels (stock Ubuntu and my custom one) side by side.
   * I only compiled for the "generic" (i386) architecture, to save time.
   * I left out fglrx, vmware stuff, and ltmodem from my restricted-modules compile, to save time.
   * I haven't created packages for the userui, acpi-support, or hibernate pieces, like Trevino has.

Andrew

---

### Post by hughes28105 on 2007-05-21
help. how do you get suspend2 to hibernate or suspend with beryl running. using beryl 0.3.0 on a hp dv6110us. all i get is a blank screen with mouse and a white solid boxs behined the mouse.

---

### Post by Treviño on 2007-05-21
That's a common bug that has been solved by some graphics drivers (mesa did), however you can simply reload it to fix...

BTW, I've patched the ubuntu kernel with suspend2 2.2.10 and rebuilt also the restricted modules... They will be on my repo as soon as I can...

BYE!

---

### Post by hughes28105 on 2007-05-22
how do you get suspend to ram working with suspend2. everytime i suspend to ram my screen just freezes including the mouse and i have to reboot.

---

### Post by Treviño on 2007-05-22
It was working before; now it doesn't :o

However I've put on the repo both the linux image and the linux restricted modules patched with suspend2 2.2.10, let me know how they work

---

### Post by reacocard on 2007-05-22
> **Treviño said:**
> It was working before; now it doesn't :o

However I've put on the repo both the linux image and the linux restricted modules patched with suspend2 2.2.10, let me know how they work

Gives me this after upgrading:

```
dpkg: dependency problems prevent configuration of suspend2:
 suspend2 depends on suspend2-userui-usplash (>= 0.7.1); however:
  Version of suspend2-userui-usplash on system is 0.7.1-0~3v1ubuntu0.
dpkg: error processing suspend2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of suspend2-userui-usplash:
 suspend2-userui-usplash depends on suspend2; however:
  Package suspend2 is not configured yet.
dpkg: error processing suspend2-userui-usplash (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of suspend2-userui-text:
 suspend2-userui-text depends on suspend2; however:
  Package suspend2 is not configured yet.
dpkg: error processing suspend2-userui-text (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 suspend2
 suspend2-userui-usplash
 suspend2-userui-text
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Other than that it seems to have installed fine, I haven't had a chance to test it yet, but I will soon.

---

### Post by Treviño on 2007-05-22
Sorry for  this, I noticed it now... I forgot to put the right userui version, however I'm uploading new svn verison now, all will be fixed (and however this was only a warning, since suspend2 is a metapackage).

---

### Post by reacocard on 2007-05-22
> **Treviño said:**
> Sorry for  this, I noticed it now... I forgot to put the right userui version, however I'm uploading new svn verison now, all will be fixed (and however this was only a warning, since suspend2 is a metapackage).

Thanks. It works as it is, but eliminating errors is always good. :)

---

### Post by Treviño on 2007-05-23
Sure... 

Anyone tested the restricted modules? The ones I could worked...

---

### Post by Ago12 on 2007-05-23
ipw3945 module works here, as it did before your special package :)

---

### Post by detyabozhye on 2007-05-23
downloading, will try soon...

---

### Post by mariner09 on 2007-05-23
madwifi works well, so far...

vmware  drivers as well.

---

### Post by hughes28105 on 2007-05-24
Work grate know thanks. suspend and hibernate works with the new kernel and suspend2 2.2.9.10

---

### Post by detyabozhye on 2007-05-25
suspend-to-ram seems to not work, hibernate worked only once after a clean start, then my main partition got corrupted on restart (I think my hard drive is just dying, I don't think it's the patched kernel's fault). nVidia drivers work fine.

---

### Post by Treviño on 2007-05-25
New kernel version out, Wait few days for uploads, However I hope they'll work without recompiling modules this time :|

---

### Post by detyabozhye on 2007-05-25
Actually it was suspend2 that messed up my partition, because it did it again after trying hibernate, tho not as bad as the first time.

---

### Post by fettuohi on 2007-05-27
I tried your suspend2 kernel again this time on a different machine and the virtualbox module still won't run with the kernel.

[   79.802756] vboxdrv: disagrees about version of symbol misc_deregister
[   79.802765] vboxdrv: Unknown symbol misc_deregister
[   79.802828] vboxdrv: disagrees about version of symbol __free_pages
[   79.802830] vboxdrv: Unknown symbol __free_pages
[   79.802845] vboxdrv: disagrees about version of symbol contig_page_data
[   79.802847] vboxdrv: Unknown symbol contig_page_data
[   79.802883] vboxdrv: disagrees about version of symbol misc_register
[   79.802885] vboxdrv: Unknown symbol misc_register
[   79.802891] vboxdrv: disagrees about version of symbol __alloc_pages
[   79.802893] vboxdrv: Unknown symbol __alloc_pages
[   79.802916] vboxdrv: disagrees about version of symbol page_address
[   79.802918] vboxdrv: Unknown symbol page_address

though madwifi isn't giving me any problems, but on this machine I don't have any wireless network cards installed anyhow (stationary pc).

Regards

André

---

### Post by Treviño on 2007-05-27
Mhmhm.. Is that module included in restricted-modules package?

---

### Post by fettuohi on 2007-05-28
Nope, the module gets build when you install the virtualbox package.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

Either through Automatix2 or from downloading it from the webpage (they have a package for Ubuntu Feisty Fawn).

Regards

André

---

### Post by Treviño on 2007-05-29
> **fettuohi said:**
> Nope, the module gets build when you install the virtualbox package.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

Either through Automatix2 or from downloading it from the webpage (they have a package for Ubuntu Feisty Fawn).

Regards

AndréWell, so I think you should rebuild it...

However, I've built few days ago the new ubuntu kernel but the version mismatch was always there... So yesterday I contacted the suspend2 team and thanks to Nigel Cunningham  (suspend2 main author) I've (maybe) found where the problem is!

Actually I'm rebuilding I hope that recompiling the restricted modules won't be needed anymore... ;)

---

### Post by fettuohi on 2007-05-29
Sounds good :).

Regards

André

---

### Post by Firetech on 2007-05-29
I also experienced some (seemingly) minor corruption of the FS, but that was caused by accidentally booting into an unpatched kernel (without suspend2) after suspending to disk and then back into the suspended kernel. The ext3 journal apparently didn't like that. :/
The visible corruption (my KDE and Beryl settings) have been fixed, but noone knows if anything has happened to the /etc files. I couldn't see anything about them during the fsck run, but then again, neither my KDE nor Beryl settings showed up there...

---

### Post by Treviño on 2007-05-30
I can confirm now that the fixed suspend2 patch works well with standard restricted modules too now! :)

Simply I removed from the patch I made for feisty (and available at suspend2.net) the lines related to the files include/linux/device.h. and drivers/base/core.c...

I'm uploading now, but then I've to go so I hope to have an updated repository in about 15hrs ;)


Bye!

---

### Post by fettuohi on 2007-05-30
Sweet, thanks 3v1n0 :D.

Regards

André

---

### Post by Firetech on 2007-05-30
The fs problem I got should have been solved by the /etc/init.d/hibernate script (linked to by /etc/rcS.d/S31hibernate), but it seems like that never got run. Can it be an upstart issue? Or does anyone have another solution?

---

### Post by Treviño on 2007-05-30
Firetech, the strange thing is that the script is loaded in a normal session... :o

However, I've **updated the repository**, let me know how it works for you (restricted modules too) ;)

---

### Post by mintcoffee on 2007-05-31
Great!! Thanks for your work Treviño! :)

---

### Post by Firetech on 2007-05-31
> **Treviño said:**
> Firetech, the strange thing is that the script is loaded in a normal session... :o

However, I've **updated the repository**, let me know how it works for you (restricted modules too) ;)
Well, my problem was partially due to  stupidity. When I've booted into the right kernel, suspend2 has always worked great on my laptop. Thanks for the new kernels! :) Only issue with them was that the device of my harddrive changed back from sda to hda (like it was before I upgraded to feisty), so suspend2 didn't find my swap partition...

The problem with /etc/init.d/hibernate might be that it's not running at the right time. The header inside the file tells quite clearly when it should be run. perhaps the suggestion of  start number 31 doesn't apply to *buntu?

**EDIT**: I spoke too soon, I actually can't resume from hibernation with this new kernel. I'm getting this when I boot:
[   15.960000] BIG FAT WARNING!! Failed to get access to block device "fe00003" (error -6).
[   15.960000]  Maybe you need to run mknod and/or lvmsetup in an initrd/ramfs?
[   15.960000]
[   15.960000] If you want to use the current suspend image, reboot and try
[   15.960000] again with the same kernel that you suspended from. If you want
[   15.960000] to forget that image, continue and the image will be erased.
[   15.960000] Press SPACE to reboot or C to continue booting with this kernel
[   15.960000]
[   15.960000] Default action if you don't select one in 25 seconds is: continue booting.
[   40.964000] Suspend2: Image invalidated.

Seems like something is wrong with initramfs?

**EDIT 2:**
Hmm... Got it to work once (but once only) by editing  /etc/initramfs-tools/conf.d/resume to contain the of my swap partition and then running update-initramfs. (Full contents of the file are now: "RESUME=UUID=...")
When I tried it again, however, I got the same thing as above...

**EDIT 3:**
Seems like I finally got it to work, _without_ the initramfs fix mentioned above. The cause seems to have been that I changed my /etc/fstab  to use the UUID instead of /dev/hda5. Suspend2 doesn't seem to understand UUID:s, so it got confused. Now it's back to working again. (The reason I edited fstab was because I didn't want to have more problems with the /dev address changing...) The effective change I've made is that every reference to /dev/sda5 has been changed to /dev/hda5.
Some fun stuff: For a while it actually mounted the swap partition twice (once as /dev/hda5 and once by UUID), because of the confusion. I wonder how that would have worked if the computer thought it could use all of it. :P

---

### Post by reacocard on 2007-06-01
> **Treviño said:**
> Firetech, the strange thing is that the script is loaded in a normal session... :o

However, I've **updated the repository**, let me know how it works for you (restricted modules too) ;)

The updated kernels don't work for me. /sys/power/suspend2/do_suspend is unwritable, gives a 'busy' error on 'echo 1 > do_suspend'. Any ideas?

---

### Post by Treviño on 2007-06-01
Mhmhm... Are you always using the -386 package?
I've tested only the generic and it works well....

---

### Post by reacocard on 2007-06-01
> **Treviño said:**
> Mhmhm... Are you always using the -386 package?
I've tested only the generic and it works well....

nope, I'm using generic too. I've rebooted several times too, no difference.  I'll try the -386, see if that works.

EDIT: nope, 386 won't even boot, gives an error about not being able to load the ext3 module.

---

### Post by Treviño on 2007-06-05
Mh :(
No ideas... When I can find time I'll try to rebuild all from scratch

---

### Post by Firetech on 2007-06-12
Any word on updated kernels? A new security update was released on June 8 ([info here]("https://lists.ubuntu.com/archives/ubuntu-security-announce/2007-June/000542.html")).

Those of you who, like me, doesn't really care about those issues, can add these lines to /etc/apt/preferences (might not exist until you create it):
```

Package: *
Pin: release c=suspend2
Pin-Priority: 991

```
That way, no official kernel package will overwrite Treviño's :KS
(Although, a computer often connected to the internet with no firewall or to some kind of untrusted LAN, like at work or in school, should NOT do the above, as the updated official kernels are a bit more important in those cases...)

---

### Post by detyabozhye on 2007-06-13
Ah, I'm just running the stock kernel for now and leaving my box running 24/7 instead of hibernating. I hope they can get a good hibernate thing in the vanilla kernel soon; either fix the current one or use Suspend2.

---

### Post by Treviño on 2007-06-21
Sorry for delay but I was working on Compiz Fusion packaging ;), however newer debs are coming, unfortunately I didn't put suspend2 2.2.10.1 since this version doesn't resume the USB devices (mouse at first) I have...

---

### Post by duncansargeant on 2007-06-23
Is anyone else having a problem with the latest patch level?

I have linux-image-2.6.20-16-generic version 2.6.20-16.28+suspend2~2.2.10+3v1ubuntu1 but the suspend attempt fails and puts me back in X.

I am continuing to use linux-image-2.6.20-15-generic              2.6.20-15.27+suspend2~2.2.9.12+3v1ubuntu0 but it appears now that after suspend/resume, my ipw2200 wifi connection is intermittently unstable and drops all my packets.  As a workaround I can do a 'iwconfig eth1 rate 2M ; iwconfig eth1 rate 11M' to bring it back most times, but not all.

---

### Post by Treviño on 2007-06-23
I've updated the suspend2 packages (finally, after two days of uploading a really slow speeds - due to tuxfamily I think)... Some are missing (sources) until I'll have a better connection...

See you!

---

### Post by mcarro on 2007-06-24
> **Treviño said:**
> I've updated the suspend2 packages (finally, after two days of uploading a really slow speeds - due to tuxfamily I think)... Some are missing (sources) until I'll have a better connection...

Just upgraded to the latest suspend2 + linux-image-2.6.20-16-generic_2.6.20-16.29+suspend2~2.2.10+3v1ubuntu0_i386.deb 
and the boot process fails.  It stops claiming that the resume file was not found - even if I am rebooting from scratch (not booting after hibernating).  I tried the /dev/hdaX and /dev/sdaX naming for the resume2 parameter with the same result (BTW, what would be resume2 syntax to use UUID-based disk naming?).  Removing the resume2 parameter does not help either.  I hope I did not do anything wrong (I just let aptitude do the upgrade).  Did anybody else have the same problem?

---

### Post by reacocard on 2007-06-24
> **Treviño said:**
> I've updated the suspend2 packages (finally, after two days of uploading a really slow speeds - due to tuxfamily I think)... Some are missing (sources) until I'll have a better connection...

See you!

Tried them, same issues I had with the first edition of the -16 kernels: suspend2 doesn't work, because the needed files in /sys/power/suspend2 are unwritable.  I'm using the -15 kernels for now, so it's not urgent, but it'd be nice to have this issue resolved.

---

### Post by mcarro on 2007-06-24
> **reacocard said:**
> Tried them, same issues I had with the first edition of the -16 kernels: suspend2 doesn't work, because the needed files in /sys/power/suspend2 are unwritable.  I'm using the -15 kernels for now, so it's not urgent, but it'd be nice to have this issue resolved.


I´ve been using the generic_2.6.20-16.28+suspend2 since it came out without any issues.  Didn't have to touch anything.

---

### Post by blingboi on 2007-08-03
sorry, just started using feisty fawn a couple days ago, have had suspend problems and have finally found this thread

i think it might solve my problem, however... how do i approach installing the meta package for suspend to from your repo?

heres what i did, i have figlx installed already
heres what i did

i put your 2 links in my sources.list , did sudo apt-get update

then:

$ wget [http://3v1n0.tuxfamily.org/pool/feisty/suspend2/suspend2_2.2.10-1~3v1ubuntu2_all.deb](http://3v1n0.tuxfamily.org/pool/feisty/suspend2/suspend2_2.2.10-1~3v1ubuntu2_all.deb)

then:

$ sudo dpkg -i suspend2_2.2.10-1~3v1ubuntu2_all.deb


..it gave me all of this

Selecting previously deselected package suspend2.
(Reading database ... 105948 files and directories currently installed.)
Unpacking suspend2 (from suspend2_2.2.10-1~3v1ubuntu2_all.deb) ...
dpkg: dependency problems prevent configuration of suspend2:
 suspend2 depends on acpi-support (= 0.95-1~3v1ubuntu0); however:
  Version of acpi-support on system is 0.95.
 suspend2 depends on hibernate (>= 1.94); however:
  Package hibernate is not installed.
 suspend2 depends on initramfs-tools-suspend2 (>= 0.4-3v1ubuntu1); however:
  Package initramfs-tools-suspend2 is not installed.
 suspend2 depends on linux-image-2.6.20-16-generic (>= 2.6.20-16.29+suspend2~2.2.10) | linux-image-2.6.20-15-386 (>= 2.6.20-16.29+suspend2~2.2.10); however:
  Version of linux-image-2.6.20-16-generic on system is 2.6.20-16.29.
  Package linux-image-2.6.20-15-386 is not installed.
 suspend2 depends on suspend2-userui-usplash (>= 0.7.1); however:
  Package suspend2-userui-usplash is not installed.
dpkg: error processing suspend2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 suspend2


i'm a noob, is this what i should be doing?  i'm reading all about the kernal(didnt install or recompile anything) stuff and i know a little bit about it, however i thought this meta package would do everything for me

if anybody could help, thanks

also, do i need a graphics driver installed? or is all of this stuff independent from it? ty

---

### Post by blingboi on 2007-08-03
bump,need help :)

---

### Post by blingboi on 2007-08-03
argh!, i hate being in windows right now, if anyone can put up a quick guide on what I should get from trevinos repo and how to use it, it would be much appreciated! :) :)

---

### Post by reacocard on 2007-08-05
blingboi, the easiest way to fix it is to go to [trevino's site]("http://3v1n0.tuxfamily.org/"), download the suspend2 package and install it by hand. There's an error in the repo package lists that makes it fail.

@Trevino - If you see this, remove the falcon.db and regen the package lists to fix the problem.

---

### Post by blingboi on 2007-08-09
could anyone be more specific about what reacocard is saying?  i cant really see what to do

---

### Post by reacocard on 2007-08-09
> **blingboi said:**
> could anyone be more specific about what reacocard is saying?  i cant really see what to do

Oops, sorry, just reread your post and sae you had already done what I said. >.< Try installing the suspend2 package you got with wget using gdebi instead of dpkg. If that fails, download all the suspend2-* packages the same way and install them all at once with one dpkg command.

---

### Post by catfishk on 2007-08-12
here's a repository for suspend2 patched kernels and packages for use in edgy, if it hasn't been mentioned (i didn't read all the posts, sorry!);

 [HTML] deb http://download.tuxfamily.org/3v1deb edgy suspend2
deb-src http://download.tuxfamily.org/3v1deb edgy suspend2[/HTML]

 taken from here:

 [http://3v1n0.tuxfamily.org/dists/edgy/suspend2/](http://3v1n0.tuxfamily.org/dists/edgy/suspend2/)

---

### Post by karimha on 2007-08-23
Hi, 

thanks to Treviño for these very nice suspend-enabled kernels. Very useful for newbies like me!
The suspend package works very smoothly with on one on my laptops but the other one doesn't seem to like much. Anyway, my biggest concern now is that on resume neither my internet connection nor my 4-slots usb cardbus pcmcia are working. For the internet connection it is not so surprising because I have a speedtouch 330 usb modem which is one of the most troublesome pieces of hardware out there in terms of linux compatibility. On resume, there is no way to have the modem manager authenticate, it just freezes. 
As for the usb cardbus pcmcia, pccardctl tells me it is recognized by the system, but none of the accessories I plug in the slots works. The usb pens and the wacom tablet seem to get juice (the leds are on) but they don't work at all. Is there a way to manually reset the pcmcia services at a system level, just as it happens automatically on boot-up?

Please, any help would be very much appreciated; I've spent two entire weeks to get the suspend feature to work on my laptop, and no theses problems make it virtually useless because I need a full reboot to get the internet and the usb slots to work.

Thanks.

---

### Post by karimha on 2007-08-23
BY the way, I am on feisty.

thanks again.

---

### Post by reacocard on 2007-08-23
> **karimha said:**
> Hi, 

thanks to Treviño for these very nice suspend-enabled kernels. Very useful for newbies like me!
The suspend package works very smoothly with on one on my laptops but the other one doesn't seem to like much. Anyway, my biggest concern now is that on resume neither my internet connection nor my 4-slots usb cardbus pcmcia are working. For the internet connection it is not so surprising because I have a speedtouch 330 usb modem which is one of the most troublesome pieces of hardware out there in terms of linux compatibility. On resume, there is no way to have the modem manager authenticate, it just freezes. 
As for the usb cardbus pcmcia, pccardctl tells me it is recognized by the system, but none of the accessories I plug in the slots works. The usb pens and the wacom tablet seem to get juice (the leds are on) but they don't work at all. Is there a way to manually reset the pcmcia services at a system level, just as it happens automatically on boot-up?

Please, any help would be very much appreciated; I've spent two entire weeks to get the suspend feature to work on my laptop, and no theses problems make it virtually useless because I need a full reboot to get the internet and the usb slots to work.

Thanks.

You can probably solve it by telling suspend2 to unload the kernel modules for those items before hibernating, and then adding them back in afterwards. All the configuration files are in /etc/hibernate, it shouldn't be too hard to figure out.

---

### Post by karimha on 2007-08-25
> **reacocard said:**
> You can probably solve it by telling suspend2 to unload the kernel modules for those items before hibernating, and then adding them back in afterwards. All the configuration files are in /etc/hibernate, it shouldn't be too hard to figure out.

Thanks reacocard. 
nfortunately, my knowledge of ubuntu is really too poor to figure out this apparently simple tweak. I guess the request to suspend2 to unload and reload the modules should be added to 'on-suspend.sh' and 'on-resume.sh' respectively. However, I don't know what the syntax should be. Also, I am thinking that this might work with the usb slot pcmcia problem because the service running the card is indeed included in the kernel, but probably not for the speedtouch usb modem problem, because the manager running this service is not (yet) in the kernel. So I wonder how it would be possible to completely stop it before suspend. I get to stop the connection, and even the manager, which is GUI-driven, but there still is something remaining in the system which will prevent the authentication once the cable is unplugged - which is what the system assumes when resuming without a cold reboot. I try with another, more manual, method to get the speedtouch modem working and it does the same. I can connect and disconnect the connection, but whenever the cable is unplugged - or the system resumed without reboot-  there is no way to authenticate.

Thanks for any help.

---

### Post by karimha on 2007-08-25
OK, I fixed the pcmcia problem.
In 2.6 kernels, the pcmcia service is run by pcmciautils, but the command to use is pccardctl. There is a suspend and resume option, but it seems to not work on my comp. So I tried the pccardctl eject and insert commands, which magically work!

So if anyone needs a pcmcia card to work after resume here is what you have to do:
open with a text editor the file: /etc/hibernate/on-suspend.sh and add the command:
sudo pccardctl eject
now open the file /etc/hibernate/on-resume.sh and add:
sudo pccardctl insert

Hope it can help someone. 

As for the speedtouch connection, I still need some help!

Cheers

---

### Post by karlrt on 2007-09-06
> **blk_jack said:**
> (December 12th, 2006)
Tried to install it on my amd64 machine and there were missing 64bit packages that prevented the installation.

It sounds like you've got a great thing going here and I was wondering when/if you'll have those missing packages for amd64?

Thanks! 8)

Hi Trevino! used your repository for i386, and you claim it works for amd64 so i did a new install,   but i got the same problems:

your suspend2 package depends on "acpi-support" "initramfs-tools-suspend2" and "suspend2-userui-usplash" which are all not available for amd64!!!

is it possible to get suspend2 for amd64 feisty?

hope to get an answer!!!

---

### Post by harty83 on 2007-09-19
Any hopes of getting the latest feisty kernel compiled with suspend2 soon?  I know you've been cranking on the compiz repository which I love :-)

Also, I've read in a couple different spots of suspend2 modules.  Would that mean that there would be the possibility of not having to recompile kernels but rather simply load a module?

Thanks!
Alan

---

### Post by reacocard on 2007-09-19
I'd like to re-re-re-iterate the request for a guide. I just upgraded to gutsy so now I have no suspend2, and compiling via [this guide]("http://ubuntuforums.org/showthread.php?t=311158") has always yielded unsatifactory results. Even just a set of commands for the terminal or some quick pointers would be great.

---

### Post by mbeierl on 2007-10-25
A guide?  For compiling the kernel with tuxonice?

Here's my quick and dirty:
```

wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.23.1.tar.bz2
wget http://www.tuxonice.net/downloads/all/tuxonice-3.0-rc1-for-2.6.23.patch.bz2
tar jxvf linux-2.6.23.1.tar.bz
cd linux-2.6.23.1.tar.bz
bzcat ../tuxonice-3.0-rc1-for-2.6.23.patch.bz2 | patch -p1
make xconfig
[select appropriate Hibernation options and save]
fakeroot make-kpkg --stem linux --initrd kernel_image
[have a coffee...]
cd ..
dpkg -i *.deb

```

---

### Post by reacocard on 2007-10-26
> **mbeierl said:**
> A guide?  For compiling the kernel with tuxonice?

Here's my quick and dirty:
```

wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.23.1.tar.bz2
wget http://www.tuxonice.net/downloads/all/tuxonice-3.0-rc1-for-2.6.23.patch.bz2
tar jxvf linux-2.6.23.1.tar.bz
cd linux-2.6.23.1.tar.bz
bzcat ../tuxonice-3.0-rc1-for-2.6.23.patch.bz2 | patch -p1
make xconfig
[select appropriate Hibernation options and save]
fakeroot make-kpkg --stem linux --initrd kernel_image
[have a coffee...]
cd ..
dpkg -i *.deb

```

no, compiling the *Ubuntu* kernel with tuxonice. That is to say, packaged and configured exactly the the ubuntu kernel, just with tuxonice enabled, as trevino here has been doing.

---

### Post by Rui Pais on 2007-11-03
> **reacocard said:**
> no, compiling the *Ubuntu* kernel with tuxonice. That is to say, packaged and configured exactly the the ubuntu kernel, just with tuxonice enabled, as trevino here has been doing.

Hi,
in that case you only need to tweak some of the above instructions:
```
sudo apt-get install build-essential libncurses5-dev kernel-package **linux-source**
cd /usr/src
tar xvjf linux-source-2.6.22.tar.bz2
cd linux-source
wget [http://www.tuxonice.net/downloads/all/tuxonice-3.0-rc1-for-ubuntu-gutsy-20071012.patch.bz2](http://www.tuxonice.net/downloads/all/tuxonice-3.0-rc1-for-ubuntu-gutsy-20071012.patch.bz2)
patch -p1 <./tuxonice-3.0-rc1-for-ubuntu-gutsy-20071012.patch.bz2
make oldconfig
make menuconfig (or xconfig)
(check tuxonice and any other tweaks)
sudo make-kpkg -initrd --revision=tuxonice kernel_image kernel_headers modules_image
```
cd ..
and dpkg your new kernel *.deb

If you want too restricted modules, check it here:
[https://help.ubuntu.com/community/CustomRestrictedModules](https://help.ubuntu.com/community/CustomRestrictedModules)

hth

---

### Post by reacocard on 2007-12-01
> **Rui Pais said:**
> Hi,
in that case you only need to tweak some of the above instructions:
```
sudo apt-get install build-essential libncurses5-dev kernel-package **linux-source**
cd /usr/src
tar xvjf linux-source-2.6.22.tar.bz2
cd linux-source
wget [http://www.tuxonice.net/downloads/all/tuxonice-3.0-rc1-for-ubuntu-gutsy-20071012.patch.bz2](http://www.tuxonice.net/downloads/all/tuxonice-3.0-rc1-for-ubuntu-gutsy-20071012.patch.bz2)
patch -p1 <./tuxonice-3.0-rc1-for-ubuntu-gutsy-20071012.patch.bz2
make oldconfig
make menuconfig (or xconfig)
(check tuxonice and any other tweaks)
sudo make-kpkg -initrd --revision=tuxonice kernel_image kernel_headers modules_image
```
cd ..
and dpkg your new kernel *.deb

If you want too restricted modules, check it here:
[https://help.ubuntu.com/community/CustomRestrictedModules](https://help.ubuntu.com/community/CustomRestrictedModules)

hth

unfortunately, the resulting kernel doesn't include firmware, nor does it seem to be compatible with l-r-m or the new l-u-m.  I do have a working tuxonice-enabled kernel now though, it works beautifully in gutsy.  maybe if I have time and I can get that firmware working I'll put together a package set for gutsy. \\:D/

---

