---
title: "Lubuntu 20.04LTS freezing after 5-10 mins of use"
date: 2022-01-18
forum: General Help
---

### Post by goemonburo on 2022-01-18
I've been running Linux and Lubuntu for years and never had this issue.  Can someone help me figure out if this is a hardware issue that I need to resolve with Dell?  Telling the full story, but not sure which parts are germane:

I have a new Dell Inspiron 3000 (the 3511 model) and it's worked fine for the few weeks I had it running Lubuntu 20.04.3LTS, up until today.  The first thing I do when I get a computer is wipe the drive and install Linux.  So I don't know if this issue occurs in Windows.

Today, I tried to add 2 monitors via a D3100 docking station, which I needed because the monitors were Displayport monitors.  I installed a Displayport driver (the beta, 5.5.x) and it ran but with a Secure Boot message, saying I had to add a password.  Instead, I clicked out, rebooted, turned off Secure Boot with F2, rebooted, and then reinstalled the Displayport driver, which now said it was already installed.

Everything -- to my shock -- worked!  I was soon up and running with 2 external monitors.  I had to tweak a bit and get them configured right, but really, I couldn't have been happier.

Then suddenly:  Everything froze.  Just locked completely.  No mouse, no keyboard, the only thing I could do was press "Power" until it did a hard shut down.

I rebooted.  Everything worked.  For about 5-10 mins.  Then again, boom, nothing worked.  Same thing.

I initially thought this was my docking station or the Displayport drivers, so with a heavy heart I unplugged it, then (when that didn't work), I uninstalled the drivers.

But that still didn't fix it.

Thinking it might be something weird with Secure Boot, I switched that back on, rebooted...and the same thing happened.

And now, finally, with only the power cord (not even the wireless USB keyboard and mouse!) the issue still happened.  Freezes solid.  

I am usually running Chrome, so perhaps that's part of the issue?  But I need Chrome, unfortunately, as it's the only way to do the Google Meet video conferences my work requires.

Anyone know what's going on, and whether this is a hardware issue with the computer itself?  It did NOT do this before today.  So I suspect it was something to do with the docking station or drivers.  But it's a new enough computer that perhaps something failed internally and needs to be serviced...in which case Dell is not going to be happy that I've put Lubuntu on there.  

Thank you in advance for any and all suggestions.

---

### Post by GhX6GZMB on 2022-01-18
Sounds to me like a (perhaps thermal) hardware problem. A bad solder joint somewhere or the like. I cannot imagine that SW would be an issue here.

---

### Post by guiverc on 2022-01-18
I'll start out with I have no idea, but I'll give my thoughts.

I don't know what kernel stack you're using (*Lubuntu 20.04 & 20.04.1 media defaults to GA stack; 20.04.2 & later media defaults to HWE, but that can be changed post-install and I didn't see you mention what you're using or if you selected a stack*). 

The reason I'm thinking stack; is I just noticed a Lubuntu 20.04 LTS box which is using the HWE stack install a 5.13 kernel; ie. the move from 20.04.3 to 20.04.4 is approaching fast and kernel stack is shifting from 21.04 (5.11; 20.04.3) to 21.10 (5.13 or 20.04.4) and I wonder if that just happened at the ~same time.

You didn't mention using SysRq keys to force a safe shutdown/reboot etc; ie. use the keyboard to direct the kernel to shutdown; is there a reason for this?  It worked on at least the 5.11 kernel (*I'll have to test on the 5.13 as it was disabled in 21.10*), as firstly that's much safer than the power button, but it also provide valuable information (ie. *it'll work on stuck GUI but not work if kernel has panic'd*)

I'd select an older kernel at `grub` and see if it occurs there; assuming you've switched to 5.13 as I noted a *focal* box do, I'd try 5.11. If the 5.11 works; I'd try switching to the GA kernel stack (*it's the more stable option; though having older drivers (kernel modules due to older kernel) it won't be as good for newer hardware*).  You can try that stack on *live* media too, but it won't have 'displayport' driver (*of which I know nothing about - thus cannot know it's impact sorry*)

---

### Post by goemonburo on 2022-01-18
Hi, and thank you for these suggestions.  @ml9104, I am just oh-so-hoping that it's not a hardware issue.  One thing I noticed is the thing was really hot, not so hot I couldn't touch it, but very hot.  Maybe that played a part?

@guiverc, can you tell me more about the kernel?  As I mentioned, this is off a fresh install of Lubuntu 20.04.3LTS.  It does, however, run through an update process, and come to think of it, I may have done that this morning or yesterday or something.  But I'm not sure how to walk back to an older kernel once I've updated.  At this point, maybe I'll reinstall from scratch (sigh, a third time) and then NOT update and see if I still have problems?  Really might indeed be what's going on.  Thank you for suggesting this.

