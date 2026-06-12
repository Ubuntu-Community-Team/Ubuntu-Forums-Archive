---
title: "need help installing stuff, ie firefox updated."
date: 2017-08-19
forum: General Help
---

### Post by seekertom on 2017-08-19
Really feeling like a fish out of water these days. I'm using desktop ubuntu 17.04.
I'm trying to update my firefox ver 54, canonical 1.0. I went to mozilla site, dl the tar file  firefox-55.0.2.tar.bz2, hoping to just click install and get back to work.
dint happen. I first clicked save, as i usually do, then back to the dl arrow in ff and clicked on open. What I get is open with the archive mgr.
It reads, then in the window i see a firefox folder icon, which I dbl clk and now see the contents, including a few folders and a zillion files.
No clue, :confused: now. Don't see any install files, so what do I do from here?
or am I not doing the upgrade/install right from the gitgo?

slomovin, but never give up. pls help.
thanks, st

aug23.. reason i was looking for firefox update is hoping for an easy solve of skinny vertical scroll slider. However, y'alls input shows me the better path to happiness. Thanks for that. Each day, learn a bit more from y'all. Many thanks while I snip the ms tendrils, one by one!
btw, maybe this isnt the best way to post a comeback or thanks or whatever, for my own posts... I welcome any alternate method.
st

---

### Post by vocx on 2017-08-19
> **seekertom said:**
> Really feeling like a fish out of water these days. I'm using desktop ubuntu 17.04.
I'm trying to update my firefox ver 54, canonical 1.0. I went to mozilla site, **dl the tar file  firefox-55.0.2.tar.bz2, hoping to just click install and get back to work.**
...

Stop right there!

Okay, so the problem is you are thinking the Windows way, where you download installable files, double click, and so on. You are using Ubuntu now, so you need to understand Ubuntu is not Windows, and things are done in a different way.

I know it's a bit of reading but try to read about the package management here
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[http://www.wikihow.com/Install-Software-in-Ubuntu](http://www.wikihow.com/Install-Software-in-Ubuntu)

Basically, software in Ubuntu is handled by a package manager, which installs programs, and also keeps track of available versions and updates. Normally you don't need to download files yourself. Everything is handled by the package manager. The package manager will tell you when there is a new version to download and install.

In the particular case of Firefox, you may be getting a bit impatient that a "new version is out" and you still don't have it. Do not worry; it will be made available to you in due time. Ubuntu normally checks for updates daily, so when an update is available you will see a pop-up saying there is a new version of Firefox available, and maybe other programs as well, and it will ask you to proceed with the installation.

What I described above is the normal way to get updates. Going to a website, downloading .tar.gz, .tar.bz2, or .zip files will just confuse you at this moment, so avoid it while you are still new to Linux.

---

### Post by pqwoerituytrueiwoq on 2017-08-19
you should be able to get it by running [FONT=courier new]sudo apt-get update && sudo apt-get upgrade[/FONT]
If the package is not yet there you can get it from this ppa
[https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa)

The file you downloaded can be run you just extract it to say [FONT=courier new]~/firefox[/FONT] then run [FONT=courier new]~/firefox/firefox-bin[/FONT] (good to know in case you ever need to run a old version, the [ESR Release]("https://www.mozilla.org/en-US/firefox/organizations/"), or [one of the other builds]("https://www.mozilla.org/en-US/firefox/channel/desktop/"))

---

### Post by Impavidus on 2017-08-20
You can always get the latest version of Firefox from the Ubuntu repositories. Just run your normal upgrades, that's the easy way. There's occasionally a small delay as Ubuntu maintainers are testing the new Firefox or are tweaking a few bits for better integration in Ubuntu, but I already got [s]Firefox 55.0.1[/s] Firefox 55.0.2 from the repos. Minor releases, not fixing any security bugs on Linux, may be skipped.

---

