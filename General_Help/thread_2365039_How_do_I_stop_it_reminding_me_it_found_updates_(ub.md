---
title: "How do I stop it reminding me it found updates? (ubuntu 16.04.2 Unity)"
date: 2017-07-01
forum: General Help
---

### Post by pretty_whistle on 2017-07-01
Just like the title says, how do I stop it or can I stop it?

Thanks for your help. :-D

---

### Post by vasa1 on 2017-07-01
This is after you've accepted the updates?

---

### Post by deadflowr on 2017-07-01
Run this to see the current setting:
```
gsettings get com.ubuntu.update-notifier no-show-notifications
```
the default should be false, so to change run
```
gsettings set com.ubuntu.update-notifier no-show-notifications true
```
from then on it should never tell you when updates are available.

---

### Post by pretty_whistle on 2017-07-01
> **vasa1 said:**
> This is after you've accepted the updates?

? Unsure what you mean.  It shows updates are available, listing them out, but I don't install them. I hit the cancel button (not the install button), the window leaves but then later here it is again saying same thing.

---

### Post by pretty_whistle on 2017-07-01
> **deadflowr said:**
> Run this to see the current setting:
```
gsettings get com.ubuntu.update-notifier no-show-notifications
```
the default should be false, so to change run
```
gsettings set com.ubuntu.update-notifier no-show-notifications true
```
from then on it should never tell you when updates are available.

Thanks.  The setting was set to false as you said and now it's set to true.

Ah...what a relief.  I've saved the instruction should I ever have to do a fresh install I'll have it handy.  Thanks again.  :)

---

### Post by pretty_whistle on 2017-07-02
Well it did it again anyway, reminding me it had found updates from before yesterday when I tried the command you gave here and asking me if I want to install it now.  It's reminding me of the same old update it had found days ago and won't stop asking me if I want to install it now.

I don't know if it has stopped "looking for updates" since the command I tried yesterday since it's been reminding me of an old one it found instead.

Now what?  Perhaps I needed to restart the computer after doing the above command to make it work.  I'll try it and report back........

Edit: To those reading this and to be of assistance for the novice, I've restarted the computer because sometimes doing so will solve a problem.  It has solved many problems in computing so it may solve this one.  :)

---

### Post by johndough2 on 2017-07-02
Hi

A coupla possibilities come to mind, don't connect to the internet and/or edit the repos to be blank lines.

The not connecting to the internet is quite relevant as you will potentially have a 16:04 install with no security updates as notifications are turned off and you risk being compromised.

---

### Post by vasa1 on 2017-07-02
Please post the output from ```
sudo apt-get update
```and```
sudo apt-get dist-upgrade
```and ```
pgrep update-notifier
```You can press "n" instead of "Y" after the second command.

---

### Post by deadflowr on 2017-07-02
So...
By notifications do you mean the pop-up bubble Ubuntu uses the show all notifications or,
do you mean that the updater box pops up?

If it's the updater box popping up, then open software and updates and go to updates.
Look at what the Setting say there and if any say Display Immediately.
(If they do then change that setting(s))

