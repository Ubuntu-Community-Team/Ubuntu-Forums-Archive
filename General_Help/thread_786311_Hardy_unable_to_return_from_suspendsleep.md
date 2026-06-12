---
title: "Hardy unable to return from suspend/sleep"
date: 2008-05-08
forum: General Help
---

### Post by xjgnsdof on 2008-05-08
I'm using Hardy 32-bit and can't return from suspend/sleep. I get a black screen with a perpetually blinking cursor. What's wrong?

---

### Post by itaintover on 2008-05-08
same here...

---

### Post by qrees on 2008-05-08
I have exactly the same problem. System is stuck with blinking cursor. Pressing any buttons (also power button) have no effect. I also think, that PC should be shutdown (so, there is no cursor visible, fan's, disk et.c are not working) when entering suspend to RAM mode.

---

### Post by empthollow on 2008-05-08
I also am unable to return from suspend.  I have a toshiba laptop with ati graphics but i can't blame the fglrx because it doesn't work with ati module either.

---

### Post by xjgnsdof on 2008-05-08
OK, that makes a handful of us with the same problem on different systems. I'm quite surprised that Ubuntu wouldn't have functional suspend/sleep when it does everything else so well.

---

### Post by danwood76 on 2008-05-08
Ive noticed that the ACPI is broken on my Toshiba Laptop (L30) with hardy.
Worked fine in gutsy.
It doesnt realise when I unplug the AC, it also wont boot when not plugged into the AC.

I think this is a kernel issue, and is probably directly related to your suspend issues seeing as its the same module that takes care of both.

---

### Post by xjgnsdof on 2008-05-08
On a related note, my Presario V2570NR notebook recovers from suspend/sleep perfectly every single time. It also has never frozen. It's my desktop that can't seem to wake up.

---

### Post by MC_LA on 2008-05-08
I'm also having the same problem with Hardy not able to recover from a suspend. I have an IBM Thinkpad T43p.

I've had this problem ever since I upgraded from Gutsy to Hardy. Hardy is unusable since every time I stop using if for a few minutes my system locksup.

Any help will be greatly appreciated!  Is there an easy way to turn off the  suspend mode.  I thought I turned it off in the Power Management in Admin, but it still goes to a black screen when unused for a short while (so I'm assuming that it's going into suspend mode).  Thanks!

---

### Post by xjgnsdof on 2008-05-08
> **MC_LA said:**
> I'm also having the same problem with Hardy not able to recover from a suspend. I have an IBM Thinkpad T43p.

I've had this problem ever since I upgraded from Gutsy to Hardy. Hardy is unusable since every time I stop using if for a few minutes my system locksup.

Any help will be greatly appreciated!  Is there an easy way to turn off the  suspend mode.  I thought I turned it off in the Power Management in Admin, but it still goes to a black screen when unused for a short while (so I'm assuming that it's going into suspend mode).  Thanks!

That might be your screen entering sleep mode, as opposed to your system. Perhaps you should verify that.

In the meantime, I have down-clocked my CPU and have not have a lock-up yet (fingers crossed). If that turns out to be a farce, I'll let you all know.

---

### Post by empthollow on 2008-05-08
i have a toshiba laptop that does not return from suspend.  the acpi wasn't supported when i first bought it a few years ago.  I think support was added back in dapper for my laptop.  I have never been able to recover from suspend on my laptop but i did't really try it much in gutsy.  i have tried sleep.sh and it yields the same results as the power manager.

---

### Post by xjgnsdof on 2008-05-10
I can confirm this same problem in Ubuntu Hardy on my VAIO laptop. Again, these power saving features work just fine in Xubuntu, on my Presario laptop.

---

### Post by itaintover on 2008-05-10
there must be some solution to this i can't leave my laptop running cause it freezes, only hard reset helps then and it checks my hdd for errors after that, no good...

my system is ubuntu 8.04, compaq presario f500

---

### Post by empthollow on 2008-05-11
I agree, there must be a solution.  Unfortunately i don't know enough about suspend do diagnose or guess.  In addition, all the solutions i've googled don't work for me.
Hopefully someone will be able to offer an idea.

---

### Post by coloured on 2008-05-12
I have exactly this same issue, I am running Hardy64 bit on a Hp Compaq nx6320, intel centrino duo with 3Gb ram.

---

### Post by itaintover on 2008-05-13
Right now all we can do (if we wanna leave our computer running idle) is setting 'put display to sleep when inactive' to NEVER in system->preferences->screensaver->power management.

---

### Post by danwood76 on 2008-05-14
Are any of you guys able to try with a different kernel version, or recompile the kernel yourself?

Could you all post your system specs and weather or not it worked in previous versions of Ubuntu? And your exact issue?
Im finding it a little hard to draw lines between your issues.

I found my ACPI issues were caused by a new feature introduced in the 2.6.24 kernel.
I think this feature is probably non compatible with my processor (I have a T2080 1.73 GHz Intel Pentium, Yonah Core)
So I think you guys probably arent affected by this.

---

### Post by i speak in math on 2008-05-14
I too cannot recover from suspend. Interestingly, it works okay the first time. I noticed after the first suspend that my network icon changed and my applications were set to sleep in the system monitor. After the second suspend, it just sits with a black screen and does not recover. ctrl-alt-fx does nothing.

Compaq c714nr

---

### Post by xjgnsdof on 2008-05-14
I'm using the 2.6-24-16 kernel. I have never recompiled a kernel before and find no reason to unless there is something drastically wrong with my machine. Perhaps some directions to a fine guide is in order.

---

### Post by danwood76 on 2008-05-14
Did your suspend work under gutsy?
Or is this your first delve into ubuntu?

You can download the gutsy kernel to test with your system from the ubuntu packages repository.
I found them for you: [32-Bit]("http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb")  [64-Bit]("http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-image-2.6.22-14-generic_2.6.22-14.52_amd64.deb")

If you download and install the correct version of this it will add the kernel to your system and it will appear on the bottom of your grub config so you can select it on bootup. (press escape before the grub timer runs out and select 2.6.22-14 from the list)
Test suspend with this kernel and report back, you can always boot back to your original kernel just by restarting and your system will be as it was.

You will probably need to disable compiz (switch off desktop effects in appearance control panel) before rebooting as your graphics drivers probably wont load properly.

---

### Post by xjgnsdof on 2008-05-14
> **danwood76 said:**
> Did your suspend work under gutsy?
Or is this your first delve into ubuntu?

You can download the gutsy kernel to test with your system from the ubuntu packages repository.
I found them for you: [32-Bit]("http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb")  [64-Bit]("http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-image-2.6.22-14-generic_2.6.22-14.52_amd64.deb")

If you download and install the correct version of this it will add the kernel to your system and it will appear on the bottom of your grub config so you can select it on bootup. (press escape before the grub timer runs out and select 2.6.22-14 from the list)
Test suspend with this kernel and report back, you can always boot back to your original kernel just by restarting and your system will be as it was.

You will probably need to disable compiz (switch off desktop effects in appearance control panel) before rebooting as your graphics drivers probably wont load properly.

I've been using Ubuntu since Feisty. I just never got around to compiling a kernel. I'll give it a shot on one of my second-hand computers (which is also having trouble is suspend mode). Thanks for the link.

---

### Post by xjgnsdof on 2008-05-14
I've got Fluxbuntu Gutsy running on the 2.6-22-14 kernel on my second-hand VAIO laptop. Suspend works perfectly; when I select Hibernate, however, I see a black screen with some text that disappears too fast for me to read it all, and I soon go right back to the desktop.

I also have Xubuntu Hardy running 2.6-24-16 on my Compaq laptop. Suspend also works perfectly, but Hibernate still puts me right back on the desktop.

I have Ubuntu Hardy running 2.6-24-16, and neither Suspend nor Hibernate will work properly.

Somehow, I don't think that the kernel has anything to do with my problem. Any ideas?

---

### Post by danwood76 on 2008-05-14
It still could be a kernel issue, seeing that the kernel is the bit that has the ACPI drivers and does all the suspend and hibernating.
It might be that xubuntu does something differently when it sends the suspend message but its still being dealt with by the kernels acpi modules.

Its still worth a test with a lower version kernel, its not much effort and if it functions better it will give an idea of what is causing the issue.

---

### Post by xjgnsdof on 2008-05-14
I installed 2.6-22-14 on my rig, installed the updated menu.lst file, and booted Ubuntu with that kernel. However, the problem remained. The older kernel didn't detect my video card, either, so I wouldn't boot into that 2.6-22-14 even if Suspend did work. Any other suggestions?

---

### Post by itsjustarumour on 2008-05-14
Same problem for me on Hardy 32-bit.  Didn't work on this same rig with Gutsy (2.6.22-14-gerneric kernel) either.

Specs as follows:

Ubuntu 8.04
GNOME 2.22.1 (Ubuntu 2008-04-30)
Linux 2.6.24-17-generic
i686
AMD Athlon(tm) 64 Processor 3400+
1.5 GB RAM
GeForce 6800LE 
NVidia 173.08 driver

---

### Post by Def13b on 2008-05-14
First, a quick disclaimer of sorts, I've only been using Linux now for a little under 2 weeks and I'm not exactly sure what the linked changes did exactly, all I know is they worked perfectly for me.

I setup a Mythbuntu 8.04 box with a nVidia GeForce4 mx 440 not long ago, suspend was a must, resume would however leave me with a black screen and the need to do a hard boot, I tried countless things none of which worked, until this link,

[http://blog.vaxius.net/?p=43](http://blog.vaxius.net/?p=43)

Hopefully this helps someone like it did me.

---

### Post by omnibot on 2008-05-14
> **i speak in math said:**
> I too cannot recover from suspend. Interestingly, it works okay the first time. I noticed after the first suspend that my network icon changed and my applications were set to sleep in the system monitor. After the second suspend, it just sits with a black screen and does not recover. ctrl-alt-fx does nothing.

Compaq c714nr

exactly same problem i have.

on each boot, suspend works fine once...freezes on second suspend and i have to reboot. 

compaq c700

---

### Post by danwood76 on 2008-05-15
I just booted my laptop up and guess what?
It does the same thing, im going to install xfce and see if that suspends.

Looks like it could be an issue with GNOME, im also gonna try suspend on my desktop later.

I never noticed it before as its not a feature I use, if I'm not using my laptop I switch it off, and my desktop never sleeps ;).
I will look into it, with a bit of luck I will find a solution for you.

Have an exam in 3 hours so it will be later on, that thread that Def13b linked looks promising if anyone with an nvidia wants to try it out, I have an ATI so the method is not quite the same.
If I get that idea to work though I will post an ATI guide also.

---

### Post by danwood76 on 2008-05-15
Ive just run some tests on my system.

Installing XFCE still caused the same behaviour.
Tried edititng the acpi-config files with various things, nothing has helped.
Tried removing fglrx which also made no difference.

I have noticed some odd things, GDM seg faults when suspending, not sure if its related or not.

Im compiling the latest kernel git tree to see if the suspend functions are better in the latest kernel.
Will report back later.

---

### Post by empthollow on 2008-05-15
I am actually using fluxbox.  I have attempted suspend with both at and fglrx drivers.  I have used pm-suspend (which is used by gnome) and /etc/acpi/sleep.sh force.  both yield the same result which is no resume.  I've tried various edits to /etc/default/acpi-support which i have found in various posts.  None of these changes have made any difference.  I am using toshiba l25 with radeon x200m.

---

### Post by danwood76 on 2008-05-15
I just tested my vanilla 2.6.26-rc2-git4 kernel build, both suspend and hibernate worked perfectly.

Im going to test a vanilla 2.6.24 to see if its the ubuntu patches causing the issue or if its a kernel bug thats been addressed in the later version.

---

### Post by danwood76 on 2008-05-15
Now tried a vanilla 2.6.24 (the base of ubuntus kernel), suspend and hibernate both work.
This leads me to believe its a ubuntu kernel patch or kernel option causing the issue.

Im going to do a few more recompiles with different configs to test, I will report back if I find anything.

---

### Post by empthollow on 2008-05-15
> **danwood76 said:**
> Now tried a vanilla 2.6.24 (the base of ubuntus kernel), suspend and hibernate both work.
This leads me to believe its a ubuntu kernel patch or kernel option causing the issue.

Im going to do a few more recompiles with different configs to test, I will report back if I find anything.

That's great news!  I tried a fedora 8 live cd and the suspend didn't work there either.  Did you have to modify any config files such as /etc/default/acpi-support to get suspend to resume or is it some kernel option that is messing it up?.

---

### Post by danwood76 on 2008-05-16
No havent changed those configs, its either a kernel option or one of the patches ubuntu uses.
I would expect fedora and ubuntu use some of the same kernel patches, for example the Initrd DSDT patch.

Im compiling the ubuntu source with the kernel config I used for the vanilla 2.6.24, this will probably tell me if the error lies in the patches or the config.
I think this should turn most of the patches off also, with a bit of luck I can turn them on one by one and see which is causing the bug.

---

### Post by danwood76 on 2008-05-17
Well after recompiling with my working config from the vanilla 2.6.24.3 in which suspend and hibernate both worked perfectly I have drawn the conclusion that the issue is with one of the patches the ubuntu team apply to the source.

There is a bug report on launchpad I just found:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226279](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226279)

If you guys add your PC specs to it it may get sorted quicker.

---

### Post by danwood76 on 2008-05-17
In the bug report it says that resume does work it just takes a long time.
I tested this just now and sure enough mine does resume but it takes like 5 minutes :)

