---
title: "Suspend2 in dapper?"
date: 2006-07-22
forum: General Help
---

### Post by grizzly on 2006-07-22
Hi ,
I have been trying to patch and recompile my kernel for suspend to disk ( hibernate)

Uptil now I have downlaoded linux-source, created symlink, did my backup...
and I am currently stuck at this stage:
```

~/documents/applications/suspend2-2.2-for-2.6.15.1/apply
Applying 100-suspend2-2.2-for-2.6.15.1.patch ...
100-suspend2-2.2-for-2.6.15.1.patch will not apply cleanly. Reverse applied patches [Yn]? y 
```
I guess I need to download a different suspend2 patch , but which one??

Now am consulting there different guides, and I am thoroughly confused, how to go about furthur. Please help, I really need to hibernate.. I mean not me, but the PC.

Guides:
[http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper)
[http://ubuntuforums.org/showthread.php?t=75443&highlight=hibernate](http://ubuntuforums.org/showthread.php?t=75443&highlight=hibernate) 
[http://www.suspend2.net/HOWTO-2.html](http://www.suspend2.net/HOWTO-2.html) - According to this, it seems that some manual editing is needed..

---

### Post by reacocard on 2006-07-22
there are precompiled kernels for dapper that have suspend2 support. see the link in my sig for instructions.

---

### Post by grizzly on 2006-07-22
on apt-get update I get 
```
Ign http://dagobah.ucc.asn.au dapper/ Release.gpg
Ign http://dagobah.ucc.asn.au dapper/ Release
Ign http://dagobah.ucc.asn.au dapper/ Packages
Err http://dagobah.ucc.asn.au dapper/ Packages
  403 Forbidden
Failed to fetch http://dagobah.ucc.asn.au/ubuntu-suspend2/dapper/Packages.gz  403 Forbidden
Reading package lists... Done

```
I have a feeling  I screwed some key thing.. suggestions

---

### Post by reacocard on 2006-07-22
hummm. that's never happened to me before. maybe the server was down when you tried? i just did apt-get update and it went through fine. if it still won't work, you can always get the packages from the repo by hand.

---

### Post by grizzly on 2006-07-22
OK, thanks, just tell me one more thing. which exact linux-image package should i go for? 

About the error.. is most probably some problem at my end. this gpg key thing is quite irritating.

---

### Post by reacocard on 2006-07-22
the linux-image you need depends on your processor.

it should have in it:
for Intel: 686-nosmp
for Intel dual-core: 686
for AMD: k7-nosmp
for AMD dual-core: k7

the most recent version will have 2.6.15-26 and 2.2.7.4-2 in it also.

so, if you're like me and have a single-core Intel, you'll want the *linux-image-2.6.15-26-686-nosmp_2.6.15-26.suspend2-2.2.7.4-2_i386.deb *
package

---

### Post by grizzly on 2006-07-24
OK I am lamost there now.
I installed the required packages, hibernate it seems to work .
I get the userui, the "writing caches" "atomic thing" message. 

But resume isn't working. 

Possible problems:
1.
>   s hibernate
You haven't specified a resume2= parameter on your kernel command line

Your GRUB or LILO config should have something like resume2=swap:/dev/hdaX
where /dev/hdaX is your swap partition. You will then need to either reboot
after doing so or set it manually (this time only) using:
    echo swap:/dev/hdaX > /sys/power/suspend2/resume2
hibernate: Aborting.


So added resume2=swap:/dev/hda8 to the menu.lst file , BUt I am still getting this message everytime.

2. on hibernateing I get 
"powering down" .. followed by..
"powerdown failed" 


My systrem uses AT power supply ( requires manual powerdown) btw.

Suggest something plz

---

### Post by reacocard on 2006-07-24
maybe you edited the line incorrectly? here's mine:
```
# kopt=root=/dev/hda6 ro resume2=swap:/dev/hda8
```
after editing, you need to update grub:
```
sudo update-grub
```

hope that helps since i have no idea about the other thing.

---

### Post by ketsugi on 2006-07-25
```
Failed to fetch http://dagobah.ucc.asn.au/ubuntu-suspend2/dapper/Packages.gz  Error reading from server. Remote end closed connection
Reading package lists... Done
W: GPG error: http://dagobah.ucc.asn.au dapper/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A4FCD4033A111759

```

:(

By the way, what users should be installing the Suspend2 kernel? How do I know if it'll work for my laptop?

---

### Post by grizzly on 2006-07-25
> maybe you edited the line incorrectly? here's mine:

IT WORKS!!! That was the problem I wasn't adding it at the corect line. Thanks a tonne , you are great!!

Entry from my menu.lst:
```
title           Ubuntu, kernel 2.6.15-26-686-nosmp
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-26-686-nosmp root=/dev/hda5 ro quiet splash [COLOR="Red"]resume2=swap:/dev/hda8[/COLOR]
initrd          /boot/initrd.img-2.6.15-26-686-nosmp
savedefault
boot

```

So here are the steps I took for suspend2 in dapper

1.GO to [http://dagobah.ucc.asn.au/ubuntu-suspend2/dapper/](http://dagobah.ucc.asn.au/ubuntu-suspend2/dapper/) 
2. Download and install the following packages: 
initrsamfs
linux-image 
acpi-support
hibernate script
suspend2-userui

READ reacocard INSTRUCTIONAS ABOVE TO KNOW WHICH 'LINUX-IMAGE' YOU NEED

3. once installed add 'resume2=swap:/dev/hdax' to /boot/grub/menu.lst 

 LOOK AT THE ABOVE CODE TO KNOW EXACTLY WHERE THIS HAS TO BE ADDED

4. ```
 sudo update-grub
```

5. ```
 sudo hibernate 
```

==========================================

If the above fails, first reboot then try again.
If still doesn't work post the first entry of your menu.lst

---

### Post by reacocard on 2006-07-25
to fix the gpg error:

```
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys A4FCD4033A111759

gpg --armor --export 3A111759 > keyName.gpg

sudo apt-key add keyName.gpg
```

BTW, do you think i should make a HOWTO for this?

---

### Post by mbeierl on 2006-07-25
There's not much to it, but I have been SOOOOO happy with suspend2, that anything that makes it easier for folks to switch over to ubuntu with suspend2 would be of great benefit.

For what it's worth, here's my vote to have the ubuntu development team incorporate suspend2 into the stock kernel instead of the kernel suspend (which gives no real feedback)

---

### Post by reacocard on 2006-07-25
Alright, I'll start putting together a HOWTO. it might take awhile though. i'm going on vacation in a few days and there's lots to do to get ready.

---

### Post by Treviño on 2006-07-27
Mh, thanks for your work... I've tried to install swsuspend2 in my kubuntu dapper machine (in which I'm using also XGL+compiz with a fglrx ATI card).

When I give the "sudo hibernate" command I get the suspend2 usplash screen and it starts working, it goes well until it says "atomic thing", then all freezes... I mean, no CPU or disk are working, but ctrl+alt+Fx keys do... Anyway also waiting a few my Notebook doesn't turn off.
Obiouvsly, on forced-rebooting there's no resume available.

My /var/log/hibernate.log "says":
> Starting suspend at gio lug 27 18:20:59 CEST 2006
hibernate: [01] Executing CheckLastResume ...
hibernate: [01] Executing CheckRunlevel ...
hibernate: [01] Executing LockFileGet ...
hibernate: [01] Executing NewKernelFileCheck ...
hibernate: [10] Executing EnsureSwsusp2Capable ...
hibernate: [11] Executing XHacksSuspendHook1 ...
hibernate: [89] Executing SaveKernelModprobe ...
hibernate: [91] Executing ModulesUnloadBlacklist ...
hibernate: [95] Executing XHacksSuspendHook2 ...
hibernate: [97] Executing ChangeToSwsuspVT ...
hibernate: [98] Executing CheckRunlevel ...
hibernate: [98] Executing FullSpeedCPUSuspend ...
hibernate: [98] Executing Swsusp2ConfigSet ...
hibernate: [99] Executing DoSwsusp2 ...
hibernate: Activating suspend ...

No way to have more detailed suspend/hibernate logs?

I know that XGL could cause problems, btw I think that those should be related mostly to resume than suspending, isn't it?
About ATi fglrx drivers, they [should support suspend2](http://wiki.cchtml.com/index.php/Suspend2).

Bye and thanks!

---

### Post by reacocard on 2006-07-27
yeah, i also use compiz. it's possible to get it working (somewhat). add these lines to your /etc/hibernate/common.conf

```
OnSuspend 20 killall compiz.real
OnSuspend 21 killall compiz-start
OnResume 21 /usr/bin/compiz-start
```

that will kill compiz before hibernating, so it won't interfere. it's also supposed to restart compiz on resume, but that doesn't work, for some reason.
if this doesn't work, take a look around the files in /etc/hibernate, and also at "man hibernate.conf". there are tons of options to play around with.

---

### Post by Treviño on 2006-07-27
Do you think that this should fix my hibernation problem? :o
Hasn't swsuspend2 problems with XGL (I mean only the graphic server)?

I've read also in the wiki I linked you before that I should add the option "ProcSetting extra_pages_allowance 5000" to hibernate.conf file...
I've done it, but It doesn't seem to do anything :o. Maybe I've used a wrong file... in which should I put it?

Thanks!

---

### Post by reacocard on 2006-07-27
put it in common.conf

hibernate.conf - order to try .conf files
common.conf - common config for all methods
suspend2.conf - config specific to suspend2


idk about XGL. I use AIGLX, which appears to have no problems with suspend2.

---

### Post by Treviño on 2006-07-27
Mmhmh... I'll try it... Who knows about AIGLX... It should be better, becouse it uses standard Xorg server, btw I'll let you know what I'll get after next hibernate... :)

Bye!

---

### Post by grizzly on 2006-07-27
my cdrom isn't detected with using this kernel!! :( 

[COLOR="Sienna"]> ``````> >[/COLOR] 
s mount -t iso9660 /dev/hdc /mnt/h 
mount: special device [COLOR="Red"]/dev/hdc does not exist[/COLOR]

[COLOR="Sienna"]
``````> > [/COLOR] ls /dev hd*
/dev/hda  /dev/hda1  /dev/hda2  /dev/hda5  /dev/hda6  /dev/hda7  /dev/hda8  /dev/hda9

if use the original kernel everything is fine. Help plz, I have been smashing my head over this for a while now.

Another thing : [this post ]("http://ubuntuforums.org/showpost.php?p=150022&postcount=2"), talks abt some hotplug thing, but it is not applicable to dapper. see if you can make sense of it.

thx

edit: I spoke too soon, the link I posted above did solve my problem :D . though i never expected that, since symlinks it asked to create, looked strange..

---

### Post by reacocard on 2006-07-27
which specific kernel are you using? the -nosmp kernels don't load the restricted modules, so that could be the problem. what cdrom drive are you using?

---

### Post by Strife on 2006-07-27
I have issues with this when using the -386 kernel version, but not the -686-nosmp version (I was mainly trying to use -386 so that I could use the fglrx driver for my ATI card, but it's honestly not that important).

Anyway, here is some of the relevent stuff from dmesg:

```

[17179656.512000] Starting to save the image..
[17179656.516000] Writing caches...
[17179657.292000] 20%...40%...60%...80%...100%...done.
[17179664.116000] Doing atomic copy.
[17179664.116000] ata2: suspend device
[17179664.116000] ata1: suspend device
[17179664.624000] eth1: Going into suspend...
[17179664.628000] ACPI: PCI interrupt for device 0000:03:03.0 disabled
[17179664.644000] ACPI: PCI interrupt for device 0000:03:01.0 disabled
[17179666.128000] ACPI: PCI interrupt for device 0000:01:00.0 disabled
[17179666.128000] ata_piix 0000:00:1f.2: suspend PCI device
[17179666.128000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[17179666.144000] ACPI: PCI interrupt for device 0000:00:1e.2 disabled
[17179666.144000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[17179666.160000] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
[17179666.160000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
[17179666.160000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
[17179666.160000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[17179666.160000] Pageset1 has grown by 3536 pages. Only 500 growth is allowed f
or!
[17179666.160000] 
[17179666.160000] Error -1 suspending

```

After that, I get back into X and I see an error message in my terminal telling me to check dmesg. Any ideas?

---

### Post by reacocard on 2006-07-27
Strife, try adding
```
ProcSetting extra_pages_allowance 5000
```
to /etc/hibernate/suspend2.conf

---

### Post by Strife on 2006-07-28
> **reacocard said:**
> Strife, try adding
```
ProcSetting extra_pages_allowance 5000
```
to /etc/hibernate/suspend2.conf

Cool, I'll give that a try whenever I restart next time. Thanks.

---

### Post by Strife on 2006-07-28
I also just experienced one other issue... After waking up my computer, I found that I could not get my wireless interface to connect to the available wireless network. Running iwlist, it found the correctly available networks, but I couldn't obtain an IP for some reason without restarting.

Has anyone else experienced these problems or know a way to get the  device to actually respond correctly?

---

### Post by Treviño on 2006-07-29
Well... As I said before I've an ATi card with XGL in :1 plus compiz, and now I have been able to hibernate...! :)
But... Not always :(

Fist of all I've tried to suspend & resume closing my X/Xgl sessions, so from terminal tty1 and worked well, then I've added 
```
 ProcSetting extra_pages_allowance 5000to /etc/hibernate/common.conf
```

There I've added this code too:
```
# Compiz stop and reload
OnSuspend 20 killall compiz.real
OnSuspend 21 killall cgwd
OnResume 21 /usr/bin/restartCompiz.sh
``` 
On *_first hibernation_* all goes well, compiz and decorations closes and my system hibernate!
On next *restart* **XGL** reloads and everything else... Also **compiz** reloads, thanks to the script I've added "before" but... It is loaded as root, and so root's gconf configuration is used, with bad settings. So I've to restart it manually.
_*Isn't there a way to reload things with user rights?*_ (Who knows, maybe a ~/.hibernate folder... :D)
[EDIT: maybe using a script like the one that is posted in the compiz forum  thread linked below I can avoid this... ]

Btw, this isn'te the **main problem**... Because from my (short) experience, I've noticed that ***suspend works only once a session***!
I've found something [here]("http://www.compiz.net/viewtopic.php?id=1520"), I don't know if it could help me (us).

About wireless, maybe try to unload your wireless module before suspending (rmmod <modulename>), and reloading it manually when you're restart...


BYE!

---

### Post by reacocard on 2006-07-29
for networking, in /etc/hibernate/common.conf there is a section like this:
```
### network
# DownInterfaces eth0
# UpInterfaces auto
```

try using this for your network card. using eth0, for example, add these lines:
```
DownInterfaces eth0
UpInterfaces auto
```

hopefully that will work.

---

### Post by reacocard on 2006-07-29
> suspend works only once a session

that's not entirely true. if hibernate is launched via "sudo hibernate" it only works once, unless you remove a file first. (look at the output of sudo hibernate to know which) If launched via System -> Quit -> Hibernate (when enabled) suspend works multiple times, but compiz will not restart at all. What I do is just kill compiz, and use the tray icon to restart it each time I resume. It's a tad annoying, but it works.

---

### Post by Treviño on 2006-07-30
My "sudo hibernate" output is
```
/usr/sbin/hibernate: 6: cannot create /sys/power/suspend2/last_result: Permission denied
```...
Is this the file I've to remove?

Couldn't a "rm <file-to-remove>" be added to the OnResume command?

Anyway, I don't have Gnome, but KDE, so I havent the menu you stated; I'd have, but I run compiz in :1 (due to ATi + XGL), so the only way I have is to use the "sudo hibernate" way... Also if kpowersave (klaptop-daemon) could help me...

Another way could be using the power button to hibernate using 
```
# gedit /etc/acpi/events/powerbtn
action=/usr/sbin/hibernate
#action=/etc/acpi/powerbtn.sh
```
Isn't it?

Anyway I'll test it something...

---

### Post by Treviño on 2006-07-30
Sorry for double-posting, btw I've tried to use power buttn to suspend, but after removing powersaved (I used it with kpowersave, but it seems that it manage my power button overwriting my acpi settings.... :o), I got the button working...
But also using this trick, my PC suspends only once a session.

I mean, on second time I try to suspend, my pc freezes at the "doing atomic copy" message.
Only forced-power-down can "help" me... :(

Any other way?

EDIT: I've found that other users have the same problem with this version of suspend2: [http://lists.suspend2.net/lurker/message/20050822.121703.a4d3df8c.en.html](http://lists.suspend2.net/lurker/message/20050822.121703.a4d3df8c.en.html)
Could you try to make packages for a previous version of suspend2 (one of the those stated by that user)? Maybe this bug could be solved... :(

---

### Post by reacocard on 2006-07-30
there are older packages available in the repo. try a "sudo killall hibernate" before tring to sleep again. and yeah, the button uses the acpi settings. look in /etc/default/acpi-support for the option to enable it.

---

### Post by Treviño on 2006-07-31
I'll try older packages... Btw no way to killall hibernate, becouse... Simply it isn't still running... :|

---

### Post by Treviño on 2006-07-31
Well... Few words... It seems that _*I can get my suspend2 to work*_!!

First of all... I noticed that **it isn't needed stopping and restarting compiz** on suspend/hibernate... I don't know how it is with AiGLX, but using XGL I can resume my compiz status without killing any process before suspending!
So, imho you can safely remove your "OnSuspend / OnResume" killall ;)

The thing that caused me not to suspend was only one: fglrx drivers... As I could have imagined :(

In fact the setting that ATi user should add (ProcSetting extra_pages_allowance X) isn't, obiouvsly, a random value but from what I've understood it *says* to Suspend2 how much space of swap memory it should use to save the graphic card video memory...
Generally (I mean using a standard X server), this value can set safetly to low values (like 5000, in fact) but using XGL which loads much data in the Vram of your card this value could be too little, and this - from my experience - makes suspend2 to freeze while it does the "atomic copy".
So reading [this thread]("http://lists.suspend2.net/lurker/message/20060624.143436.c5a5f82f.en.html") of Suspend2 mailing-list, and expecially [this message]("http://lists.suspend2.net/lurker/message/20060626.101725.740570ff.en.html")
I've understood that I'd to increase my *extra_pages_allowance* value. Reading the message I've linked above I selected a much higher value, and with a 64Mb vram Card I set it to 20000. Maybe its too much, but I prefer to be a bit exaggerate not to lose my session at all, and it doesn't seem to use too much extra time.
So set ```
ProcSetting extra_pages_allowance <your-value>
```where <your-value> it's about Your-vram-size/4 + extra padding.
Btw, you should find your best value by looking your suspend2 debug informations with
```
cat /sys/power/suspend2/debug_info | grep "Extra pages"
```
that should output something like
> - Extra pages    : 7552 used/20000.
Check this value after some hibernations, and so find your right value!
For _*furhter informations*_, I've added also something more [here](http://wiki.cchtml.com/index.php/Suspend2).

Another thing that I had to reset is the acerhk module that I use to manage my wireless power-button/led. After hibernate/suspending this module isn't reloaded. So, to reuse it I had to include two new OnResume lines to modprobe and inizialize it...

Anyway now, here's how it looks my common.conf file:
```
# ... Preset settings - not included ... #

# Reload Acerhk module for wireless power
OnResume 20 modprobe acerhk force_series=290 usedritek=1 verbose=1 autowlan=1 poll=0
OnResume 21 echo 1 > /proc/driver/acerhk/wirelessled

# ATi suspending hack
ProcSetting extra_pages_allowance 20000
```
Now I can suspend and hibernate with no problems and, no more once a session (before was "once" only becouse I hibernate when I used only a few  of my vram!) :)

I hope this could help someone...!

BYE!

PS: I noticed that after changing this ProcSetting you should reboot your PC before suspending, or the hibernate script will crash your system. This what has happened to, me. Let me know what happens to you!

---

### Post by reacocard on 2006-08-01
Great to hear you got it working, Trevino. I'll make sure that bit about the ati drivers gets into my HOWTO.

EDIT: It appears its not just ati and xgl. your tweak worked perfectly on my intel graphics with aiglx. Thank you so much for discovering this.

---

### Post by Treviño on 2006-08-01
I'm monitoring my hibernations using this /etc/hibernate/common.conf
```
OnResume 20 cat /sys/power/suspend2/debug_info | grep "Extra pages" >> /home/user/suspend2-debug
```
After some suspensions I think that I'll be able to find a better maximum extra_pages_allowance value.

Now I noticed that the value needed it is always under 7500, but I want many tests. ;)

BYE!

---

### Post by Andreas Isaksson on 2006-08-01
```

[  239.938470] CPU 1 is now offline
[  239.942718] CPU1 is down
[   16.130836] Initializing CPU#1
[   16.161251] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   16.161254] CPU: L2 Cache: 512K (64 bytes/line)
[   16.161256] CPU 1/1 -> Node 0
[   16.161258] CPU: Physical Processor ID: 0
[   16.161259] CPU: Processor Core ID: 1
[   16.161751] CPU 1: Syncing TSC to CPU 0.
[   16.161849] CPU 1: synchronized TSC with CPU 0 (last diff 0 cycles, maxerr 518 cycles)
[   16.164122] CPU1 is up

```

I'm running an amd64 dual core processor. is this right? that suspend 2 ram only should bring down one cpu? i can't see anywhere that CPU0 is brought down or initialized. anyway it's working perfectly besides long resume times.

---

### Post by frenkel on 2006-08-01
Thanks a lot for these kernels. Suspend2 has always worked great for me, also when I used Gentoo. I always used this because the standard suspend (in mainstream kernel) doesn't work for me.
Too bad it isn't shipped as default,

---

### Post by Treviño on 2006-08-01
True... Why isn't suspend2 shipped with standard kernel? Anyone knows if it will be in the future? :o

---

### Post by reacocard on 2006-08-01
> Why isn't suspend2 shipped with standard kernel?there's a discussion of this on the ubuntu-devel mailing list. basicaly, they won't incorpoate it because it makes so many changes. they'll accept it  once it is accepted upstream.

---

### Post by Treviño on 2006-08-02
Please Delete This... Double Post.

Sorry!

---

### Post by Treviño on 2006-08-02
:( Too bad... But also reading suspend2 mailing list I can't understand why it isn't included in the main kernel code, also if as an alternative (both system could be there, I think; just configuring the kernel before compiling one can select his best way. Isn't it?)... :o

Anyway actually my extra-pages record is this: 8281 used/20000.
Anyone is thesting suspend2, please monitor it as said before ;)

Regarding patched-kernel updates... Are you the only who does this work? Maybe could I help you? :o

---

### Post by reacocard on 2006-08-02
I don't create the kernels. I've just spent a lot of time fiddling with them. The email address of the person who makes the kernels is on [this page.]("http://dagobah.ucc.asn.au/dapper-kernels/")

---

### Post by Treviño on 2006-08-02
Ah, ok... I thought you were the same person :D
Are you monitoring your max-pages? What's your record? :D

---

### Post by reacocard on 2006-08-02
havent been hibernating much, since my laptop's been plugged in constantly. I'll post my info when I have enough.

---

### Post by yigal.weinstein on 2006-08-06
first my thanks to reacocard your instructions for installing ssp2 was so simple and it worked beautifully.  

Second just to add a little eye candy rather than 
```
#hibernate
```
is there a way to add instructions to hibernate from the poweroff icon i.e. through the System=>Quit..=>Hibernate icon.

I.e. where or can I change what ever hibernate does (probably something like /etc/acpi/hibernate.sh) do to something like:
```
$gksu hibernate
```   

thanks

---

### Post by yigal.weinstein on 2006-08-07
excuse me I see the icon does use suspend2. Great!  The acpi suspend was borking my computer so I had to hard kill it.  So I was frightened of using the icon, but it worked.  So again thanks for the awsome work.  I remember the headache of installing suspend2 in Debian where there was virtually no support.  It took me days to get it to work and then the tweaking extra days your work works and works well.

Custom Kernels?

I need to compile my own kernel.  This is because I have a laptop that gets very hot and therefore I need acpi control but I only get it with a custom dsdt.  Is there a way of easily using your scripts for a custom kernel.  I know it must not be so difficult but I thought I would ask if you could give me a quick answer. Thanks

---

### Post by mo-seph on 2006-09-08
Hello,

I've got suspend2 working properly, which is fantastic. However, the suspend2 package didn't install the kernel images for me - I had to manually install
linux-headers-2.6.15-26-686-nosmp and linux-image-2.6.15-26-686-nosmp.

Any thoughts?

---

### Post by reacocard on 2006-09-08
> I've got suspend2 working properly, which is fantastic. However, the suspend2 package didn't install the kernel images for me - I had to manually install
linux-headers-2.6.15-26-686-nosmp and linux-image-2.6.15-26-686-nosmp.
the suspend2 package no longer depends on the kernel image.

BTW, the -nosmp kernels are depreciated. SMP support has been folded into the -686/-k7 kernels. use them instead.

---

### Post by Treviño on 2006-09-27
After ubuntu main kernel upgrade there's no new version for suspend2 kernel... No news about it? :o

---

### Post by jakster on 2006-10-16
@trevino I found an solution, see here
[http://ubuntuforums.org/showthread.php?p=1622930#post1622930](http://ubuntuforums.org/showthread.php?p=1622930#post1622930)

---

### Post by frogotronic on 2006-11-26
Q1) If I'm running the 2.6.15-27-686 kernel, can I use a the dagobah repos?  It looks as if there is only a 2.6.15-26-686 kernel.

Q2) Can I use restricted modules? (Nvidia driver) with these kernels?

Thanks

---

### Post by reacocard on 2006-11-27
> **cement_head said:**
> Q1) If I'm running the 2.6.15-27-686 kernel, can I use a the dagobah repos?  It looks as if there is only a 2.6.15-26-686 kernel.

Q2) Can I use restricted modules? (Nvidia driver) with these kernels?

Thanks

1) Yes, but you'll only have suspend2 on the 2.6.15-26 kernel

2) I think so.


There are also suspend2 packages for edgy now. See [here]("http://ubuntuforums.org/showthread.php?t=284994") and [here]("http://3v1n0.tuxfamily.org/dists/edgy/suspend2/").

---

### Post by frogotronic on 2006-11-27
> **reacocard said:**
> 1) Yes, but you'll only have suspend2 on the 2.6.15-26 kernel

2) I think so.


