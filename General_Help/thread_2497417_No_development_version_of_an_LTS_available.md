---
title: "No development version of an LTS available"
date: 2024-05-03
forum: General Help
---

### Post by mikegreen8 on 2024-05-03
Hi.

I'm trying to upgrade from Ubuntu 22.04  ---> 24.04.      May.03.2024
                
When I try this:    sudo do-release-upgrade

or this:                 sudo do-release-upgrade -d

I get this message: [I]There is no development version of an LTS available
[/I]
Do I have to wait a little longer ?

Chomping at the bit for 22.04,
M.....

---

### Post by grahammechanical on 2024-05-03
The official upgrade path from Ubuntu 22.04 LTS to Ubuntu 24.04 LTS will not be open for another 6 months, or there about. At that time Software Updater will offer an upgrade to the latest LTS release which will be 24.04 LTS.

the -d switch in the command that you used will update/upgrade to the development version if we are on the latest release. So, if I was on 24.04 LTS I could upgrade to 24.10 development version with that command.

As you are on 22.04 LTS you cannot upgrade to the 24.10 development release.

If you are determined to get on to 24.04 LTS then I suggest but not recommend that you upgrade to 22.10; then 23.04, then 23.10, then 24.04. 

The problem with that method is the fact that both 22.10 and 23.4 are now both end of life versions and their repositories have been moved to the old-releases part of the Ubuntu repositories. This complicates things a great deal.

Regards

---

### Post by mikegreen8 on 2024-05-04
Thank you for your informative response. I will wait for the Fall and try again.

Have a nice day,
M...

---

### Post by mar.ste on 2024-07-21
> **grahammechanical said:**
> The official upgrade path from Ubuntu 22.04 LTS to Ubuntu 24.04 LTS will not be open for another 6 months, or there about.  What is the reason to postpone so much the LTS upgrade if not newly installed?  (we are at the end of July and I on Kubuntu 22.04  still have the same message!...)

---

### Post by deadflowr on 2024-07-21
It's not 6 months until the upgrade is available, it's usually just over 3 months.
The upgrade path should be available mid-August. (August 15th to be exact as of right now: [https://discourse.ubuntu.com/t/noble-numbat-release-schedule/35649](https://discourse.ubuntu.com/t/noble-numbat-release-schedule/35649))

The reason is LTS systems tend to dominate production environments so they want those to be as tight and error free as possible,
with as many known bugs quashed before they allow for the upgrade.

And unlike an upgrade from a non-LTS system, an LTS to LTS upgrade has to deal with 2 years of new packages and versions and stuff.
Some packages have new requirements, some packages no longer exist some packages stay the same.
There is a lot to do in order for a seamless upgrade with such systems.

Unlike a non-LTS release which tend to have all those changes slowly integrated incrementally across 3 releases.


But my personal  opinion is if you run LTS systems, you shouldn't even start considering upgrading until at least 6 months after release.
Maybe wait until the next year even. Or skip the upgrade entirely. It's perfectly fine to do so.
The LTS system is supported for 5 years with an additional 5 years of Ubuntu Pro support. So I see no rush. And that is the entire point of an LTS release.
If you're someone who runs an LTS system but upgrades as soon as the next LTS version is released, I see no reason why you shouldn't just run non-LTS releases.

---

### Post by Dennis N on 2024-07-21
> The upgrade path should be available mid-August.
This is what I had thought too, but on July 17 the Ubuntu 22.04 Software Updater offered to upgrade to 24.04. A screenshot is attached.

And do-release-upgrade -c run from 22.04 also indicates such an upgrade is available:
```
dmn@Sydney-vm:~$ do-release-upgrade -c
Checking for a new Ubuntu release
New release '24.04 LTS' available.
Run 'do-release-upgrade' to upgrade to it.
```

---

### Post by mar.ste on 2024-07-25
> **deadflowr said:**
> It's not 6 months until the upgrade is available, it's usually just over 3 months.
The upgrade path should be available mid-August. (August 15th to be exact as of right now: [https://discourse.ubuntu.com/t/noble-numbat-release-schedule/35649](https://discourse.ubuntu.com/t/noble-numbat-release-schedule/35649))

The reason is LTS systems tend to dominate production environments so they want those to be as tight and error free as possible,
with as many known bugs quashed before they allow for the upgrade.

And unlike an upgrade from a non-LTS system, an LTS to LTS upgrade has to deal with 2 years of new packages and versions and stuff.
Some packages have new requirements, some packages no longer exist some packages stay the same.
There is a lot to do in order for a seamless upgrade with such systems.

Unlike a non-LTS release which tend to have all those changes slowly integrated incrementally across 3 releases.


But my personal  opinion is if you run LTS systems, you shouldn't even start considering upgrading until at least 6 months after release.
Maybe wait until the next year even. Or skip the upgrade entirely. It's perfectly fine to do so.
The LTS system is supported for 5 years with an additional 5 years of Ubuntu Pro support. So I see no rush. And that is the entire point of an LTS release.
If you're someone who runs an LTS system but upgrades as soon as the next LTS version is released, I see no reason why you shouldn't just run non-LTS releases.

Thank you deadflowr for your kind answer! It makes a lot of sense, if you think of a production server environment.
My is one of my personal computers, where I can allow myself some minor initial hiccups (I would wait if there are major issues).
Surely I can go the long way of the three cumulative upgrades, but I was hoping to have a fast track. Some "forcing" flag on do-release upgrade would have been good. Surely next upgrade I'll do non LTS also :)


[QUOTE=Dennis N]This is what I had thought too, but on July 17 the Ubuntu 22.04 Software  Updater offered to upgrade to 24.04. A screenshot is attached.

And do-release-upgrade -c run from 22.04 also indicates such an upgrade is available:[/QUOTE]

I tried also with -c flag, but on my system is still not available. It might depend on the release where you come from...

---

### Post by deadflowr on 2024-07-25
I see what Dennis N refers to.

On Ubuntu Desktop:
If you go into Software and Updates > Updates and change the Notify for new version option from For Long term support release version option to the Any new release option.
It'll show the new 24.04 release as available for upgrade.

Because Ubuntu 23.10 has hit it's end of life, Ubuntu 22.04 automatically points to the next available release as the any new release.

So if you change the setting to that instead of check for lts versions it'll actually find the 24.04 release for you.


On Ubuntu server:
you'd need to edit the file /etc/update-manager/release-upgrades
and change it from Prompt=lts to Prompt=normal


Make sense?

---