---

### Post by MC_LA on 2008-05-17
I'm having the same problem on my Thinkpad T43, but I think my problem is related to the screensaver. When I got into System->Screensaver  a window partially opens, but hangs before it completes. I've turned off all power saving, so I think my laptop is going into screen saver mode when I get the black screen.

---

### Post by MC_LA on 2008-05-17
mine does **not** resume even when left overnight.  Maybe I'm having a different problem...though it sounds very similar

---

### Post by xjgnsdof on 2008-05-17
I posted a confirmation at the bug report page given above.

---

### Post by danwood76 on 2008-05-17
> **MC_LA said:**
> mine does **not** resume even when left overnight.  Maybe I'm having a different problem...though it sounds very similar

Its probably the same issue, or at least connected to it.

---

### Post by Handssolow on 2008-05-17
I assume ACPI handling was changed with the Hardy kernel 2.6.24-16-generic hence these suspend/sleep problems. What was changed and why?

I think I have a linked issue. After the upgrade I was unable to boot 32 bit 8.04 until I altered acpi handling, currently by adding pci=noacpi to the kernel line in  /boot/grub/menu.lst. However, I have to manually switch of the power of my desktop after I've shut down Ubuntu. Hardy boots if use the Gutsy kernel unmodified and I also have no problem with 64bit Hardy.