Also, install what you have gotten, since typically very few will be non-security related.
(An un-updated system isn't just bad for you, it is bad for all of us if you keep the machine connected to the internet)

---

### Post by pretty_whistle on 2017-07-02
> **deadflowr said:**
> So...
By notifications do you mean the pop-up bubble Ubuntu uses the show all notifications or,
do you mean that the updater box pops up?

If it's the updater box popping up, then open software and updates and go to updates.
Look at what the Setting say there and if any say Display Immediately.
(If they do then change that setting(s))

Also, install what you have gotten, since typically very few will be non-security related.
(An un-updated system isn't just bad for you, it is bad for all of us if you keep the machine connected to the internet)

The updater box/window pops up.

About going to software and updates, then going to updates, I did that already and changed it to the best I could find which is to "display immediately" for the security updates and for the "other updates" display every 2 weeks.

I know this sounds bad but I don't want to install updates yet, maybe in a couple months because it's finding too many and I have to back up the system before each one and it's a pain to keep doing it so I'd rather do updates infrequently because of the trouble.  Call me stubborn but I'm trying to rid it letting me know because of it, then when I'm ready I'll run updates manually and install it after I do a backup of the HDD.  And talk about putting me out, I already did a backup and ran updates on the 15th, then it found more kernels (already got that though on the 15th as I just said) again on the 18th.... every 3 days is too often so I need it to stop it if it can be done.

---

### Post by vasa1 on 2017-07-02
Put "pkill update-notifier" in your autostart?

---

### Post by pretty_whistle on 2017-07-02
> **vasa1 said:**
> Put "pkill update-notifier" in your autostart?

I'll try that, thanks.

---

### Post by efflandt on 2017-07-02
While I cannot say that a kernel update will never have issues, I have been running Linux in various forms for over 20 years (since before Win95), and the only issue I can think of off the top of my head was insignificant. An Ubuntu kernel update a year or 2 ago (in original 14.04) resulted in steam not running (an app for games). The simple solution in that case was to boot the previous kernel until the next kernel update which resolved that issue. I cannot think of any updates which rendered my system unusable.

But when I switch Ubuntu versions I usually install those fresh.

---

### Post by ian-weisser on 2017-07-02
One simple way to prevent notifications is to uninstall the update-notifier package...however, it's unwise to do that.
Another simple way is to use unattended-upgrades to automate the upgrades.

Debian and Ubuntu are intended to be upgraded.
Not upgrading will take you out of the normal, supported Ubuntu and send you into the unexplored paths of the wilds. 
The notifier is not offering a choice of *whether* to upgrade - it's politely offering you the choice of *when* to upgrade.

All this support forum can really offer is to advise you to install the upgrades to stop the notifications.

---

### Post by pretty_whistle on 2017-07-02
It's not about upgrading anything, just installing updates to software and security updates.

Also, I'm not about to let it automatically install kernels since one broke my system and rendered it 100% dead.  Therefore I need to do it manually after I've backed up the HDD so if it crashes I can restore it ok.

---

### Post by pretty_whistle on 2017-07-02
> **vasa1 said:**
> Put "pkill update-notifier" in your autostart?

Just a prediction here but I bet this won't work since I see "update notifier" listed as running in the System Monitor.  I'll wait and see though.....

If this keeps up, I think killing process on it in the System Monitor may be what I'll try. It may keep it quiet until the next time I restart the computer.

---

### Post by pretty_whistle on 2017-07-02
Another thing, why did it "automatically check for updates" anyway when I have it set to "never"? Maybe I need a separate thread for that question....

---

### Post by Bashing-om on 2017-07-02
pretty_whistle; Hey hey ;

My thought:
The types of updates you can do automatically are set by /etc/apt/apt.conf.d/50unattended-upgrades , which is provided by the 'unattended-upgrades' package. It's powerful - many of those options do not have a corresponding checkbox in the GUI.

Think it may Have been Ian that told me that.

[INDENT][INDENT]all in this together
[/INDENT][/INDENT]

---

### Post by pretty_whistle on 2017-07-02
> **Bashing-om said:**
> pretty_whistle; Hey hey ;

My thought:
The types of updates you can do automatically are set by /etc/apt/apt.conf.d/50unattended-upgrades , which is provided by the 'unattended-upgrades' package. It's powerful - many of those options do not have a corresponding checkbox in the GUI.

Think it may Have been Ian that told me that.
[INDENT][INDENT]all in this together
[/INDENT]
[/INDENT]


Oh. That would explain it finding kernel updates.  I may have to kill process on update notifier then, like I mentioned above.  Hopefully that would solve that sucker till a reboot & then I'll just do it again, bwahaha.

---

### Post by pretty_whistle on 2017-07-03
Well, it's now the next morning and that sucker reappeared.  Stubborn like a bratty 3 year old kid!  Ok then, I'll try the kill process idea and report back results.

---

### Post by vasa1 on 2017-07-03
Your argument about not wanting to update because backing up your HDD is a chore is a bit hard to digest. So not only are you not backing up your HDD but you aren't installing security updates despite three contributors, [deadflowr]("https://ubuntuforums.org/showthread.php?t=2365039&p=13661678#post13661678"), [efflandt]("https://ubuntuforums.org/showthread.php?t=2365039&p=13661732#post13661732"), and [ian-weisser]("https://ubuntuforums.org/showthread.php?t=2365039&p=13661745#post13661745"), suggesting otherwise. 

If you need help on how to do differential backups, efficiently both in terms of time and space, start a new thread.

---

### Post by pretty_whistle on 2017-07-03
> **vasa1 said:**
> Your argument about not wanting to update because backing up your HDD is a chore is a bit hard to digest. So not only are you not backing up your HDD but you aren't installing security updates despite three contributors, [deadflowr]("https://ubuntuforums.org/showthread.php?t=2365039&p=13661678#post13661678"), [efflandt]("https://ubuntuforums.org/showthread.php?t=2365039&p=13661732#post13661732"), and [ian-weisser]("https://ubuntuforums.org/showthread.php?t=2365039&p=13661745#post13661745"), suggesting otherwise. 

If you need help on how to do differential backups, efficiently both in terms of time and space, start a new thread.

Oh, I run a backup in 2 phases: 1) backup entire HDD right before running an update in case the update breaks the computer; 2) differential backup of desktop and Documents folders hourly and if anything is new I back it up there and then to a flash drive.

