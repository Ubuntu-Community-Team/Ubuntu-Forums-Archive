---
title: "Firefox train wreck, has no option for 'auto update'"
date: 2015-01-10
forum: General Help
---

### Post by adambond on 2015-01-10
Im running Ubuntu 12.04. 

I know I know, thats prolly the problem. I used to update Ubuntu religiously, until that became a constant trainwreck issue aswell. I have a version I like, and would like to stick with it. 

Is there any possible way I can update firefox to work with 12.04, or find some browser that will?  Chrome is even buggy every now and then. 
Supposedly, when you go to HELP, and ABOUT FIREFOX, it automatically looks for updates. However, mine doesnt. 

So I go into preferences and ADVANCED to click CHECK FOR UPDATES. But that option isnt even there also. Just says CHECK FOR UPDATES for SEARCH ENGINE. 


If I have to do a clean install, or something like that, im just gonna ditch Ubuntu all together.

---

### Post by dFlyer on 2015-01-10
My advice is to upgrade to 14.04 which is very stable and is LTS. Otherwise you might be able to download the source for Firefox and compile it yourself.

---

### Post by kostkon on 2015-01-10
What's your problem exactly?

---

### Post by kerry_s on 2015-01-10
theres a ppa for firefox.
[https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa?field.series_filter=precise](https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa?field.series_filter=precise)

---

### Post by lisati on 2015-01-10
I'm curious..... In the years I've been running some flavour of Ubuntu, the updates I've received from time to time through update-manager have been sufficient to keep me happy. And yes, I'm currently running Firefox on 12.04.

---

### Post by kerry_s on 2015-01-10
> **lisati said:**
> I'm curious..... In the years I've been running some flavour of Ubuntu, the updates I've received from time to time through update-manager have been sufficient to keep me happy. And yes, I'm currently running Firefox on 12.04.

what version?

firefox gets faster with each release, that ppa is currently firefox 35, which i'm using & it is fast. faster then i remember anyway. lol

---

### Post by lisati on 2015-01-10
> **kerry_s said:**
> what version?

firefox gets faster with each release, that ppa is currently firefox 35, which i'm using & it is fast. faster then i remember anyway. lol

Version 34.0 here, and its speed is adequate to my needs. Doesn't worry me too much if I don't always have the latest, as long as it works and any needed security updates come through.....

---

### Post by Irihapeti on 2015-01-10
The idea seems to be that the version of Firefox that comes with the system doesn't get updated from Mozilla directly, but through the repositories.

If you don't like that idea, then you can either download Firefox directly from Mozilla and update it yourself, or use Ubuntuzilla, which manages the update process (from Mozilla) for you.

---

### Post by deadflowr on 2015-01-11
I run this
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ubuntu/ppa)
which you can run along side the normal version.
For nightly builds (well, really weekly builds) it's unbelievably stable.

Benefit is since it installs a firefox with a new-different name (firefox-trunk) it doesn't replace the current version, but instead adds a second version.

Yes, and this is precise(12.04)
no need to upgrade, precise still has 2 years and a couple of months left in the tank.