Here's my Launchpad bug report but I'm not confident that my acpi problem will be resolved for the foreseeable future.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/224268](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/224268)

---

### Post by SaschaL75 on 2008-06-04
Hello,

I've tested out Hardy on a Asus A6000 Laptop with Intel 1,7GHz Centrino with Live CD.
All features like ATI Grafik and Suspend worked fine.

Then I installed Hardy to HDD, got the new ATI Drivers für 3D support.
Now the supend mode doesn't work like yours.
Then I found this:
[see here]("http://wiki.ubuntuusers.de/ATI-Grafikkarten/fglrx/Problembehebung")
Worked!

But an update to Kernel 2.6.24-18... now the problem is the same again.
What can we do? Suspend is important for me.

Bye
Sascha

---

### Post by danwood76 on 2008-06-04
In the launchpad bug I posted earlier there is a working kernel, the second one Tim Gardner posted worked perfectly for me.

See post 59:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226279/comments/59](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226279/comments/59)

---

### Post by Zoasterboy on 2008-06-19
Same problem here. Toshiba Satellite.

I made a similar post today, but from looking at this post it doesnt look like anyone knows the problem.

Sleep worked before, but now sleep and hibernate do not work, causing the computer to freeze when I try to turn it back on.

---

### Post by danwood76 on 2008-06-19
The version 2.6.24-19 kernel has the bug fixed.
You may need to enable the hardy proposed repository to get it, or just wait until it gets released into the main repos.