Frankly, I've looked into doing backups the best way possible and this is the best I can find given I have a laptop and that's portable so I cannot have my portable drive connected to it 24/7 placing backups on it.  Also, backing up the HDD and getting the last differential backup before running updates takes about 1-3 hours, 3 if I have to restore everything from a bad update.  I wished I could run updates every time they come up, even if that's daily, but 3 hours of backups etc a day I don't have time for- not practical.

Just saying, I do backups just not that often except for differential and entire HDD if I've made big enough changes recently.

---

### Post by leunam12 on 2017-07-04
That is a long time for a backup, I have all my system files installed on a 24GB partition and I can backup my root partition in less than 5 minutes. If an upgrade breaks the system or some functionality (and it has) I can restore in less than 5 minutes as well.

---

### Post by pretty_whistle on 2017-07-04
> **leunam12 said:**
> That is a long time for a backup, I have all my system files installed on a 24GB partition and I can backup my root partition in less than 5 minutes. If an upgrade breaks the system or some functionality (and it has) I can restore in less than 5 minutes as well.

Hmm.... a separate partition sounds good as far as location goes but I use Clonezilla and have 11 GB used up and for some reason Zilla takes 35 minutes to back it up...wait...I'm thinking of ReDo Backup, this one takes about 5-10 minutes instead. I hadn't realized it was quicker by a large degree till just now, oops. Well now, what can I say? Clonezilla is much quicker which helps a bundle.  I'm now rethinking this thing.  Question is, I'd have to get a good partition program since Gparted has a few bad reviews and I had tried it anyway only to find the same bad thing they did which was it left the area unreadable.

As a note here, I didn't mean to start talking about another topic here but it's happened by accident.  Your fault people, you brought it up! jk....lol....

Wait....backing up to another partition on the HDD?  If the HDD fails I could lose that backup. No wonder I use a separate portable drive to save a backup to.  Ok then. In any case, Zilla is a lot quicker and I have noted restoring is a lot quicker too.  Well then, I think I'll give this a try and do it more often, backing up and running updates I mean, maybe weekly?  How often would you all recommend, I'm guessing weekly....

---

### Post by leunam12 on 2017-07-04
I backup in clonezilla from an ssd to an internal hard drive that I use for storage. After backup I boot the system and use rsync to make two backup copies of my home directory and storage drive on separate removable drives. But the clonezilla operation only takes less than five minutes including boot time. I have a really fast computer, though.

---

### Post by pretty_whistle on 2017-07-04
Well, it's too bad I can't get it to not let me know about updates when it has the option to set it to "never" auto check for updates.  It's just not working!  :(  I'll just have to "kill process" on update-notifier then unless it catches me when I can do one "right then" because I may be busy that day and can't yet but it would keep letting me know anyway!

Oh well.

---

### Post by Tadaen_Sylvermane on 2017-07-04
Sounds like a job for lvm snapshots to me if you are taking 3 hours to do backups each time.

---

### Post by mc4man on 2017-07-04
purge update-notifier & unattended-upgrades, you'll not be bothered anymore. Also consider installing synaptic & purging update-manager.
> 1) backup entire HDD right before running an update in case the update breaks the computer

Unless you're using some real sketchy 3rd party repos or -proposed without paying attention the odds of that happening are extremely slim to none
Backing up entire hdd prior to simple updates seems like useless overkill

---

### Post by pretty_whistle on 2017-07-05
> **mc4man said:**
> purge update-notifier & unattended-upgrades, you'll not be bothered anymore. Also consider installing synaptic & purging update-manager.


