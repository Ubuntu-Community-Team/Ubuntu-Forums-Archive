---
title: "Recent Ubuntu Epic Fail"
date: 2021-09-17
forum: General Help
---

### Post by abpainter on 2021-09-17
I doubt if I'm the first one posting about this because the problems started weeks or months ago, but I've worn out search engines looking for existing posts so I don't know what else to search for.  I didn't make note of the exact date that everything went pear-shaped because of recent  events including major surgeries and ensuing therapies that leave me with a generally nonfunctional GAF.  If there are existing threads, kindly point me to them please.  

I started with Ubuntu Desktop 18/gNome a year or so ago, then just let it roll with automatic updates.  I believe that at some point I was running Ubuntu 19, but now I can't find any installation for that in Ubuntu Downloads.  I know that at some point I had a working upgrade of Ubuntu 20, but I don't know what exact version/build number that was and there is no longer an installer available that is pre-brickuntu.  Before the updates hammered the system, my only issue has ever been the need for the nVidia proprietary drivers.  My most commonly used desktop software is Steam, Discord, a GUI hex editor called gHex, some GUI wrappers around the terminal networking tools, xfreerdp2, and the Mono Framework.  I know Mono is an old way to run DotNET on Nix, but I'm an old guy so I don't want any tips on the big new thing.

So in the last few months an automatic update (I believe from Ubu 20.? to a newer Ubu 20.?.!) just turned the whole system into a brick.  I literally found it asking to restart after automatic updates, clicked Restart Now, and was no longer able to boot.  I was immediately able to identify that the problem was with the nVidia driver and got going with nomodeset.

After figuring out how to get my system to boot to gNome at all, I spent days dinking around with the nVidia drivers package via apt.  Ultimately I resigned myself to crappy resolution and weird aspect ratio, learned to live with just 1 monitor, and promptly  discovered that gHex had quit working.  That's when I found that the GUI Software Updater just hangs.  Attempts to reinstall both the nVidia drivers and gHex via apt were met with failures which spit out a laundry list of unmet dependencies with the conditions "will not be installed" or "is not installable" and falsely accuses me of "holding broken packages" (by falsely I mean that when this started, I was using no holds at all).  Attempts to manually install each "unmet dependency" individually resulted in more failures with the same errors.  I also started getting weird errors from various repositories when attempting apt update, some of which are persistent and some of which come and go on different attempts to run apt.  The most persistent (and verbose) repo errors are actually from the MS repos where I get Mono from, but in spite of those errors the Mono Framework installs just fine and DotNET apps run fine too.

I was able to roll back to Ubu 18 and prevent kernel/distro updates by setting apt/dpkg holds on the kernel and the ubuntu-standard package at that current version.  Then I couldn't get a working installation of Steam or Discord with failure messages indicating that my Ubu version was just too old.  I've been working with that for a month or so, but it's very kludgy - apart from not being able to get my communication app (Discord, which my company uses for PC and Phone IM) and not being able to get Steam (because all work and no play makes me a dull boy), the version of freerdp I get with Ubu 18 is broken in several ways that make it more of an annoyance than a tool.

Finally I tracked down an installer for the oldest available version of Ubu 20, then put apt/dpkg holds on the kernel and ubuntu-standard packages.  At that point I can get the nVidia driver to install just fine through the Ubuntu Software app, but still no joy with gHex, Steam, Discord, et al, and still the same old collection of failure messages, and still unable to obtain dependencies when trying to manually install them one by one, and still the same on-again-off-again errors from apt repositories.  At least now I really do have holds set, but I'm absolutely positive that isn't the problem.  

I can't find an emoji that switches from laughing hysterically to sobbing uncontrollably.

---

### Post by abpainter on 2021-09-18
I managed to find a Ubuntu 19.10 ISO which I had saved locally.  Why on Earth did Ubuntu devs think it was a good idea to delete the only modern Ubu release that actually works from their download site?

---

### Post by coffeecat on 2021-09-18
The ISO for Ubuntu 19.10 can be found for download if you know where to look but I'm not going to tell you, since it was an interim release only supported for 9 months and now well past end-of-life. To say that 19.10 is the only release that works is an absurd statement.

If you want help in solving issues with a **supported** release of Ubuntu, you are very welcome to start a new thread. If you do, please give a clear and concise description of your problem, and include details of the hardware that you are using. Rambling diatribes are extremely unlikely to be productive.

Thread closed.

---