---

### Post by muguwmp67 on 2008-06-21
The problem still exists on my Dell laptop.  It worked fine in Gutsy, but no longer resumes properly.  I can ctrl-alt-backspace though and the display will restart properly.

---

### Post by lanzailan on 2008-06-22
[SIZE="4"][COLOR="DarkOrange"]sleep and never wake up.. :confused:
im having the same problem too.. [/COLOR][/SIZE]

---

### Post by danwood76 on 2008-06-22
Have you guys tried the -19 kernel in the proposed updates?
This has solved the issue for loads of people.

---

### Post by muguwmp67 on 2008-06-22
Kernel Version 2.6.24-19-generic here.

---

### Post by rnajera on 2008-06-22
> **danwood76 said:**
> Have you guys tried the -19 kernel in the proposed updates?
This has solved the issue for loads of people.

I have the problem with the -19 kernel. I have a HP Compaq nc6230 laptop and I'm not using any non-supported ATI drivers.

After trying to come back from suspend mode I get a blank screen.

```
 $uname -a
Linux rafael-laptop 2.6.24-19-generic #1 SMP Wed Jun 4 16:35:01 UTC 2008 i686 GNU/Linux

```

Regards,

Rafael.

---

### Post by lanzailan on 2008-06-23
> **muguwmp67 said:**
> Kernel Version 2.6.24-19-generic here.