There are also suspend2 packages for edgy now. See [here]("http://ubuntuforums.org/showthread.php?t=284994") and [here]("http://3v1n0.tuxfamily.org/dists/edgy/suspend2/").

i can't run edgy - the fonts in OO are unusable and renders my machine useless.

i don't have the 2.6.15-26 kernel, so I guess I'm out of luck

I also MUST have ability to use the nvidia driver (for twinview)

looks like there's no solution - compiling a kernel is a bit beyond me, and most of the howto's are confusing

- CH

---

### Post by reacocard on 2006-11-27
> **cement_head said:**
> i don't have the 2.6.15-26 kernel, so I guess I'm out of luck

Well, if you use the repo you'll have the 2.6.15-26 kernel w/ suspend2 *and* the 2.6.15-27 kernel without suspend2. So you can just use the repo and try the 2.6.15-26 kernel, and if it works for you, you can just make that your default kernel.

---

### Post by frogotronic on 2006-11-27
> **reacocard said:**
> Well, if you use the repo you'll have the 2.6.15-26 kernel w/ suspend2 *and* the 2.6.15-27 kernel without suspend2. So you can just use the repo and try the 2.6.15-26 kernel, and if it works for you, you can just make that your default kernel.


what's the difference between the 2.5.15-26 and -27 kernels?

