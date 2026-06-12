---
title: "Ubuntu Pro?"
date: 2024-02-18
forum: General Help
---

### Post by Gottier on 2024-02-18
I'm confused about the software center suddenly telling me I need Ubuntu Pro to update stuff applications on my computer. I may have some applications that aren't from the standard Ubuntu repositories, and I can't have Ubuntu Pro messing with that. Is there a way to bypass the need for Ubuntu Pro? Does everyone just need Ubuntu Pro now to do anything with Ubuntu moving forward?

I'm a web developer, so have a common LAMP stack, node, Filezilla, Sublime Text, SQLyog running on Wine, Dropbox, Chrome, Meld, etc. If there's a way to disable the need for Ubuntu Pro, it's not being presented.

I just want to use my computer and feel like I trust Ubuntu to keep taking care of my software updates without something like this.

---

### Post by TheFu on 2024-02-18
If you search these forums, what Ubuntu Pro is and isn't is spelled out. Of course, google will find the Ubuntu Marketing page for "Pro" too.

TL;DR - "Pro" is marketing of an added level of longer support.  **It provides additional support.**  The fact that you may not have known about the lack of support you were already under (and had been for the last 15 yrs) could be an issue.  They are just highlighting it so you are aware now.  Some call that FUD. Some call it clever marketing.

Whether we choose or don't choose to have added support or longer support, is a personal/management choice. I don't choose to do that. You should learn more about it so you can clearly convey the options to your management and make an informed decision.

If you want all the support possible, you have 2 real choices.
Stick with LTS Server releases and move from LTS to LTS every 2 yrs.
Or 
Stick with LTS Server releases, sign up for Pro, and run an LTS for 5 yrs, perhaps 9 yrs, before you need to migrate to a new release.

As a developer, you know the longer you wait to migrate released, the harder it is.  I find that 4-5 yrs is long enough that I don't feel like I'm constantly migrating, but still usually don't have too many underlying library changes that I've forgotten about major diversions from different languages or their toolkits I may be leveraging.  

Ruby was constantly changing their language or Rail - basically, every year, one of those things seemed to completely change, so I couldn't get onto new projects for all the re-work on old projects that was required.  After 5 yrs of trying to figure out how to make it write once and have it work for 20 yrs, I gave up and ran back to Perl.  I have perl scripts from the early 1990s that still run flawlessly.  I've written webapps in perl (Mojo and Dancer) in 2015 that are still working and migrate easily to new OSes. Even though Perl and Ruby and Python were all created around the same time (early 1990s), Perl was created by a linguist with his eyes on the future. He ensured it was feature rich and provided options.  Larry still watches over Perl, though many other people are part of the language team.

Why would anyone use Filezilla when you have a Linux workstation?  Any file manager supports whatever filezilla does.  

Meld rocks, however.  I'd wonder exactly how do you think meld could be hacked?  You're a developer.  It is a standalone program. No networking.  If someone is in a position to hack meld, you have bigger issues.  OTOH, if there is a bug in meld that breaks your workflow, the way to get a newer version under Ubuntu would be to move to a new release, since non-security patching is unlikely to be backported to an older release.

Anyway, go read the forum posts on Ubuntu Pro. There must be 10 threads about it, easily found.

---

### Post by #&amp;thj^% on 2024-02-18
> **Gottier said:**
> 
I just want to use my computer and feel like I trust Ubuntu to keep taking care of my software updates without something like this.

that would be nice, but at times it takes the user to decide their comfort level of security or ease of use.
```
sudo cat /var/lib/update-notifier/updates-available
[sudo] password for me: 

Expanded Security Maintenance for Applications is not enabled.

76 updates can be applied immediately.
To see these additional updates run: apt list --upgradable

Enable ESM Apps to receive additional future security updates.
See https://ubuntu.com/esm or run: sudo pro status

```
and more:
```
sudo pro status --all
SERVICE          AVAILABLE  DESCRIPTION
anbox-cloud      no         Scalable Android in the cloud
cc-eal           no         Common Criteria EAL2 Provisioning Packages
cis              no         Security compliance and audit tools
esm-apps         yes        Expanded Security Maintenance for Applications
esm-infra        yes        Expanded Security Maintenance for Infrastructure
fips             no         NIST-certified FIPS crypto packages
fips-preview     no         Preview of FIPS crypto packages undergoing certification with NIST
fips-updates     no         FIPS compliant crypto packages with stable security updates
landscape        yes        Management and administration tool for Ubuntu
livepatch        yes        Current kernel is not supported
realtime-kernel  no         Ubuntu kernel with PREEMPT_RT patches integrated
ros              no         Security Updates for the Robot Operating System
ros-updates      no         All Updates for the Robot Operating System

This machine is not attached to an Ubuntu Pro subscription.
See https://ubuntu.com/pro

Supported livepatch kernels are listed here: https://ubuntu.com/security/livepatch/docs/kernels

```

I guess you could just patch by hand.

If your comfortable with not seeing that window shown:
```
sudo pro config set apt_news=false
```

BTW you can also re-enable it later:
```
sudo pro config set apt_news=true
```
To Check:
```
pro config show apt_news
apt_news True

```

---

