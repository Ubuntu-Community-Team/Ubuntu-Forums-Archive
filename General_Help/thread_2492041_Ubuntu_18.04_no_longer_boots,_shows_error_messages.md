---
title: "Ubuntu 18.04 no longer boots, shows error messages on black screen."
date: 2023-10-28
forum: General Help
---

### Post by Richard_York on 2023-10-28
We're still running Ubuntu 18.04 on a desktop machine. While it's always been bomb-proof up to now, it currently won't boot up.

After a while I get this first screen,  [IMG]https://ubuntuforums.org/attachment.php?attachmentid=292972&stc=1[/IMG]
which leads on to this, sometimes with many other message lines first, but always ending the same:

 [IMG]https://ubuntuforums.org/attachment.php?attachmentid=292971&stc=1[/IMG] (These are camera shots because I can't access screenshots just now)
I've tried the various "systemctl reboot" commands, I've tried most of the options, but it always shows the first screen, and it always ends up with the "You are in emergency mode" stage.
When I asked for the journal - none of which I understand! - among all the rest it highlighted in red the lines shown in my first screen image.

So we're locked out of everything - not good.
One possibility I can offer is that the monitor screen, which is old, sometimes loses the plot and goes dark, when the way to restore it is to close down by pressing the computer power button for 10 then switch off power to the whole set-up, allow a few minutes and start again; I tried to start it when the screen was dark earlier, realised, and powered down half way through the start-up process - maybe that upset things?

Please note: I write as one who a uses Ubuntu because I like the principle, I don't like Windows, and it's enabled older machines to carry on working, but not because I understand what's going on inside the machine, my brain doesn't work that way -
I'm a paid-up non-geek, so not the average Ubuntu user, I realise!

But I would be extremely grateful for any step-by-step suggestions of how to get our machine back, please. While it ran its back-up a few days ago, I'd need serious help to use that... even to know how to get the machine to find the relevant part of the external drive where it's stored, while the computer's in this state. 
Meanwhile I have a ticketed event I'm organising on Wednesday,  with all the details currently locked  behind this barrier.

Thank you for any help. Especially if it's the sort I can understand how to follow!