---

### Post by goemonburo on 2022-01-18
@guiverc, I think you hit the nail on the head.  I did a fresh Lubuntu install, sorry, probably a more classy way to do that but I didn't have anything vital there...just easy to reinstall.  Then instead of doing the "There are updates..." and updating, I left it as is, and, whereas it was crashing 5 or 10 mins repeatedly, I ran it for more than an hour this time.  So I suspect you're right, that it's something in the kernel that's messed up.

My next question is what are the next steps?  I don't really want to leave an un-updated system out there.  Can I update most things but not the kernel?  

And for the Secure Boot, which seems to not have been the issue at all, will I have any problems (other than boot being insecure) if I turn it off and try to get this docking station and dual monitors running?

Again, thank you for your time and for the insightful suggestion.  Never occurred to me it was the updates I'd just put in.  Really hope this gets fixed soon.  Is there a way to track kernel updates and see when a new one is released?  (Going to google, yes, I'm sure there's a way.)

---

### Post by guiverc on 2022-01-19
Ubuntu LTS releases offer two kernel stack choices.

The most *stable* choice is GA; which is the default for all Ubuntu Server installs (*though live Server installs allow that to be changed at install time*)

Ubuntu 20.04 LTS Desktop defaults to the HWE choice as it's more useful for *newer* desktops as the newer stack gives you newer kernel modules (which are commonly called *drivers*) which are needed for newer desktop/laptop hardware.  

With Lubuntu; the ISO used to install dictates the kernel stack you're using.

- Lubuntu 20.04 LTS & Lubuntu 20.04.1 LTS media defaults to the GA stack for installs.

- Lubuntu 20.04.2 & later (ie. your 20.04.3) default to the HWE stack; thus with 20.04.2 media you'll start with 5.8 kernel, 20.04.3 media starts with 5.11, but both upgrade as appropriate (*we're getting close to 20.04.4 which uses the 5.13 kernel - thus it'll upgrade to the 5.13*).