[SIZE="4"][COLOR="DarkOrange"]how to apply.. :confused:[/COLOR][/SIZE]

---

### Post by muguwmp67 on 2008-06-23
Interesting, I switched the 'when laptop closed' setting to hibernate (which my laptop doesn't support) and it wakes up fine now.  

It is also interesting that I have to unlock the desktop when it wakes up, even though I have the 'lock screen when screensaver active' box checked.

---

### Post by shebuwa on 2008-06-24
This is by no means a complaint. :) 

I am sure the devel team will come up with a fix for this very soon, and I really wish I could be of some help with that. I thought, perhaps it may help though, if I reported my particular version of this problem.

My Dell Latitude C610, for the very first time ever, locked up after attempting to resume from suspend this evening. 

Oddly enough, there was no problem with this after the kernel update from 2.6.24-16 to 2.6.24-19, until just this evening, and I had opened the lid several times to see my session resume with no problem after the update.

Hope that is helpful.


PS

I love Ubuntu Hardy!

---

### Post by muguwmp67 on 2008-06-24
Mine's a C610 too.  I set the 'when lid closed' option in power management to Hibernate, and it seems to be working now.  For whatever reason, the "Blank Screen" option made it hang.  As an added bonus, my wifi card doesn't drop out when I close the lid anymore.

---

### Post by drjonze on 2008-06-24
Same issue, I also get in intermittently when my screen saver comes on (since turned it off).

Hardy 64 kernel 19
Acer Aspire 9300 AMD64

---

### Post by w00t951 on 2008-06-24
I have an ancient Dell Inspiron 2650 that won't wake up. I the screensaver works fine, but when the system truly sleeps, (no fan, hard drive, CPU, blinking power light) and I press the power button, the computer turns on, but nothing is on the screen. Just a black display that is powered on.

