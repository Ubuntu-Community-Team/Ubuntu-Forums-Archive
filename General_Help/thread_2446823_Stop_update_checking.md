---
title: "Stop update checking"
date: 2020-07-07
forum: General Help
---

### Post by apg6xswhjc on 2020-07-07
What I want to do is only check for software updates when I specifically ask for them.

So, in "Software & Updates", in the Updates tab, I have Automatically check for updates set to Never. But, it seems no matter what settings I have, I am always prompted by Software Updater to install software, without asking for software updates. 

How can I stop this and only check for updates when I launch the software updater or apt update/upgrade??

---

### Post by &amp;KyT$0P# on 2020-07-07
Did you uninstall unattended-upgrades?
Do you have snapd installed?
Do you use a GUI software manager that might be automatically checking for updates when it runs?

---

### Post by apg6xswhjc on 2020-07-07
> **halogen2 said:**
> Did you uninstall unattended-upgrades?


Umm. no? What is it and why wouldn't it honour the configurations settings??

> 
Do you have snapd installed?

snapd.service is enabled/active, but I am prompted for upgrades to only normal packages even when no snaps are updated?

BTW, I would also like to disable any 'automatic' snap checks/updates, should I disable this service?

> 
Do you use a GUI software manager that might be automatically checking for updates when it runs?

Not that I'm aware of.

---

### Post by &amp;KyT$0P# on 2020-07-07
> **apg6xswhjc said:**
> Umm. no? What is it and why wouldn't it honour the configurations settings??

unattended-upgrades is a way to automatically update APT packages.  By default it's configured to only apply security updates, and ignore non-security updates. (update-notifier will then notify you about the not installed updates by popping up Software Updater.)

I don't know why unattended-upgrades didn't honor the configuration setting.  All I know is that ever since I first saw it ignore that setting, I have uninstalled it on all systems where I don't want automatic updates.

> I would also like to disable any 'automatic' snap checks/updates, should I disable this service?

You'll have to uninstall snapd.  The snapd devs intentionally made it impossible to disable automatic updates.

---

### Post by ajgreeny on 2020-07-07
I have never tried this so proceed with caution, but rather than removing snapd from your system you could attempt removing the execute flag from it with command ```
sudo chmod -x /usr/lib/snapd/snapd
```
As I say I have no idea how well this will work, nor if it might create other problems, but it should stop snapd from automatically upgrading any current snap packages installed and will allow you to add in the execute flag quickly with ```
sudo chmod +x /usr/lib/snapd/snapd
``` if needed to install a snap without the need to reinstall snapd; just make it executable again.

---

### Post by &amp;KyT$0P# on 2020-07-07
> **ajgreeny said:**
> I have never tried this so proceed with caution, but rather than removing snapd from your system you could attempt removing the execute flag from it with command ```
sudo chmod -x /usr/lib/snapd/snapd
```
As I say I have no idea how well this will work, 

How is that any better than disabling/masking snapd via systemctl?

> it should stop snapd from automatically upgrading any current snap packages installed and will allow you to add in the execute flag quickly with ```
sudo chmod +x /usr/lib/snapd/snapd
``` if needed to install a snap

... and then watch snapd run automatic update as soon as you start it again?

---

### Post by GhX6GZMB on 2020-07-07
Just remove snapd, it won't hurt and it does a lot of good. The idea behind snaps is flawed IMHO.
You might encounter an application or two that only install as snaps. Consider if you really need them.

Just my $0.02

---

### Post by ajgreeny on 2020-07-07
> **halogen2 said:**
> How is that any better than disabling/masking snapd via systemctl?

... and then watch snapd run automatic update as soon as you start it again?
You're probably right, unless you want some snap applications, eg chromium, spotify and probably others that are available only as snaps.

Personally  I'm  still on the fence about snaps as there are some applications that are not available as PPA packages that I want, but I would certainly prefer .deb versions, and have added a PPA for chromium.

Life was so much simpler before snaps!

---

### Post by GhX6GZMB on 2020-07-07
Spotify is available as debian install, Chromium IDK and IDC.

---

### Post by monkeybrain20122 on 2020-07-07
I have uninstalled all snap related stuffs on one of my systems (i don't need it but don't mind it either on 20.04 since it no longer slow down boot like in 18.04). It takes only a few steps and does no harm.  There are packages which are not available on apt but they are usually available on flatpak, which I think is better than snap as it doesn't mount a lot of volumes and there is a simple, unified gui to manage file and device access (flatseal)

P.S Chromium is snap only but who cares? Chromium is a poorly maintained alpha which is never a finished product. There are many finished products based on chromium: chrome, opera, vivaldi