security & bug fixes?

- CH

---

### Post by reacocard on 2006-11-27
> **cement_head said:**
> what's the difference between the 2.5.15-26 and -27 kernels?

security & bug fixes?


Yep. That's all.

---

### Post by frogotronic on 2006-12-02
> **reacocard said:**
> Yep. That's all.

So I installed suspend2 from the dagobah repos and used the 2.6.15-26-686 kernel.

X server is broken.

It states that it cannot find my nvidia module

Choosing the regular 2.6.15-27-686 kernel (not from dagobah) loads absolutely fine.

Suggestions on how to fix the X server?  ](*,)

---

### Post by reacocard on 2006-12-02
> **cement_head said:**
> So I installed suspend2 from the dagobah repos and used the 2.6.15-26-686 kernel.

X server is broken.

It states that it cannot find my nvidia module

Choosing the regular 2.6.15-27-686 kernel (not from dagobah) loads absolutely fine.

Suggestions on how to fix the X server?  ](*,)

Try switching the video driver to 'nv' in xorg.conf. If that works, you'll just need to reinstall the nvidia drivers under the new kernel.

---

### Post by frogotronic on 2006-12-02
> **reacocard said:**
> Try switching the video driver to 'nv' in xorg.conf. If that works, you'll just need to reinstall the nvidia drivers under the new kernel.

