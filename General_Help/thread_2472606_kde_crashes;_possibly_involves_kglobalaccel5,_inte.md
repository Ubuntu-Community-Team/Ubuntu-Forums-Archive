---
title: "kde crashes; possibly involves kglobalaccel5, intel microcode update"
date: 2022-03-05
forum: General Help
---

### Post by Peter_Brandon on 2022-03-05
A number of days ago, I think within the last week, I started having trouble with suspend on my kde-ubuntu computer.  A couple times, I suspended and, when I resumed, I got a completely black screen (no signal) despite the computer being active and had to hard power off.  I don't believe I had ever seen that before.

A few days ago, I upgraded to Nvidia driver 510, upgraded to the latest intel microcode (actually upgraded earlier, but I hadn't restarted my computer), and made some other changes that probably aren't relevant (updating CUDA, etc.).  

When I tried to suspend, the computer consistently did not suspend but went to a login screen and dumped my kde session.

So, I returned to Nvidia driver 470.  But I continue to have the suspend issue.

The apport log (see enclosed) suggests that kglobalaccel5 crashed.  There's also an apport crash report (/var/crash) regarding kglobalaccel5.  However, I don't know for certain that kglobalaccel5 initiates the crash.  I also don't know that the apport crash report ever got sent because it looks like my internet connection is down around the time of the crash.

The enclosed also shows an outtake from my systemlog at the time of the crash.  It shows the system trying to sleep but then waking up and losing the kde session.  Network manager seems to be acting strangely, but, again, this may due to a less visible event.

Another suspect here is the intel microcode update.

Any suggestions on what I should try?  Is there a way for me to send the crash report after the system comes back up?

---

### Post by QIII on 2022-03-05
Hello!

What release of Kubuntu are you running?

---

### Post by Peter_Brandon on 2022-03-06
Hi QIII:

My kde info is as follows.  If you need anything else, let me know.

```
$ plasmashell --version
plasmashell 5.18.8 
(base)
$ kf5-config --version 
Qt: 5.12.8 
KDE Frameworks: 5.68.0 
kf5-config: 1.0
```

---

### Post by Peter_Brandon on 2022-03-06
Incidentally, I downgraded the Intel microcode to the last version, but the suspend problem continued.  So, probably not caused by the microcode update.

I wanted to try to remove kglobalaccel5 from my system to see if that would make a difference, but that piece of software is tied into KDE, so removing it would mean removing a lot more.

In any event, I had another crash today.  This time there was no crash report for kglobalaccel5.  But there were for kactivitymanagerd and plasmashell, with the first of these being reported a full minute before the second.  Neither showed up as a crash report before.  None of the crash reports mention a segmentation fault.  I suspect none have been sent.

I did discover that suspending with pm-suspend does not cause my computer to crash.

---

### Post by SeijiSensei on 2022-03-07
I had various issues with Kubuntu and decided to give KDE Neon a try. So far it's been a great success. Smooth installation and no glitches so far.

[https://neon.kde.org/](https://neon.kde.org/)

It's built on top of Ubuntu so you can install the packages you need with apt.  No libre-office for instance.

---

### Post by Peter_Brandon on 2022-03-07
Thanks SeijiSensei!  Neon sounds interesting.  Is there any way to install it on top of my Ubuntu 20.04 (my kde is on top of that)?  I looked for but didn't find a ppa for KDE Neon.  Also, Neon evidently provides the latest KDE software on top of a Ubuntu 20.04 foundation.  Wouldn't the fact that it's the latest software mean that it's less likely to be stable than the older KDE software on Ubuntu?

---

### Post by Peter_Brandon on 2022-03-07
I gather that I could try to install on top of Ubuntu using the following code.  Still wondering though why the latest software is likely to be stable.

sudo apt-add-repository [http://archive.neon.kde.org/release](http://archive.neon.kde.org/release)
wget -q -O - [http://archive.neon.kde.org/public.key](http://archive.neon.kde.org/public.key) | sudo apt-key add -

sudo apt-get update
sudo apt-get upgrade

---

### Post by #&amp;thj^% on 2022-03-07
Quote: 
Can I turn Kubuntu into KDE neon with a PPA? &#65533;&#65533;

We recommend that you install a fresh KDE neon from the provided ISO images. But you can indeed add an APT repository to switch from Kubuntu to KDE neon. This is absolutely not tested or supported. If things take a turn for the worse you are expected to be knowledgeable enough to repair your system on your own. A web search should quickly give you relevant information on how to do this.

KDE neon is however not compatible with Kubuntu, as there is vast overlap in the base offerings of both Kubuntu and KDE neon. You can not use both systems at the same time. Installing KDE neon will simply replace Kubuntu.

---

### Post by Peter_Brandon on 2022-03-08
Thanks for the warning 1fallen!

---

### Post by #&amp;thj^% on 2022-03-08
> **Peter_Brandon said:**
> I gather that I could try to install on top of Ubuntu using the following code.  Still wondering though why the latest software is likely to be stable.

sudo apt-add-repository [http://archive.neon.kde.org/release](http://archive.neon.kde.org/release)
wget -q -O - [http://archive.neon.kde.org/public.key](http://archive.neon.kde.org/public.key) | sudo apt-key add -

sudo apt-get update
sudo apt-get upgrade

I actually converted Kubuntu to KDE neon, [U]not that I'm telling you to, but it is doable.
[/U]
sources.list:
```
Repos:     Active apt repos in: /etc/apt/sources.list 
           1: deb http://archive.ubuntu.com/ubuntu/ focal main restricted universe multiverse
           2: deb http://security.ubuntu.com/ubuntu/ focal-security main restricted universe multiverse
           3: deb http://archive.ubuntu.com/ubuntu/ focal-updates main restricted universe multiverse
           Active apt repos in: /etc/apt/sources.list.d/neon.list 
           1: deb http://archive.neon.kde.org/user focal main
           2: deb-src http://archive.neon.kde.org/user focal main
           Active apt repos in: /etc/apt/sources.list.d/preinstalled-pool.list 
           1: deb [arch=amd64] file:/var/lib/preinstalled-pool/ focal main restricted universe multiverse

```

---

### Post by Peter_Brandon on 2022-03-08
Thanks 1fallen!

I realized that I could switch to Gnome desktop today and tried that.  But the suspend issue persists.  I thought for a moment that meant that KDE wasn't involved, but this time the crash report was for drkonqi, the KDE crash handler (ironically).  I guess it's still active even when I have Gnome as my desktop.  One thing that's odd about all this is that each crash seems to generate a different report or pair of reports.

The syslog under the gnome crash seems to show the same pattern as for the crashes in KDE:  the system tries to go to sleep, it thus seeks to deactivate my network (network manager and modem manager), as it's trying to do that something tells the system to not suspend, it tries to recover, and my existing user session crashes.  Tried to reinstall all the network / modem manager software, but this had no effect.

---

### Post by #&amp;thj^% on 2022-03-08
Gnome and Plasma has know issues.
If your going to use multiple desktops>> Create another user so things don't mix between the two.
Gnome user and KDE user, you'll find it a bit more rewarding
One question I've been dying to ask, have you just tried screen-lock instead of suspend.
I'll also use "dm-tool lock" 

Locking Screen with LightDM
	
The LightDM display manager provides dm-tool to allow us to lock the screen from the command line

```
dm-tool lock
```
 A similar command will also lock the screen and switch to the display manager's login screen.

```
 dm-tool switch-to-greeter
```

---

### Post by Peter_Brandon on 2022-03-10
Hi 1fallen:  I never use screen lock.

---

### Post by #&amp;thj^% on 2022-03-10
So just suspend? It was kind of a tip for your suspend issues.
Has it improved with Gnome?

---

### Post by SeijiSensei on 2022-03-10
You could consider giving Neon a try in a virtual machine. You can install virtualbox from the repositories, or install the armament required to run "kernel virtual machines" or KVM. Here's the guide I followed: [https://phoenixnap.com/kb/ubuntu-install-kvm](https://phoenixnap.com/kb/ubuntu-install-kvm)

I just bit the bullet and installed Neon from the most recent ISO image: [https://neon.kde.org/download](https://neon.kde.org/download)

---

### Post by Peter_Brandon on 2022-07-18
I found a solution to my problem.

I switched to the lightdm display manager (from sddm), which made it easier to identify the problem because the system wouldn't crash when I suspended, it would simply come out of suspend.  I then looked at every available system log and, in the authentication log, I found this:  systemd-logind    Error during inhibitor-delayed operation (already returned success to client): Unit nvidia-suspend.service is masked.  This error occurred right between  my system was putting various things to sleep and, for no apparent reason, suddenly waking them back up.  

That then led me to this discussion of how to fix nvidia-suspend problems:  [https://gist.github.com/bmcbm/375f14eaa17f88756b4bdbbebbcfd029](https://gist.github.com/bmcbm/375f14eaa17f88756b4bdbbebbcfd029) .  Reading between the lines of that, I discovered that there were several broken symlinks found with:  ls /etc/systemd/system/systemd* .  I'm using nvidia-470, and I think the broken symlinks are from earlier versions.  I disabled these symlinks (renamed them).  Viola, my system is able to suspend without incident for the first time in months.

Would be nice if nvidia were to be more careful with their driver installers and Ubuntu didn't bury the relevant error message in the authentication log.

---