Perhaps the OP could explain what odd update problems they've had
[COLOR=#000000] > I used to update Ubuntu religiously, until that became a constant trainwreck issue aswell.[/COLOR]

I update fanatically, and don't see trainwrecks, so...

---

### Post by Dennis N on 2015-01-11
> Supposedly, when you go to HELP, and ABOUT FIREFOX, it automatically looks for updates. However, mine doesnt.

Ubuntu's Firefox is being updated through the normal software update process, and that applies to all supported releases, including 12.04.

You are remembering perhaps the Windows version which does look for and installs its own updates. If you go with the Linux version offered through Mozilla's website, it also does its own updating in the way you describe. Ubuntu releases seem pretty much in step with those and may also offer some special mods for Ubuntu.

---

### Post by Impavidus on 2015-01-11
> **Dennis N said:**
> Ubuntu's Firefox is being updated through the normal software update process, and that applies to all supported releases, including 12.04.
+1 to this. No need for PPAs or Firefox updating itself, all should be handled automatically. Which tells us your package manager is broken. Running these two commands and posting the output will give us some useful diagnostics:```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by buzzingrobot on 2015-01-11
The current Firefox version in the repos for Precise is 34.0.  That's the same version available for all other current releases.

Firefox updates are provided via the normal update procedure, not through the internal Firefox function.

---

### Post by adambond on 2015-01-11
Thanks for all the outstanding replies. I will start with checking my update manager.

I have no doubt that I have caused most of my troubles. But it is essence, to avoid Upgrading. I do not want to go to Ubuntu 14.  And so, on my update manager, can I actually 'Update' without 'Upgrading'?

[ATTACH=CONFIG]259171[/ATTACH]   It has the 'upgrade' and the 'update' as being seperate. But, below in the descriptoin of the update, it seems to say it will install v14.

If that is the case, i guess what I need is, a method to update my browsers, without upgrading the operating system (if there is such a thing). I realize such a solution may have already been posted above. I am currently going through and reading everything posted, througoughly.

---

### Post by SeijiSensei on 2015-01-11
The "update" command tells apt-get to download the latest package lists from the repositories you use.  It doesn't affect the installed software on the machine.  The "upgrade" command replaces any updated packages on your machine with their newer versions.  "Upgrading" does not mean replacing one version of Ubuntu with a more recent one.  You should routinely upgrade your system to ensure you have the latest versions of the packages with any security fixes that may have been added.

---

### Post by adambond on 2015-01-11
Well, for lack of time and understanding im gonna try and 'update'. In the past ive had major problems with updating. So hopefully, it will work better this time.

Im currently backing up the Home folder. Then i'll try the update.

---

### Post by deadflowr on 2015-01-11
700 MB of Updates for Precise.
Have you ever ran an update?

Note, also if you were to click on the button marked Upgrade up top, it won't actually start the upgrade process to Trusty. You'll have several pop-up windows to get through before that happens, at which point you can still cancel at anytime. The upgrading happens when you click on the upgrade button on the page that lists how much will be downloaded and how long it will take. The page has a details dropdown w/ arrows to show you what will be installed upgraded and removed.

---

### Post by adambond on 2015-01-11
Yes. I used to update on schedule. But after running into problems after each update, i just quit doing it.

---

### Post by efflandt on 2015-01-11
"Install Updates" installs updates for your current Ubuntu version. If you do that sometime after Updates pops up as a reminder, you may want to hit the "Check" button again just to make sure you have most recent list (in case some updates were since updated or replaced).

"Upgrade" button next to the 14.04.1 is the only button that would begin an upgrade to that Ubuntu version.

I have been running 64-bit 12.04 for years doing whatever updates for that were suggested, up until I did a fresh 14.04.1 install about a week ago. I don't have separate /home partition, so I did a cp -r of my home to ext4 partition on USB drive, then back after install (took awhile on USB 2.0). The only snag I ran into is that I had been running a newer nvidia driver version in 12.04, which worked fine with my new GTX 750 Ti. But nvidia-current in 14.04 is still the old 304 version that 12.04 used which does not support new Maxwell chips. So I had to do some apt-get juggling in the shell to purge/install a newer nvidia version before X worked.

---

### Post by Sef on 2015-01-11
> [COLOR=#000000]Yes. I used to update on schedule. But after running into problems after each update, i just quit doing it.[/COLOR]

What problems were you getting?

---

### Post by adambond on 2015-01-11
Thats the majority of the problems Ive had i believe. nvidia complications. Kinda hard to get online and get help, when the monitor wont work lol. 
But, i'll boot over to windows if need be after this update. Waiting on this backup at the moment. Will probably take 5hrs.  

[COLOR=#b22222]Another question while I wait.[/COLOR] Ive already 'backed up' in the past. And ofcourse its a pretty big file. Now that im backing up again, it seems as though its making a totally different file? Wouldnt it just update the previous backup?  Is there a way to make it do that, as i'll be low on disk space if im not careful.

---

### Post by SeijiSensei on 2015-01-11
Rsync only copies files on the source that are newer than, or not present on, the target.

```

cd /
sudo rsync -av home /path/to/backup/location

```

Type "man rsync" at a prompt to get its "[manual page]("https://rsync.samba.org/ftp/rsync/rsync.html")."  Rsync has a **lot** of options, but just using "**-av**" will make an "**a**rchive" copy of the source with a "**v**erbose" list of the files transferred.

---

### Post by whitesmith on 2015-01-11
Please learn more about Ubuntu and Firefox before bashing them. I'm on Ubuntu 14.04 LTS and Firefox 34. I get regular FF updates through the Ubuntu update process, although these sometimes lag behind downloads from Mozilla. I'm not really interested in whether I run FF 34.0 from the Ubuntu repos or FF 34.01 from Mozilla as long as both are operational, feature-rich and secure. I can assure you that Ubuntu offers updated software that satisfies both criteria. Loosen up and enjoy your freebies. Your implied threat to return to costly commercial software is covered by the first link in my sig line. Regards (meant sincerely). Have a good day (also meant sincerely).

---

### Post by adambond on 2015-01-11
I would never got back to windows. Theres plenty of other options out there. 
My intention of having a operating system, is to have one that essentially stays the same after each update. Instead of changing things so drastically every time, I have to spend several hours the next day, relearning where this menu suddenly went, where that menu went, why this menu was deleted, oh wait,it wasnt deleted, it was renamed! etc etc. 
Some of us, use a computer as a tool. Not a hobby. Would be nice if the tool did not change function and form with every update.

---

### Post by buzzingrobot on 2015-01-11
> **adambond said:**
> 
My intention of having a operating system, is to have one that essentially stays the same after each update.

Operation of Ubuntu Unity has not changed significantly since 12.04, although it is considerably faster and more polished. 

Firefox, of course, is not a Canonical product. Mozilla made a specific and well-publicized decision some time ago to release more frequent updates to Firefox, and did adopt a new look a few releases ago, which seemed to annoy some people. (I believe the older interface is available as an addon theme.) Distributions would be foolish to package older Firefox releases Mozilla no longer supports.

If Firefox is originally installed as a package from Canonical, as it is in a default Ubuntu install, then any updates released by Mozilla are made available in the routine Ubuntu updates. Installing Firefox directly via an archive from Mozilla means the user becomes responsible for updates as well as resolving conflicts that may arise with Ubuntu packages.

If you are really looking for a Linux distribution that is as unchanging as you describe, you ought to consider looking at Debian Stable or, better yet, CentOS 7, which is a recompilation of RHEL 7. Once released, RHEL, and, hence, CentOS, see minimal feature updates.  The Firefox that ships with RHEL/CentOS is Mozilla's ESR version ([https://www.mozilla.org/en-US/firefox/organizations/faq/](https://www.mozilla.org/en-US/firefox/organizations/faq/)) which targets organizations and enterprises that don't want to deal with Firefox updates every month or so.

(RHEL 6/CentOS 6, released in 2011, actually still use the Gnome 2 desktop from that year, and will be supported for several more years. However, a number of their core components also date to 2011 and have not been updated, making use of current desktop applications sometimes problematic.)

---

### Post by adambond on 2015-01-11
Thanks

---

### Post by mörgæs on 2015-01-12
If an unchanging operative system is important then a fresh install of Ubuntu 14.04.1 is also an option. Though it's not as steady as the distros mentioned above it's still expected to be fairly constant all the way to 2019.

The important part is that you do something now about your un-updated system, which translates to 'security breach'.

I would do a backup, install a clean 14.04.1 and apply all updates, change all web passwords which have been entered into your present system and from now on apply all updates within the 14.04 family as soon as they are available. Updating to another release number is dangerous but upgrading within a release should be done by routine.

---

### Post by adambond on 2015-01-12
Ok. Clicked INSTALL UPDATES. It chugged along for a while. Then this popped up.  [ATTACH=CONFIG]259207[/ATTACH]

Havent restarted yet.

---

### Post by adambond on 2015-01-12
So at the end, it said 1 package downloaded but not installed. So i went ahead and clicked to install it and got this. 
[ATTACH=CONFIG]259208[/ATTACH]

---

### Post by buzzingrobot on 2015-01-12
One thing comes quickly to mind:

You need to preface those apt-get commands with "sudo".  Eg., "sudo apt-get update", "sudo apt-get upgrade", "sudo apt-get install -f".

You also have at least one PPA installed. PPA's are a potential problem in a system that hasn't been updated for so long.

I agree with the suggestion to do a backup of the files you want to retain and then do a clean install of 14.04.1.

---

### Post by adambond on 2015-01-12
how do I uninstall the PPA

---

### Post by adambond on 2015-01-12
Using 'software sources' I can disable the PPA's. Would that be ok to disable, then finsish the update?

---

### Post by buzzingrobot on 2015-01-12
> **adambond said:**
> Using 'software sources' I can disable the PPA's. Would that be ok to disable, then finsish the update?

Yes, do that and try the update.

---

### Post by adambond on 2015-01-12
Just not sure which PPA's to disable.[ATTACH=CONFIG]259214[/ATTACH]

---

### Post by buzzingrobot on 2015-01-12
Good question. I'd disable all of them.  If the updates works, then enable each, one at a time, do another update and see if that update works.

---

### Post by adambond on 2015-01-12
With all PPA's disabled, still same failure to install.

---

### Post by adambond on 2015-01-12
Ok, got it to install vie the terminal (thanks for the sudo tip).  Im gonna restart. Hopefully wont see you back here on Windows.

---

### Post by adambond on 2015-01-14
The updates went well. Thank you very much for the help. :KS

---

### Post by Irihapeti on 2015-01-14
Good to hear!

Could you mark the thread as "solved" (use the Thread Tools at the top of the page).

---