(I would copy here the details of the computer, but since I can't get in I find that a difficult thing.)
[Edit... or if anyone knows of a friendly Ubuntu competent person within easy range of Northampton UK who might help, I'd appreciate the contact...]

---

### Post by Richard_York on 2023-10-28
More research.... is reinstalling Ubuntu while preserving files, as at[ [https://www.makeuseof.com/tag/fix-ubuntu-linux-pc-wont-boot/](https://www.makeuseof.com/tag/fix-ubuntu-linux-pc-wont-boot/) ]("https://www.makeuseof.com/tag/fix-ubuntu-linux-pc-wont-boot/") option 4, my easiest and most foolproof route?

---

### Post by Rubi1200 on 2023-10-28
18.04 has reached EOL. Therefore, it will no longer receive security updates and thus puts the system at risk.

You should consider using a liveUSB to backup any important data and then install the latest LTS, which is 22.04

---

### Post by Richard_York on 2023-10-28
Thank you - yes, I'm sadly aware it's past its EOL support date, and now have a newer machine ready to install a new system on, because the existing desktop is, I believe, not up to 22.04 requirements. Ironic that it's fallen over before I got to doing this...
I was seriously considering re-installing 18.04 with the preserving files option, through a live USB, to reclaim the data, (as in my #1 post) but don't have the original USB with 18.04 any more.
 I've tried downloading a new iso from [https://releases.ubuntu.com/18.04/](https://releases.ubuntu.com/18.04/)  but I can't get it to verify satisfactorily with the SHA256SUMS files on the same page.  Probably too risky just to make a live-boot and  go ahead anyway for the sake of releasing the data?

---

### Post by MAFoElffen on 2023-10-28
Did you check your BIOS settings to ensure that SecureBoot didn't somehow get toggled to "Enabled"? Please check that before doing anything...

All those errors were on EFI and trusted keys. (Such as being signed for SecureBoot)

Just saying: Some things, like a doing reinstall, will fix something, but is a lot of unneeded work if the underlying cause was just something very simple.

If that fixes it, the first thing you should do is to get a good backup of your system, then _please do a release upgrade or migration to a release that is supported._ If, for some reason, there is something that requires you to stay with that release version, then enroll it into ESM with Ubutu Pro, so that it gets security updates.

---

### Post by Richard_York on 2023-10-29
> **MAFoElffen said:**
> Did you check your BIOS settings to ensure that SecureBoot didn't somehow get toggled to "Enabled"? Please check that before doing anything...

All those errors were on EFI and trusted keys. (Such as being signed for SecureBoot)

Just saying: Some things, like a doing reinstall, will fix something, but is a lot of unneeded work if the underlying cause was just something very simple.

If that fixes it, the first thing you should do is to get a good backup of your system, then _please do a release upgrade or migration to a release that is supported._ If, for some reason, there is something that requires you to stay with that release version, then enroll it into ESM with Ubutu Pro, so that it gets security updates.

Thank you. I just tried to find the "SecureBoot" option and am embarrassed by failure to do so, though have found it on other machines... I get as far as the screens shown in photos here, but am wary of pressing too many options in case I mess things up more. Is it through one of these, please?
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292976&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292977&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292978&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292979&stc=1[/IMG]

And thanks too for your emphasis on the need to get a system update. I will -  it had been my intention months ago until distracted by some health issues. I'm realising that truly excellent as Ubuntu is, it's probably increasingly better for those of you much more tech savvy, but I still don't lilke Windows, so am thinking to try Mint. But that's going OT to pursue here.

---

### Post by guiverc on 2023-10-29
You can *non-destructively *reinstall Ubuntu Desktop systems if it comes to that.

I too wonder if your issue relates to a *deprecated* key due to not applying security fixes (*you'll need ESM for those*), but I've not looked, what I was reminded of from your messages refers to Secure-boot uEFI only (*the fix for which is disabling Secure-boot; applying security fixes then Secure-boot can be re-enabled, BUT this will require ESM to be enabled!* *unless you're willing to fix it yourself manually*).  I won't provide help here though, as your release is EOSS.

I'll provide a link to [an answer I wrote (*somewhat recently*) on non-destructive installs]("https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533"); it only partially relates to the question; but I was asked to write it & selected that question.  I used it on this box last on 29-August-2023 when I got tired of an issue & my inability to resolve it & used it as an easy fix. I even planned to use it myself for an old *xenial* or 16.04 box just prior to [18.04 reaching EOSS]("https://fridge.ubuntu.com/2023/05/13/extended-security-maintenance-for-ubuntu-18-04-bionic-beaver-begins-31-may-2023/") as it would allow me to jump to 22.04 in a fraction of the time a *release-upgrade* would have taken just to 18.04 (*the next upgrade*), but I'd read numerous posts of people unable to *release-upgrade* 16.04 boxes; thus used the  slow process instead so I could use it as example of it working.. (*followed by 18.04 to 20.04 etc... so 30 minute re-install expanded to ~day*)

---

### Post by yancek on 2023-10-29
I see in one of your images that the build date for the system was September, 2011.  Windows and Linux did not start using UEFI as a default until 2012 although it was available so was/is this an EFI install of Ubuntu or was it installed in Legacy mode?  Were any changes made to the system just prior to this problem and if so, what were they?  If it is an EFI install something must have changed to prevent it from getting the UEFI db list which shows in your first image.

---

### Post by Richard_York on 2023-10-29
> **guiverc said:**
> You can *non-destructively *reinstall Ubuntu Desktop systems if it comes to that.

I too wonder if your issue relates to a *deprecated* key due to not applying security fixes (*you'll need ESM for those*), but I've not looked, what I was reminded of from your messages refers to Secure-boot uEFI only (*the fix for which is disabling Secure-boot; applying security fixes then Secure-boot can be re-enabled, BUT this will require ESM to be enabled!* *unless you're willing to fix it yourself manually*).  I won't provide help here though, as your release is EOSS.

I'll provide a link to [an answer I wrote (*somewhat recently*) on non-destructive installs]("https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533"); it only partially relates to the question; but I was asked to write it & selected that question.  I used it on this box last on 29-August-2023 when I got tired of an issue & my inability to resolve it & used it as an easy fix. I even planned to use it myself for an old *xenial* or 16.04 box just prior to [18.04 reaching EOSS]("https://fridge.ubuntu.com/2023/05/13/extended-security-maintenance-for-ubuntu-18-04-bionic-beaver-begins-31-may-2023/") as it would allow me to jump to 22.04 in a fraction of the time a *release-upgrade* would have taken just to 18.04 (*the next upgrade*), but I'd read numerous posts of people unable to *release-upgrade* 16.04 boxes; thus used the  slow process instead so I could use it as example of it working.. (*followed by 18.04 to 20.04 etc... so 30 minute re-install expanded to ~day*)

Thank you - so if I'm understanding correctly, is this more or less the same as option 4 in [https://www.makeuseof.com/tag/fix-ubuntu-linux-pc-wont-boot/ ]("https://www.makeuseof.com/tag/fix-ubuntu-linux-pc-wont-boot/") ?

If so, since I no longer have my original liveboot USB with 18.04LTS on, I tried preparing for this by downloading the iso from [https://releases.ubuntu.com/18.04/](https://releases.ubuntu.com/18.04/)   but couldn't get the SHA256SUMS to agree, despite repeating the download. I haven't yet found another source of 18.04.  
Or am I barking up the wrong tree here?

---

### Post by Richard_York on 2023-10-29
> **yancek said:**
> I see in one of your images that the build date for the system was September, 2011.  Windows and Linux did not start using UEFI as a default until 2012 although it was available so was/is this an EFI install of Ubuntu or was it installed in Legacy mode?  Were any changes made to the system just prior to this problem and if so, what were they?  If it is an EFI install something must have changed to prevent it from getting the UEFI db list which shows in your first image.

I have to apologise that I can't answer these questions, because I'm rather like the passenger in the plane who ends up having to bring it in to land never  having flown, with instructions from the control tower!
The build date is shown as then, but I didn't buy the machine for a few more years, maybe even around 2018.

I honestly can't tell you if it was in Legacy mode... I tried to make it dual boot with Windows, which came on the machine already, having daringly partitioned it first to make a space for Ubuntu to occupy, but other than that I'd have used as many default settings as possible. It's quite possible the only change to the settings I made was to alter the BIOS order. If maybe I saw advice online to make other changes I could have made them on the passenger flying the plane being told to press that button by the control tower principle, but not because I knew why!
I have no memory of Legacy Mode being one of the things I touched.

---

### Post by MAFoElffen on 2023-10-29
You have an ASUS P8Z68-V LX... It was made in 2011. I went completely through the User Manual for that... There are some features missing from that in the BIOS, which brings up more specific questions.

Here are some commands for gathering information that might help us with this. Please boot from the Installer LiveUSB, use "Try". Open a browser and a terminal session. Go to this post from the browser. Copy and paste these commands into the terminal session. Please copy and paste the output from them into a post the results of these "within CODE tags". Visit the "CODE Tags" link in my signature line, if you need guidance on adding CODE Tags.
```

[ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"
sudo dmi-decode -t 0,1
mokutil --sb-state

```
The output from those will tell us what it is capable of... Which will guide us on how to recommend solutions for it.

---

### Post by guiverc on 2023-10-29
> **Richard_York said:**
> Thank you - so if I'm understanding correctly, is this more or less the same as option 4 in [https://www.makeuseof.com/tag/fix-ubuntu-linux-pc-wont-boot/ ]("https://www.makeuseof.com/tag/fix-ubuntu-linux-pc-wont-boot/") ?

If so, since I no longer have my original liveboot USB with 18.04LTS on, I tried preparing for this by downloading the iso from [https://releases.ubuntu.com/18.04/](https://releases.ubuntu.com/18.04/)   but couldn't get the SHA256SUMS to agree, despite repeating the download. I haven't yet found another source of 18.04.  
Or am I barking up the wrong tree here?

I won't provide support for an EOSS release, providing only pointers (*usually being what I'd do*).

Most ISOs for *bionic* (18.04) will be found at [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/) however most *flavor* ISOs I'd expect to have been *dropped *already (*I've not looked*, *flavor ISOs are not  moved to old-releases.ubuntu.com*).

Ubuntu 18.04 LTS was available with many ISOs, and my instructions applied only to `ubiquity` ISOs for 18.04. 

 Whilst no ISO existed using `calamares` until 18.10, and ISOs using *canary* didn't exist until 19.10, with *canary* being renamed to `ubuntu-desktop-installer` for 23.04. Whilst it may work with *di* (debian installer) and `subiquity` (*I think a later respin with subiquity was made for 18.04*, *not sure if it was released or only for QA as I don't remember*) I didn't test those with non-destructive installs, and wouldn't expect them to be usable.

My intention was to provide it as an option, ie. you don't re-install a 18.04 system, but use the re-install to achieve an _*upgrade via re-install*_ by non-destructively re-installing a *fully supported* and modern release of Ubuntu.

I didn't think much of the link you provided; yes step 4 maybe an equivalent option providing you selected an ISO that used the `ubiquity` installer; the link you provided gave no details. It did mention *live* ISO (`ubiquity` ISOs were live, but so was `subiquity`) where as *di* ISOs I exclude was not live.  Further the options that article mentioned however I'm not familiar with being offered, but it's been a long time since I performed any QA using 18.04(.5) ISOs ([2020-August]("https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/")), and those 18.04.5 ISOs won't boot on modern updated hardware anyway, due to now *revoked* keys baked into the ISO & [later 18.04.6 ISOs being generated]("https://fridge.ubuntu.com/2021/09/17/ubuntu-18-04-6-lts-released/") which I didn't QA with new keys.

---

### Post by Richard_York on 2023-10-30
> **MAFoElffen said:**
> You have an ASUS P8Z68-V LX... It was made in 2011. I went completely through the User Manual for that... There are some features missing from that in the BIOS, which brings up more specific questions.

Here are some commands for gathering information that might help us with this. Please boot from the Installer LiveUSB, use "Try". Open a browser and a terminal session. Go to this post from the browser. Copy and paste these commands into the terminal session. Please copy and paste the output from them into a post the results of these "within CODE tags". Visit the "CODE Tags" link in my signature line, if you need guidance on adding CODE Tags.
```

[ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"
sudo dmi-decode -t 0,1
mokutil --sb-state

```
The output from those will tell us what it is capable of... Which will guide us on how to recommend solutions for it.


Thank you for spending time on this, it's much appreciated.
Because I no longer have the original USB stick I downloaded 18.04 from [https://releases.ubuntu.com/18.04.6/](https://releases.ubuntu.com/18.04.6/)  just now, along with the SHA256SUMS files. Because I'm thinking of  changing to Mint Cinnamon I already had instructions for verifying an  ISO at [https://forums.linuxmint.com/viewtopic.php?f=42&t=291093](https://forums.linuxmint.com/viewtopic.php?f=42&t=291093)   and followed these - I'd already used them for Cinnamon and can follow  them. Verification worked perfectly this time. The second stage, the  Authenticity Check, didn't - I got 
```
C:\Users\yanad\Desktop\Ubuntu 18>gpg --verify sha256sum.txt.gpg sha256sum.txt
gpg: can't open 'sha256sum.txt.gpg': No such file or directory
gpg: verify signatures failed: No such file or directory
```

I don't know if the method  I'm using there is specific to Mint, thus creating a problem  ... both the SHA256SUMS files show in the directory...

Would it be foolish, given that verification worked, to create a liveboot USB from this so I can try your suggestion?

Once I've retrieved my files and profiles for Thunderbird and Firefox  I'll not be continuing to use the machine, so as long as it works long  enough for that I'll be content. 
On the other hand I don't wish to risk losing those essential data.

---

### Post by Richard_York on 2023-10-30
Thank you Guiverc - as in my post #13 here the old releases link led me to one where the verification process worked up to a point. Which is progress!
It's no criticism of your post, but rather a comment on my level of knowledge/way my brain works, is that I can't claim to understand many of the terms in what follows, I'm truly sorry.

Re-the suggestion of non-destructively installing a fully supported modern release of Ubuntu - I don't know that the machine now sitting on my desk is up to this. If the information I've already posted in images suggests that it would, or if photographing other screens at the set-up stage, might indicate otherwise I'll take more photos and post them.

---

### Post by kinddolphin8827 on 2023-10-30
I would strongly recommend that the original poster consider backing up their important data and migrate to a newer release of Ubuntu. I would also recommend that the original poster invest in a separate HDD or ssd so as to separate  their Windows and Linux installations.

---

### Post by Richard_York on 2023-10-31
> **MAFoElffen said:**
> You have an ASUS P8Z68-V LX... It was made in 2011. I went completely through the User Manual for that... There are some features missing from that in the BIOS, which brings up more specific questions.

Here are some commands for gathering information that might help us with this. Please boot from the Installer LiveUSB, use "Try". Open a browser and a terminal session. Go to this post from the browser. Copy and paste these commands into the terminal session. Please copy and paste the output from them into a post the results of these "within CODE tags". Visit the "CODE Tags" link in my signature line, if you need guidance on adding CODE Tags.
```

[ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"
sudo dmi-decode -t 0,1
mokutil --sb-state

```
The output from those will tell us what it is capable of... Which will guide us on how to recommend solutions for it.

I was hoping to report back but two hurdles arise. One is my query over whether my newly downloaded 18.04 iso, which passses the verification but not the authenticity test, would be safe or foolish to try this with, (please see my post of yesterday on this thread). I'd welcome advice on that, please.
Meanwhile I wondered if the bootable USB I already have of Mint Cinnamon 20, which passes both verification and authenticity tests, might produce a useful result with your commands, since I understand Mint is also Ubuntu based and it would produce a terminal to type into. It fires up perfectly on the newer machine I tested it on, the one I'm hoping to transfer operations to when I've recovered my data, but on the crashed desktop it started well, got as far as the Mint logo,  but then the monitor showed "Video Mode Not Supported" and I was stuck there, and am now even further out of my depth!

---

### Post by go88com on 2023-10-31
Thanks you

---

### Post by MAFoElffen on 2023-10-31
You keep mentioning "Mint"... I seem to be confused.

Is this Mint or Ubuntu?

---

### Post by Richard_York on 2023-11-03
> **MAFoElffen said:**
> You keep mentioning "Mint"... I seem to be confused.

Is this Mint or Ubuntu?

Sorry, my failure to explain.
 I've increasingly realised that the level of knowledge needed to work Ubuntu well is far above my own understanding, and as I'm prone to brain fog and come from a very non-tech background I'm not good at learning such - I tried, but just don't have the right sort of brain shape.
So I'm thinking of jumping ship, with regret. I was tempted to return just to the Windows which comes already installed,  but the more I use it (on the laptop I'm currently typing on, for example) the more I don't like it. So Linux Mint appears to be less challenging, more "out of the box" while still being Linux and not Windows. 
 I've been experimenting with downloading the Mint Cinnamon iso, and trying it in a live USB session on the newer desktop tower which is to replace the 18.04 machine which has crashed and probably won't stand being upgraded to current Ubuntu versions.
Hence my having a verified and authenticated version of Mint.
And I confess to being easily confused with most things related to computers, I just don't like Windows, and have vastly preferred Ubuntu as a day-to-day OS!

Meanwhile, with **very** many thanks to all who have so patiently contributed to this thread, I confess to having chickened out - I've at last found a professional local computer technician who works with Linux iuncluding Ubuntu, and he now has my crashed machine in order , hopefully, to recover the data there so I can transfer it to the newer tower.... probably running Mint.  
If he can't recover my data, I may well be back, cap in hand, asking for more help...

---

### Post by MAFoElffen on 2023-11-03
If he needs help or ideas, he can PM or email me. Maybe it's best that he try. Will be faster, and maybe he will show you what went wrong, as an educational expereince for you.

You had copied the commands I asked for output on twice, without actually doing them... If it had just booted on your LiveUSB media, you could have tried. If it had booted, we could have also explained how to recover your data from that. No matters.

Sorry we couldn't explain in way way that made you comfortable and more self-confident. Tell us what they found, so we know you got taken care of.

---

### Post by Richard_York on 2023-11-04
> **MAFoElffen said:**
> If he needs help or ideas, he can PM or email me. Maybe it's best that he try. Will be faster, and maybe he will show you what went wrong, as an educational expereince for you.

You had copied the commands I asked for output on twice, without actually doing them... If it had just booted on your LiveUSB media, you could have tried. If it had booted, we could have also explained how to recover your data from that. No matters.

Sorry we couldn't explain in way way that made you comfortable and more self-confident. Tell us what they found, so we know you got taken care of.

Thank you - I will report any info I can from the technician, indeed.

I'm sorry not to have fed back results from the commands you suggested. I was fully intending to do so but that, as I mentioned in #16 above, I  no longer had the original  18.04 LiveUSB, and wasn't confident about the new download I made which got stuck at the authentication stage. And I don't know if the other iso I had, of Mint Cinnamon, might have worked enough to give the information?
I'm wary of pressing buttons I know nothing about, to see what they do, in case the whole thing breaks!

The fault's not in your lack of explanations nor willingness to help, more that no matter how much I admire the principle and day-to-day front-end working of Ubuntu, my brain doesn't grasp digital technology concepts nor the terminology at all well, especially since ME/Chronic Fatigue struck some years ago. I'm fine as long as it chugs on nicely without the need for tinkering, and for around 10 years Ubuntu's been far more agreeable than Windows to use. ( I realise that for most here, getting stuck in and working under the bonnet/hood is a large part of the pleasure.)

My best wishes to you and all reading.

---

### Post by MAFoElffen on 2023-11-04
For future reference: You could have done those commands from any bootable Linux LiveUSB, that would boot on it, and allow you to get to a terminal session or Vtty console session... You did not need the "original" iso of the installed system to do that.

---

### Post by Richard_York on 2023-11-05
> **MAFoElffen said:**
> For future reference: You could have done those commands from any bootable Linux LiveUSB, that would boot on it, and allow you to get to a terminal session or Vtty console session... You did not need the "original" iso of the installed system to do that.
So that Linux Mint USB I mentioned would have done the job after all? Ah well...

---

### Post by MAFoElffen on 2023-11-05
> **Richard_York said:**
> So that Linux Mint USB I mentioned would have done the job after all? Ah well...

Yes. You could have run those commands from any bootable Linux LiveUSB, from a terminal session while it is running.

*** See? This is why I started the Ama-Gi Project: I created a bootable Linux LiveCD back in 2012, based on Ubuntu 12.04 LTS, to be able to repair computers with Linux installed. The infinite combinations of what might be running on top of the kernel made that, well... a big challenge.

---

### Post by Richard_York on 2023-11-07
> **MAFoElffen said:**
> Yes. You could have run those commands from any bootable Linux LiveUSB, from a terminal session while it is running.

*** See? This is why I started the Ama-Gi Project: I created a bootable Linux LiveCD back in 2012, based on Ubuntu 12.04 LTS, to be able to repair computers with Linux installed. The infinite combinations of what might be running on top of the kernel made that, well... a big challenge.

If only I'd  known that... !!

---

### Post by Richard_York on 2023-11-11
Many thanks again to all who offered such helpful responses to my questions. The good news is that the Ubuntu 18 machine is now restored to fully working order and I'm currently trawling all the data from it to install into a newer machine.
While I know that the technician who worked on it was able to open the back-up files I supplied, we met so I could collect it from him when he was about to run an AGM for a local radio club, so there wasn't time to ask more about just how he got into my computer, I'm sorry. 
If I find out more from him I'll pass it on here.

---