---

### Post by apg6xswhjc on 2020-07-07
> **halogen2 said:**
> unattended-upgrades is a way to automatically update APT packages.  By default it's configured to only apply security updates, and ignore non-security updates. (update-notifier will then notify you about the not installed updates by popping up Software Updater.)

I don't know why unattended-upgrades didn't honor the configuration setting.  All I know is that ever since I first saw it ignore that setting, I have uninstalled it on all systems where I don't want automatic updates.


Cool thanks for the explain, I'll give that a go.


Re snaps:

>  The snapd devs intentionally made it impossible to disable automatic updates. 				
Wow. That's enough to make me want to uninstall it.

Sadly I do have a couple of snaps installed. I'll have to check if there are alternatives to install.

I might try chmod -x/+x approach. Then when I want to update snaps, I could just chmod +x.

Thanks for your help and explanations, guys.

---

### Post by &amp;KyT$0P# on 2020-07-07
> **monkeybrain20122 said:**
> There are packages which are not available on apt but they are usually available on flatpak, which I think is better than snap 

+1 for flatpak in this context.  [flatpak does not force automatic updates.]("https://ubuntuforums.org/showthread.php?t=2446274")

> **apg6xswhjc said:**
> Re snaps:


Wow. That's enough to make me want to uninstall it.

I agree with you and do exactly that.

> Thanks for your help and explanations, guys.

You're welcome. 8-)

---

### Post by apg6xswhjc on 2020-07-08
Also, I chmod -x snapd and that seems to work as we intended. I do get some errors in log about systemd couldn't start snap daemon (permission denied :p as expected). Snap apps seem to run fine. And when I ran the Software Upgrade, it went through to where it says "Updating snaps" and then just hung there until I did a force quit. So it wouldn't let the snaps update. And if I want to update them, I can manually chmod +x and update away. Hmmm could I/should I disable the snapd service as well?

on the apt side, however:

I removed unattended  upgrades yesterday, and this morning, not long after booting, I'm prompted by Software Updater to update Thunderbird - a non security related application! :sad:

There is still an unattended-upgrades service listed in systemctl :

```

$systemctl status unattended-upgrades
&#9679; unattended-upgrades.service
     Loaded: masked (Reason: Unit unattended-upgrades.service is masked.)
     Active: inactive (dead)

```

but I don't think that could be it. Even if it ran, it would try run a command from a package that's no longer installed, and would fail anyways?

I started to poke around. There was nothing in my Startup Applications, but /etc/cron.daily/apt-compat looks suspicious! This runs /usr/lib/apt/apt.systemd.daily.  I don't really follow everything going on in there, but it looks to me that it tries to observe the options in the Software & Updates and runs update/upgrade and unattended-updates.

If my guess is correct, this might be the culprit and removing the cron entry would stop the mystery update?

---

### Post by &amp;KyT$0P# on 2020-07-08
> **apg6xswhjc said:**
> on the apt side, however:

I removed unattended  upgrades yesterday, and this morning, not long after booting, I'm prompted by Software Updater to update Thunderbird - a non security related application! :sad:

There is still an unattended-upgrades service listed in systemctl :

```

$systemctl status unattended-upgrades
&#9679; unattended-upgrades.service
     Loaded: masked (Reason: Unit unattended-upgrades.service is masked.)
     Active: inactive (dead)

```

Masking the service is not equivalent to actually uninstalling the package.

Did you do a manual software update of APT packages after masking the unattended-upgrades service and rebooting?

---

### Post by mc4man on 2020-07-08
Putting aside snaps the best way to stop update checking and updating without explicitly doing so is - 
Remove unattended-upgrades
Remove update-manager
Remove update-notifier 
Install synaptic and use it for all update/upgrades..

