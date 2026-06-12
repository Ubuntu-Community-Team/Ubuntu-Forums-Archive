---
title: "Xubuntu 12.04.5 &quot;Unsupported Packages&quot;. Why?"
date: 2014-10-11
forum: General Help
---

### Post by mikodo on 2014-10-11
While reading [SIZE=2][LTS, why should I upgrade from 12.04 to 14.04 when 12.04 support is to 2017]("http://ubuntuforums.org/showthread.php?t=2247238")[/SIZE]  I thought I would look at my Xubuntu version and packages.

I wonder why I have Unsupported Packages. I have updated etc.

Is it maybe in part, because of my PPA's I have for sources? See link below.

I have brought forward files (documents), from Ubuntu 10.04, that I still have on disk, but don't use, due to EOL.

I'm not ready to install Xubuntu 14.04, just yet.

Please see below:

[http://pastebin.ubuntu.com/8542586/](http://pastebin.ubuntu.com/8542586/)

[/etc/apt/sources.list]("http://pastebin.ubuntu.com/8543250/")

This didn't help:
>  sudo apt-get autoclean
Should I worry?

Thanks.

---

### Post by nerdtron on 2014-10-12
Does "sudo apt-get update" shows any errors?

---

### Post by ian-weisser on 2014-10-12
"Unsupported Packages" include PPAs, Third-Party Repositories, and obsolete (withdrawn) Ubuntu packages that you still have installed.

You should worry only that:
1) All the non-Ubuntu software, and their unreliable versioning and conflicts, may block the package manager from installing security updates.
 2) Breakage in that non-Ubuntu software will be difficult or impossible for us to help you with.
3) Someday when 12.04 goes out of support you will likely need to reinstall rather than upgrade to 16.04.

In other words, your rather complex setup means that you will someday learn the details of package management, how to troubleshoot it, and how to fix it.

---

### Post by mikodo on 2014-10-12
> **nerdtron said:**
> Does "sudo apt-get update" shows any errors?

None! When it does, I usually run, "sudo apt-get dist-upgrade". That usually fixes it and/or, I sometimes need to remove some PPA respoitory(s), from sources.

> **ian-weisser said:**
> "Unsupported Packages" include PPAs, Third-Party Repositories, and obsolete (withdrawn) Ubuntu packages that you still have installed.

You should worry only that:
1) All the non-Ubuntu software, and their unreliable versioning and conflicts, may block the package manager from installing security updates.
 2) Breakage in that non-Ubuntu software will be difficult or impossible for us to help you with.
3) Someday when 12.04 goes out of support you will likely need to reinstall rather than upgrade to 16.04.

In other words, your rather complex setup means that you will someday learn the details of package management, how to troubleshoot it, and how to fix it.

I have been sick. I plan to new install Xubuntu 14.04, when I can. I will try to stay within the Ubuntu Repositories after that. To learn new details is, *not in the cards*, for now. 


Thank you both.

---

### Post by Impavidus on 2014-10-12
Checking my own system using those commands (ubuntu-support-status --show-all) I get this:

1 package cannot be downloaded any more. This is google earth, which I installed manually from a .deb. This makes it quite logical. It automatically added a ppa, but that ppa provides version 6, whereas the .deb had version 7.

110 packages unsupported: celestia, gthumb, gufw and many others. Pretty standard stuff, some even installed by default I think. Must somehow  mean provided, but not supported, by canonical.

69 packages supported until February 2015 (9 months): hugin, texlive and a  bunch of libraries, amonst others, all installed from the official  repos. Not really sure what it means.

8 packages supported until July 2015 (also 9 months, but counting from September): kernel images and headers. No big deal, they are never upgraded anyway. Their metapackages are, and completely new packages are then provided with the actual updated versions.

197 packages supported until May 2017 (3 years): All the standard Xubuntu stuff, like abiword, gnumeric, xfce4-power-manager.

1530 packages supported until May 2019 (5 years): the stuff common with Ubuntu. Almost 80% of the packages actually.

