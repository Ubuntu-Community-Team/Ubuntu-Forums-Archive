---
title: "Upgrading from 20.10 to the recent version using the terminal"
date: 2023-07-10
forum: General Help
---

### Post by orengolan on 2023-07-10
My laptop is on Ubuntu 20.10 and I am thinking of upgrading it to a new version. What's a good way to do that and can it be done using the terminal? (I am using I3).

---

### Post by Bashing-om on 2023-07-10
orengolan; Uh OH -- But there is a way !

> 
Ubuntu 20.10 (Groovy Gorilla) was the 33rd release of Ubuntu, support ended July 22nd, 2021. See                [https://lists.ubuntu.com/archives/ubuntu-announce/2021-June/000269.html](https://lists.ubuntu.com/archives/ubuntu-announce/2021-June/000269.html)

 [https://help.ubuntu.com/community/EOL](https://help.ubuntu.com/community/EOL) and [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) for more info. Looking to upgrade from an EOL release? See [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)


-terminally, but this is not a terminal issue :D -

---

### Post by TheFu on 2023-07-11
> **orengolan said:**
> My laptop is on Ubuntu 20.10 and I am thinking of upgrading it to a new version. What's a good way to do that and can it be done using the terminal? (I am using I3).

FWIW, if you choose to install a non-LTS release, plan to do a fresh install every 6 months.  If you can't commit to this, then only use LTS releases which provide 3 yrs of support for most DE flavors. That's enough time to move from LTS to LTS.

Once a release isn't supported anymore, upgrading becomes more difficult.  Always.  Always, migrate to the next LTS **before** the prior release support ends.  Always.

At this point, my best advice is that you should backup anything you don't want to lose and do a fresh install of 22.04 which is an LTS release.

Sorry, I don't have a magic time machine to go back and make all this easier.Support for 20.10 ended 2 yrs ago.

---

### Post by ian-weisser on 2023-07-11
> **TheFu said:**
> At this point, my best advice is that you should backup anything you don't want to lose and do a fresh install of 22.04 which is an LTS release.

This is indeed excellent advice. Heed it.

There are some back-door methods, and sometimes they work. But they are complex. Some are unsupported. They might make things worse if you make a typo or click the wrong unfamiliar option.

---

### Post by orengolan on 2023-07-13
Thanks for all the replies!

---

### Post by guiverc on 2023-07-13
I actually wrote a reply for this awhile ago, but as I don't use i3 and your setup is therefore rather different to a default install, I likely opted to close the window & didn't click 'post'.

I keep systems of all supported releases of Lubuntu on actual hardware, and when a release goes EOL, I never have need of the next release (I'll already have it), but do an unclean install of the newer *development* release and thus change the release in a way that causes my *manually installed* packages (esp. music player I use) auto-reinstalled, plus my data files remain so I have music etc. to play on re-install.

During the development cycle that install will get re-installed at least weekly, and even now that 22.04 or jammy is a released product, I don't upgrade packages for that install, instead re-install using the current daily (~weekly) which upgrades my packages AND performs a QA-test install on the unreleased 22.04.3 ISO we have.

It's what I often use, and would have used when 20.10 reached EOL & I didn't want 21.04 (*already having at least one install of that release) *thus moved that install to 22.10 or another LTS (*whatever release I felt I needed another install of*).

What I use is called the *install using existing partition* and I've attempted to document (for QA-testers) here - [https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743](https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743)

I've also written about it many times on different sites (askubuntu etc, possibly here too)

------   My unsent reply follows

If you're using a Desktop system, you can use the repair installation option to achieve an *upgrade via re-install* where you're doing the repair with a different release.

The expected *release-upgrade* path that was *supported* and thus QA-tested, was to the next release being Ubuntu 21.04, however that *intended* & *tested* path ended when [Ubuntu 21.04 reached EOL 9 months after its release]("https://fridge.ubuntu.com/2022/01/21/ubuntu-21-04-hirsute-hippo-end-of-life-reached-on-january-20-2022/"), thus making your job harder.

You can try what is provided on links already provided (by Bashing-om), otherwise you can backup, download & write a later release to thumb-drive, then install that but do **not** format your drives; just mark them for re-use exactly as they're used now. The lack of format & re-use of partitions *triggers* the repair installation option, which notes what packages you have installed, erases system directories (***this will be a problem with many server apps as they often store configs in system directories, but isn't a problem for desktop apps***), installs apps from media, then if internet is available, downloads and installs the *manually installed* packages you'd added to your system (*if available for the new release in Ubuntu repositories*) before asking to reboot.

Note: The *repair* feature I'm talking about is only QA-tested using Ubuntu repository software (*no 3rd party*), though from personal experience some 3rd party will auto-reinstall, but others will not, depending on how & who packaged it, but this is somewhat predictable but won't be if you're a newbie or don't have much experience with Ubuntu software vs 3rd party (ie. *did the packager intend you to upgrade? or clean re-install; its easier for packagers to ignore upgrades so  where it came from is important* *as what I'm describing here is a unclean (repair) re-install*)

 Backup first, and if using a Server install I'd likely disregard this option (*I only use it for desktop systems**; and find it easier for flavors over Ubuntu Desktop as flavors always have 'universe' enabled needed to re-install the packages from universe*)

---