Unless you're using some real sketchy 3rd party repos or -proposed without paying attention the odds of that happening are extremely slim to none
Backing up entire hdd prior to simple updates seems like useless overkill

The purging idea sound interesting.  I do have synaptic as luck would have it.

I've never used sketchy 3rd party repos but once, though rare, had a kernel update render my computer unusable - I couldn't reach the desktop anymore.  Though it's rare it happened so I run a backup of the HDD right before it just in case.  Luckily when that happened I did that and could restore it ok right afterwards.

One thing about synaptic, it never asks to restart the computer afterwards although if it installed kernels I'd know to restart it afterwards anyway.  Come to think of it I don't think restarting is needed any time except then anyway so no big deal to not have update manager tell me it needs to be done since I already know that.  As far as getting the latest LTS I can always run that in the terminal so I wouldn't need update manager for that one either.

Funny thing is update manager doesn't always find all the updates anyway because I always run synaptic afterwards and it sometimes finds some the other one missed so what good is it if it can't find all the updates I need?  I seem to be duplicating my efforts in updating this thing, lol.

Thanks for the post.  This got me thinking.  I'm going to do a bit more thinking and then decide to dump that off, which is where I'm going with this.....

[B]mc4m


[/B]There, now it's removed.  And I checked in the System Monitor to verify that update-notifier wasn't there upon reboot and it wasn't!  That sucker is dead dead dead!  Good.

Thanks again for the idea.  :popcorn:

---

### Post by pretty_whistle on 2017-07-05
That's funny. That last part above I wrote to mc4m was a separate post and now it's merged with the above post.  Did a mod do it or is the forum messing up?

---

### Post by Impavidus on 2017-07-05
> **pretty_whistle said:**
> 
Funny thing is update manager doesn't always find all the updates anyway because I always run synaptic afterwards and it sometimes finds some the other one missed so what good is it if it can't find all the updates I need?  I seem to be duplicating my efforts in updating this thing, lol.


See [phased updates](https://wiki.ubuntu.com/PhasedUpdates).

I never backup my system, only my documents. If my system breaks beyond repair, I just reinstall. Although that never happened in over 10 years of using Ubuntu. I once had an upgrade to grub break my system, but I could fix that in ten minutes.

---

### Post by pretty_whistle on 2017-07-05
> **Impavidus said:**
> See [phased updates]("https://wiki.ubuntu.com/PhasedUpdates").

I never backup my system, only my documents. If my system breaks beyond repair, I just reinstall. Although that never happened in over 10 years of using Ubuntu. I once had an upgrade to grub break my system, but I could fix that in ten minutes.

Phased updates? Interesting.  I read the blog and it said this :

> **Who is participating?**[COLOR=#29303B][FONT=&quot]Users of Ubuntu 13.04 who install updates with update-manager are automatically participating in this process. For every package, in -updates, update-manager will generate a random number and if that number is less than the Phased-Update-Percentage the package will be installed. One can opt out of the Phased Update process by adding ‘Update-Manager::Never-Include-Phased-Updates “True”;’ to the configuration file “/etc/apt/apt.conf”.

I wished it said which file to add that too since there are several in that folder. Ho hum....  :?

Interesting this process is with Update Manager and not Synaptic.  Technically then it's a bit risky to use it then since I could get one of those updates.  With Update Manager, there may be a chance if I'm in that phased percentage of random users.

Interesting.


[/FONT][/COLOR]

---

### Post by pretty_whistle on 2017-07-05
[B]Impavidus
[/B]

You know it seems to me I have a way to opt out of the phasing mentioned above if I simply ran Synaptic, wait 3 days, run it again and then install anything it finds, thereby bypassing the 3 day window of phasing updates.

---

### Post by pretty_whistle on 2017-08-02
Update :

Removing update manager solved this for me, that is for the reason why I made this thread.  I'm using Synaptic instead.

I don't know if marking it solved would be appropriate since the problem would still exist had I not removed it.  I don't know so I'll mark it solved and it leave it up to readers as to whether they care to do this to solve it.

---

### Post by deadflowr on 2017-08-02
> I don't know if marking it solved would be appropriate since the problem would still exist had I not removed it.
You found the solution that worked for you.
And that's all that matters in terms of marking a problem solved.
(Look at all the threads where the OP marked as solved and the solution was a reinstall, or even ditching Ubuntu completely)

Not every solution can be a winner for everybody.

---