This was a fresh install of Xubuntu 14.04 and I added only few packages, no PPAs (except for the google one). So your situation seems normal. But still, best to move to 14.04 before your Xubuntu 12.04 hits end of life.

---

### Post by mikodo on 2014-10-12
> **Impavidus said:**
> Checking my own system using those commands (ubuntu-support-status --show-all) I get this:

1 package cannot be downloaded any more. This is google earth, which I installed manually from a .deb. This makes it quite logical. It automatically added a ppa, but that ppa provides version 6, whereas the .deb had version 7.

110 packages unsupported: celestia, gthumb, gufw and many others. Pretty standard stuff, some even installed by default I think. Must somehow  mean provided, but not supported, by canonical.

69 packages supported until February 2015 (9 months): hugin, texlive and a  bunch of libraries, amonst others, all installed from the official  repos. Not really sure what it means.

8 packages supported until July 2015 (also 9 months, but counting from September): kernel images and headers. No big deal, they are never upgraded anyway. Their metapackages are, and completely new packages are then provided with the actual updated versions.

197 packages supported until May 2017 (3 years): All the standard Xubuntu stuff, like abiword, gnumeric, xfce4-power-manager.

1530 packages supported until May 2019 (5 years): the stuff common with Ubuntu. Almost 80% of the packages actually.

This was a fresh install of Xubuntu 14.04 and I added only few packages, no PPAs (except for the google one). So your situation seems normal. But still, best to move to 14.04 before your Xubuntu 12.04 hits end of life.

Well Impavidus, thank you very much, for checking your new 14.04 system and providing your explanations!

I feel a lot better about how I do things. It appears, I haven't completely screwed things.

 I  wonder why too, that some packages on a LTS, are so shortly supported.

---

### Post by Bucky Ball on 2014-10-12
Be aware that Xubuntu 12.04 LTS does NOT have support until 2017. Xubuntu has three years LTS (long-term support) rather than five and support for it will end in April 2015.

---

### Post by ian-weisser on 2014-10-13
> **mikodo said:**
> I  wonder why too, that some packages on a LTS, are so shortly supported.

Look at the repository that the packages come from.
See [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

> The repository components are: 

[LIST]
[*]**Main** - Officially supported software. 

[*]**Restricted** - Supported software that is not available under a completely free license. 

[*]**Universe** - Community maintained software, i.e. not officially supported software. 

[*]**Multiverse** - Software that is not free. 

[/LIST]


Main and Restricted software is supported for the full LTS period of the appropriate flavor of Ubuntu.
Universe and Multiverse are not supported by the Ubuntu community (nor Canonical) anyway.

On my system 90% of packages are in Main, and are supported for 5 years.
Of the remainder: 
- Some are kernel packages (in Main) that will be updated with 14.04.2 or 14.10.
- The rest are all Universe packages. I installed them.

---

### Post by mikodo on 2014-10-13
> **ian-weisser said:**
> Look at the repository that the packages come from.
See [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)



Main and Restricted software is supported for the full LTS period of the appropriate flavor of Ubuntu.
Universe and Multiverse are not supported by the Ubuntu community (nor Canonical) anyway.


Thanks again, ian-weisser!

So then, the Universe and Multiverse repositories are suspect. Should one not use them, and be careful with PPA's? Or, one (like me), needs to do what you said in an earlier post, and learn more about package management? <-- I think, that is my answer.

---

### Post by Bucky Ball on 2014-10-13
Be careful with third-party PPAs. Some can die without notice and then you will never get an update for that package, just problems. I personally try to avoid them. ;)

---

### Post by ian-weisser on 2014-10-13
> **mikodo said:**
> So then, the Universe and Multiverse repositories are suspect.

There's a lot of great, stable software software in Universe, and Multiverse.
It's just that support for those is handled upstream.

If you are looking for some software, and discover appropriate applications in both Main and Universe, do try both. Use the best tool for you.

---

### Post by mikodo on 2014-10-13
> **Bucky Ball said:**
> Be careful with third-party PPAs. Some can die without notice and then you will never get an update for that package, just problems. I personally try to avoid them. ;)

