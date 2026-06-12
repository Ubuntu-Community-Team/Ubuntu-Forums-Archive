---
title: "What is upgrading like?"
date: 2013-02-07
forum: General Help
---

### Post by evilbrent on 2013-02-07
I'm currently on 10.04 LTS but running out of excuses to not upgrade to 12.04.

What's it like? Will it bork everything?

Will I have to download all the packages and install all my programs again? 

I get the impression that it's SUPPOSED to just change the OS, not the packages/file structure, but am I completely wrong about that?

I will back up all the files first, as a matter of course. It's just that I've never updated a Ubuntu before, it keeps asking me to upgrade and I keep putting it off for fear of it going badly.

---

### Post by PhilGil on 2013-02-07
It's supposed to work as you described, upgrading the OS and all your programs without borking your data and file system. Ubuntu upgrades tend to be hit or miss, with some users reporting that the process was trouble free while other people have lots of problems.

Off the top of my head, here are a few things you can do to improve your chances of a trouble-free upgrade. The idea being that the closer your 10.04 install is to stock the better things should go.

1) Be sure your Lucid system is up to date and that all upgrades have been done.

2) Uninstall any programs you've obtained from 3rd party repositories and remove or disable the repositories.

3) If you are using a non-standard theme, I'd return to Ambience or Radiance during the upgrade.

4) You may want to do a dry run of Precise from a CD or USB drive to see if there are any driver regressions you'll need to troubleshoot after the upgrade.

5) Back up, back up, back up (at least your home folder and any data partitions you keep). Depending on your system, there may be other configuration files you'd like to back up, such as xorg.conf and/or smb.conf. Config files can be a pain to recreate after an upgrade.

---

### Post by deadflowr on 2013-02-07
> I get the impression that it's SUPPOSED to just change the OS, not the packages/file structure, but am I completely wrong about that?

An upgrade upgrades the entire system, so if any package installed has a newer version it too will be upgraded.

Some packages, like openoffice have been replaced. (Openoffice has been replaced with libreoffice.) Thunderbird is the new default email client. And several others as well.

What an upgrade won't do is mess with any of your stuff in your home folder.

As far as the file structure, 12.04 is basically the same as 10.04 with changes to various files here and there.

If you're going to go for it, my suggestion is to always backup whatever you feel is important, just in case.

Upgrades are pretty reliable though.

---

### Post by QIII on 2013-02-07
In addition to uninstalling third party software, make sure to uninstall any proprietary hardware drivers -- particularly video drivers.

Not doing so is one of the quickest ways to have a significant emotional event associated with the upgrade.

And I'll repeat this:  Back up, back up, back up.

---

### Post by BBQdave on 2013-02-07
> **deadflowr said:**
> If you're going to go for it, my suggestion is to always **backup whatever you feel is important**, just in case.

+1 - Save yourself some pain, and back up your data on a separate drive :)

Personally, I have always backed up my data on a separate drive - and then did a fresh install. Some what similar to you, I was cruising along on Debian 6 with Gnome 2. My hardware was starting to show signs of failure - so with new hardware, I did  a fresh install of Ubuntu 12.04 and copied over my saved data. Quick and easy set up of new hardware and new LTS :D

---

### Post by DuckHook on 2013-02-07
**BACKUP** **BACKUP** **BACKUP**

Did I mention, backup first? Thousands upgrade with no problems. Those that run into problems can be separated into two groups: A mildly frustrated gang who have the luxury of knowing that their data is safe and the worst shape they will be in is being forced to make a clean install (20 minutes). The frantic heart-pounding nail-biting crowd desperately begging this forum for a miracle that will salvage the priceless photos they've lost because they... I'm flogging a dead horse, I know, but I've just tried to help 3 lost souls over the past 2 days trying to recover data from a bad upgrade.

As for the upgrade itself:

1. Are you sure you want Unity? It sounds like you've run the LiveDVD and know what you are getting, but many have used this opportunity to go to Xubuntu or Lubuntu to retain a more traditional DE.

2. Have you considered a clean virgin install? This is the best way to install, in my opinion. You don't inherit any wonky settings, misconfigurations or inappropriate configs from the old system.

3. A clean install also gives you the opportunity to rethink everything from your partitioning scheme to security to the apps you really need.

4. I've gone both routes and have upgraded with no problems whatsoever. However, I always find myself wishing that I'd done clean installs on my upgrades, usually due to various hindsights: should'a made a separate /home partition, should'a deleted half my apps, should'a cleaned up my caches, old kernels, etc.

5. This is just my personal neurosis, but a new install feels like a new baby, or a new toy; an upgrade feels like a used car. I'm just never sure if that wonky video/sound/USB port would have happened had I done a clean install.

---