---

### Post by shebuwa on 2008-06-24
Glad to see mine isn't the only C610. I am still amazed to have a Linux distro up and running on it.

I finally got mine working again by going into System > Power Management, and switching all the suspend options to 'do nothing', and then back to suspend once again. I am guessing that just rewrites the code or something. :confused:

The only remaining annoyance now, is how the login panel hangs for a few seconds as it comes out of suspend, showing a whited out normal sized version of the login panel, before it then re-sizes to fill the entire screen with it.

I think my grub just needs to be edited. I am not knowledgeable enough to do that though.

---

### Post by shebuwa on 2008-06-28
Once again I have spoken too soon. I am on Xubuntu now, still Hardy 8.04 though, and now it freezes upon opening the lid. 

I am afraid to try the setting it to 'hibernate' fix mentioned by muguwmp. I have it set to 'do nothing' for now.

---

### Post by muguwmp67 on 2008-06-28
> **shebuwa said:**
> I am afraid to try the setting it to 'hibernate' fix mentioned by muguwmp. I have it set to 'do nothing' for now.

I don't know why it worked but it hasn't hurt anything on my 610.  Its only locked up twice so far after waking up, and I think that is because of a thrashing problem that's recently come up.  Having it reconnect my wireless card after it wakes is a huge bonus.

I'm still experiencing some strangeness though.  Even though I have the "lock screen" option off, I get the password screen after the laptop wakes, and usually have to reenter my wifi key.  That may be by design though.

I use Ubuntu instead of Xubuntu.  Its pretty easy to change power settings back and forth in Ubuntu.  If it's not that hard in Xubuntu, I can't imagine that it would hurt anything.

---

### Post by danwood76 on 2008-06-28
> **muguwmp67 said:**
> 
I'm still experiencing some strangeness though.  Even though I have the "lock screen" option off, I get the password screen after the laptop wakes, and usually have to reenter my wifi key.  That may be by design though.


This is not strange behavior it is supposed to do that for security reasons.
The lock screen option is only for the screen saver and doesn't effect the suspend/hibernate options.

---

### Post by Zoasterboy on 2008-07-01
> **lanzailan said:**
> [SIZE="4"][COLOR="DarkOrange"]how to apply.. :confused:[/COLOR][/SIZE]

It should come automatically in updates now.

---

### Post by thanos_pc on 2008-07-01
The same problem still with my acer aspire 5920g...with -16 kernel all wotked fine...after the kernel updates and now with the -19 when i close my laptop in order to suspend it wakes up with a blank screen and a flashing symbol..Hibarnate i thnik its working but suspend is importan for me..i hope at new kernel update at -20 the problem will stop to exist.

---

### Post by ar-jar on 2008-07-06
Hibernate works fine for me now (ever since the kernel was updated to 19 I suppose). But suspend still does't work. The graphics card won't even output a video signal when I turn on the machine after suspend. I'm running a four core AMD Phenom system.
-Arto

---

### Post by danwood76 on 2008-07-06
> **ar-jar said:**
> after suspend. I'm running a four core AMD Phenom system.

Unlucky. (with regards to the phenom)

What graphics card do you have?
There are some tweaks with the Nvidia cards that can help the suspend issue.

---

### Post by Avinash.Rao on 2008-07-07
Guys,

I installed Ubuntu8.0 on a ACER Aspire 3620 Laptop and both the suspend and hibernate options don't work! Does anyone have a solution for this?

Avinash

---

### Post by Avinash.Rao on 2008-07-08
Hello all,

I tried everything you all said but nothing happened. 
When i closely read the system log, i noticed that, the OS was probing the wireless adpater continuously. So, i installed the wireless adpater using the GUI tool and everything worked, both Suspend and Hibernate works!! 



> **Avinash.Rao said:**
> Guys,

I installed Ubuntu8.0 on a ACER Aspire 3620 Laptop and both the suspend and hibernate options don't work! Does anyone have a solution for this?

