---
title: "Software Updater running daily despite settings specifying otherwise"
date: 2016-09-28
forum: General Help
---

### Post by danemaslen on 2016-09-28
Ever since I upgraded to 16.04, Software Updater has been running daily even though its settings specify a different frequency.  I've tried various settings - weekly, fortnightly, never - all to no avail.

I've confirmed that whenever I change the frequency setting in Software Updater, the value of APT::Periodic::Update-Package-Lists in /etc/apt/apt.conf.d/10periodic is changed appropriately.  Currently I have Software Updater's frequency set to fortnightly and the value is indeed set to 14.

Yesterday morning I accepted the updates that Software Updater offered me.  The timestamp on /var/lib/apt/periodic/update-success-stamp was Sep 27 07:46.  This morning Software Updater is again offering me updates and the timestamp on the file is Sep 28 07:57.

I've not found anyone else reporting exactly this bahaviour, but I did come across another thread ([https://ubuntuforums.org/showthread.php?t=2323320](https://ubuntuforums.org/showthread.php?t=2323320)) describing a problem in which Software Updater was never running despite being set to do so daily.

I see from looking at /usr/lib/apt/apt.systemd.daily that there is scope for it to produce debugging output.  Maybe that would shed some light on what is going on, but I know neither how to cause it to do so, nor where to look for any such output that is produced.

EDIT (25/01/17): To save anyone else who is suffering this problem from having to read through the thread, the solution was to use dconf-editor to uncheck download-updates in org.gnome.software.

---

### Post by howefield on 2016-09-28
Not sure if it will help but try stopping Gnome Software from loading up at boot.

---

### Post by danemaslen on 2016-09-28
> **howefield said:**
> Not sure if it will help but try stopping Gnome Software from loading up at boot.
Thanks for the reply.  Unfortunately when I look at Startup Applications, Gnome Software didn't appear there.  It occurs to me that in my original post I should have mentioned that I use GNOME Megacity rather than Unity.

Your reply did, however, prompt me to do some more searching and I found a suggestion to use dconf-editor to uncheck download-updates in org.gnome.software.  I've now tried that.  It could be a few days before I know whether it has worked, or as little as a day before I know that it has not!

---

### Post by howefield on 2016-09-29
Guess you mean Metacity as opposed to Megacity and are running Ubuntu Gnome.

I believe what you have done is the equivalent to unchecking from the Startup Applications, which in Unity the default is not to show startup applications so there is a need to run.. so hopefully that'll do it :)

```
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

from the /etc/xdg/autostart folder. I don't have a gnome installation handy to test if it is the same for Ubuntu Gnome.

---

### Post by danemaslen on 2016-10-03
> **howefield said:**
> Guess you mean Metacity as opposed to Megacity and are running Ubuntu Gnome.

Yes, indeed.  Given the convenient proximity of T and G on the keyboard, I could try claiming it was a typo, but alas the truth is that 'Metacity' is a word that refuses to stick in my memory without getting corrupted. :-(

> **howefield said:**
> I believe what you have done is the equivalent to unchecking from the Startup Applications, which in Unity the default is not to show startup applications so there is a need to run.. so hopefully that'll do it :)

It's now been five days without Software Updates popping up unbidden, so things are certainly looking promising, though I can't rule out the possibility that there haven't been any updates released during that time.  Another nine days to go to be sure that the fix worked...

---

### Post by mcduck on 2016-10-03
As far as I know, the idea is that the setting is for *how often to inform the user about updates*, not about *how often to check  for them*. The reason for this is that any important security updates should be installed immediately, so if there's any of those available they will be displayed to you as soon as possible, regardless of the normal update schedule. (and this is of course only possible if the system at least checks for available updates daily).

Any normal, non-critical updates will then just work like you'd expect from the setting, so if it's set to once per week, the updater will only notify you about those updates once per week (even though it's already aware that they are available).

---

### Post by danemaslen on 2016-10-06
> **mcduck said:**
> As far as I know, the idea is that the setting is for *how often to inform the user about updates*, not about *how often to check  for them*. The reason for this is that any important security updates should be installed immediately, so if there's any of those available they will be displayed to you as soon as possible, regardless of the normal update schedule. (and this is of course only possible if the system at least checks for available updates daily).

Any normal, non-critical updates will then just work like you'd expect from the setting, so if it's set to once per week, the updater will only notify you about those updates once per week (even though it's already aware that they are available).
For various reasons I'm fairly sure that this is not the case and that the setting is indeed for how often to check for updates, not for how often to inform the user about them.  The netbook in question had spent the last five years (running 10.04, 12.04 and 14.04) with the frequency set to 'Never' (it's mainly used in situations of limited bandwidth or data allowance, so I want to do manual updates on those occasions when I have good internet access) and prior to the upgrade to 16.04 Software Updater had indeed never offered me any updates unbidden.  Since I unchecked download-updates in org.gnome.software the timestamp on /var/lib/apt/periodic/update-success-stamp has not changed, whereas on my desktop PC (which has the frequency set to 'Daily') the timestamp is updated each day irrespective of whether any updates are found.

---

### Post by danemaslen on 2016-10-13
After 15 days the timestamp on /var/lib/apt/periodic/update-success-stamp was still Sep 28 07:57, Software Updater still hadn't popped up, and there was a notification that the update information was outdated.  As it happens, that's precisely the behaviour I want in the long term (because I'll set the update frequency to 'Never' and run Software Updater manually on those occasions that I have good internet connectivity), but I'm fairly sure it's not what should have happened with the update frequency set to fortnightly, though it's just possible that this situation arose because automatic runs of Software Updater had managed to occur before the netbook successfully connected to the network.

I've now run Software Updater manually (the timestamp on /var/lib/apt/periodic/update-success-stamp got updated appropriately) and installed all the outstanding updates.  I've also changed the schedule of runs to weekly so that I won't have quite so long to wait to see what happens next time.

---

### Post by danemaslen on 2016-11-01
> **danemaslen said:**
> I've now run Software Updater manually (the timestamp on /var/lib/apt/periodic/update-success-stamp got updated appropriately) and installed all the outstanding updates.  I've also changed the schedule of runs to weekly so that I won't have quite so long to wait to see what happens next time.
After just over a week Software Updater popped up with updates to be installed, so it looked like the fix had indeed restored the desired behaviour.  Since then, however, I've also upgraded to 16.04 on my PC and subsequently set download-updates in org.gnome.software to false on it too.  Unlike on my netbook Software Updater on my PC is configured to check for updates daily, but I'm not yet convinced that it is successfully doing so.  Unfortunately as the PC is now not going to get used for another month, I won't know the true state of affairs until some time in December.

---

### Post by charonme on 2016-12-18
I have this problem too

---

### Post by danemaslen on 2016-12-19
> **charonme said:**
> I have this problem too

I suggest you use dconf-editor to uncheck download-updates in org.gnome.software.  That solved the problem for me, though now I find that Software Updater doesn't run successfully as often as it should do.  That could, however, be a consequence of the way Software Updater is scheduled to run and the way I tend to use my computer first thing in the morning (I believe that to avoid everyone's system hitting the servers simultaneously the Software Updater job waits for a random period before actually running Software Updater.  I suspect that I might well often be shutting my system down before that random period expires.  This is, however, just speculation).

---