Thank you, Bucky Ball.

I guess I need to do that. Damn shame but, I need to be safe. C'est la vie!

To get newer stable applications, do you build them yourself?

---

### Post by Bucky Ball on 2014-10-13
> **mikodo said:**
> 

To get newer stable applications, do you build them yourself?

Tough question in as much as a newer version of any application may not be stable on your particular release. If we take, for example, something like VLC, then the most appropriate version for your release will be already in the official Ubuntu repos (= software centre).

If you are keen for the latest and greatest, use the latest (but not always greatest!) Ubuntu release. 14.10 is out at the end of October and you could install that and see if there is a different version of whatever it is you are looking for. Be aware that interim releases (i.e. not LTS) are supported for nine months only. But you probably know that already.

I use Xubuntu (minimal install with xfce4 desktop environment actually) and LTS releases only, so don't really need latest and greatest. If it ain't broke, don't fix it is my theory! Which app, specifically, are you wanting to get to the newest version of? ;)

---

### Post by mikodo on 2014-10-13
> **ian-weisser said:**
> There's a lot of great, stable software software in Universe, and Multiverse.
It's just that support for those is handled upstream.

If you are looking for some software, and discover appropriate applications in both Main and Universe, do try both. Use the best tool for you.

Thanks!

Try them and then learn to watch for errors, I guess.

---

### Post by mikodo on 2014-10-13
> **Bucky Ball said:**
> Tough question in as much as a newer version of any application may not be stable on your particular release. If we take, for example, something like VLC, then the most appropriate version for your release will be already in the official Ubuntu repos (= software centre).

I use Xubuntu (minimal install with xfce4 desktop environment actually) and LTS releases only, so don't really need latest and greatest. If it ain't broke, don't fix it is my theory! Which app, specifically, are you wanting to get to the newest version of? ;)

I forget (old guy), but there have been occasions, where the newer app, in the PPA, did provide functionality that I couldn't get in main repos. Most of the time (until now), I just thought it would be nice to have the newest and freshest. Having said that, I am really going to the stable scenario now, so it won't be a hardship to stick close to the release's apps. I am even going to try to stick to just what is in Debian Stable (I have often multibooted distro's for fun), but knowing how to manage the libraries is above me, so Xubuntu LTS and Debian Stable, are my future.

Thanks.

---

### Post by ian-weisser on 2014-10-13
> **mikodo said:**
> To get newer stable applications, do you build them yourself?

The purpose of an LTS release (12.04, 14.04) is that applications don't change versions over the 5-year life of the release. Your workflow won't be disrupted by an unexpected change from an upgrade.
The "Stable" part of LTS refers to that lack of change. It does _not_ mean that the applications are somehow more stable...though the 4-year cycle of LTS development does indeed lend itself to extra bugfixing right before the LTS release.
 
There are many possible answers to your question, and everyone will have a different opinion.

My opinion is that if you like your applications stable (unchanging), and you like your workflow unchanged, and you prefer a massive disruption/migration every two or four years, then LTS releases of Ubuntu are more appropriate for you.

If you prefer newer applications, incremental changes that are more frequent, and the risk of small disruptions to your workflow each time, then the 6-month releases of Ubuntu are more appropriate for you.

---

### Post by mikodo on 2014-10-13
> **ian-weisser said:**
> The purpose of an LTS release (12.04, 14.04) is that applications don't change versions over the 5-year life of the release. Your workflow won't be disrupted by an unexpected change from an upgrade.


My opinion is that if you like your applications stable (unchanging), and you like your workflow unchanged, and you prefer a massive disruption/migration every two or four years, then LTS releases of Ubuntu are more appropriate for you.

Yes, that is me now ian-weisser. But, there have been occasions, (I forget which apps), that didn't work or provide what I needed in functionality, when getting the older versions in the repos, in the LTS's. That is when I thought I would "build the newer versions", and now I know, I need to learn to watch them for inconsistencies, with the LTS/Stable release I am using.

Thank you.

---