As far as snaps, they update in the background without notice or comment. You may have seen note of some wherever but generally you'd never know
(- it checks up to 4 times or so a day..

---

### Post by ajgreeny on 2020-07-09
As a test for future, I have now removed all snap related packages and all snaps themselves from my laptop running Xubuntu 20.04. I do use chromium occasionally and have that installed from the PPA, so snapd is not needed for that, and Spottify is now installed from their own repos which I think were way behind the snap version when I first started using it.

I'll  see how things progress with all snaps gone and only add them back if really needed which seems unlikely at the moment.

---

### Post by apg6xswhjc on 2020-07-09
> **halogen2 said:**
> Masking the service is not equivalent to actually uninstalling the package.

Did you do a manual software update of APT packages after masking the unattended-upgrades service and rebooting?

I didn't actually touch the service. I did `sudo apt-get remove unattended-upgrades`. I assumed it would take care of the service as part of any install/remove...

Yes, I've done update/upgrade and rebooted multiple times since uninstalling it.

> **mc4man said:**
> Putting aside snaps the best way to stop update checking and updating without explicitly doing so is - 
Remove unattended-upgrades
Remove update-manager
Remove update-notifier 
Install synaptic and use it for all update/upgrades..


Hmmmm. That might be my best approach...

How can it be so ridiculously difficult to have control over updating your own machine at your own time??? My mind is just blown away by this. It's making Windows look like the OS that respects the user.

---

### Post by &amp;KyT$0P# on 2020-07-09
> **apg6xswhjc said:**
> I did `sudo apt-get remove unattended-upgrades`. I assumed it would take care of the service as part of any install/remove...

Not fully.  That leaves the configuration files.  Parts of the service live in /etc which is where configuration files are stored.

Do you have Synaptic installed?  If so, you can try using that to purge what's left of unattended-upgrades.

(For future reference, a full uninstall would have been [FONT=Courier New]sudo apt-get **purge** unattended-upgrades[/FONT] .)

> Yes, I've done update/upgrade and rebooted multiple times since uninstalling it.

To be clear, that's [FONT=Courier New]sudo apt-get dist-upgrade[/FONT] or running Software Updater?

What do you get if you run -
```
apt list --upgradable
```
(If it lists anything, is it entirely [phased updates]("https://wiki.ubuntu.com/PhasedUpdates") you're not yet due for?)

> Hmmmm. That might be my best approach...

If you want to go that route, first make sure that removing update-notifier and update-manager won't just be sweeping the root cause under the rug.

---

### Post by apg6xswhjc on 2020-07-10
> **halogen2 said:**
> Not fully.  That leaves the configuration files.  Parts of the service live in /etc which is where configuration files are stored.

Do you have Synaptic installed?  If so, you can try using that to purge what's left of unattended-upgrades.

(For future reference, a full uninstall would have been [FONT=Courier New]sudo apt-get **purge** unattended-upgrades[/FONT] .)


Installed synaptic and done ;). That seems to have removed the service too.

> 
To be clear, that's [FONT=Courier New]sudo apt-get dist-upgrade[/FONT] or running Software Updater?

What do you get if you run -
```
apt list --upgradable
```
(If it lists anything, is it entirely [phased updates]("https://wiki.ubuntu.com/PhasedUpdates") you're not yet due for?)


I just did sudo apt udpate and sudo apt upgrade. All packages are up to date and there's nothing to do. sudo apt list --upgradable says "Listing... Done". I think the dist-upgrade happens when I choose to Upgrade to new Ubuntu version from the Software Updater (ie from 19.04->19.10 and then 19.10 to 20.04).

> 
If you want to go that route, first make sure that removing update-notifier and update-manager won't just be sweeping the root cause under the rug.

I'm running out of ideas on what else to do. I didn't see any updates today, but I'm betting when there are some available, Software Updater is going to prompt me again. I'd really prefer to leave everything if it would just follow the settings I have in Software & Updates. **Never** to check for updates. Why is that option even in there when it is entirely ignored?

---

### Post by apg6xswhjc on 2020-07-10
Well, further into my quest, I was looking through logs and came across packagekitd, which I recalled I used to get a message about it needing to stop before Software Updater would run. 

Searching for additional information on that, I came across [Disable Automatic Updates on Ubuntu Eoan Ermine]("https://www.ubuntubuzz.com/2019/10/disable-automatic-updates-on-ubuntu-eoan-ermine.html"). This includes Graphically, snapd, packagekitd, unattended-upgrades, apt-daily, and other data downloads.

It looks pretty complete, and I'm game to give it a try. 

I'm staggered that such a simple use case is made so complicated.

---

### Post by &amp;KyT$0P# on 2020-07-10
> **apg6xswhjc said:**
> I think the dist-upgrade happens when I choose to Upgrade to new Ubuntu version from the Software Updater (ie from 19.04->19.10 and then 19.10 to 20.04).


No, both apt-get commands keep you on the same Ubuntu version.

[FONT=Courier New]apt-get upgrade[/FONT] only does package updates that don't require installing or removing any additional packages.  [FONT=Courier New]apt-get dist-upgrade[/FONT] installs **all** available package updates, including those that require installing or removing other packages, and also performs said installations/removals.

Refer to [FONT=Courier New]man apt-get[/FONT] for more info

> I'm betting when there are some available, Software Updater is going to prompt me again.

Maybe wait for that to actually happen before deciding whether more action is needed?

---

