---
title: "I thought 14.04 was supported for 5 years so why am I getting HWE stack message?"
date: 2016-08-18
forum: General Help
---

### Post by bullwinkle2 on 2016-08-18
Tonight I got a popup on my machines that says:

[INDENT]**New important security and hardware support update.**

WARNING: Security updates for your current Hardware Enablement Stack ended on 2016&#8211;08&#8211;04:
* [https://wiki.ubuntu.com/1404_HWE_EOL](https://wiki.ubuntu.com/1404_HWE_EOL)
[/INDENT]

**EDIT:** I forgot to mention that there are also three buttons on this popup: "Settings", "Install", and "OK".  But there is no indication whatsoever of what exactly the "Install" button is going to install.

I thought 14.04 was supported for five years, and it looks like this is trying to force me to upgrade to 16.04 or else not get kernel security update.  I DO NOT wish to upgrade to 16.04 at this time for a couple of reasons, first I have seen too many reports of people having problems after an upgrade, but more important I am running an older version of Kodi and I do NOT want to be forced to upgrade that because it has some bugs I don't want to deal with.

I really don't understand what the link above is telling me but it sure looks like Ubuntu is for all intents and purposes abandoning a LTS version after only two years and a few months.  AND doing so with no advance warning at all.  This really sucks in my opinion.

Am I missing something?  Is there a way to stay with 14.04 and continue to receive security updates?  I don't care about getting newer kernel versions necessarily, but what's the point of having an LTS release that's supposed to be supported for five years if you stop offering security updates after two years?  I might be willing to install 16.04 in another year or so (I generally never install the first version of a Ubuntu LTS release anyway) but first I want to wait for Kodi to release a new version that doesn't have the bugs of Jarvis (the current version) in it.  And, I'd rather not be forced to do ii in a big all-fired hurry because you decided to end support with no advance warning (in fact the warning came two weeks AFTER the updates ended, according to the popup message).

**THIS REALLY SUCKS IN MY OPINION!!!**  Either there should be a way to just update the "Hardware Enablement Stack", whatever that is, or you should stop telling users that LTS versions will be supported for five years.  And if there IS a way to just update the "Hardware Enablement Stack" then your link above should clearly offer that as an option.  I **hope** I am just missing something here, and that you are not effectively forcing user to upgrade 14.04 now or run an insecure system.

---

### Post by oldfred on 2016-08-19
If you keep the original 14.04 it is supported until 2019.
Once you start using the HWE, you have to keep updating it until you get to 14.04.5 and then 14.04.5 is supported until 2019. 
But the interim HWE are not supported.

That is what the link you have above says.

You may also be getting notices that you can update to 16.04, but that is optional. 

I have always done a new clean install of next LTS keeping old one. My two / (root) partitions (14.04 will become 18.04) will be alternated if I still have same SSD as boot drive.

---

### Post by mastablasta on 2016-08-19
HWE stack is bringing kernels from new releases (e.g. 14.10, 15.04, 15.10...) to 14.04 LTS. drivers in linux are part of kernels, so to have new PCs from say this year work with OS from 2014 you need to upgrade the kernel. the programs will stay the same though. that way one can install old LTS to new PC or upgrade the PC and stay on old LTS.

in this particular case upgrading kernel shouldn't change much for you unless you are using AMD and fglrx driver (proprietary driver) which i think can't yet (not sure if it ever will) patch the kernel in 14.04.5. instead it get's replaced by latest Radeon (opensource driver). if you are using nvidia or intel GPU then this is not an issue at all. you will just get latest stable drivers.

---

### Post by bullwinkle2 on 2016-08-19
> **oldfred said:**
> If you keep the original 14.04 it is supported until 2019.
Once you start using the HWE, you have to keep updating it until you get to 14.04.5 and then 14.04.5 is supported until 2019. 
But the interim HWE are not supported.

That is what the link you have above says.

You may also be getting notices that you can update to 16.04, but that is optional. 

I have always done a new clean install of next LTS keeping old one. My two / (root) partitions (14.04 will become 18.04) will be alternated if I still have same SSD as boot drive.

I don't even know what HWE is.

I just installed plain old Ubuntu Desktop 14.04, as far as I knew.  And then every time Update Manager offered an update, I let it install.  I never did anything to "start using the HWE" because I would not have had any reason to do so.

So then my next question is, if going to 14.04.5 solves the problem, why am I getting this message when I **already** have Ubuntu 14.04.5 LTS, according to "lsb_release -a"?

[INDENT]$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty
[/INDENT]

Also, going back to that original popup that I mentioned in my first post, I forgot to mention there are three buttons on it, "Settings", "Install", and "OK".  But it gives you no clue what you will get if you click "Install" - will that attempt to upgrade you to 16.04?  Why would there be an "Install" button with no clues as to what you are actually about to install?  I don't want to click it to find out, because I fear it will just go ahead and attempt to install 16.04 without first asking if that's what I want to do.

> **mastablasta said:**
> HWE stack is bringing kernels from new releases (e.g. 14.10, 15.04, 15.10...) to 14.04 LTS. drivers in linux are part of kernels, so to have new PCs from say this year work with OS from 2014 you need to upgrade the kernel. the programs will stay the same though. that way one can install old LTS to new PC or upgrade the PC and stay on old LTS.

in this particular case upgrading kernel shouldn't change much for you unless you are using AMD and fglrx driver (proprietary driver) which i think can't yet (not sure if it ever will) patch the kernel in 14.04.5. instead it get's replaced by latest Radeon (opensource driver). if you are using nvidia or intel GPU then this is not an issue at all. you will just get latest stable drivers.

I am NOT using AMD and fglrx driver.  But the way that referenced page reads, I won't get any kernel updates anymore:

[INDENT][B]And why should I care?
[/B]
Starting  Aug 4, 2016, systems using an interim HWE Stack older than the Xenial  HWE Stack will no longer receive software updates for the kernel and, if  you're running it, the graphics stack.  We encourage all Ubuntu 14.04  HWE Stack users to update to the final Ubuntu 16.04 Xenial HWE Stack or  fully upgrade to the Ubuntu 16.04 LTS release.
[/INDENT]
 
So while you are saying that "upgrading kernel shouldn't change much for you", according to that there will be a huge change in that I won't get any more updates (presumably including security updates)!

So either someone did a very poor job of communicating the real situation through that popup and the web page linked from it, in which case I'd like to see the page updated with correct information, or they really are abandoning support of 14.04 prematurely.

I want to emphasize again that I did ABSOLUTELY NOTHING to proactively install a HWE stack, because I had no idea such a thing existed and still have no clue why you'd need one (nor do I really care to know).  I just installed Ubuntu using the standard download.  The page seems to imply that there are two versions of  Ubuntu (for example, in the FAQ at the bottom it says "14.04.3 is not 14.04.3 HWE") but I did not select a HWE version.  So I am totally confused as to why I'm getting this popup in the first place.

---

### Post by howefield on 2016-08-19
> **bullwinkle2 said:**
> So then my next question is, if going to 14.04.5 solves the problem, why am I getting this message when I **already** have Ubuntu 14.04.5 LTS, according to "lsb_release -a"?

[INDENT]$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty
[/INDENT]

What is the output of 

```
uname -a
```

No matter which 14.04 installation media you used, whether it be the original 14.04 release or any of the point releases, applying the updates will take it to 14.04.5. The difference is the kernel which will stay on the "series" from the install media (or HWE stack which includes X support as well). So being on 14.04.5 doesn't necessarily that you are on a  supported kernel/X.

---

### Post by bullwinkle2 on 2016-08-19
> **howefield said:**
> What is the output of 

```
uname -a
```

uname -a shows this on the affected systems, the only thing that differs is the *machinename* and the current time:

Linux *machinename* 3.19.0-66-generic #74~14.04.1-Ubuntu SMP Tue Jul 19 19:56:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

> **howefield said:**
> No matter which 14.04 installation media you used, whether it be the  original 14.04 release or any of the point releases, applying the  updates will take it to 14.04.5. The difference is the kernel which will  stay on the "series" from the install media (or HWE stack which  includes X support as well). So being on 14.04.5 doesn't necessarily  that you are on a  supported kernel/X.

Again, I don't understand what you're trying to tell me here.  All I know is I installed it using the normal Ubuntu install file which was saved to a bootable thumb drive.

The only thing really I want to know right now is, what do I have to do, if anything, **to continue to get kernel security updates** without upgrading to 16.04.  That is the thing that concerns me most.  I don't want to upgrade; that's why I used a LTS version, but I also don't want to leave my systems insecure.  And I am not a Linux expert by any means, that's why I installed Ubuntu.

---

### Post by howefield on 2016-08-19
According to what you have written above, it would appear that you installed with the 14.04.3 image which has that kernel series.

Although normal updates will take you to 14.04.5 in all other respects, your kernel is no longer supported, see..

[http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life)

and scroll down the page to the section entitled "*Kernel release end of life*". Note that the 3.19 series is end of life right about now.

---

### Post by mc4man on 2016-08-19
> **bullwinkle2 said:**
> uname -a shows this on the affected systems, the only thing that differs is the *machinename* and the current time:

Linux *machinename* 3.19.0-66-generic #74~14.04.1-Ubuntu SMP Tue Jul 19 19:56:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux



Again, I don't understand what you're trying to tell me here.  All I know is I installed it using the normal Ubuntu install file which was saved to a bootable thumb drive.

The only thing really I want to know right now is, what do I have to do, if anything, **to continue to get kernel security updates** without upgrading to 16.04.  That is the thing that concerns me most.  I don't want to upgrade; that's why I used an LTS version, but I also don't want to leave my systems insecure.  And I am not a Linux expert by any means, that's why I installed Ubuntu.
Your _installation image_ was 14.04.3, i.e. lts~vivid (In other words 14.04 with the vivid 15.04 kernel & mesa libraries
So there will be no more updates to the 3.19 kernel as 15.04 is EOL (end of life

Unfortunately Ubuntu doesn't make that clear before installation &  give users the opportunity to use the original image for installation instead.  The HWE deal is somewhat described here - [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Myself also have a 14.04.3 image installation & will not be upgrading to the final lts (lts~xenial) as the kernel causes my hardware issues & the newer mesa libraries also. I'm not that concerned about kernel updates for what's generally obscure issues.

If you want full 5 yr. kernel support then you'd need to upgrade to the final lts (lts~xenial) or start over & use the 14.04.1 installation image, found here half way down the page (ones showing a last modified on July 22, 2014
[http://old-releases.ubuntu.com/releases/14.04.1/](http://old-releases.ubuntu.com/releases/14.04.1/)
That kernel (3.13.x) is fully supported for 5 years

---

### Post by mastablasta on 2016-08-19
> **bullwinkle2 said:**
> 
The only thing really I want to know right now is, what do I have to do, if anything, **to continue to get kernel security updates** without upgrading to 16.04.  That is the thing that concerns me most.  I don't want to upgrade; that's why I used a LTS version, but I also don't want to leave my systems insecure.  And I am not a Linux expert by any means, that's why I installed Ubuntu.

HWE stack is hardware enablement stack. i though i explained how it works. but again in short it is there to enable new hardware to work with old LTS.

to upgrade the kernel only you need to copy and paste a few commands (depending on how you have it installed):

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

> [h=3]Ubuntu 14.04 LTS - Trusty Tahr[/h]
The 14.04.2 and newer point releases will ship with an updated kernel and X stack by default. If you have installed with older media you can use the following to install the newer HWE kernel derived from 16.04 (Xenial): 
[h=4]Desktop[/h]```
sudo apt-get install --install-recommends linux-generic-lts-xenial xserver-xorg-core-lts-xenial xserver-xorg-lts-xenial xserver-xorg-video-all-lts-xenial xserver-xorg-input-all-lts-xenial libwayland-egl1-mesa-lts-xenial  

```
[h=4]Multiarch Desktop[/h]If you run a multiarch desktop (for example, i386 and amd64 on amd64, for gaming or Wine), you may find you need a slightly more involved command, like this: 
```
sudo apt-get install --install-recommends linux-generic-lts-xenial xserver-xorg-core-lts-xenial xserver-xorg-lts-xenial xserver-xorg-video-all-lts-xenial xserver-xorg-input-all-lts-xenial libwayland-egl1-mesa-lts-xenial libgl1-mesa-glx-lts-xenial libgl1-mesa-glx-lts-xenial:i386 libglapi-mesa-lts-xenial:i386
```  


---

### Post by bullwinkle2 on 2016-08-19
> **howefield said:**
> According to what you have written above, it would appear that you installed with the 14.04.3 image which has that kernel series.

Although normal updates will take you to 14.04.5 in all other respects, your kernel is no longer supported, see..

[http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life)

and scroll down the page to the section entitled "*Kernel release end of life*". Note that the 3.19 series is end of life right about now.

I installed the version that was offered on the Ubuntu site.  This is what is really frustrating to me; people are acting like I made a conscious choice to use a version with a short kernel end of life.  **I did not.**  I simply took what was offered on the Ubuntu site as the current version.  But beyond that, I have 16.04.5 according to the output of the "lsb_release -a" so according to that chart, I should be good until sometime in 2020.  I have applied all the kernel updates that have been offered in Update Manager.  So **why** would I have a kernel that is no longer supported? (That's a rhetorical question; I probably would not understand the answer.)

What I hear you guys saying is that even though this is a "Long Term Support" release that is supposed to be supported for **five years**, depending on when I downloaded it, or on the position of the moon and stars, or whether a gnat sneezed, or some other unknown factor that I probably wouldn't understand if you tried to explain it to me, **somehow** I wound up with a version that was only supported for part of that five years.  I didn't **want** such a version, and would never have knowingly downloaded such a version, but that's what was offered on the Ubuntu site at some point in time.  And now, all people can tell me is that even though my version identifies as the current version when I run "lsb_release -a" (because I HAVE applied all the updates), somehow I'm stuck with this funky kernel, and what nobody's explaining so far is, "How do I upgrade that to the version that will last until the end of the five years?"

Seriously, it does not help me at all to get explanations for why this happened, particularly since I'm apparently not familiar enough with the guts of Linux to understand any of the ones that have been offered so far.  The only thing that's really going to be helpful is if someone can explain what I have to do now to get the **supported** kernel installed on these systems.  Which is really something that should be prominently featured on that web page I referenced in my first post, which right now basically only tries to get you to upgrade to 16.04.

---

### Post by bullwinkle2 on 2016-08-19
> **mastablasta said:**
> HWE stack is hardware enablement stack. i though i explained how it works. but again in short it is there to enable new hardware to work with old LTS.

to upgrade the kernel only you need to copy and paste a few commands (depending on how you have it installed):

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

THANK YOU!!!  So, just to be very clear, since these are standard desktop Ubuntu installs, all I have to do is run

```
sudo apt-get install --install-recommends linux-generic-lts-xenial xserver-xorg-core-lts-xenial xserver-xorg-lts-xenial xserver-xorg-video-all-lts-xenial xserver-xorg-input-all-lts-xenial libwayland-egl1-mesa-lts-xenial
```

And that will fix the problem and NOT upgrade my systems to 16.04?  If so, seems easy enough.  Might want to put that in something like a "quick fix" section right at the top of that page, so people who don't understand all the Linux expert talk won't have to wade through a discussion the mostly don't understand, trying to figure out what to do.

Please assure me this will NOT upgrade my 14.04 system to 16.04 and I will give it a try.  The only thing that's worrying me is all the references to "xenial" in that software.

---

### Post by bullwinkle2 on 2016-08-19
> **mc4man said:**
> Your _installation image_ was 14.04.3, i.e. lts~vivid (In other words 14.04 with the vivid 15.04 kernel & mesa libraries
So there will be no more updates to the 3.19 kernel as 15.04 is EOL (end of life

Unfortunately Ubuntu doesn't make that clear before installation &  give users the opportunity to use the original image for installation instead.

**THIS IS WHAT REALLY SUCKS.**  You think you are downloading a LTS version that should work (in all respects) for five years from the release of the original image.  And they don't tell you that what you are downloading is an image that won't be supported nearly that long.

  > **mc4man said:**
> The HWE deal is somewhat described here - [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Which is a page that most people trying to download Ubuntu would never know to look at, and even if they did, I suspect a fair number are like myself and would have no idea what that's all about.

> **mc4man said:**
> Myself also have a 14.04.3 image installation & will not be upgrading to the final lts (lts~xenial) as the kernel causes my hardware issues & the newer mesa libraries also. I'm not that concerned about kernel updates for what's generally obscure issues.

Are these hardware issues something that a lot of people are experiencing, or do you have some particularly funky hardware?  I have no idea what mesa libraries are, so I don't know whether I should be concerned or not.  These are all just basic commercial desktop machines with Intel processors and graphics (except for one older system that has nVidia graphics).  I am not concerned about kernel updates per se, in fact I'd be happy to never have to deal with them, but my fear has always been that if I don't apply them it will leave some security hole unpatched.  But, I do NOT want to do an upgrade that's going to break things!

All my systems are really used for is to run Kodi.  So, do you think I'd be likely to have problems if I do the upgrade suggested by mastablasta?

> **mc4man said:**
> If you want full 5 yr. kernel support then you'd need to upgrade to the final lts (lts~xenial) or start over & use the 14.04.1 installation image, found here half way down the page (ones showing a last modified on July 22, 2014
[http://old-releases.ubuntu.com/releases/14.04.1/](http://old-releases.ubuntu.com/releases/14.04.1/)
That kernel (3.13.x) is fully supported for 5 years

The reason I feel like I am between a rock and a hard place here is because if I do ANY type of reinstall, I'll have to re-download Kodi, and the repository no longer offers Isengard, which is the version I want because Jarvis has too many bugs (one particularly nasty one that would make life much less pleasant for me).  If it were not for that, I would probably be somewhat less reluctant to try 16.04.

This is the one thing I hate about most Linux distros - unlike in the Windows or Mac world, in most cases (Ubuntu itself being an exception), you can't save and keep using old versions of software that you know work.  You are stuck with whatever version is currently offered in the repository.  I know the Linux experts probably know ways around that, but I'm not one.  I have heard that SNAP packages (I think they are called) eliminate this problem but until all Linux software is distributed that way, we're stuck with whatever is currently on offer in the repositories if we decide to do a fresh reinstall of Ubuntu.

---

### Post by kansasnoob on 2016-08-19
There is an expectation that users will read the release notes. In the case of 14.04.3:

[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/14.04.3](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/14.04.3)

Then read the section about HWE:

[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/14.04.3#LTS_Hardware_Enablement_Stack](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/14.04.3#LTS_Hardware_Enablement_Stack)

That's why a link to the release notes is always prominently posted on the [main download page]("http://www.ubuntu.com/download/desktop"):

[ATTACH=CONFIG]270747[/ATTACH]

---

### Post by mc4man on 2016-08-19
> **bullwinkle2 said:**
> 



Are these hardware issues something that a lot of people are experiencing, or do you have some particularly funky hardware?  

The issue here is with the current lts kernel from xenial my wifi (intel on 3 yr. old lenovo laptop) gets disconnected every so often & then the router disappears from connection choices until I disable wifi, re-enable or log out/in. Never ever had an issue before with wifi on this machine. (see the same in 16.04 but at least there can go back to the 16.04 release kernel which is fine.

Mesa/xserver libs are display & video related, in 14.04 >14.04.3 the 10.x are used, in 14.04.5 the 11.x are used & in some area's are broken, particularly for nvidia optimus laptops. So for me on that laptop the best 14.04 is the 14.04.1 or 14.04.3 install images. 
One can upgrade just the kernel & not the mesa/xserver if desired.. At least with kernel if not happy one can just boot to older version & if desired remove the newer one. With the mesa/xserver libs there is no easy way to go back. (though not impossible

---

### Post by bullwinkle2 on 2016-08-19
> **kansasnoob said:**
> There is an expectation that users will read the release notes.

You might as well expect the sun to shine 365 days a year.  What you fail to realize is there is a big divide between, for want of a better term, geeks and non-geeks.  The geeks might read release notes and actually understand what they are reading.  But the typical user will never read release notes, because 99% of the time they are meaningless to him or her.  A typical user expects to be able to go to the current download link, download the operating system, install it, and get on with life, and if they download a LTS version they expect it to work for the full period of LTS support.

I really thought Ubuntu was supposed to be a distribution for everyone, not just for those able to decipher the hidden meanings in what they say, like when they use LTS to refer to a version that really isn't.  If Ubuntu were a commercial product, this would be a classic case of false advertising.  I am very, VERY disappointed with Ubuntu right now.

---

### Post by bullwinkle2 on 2016-08-19
Well I think I solved this on at least one of my systems - see my last message in the other thread at [https://ubuntuforums.org/showthread.php?t=2334450&p=13533288#post13533288](https://ubuntuforums.org/showthread.php?t=2334450&p=13533288#post13533288) - The upshot was that clicking "Install" in that popup box gave me an error the first time I tried it, but for some reason a subsequent attempt worked.  If it doesn't prompt you to enter your password, it probably won't work, but if you keep trying maybe it eventually will.  I'm not marking this "solved" yet because I don't consider blind luck to be a real solution, and I really think it was pretty <snip> of the Ubuntu developers to put us users (those of us who are not certified Linux geeks) into this position.  If you are going to offer a version as having "long term support" then you should not be offering a version in your download area that's going to do this sort of thing.  My opinion of Ubuntu is a lot lower after all this; were it not for the security breach earlier this year I'd probably be ready to give Linux Mint a try.  You can say that a user should have done thus and such before downloading a "point" version and if that lets you sleep well at night, fine, but honestly you know that most users will just download the currently offered version, and not bother to read release notes that might as well be written in ancient Sanskrit as far as they're concerned.  I appreciate everyone's help, and I know it's not the fault of anyone who attempted to help, even if I didn't understand what you were telling me.  But really, no Windows or OS X user would be faced with something like this, and I don't understand why anyone, particularly the Ubuntu developers, would think this is a good way to do things.  There are Linux distributions intended for use only by true Linux gurus, but I didn't think Ubuntu was supposed to be one of them.

---

### Post by banceu_sergiu_ione on 2016-08-19
> **bullwinkle2 said:**
> Well I think I solved this on at least one of my systems - see my last message in the other thread at [https://ubuntuforums.org/showthread.php?t=2334450&p=13533288#post13533288](https://ubuntuforums.org/showthread.php?t=2334450&p=13533288#post13533288) - The upshot was that clicking "Install" in that popup box gave me an error the first time I tried it, but for some reason a subsequent attempt worked.  If it doesn't prompt you to enter your password, it probably won't work, but if you keep trying maybe it eventually will.  I'm not marking this "solved" yet because I don't consider blind luck to be a real solution, and I really think it was pretty <snip> of the Ubuntu developers to put us users (those of us who are not certified Linux geeks) into this position.  If you are going to offer a version as having "long term support" then you should not be offering a version in your download area that's going to do this sort of thing.  My opinion of Ubuntu is a lot lower after all this; were it not for the security breach earlier this year I'd probably be ready to give Linux Mint a try.  You can say that a user should have done thus and such before downloading a "point" version and if that lets you sleep well at night, fine, but honestly you know that most users will just download the currently offered version, and not bother to read release notes that might as well be written in ancient Sanskrit as far as they're concerned.  I appreciate everyone's help, and I know it's not the fault of anyone who attempted to help, even if I didn't understand what you were telling me.  But really, no Windows or OS X user would be faced with something like this, and I don't understand why anyone, particularly the Ubuntu developers, would think this is a good way to do things.  There are Linux distributions intended for use only by true Linux gurus, but I didn't think Ubuntu was supposed to be one of them.

Look at it as an open book where you like the content but not the introduction.

---

### Post by Yellow Pasque on 2016-08-19
> EDIT: I forgot to mention that there are also three buttons on this popup: "Settings", "Install", and "OK". But there is no indication whatsoever of what exactly the "Install" button is going to install.

On the one hand, you claim you don't want to bother reading technical notes and can't understand any of them anyway. On the other hand, you're demanding a more in-depth technical explanation when prompted to install newer HWE components.

>  If you are going to offer a version as having "long term support" then you should not be offering a version in your download area that's (not) going to do this sort of thing.
They don't, but you do need to perform a kernel/security update when prompted.

> But really, no Windows or OS X user would be faced with something like this
False. Point releases of OS X are only supported for so long and then you have to upgrade to receive updates. Also, see Windows "anniversary" upgrade, for another example.

> A typical user expects to be able to go to the current download link, download the operating system, install it, and get on with life, and if they download a LTS version they expect it to work for the full period of LTS support.
Again, it does if you install updates as prompted. The updated point releases (and HWE components) allow users with newer hardware to use LTS releases, but they do complicate things for users who would prefer to use the original LTS kernel. Basically, it's a case where you "can't please all of the people all of the time."

---

### Post by bullwinkle2 on 2016-08-19
> **Temüjin said:**
> On the one hand, you claim you don't want to bother reading technical notes and can't understand any of them anyway. On the other hand, you're demanding a more in-depth technical explanation when prompted to install newer HWE components.

I am NOT "demanding a more in-depth technical explanation when prompted to install newer HWE components."  In fact that's exactly what I DO NOT want.  What I want is simply an explanation of what clicking "Install" will do in the simplest possible terms.  Like "Clicking Install will install the newer HWE components, but will not upgrade Ubuntu to 16.04".  That would have been sufficient to assure me that clicking Install was the thing to do, without sending me to some freaking long technical document that I don't understand, and that only seems to be trying to get me to upgrade to 16.04 prematurely.

The problem is that some people want to make everything SO complicated.

As for Windows and OS X, yes you have to upgrade occasionally, but the process is fairly straightforward and more to the point you can still easily use your older software after an upgrade, up to a point anyway.  That's because you can reinstall from the original .exe or .dmg or whatever file.  This assumes you are not in the habit of acquiring all your software from the "app store" and actually go to the trouble of downloading the installer files for the software you depend on.  But Ubuntu wants you to install nearly everything from their repository and because of the way dependencies work, you don't have the same luxury of sticking with an older version of some software app that works well for you.  I understand that "Snap" packages will address that issue, but obviously nothing I currently run came in a "Snap" package.

Also their updates don't leave you in a place where you don't know what to do, or send you to long pages of meaningless technical mumbo-jumbo.  They clearly do NOT assume that every single one of their users is an uber-geek.

---

### Post by Yellow Pasque on 2016-08-20
> **bullwinkle2 said:**
>  What I want is simply an explanation of what clicking "Install" will do in the simplest possible terms. 

It says "New important security and hardware support update" so logically, clicking Install would install that. It says nothing about 16.04 from what I can tell. That is a conclusion you are leaping to on your own.

> Like "Clicking Install will install the newer HWE components, but will not upgrade Ubuntu to 16.04".
You also said..
> I don't even know what HWE is.

Do you see the problem there?

---

### Post by atrab101 on 2016-08-20
> [INDENT]**New important security and hardware support update.**

WARNING: Security updates for your current Hardware Enablement Stack ended on 2016–08–04:
* [https://wiki.ubuntu.com/1404_HWE_EOL](https://wiki.ubuntu.com/1404_HWE_EOL)
[/INDENT]


I discovered, after reading this thread on August 18, that I had been without security updates for Ubuntu 14.04.5 since August 4, 2016.  My system was on Kernel 4.2.0-42.  I use Ubuntu every day, yet I had not received the above message or any other warning of the fact that support for my kernel version had stopped.  Is it possible that this was because I had indicated in software settings that I did not want to be informed of new versions?  I had set it this way because I have been a trouble-free user of 14.04 since I installed 14.04.4 in February 2016.  I do not plan to move to 16.04 for a year or two.  I have looked at the documentation on Ubuntu and found that the support times for versions and kernels are very clear if you look them up.  

However, when I first installed 14.04.4 I just assumed that the 5 year support rule (from April 2014) was in effect for me with my new installation.  I did not realize that (with kernel 4.2.0) I was only covered until August 4, 2016.  I don't believe that there was anything on the download page for the iso file that clarified this issue, although I may have missed something.  Did I miss something?

After thinking about the issue I went to "About This Computer" and clicked on the update box, but it did not offer anything for the kernel.  Then I did some further searching on the issue and found a post that said to check the software updater in Bash.  When I did that I got the above warning.  So I slept on it and then did a disk image in the morning, in case I would encounter problems with the update.  The good news is that I completed the update to Kernel 4.4.0-34 (supported to April 2019) and everything works perfectly!  No boot issues, no broken software packages, no video issues and no program issues.  I do believe I have checked everything.  So I continue to be amazed at how well Ubuntu works. It is rock solid. It has been absolutely trouble-free since the day I installed it over six months ago.

Best regards to the developers and all who provide support for this great product! :)

---

### Post by kansasnoob on 2016-08-20
> **atrab101 said:**
> I discovered, after reading this thread on August 18, that I had been without security updates for Ubuntu 14.04.5 since August 4, 2016.  My system was on Kernel 4.2.0-42.  I use Ubuntu every day, yet I had not received the above message or any other warning of the fact that support for my kernel version had stopped.  Is it possible that this was because I had indicated in software settings that I did not want to be informed of new versions?  I had set it this way because I have been a trouble-free user of 14.04 since I installed 14.04.4 in February 2016.  I do not plan to move to 16.04 for a year or two.  I have looked at the documentation on Ubuntu and found that the support times for versions and kernels are very clear if you look them up.  

However, when I first installed 14.04.4 I just assumed that the 5 year support rule (from April 2014) was in effect for me with my new installation.  I did not realize that (with kernel 4.2.0) I was only covered until August 4, 2016.  I don't believe that there was anything on the download page for the iso file that clarified this issue, although I may have missed something.  Did I miss something?

After thinking about the issue I went to "About This Computer" and clicked on the update box, but it did not offer anything for the kernel.  Then I did some further searching on the issue and found a post that said to check the software updater in Bash.  When I did that I got the above warning.  So I slept on it and then did a disk image in the morning, in case I would encounter problems with the update.  The good news is that I completed the update to Kernel 4.4.0-34 (supported to April 2019) and everything works perfectly!  No boot issues, no broken software packages, no video issues and no program issues.  I do believe I have checked everything.  So I continue to be amazed at how well Ubuntu works. It is rock solid. It has been absolutely trouble-free since the day I installed it over six months ago.

Best regards to the developers and all who provide support for this great product! :)

One thing at a time:

> I use Ubuntu every day, yet I had not received the above message or any other warning of the fact that support for my kernel version had stopped.  Is it possible that this was because I had indicated in software settings that I did not want to be informed of new versions?

No. The two are not related. Notify of new version notifies of a full new release, eg; 16.04. I just posted some info about HWE here:

[https://ubuntuforums.org/showthread.php?t=2334515&p=13533598#post13533598](https://ubuntuforums.org/showthread.php?t=2334515&p=13533598#post13533598)

If that doesn't totally answer your question I'll try to help clear up any confusion.

The reason you weren't notified until now is bugs - yes, bugs! I tried to improve the testing of the HWE upgrade process over what we saw with Precise HWE-EOL and posted about it here:

[https://ubuntuforums.org/showthread.php?t=2330466](https://ubuntuforums.org/showthread.php?t=2330466)

[https://ubuntuforums.org/showthread.php?t=2333095](https://ubuntuforums.org/showthread.php?t=2333095)

I even filed a bug report about the need for official testing:

[https://bugs.launchpad.net/ubuntu-manual-tests/+bug/1602066](https://bugs.launchpad.net/ubuntu-manual-tests/+bug/1602066)

I wasn't able to make that happen but I did spur enough testing that various bugs were discovered and fixed (two examples):

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati-lts-xenial/+bug/1611982](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati-lts-xenial/+bug/1611982)

[https://bugs.launchpad.net/ubuntu/+source/xorg-lts-xenial/+bug/1610434](https://bugs.launchpad.net/ubuntu/+source/xorg-lts-xenial/+bug/1610434)

So the release of the updated update-manager & update-notifier packages needed to notify of the HWE upgrade was delayed.

> However, when I first installed 14.04.4 I just assumed that the 5 year support rule (from April 2014) was in effect for me with my new installation.  I did not realize that (with kernel 4.2.0) I was only covered until August 4, 2016.  I don't believe that there was anything on the download page for the iso file that clarified this issue, although I may have missed something.  Did I miss something?

No, you didn't really miss anything. As I said [here]("https://ubuntuforums.org/showthread.php?t=2334371&page=2&p=13533077#post13533077") there is an expectation that users will read the release notes. That was not meant as snark. If you go back to this bug report:

[https://bugs.launchpad.net/ubuntu-manual-tests/+bug/1602066](https://bugs.launchpad.net/ubuntu-manual-tests/+bug/1602066)

You'll see that I say, "I began saving a list of web links of problems encountered when Precise users were notified of HWE EOL in anticipation of recommending that we amend our download page to recommend users always try the first point release. I chose not to do that because the 14.04.1 images were affected by [bug #1265192]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192") which could result in data loss. (That may be worth pursuing prior to 16.04.2 but that's a whole different issue)."

We (btw I'm just an Ubuntu GNOME tester) need to do a better job of letting users know about HWE EOL so they can make a more informed decision. I posted some thoughts about this here:

[https://ubuntuforums.org/showthread.php?t=2330466&page=3&p=13528657#post13528657](https://ubuntuforums.org/showthread.php?t=2330466&page=3&p=13528657#post13528657)

> The good news is that I completed the update to Kernel 4.4.0-34 (supported to April 2019) and everything works perfectly!

Whew \\:D/ I'm glad to hear that. I tested my brains out (almost literally) with 16.04.1 testing followed closely by 14.04.5 testing and then this go at HWE EOL testing.

---

### Post by atrab101 on 2016-08-20
> Whew \\:D/ I'm glad to hear that. I tested my brains out (almost literally) with 16.04.1 testing followed closely by 14.04.5 testing and then this go at HWE EOL testing.

Thanks, Kansasnoob, for the great explanation of issues.  I am very much a novice with Ubuntu.  The links you provided show that there is much indeed that goes on behind the scenes to deliver the product that I have found to be trouble-free over these last 6 months since I installed 14.04.4.  As an aside, I posted my initial thoughts on my great experience with Ubuntu here:  [https://ubuntuforums.org/showthread.php?t=2320111](https://ubuntuforums.org/showthread.php?t=2320111)

I am sure I will install the first point release when I do move to a new version (16.04.1).  That is a great recommendation.  Hopefully, that will be clarified on the download page as you have suggested previously.  It would be a big help for new users and easy to do.  

Finally, I'm wondering if my trouble-free move to the 4.4.0-34 Kernel with 14.04.5 is a prognosticator of success when moving to 16.04.1, since I presume I now have the same kernel as that version?  Am I apt to have other issues not related to the kernel, or are the kernel and HWE stack transitions where most issues reside?

Best regards

---

### Post by kansasnoob on 2016-08-20
> Finally, I'm wondering if my trouble-free move to the 4.4.0-34 Kernel with 14.04.5 is a prognosticator of success when moving to 16.04.1, since I presume I now have the same kernel as that version? Am I apt to have other issues not related to the kernel, or are the kernel and HWE stack transitions where most issues reside?


In my own usage I'd say no. I've found 14.04.5 (with the lts-xenial HWE) to run fine on my computers, but 16.04 itself has presented just one problem after another. I plan on running 14.04 until 18.04.1 is released and reevaluate the situation then. There is a good chance that I'll skip 16.04 altogether and just do a fresh install of 18.04 - that's the great thing about a five year support cycle. For that matter I may be ready to retire some of my hardware by then (one is an energy hog and another is just slow).

Always read the Release Notes (look before you leap):

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

Does the "New features in 16.04 LTS" make you say, "oh goody, that's just what I've been waiting for"? Do the "Known issues" make you say, "uh-oh, sounds like a lot of problems"? For me the answer to question #1 was "no" and the answer to #2 was "sounds like a mess". But if I were to get new hardware I'd probably try 16.04.1 first keeping in mind that I may decide to scrap it and start over with either 14.04.1 or 14.04.5.

---

### Post by Mythological on 2016-08-21
> **kansasnoob said:**
> In my own usage I'd say no. I've found 14.04.5 (with the lts-xenial HWE) to run fine on my computers, but 16.04 itself has presented just one problem after another.

You aren't the only one.  Tried upgrading to 16.04 on an MSI Cubi and the sound went to hell (this also happened after applying the HWE upgrade in 14.04.5, except that also screwed up video!).  Even doing the audio test, the sounds played at about one-quarter speed.  I found a page that was supposed to offer a fix and it would work for one session but after the next reboot the problem would be back.

Dropped back to 14.04 (the very first release, that avoids the HWE update) and everything works beautifully.

Funny thing is that the MSI Cubi is less than a year old but works best with the oldest version of Ubuntu 14.04.

I can never understand why, once a piece of software is working great, developers have to go and break it.  :frown:

(Yeah, I know, the new release probably fixes problem for some people, at the expense of introducing problems for existing users).

---

### Post by mastablasta on 2016-08-22
> **Mythological said:**
> 
I can never understand why, once a piece of software is working great, developers have to go and break it.  :frown:

(Yeah, I know, the new release probably fixes problem for some people, at the expense of introducing problems for existing users).

i am hesitant to update to 16.04 as we use Kubuntu. new Plasma just stabilised lately but i am not convinced stability wise it is near the version 4 present in 14.04. sure a few quirks here and there but over all very stable now and rarely gives any issues. besides the latest version of plasma in not in Kubuntu. i will follow up closely. for now ther ei sno need to move, btu when i do i will likley have to add stable Plasma version ppa.

anyway if we move away form Plasma issues, the one thing that bothers me is there is usually no easy way ot move to the old version of software. perhaps containers/snaps etc. will finally solve this. often i would run older versions of software on windows as they were better to me (e.g. better GUI), or they would run faster (better optimisation?!).

i think i am maybe getting old and conservative :)


> **bullwinkle2 said:**
> THANK YOU!!! 
Please assure me this will NOT upgrade my 14.04 system to 16.04 and I will give it a try.  The only thing that's worrying me is all the references to "xenial" in that software.
yup.

linux-generic-lts-xenial --> kernel
xserver-xorg-core-lts-xenial xserver-xorg-lts-xenial xserver-xorg-video-all-lts-xenial xserver-xorg-input-all-lts-xenial libwayland-egl1-mesa-lts-xenial --> GPU stuff (X.window and wayland)

not other apps. you bring 16.04 kernel back to 14.04. the only issue with 14.04.5 is the AMD driver as i know. i don't think they made fglrx that goes with xenial kernel yet (if they ever will) os it should fall back to the open source radeon. not sure how they solved it but i guess like that.  this is specific AMD decision as they went full opensource. or nearly full. a much better result in the long run. plus they helped with opensource radeon again.

someone else would have to confirm this but i believe you should be able to fall back to older kernel in case of torubles. after all there are probably at least a few older kernles available to boot fro1m on your PC.

and finally, we are not developers here. a tleast not most of us. we are users. some file bug reports, a few developed some apps, but most of us are just simple users. arguing how things should be is not really productive. we can talk about how things are and i am sure somone can also explain why they are made like so.

---

### Post by c_xy on 2016-08-25
I too was shocked to see this warning message the other day on our newer server.

On another (older) server we had upgraded from 12.04 to 14.04.

Older server has 14.0.5 currently installed, kernel 3.13.0-93-generic.

We installed 14.04 on our newer server directly from a CD containing an iso image. The newer server also has 14.0.5 currently installed, but the kernel listed is 3.19.0-66-generic

I couldn't figure out why we had the same operating system, 14.04.5, installed on two machines, but had two different kernels. Thought maybe it was due to the fact our newer system was more high-end and it also had a GPU.

It all makes sense now.

Unfortunately, I'm hesitant to install the update kernel because we use x2go and freenx with our current system 14.04. We don't want to upgrade the to 16.04, but would upgrading just the kernel affect our use of x2go and freenx? We use both programs to connect to the server by way of creating virtual desktops on Windows and OS-Clients.

Any thoughts or suggestions would be appreciated.

Also, is there anyway possible to downgrade from one kernel to another. In my case it would be, 3.19.0-66-generic to 3.13.0-93-generic?

Thanks.

c

---

### Post by Yellow Pasque on 2016-08-26
> **c_xy said:**
> I couldn't figure out why we had the same operating system, 14.04.5, installed on two machines, but had two different kernels.

When lsb-release package gets updated, so does your "OS" version.

---

### Post by c_xy on 2016-08-26
> **Temüjin said:**
> When lsb-release package gets updated, so does your "OS" version.

I'm still a bit confused? What exactly does that mean?

We didn't the older system kernel ([COLOR=#000000]3.13.0-93-generic) get updated to match the newer system kernel ( [/COLOR][COLOR=#000000]3.19.0-66-generic), yet  both with 14.04.5 installed?

What causes these differences, which really gets back to the OP's point.

When both systems are up-to-date, the kernels are still different.

Thanks.

c[/COLOR]

---

### Post by nordic2 on 2016-08-26
Sorry to add noise to this thread, but will clicking install just update the kernel keeping the SO in 14.04?

I usually disregard software updater pop-ups and instead use apt-get upgrade / dist-upgrade (almost daily), but apt-get doesn't show me anything to upgrade and yet the warning keeps coming up.

---

### Post by brian-murray on 2016-08-26
> **bullwinkle2 said:**
> I installed the version that was offered on the Ubuntu site.  This is what is really frustrating to me; people are acting like I made a conscious choice to use a version with a short kernel end of life.  **I did not.**  I simply took what was offered on the Ubuntu site as the current version.  But beyond that, I have 16.04.5 according to the output of the "lsb_release -a" so according to that chart, I should be good until sometime in 2020.  I have applied all the kernel updates that have been offered in Update Manager.  So **why** would I have a kernel that is no longer supported? (That's a rhetorical question; I probably would not understand the answer.)

What I hear you guys saying is that even though this is a "Long Term Support" release that is supposed to be supported for **five years**, depending on when I downloaded it, or on the position of the moon and stars, or whether a gnat sneezed, or some other unknown factor that I probably wouldn't understand if you tried to explain it to me, **somehow** I wound up with a version that was only supported for part of that five years.  I didn't **want** such a version, and would never have knowingly downloaded such a version, but that's what was offered on the Ubuntu site at some point in time.  And now, all people can tell me is that even though my version identifies as the current version when I run "lsb_release -a" (because I HAVE applied all the updates), somehow I'm stuck with this funky kernel, and what nobody's explaining so far is, "How do I upgrade that to the version that will last until the end of the five years?"

Seriously, it does not help me at all to get explanations for why this happened, particularly since I'm apparently not familiar enough with the guts of Linux to understand any of the ones that have been offered so far.  The only thing that's really going to be helpful is if someone can explain what I have to do now to get the **supported** kernel installed on these systems.  Which is really something that should be prominently featured on that web page I referenced in my first post, which right now basically only tries to get you to upgrade to 16.04.

To get the supported kernel installed on the systems you can use the command "hwe-support-status --show-replacements" to find out what packages to install.  It will return something like what is listed on this wiki page - [https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Desktop](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Desktop).  The wiki page you referenced in your first post does seem to contain information about how to use hwe-support-status, [https://wiki.ubuntu.com/1404_HWE_EOL#A1._Install_Ubuntu_16.04_Xenial_HWE_Stack](https://wiki.ubuntu.com/1404_HWE_EOL#A1._Install_Ubuntu_16.04_Xenial_HWE_Stack), which is different than upgrading to 16.04.

---

### Post by kansasnoob on 2016-08-26
> **c_xy said:**
> I'm still a bit confused? What exactly does that mean?

We didn't the older system kernel ([COLOR=#000000]3.13.0-93-generic) get updated to match the newer system kernel ( [/COLOR][COLOR=#000000]3.19.0-66-generic), yet  both with 14.04.5 installed?

What causes these differences, which really gets back to the OP's point.

When both systems are up-to-date, the kernels are still different.

Thanks.

c[/COLOR]

Please read:

[https://ubuntuforums.org/showthread.php?t=2334515&p=13533598#post13533598](https://ubuntuforums.org/showthread.php?t=2334515&p=13533598#post13533598)

Specifically in answer to:

> What causes these differences, which really gets back to the OP's point. 

It's due to this:

> Those who installed Trusty using the 14.04.2, 14.04.3, and 14.04.4 images got the lts-utopic, lts-vivid. or lts-wily HWE stacks respectively which all reached HWE-EOL this month

---

### Post by acornbrain on 2016-08-27
I have read the whole thread and do not think I saw an answer to the basic question: Should I click "Install" or not?

'backup your files/disc image first' does not fill me with confidence. And yet, what are the consequences (if any) of inaction on this matter? I want to continue receiving updates to 14.04, I do not want to upgrade to 16.

Please, some simple advice is all I am asking. I do not really need to wade into a debate on "why is this happening" and reading the fine print, etc.

thank you
-brian

---

### Post by howefield on 2016-08-27
> **acornbrain said:**
> I have read the whole thread and do not think I saw an answer to the basic question: Should I click "Install" or not?

No one can answer that on your behalf, if you are running an unsupported kernel and/or graphics stack in 14.04.x you have a choice, continue to run unsupported software or upgrade. I'd think most people would upgrade. 

> 'backup your files/disc image first' does not fill me with confidence. And yet, what are the consequences (if any) of inaction on this matter?

Basic machine housekeeping would be to have multiple copies of important data, this applies whether or not you are upgrading. The consequences of not securing your important data could be that if you mess up with the update and are incompetent to fix it, you get to keep all the pieces.

---

### Post by c_xy on 2016-08-27
kansasnoob, thank you for your clarification. Wow. 

It is important to understand why this is happening to prevent something like this from happening again in the future.

Downloading iso images of a LTS product a couple of years after its initial release, is not necessarily for the entire length with regard to support for the kernel.

This is a very big pain to say the least and somewhat conflicts with the meaning of LTS. 

Is there a way to downgrade a kernel version?

c

---

### Post by acornbrain on 2016-08-27
> **howefield said:**
> No one can answer that on your behalf, if you are running an unsupported kernel and/or graphics stack in 14.04.x you have a choice, continue to run unsupported software or upgrade. I'd think most people would upgrade. 



Basic machine housekeeping would be to have multiple copies of important data, this applies whether or not you are upgrading. The consequences of not securing your important data could be that if you mess up with the update and are incompetent to fix it, you get to keep all the pieces.

I meant, what are the consequences of NOT UPGRADING (Not NOT BACKING UP DATA).

---

### Post by howefield on 2016-08-27
> **acornbrain said:**
> I meant, what are the consequences of NOT UPGRADING (Not NOT BACKING UP DATA).

Your software will continue to run.

If there are no vulnerabilities exploited in your kernel/X version, there are no consequences, but if there are vulnerabilities found then you are at risk.

---

### Post by tiitanic1912 on 2016-08-28
you need to update the kernel, the 3 to 4.4.

You can use the following command to do this, I've tried works.
```
sudo apt install linux-generic-lts-xenial linux-image-generic-lts-xenial
```
The truth is, us are giving a good scare with this.

---

### Post by lou6 on 2016-08-28
After upgrading to the Xubuntu 16.04 LTS point release I was deluged with bugs - eventually reinstalled 14.04 and wondered what to do next until I found this thread. Thanks to mastablasta, I installed the 16.04 kernel and my 14.04 has a new lease on life...

Now I have what is probably a noob question...

How does having the 4.4 series HWE installed impact my future release upgrade abilities?  Must I upgrade to 16.04 at some time in the future to be eligible for 18.04?

---

### Post by pterosky on 2016-08-30
I just installed the 4.4.0 kernel by clicking "Install". My PC booted up fine after the restart, and so far everything seems to be working. Clicking "Install" did **not** upgrade my Ubuntu installation to 16.04.

**Before clicking "Install"**
$ uname -a
Linux pc_name 3.19.0-66-generic #74~14.04.1-Ubuntu SMP Tue Jul 19 19:56:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

**After clicking "Install" and restarting**
$ uname -a
Linux pc_name 4.4.0-34-generic #53~14.04.1-Ubuntu SMP Wed Jul 27 16:56:40 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by oleg-kuts on 2016-10-02
Sorry, for it might be offtop. I have xubuntu 14.04.5 and have the same problem. When I press "install" I get 
[HTML]This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same...[/HTML]
I have Intel Graphics HD 2000, and Intel Pentium B970 if it matters. Should I update ketnel manualy?

---

### Post by The Cog on 2016-10-02
> **kansasnoob said:**
> There is an expectation that users will read the release notes. In the case of 14.04.3:

[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/14.04.3](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/14.04.3)

Then read the section about HWE:

[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/14.04.3#LTS_Hardware_Enablement_Stack](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/14.04.3#LTS_Hardware_Enablement_Stack)

That's why a link to the release notes is always prominently posted on the [main download page]("http://www.ubuntu.com/download/desktop"):

[ATTACH=CONFIG]270747[/ATTACH]

Eew! 
I had not appreciated before reading this thread that certain point release installations would not receive the claimed long term support. I will be much more wary of using point release installers in future. From the 14.04.3 release notes:
Paragraph 1: > These release notes for Ubuntu 14.04.3 (Trusty Tahr) provide an overview of the release and document the known issues with Ubuntu 14.04.3 and its flavors.
Paragraph 2: > Ubuntu 14.04 LTS will be supported for 5 years...
So in reply to your snarky comment, I would reply that there is an expectation that the release notes will be truthful. The fact that paragraph 2 is not referring to release 14.04.3 at all, but to the earlier 14.04 release is not spelled out. The actual truth is hidden in a separate document that is referred to in the "New Features" section of the release note. If not an outright lie the release note is certainly deceptive, even though I doubt there was an actual intention to deceive.

I see no reason for your belittling people like bullwinkle2 and myself who failed to failed to follow all the links in the new features section.
I shall be careful to avoid using point release install images in future.

---

### Post by marcerickson on 2016-10-11
> **kansasnoob said:**
> There is an expectation that users will read the release notes. 

Guess what?  Lots of us don't read them.  And even if we did, we might not understand them.  We just want our computers to work and to be secure.  Some of us don't want to become Linux experts to be able to use it - which is what some people in this thread are implying.  Some of us prefer to do other things than learn about Linux - especially when it's under pressure because our systems are borked due to an unwanted kernel upgrade that borks Samba. Or borks Linux so badly that it won't boot at all.

> **The Cog said:**
> ...I would reply that there is an  expectation that the release notes will be truthful. The fact that  paragraph 2 is not referring to release 14.04.3 at all, but to the  earlier 14.04 release is not spelled out. The actual truth is hidden in a  separate document that is referred to in the "New Features" section of  the release note. If not an outright lie the release note is certainly  deceptive, even though I doubt there was an actual intention to deceive.


You want Linux to take over the Desktop?  Great.  I'd like to see Microsoft get some real competition.  But the issue in this thread is the kind of thing that makes novice users say to themselves, "At least the Borg (Microsoft) ensure that my version of Windows is secure and works. (Usually.)"  Yes, they have bad patches, but until Linux or Ubuntu starts making these updates less opaque and more user-friendly, I believe that the Linux share of desktop OSes installed will remain where it is now.

---

### Post by QLee on 2016-10-11
> **marcerickson said:**
> Guess what?  Lots of us don't read them.  And even if we did, we might not understand them.  We just want our computers to work and to be secure.  Some of us don't want to become Linux experts to be able to use it - which is what some people in this thread are implying.  Some of us prefer to do other things than learn about Linux - especially when it's under pressure because our systems are borked due to an unwanted kernel upgrade that borks Samba. Or borks Linux so badly that it won't boot at all.

I am confident that kansasnoob is well aware that many don't read the release notes, most people trying to help here are aware of it because so many unexperienced users here have trouble when they didn't read them. People who don't want to learn GNU/Linux generally buy a computer with an operating system already installed and configured and then they can complain to who they bought it from for support. Here are just other users trying to help new users. One thing that you could have learned was, do read the release notes and ask here first about anything that you didn't understand or had a question about.

> **marcerickson said:**
> 
You want Linux to take over the Desktop?  Great.  I'd like to see Microsoft get some real competition.  But the issue in this thread is the kind of thing that makes novice users say to themselves, "At least the Borg (Microsoft) ensure that my version of Windows is secure and works. (Usually.)"  Yes, they have bad patches, but until Linux or Ubuntu starts making these updates less opaque and more user-friendly, I believe that the Linux share of desktop OSes installed will remain where it is now.

I've never seen anyone here make any statement about wanting "Linux" to take over the desktop. I don't know what Canonical has in mind but I imagine Ubuntu use has continued to increase over time and expect that will continue. Keep in mind that user-friendly does depend somewhat on the specific users knowledge and ability and previous experience.

Have you considered that the situation between 14.04 and 16.04 was a big change with the kernel (out of Ubuntu's control) and Ubuntu had to find a way to deal with the change, which by the way, worked for many people, they didn't have to post for help so you don't see them, except for one who mentioned it. Another example: It worked for me, but anecdotal information like that isn't useful for someone who is having problems. 

Everyone helping here seems to acknowledge, there was a mess, and almost everyone here is just trying to help people solve their issues and learn skills for the future. If you choose to not learn new skills then that is fine, GNU/Linux has always been about choice.

---

### Post by howefield on 2016-10-11
And with that, thread closed as question has been asked and answered.

---

