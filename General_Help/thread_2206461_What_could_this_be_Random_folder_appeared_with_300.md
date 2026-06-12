---
title: "What could this be? Random folder appeared with 300,000+ items in it."
date: 2014-02-19
forum: General Help
---

### Post by stevephillipgreen on 2014-02-19
Just happened to be in my home folder when I noticed a folder i'd never seen before.. The folder is labelled "WyTJY0vmw1".. I attempted to open it and it's a complete mess of letters and numbers jumping around all over the place, the folder times out without ever finishing loading the contents so I press stop and it's just jumbled garbage. I then went to properites to see how many items are in this folder and it's 368,470 items, totalling 0 bytes.

What on earth could this be? 

[IMG]http://dl.dropbox.com/u/2528687/Selection_059.png[/IMG]

PS, I've been a Ubuntu user for nearly 7 years, I already have an forum account but I went and clicked the SSO link at the top of the page which I thought would log me into my forum account but it appears I've never used the forum before under this login.

---

### Post by TheFu on 2014-02-19
Sounds like a virus.
Recover the system from the backup the day before this all started.

Or it could be a hardware issue ... manually run fsck on the disk, check the controller, cables and disk.

---

### Post by stevephillipgreen on 2014-02-19
Thanks for the reply, On the extremely remote chance that it could have  been a virus (I've yet to encounter one in 7 years) I ran ClamAV anyway,  i've never installed or used it before as I don't see the need. Anyway,  it came back clean.

I've decided to leave the folder for the  time being, it hasn't grown in size throughout the day or anything so  i'm just going to keep an eye on it.

---

### Post by QDR06VV9 on 2014-02-19
Wow I tend to side with TheFu I find him very knowledgeable.
I'm Following this post for a bit.
Please keep us updated.
regards

---

### Post by tgalati4 on 2014-02-19
Check the SMART status of the drive.  Make sure it is working OK.  Are you sure it is not a firefox profile?  Did you install firefox manually?

---

### Post by TheFu on 2014-02-19
> **stevephillipgreen said:**
> Thanks for the reply, On the extremely remote chance that it could have  been a virus (I've yet to encounter one in 7 years) I ran ClamAV anyway,  i've never installed or used it before as I don't see the need. Anyway,  it came back clean.

I've decided to leave the folder for the  time being, it hasn't grown in size throughout the day or anything so  i'm just going to keep an eye on it.

I didn't write that "virus" term lightly.  As more and more non-technical users start using Ubuntu, I expect more and more end-user viruses to happen. Java will be the initial vector, since it can work on other platforms, but Linux desktop users are like Mac users of 7 yrs ago - no virus possible - until it is.  PDF files, javascript, breaking out of browser sandboxes will be next, then someone reputable with an honored GPG key will get their program-package hacked and end-users with sudo will install it. A trivially modified ~/Desktop/something.desktop file can sit there for years waiting until the user clicks it to do what they asked plus something else.  I've thought about this for a few years and even made a tiny test to put a front-end on sudo that nobody would notice.

The best AV tools are 50% effective.

So ... all I can suggest at this point is get your backups working and make certain the backups are versioned so changes over time can be tracked for weirdness. Backups are still the #1 security method.

---

### Post by EnglishElectricAndy on 2014-02-19
+1 regarding TheFu's observations about backing up.

My small contribution is to make sure a pristine copy of the preferred distro exists on removable media. With this, a re-install, combined with known to be clean backups, is relatively straightforward, albeit time consuming. At least there's no ferreting about for a misplaced 20-digit license code!

---

### Post by stevephillipgreen on 2014-02-20
[IMG]http://dl.dropbox.com/u/2528687/Selection_066.png[/IMG]

Well,  I deleted the folder, caused the system to completely freeze and it  wouldn't come back so hard restart and then I find this on the desktop..  Right clicking on them, they claim to be Gif images at 1x1 pixels in  size, created yesterday morning and accessed 4 hours later.. I'm not  sure if it's releated at all.

@TheFu - sorry if I came across as  slightly smug about virus possibility, I guess it's years of living  virus free on Linux after viruses caused me to ditch previous OS as I  was just sick of it.

@[[COLOR=#000000]tgalati4[/COLOR]]("http://ubuntuforums.org/member.php?u=241895") - I'm running 27.0.1 and the nightly. Smart data checks out ok.

---

### Post by TheFu on 2014-02-20
I'd wipe the entire system and restore from a pre-problem backup. You never said if that was possible. Do you have versioned backups? Heck, even a mirror from before the issue could work, though it is less useful.

If you want to do some forensics, keep the HDD and use a new one for the install and please, please, please get your versioned backups working, so when this happens again, you can determine what exactly has changed from before the issue.  [Get backup religion]("http://blog.jdpfu.com/ALE/ALE-NW/a09_backups.html") now.

With a pre-incident backup, we can compare all the current files against the backup to see if anything malicious has been done. 
How to compare directories [https://stackoverflow.com/questions/4997693/given-two-directory-trees-how-can-i-find-out-which-files-differ](https://stackoverflow.com/questions/4997693/given-two-directory-trees-how-can-i-find-out-which-files-differ)
Without a backup, we are just guessing. Where I work, we need to know the root cause and take proactive steps to mitigate the issue from happening again.

I'm not convinced this is actually a virus. Looks more like data corruption to me, but if a rootkit got installed ... who knows.
BTW, I've been cracked a few times, but not since 2002. My paranoia has served me and my clients well.  Anyone who hasn't been cracked and believes they are smart or better than others is just fooling themselves.  I honestly believe **there is not an OS made today that cannot be hacked by a targeted attacker**. The best we can hope for is to hold the script-kiddies at bay with our security setups.

Linux desktops are not immune from attacks. End-users need to practice safe-browsing setups and techniques still and they need to have their [systems properly maintained.]("http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs") Lifehacker republished that article, but I've updated it a few times since.

I've had this conversation with a few CEOs. Found myself explaining that our actions immediately after the crack is discovered needs to be planned immediately to lesson any impact, but that preventing a crack from occurring was unlikely.

---

### Post by tgalati4 on 2014-02-20
Run a memtest for 30 full cycles.  If it passes, then it might be time for a wipe and fresh install.

---