### Post by evilbrent on 2013-02-07
Thanks guys, you've exactly given the answers I was after and some useful tips too.

FWIW, I intend to back up like crazy. I have had "significant emotional events" before and not enjoyed them or the fire rained down upon me by my lovely wife.

---

### Post by pakopako on 2013-02-08
I'd go as far as using *dd* to create an image on an external drive in case you have to restore your entire computer back in a snap.

[Examples](http://linuxpoison.blogspot.com/2009/04/creating-backuprestore-images-using-dd.html) of [using](http://ubuntuforums.org/showthread.php?t=1595195) the [command](http://ubuntuforums.org/showthread.php?t=1540873). (And a [warning](http://askubuntu.com/questions/148685/how-to-create-a-complete-recovery-image-for-my-new-netbook) before doing so.)

---

### Post by fantab on 2013-02-08
> **evilbrent said:**
> I'm currently on 10.04 LTS but running out of excuses to not upgrade to 12.04.

What's it like? Will it bork everything?

Will I have to download all the packages and install all my programs again? 

I get the impression that it's SUPPOSED to just change the OS, not the packages/file structure, but am I completely wrong about that?

I will back up all the files first, as a matter of course. It's just that I've never updated a Ubuntu before, it keeps asking me to upgrade and I keep putting it off for fear of it going badly.

I suggest CLEAN INSTALL of 12.04. The reason being Ubuntu has undergone some major changes since 10.04... (you can read '[**release notes**]("http://www.ubuntu.com/getubuntu/releasenotes")' since 10.10 for more info).

And also since you seem like an LTS to LTS guy 20-60mins of your time dedicated to clean install and customizing in 2-5 years shouldn't be a biggie. Plus you may not run into the risks of any conflicting files and packages later. Also LTS to LTS upgrades are time consuming compared to doing a clean install. 

My two cents...

---

### Post by fdrake on 2013-02-08
*one sunny day two strangers setting at the bus-stop bench started talking to each other:*

[COLOR="Red"][SIZE="4"]*_**evilbrent:What is upgrading like?**_*[/SIZE][/COLOR]

[B]
[SIZE="4"][COLOR="Purple"]Forrest Gump: My momma always said, "Upgrading is like a box of chocolates. You never know what you're gonna get." [/COLOR][/SIZE][/B]

---

### Post by wildmanne39 on 2013-02-08
+1 for a clean install, there are some significant differences that makes it hard to upgrade from 10.04 to 12.04 or above.

Plus it takes a lot longer to upgrade then it does to do a clean install and with an upgrade you will  most likely end up with a broken system.
Thanks

---

### Post by C.S.Cameron on 2013-02-08
I used to upgrade twice a year, never had a problem, except sometimes it took days and many times some programs did not upgrade.
I always feared a power outage when upgrading.

Nowadays I install fresh and reuse the /home partition. If the install is not using a /home partition, I copy the old home folder to the new install using rsync, (Grsync actually).
It is much faster than upgrading.

10.04 to 12.04 was no problem this way.

---

### Post by furything on 2013-02-08
> I used to upgrade twice a year, never had a problem, except sometimes it took days and many times some programs did not upgrade.I guess it depends how many packages you have installed to how long it takes and what breaks. The devs I believe take a long time making sure an upgrade works (I know that upgrades don't always work - believe me)

I know the pain of upgrade failures but am obviously in the minority - I always upgrade although I do this mostly from a cd/dvd as I have 6 pcs to upgrade.

I used to upgrade every 6 months as well but switched to LTS from 12.04 for mythtv boxes and kids PCs. My own box I always keep the latest GA.

As for data - all boxes bar myth are dual boot so share an ntfs partition for use as local backup. I my box/mythboxes are** backed up on a weekly basis** at minimum to external hard drives. **Regular backups of important data avoids any major pain.**

---

### Post by Stonecold1995 on 2013-02-08
> **pakopako said:**
> I'd go as far as using *dd* to create an image on an external drive in case you have to restore your entire computer back in a snap.
I can't agree more.  It takes a bit longer and you'll need a bigger backup drive, but it's literally a clone of your hard drive, which makes it REALLY easy to restore the backup.

---

### Post by Warren Hill on 2013-02-08
> **pakopako said:**
> I'd go as far as using *dd* to create an image on an external drive in case you have to restore your entire computer back in a snap.


Could not agree more upgrading can be hit and miss so you need good backups.

that said take a look here

[http://www.omgubuntu.co.uk/2012/04/ubuntu-10-04-12-04-upgrade-how-well-does-it-go]("http://www.omgubuntu.co.uk/2012/04/ubuntu-10-04-12-04-upgrade-how-well-does-it-gohttp://")

Seems its getting better

---