The "nv" drivers work in the dagobah kernel.  However, when I installed the nvidia drivers (in 2.6.15-27-686 kernel) I used Automatix2.  I'm unsure how to "reinstall/install" the drivers in the 2.6.15-26-686 kernel.  Do I "uninstall" the nvidia drivers via Automatix2 and the reinstall?  Or should I try to install the binary drivers via the nvidia installer, downloaded from the nvidia website?

Thanks
 -CH

---

### Post by reacocard on 2006-12-02
> **cement_head said:**
> The "nv" drivers work in the dagobah kernel.  However, when I installed the nvidia drivers (in 2.6.15-27-686 kernel) I used Automatix2.  I'm unsure how to "reinstall/install" the drivers in the 2.6.15-26-686 kernel.  Do I "uninstall" the nvidia drivers via Automatix2 and the reinstall?  Or should I try to install the binary drivers via the nvidia installer, downloaded from the nvidia website?

Thanks
 -CH

I'm not quite certain, as I don't have an nvidia card myself, but try doing it via Automatix first and if that doesn't work use nvidia's.

---

### Post by frogotronic on 2006-12-03
> **reacocard said:**
> I'm not quite certain, as I don't have an nvidia card myself, but try doing it via Automatix first and if that doesn't work use nvidia's.

Automatix2 uninstall/install didn't work.  I guess I'll have to install by hand, but I may as well recompile the kernel if I'm going to do that.

Thanks,
- CH

---

### Post by Prox on 2006-12-08
I just cant make it working on my T20. If I "sudo hibernate" it start to do this, executing commands..then some hex codes...and that nothing, cursor is blinking but thats all. If I check hibernate.log the last post is "activating sysfs power state disk..."

Any advice?

---

