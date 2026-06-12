---
title: "Accidentally had to cancel mantic minotaur update, now software updater won't work."
date: 2024-06-28
forum: General Help
---

### Post by Jotaro on 2024-06-28
So the mantic minotaur upgrade dropped. At first I decided to wait a bit, before installing it. Well when I tried, it gave me some sort of error involving xscreensaver and xlockscreen, so I panicked and canceled it. I restarted the computer, very scared that I had ruined everything, but thankfully everything was fine, at first glance.

   Later, I realized I'm on LTS anyways, and won't need a full upgrade till April 2025, which gave me relief. Things were looking up, but then I got a update notification about a "partial update". I used google to see what this was, and people mainly said to use the terminal to update. I did, and it downloaded like a LOT of stuff, some of which was mantic minotaur stuff it seemed.

   So everything was still looking fine, but then I tried going to Preferences, Software Updater, and checking for updates, but here's the problem. It gets to "Checking for Updates" and does nothing after that. Its just stuck.

   So I tried the terminal with "sudo apt-get install update-manager, and it gave me this:

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nautilus : Breaks: nautilus-share (< 0.7.3-2ubuntu7~) but 0.7.3-2ubuntu6 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

I'm sorry for being so stupid, can someone please help me set software updater back to normal?

---

### Post by grahammechanical on 2024-06-28
Some information that may explain why you have a problem.

Every version of Ubuntu has its own repositories of software (also called sources) located at particular internet addresses. So, the repositories for Ubuntu 22.04 LTS are at different internet addresses to the manic (23.10) internet addresses.

Now, let us think about what happens when we click to do an online upgrade from one version of Ubuntu to another. The first thing that happens is those internet addresses get changed. You stopped the upgrade but your system now has the internet addresses for 23.10 (manic).

This is what I do not understand. You say that you are on an LTS version of Ubuntu. We can set Ubuntu to tell us when the next new version is available or when the next LTS version is available.

What is your system set up to be notified of? The next new version from 22.04 LTS would be 22.10 and not 23.10. The next new version from 23.04 would be 23.10. The next new LTS version from 22.04 LTS will be 24.04 LTS.

So, what version were you on? Please open Software & Updates> Updates tab and see what "Notify me of a new Ubuntu version" is set to. Also run:

```
cat /apt/sources.list
```

and see what internet addresses are listed there. I am on 24.10 (development version). This is one line of what I see when I run that command.

> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oracular-security main restricted

Regards

---

### Post by guiverc on 2024-06-28
You mention *mantic* (23.10) but actually didn't state what you were starting with; as us understanding your situation is necessary for us to provide meaningful advice.

Your package contained a clue in package detail, and it looks like you're using *jammy* or 22.04.

```

nautilus-share | 0.7.3-2ubuntu6  | jammy             | source, amd64, arm64, armhf, ppc64el, riscv64, s390x

```

But nautilus is a GNOME app, are you put this is the Lubuntu section? where pcmanfm-qt is the expected app for a LXQt or Lubuntu environment.

Upgrades from 22.04 to 24.04 are **NOT** yet open, the date listed in the release announcements for both Ubuntu & Lubuntu was 15 August 2024 for release of 24.04.1 which was mentioned as occurring **before**the upgrade from 22.04 would open.  I wonder if you were attempting to *release-upgrade* thus from 22.04 to 23.10 ?  (*jammy to mantic*)

If an upgrade has started, and is cancelled, you're usually in a mess IF package installs have started installing, and in my opinion you're better completing that *release-upgrade* than attempting to remain where you are (*unless you have backups to restore*).   If however you cancelled the upgrade **BEFORE**packages had started installing/upgrading, or cancelled during the download packages stage - there will be no consequences at all to this cancel upgrade; and you only need to check your sources are correct & all should be good.

I'd suggest viewing your sources, ie. a `sudo apt update` OR actually view sources & see what is there.  Work out what you're actually running, and please give us full details if you'd like meaningful and accurate advice. You don't want us guessing.

---

### Post by Jotaro on 2024-06-28
I decided now to try and restore a previous backup from 6/14/2024 to see if that can set everything back to the way it was. Though due to restoring EVERYTHING I cannot tell if its frozen, or just taking a long time. Gonna post to the replies after this.

---

### Post by Jotaro on 2024-06-28
So I tried "cat /apt/sources.list" and it says this:

cat: /apt/sources.list: No such file or directory

---

### Post by Jotaro on 2024-06-28
sudo apt update gave me this:

Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) mantic InRelease
Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) mantic-security InRelease
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) mantic-updates InRelease [127 kB]
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) mantic-backports InRelease
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) mantic-updates/main amd64 Packages [478 kB]
Fetched 605 kB in 1s (803 kB/s)   
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
852 packages can be upgraded. Run 'apt list --upgradable' to see them.

---

### Post by Jotaro on 2024-06-28
And yes I had accidentally had "Notify me of a new Ubuntu version" set to "anything" instead of only LTS releases. I changed it to LTS releases only now.

