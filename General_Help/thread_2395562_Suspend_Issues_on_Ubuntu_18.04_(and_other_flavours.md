---
title: "Suspend Issues on Ubuntu 18.04 (and other flavours) – Troubleshooting and Fixes"
date: 2018-07-03
forum: General Help
---

### Post by perryhelionsemail on 2018-07-03
I’ve experienced an issue with suspend on Ubuntu and Kubuntu 18.04, but the issue only occurs on one machine. 

Another three different machines I’ve tested had no suspend issues at all and I would have assumed that the fault was with my own crappy laptop, except that suspend was working fine on both Ubuntu and Kubuntu 17.10 and it also turns out that suspend works without issue on 18.04 when using a 4.14 kernel (more on that later).

Whilst searching the forums for a solution to my problem, it has become apparent that although suspend works fine for many people using 18.04 there are a few issues which look similar but have slightly different behaviours and different fixes.

**As a quick troubleshooting guide I have outlined a few steps to narrow down where the problem might lie and what might help resolve the issue.**

The first thing to check is that suspend actually works at all. It can appear that the machine is failing to resume after going to sleep, but in many cases the machine is failing to enter suspend properly in the first place.


**Manually Select Suspend**
[I]
You should be able to manually select suspend on any desktop but it's slightly hidden in Gnome Shell - you can either longpress the power button from the top right hand menu of the screen, or click that button whilst holding Alt or press the Super key and type in 'suspend'[/I]

If you manually select suspend you can check that the screen switches off and that the power LED is flashing. Any fan that may be spinning should also switch off.

In my case, the screen would switch off but the power LED stayed on and the fan would continue to run if already doing so. The machine did not respond to any keypresses or mouse movements or pressing the power button (which would normally ‘resume’).

The usual tricks of Ctrl + Alt + f1 or f2, f3 etc had no effect. The only thing that could be done was to force the machine to shutdown by holding down the power button.

In order to provide consistent language to describe the problem, I’m going to call this ‘seizing up and requiring a forced shutdown’.


**Nvidia Graphics**

I don’t have nVidia graphics on my machine, but for some people experiencing suspend issues who do, there is a fix that has reportedly resolved the issue for a number of people.

It’s outlined here by cascagrossa: 

[https://askubuntu.com/questions/1029405/ubuntu-18-04-crashes-on-resuming-from-suspend/1041395#1041395](https://askubuntu.com/questions/1029405/ubuntu-18-04-crashes-on-resuming-from-suspend/1041395#1041395)

and basically involves adding the kernel parameter ‘nouveau.modeset=0’ in /etc/default/grub

The assumption is that you are using the open source ‘nouveau’ graphics driver [I](if you are experiencing suspend problems whilst using the proprietary nVidia graphics drivers then it’s worth trying nouveau instead just to be sure the fault isn’t with the proprietary drivers)
[/I]
For those who are unfamiliar with Linux, you want to open up a terminal and use ```
sudo nano etc/default/grub
``` to change the line 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to be 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nouveau.modeset=0"

*(press Ctrl + x to exit, press ‘y’ to agree to save the changes and press 'enter' to accept the filename)*

and then run ```
sudo update-grub
``` and reboot the machine.


**s2idle**

There has also been a problem with the machine not going into ‘deep’ sleep, but instead going into an ‘s2idle’ mode instead. 

It’s easy to check, just type

```
cat /sys/power/mem_sleep
``` 

and you should see the default suspend mode with [square brackets] around it. 

For the ‘normal’ suspend mode that most users expect, cat /sys/power/mem_sleep should return something like:

s2idle [deep] 

If you have [s2idle] in the square brackets then s2idle is currently the default suspend mode. 

The fix for that has been helpfully described here by monty47:

[https://askubuntu.com/questions/1029474/ubuntu-18-04-dell-xps13-9370-no-longer-suspends-on-lid-close/1036122#1036122](https://askubuntu.com/questions/1029474/ubuntu-18-04-dell-xps13-9370-no-longer-suspends-on-lid-close/1036122#1036122)

[B]
Try An Older Kernel[/B]

I was unaware of a rather handy program called UKUU until I stumbled across a solution helpfully outlined by matalak here:

[https://askubuntu.com/questions/1029405/ubuntu-18-04-crashes-on-resuming-from-suspend/1038528#1038528](https://askubuntu.com/questions/1029405/ubuntu-18-04-crashes-on-resuming-from-suspend/1038528#1038528)

It involves installing the Ubuntu Kernel Update Utility by following the steps from omgubuntu.co.uk:

[https://www.omgubuntu.co.uk/2017/02/ukuu-easy-way-to-install-mainline-kernel-ubuntu](https://www.omgubuntu.co.uk/2017/02/ukuu-easy-way-to-install-mainline-kernel-ubuntu)

and then choosing any kernel from the 4.14 branch. 

I chose the most up-to-date 4.14 kernel, mainly to see if the problem only turned up in the 4.15 branch, which it appears at least for my machine, that it did.

Under ‘Advanced options for Ubuntu’ in the grub menu you can then choose which kernel to boot into.

Using this method I was able to see that using 18.04 with a kernel from the 4.14 branch allowed suspend to work again without issue.


**Bug Report**

I have opened a bug report about my particular suspend issue and a few others have been afflicted with the same problem. I’ve not opened a bug report before, but I assume that the developers are busy and need to focus their time and energy on specific issues.

I was concerned that because the bug was only able to be reproduced on specific hardware combinations that it might not get any attention. I attempted to point people from AskUbuntu towards the bug report if the nVidia nouveau modeset trick didn’t help and the s2idle fix wasn’t at the root of their suspend problems.

That being said, whenever anyone added their voice to the bug report, I tried to show some appreciation that they’d taken the time to report it and also to confirm that the behaviour was a consistent failure to suspend, with the screen going blank, the power LED staying on and leaving an unresponsive machine that required a forced reset.

[I]Unfortunately, this may have had a detrimental effect on the bug report, filling it up with discussion rather than a developer being able to look through and quickly see what the issue was.
[/I]
I’ve not been told off for not keeping it succinct, and initially I thought it was important to put as much detail into describing the issue as possible, but looking at the bug report it has occurred to me that there’s quite a lot to read through, which might not be helpful to the busy developers.

Fortunately, despite not affecting a large number of users, one of the Canonical developers, Kai-Heng Feng, contacted the kernel team who applied a patch and he then posted the patched 4.15 kernel to test. 

It’s in post #35 of the bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1774950/comments/35](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1774950/comments/35)

The patched kernel has resolved my suspend issue and will hopefully be added into the upstream code, but for now I just have to make sure I don’t update the kernel when any updates are available.  

[B]
Suspend Issues In 18.04 In General[/B]

I’d like to attempt to move the discussion away from the bug report and into this thread, so that anyone experiencing a similar issue can check for other fixes, discuss their findings and, if the problem seems to be a kernel issue too, can report their problem succinctly to the developers.

‘Suspend Issues In 18.04 In General’ is too large a topic to be helpful in a bug report, but should be a good place in the forums to gather all the issues and then be able to report them individually. 

It was only by searching for a solution to my own problem that I became aware of a number of separate issues that had similar looking behaviour, so hopefully a bit of further discussion of people’s suspend issues will bring to light any other issues and help narrow down where things might be going wrong.

---

### Post by cmeerw on 2018-07-04
BTW, how do I find out what patch was actually applied in the kernel posted by [COLOR=#000000]Kai-Heng Feng (as the download is only for the binaries)?
[/COLOR]

---

### Post by perryhelionsemail on 2018-07-04
Hi cmeerw, not sure if this gives you the answer or if it's still a bit cryptic, but a few of the developer correspondances showed up as an email thread in my inbox (probably because my address was on the bug report) and it said:

[B]It is reported that commit a192aa923b66a (ACPI / LPSS: Consolidate runtime PM and system sleep handling) introduced a system suspend regression on some machines, but the only functional change made by it was to cause the PM quirks in the LPSS to also be used during system suspend and resume.  

While that should always work for suspend-to-idle, it turns out to be problematic for S3 (suspend-to-RAM).

To address that issue restore the previous S3 suspend and resume behavior of the LPSS to avoid applying PM quirks then.
[/B]

The commit a192aa923b66a seems to be in linux-pm/drivers/acpi/acpi_lpss.c which I assume is up somewhere on the kernel.org site if you need more information, but it would certainly appear that that's where the patch was applied.

The result of the original kernel bisection between 4.14 and 4.15 is up on the bug report but it said:

a192aa923b66a435aae56983c4912ee150bc9b32 is the first bad commit
ACPI / LPSS: Consolidate runtime PM and system sleep handling

Kindest regards,
pHeLiOn

---

### Post by ariake on 2018-08-04
By the way, the Ubuntu 18.04 based Linux distributions are, of course, also affected by this 'bug'. The all new Linux Mint 19, is experiencing the same problem.
It also seems that the patched kernel done by Kai-Heng Feng is a revoked version because of some serious issues.

What's the plan to fix the bug? Will the fix made by Kai-Heng Feng will be merged to a newer version?

---

### Post by perryhelionsemail on 2018-08-06
Hi ariake, as far as I can tell from the bug report ([**Bug #1774950**]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1774950")) the fix has been committed to the Cosmic Cuttlefish branch. 

Cosmic Cuttlefish (Ubuntu 18.10) looks likely to be using a 4.18 or greater kernel, so the patch that currently fixes the suspend problem on our affected machines will be implemented in whichever kernel 18.10 will be using.

I would like to think that the fix will be backported to the 4.15 kernel, but I'm not entirely sure how it works - because 18.04 is a Long Term Support release they will probably stick with a 4.15 kernel until a later point release. I don't know if they will add the fix to the 4.15 kernel in an update or whether we will have to wait until they move the LTS to a later kernel.

In the bug report, Jacob Pedersen said that when the latest kernel update came through in the repos (kernel 4.15.0-29) that suspend started working for him again on his machine. I was pleased to hear this news but my problematic HP Pavilion (with an Intel 'Pentium' N3540) still seized up and required a hard reset.

For just now, I'm just keeping the patched 4.15 kernel that Kai-Heng Feng put together and avoiding any kernel updates. When I get a bit more time I might experiment with some of the more recent kernels using the Ubuntu Kernel Update Utility (details in the 'Try An Older Kernel' section in my first post but the UKUU details are from [here]("https://www.omgubuntu.co.uk/2017/02/ukuu-easy-way-to-install-mainline-kernel-ubuntu")). Some of the more recent kernels might have the patch applied already - I haven't tried any of them recently but they are up to 4.17.12 so far, so might be worth a look if you are curious.

I'm glad we've managed to get the bug looked into - the issue seems to be affecting quite a small number of specific machines - but I suspect we will have to either wait it out on the patched kernel or experiment with UKUU to find a more recent 'suspend friendly' kernel for the affected machines for now.

Kindest regards,
pHeLiOn

---

### Post by perryhelionsemail on 2018-08-12
@yeboster - this is just a quick note after seeing your post on the bug report. It seems likely that the bug outlined in [**Bug #1774950**]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1774950?comments=all") is mainly affecting Bay Trail Atom Celeron/Pentium Cpu's. 

There are other suspend issues with 18.04 however, so it would be best to see if it might be an s2idle problem or the nVidia drivers that are causing suspend to fail first. Take a look at the first post in this thread and see if any of the solutions that worked for others help fix your suspend problems.

*If the suspend issue is with the nVidia proprietary drivers then the only people who can help there are the nVidia developers because the closed-source graphics driver model means that noone else is able to check the code, make modifications or fix any issues.*

The nouveau graphics driver (the open source nVidia graphics driver) unfortunately seems to have had a bug in the driver code which has caused suspend to 'misbehave' on 18.04. I don't know if a fix has been issued for it yet, but if you are experiencing suspend problems with 18.04 it's definitely worth checking whether the *nouveau.modeset=0* trick fixes it, because in that case you know it's a problem with the nVidia graphics rather than needing a patched kernel.

Let us know how you get on - it's not absolutely definite that only Bay Trail Atom Celeron/Pentium CPU's are affected, but it seems quite likely from the evidence so far - it would be useful to know what machine you are using, if trying to enter suspend causes the same 'seizing up and requiring a forced shutdown' behaviour and whether the nVidia nouveau or s2idle 'fixes' resolve your suspend issues.

---

### Post by perryhelionsemail on 2018-08-12
@smustgrave and @ariake,

If you have come here from the message in the bug report then it'd be really helpful to let us know here how you get on with checking whether the XPS has the same issue as those with a Bay Trail Atom Celeron/Pentium. 

As mentioned, whilst searching on AskUbuntu and trying to find out what was wrong with my machine, I saw some issues with nVidia graphics and s2idle problems that exhibited the same behaviour as my machine but were not the cause of my suspend problems - my machine has only Intel Graphics and cat /sys/power/mem_sleep showed that it was trying to enter [deep] sleep by default rather than s2idle (I still followed the solution just in case, but to no avail) - the first post in this thread points at some of the AskUbuntu questions and solutions that helped fix it for others.

The s2idle problem was from an AskUbuntu question about a Dell XPS and I think most of the recent XPS laptops have nVidia graphics as well. There's a reasonable likelihood that those issues are giving you suspend problems and that you don't require a patched kernel to get suspend to work on your machines.

---

### Post by yeboster on 2018-08-13
Thank you for your reply!
I have an HP pavilion 15 (Intel i7- 6700HQ) with installed last 390 non free nvidia driver.
Sometimes the machine goes to suspend well, sometimes when I boot it up again, the gnome restarts and the session is recreated twice (I need to log in twice).
I've putted into the grub the nomode_set and I saw an improvement: before it was not working and now sometimes it works. The mem_sleep is [deep]
So I'm not sure what is the cause but I think I need to try the free driver.
I have a question: When I install the free driver, do I need to remove the modeset line? Basically what that line does? It blacklist the nouveau driver? 
Also, why the free driver is the nouveau?
Sorry for too many questions but I've never covered this stuff in my new experience with Linux.

---

### Post by perryhelionsemail on 2018-08-13
@yeboster - hello, firstly it would be best for me to point out that I have not really had any experience using nVidia graphics. Whilst investigating what was going wrong with my machine when I tried to suspend, I searched on the AskUbuntu questions and saw several mentions of the **nouveau.modeset=0** trick that helped out people with nVidia graphics experiencing problems.

The feedback from other users was that it solved a couple of problems on 18.04. There was even someone who couldn't get the live USB to boot but was able to by adding nouveau.modeset=0 to grub. Initially I thought it was just changing a setting on the nouveau driver, but as far as I can tell it is just disabling the nouveau driver on boot and stopping it from interfering with the proprietary drivers.

There is a way to remove the proprietary drivers and (assuming you also remove nouveau.modeset=0 from /etc/default/grub) it will fall back to using the nouveau drivers, but it might not be necessary to do that in order to get suspend to function correctly on your machine.

I'd recommend taking a look at this AskUbuntu question about nVidia graphics drivers: [https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers](https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers)

As far as I can tell, if you add the ppa using:

sudo add-apt-repository ppa:graphics-drivers/ppa

and update your system with **sudo apt update** and **sudo apt upgrade** then it will update your proprietary nVidia graphics drivers to the latest versions. With a bit of luck, any suspend issues will have been fixed by now in the most up-to-date versions of the drivers. 

The 'nouveau.modeset=0' parameter is probably still required to ensure that the nouveau drivers don't interfere, but hopefully you should be able to suspend and resume without further issues.

It would be interesting to know how you get on - the particular suspend issue I'm experiencing on my machine (without the patched kernel) looks very similar to people with s2idle and nVidia driver problems, so if anyone else joins the bug report about suspend issues it'll be good to know what has worked (or not worked) for nVidia users experiencing a similar looking problem.

---

### Post by perryhelionsemail on 2018-08-15
**Kernel 4.17.14**

Using 'Ubuntu Kernel Update Utility' ([an easy way to try out other kernels]("https://www.omgubuntu.co.uk/2017/02/ukuu-easy-way-to-install-mainline-kernel-ubuntu")) I have tried the most recent 4.17.14 kernel and suspend and hibernate both work fine on Kubuntu 18.04 so far.

I haven't tried 4.18 yet - it's available but might be a bit too 'bleeding edge' at the moment - I assume that the same patch that fixes the suspend issues is already in 4.18.

I'll keep running my machine with 4.17.14 and look out for any further odd behaviour, but it'll be nice not to keep having to make sure I don't accidentally update the 4.15 kernel and break suspend again :)

---

### Post by perryhelionsemail on 2018-08-27
**Kernel 4.18**

Have been running Ubuntu and Kubuntu with kernel 4.18.3 over the past week or so and suspend has been working fine. I don't tend to use hibernate but gave it a quick test and it seems to be working without issue too. Haven't been doing anything particularly complicated with the machine but everything has been running well. I'd recommend a recent(ish) 4.17 or 4.18 kernel for anyone who's been having the same suspend issues as described in the first post on this thread.

---

### Post by perryhelionsemail on 2018-08-29
**Update from Bug Report ([Bug #1774950]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1774950"))**

A proposed update in 4.15 (kernel 4.15.0-34) has been tested and confirmed as fixing the main Suspend issue (where attempting to Suspend causes the system to seize up and require a forced shutdown) for a number of machines.

The proposed update should be available as a standard update to everyone on 18.04 soon (don't know how long that normally takes but probably something like a week or so).

[I]Anyone still experiencing suspend issues is welcome to post here for further discussion. I'll try and check the post regularlyish.
[/I]
Bug #1774950 should be closed and marked as 'fixed' in the coming weeks, so if you are still experiencing suspend issues after the update to kernel 4.15.0-34 then it is likely that a different bug is affecting your machine.

---

### Post by leopd on 2018-09-08
I've kept my 16.04 lts consistently updated and chose to upgrade today to 18.04 lts. I followed instructions within 16.04 and was still able to use the computer until it was ready to reboot with 18.04 lts. I was hoping this would work rather than a fresh installation since I wish to keep my files and folders. 

After passing the BIOS I had my usual choices of *Ubuntu, Advanced Options and Win 10 (It is a dual boot set up machine).   Then white writing on black:
2 ACPI errors [CAPD] and another

The dark purple/black screen appeared with 18.04 and the dots. Then came flashing a message, that...Gave up waiting for suspended/ resume d ervice:  /dev/sdc1: clean, 467342/16580608 files, 10722236/66302208 blocks

There is nothing further, it stops flashing. So I switched off and tried Advanced options

Using the advanced option 4.1.15 0-30 (recovery mode), it failed,everything ok'd i chose then a normal boot, again all ok'd, except  [FAILED] Failed to start Samba NMB Daemon. See 'systemc1 status nmdb.service' for details.  Further down says  [OK] started  Samba SMB Daemon. And the PC remains in this mode unbooted at the last entry [OK] Started Update UTMP about system Runlevel 
Changes


What can I do other than do a fresh install from a DVD?

---

### Post by perryhelionsemail on 2018-09-08
Hi leopd - sorry to hear you're experiencing these issues and can't get the system to boot.

I'm afraid I have very little experience of successfully  fixing a problematic full upgrade to another Ubuntu version. Any issues I  encountered were generally less severe but usually annoying enough  for me to end up just making a fresh install a few weeks or a month or  so later.

I do usually get ACPI errors or warnings flashing up on  boot on a couple machines - *I'm sure I've read somewhere that these have started showing up  since 16.04 because the reporting of them has changed so they are more  visible now* - but I don't think they're anything particularly to worry  about. They haven't seemed to noticably affect the running of the  machines they showed up on, anyway.

My best guess is that something is going wrong with  the Samba client (a program that I am entirely unfamiliar with) so might  be worth asking a question on **Ask Ubuntu **about being unable to boot after upgrading to 18.04 - hopefully you'll find someone who  knows more what they are talking about than I do.

The simplest way is, unfortunately, a fresh install *(If  you haven't backed up your files then a Live USB should have full  access to your filesystem so you can copy them somewhere safely)* but if you're going to do that then it's also worth trying a few of the options first from the '***Advance options for Ubuntu***' and (***recovery mode***) where you can attempt to '**Repair broken packages**' or '**Drop to root shell prompt**' and see if there's any clues in the **/var/log** folder. 

If you use ```
less /var/log/boot.log
``` you can use **Page Up**, **Page Down**, **Home** and **End** to look through the many lines of text more easily. There should be a few better clues in there and in the same manner you can also see if syslog or kern.log have anything useful too.

It's also a good way of collecting some possibly useful information if you do ask a question on Ask Ubuntu, although a Live USB might be easier to access the log files from and save them somewhere useful so you can cut and paste them into your question if needed.

** So yeah, sorry I'm not much help but I'd recommend checking on Ask Ubuntu or asking your own '*Upgraded from 16.04 to 18.04 and now Unable to Boot Properly*' question [B](someone may already have asked something similar and there might be a fairly straightforward fix) **and also checking if any '(recovery mode)' options like 'Repair broken packages' have any effect on the non-bootable situation.[/B]

---

### Post by perryhelionsemail on 2018-09-08
@[**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=488462")leopd - a quick look on Ask Ubuntu shows a couple of questions about 16.04 to 18.04 upgrades with booting issues. 

One quick temporary fix that worked for someone else was to boot using their old kernel (4.4 I think) that was still there in the Grub menu's 'Advanced options for Ubuntu'. You may already have tried this or if you updated to the HWE (HardWare Enablement kernel) to get a more recent kernel then this may not be relevant, but thought it might be worth mentioning.

---

### Post by leopd on 2018-09-09
Thank you @perryhelionsemail, I really appreciate the thought and time you have put into answering

---

### Post by Hasimir on 2018-10-08
Hi @perryhelionsemail, thanks for this thread!

I have suspend problems I'm failing to solve >_<
Here are some info on my system:
Asus ZenBook UX310UQ
Intel Graphics + nVidia GeForce 940mx
Ubuntu 18.04
Kernel 4.18.12
nVidia drivers 396.54 (the latest)

I have no suspend problem using the Nouveau drivers. But the moment I switch to the proprietary nVidia ones the problem appears, both on the latest 396 and the older/long-term 390.
I have checked the s2idle status, and it says [deep].
I have added the nouveau.modeset=0 element to grub.
This problem was present since I first installed Ubuntu on my machine, 2 years ago... no kernel ever fixed it. Only using the open drivers made the problem go away.
I've also put into action [these other fixes]("https://devtalk.nvidia.com/default/topic/969433/-quot-solved-quot-suspend-resuming-and-wakeup-with-nvidia370-28/"), but to no avail (and later on mor epeople report the solution not working on Ubuntu 18.04 specifically).

Someone seems to have patched the issue with [this solution]("https://lists.freedesktop.org/archives/nouveau/2018-August/030954.html") but HOW to do it is not clear. Maybe someone here knows how to help? :)

---

### Post by Azeroth on 2018-10-09
I have suspend issues as well, to me, they are not worthy of a new thread.

I have an old Samsung np530u3c (core i5 3317U, 8gb ram, Intel HD 4000 graphics) with Xubuntu 18.04 installed. The only way I can suspend is with the power menu. Either closingthe lid nor automatic suspend after X minutes idle work and I don't know where to look

---

### Post by perryhelionsemail on 2018-10-24
Hi Hasimir - it'd probably be best for me to mention that I have no experience of using nVidia graphics on any of my machines, so any suggestions I make are just from some of the things I have read and may not be all that helpful.

I was fascinated to read that the open source Nouveau drivers are actually made by reverse engineering the proprietary nVidia drivers: [https://en.wikipedia.org/wiki/Nouveau_(software)](https://en.wikipedia.org/wiki/Nouveau_(software)). All perfectly legally, but a pain in the bahooky for the developers. 

I'm sure they're very good at it by now, some of them may even enjoy the challenge to puzzle it out but it still impresses me that the Nouveau drivers work decently, given the distinct lack of help and documentation from nVidia.

The proprietary nVidia drivers, on the other hand, should offer better performance *(since the developers making them have access to all the documentation about the graphics chipsets they are writing the drivers for)* but whilst investigating my own suspend issues it did appear that a number of nVidia users were encountering bugs whilst using the proprietary drivers.

The '**Nouveau Modeset Trick**' of adding the kernel parameter **nouveau.modeset=0** in the **/etc/default/grub** file is something that I saw crop up a number of times. Many comments indicated that it fixed the issue for them but my understanding of how it worked was quite vague.

My understanding of it is still quite vague but this article from the nVidia website has helped a bit: 
[https://us.download.nvidia.com/XFree86/Linux-x86/375.26/README/commonproblems.html#nouveau](https://us.download.nvidia.com/XFree86/Linux-x86/375.26/README/commonproblems.html#nouveau)

> **8.1. Interaction with the Nouveau Driver**    

What is Nouveau, and why do I need to disable it?    

Nouveau is a display driver for NVIDIA GPUs, developed as an open-source project through reverse-engineering of the NVIDIA driver. It ships with many current Linux distributions as the default display driver for NVIDIA hardware. It is not developed or supported by NVIDIA, and is not related to the NVIDIA driver, other than the fact that both Nouveau and the NVIDIA driver are capable of driving NVIDIA GPUs. Only one driver can control a GPU at a time, so if a GPU is being driven by the Nouveau driver, Nouveau must be disabled before installing the NVIDIA driver.

Nouveau performs modesets in the kernel. This can make disabling Nouveau difficult, as the kernel modeset is used to display a framebuffer console, which means that Nouveau will be in use even if X is not running. As long as Nouveau is in use, its kernel module cannot be unloaded, which will prevent the NVIDIA kernel module from loading. It is therefore important to make sure that Nouveau's kernel modesetting is disabled before installing the NVIDIA driver.
    
I'm not sure how up to date the article is, so things may have changed more recently, but having no experience of nVidia graphics I just assumed that you could install Ubuntu and it would let you choose which graphics driver you wanted to use and work fine with either.

The article suggests that you need to ensure that nouveau is disabled in order to use the proprietary graphics and that it requires a little bit of fiddling in order to get it to work. 

The article goes on to explain how to blacklist the nouveau driver, so it would be interesting to know if you have already implemented these changes when trying to use the proprietary drivers. 

I'm not sure if this will have any effect on the suspend issues that you've been experiencing, but it's worth checking even if it's just to confirm that it doesn't fix the problem.

kindest regards,
pHeLiOn


-- It's worth reading the nVidia article, but here's a summary:

With the nVidia Proprietary Graphics Drivers installed on your machine, create a new file in the **/etc/modprobe.d** folder. 

(The actual name of the file isn't important as long as it ends with **.conf** but they offer a suggestion of **disable-nouveau.conf** )

The file only needs to contain the two lines:

```
blacklist nouveau
options nouveau modeset=0
```


Once your **/etc/modprobe.d/disable-nouveau.conf** file has been created and saved you need to run:

```
sudo update-initramfs -u
```

(so that initramfs is updated with your new module blacklist file included) and then **reboot** your machine.

[I]With nouveau now blacklisted we can feel pretty confident that it's not to blame for any further issues that you may encounter.
[/I]

--Also, this is another guide that does the same thing in a slightly different way: 

[https://linuxconfig.org/how-to-disable-nouveau-nvidia-driver-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-disable-nouveau-nvidia-driver-on-ubuntu-18-04-bionic-beaver-linux)

---

### Post by Hasimir on 2018-10-25
It effing WORKS!
Thanks you @[perryhelionsemail]("https://ubuntuforums.org/member.php?u=2100258") !

Using the latest 396 nVidia drivers I'm noticing the system is a tad slower when booting up, and there is a weird visual artefact on the top-left corner when shutting down.
But other than that, the suspent/resume now works!

Again, thank you :D

---

### Post by perryhelionsemail on 2018-10-25
That's great news! Glad it seems to have fixed the suspend issue for you Hasimir - that would suggest that in some cases the nouveau driver being present (and not blacklisted) might interfere with the suspend/resume function when using the nVidia proprietary drivers. That's good to know and looks like it'll be a useful suggestion for anyone else experiencing similar problems :)

---

### Post by perryhelionsemail on 2018-10-25
Hi Azeroth - I've been having a look around the forums to see if anyone else has been experiencing similar issues with xfce or xubuntu and it might have something to do with the **logind.conf** file that's in the **/etc/systemd** folder. 

This is possibly an older issue that has since been resolved, so I'm not sure if I'm on the right track here, but it's worth taking a look at the **/etc/systemd/logind.conf** file and see what the various options are set as.

From a few of the threads and bug reports I've read, it seems that some xfce users were choosing '*what happens when the lid closes*' options without them having any effect because the **xfce4-power-manager** settings were being ignored in favour of whatever **systemd** had been set to do.

I'm thinking that from your post that is also what you are experiencing: you are choosing options like '*suspend when lid closes*' and '*after X minutes suspend machine*' but then these settings are subsequently ignored? 

If so, it might be worth checking whether your **logind.conf** file has **HandleLidSwitch=suspend** as one of the options and whether changing that to **HandleLidSwitch=ignore **results in the correct behaviour according to your xfce power settings.

I'm guessing a little at this but it should be quite straightforward to change it, reboot and see if it makes any difference and if not, quite easy to change back again. 
[I]
(Of course, this doesn't help with the 'not suspending after idle for X minutes' issue but it'll be useful to know if it's somehow related to this older 'power-manager/systemd conflict')[/I]

kindest regards,
pHeLiOn

---

### Post by jgcfc on 2018-12-01
I had this issues with the lxde and xfce flavors, the solution to suspension work correctly is copy and paste this line bellow on terminal 
xfconf-query -c xfce4-power-manager -p /xfce4-power-manager/inactivity-sleep-mode-on-battery -n -t int -s 1
and reboot the system.
Miss one line to it work correctly. I don't know the why the developers forget a simple line. Please report it for ubuntu!!!
I have issues with suspension with no solution on mate and budgie flavour. Please help me ubuntu team.
Ubuntu can't loose your reputation with suspension and hibernation issues. I don't want to use windows anymore but this issues they need to give more attention. I have fear with the ubuntu damage my laptop battery if the shutdown dont work when the battery is in a critical level. &#128555;
My favorite ubuntu flavour is budgie.

Thank you.

---

### Post by rasutt on 2018-12-16
Hi Perry,  Excellent post thanks.  My new gigabyte aero laptop has an NVIDIA gtx 1070 and the screen has been freezing whenever I close the lid without powering off.  This continued despite setting nouveau.modeset=0 as the default boot option in grub.  I added the ppa you suggested and updated and upgraded, and rebooted, and now it suspends and awakes perfectly.  I am also still using the 4.15.0 kernel by the way, and I don't want to upgrade because I want to install CUDA for deep learning...  Anyway thanks a lot!

---

### Post by chandap on 2018-12-18
> **rasutt said:**
> Hi Perry,  Excellent post thanks.  My new gigabyte aero laptop has an NVIDIA gtx 1070 and the screen has been freezing whenever I close the lid without powering off.  This continued despite setting nouveau.modeset=0 as the default boot option in grub.  I added the ppa you suggested and updated and upgraded, and rebooted, and now it suspends and awakes perfectly.  I am also still using the 4.15.0 kernel by the way, and I don't want to upgrade because I want to install CUDA for deep learning...  Anyway thanks a lot!

Hi,
New to ubuntu. I am having the suspend/wakeup problem with my Dell XPS-15-9570, removed windows 10 and installed ubuntu 18.04.01 LTS.
Installed nvidia driver 410 for my nvidia card (GeForce GTX 1050 Ti Mobile) as suggested by nvidia. Reboot happens fine, but when I suspend the machine, and try to wake it up, I get a blank screen with the cursor on the top left corner, and nothing happens after that. 


Tried setting : GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force" GRUB_CMDLINE_LINUX="noveau.blacklist=1 nouveau.modeset=0"


nothing seems to work. 

Seems you have the same issue and solved it, can you tell me the steps ? 
Any help highly appreciated 

-Pritam

---

### Post by gh0zt362 on 2018-12-22
Brand new HP 17byxxxx laptop using intel UHD 620 integrated graphics having a similar issue . upon wake from suspend the screen comes on for just a moment ( black screen with cursor ) then goes black black as in screen off . my only option then is to tap the power button to initiate auto shutdown  and the screen comes back on just so I can see the Ubuntu Studio logo before it shuts down . 

Ubuntu studio 18.10 4.18.0-13-lowlatency

---

### Post by gh0zt362 on 2018-12-31
Great news !  For those having the problem where you are experiencing a black screen upon suspend wake I found a solution for atleast my problem .  This solution pertains to Ubuntu Studio 18.10 xfce  , Kernel version 4.18.0-13 low latency  

Scenario : Hit suspend button , system spins down goes into suspend . Either touch mousepad or tap mouse button . Systemp spins up to black screen with cursor then screen powers down and doesn't come back . harddrive light on , laptop is powered up fan is running with a completely shut down screen , No buttons or other actions able to wake screen despite system running .  Only option to shut down and restart . 

 Solution : install power manager plugin button to panel if it isn't there already ( icon is a battery by default ) / right click power manager plugin and select properties / left click security tab /  change " automatically lock session after " to never  and then what solved the issue for me was under delay locking after screen saver slider UNCHECK lock screen after system is going for sleep . 

Unchecking the lock screen upon sleep was the fix . 

I am now freely able to suspend system and then use either mouse pad or click mouse buttons and system as well as screen awakes as it should and all systems resume . 

Also in general tab under power manager plugin as well when lid closed change from lock screen to suspend  either on battery or both battery and  plugged  in  to prevent the system from locking your screen . 

Hope this helps you folks having suspend issue !

---

### Post by softrabbit on 2019-06-05
As I have describe [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1774950/comments/92"), suspend did not work since kernel 3.16.57/3.17 on my Acer ES-512. A guy on ubuntuforum had found out that the problem disappeared when xHCI (external USB3.O controller) was turned off in the BIOS. The suspend problem also disappeared on my wife's laptop (another Acer Aspire).

Someone that is knowledgable about suspend, USB3.0 and changes after kernel 3.17 is perhaps able to figure out how to fix this bug.

---

### Post by jis on 2019-07-15
gh0zt362 , it seems like this [bug]("https://bugs.launchpad.net/ubuntu/+source/light-locker/+bug/1832960"), which has several workarounds.

---

### Post by Pepe Lebuntu on 2019-08-05
So, this is driving me insane. I have a Dell Inspiron 13 [FONT=Arial][SIZE=2]5378. I had it working fine until I needed to upgrade the RAM and harddrive after the year's warranty ran out. Nine times out of ten, when I wake it up from suspend, the keyboard just does not work. It is SOOOO frustrating. I can't figure out if it's the NVIDIA thing - I'm still not sure if I even have an NVIDIA driver in this computer. I usually think I can deal with most techie issues even as a non-techie, but I'm at my wit's end.[/SIZE][/FONT]

---

### Post by MrKimi on 2019-08-17
My wife's laptop is failing to suspend since the last few days. There was an update over that time I think.
Her machine is running Lubuntu 18.04

```
Linux Lucia 4.15.0-58-generic #64~16.04.1-Ubuntu SMP Wed Aug 7 14:10:35 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
```

It is not running Nvidia, ```
glxinfo|egrep "OpenGL vendor|OpenGL renderer*"
``` gives 

```
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Haswell Mobile
```

When she picks 'suspend' from the shutdown menu it seems to suspend but then it bounces back up again.
There's an error that flashes on the screen referring to usb2 and when I did 'cat /var/log/syslog | grep PM:'''''
I get:

```
Aug 18 13:25:04 Lucia kernel: [189999.295342] PM: suspend entry (deep)
Aug 18 13:25:09 Lucia kernel: [189999.295345] PM: Syncing filesystems ... done.
Aug 18 13:25:09 Lucia kernel: [189999.787357] PM: Device usb2 failed to suspend async: error -16
Aug 18 13:25:09 Lucia kernel: [190004.405709] PM: Some devices failed to suspend, or early wake event detected
Aug 18 13:25:09 Lucia kernel: [190004.406492] PM: Device hdaudioC0D0 failed to resume async: error -16
Aug 18 13:25:09 Lucia kernel: [190004.563056] PM: suspend exit
Aug 18 13:25:09 Lucia kernel: [190004.563109] PM: suspend entry (s2idle)
Aug 18 13:25:09 Lucia kernel: [190004.563110] PM: Syncing filesystems ...
Aug 18 13:25:14 Lucia kernel: [190008.565065] PM: Device usb2 failed to suspend async: error -16
Aug 18 13:25:14 Lucia kernel: [190009.356270] PM: Some devices failed to suspend, or early wake event detected
Aug 18 13:25:14 Lucia kernel: [190009.356885] PM: Device hdaudioC0D0 failed to resume async: error -16
Aug 18 13:25:14 Lucia kernel: [190009.501917] PM: suspend exit
```

Which looks like I have a couple of devices playing up and waking the machine from suspend. I tried disabling the wake from the relevant usb port using:
```

sudo echo disabled > 2-3.41/power/wakeup
```
but it gives me permission denied.

I was getting hopeful about trying a different kernel but [https://ubuntuforums.org/showthread.php?t=2395562&p=13796073#post13796073](https://ubuntuforums.org/showthread.php?t=2395562&p=13796073#post13796073) refers to kernel 4.15.0-34 being a solution to this kind of problem and I am on 4.15.0-58.

Her machine is an HP Elitebook 850 CPU: i5 Memory: 8G 

I run Xubuntu 18.04 on a Toshiba, same kernel version and same updates, with no problems. So I figure this is hardware specific, probably related to the USB thing.

Does anyone know how I can diagnose this further? Thanks for any help.

---

### Post by mlnease on 2020-06-25
> **perryhelionsemail said:**
> @yeboster - hello, firstly it would be best for me to point out that I have not really had any experience using nVidia graphics. Whilst investigating what was going wrong with my machine when I tried to suspend, I searched on the AskUbuntu questions and saw several mentions of the **nouveau.modeset=0** trick that helped out people with nVidia graphics experiencing problems.

The feedback from other users was that it solved a couple of problems on 18.04. There was even someone who couldn't get the live USB to boot but was able to by adding nouveau.modeset=0 to grub. Initially I thought it was just changing a setting on the nouveau driver, but as far as I can tell it is just disabling the nouveau driver on boot and stopping it from interfering with the proprietary drivers.

There is a way to remove the proprietary drivers and (assuming you also remove nouveau.modeset=0 from /etc/default/grub) it will fall back to using the nouveau drivers, but it might not be necessary to do that in order to get suspend to function correctly on your machine.

I'd recommend taking a look at this AskUbuntu question about nVidia graphics drivers: [https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers](https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers)

As far as I can tell, if you add the ppa using:

sudo add-apt-repository ppa:graphics-drivers/ppa

and update your system with **sudo apt update** and **sudo apt upgrade** then it will update your proprietary nVidia graphics drivers to the latest versions. With a bit of luck, any suspend issues will have been fixed by now in the most up-to-date versions of the drivers. 

The 'nouveau.modeset=0' parameter is probably still required to ensure that the nouveau drivers don't interfere, but hopefully you should be able to suspend and resume without further issues.

It would be interesting to know how you get on - the particular suspend issue I'm experiencing on my machine (without the patched kernel) looks very similar to people with s2idle and nVidia driver problems, so if anyone else joins the bug report about suspend issues it'll be good to know what has worked (or not worked) for nVidia users experiencing a similar looking problem.

*Thank* you!  This fix worked immediately for me in xubuntu 18.04 on a Lenovo Thinkpad T60.
[Edit]. This worked for me for three suspend/resumes.  After that my Thinkpad  reverted to the original problem (failure to resume after suspend); then  it failed to boot to a cold start; then it ceased to respond to input  including reinstall.  BRICKED.  BE WARNED

---