For more details you can read [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

It provides commands that will let you switch from HWE to GA stack.

I've got to *step away from keyboard* now, so this is all I can quickly type.. I'll read the rest of your post & reply if necessary later today.

---

### Post by guiverc on 2022-01-19
Further to my last post.

If you'd like to install Lubuntu and have it default to the GA stack I'll provide the following

- a link can be found* somewhat* *hidden* here [https://help.ubuntu.com/community/LXDE-lubuntu/Alternate_ISO](https://help.ubuntu.com/community/LXDE-lubuntu/Alternate_ISO)

Do **NOTE** it's a link to a 3rd party site.. so all you'll have is my word that I believe it to be safe.  That page will direct you to

- [https://phillw.net/isos/lubuntu/focal/](https://phillw.net/isos/lubuntu/focal/)

Your alternative is to use an existing 20.04.3 install, where you said it was fine on install (until it upgraded to the .4 or 5.13 kernel) and then run the instructions in the [link I provided last post]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") in the section that starts "*To downgrade from HWE/OEM to GA kernel:*". ie. it'll get you to run

```

sudo apt install --install-recommends linux-generic 

```

which installs the GA stack onto your existing Lubuntu system, meaning you'll have both.  Yes there is a command to remove the HWE kernel in the page as well; but that's optional (*the instructions say to do it when you know the other stack is working*).  

You can select which kernel you boot at the `grub` menu.. How `grub` appears though is dictated by your hardware; on some boxes I get a really nice blue background, logo & nice easy to read menu.. but on others it's a black screen with a white box drawn around some text (*even this can vary; on some it's whole screen yet on other boxes it's top left, some in the centre - ie. your boxes firmware dictates how it shows by default*).  The page in the Lubuntu manual that describes this can be found at

[https://manual.lubuntu.me/lts/A/tips_and_tricks.html?highlight=grub](https://manual.lubuntu.me/lts/A/tips_and_tricks.html?highlight=grub)

Grub allows you to select which kernel is used for the session, ie. since you have trouble with 5.13; you can select an older 5.11 kernel that was used during installation (*bypassing your issue*), or IF you do as I've suggested this post & installed the GA stack to sit alongside the HWE your media installed; you can select which you'll use.

The GA stack is the 5.4 kernel & will remain it for the life of Ubuntu 20.04 LTS  (ps:  I think of Lubuntu as a Ubuntu system, so where I've said Ubuntu just read it as Lubuntu being the *flavor* of Ubuntu you & me are actually running).

Secure boot.... I don't remember that part of your question so I can't reply to that.  Ubuntu/Lubuntu will use whatever your machine is set to use at installation time; so if you are dual booting (ie. installing two OSes and using `grub` or uEFI to select which you'll boot) they both need to be in the same mode for menus to show both options.  I gather Secure mode is more *secure* (*I've seen posts on this site saying why*) but I worry most about not losing my systems.  If your system is working for you; I'd just use it & not worry about it.



Another thought that occurred to me.

You do realize you can re-install a Lubuntu system, and have it auto-install any additional packages (apps) you'd installed automatically (*deb* packages anyway, or *snap* if installed by *deb* stubs)... and not have it touch your user files.. Yes you should **always****have backups**as mistakes are easy to make, but we at Lubuntu call it "*Install using an existing partition*" and it's a QA (*Quality Assurance*) testcase which I describe here

- [https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743](https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743)

just search for "*Install using existing partition:*"   I*t was written by me; so it's likely more wordy than it needs to be*..   I'm not describing it for end-users so they can make use of it there, the document is geared for those wanting to do some QA test installs and it's explanatory around following that testcase.  I use `clementine` & my music as example; but that could be whatever programs you've added to your Lubuntu 20.04 LTS system, and music whatever files you've created/added etc.  FYI: Chrome you mention is a 3rd party app; and we only QA-test with Ubuntu repository software, so I don't know how well it'll cope with that (*nor do I want to know!*) but it copes with`chromium` in Ubuntu repositories (*the **open source version from which Chrome is generated by the Chromium Project*)

Your real issue:
- I'd see if you can use the GA kernel; check out everything works... 
- I'd have GA & HWE stack installed; the HWE *bump* to 5.13 is only new & loads of bugs have been noticed as tends to happen... You'll need to report a bug if you want your issue addressed though; but I'd hope & expect the GA stack will return your system to working.  You can always try HWE now & again to see if it's fixed  (*now and again being when you note new HWE kernels appearing in your upgrades*)

---

### Post by goemonburo on 2022-01-19
So again, THANK YOU for the help and I'm thrilled to say that the system is still working fine after a whole night...so I'm convinced that it was the upgrade that broke things.  uname -r reports that the WORKING kernel is 5.11.0-27-generic, and seeing as this works, I think ideally I'd like to keep this existing install.  Mainly just want to know if it's possible to update the system and only flag the kernel to remain the same.  Or will that cause other things to break or become unstable?  I guess I don't fully understand the differences and benefits of the GA vs HWE kernels.  

How often are kernel updates made?  Might I expect this freezing issue to be resolved in the next HWE update?  (You suggest filing a bug report, which I'll be happy to do, though I haven't done that before and am unsure what that process is.)

I am seeing a black screen with white text when I boot, so if I upgrade as I did before, then have the problem, you're saying I can just reboot, get that GRUB options, and boot with the older kernel.  But might (just thinking) I be able to modify Grub such that the older kernel is the default again?)

I would say that in my case, the easiest solution is probably the one that I want to do, and that easiest solution may be to just remember to click to the older kernel at boot each time...updating as usual, but hopefully finding that a 5.13.0.xyz kernel fixes the issue.  Right now, I'm being prompted to update but holding off, since the 5.11.0-27-generic kernel is working fine.  Presumably, based on what you're saying, I could go ahead and do the Update, reboot, and then if I see this happen again, instead of reinstall Lubuntu from scratch, just select the older kernel at boot from that black and white box screen of boot options.  At some point, after updating, the issue may go away.  

If that's a reasonable scenario I think that's what I'd opt for, rather than to go to the GA kernel or fork my system into something that's on a different track.  Thank you so much for the answers, and I really appreciate the detail you've offered, no apology needed for being verbose -- it's been very helpful to have things explained clearly.  Really really appreciate it.  

So at this point, I think I just want to know if I should: 

1)  Not upgrade at all, clicking "Cancel" when prompted to.
2)  Upgrade, but do it in a way that leaves the existing kernel.
3)  Upgrade, including the kernel, and forevermore revert to the older kernel at boot
4)  Upgrade, including the kernel, then adjust Grub defaults to use the older kernel if the new one isn't working

Probably my ideal would be #4, if that's possible.

But in any case, the eureka hallelujah moment for me is knowing that indeed, it's a kernel issue.  From there, I can move forward with one of these 4 options, probably #3 or #4 I'm guessing, would be the best.

---

### Post by T6&amp;sfpER35% on 2022-01-19
> and it's worked fine for the few weeks I had it running Lubuntu 20.04.3LTS, up until today
>  I did a fresh Lubuntu install, sorry, probably a more classy way to do that but I didn't have anything vital there...just easy to reinstall. Then instead of doing the "There are updates..." and updating, I left it as is, and, whereas it was crashing 5 or 10 mins repeatedly, I ran it for more than an hour this time. So I suspect you're right, that it's something in the kernel that's messed up.

iv'e used linux for about 2 years now and i experienced the same , everything would work flawlessly for up to 3 months and then random freezes starts and it just gets worse ... then i'd do a fresh install (**update everything after install.**.. ) , and its all good for another 2 or 3 months and then freezes starts again.
i eventually grew tired of trying to find solutions and re-installing every now and again . I went with windows10 now and well, everything just works , even my usb ports in the front of box ,that didn't work with linux , now suddenly works just fine.
not  trying to bash linux , i loved it when it was working , but the hassle to just keep it going problem free became to much for me .

PS . wanted to post links to my threads i started trying to resolve freezes  and usb ports not working... i know i started threads , but cant find it now it seems to have disappeared , anyway...

---

### Post by dragonfly41 on 2022-01-19
> I went with windows10 now and well, everything just works , even my usb ports in the front of box ,that didn't work with linux , now suddenly works just fine.
not trying to bash linux , i loved it when it was working , but the hassle to just keep it going problem free became to much for me .

I have the opposite experience. Ubuntu 20 (on Dell) solid, but when I dual boot into Windows 10 it is sluggish, subject to various virus scanning etc. I intend to reinstall Windows 10 at some point. And then we have Windows 11 to contend with.


> PS . wanted to post links to my threads i started trying to resolve freezes and usb ports not working... i know i started threads , but cant find it now it seems to have disappeared , anyway.

I can view the history of your posts by clicking on your profile.

[https://ubuntuforums.org/member.php?u=2146576](https://ubuntuforums.org/member.php?u=2146576)

---

### Post by T6&amp;sfpER35% on 2022-01-19
i can also see "find all my posts" and "find all my threads" , but some of my threads that i know i have started ,is gone . 
doesn't matter though.

---

### Post by Autodave on 2022-01-19
Eleven machines currently using 20.04.  Machines range from very fast ones to incredibly slow ones, but none give me any issues at all.  3 are dual-booted with Win 10 and one with Win 7.  Win7 sucks and one Win 10 machine has lots of problems all the time.

---

### Post by goemonburo on 2022-01-19
So the saga continues just a bit longer (and sorry for those who are suggesting Windows, I left that train in 1999 and have run Linux in one form or other since then, after half a novel vaporized and a backup that I thought was being done by Word had not been.  For stability overall, Linux is hands down the best option that I've used and worked with.  Not sure we need to debate that on an Ubuntu forum.)  

But back to this issue:  Alas, it has not yet been solved.  I had a good run this afternoon, thinking that it had been due to my tweaking and then failing to readjust the Secure Boot, but eventually that (and yes, sigh, another reinstall) failed.

I have not had the window appear where I can choose which kernel to boot to.  Is there a way to modify the Grub conf file or such that it will show?  I feel like that's the next step.  I did upgrade to the 5.13.x kernel (since I thought Secure Boot had been the culprit), and I think now that it may be the kernel after all.

So I'm going to try booting back into the 5.11.x kernel and see if that fixes things.  Fingers crossed.

---

### Post by T6&amp;sfpER35% on 2022-01-20
> For stability overall, Linux is hands down the best option that I've used and worked with.
>  those who are suggesting Windows, I left that train in **1999**
hope you can see where i'd go with this , but i'm not going to lol , like you said , we not here to debate on OS's

---

### Post by dragonfly41 on 2022-01-20
I am going to suggest trying a "parallel universe" - at least it works for me.
Until you find time to sort out / repair grub issues, you can install rEFInd.
[https://www.rodsbooks.com/refind/installing.html](https://www.rodsbooks.com/refind/installing.html)

It will install into /boot/efi/EFI/refind and offers an emergency route to launch kernels.
It offers a nice GUI and does not stop conventional grub from working. But only works with UEFI.

It may not help with your freezing problems - only your grub problems.

---

### Post by Autodave on 2022-01-20
I would try booting to your install medium and running from that to see what happens.  If it crashes on that, then I would be looking at a hardware issue.

---

### Post by goemonburo on 2022-01-20
Have had the longest run yet by staying in 5.11.x.  Seems to be the kernel.  There are some issues (laggy external monitors) but I'll take that over a complete freeze.

I installed grub-configurator, but probably could have just edited the config file by hand.  But now, I get a nice 3 second window to choose my kernel or other such boot options, and then it goes to the default (which is the last one booted previously).

I think we can say this is solved.  It was the kernel.  So I'll just hope something comes along and fixes that.

---