---

### Post by guiverc on 2024-06-28
> **Jotaro said:**
> So I tried "cat /apt/sources.list" and it says this:

cat: /apt/sources.list: No such file or directory

What you should have used is `cat /etc/apt/sources.list`  ... ie. you're missing the necessary /apt, thus you tried to view a different non-existent file.


Your sources do show *mantic* or 23.10, meaning they're not Ubuntu 22.04 LTS or Ubuntu 24.04 LTS sources, so no LTS shows in your sources.

You've still not said what you believe you were running, as your provided sources do match a 23.10 system, however your package in the first post showed *jammy* or 22.04, but you still haven't said what you believed you were using.

The 23.10 or *mantic* upgrade was intended for Ubuntu 23.04 users ([https://help.ubuntu.com/community/ManticUpgrades](https://help.ubuntu.com/community/ManticUpgrades)) so I'd like confirmation as to what you at least believe you were using, as nautilus package does not match *lunar* or 23.04.

I'll suggest not applying or installing any package currently IF you believe you were using a LTS, as your sources are for 23.10, and the warnings notices of its EOL are already out, ie. [https://fridge.ubuntu.com/2024/06/05/ubuntu-23-10-mantic-minotaur-reaches-end-of-life-on-july-11-2024/](https://fridge.ubuntu.com/2024/06/05/ubuntu-23-10-mantic-minotaur-reaches-end-of-life-on-july-11-2024/) which shows EOL on 11 July 2024.

---

### Post by Jotaro on 2024-06-28
Ok, so I looked up the version I am using, and its well bad:


No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 23.10
Release:        23.10
Codename:       mantic

So its moved me to mantic, even though I canceled it before it could finish. So what should I do now? I had canceled it because it stated something about xscreensaver and xlockscreen, saying that if I continued the update, it would lock me out of the computer. So there's no way for me to return to the LTS I was on before? ;(

---

### Post by Jotaro on 2024-06-28
So the restore backup I activated is still going, is it really gonna restore my computer back to before all this happened, or is this gonna mess up my computer even worse somehow?

---

### Post by Jotaro on 2024-06-28
I entered "cat /etc/apt/sources.list" exactly as you told me, and it gives me this:

# deb cdrom:[Lubuntu 17.10 _Artful Aardvark_ - Release amd64 (20180105)]/ artful main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) mantic main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) artful main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) mantic-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) artful-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) mantic universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) artful universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) mantic-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) artful-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) mantic multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) artful multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) mantic-updates multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) artful-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) mantic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) artful-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) mantic-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) artful-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) mantic-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) artful-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) mantic-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) artful-security multiverse

---

### Post by Jotaro on 2024-06-28
Ok so I just collected all my valuable files and placed them on another computer, and made a thumb drive into a startup disk for Lubuntu LTS. I'm still waiting on duplicity to finished apparently trying to restore my computer. Again either its taking a long time to restore the entire computer, or its just frozen in place, I cannot tell either way. All I can do is just leave backups program alone in the hopes it will resolve and finish, until then I guess I just won't turn my computer off. But if it just hasn't resolved by tomorrow night, I'm gonna go ahead and hit reboot in the hopes that it finished and just hadn't closed the window for some reason.

---

### Post by Jotaro on 2024-06-28
I'm going to bed, and i will just have to hope this all works out...

---

### Post by guiverc on 2024-06-28
This will be mostly fyi, and actually also details I've mentioned before.

- You can CANCEL an upgrade before it actually starts, or in the download process, as packages are downloaded prior to them being installed

- You should NOT CANCEL a *release-upgrade* once its started installing the newer packages, as you'll end up with a *broken* system that is partially your old release, and partially the newer release.   If you do cancel an upgrade at this stage, personally I think its best to just continue the upgrade process; so as least your system is in a stable state (ie. all the same release) which is whatever release you were upgrading to.

You've still not said what you believe you were running.  You do mention LTS, but as 23.10 is the intended upgrade path for 23.04 users; is that what you were using (*upgrade to 23.10 is the best option for sure if this is the case!!*) or you were using 22.04 LTS (*which will allow an upgrade to the next release, which currently is 23.10 as 22.10 & 23.04 are now EOL; thus upgrades from 22.04 to 23.10 are supported by your base Ubuntu system; this upgrade path gets full CI QA testing, but almost no QA testing by users on actual hardware*).

To continue an upgrade, do NOT login to a GUI (*the GUI should not be attempted until your upgrade is complete*), and you can just `sudo apt update` & ensure no errors are present, the `sudo apt full-upgrade` will generally allow a *release-upgrade* to complete; unless the CANCEL was made during a package install & thus its got a *corrupted package* position that needs to be fixed first; but you can usually just follow the advice given in that circumstance anyway (*ie. it'll usually suggest `apt -f install` etc*)

You've still not said what you were actually running; ie. 23.04 or 22.04? as yes we can see its at least currently a *mantic* or 23.10 system now.

---

### Post by Jotaro on 2024-06-30
Thank you for your help, I really mean that. I was on jammy 22.04 LTS before, and made the mistake of choosing to go to mantic, not aware that I was on LTS. And yes, I now have a half and half system like you said. I saved everything I care about on another computer, so if the worst happens I can be ready at least. I might just burn an iso of jammy onto a disc and do a new install with jammy maybe. Or is it better to do that with numbat instead?

---

### Post by guiverc on 2024-06-30
If it was me, and you have good backups... I'd try and continue the upgrade; as you're likely need to re-install *jammy* anyway, as reverting packages is a rather manual process; and I have no idea how many *mantic* packages upgraded & thus need to be reverted (*Debian/Ubuntu apt tools are intentionally forward only automatically*).

To continue... I'd boot your system, login to a text terminal, ensure `sudo apt update` looks correct without errors, then `sudo apt full-upgrade` and let the upgrade complete...   If you have any problems, I'd expect messages would give clues on fixing (`apt -f install` etc).

**As for re-install**, you do know you can *non-destructively  *re-install, I write about it at the following places

- [https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533](https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533)
- [https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743](https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743)  (*see the 'Install using Existing Partition' testcase*)

ie.   it's just an install without format, which causes a *repair* type of install to be triggered.

**As for which to re-install**, that will depend on a number of things, which I'll just comment about

- Ubuntu 22.04 LTS is supported until 2027-April in *standard* support (5 years), Lubuntu however only provides support until 2025-April (3 years)
- Ubuntu 24.04 LTS is supported until 2029-April in *standard* support (5 years), Lubuntu is supported until 2027-April (3 years); thus has longer support remaining...
- (I'm ignoring ESM/Pro/legacy support options on purpose)

- consider your kernel, have you booted a 24.04 LTS system on your hardware in *live* mode, ie. the TRY LUBUNTU option???   Some older hardware (esp. GPU or graphics hardware) doesn't react well to newer kernels, thus using an older release can be beneficial

- If you re-install 22.04; which kernel stack were you using on your last install???  If using the GA kernel, the Lubuntu install media that used that will be rather hard to find I suspect as Ubuntu only keep the latest *flavor* ISOs, meaning on HWE kernel stack media will exist. Do you know what kernel you're using?  5.15 is the GA kernel of *jammy* or 22.04, but if using HWE *jammy*/22.04 was using the 6.5 kernel from 23.10..   Yes kernel stack can be changed post-install, but you may not yet have booted into the 6.5 kernel of 23.10 yet, and your re-install of *jammy*/22.04 maybe your first boot into that kernel stack and be a very different experience if your 22.04 used GA. With *flavors* like Lubuntu, the install media sets the default, and the mention of *artful* in an earlier post make me think you were using the GA kernel stack! but I don't know what changes you actually made, thus don't know what you're actually using.

---

### Post by Jotaro on 2024-06-30
I don't know how to check what kernal stack I have now. "install without format which causes a repair type install to be triggered" Could I use this to go back to jammy LTS? And if so, what would the steps be? I don't have anything like a backup partition though, just all my important stuff saved on a separate computer. So now I will burn iso image for 24.4 LTS onto a 650mb rewrite-able disc (hopefully that works) then try that disc out and try "Try Lubuntu" option to see how the compatibility looks.

---

### Post by Jotaro on 2024-06-30
Would this be a good disc to burn a Lubuntu 22.04 or Lubuntu 24.04 onto?
[https://www.amazon.com/gp/product/B0001XX0NU/ref=ox_sc_act_title_1?smid=ATVPDKIKX0DER&psc=1](https://www.amazon.com/gp/product/B0001XX0NU/ref=ox_sc_act_title_1?smid=ATVPDKIKX0DER&psc=1)

---

### Post by guiverc on 2024-06-30
Ubuntu hasn't aimed itself on DVD or *optical* media since 20.04, so I'd use thumb-drive.

Due to users having problems with bad writes on USB thumb-drives or flash media; the OS now checks the media for problems & reports that automatically as a background process. Users of thumb-drives rarely notice this as it takes only a few minutes with it run in the background.

That check can take >60 mins on *optical* media and can be noticed!  Further some apps can get *timeouts* due to the background checking occurring, with the *timeouts* being wrongly reported as different errors because the apps running don't expect or check for media-slow condition.  If you'll have problems with *optical* (DVD) I won't know, newer hardware is often faster & performs better, but on drives that are 8+ years old you can expect problems, so I'd avoid it.

You'll find mention of *optical* media here on the Lubuntu discourse ( [https://discourse.lubuntu.me/t/bug-failed-snap-daemon-in-lubuntu-22-04-lts-no-firefox-help-please/3246](https://discourse.lubuntu.me/t/bug-failed-snap-daemon-in-lubuntu-22-04-lts-no-firefox-help-please/3246) ) which includes some replies in the thread by me...   and I'd just use a thumb-drive.  I personally find the SanDisk brand the best, but all of them will fail; they're still good value for money though.

---

### Post by Jotaro on 2024-06-30
Well then I have a problem, I used startup disk creator on a 64gb sandisk thumbdrive, it "seemed" to work, but when I attempt to boot to it, it simply won't boot to any usb drive at all. My computer is an ASUS, I use the button prompt to enter boot menu, even select the thumb drive, force boot, and it doesn't work, it goes completely ignored. So if I can't use optical media, and my computer won't boot from this 64gb usb drive, what do I do? Is there a way I can format the usb thumb drive on this system, then turn it into a launch drive, then attempt to boot from it?

---

### Post by guiverc on 2024-07-01
To write an ISO to thumb-drive, you can just `dd` it to the device, ie.

```

sudo dd bs=4M oflag=sync status=progress of=/dev/sdb if=/de2900/lubuntu_64/hirsute-desktop-amd64.iso

```


(*that's an old example; but the latest actual command I could find where I used `dd`; as I mostly use mkusb to write ISOs, or more recently use a Ventoy setup thumbdrive; mkusb just does some checks to ensure you're not destroying incorrect drives before it does the dd command*)

I'll check using `sudo blkid` etc. to ensure the device is mounted on the machine I'm doing the `dd` too first... but I stopped using `dd` after overwriting a backup drive in error, THEN overwriting a server disk array the following week... 

I wasn't saying you can't use *optical* or DVD media; just that I'd not recommend it.. If you use it, I'd not start the install until you've verified the media check has completed (*which can take more than an hour on a couple of my machines*), and then don't push the install. I've had successful installs from *optical* media for 22.04 & maybe 22.10, but I no longer use it in QA unless someone reports a problem with it.

If interested in media checks; I'll provide a link to answer I wrote - [https://askubuntu.com/questions/1311183/do-i-need-to-check-the-integrity-of-a-ubuntu-install/1311209#1311209](https://askubuntu.com/questions/1311183/do-i-need-to-check-the-integrity-of-a-ubuntu-install/1311209#1311209)  ie. I don't start the install from *optical* media until I note the "Check finished: no errors found." message I mention in that answer.

---

### Post by Jotaro on 2024-07-01
Well, a miracle has happened, with no explanation. So I woke up and turned the computer on today when, at launch, the updater actually showed up and worked, and gave me the option to finish the upgrade. Since I moved everything over to a laptop anyways, I chose yes. Even better, it didn't lock me out of the computer like it said it was going to last time. So I am now fully on Mantic Minotaur. And now the update to Ubuntu 24.04 LTS has shown up, and its asking if I want to upgrade to it or not. I thought it was Lubuntu 24.04 LTS? Are they the same or different? Again, thank you so much for your help, I really mean it, I'm sorry I seem like such an uneducated person. You made a good point on using "Try Lubuntu" to check if my graphics card can handle 24.04, but now its asking if I want to just go ahead and upgrade to it anyways? Is there a way I can test it out first?

---

### Post by guiverc on 2024-07-01
> **Jotaro said:**
> So I am now fully on Mantic Minotaur. And now the update to Ubuntu 24.04 LTS has shown up, and its asking if I want to upgrade to it or not. I thought it was Lubuntu 24.04 LTS? Are they the same or different?

Ubuntu 23.10 is *mantic minotaur*, ie.

- [https://fridge.ubuntu.com/2023/10/16/ubuntu-23-10-mantic-minotaur-released/](https://fridge.ubuntu.com/2023/10/16/ubuntu-23-10-mantic-minotaur-released/) or "*Ubuntu 23.10 (Mantic Minotaur) released*"
- [https://lubuntu.me/mantic-released/](https://lubuntu.me/mantic-released/)

and yes it's very close to its EOL

- [https://fridge.ubuntu.com/2024/06/05/ubuntu-23-10-mantic-minotaur-reaches-end-of-life-on-july-11-2024/](https://fridge.ubuntu.com/2024/06/05/ubuntu-23-10-mantic-minotaur-reaches-end-of-life-on-july-11-2024/) or "*Ubuntu 23.10 (Mantic Minotaur) reaches End of Life on July 11, 2024*"
- [https://discourse.lubuntu.me/t/lubuntu-23-10-is-approaching-its-end-of-life-11-july-2024/4979](https://discourse.lubuntu.me/t/lubuntu-23-10-is-approaching-its-end-of-life-11-july-2024/4979)

[Ubuntu 24.04 LTS is *noble numbat *]("https://fridge.ubuntu.com/2024/04/25/ubuntu-24-04-lts-noble-numbat-released/")and as you'll find in that link I provided (*as well as official release notes & elsewhere*)

> 
Users of 22.04 LTS will be offered the automatic upgrade when 24.04.1  LTS is released, which is scheduled for the 15th of August.


with the only upgrade currently open for 22.04 users being to 23.10, or what you actually opted to use (*knowingly or not*).

> **Jotaro said:**
> I'm sorry I seem like such an uneducated person. You made a good  point on using "Try Lubuntu" to check if my graphics card can handle  24.04, but now its asking if I want to just go ahead and upgrade to it  anyways? Is there a way I can test it out first?

There is no need to apologize... Computer systems are complex, and take time to master. Worse they keep changing, so we never master everything, and besides we all start at some time, and hopefully learn.

If I was in your position, I'd not *release-upgrade* to 24.04 straight away, but use your system a few days and ensure everything is as you want it to be.  Once you're happy, I'd make additional backups, then plan for when you're going to *release-upgrade* to 24.04.

I'll provide the Lubuntu 24.04 Release blog link  ( [https://lubuntu.me/noble-released/](https://lubuntu.me/noble-released/) ) which I'd read prior to *release-upgrading* to it, esp. known bugs section & see if they'll likely impact your hardware. I'd also then read the Common Release Notes, as *flavors* like us at Lubuntu don't replicate all detail in that report but provide links to it.

Yes I'd download & write the 24.04 ISO to thumb-drive, and [*live* test it]("https://ubuntu.com/tutorials/try-ubuntu-before-you-install") (ie. no install, just using the TRY mode so you can TEST it out on your hardware..  I doubt you'll have any issues with the Lubuntu packages, but hardware can always react differently to different kernel stacks; 22.04 used 5.15 & 6.5, 23.10 used 6.5, where 24.04 currently uses 6.8 only.. ie. its newer than prior releases... The kernel packages are common to all Ubuntu systems, thus the most detail on this will have come from the *Common Release Notes* I mentioned earlier, but using it *live* allows you to see for yourself how it'll act on your hardware...  

If all looks good on the *LIVE* or *TRY* boot(s), then you can boot into your actual 23.10 system, and after ensuring you have good backups, perform the *release-upgrade*. The page on do that was mentioned in the Lubuntu 24.04 LTS Released page, but is [https://manual.lubuntu.me/stable/D/upgrading.html](https://manual.lubuntu.me/stable/D/upgrading.html) though I'd also scan the *[Common Ubuntu upgrade instructions link]("https://help.ubuntu.com/community/NobleUpgrades/") too *(*that page will provide the least detail of the links I've provided** as its details were already covered in prior links I used, but worth scanning to ensure you didn't miss anything*).

That is what I'd do anyway.

---

### Post by Jotaro on 2024-07-01
How do I make sure to have "good backups", because I had tried using restore with deja dup and it wouldn't work. I think I might wait till I can buy those optical discs I showed you on amazon through that link, then burn the iso image for 24.04LTS onto it, and try that for trying it live. And make sure the media check clears too. Only issue is this is gonna be a bit after July 11. Is it ok to go for a while after that date on Mantic Minotaur? Or should I treat it like an emergency and make sure to go ahead with the update as soon as possible? I only use this computer for watching videos on the web and checking emails, not for downloading anything, so would I be safe for a bit? Or is that too dangerous?

---

### Post by guiverc on 2024-07-02
> **Jotaro said:**
> Only issue is this is gonna be a bit after July 11. Is it ok to go for a while after that date on Mantic Minotaur? Or should I treat it like an emergency and make sure to go ahead with the update as soon as possible? I only use this computer for watching videos on the web and checking emails, not for downloading anything, so would I be safe for a bit? Or is that too dangerous?

I'll provide ***my opinion***** **here only.. 

After a release goes EOL, no warning notices of CVE/problems etc are provided ([https://ubuntu.com/security/notices?order=newest&release=mantic&details=](https://ubuntu.com/security/notices?order=newest&release=mantic&details=) will not show new problems) thus you won't know of what risks you're adding on.  These risks will grow as time progresses.

You'll likely discover some packages still update; eg. *firefox* is a *snap* package on 23.10, thus it may continue to upgrade, and a lot of what people do will be within browsers, thus some updates & risk will not accrue, however this will only continue for a time.. eg. as you won't be getting *deb* package upgrades, sooner or later the *snap* packages will become out of sync with your *deb* base system and thus *snap* packages may stop working, or no longer update.  There is a risk you may not notice this too.

If your machine is used as a server, always online 24/7 the risk is far greater than say a normal desktop that's used an hour or more a day, often at random intervals..

I'd not use that machine for *banking* or anything really important after EOL, but the risk would be minimal a few days after, but grows over weeks and then months.  Risks don't just impact the machine itself, but it could be used as an *attack vector* for other machines in your network; so using an EOL release also impacts those around you.

If I turned on a machine and say my purpose of it was just to have a video play from youtube whilst I perform a task I do daily for ~30 minutes & discovered that machine hadn't been upgraded from say 22.10... I can't see myself looking for another machine to use in its place; I'm pretty certain I'd not be worried about the risk of *watching a video* on an EOL device streaming from the internet; but I'd consider what data existed on that machine (*should someone hack their way in**; even if I consider that unlikely, being EOL I can't know what its vulnerable to) *and almost certainly use it. If I was going to login to some accounts for personal/private reasons (health etc), or something such as banking, I'd not do it on that device.

---

### Post by guiverc on 2024-07-02
Sorry I forgot to write about *ensuring you have good backups*.

I don't feel qualified to actually help there sorry. I don't use *deja dup* or any of the normal backup tools, so anything I'd say won't likely help.

Myself, I just backup files using `rsync` and basically copy files to other drives/devices. Less than an hour ago I turned off a machine that runs a script job (*it ran overnight*) and updated a backup of files on a server of mine to an external HDD.. ie. I just ensure I have multiple copies of whatever I consider important, and rely on me re-creating a system in case it gets destroyed...

FYI:  The server that I backed up I accidentally wiped myself (*in error!*) a couple of years ago using the `dd` command I mentioned in a prior message of mine... I didn't realize my terminal was logged into that device, and thus wrote an ISO to what I expected was a thumb-drive, but was instead an ~11TB array which was very quickly gone... I knew I didn't have backups of everything on that disk array, but still formatted it & started again... I restored ~8TB from the backups i did have being the stuff I didn't want to lose, the rest was just gone.  Myself I assume I'm going to destroy whatever (*or the disks will fail etc*), and thus have thought thru what data is important, and how I would get that back... My 'backup strategy' isn't ideal (*cost prevents me buying newer/larger drives, so I have data spread across older/smaller drives*) but I have multiple copies in a simple format (ie. simple copies) to a point where I can consider I can re-create data.

I don't actually backup my desktop itself, only data I consider of value.  As I perform QA test installs regularly; now and again I'll copy configs to a new install so I can use it for a day instead of my primary (and setup) machine (*Quality Assurance testing purposes*).. so I'm somewhat accustomed to re-creating a new desktop as I need in 5-10 minutes. I don't consider I have a good backup strategy, as I just rebuilt whatever I need from my copies..

---

### Post by Jotaro on 2024-07-02
Well I decided to click "apply upgrade" and it loaded very little and then said "full upgrade completed" and clearly didn't work. So what can I do? I checked the software updater, and it says I can upgrade, but when I click that its the same thing, no upgrade, it just downloads very little, and says "upgrade finished"

So I tried sudo apt update and got some stuff to show up, saying there are 9 packages that can be upgraded, and to use apt list --upgradable to see them, so I did that and the terminal gave me this:

apt list --upgradable
Listing... Done
frei0r-plugins/mantic 1.8.0-1build1 amd64 [upgradable from: 1.7.0-2build1]
grub-common/mantic-updates 2.12~rc1-10ubuntu4.2 amd64 [upgradable from: 2.12~rc1-10ubuntu4]
grub-pc-bin/mantic-updates 2.12~rc1-10ubuntu4.2 amd64 [upgradable from: 2.12~rc1-10ubuntu4]
grub-pc/mantic-updates 2.12~rc1-10ubuntu4.2 amd64 [upgradable from: 2.12~rc1-10ubuntu4]
grub2-common/mantic-updates 2.12~rc1-10ubuntu4.2 amd64 [upgradable from: 2.12~rc1-10ubuntu4]
libmlt++7/mantic 7.18.0-1 amd64 [upgradable from: 7.4.0-1build1]
libmlt7/mantic 7.18.0-1 amd64 [upgradable from: 7.4.0-1build1]
lubuntu-desktop/mantic 23.10.2 amd64 [upgradable from: 22.04.3]
melt/mantic 7.18.0-1 amd64 [upgradable from: 7.4.0-1build1]

---

### Post by Jotaro on 2024-07-02
So now I tried sudo apt upgrade to upgrade those nine packages, and this is what I got:

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  apturl apturl-common attr breeze catdoc
  chromium-codecs-ffmpeg-extra endeavour endeavour-common g++-11
  gcc-12-base:i386 gdal-data gdal-plugins gdisk gedit gedit-common
  gir1.2-gtksource-4 gir1.2-gweather-3.0 gir1.2-nma-1.0
  gir1.2-snapd-1 gnome-bluetooth gnome-bluetooth-common gnome-todo
  guile-2.2-libs haveged ibverbs-providers kdenlive-data
  kwin-style-breeze libabsl20210324 libaec0 libamd2 libamtk-5-0
  libamtk-5-common libappimage0 libappimage1.0abi1 libarmadillo10
  libarmadillo11 libarpack2 libavcodec58 libavdevice58 libavfilter7
  libavformat58 libavutil56 libblockdev-crypto2 libblockdev-fs2
  libblockdev-loop2 libblockdev-part-err2 libblockdev-part2
  libblockdev-swap2 libblockdev-utils2 libblockdev2 libblosc1
  libbpf0 libcamd2 libcamel-1.2-63 libccolamd2 libcephfs2
  libcfitsio10 libcfitsio9 libcharls2 libcholmod3 libcodec2-1.0
  libcolamd2 libcolord-gtk1 libdav1d5 libdazzle-1.0-0
  libdazzle-common libdmapsharing-3.0-2 libdns-export1110
  libebackend-1.2-10 libebook-1.2-20 libebook-contacts-1.2-3
  libebur128-1 libecal-2.0-1 libedata-book-1.2-26 libedata-cal-2.0-1
  libedataserver-1.2-26 libedataserverui-1.2-3 libepub0
  libexporter-tiny-perl libflac++6v5 libfreexl1 libfyba0 libgdal30
  libgdal33 libgdcm3.0 libgeocode-glib0 libgeos-c1v5 libgeos3.10.2
  libgeos3.12.0 libgeotiff5 libgfapi0 libgfrpc0 libgfxdr0
  libglusterfs0 libgnome-bluetooth13 libgnome-todo libgweather-3-16
  libgweather-common libhavege2 libhdf4-0-alt libhdf5-103-1
  libhdf5-hl-100 libhwloc-plugins libhwloc15 libibverbs1 libicu70
  libilmbase25 libio-prompt-tiny-perl libisc-export1105 libixml10
  libjte2 libkdecorations2-5v5 libkdecorations2private10
  libkdecorations2private9 libkf5filemetadata-bin
  libkf5filemetadata-data libkf5filemetadata3 libkmlbase1 libkmldom1
  libkmlengine1 libldap-2.5-0 liblept5 liblist-moreutils-perl
  liblist-moreutils-xs-perl liblua5.3-0 libmediainfo0v5 libmetis5
  libmlt++7 libmlt-data libmlt7 libmovit8 libmozjs-91-0 libmpdec3
  libmpv1 libmujs1 libnetcdf19 libnetpbm10 libodbc2 libodbcinst2
  libogdi4.1 libopencv-calib3d4.5d libopencv-contrib4.5d
  libopencv-core4.5d libopencv-dnn4.5d libopencv-features2d4.5d
  libopencv-flann4.5d libopencv-highgui4.5d libopencv-imgcodecs4.5d
  libopencv-imgproc4.5d libopencv-ml4.5d libopencv-objdetect4.5d
  libopencv-video4.5d libopenexr25 libopenh264-6 liborcus-0.17-0
  liborcus-parser-0.17-0 libparted-fs-resize0 libplacebo192
  libpoppler118 libpostproc55 libprocps8 libproj22 libproj25
  libprotobuf-lite23 libprotobuf23 libpython3.10
  libpython3.10-minimal libpython3.10-stdlib libqhull-r8.0
  libqmobipocket2 libqpdf28 libqt5networkauth5 librados2 libraw20
  librdmacm1 libre2-9 libreoffice-pdfimport librtaudio6 librttopo1
  librygel-core-2.6-2 librygel-db-2.6-2 librygel-renderer-2.6-2
  librygel-server-2.6-2 libsnapd-glib1 libsnapd-qt1 libsocket++1
  libsox-fmt-alsa libsox-fmt-base libsox3 libspatialite7
  libspatialite8 libsquashfuse0 libsrt1.4-gnutls libstdc++-11-dev
  libsuitesparseconfig5 libsuperlu5 libsuperlu6 libswresample3
  libswscale5 libsz2 libtbbbind-2-5 libtepl-6-2 libtepl-common
  libtesseract4 libtesseract5 libtinyxml2-9 libumfpack5 libupnp13
  liburiparser1 libvncserver1 libwpe-1.0-1 libwpebackend-fdo-1.0-1
  libwxbase3.0-0v5 libwxgtk3.0-gtk3-0v5 libx264-163
  libxdgutilsbasedir1.0.1 libxdgutilsdesktopentry1.0.1
  libxerces-c3.2 libxnvctrl0 libzen0v5 libzxingcore1 mediainfo melt
  nautilus-share proj-bin proj-data python3-macaroonbakery
  python3-protobuf python3-pymacaroons python3-rfc3339 python3-tz
  python3.10 python3.10-minimal qtxdg-tools samba samba-ad-provision
  tdb-tools unixodbc-common youtube-dl
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  frei0r-plugins grub-common grub-pc grub-pc-bin grub2-common
  libmlt++7 libmlt7 lubuntu-desktop melt
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

So it says here at the end that it did NOT upgrade them, and I'm scared that if I do sudo apt autoremove it might break something. Is this right, and I can remove these, or not?

---

### Post by guiverc on 2024-07-02
> **Jotaro said:**
> Well I decided to click "apply upgrade" and it loaded very little and then said "full upgrade completed" and clearly didn't work. So what can I do? I checked the software updater, and it says I can upgrade, but when I click that its the same thing, no upgrade, it just downloads very little, and says "upgrade finished"

So I tried sudo apt update and got some stuff to show up, saying there are 9 packages that can be upgraded, and to use apt list --upgradable to see them, so I did that and the terminal gave me this:

apt list --upgradable
Listing... Done

lubuntu-desktop/mantic 23.10.2 amd64 [upgradable from: 22.04.3]


I quickly noted the 22.04.3 in the lubuntu-desktop package, meaning your system is still running Ubuntu 22.04 desktop.

You're not using the desktop or a GUI are you?  as your system has not completed it's upgrade.  I said in a prior post

> **guiverc said:**
> 
To continue an upgrade, do NOT login to a GUI (*the GUI should not be attempted until your upgrade is complete*), and you can just `sudo apt update` & ensure no errors are present, the `sudo apt full-upgrade` will generally allow a *release-upgrade* to complete; unless the CANCEL was made during a package install & thus its got a *corrupted package* position that needs to be fixed first; but you can usually just follow the advice given in that circumstance anyway (*ie. it'll usually suggest `apt -f install` etc*)


ie. you need to do all of this using only a basic terminal login, ie. boot & use Ctrl+Alt+F4 for example, to switch to a simple text terminal & complete your *release-upgrade* there.. As I stated you just follow instructions until you've got all packages installed using

- sudo apt update  (you need no warnings, errors etc)
- sudo apt full-upgrade  (this should complete with all packages installed)
- follow any other instructions it required  (`sudo apt -f install` etc as the output suggests)

If a specific package seems to be be prevented from upgrading, you can try and upgrade it using for example

> 
sudo apt upgrade lubuntu-desktop


where `lubuntu-desktop` will be multiple packages if multiple need to be done.  In my experience this usually works, however even if it doesn't work, it usually provides you with more detailed instructions as to what the problem is, and thus what you need to do in order to get the result we want.


Once all upgrades are done, you can reboot & login normally (ie. use a GUI or graphical login/session) to start the assessment of how the end result is.

The mention of a 22.04 package implies to me you're still not running Ubuntu 23.10, but a *frakensystem (broken system) *that is part 22.04 & part 23.10 due to the cancelled *release-upgrade*.  You need to get the *release-upgrade* to complete, before you can move on.

---

### Post by Jotaro on 2024-07-02
I don't understand what "login to a GUI" means. The steps that happen when I turn on my computer are, ASUS boot settings option, then a blue Lubuntu boot screen that will auto load the first option, I load the correct option, then some terminal stuff on a black screen, then "clean number of files", then the login screen where I type in my password and login, then the desktop loads. So are you suggesting what I need to do is, logout, and then do sudo apt upgrade lubuntu-desktop? I just want to check this before I do it.

---

### Post by Jotaro on 2024-07-02
Hey so I have some great news. So I was fiddling around with booting a USB stick with 24.04, and I figured out why it didn't seem to be booting...it was strangely hidden. So on my list of "boot" options, it would list the jammy I have on a 128GBSSD, my main one, and a third ubuntu option titled "Ubuntu Sandisk Drive", and since I don't have a third one, I assumed this was the bootable, but when I tried, it wouldn't work and would go ignored. Well, all the way down the list, past all that, there was a final option I never even looked for, "UEFI Ubuntu Sandisk Drive" So, I tried that and, bingo, it worked. So I picked Try 24.04, and boom and it worked too. So I bit the bullet and erased everything and installed 24.04LTS. I'm on it now, and so far, it seems fine. Although, now one of the screens while going through boot has some fuzzy stuff on the top of it, but it still correctly boots to my desktop, so I should be fine I think?

---

### Post by guiverc on 2024-07-02
> **Jotaro said:**
> I don't understand what "login to a GUI" means. The steps that happen when I turn on my computer are, ASUS boot settings option, then a blue Lubuntu boot screen that will auto load the first option, I load the correct option, then some terminal stuff on a black screen, then "clean number of files", then the login screen where I type in my password and login, then the desktop loads. So are you suggesting what I need to do is, logout, and then do sudo apt upgrade lubuntu-desktop? I just want to check this before I do it.

The GUI is the *graphics user interface*, and by no GUI I'm meaning restrict yourself to the *text user interface*.

When you get to the *greeter* or DM (ie. where you login), you do NOT login there, as that will log you into a *graphical session* depending on which you have selected; you may not have noticed it, but there is capability in `sddm` or the DM that Lubuntu uses to pick other sessions you have installed; Lubuntu comes with a Lubuntu session (*all our configs; what [our manual relates to]("https://manual.lubuntu.me/stable/")*), a LXQt session (*purer upstream session without changes made by Lubuntu team*), Openbox (WM alone, *lighter environment without the panel & other features function, ie. no desktop just window manager*) etc.

At the greeter/DM or login screen, you tell your machine to switch to a text terminal..  my example being CTRL + ALT + F4, where you can login using a terminal like interface just like you're using a server system.  I was suggesting logging in there & running the upgrades & installs from there..   When you've got all `apt full-upgrade` functional, I'd just reboot & THEN attempt to login normally (ie. entering your password into the greeter/login screen).

---