Avinash

---

### Post by Square on 2008-08-21
> **Avinash.Rao said:**
> So, i installed the wireless adpater using the GUI tool

Which GUI tool was that?

---

### Post by danwood76 on 2008-08-21
Most probably the hardware drivers GUI. (Used to be restricted drivers manager)

---

### Post by Square on 2008-08-21
Thanks,

my driver is installed via the hardware drivers GUI :(

As you can see from here [http://ubuntuforums.org/showthread.php?t=895588](http://ubuntuforums.org/showthread.php?t=895588) , I'm also having problems with suspend/hibernate.

Do you know if the problem has been sorted out for most of the cases in this thread?

Pierre

---

### Post by danwood76 on 2008-08-21
Most suspend issues were solved in version 19 of the ubutnu hardy kernel.
If you have all the updates installed and your suspend still doesnt work there are many things that can cause issues.

For example nvidia drivers used to give major issues with linux suspend and hibernate.

It could also be an issue with your computer not following the ACPI conventions properly.
There are no specific rules for motherboard manufacturers to follow just a set of guidelines which makes it hard for linux.
On top of that most laptop manufacturers write their ACPI to adhire to the windows standard which of course linux cannot run to.

What PC do you have?

---

### Post by Square on 2008-08-21
I'm using the 2.6.24-19-generic kernel (obtained via update-manger), with gnome and compiz-fusion on the desktop.

As far as hardware is concerned, I've got a Fujitsu-Siemens Amilo A1655g which has a Radeon Xpress 200M graphics card and Broadcom 4318 Wifi card with  a Turion64 processor.

As far as graphics drivers are concerned, at first I was using the propriety drivers available in the repos which didn't solve the problem. I then updated to the latest Catalyst drivers available directly from AMD/ATI which never solved the problem either.

I think I should also mention that my wireless didn't work out of the box which required me to install an additional module to get it working.

BTW, thanks for taking the time to try to help me with my problem

---

### Post by danwood76 on 2008-08-21
A quick google on your laptop reveals this page:
[http://docs.mht.bme.hu/~balazs/amilo/KubuntuonFSA1655G.html](http://docs.mht.bme.hu/~balazs/amilo/KubuntuonFSA1655G.html)

Although its for a very old version of ubuntu it does say that suspend does work so it _should_ work now.
He stated that he needed to add the boot options noapic and nolapic to get them working although the linux kernel has come a long was since 2005 so I doubt you need them.

The Graphics card you have in it (Xpress 200M) is the same as in my laptop and I was able to suspend with fglrx (ati proprietry driver) installed.

---

### Post by Square on 2008-08-21
Hmmm, I just tried booting with those parameters and I couldn't even make it to the login screen.

Would you happen to know which logs I should be checking out to help troubleshoot my problem?

Also, if you didn't see it in my other thread, the CPU fan doesn't turn off even though the computer is 'suspended' so perhaps that is another clue.

---

### Post by christofer on 2008-12-03
Well just set up a new system and look what decided to show its ugly face. The same lock screen issue that has been haunting this distro from the beginning of 8.04. My motherboard is a Gigabyte 945GCM-S2C with a onboard Intel GMA 950 graphics chipset. It started after applying the updates in the recommended updates. I don't mess with proposed unless i really have to. I noticed there is a new Intel driver in the proposed updates. But I don't trust it and don't need any extra work. 64 Bit 8.04. Anyone care to try???????????

---

### Post by christofer on 2008-12-03
bump

---

### Post by christofer on 2008-12-09
bump

---

### Post by christofer on 2008-12-11
bump!!!!!!!!!!!!!

---

### Post by danwood76 on 2008-12-12
Its an issue with the kernel.

Try the latest version of ubuntu (8.10) as this has a much later kernel which has a lot better suspend/hibernate support!

---

### Post by d4rk_rebel on 2008-12-13
I am using 8.10 and am having the same trouble.  I am using ATI HD 2600 pro

---

