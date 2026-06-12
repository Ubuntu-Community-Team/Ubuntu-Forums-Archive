---
title: "after a month just a kenel update is available for ubuntu 13.04 not more"
date: 2013-05-15
forum: General Help
---

### Post by woxuxow on 2013-05-15
I have installed ubuntu 13.04 about a month ago
but the only update that was available for was a kernel update about 2 weeks ago
does my installed ubuntu have problem or any else updates is not released yet?

i use terminal to upgrade my distro and i removed graphical tool for upgrading ubuntu that is installed by default

sudo apt-get update && sudo apt-get dist-upgrade

What's wrong?

---

### Post by vasa1 on 2013-05-15
Please look over here: [http://www.ubuntuupdates.org/](http://www.ubuntuupdates.org/)
That site offers various filters. You will see that there's been more than just one kernel update. On my system, the latest was a Flash update today.
> 
Start-Date: 2013-05-15  06:57:43
Commandline: aptdaemon role='role-commit-packages' sender=':1.36'
Upgrade: flashplugin-installer:i386 (11.2.202.280ubuntu0.12.10.1, 11.2.202.285ubuntu0.13.04.1), firefox-locale-en:i386 (20.0+build1-0ubuntu2, 21.0+build2-0ubuntu0.13.04.2)
End-Date: 2013-05-15  07:12:01


---

### Post by kurt18947 on 2013-05-15
There haven't been the usual deluge of updates after the official release of 13.04.  There were certainly enough prior to release though :).

---

### Post by woxuxow on 2013-05-15
> **vasa1 said:**
> Please look over here: [http://www.ubuntuupdates.org/](http://www.ubuntuupdates.org/)
That site offers various filters. You will see that there's been more than just one kernel update. On my system, the latest was a Flash update today.

And Firefox update is available since yesterday too!

I mean why there is not any update for unity or nautilus or some others

---

### Post by CaptainMark on 2013-05-15
do you get any errors from 'sudo apt-get update'?

---

### Post by woxuxow on 2013-05-15
> **kurt18947 said:**
> There haven't been the usual deluge of updates after the official release of 13.04.  There were certainly enough prior to release though :).

ubuntu 13.04 is one od the most stable and bugs free ubuntu ever
but i (and surely many other) have many problems with ubuntu 13.04
like disappearing launcher , nautilus issues  and ...

---

### Post by woxuxow on 2013-05-15
> **CaptainMark said:**
> do you get any errors from 'sudo apt-get update'?

Not at all

---

### Post by Impavidus on 2013-05-16
Then you should get all updates, unless there's a problem with the repository mirror you use.

---

### Post by alan9800 on 2013-05-16
which software sources and frequency of update checks do have you set in the "Updates" tab?
And why don't you use also "sudo apt-get upgrade" in addition to "sudo apt-get update && sudo apt-get dist-upgrade"?

---

### Post by ibjsb4 on 2013-05-16
There is a GUI for apt-get called [Synaptic Package Manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9"), you may want to give it a try.

[https://help.ubuntu.com/community/SynapticHowto#How_to_keep_your_system_up-to-date.2C_including_the_Kernel](https://help.ubuntu.com/community/SynapticHowto#How_to_keep_your_system_up-to-date.2C_including_the_Kernel)

```
sudo apt-get install synaptic
```

---

### Post by woxuxow on 2013-05-16
> **Impavidus said:**
> Then you should get all updates, unless there's a problem with the repository mirror you use.

I don't no
had you any system update? like unity update

> **alan9800 said:**
> which software sources and frequency of update checks do have you set in the "Updates" tab?
And why don't you use also "sudo apt-get upgrade" in addition to "sudo apt-get update && sudo apt-get dist-upgrade"?

I have had checked all of them except pre-released update
dist-upgrade do what upgrade do plus kernel update and update packages that have been installed manually 

> **ibjsb4 said:**
> There is a GUI for apt-get called [Synaptic Package Manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9"), you may want to give it a try.

[https://help.ubuntu.com/community/SynapticHowto#How_to_keep_your_system_up-to-date.2C_including_the_Kernel](https://help.ubuntu.com/community/SynapticHowto#How_to_keep_your_system_up-to-date.2C_including_the_Kernel)

```
sudo apt-get install synaptic
```

I have installed synaptic and use it all the time
it don`t show any systemic update for my PC

I`m completely confused!

---

### Post by Impavidus on 2013-05-16
> **woxuxow said:**
> I don't no
had you any system update? like unity update


I get updates about once every two or three days, but I'm on 12.04. And most likely using a different mirror. But I had expected more updates for 13.04 compared to 12.04. Maybe it helps if we know the contents of your /etc/apt/sources.list file. There could be something wrong there.

---

### Post by alan9800 on 2013-05-17
Consider also that Ubuntu 13.04 has an EOL cycle of only 9 months (and, by the way, Ubuntu 13.10 will be released next october), while Ubuntu 12.04, being a LTS release, has an EOL cycle of 5 years, so it is not much surprising if Ubuntu 13.04 has less updates than Ubuntu 12.04.

---

### Post by woxuxow on 2013-05-17
> **Impavidus said:**
> I get updates about once every two or three days, but I'm on 12.04. And most likely using a different mirror. But I had expected more updates for 13.04 compared to 12.04. Maybe it helps if we know the contents of your /etc/apt/sources.list file. There could be something wrong there.

I had the same experience  with 12.04 but now ...

this is the output of cat /etc/apt/sources.list

```

# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424)]/ raring main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu raring main restricted
deb-src http://archive.ubuntu.com/ubuntu raring main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu raring-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu raring-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu raring universe
deb-src http://archive.ubuntu.com/ubuntu raring universe
deb http://archive.ubuntu.com/ubuntu raring-updates universe
deb-src http://archive.ubuntu.com/ubuntu raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu raring multiverse
deb-src http://archive.ubuntu.com/ubuntu raring multiverse
deb http://archive.ubuntu.com/ubuntu raring-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu raring-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu raring-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu raring-security main restricted
deb-src http://archive.ubuntu.com/ubuntu raring-security main restricted
deb http://archive.ubuntu.com/ubuntu raring-security universe
deb-src http://archive.ubuntu.com/ubuntu raring-security universe
deb http://archive.ubuntu.com/ubuntu raring-security multiverse
deb-src http://archive.ubuntu.com/ubuntu raring-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu raring partner
deb-src http://archive.canonical.com/ubuntu raring partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu raring main
deb-src http://extras.ubuntu.com/ubuntu raring main


```

---

### Post by woxuxow on 2013-05-17
> **alan9800 said:**
> Consider also that Ubuntu 13.04 has an EOL cycle of only 9 months (and, by the way, Ubuntu 13.10 will be released next october), while Ubuntu 12.04, being a LTS release, has an EOL cycle of 5 years, so it is not much surprising if Ubuntu 13.04 has less updates than Ubuntu 12.04.

In someway you are right but my question is had you ever any systemic update for ubuntu 13.04? specially  unity or nautilus updates

---

### Post by alan9800 on 2013-05-17
> **woxuxow said:**
> In someway you are right but my question is had you ever any systemic update for ubuntu 13.04? specially  unity or nautilus updatesI tried Ubuntu 13.04 for some days, but since I have had some troubles with my graphics card, I preferred to come back to Ubuntu 12.04.

---

### Post by Impavidus on 2013-05-17
I can't find any obvious problems in your sources.list.

---

### Post by slickymaster on 2013-05-17
You might have selected 'automatically install updates' in the settings of update-manager, and the updates might have been installed without you noticing it. You can open software-center and check the history. If you see that there were regular updates, you have the proof that updating works well.

---

### Post by vasa1 on 2013-05-17
> **slickymaster said:**
> You might have selected 'automatically install updates' in the settings of update-manager, and the updates might have been installed without you noticing it. You can open software-center and check the history. If you see that there were regular updates, you have the proof that updating works well.
From OP's first post:
*and i removed graphical tool for upgrading ubuntu that is installed by default*
Yikes!

---

### Post by slickymaster on 2013-05-17
> **vasa1 said:**
> From OP's first post:
*and i removed graphical tool for upgrading ubuntu that is installed by default*
Yikes!

You're right. My bad.

---

### Post by pqwoerituytrueiwoq on 2013-05-17
there is a new kernel now, came out last night: 3.8.0-21 hopefull that fixes broken hdmi audio and a certain [booting](http://i.imgur.com/EG6zyWQ.jpg) issue on nvidia systems

---

### Post by woxuxow on 2013-05-17
> **slickymaster said:**
> You might have selected 'automatically install updates' in the settings of update-manager, and the updates might have been installed without you noticing it. You can open software-center and check the history. If you see that there were regular updates, you have the proof that updating works well.

No, "Automatically check for updates" is set "never" and "when there are security updates" is set to "display immediately"

---

### Post by woxuxow on 2013-05-17
I just replaced the following lines with existing ones in sources.list and got some updates

```

deb http://archive.ubuntu.com/ubuntu raring main restricted
deb-src http://archive.ubuntu.com/ubuntu raring restricted universe main multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu raring-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu raring-updates restricted universe main multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu raring universe
deb http://archive.ubuntu.com/ubuntu raring-updates universe
deb http://archive.ubuntu.com/ubuntu raring multiverse
deb http://archive.ubuntu.com/ubuntu raring-updates multiverse
deb http://archive.ubuntu.com/ubuntu raring-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu raring-backports main restricted universe multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu raring-security main restricted
deb-src http://archive.ubuntu.com/ubuntu raring-security restricted universe main multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu raring-security universe
deb http://archive.ubuntu.com/ubuntu raring-security multiverse
deb http://archive.canonical.com/ubuntu quantal partner
deb-src http://archive.canonical.com/ubuntu quantal partner
deb http://extras.ubuntu.com/ubuntu raring main
deb-src http://extras.ubuntu.com/ubuntu raring main 

```

The following NEW packages will be installed:
  linux-headers-3.8.0-21 linux-headers-3.8.0-21-generic
  linux-image-3.8.0-21-generic linux-image-extra-3.8.0-21-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.

---

### Post by slickymaster on 2013-05-17
> **woxuxow said:**
> No, "Automatically check for updates" is set "never" and "when there are security updates" is set to "display immediately"

When I posted I wasn't aware, for not having read with due attention your fist post, you removed the graphical tool for upgrading Ubuntu that is installed by default. Did you reinstalled it?

---

### Post by woxuxow on 2013-05-18
> **slickymaster said:**
> When I posted I wasn't aware, for not having read with due attention your fist post, you removed the graphical tool for upgrading Ubuntu that is installed by default. Did you reinstalled it?

No
After installing ubuntu the first thing i do is removing unnecessary packages like some graphical tool, Thunderbird, etc

---

### Post by slickymaster on 2013-05-19
Besides those kernel upgrades you mentioned on post#23, did you get anything else until today?

---

### Post by woxuxow on 2013-05-20
> **slickymaster said:**
> Besides those kernel upgrades you mentioned on post#23, did you get anything else until today?

Nothing

---

### Post by slickymaster on 2013-05-20
> **woxuxow said:**
> Nothing

Well, in this particular machine, running Raring, since I've installed I only got 2 software updates to be installed which were Adobe Flash Player plugin installer and Xubuntu base (Shared library for ALSA applications) with a total amount 431 KB downloaded.

You can check the number of packages that the package management system assumes installed using this command:
```
dpkg -l | grep ^ii | wc
```

---

### Post by woxuxow on 2013-05-21
> **slickymaster said:**
> Well, in this particular machine, running Raring, since I've installed I only got 2 software updates to be installed which were Adobe Flash Player plugin installer and Xubuntu base (Shared library for ALSA applications) with a total amount 431 KB downloaded.

You can check the number of packages that the package management system assumes installed using this command:
```
dpkg -l | grep ^ii | wc
```

Output is: 2018   20183  282933

So my system is normal
I think canonical is working hard on ubuntu mobile and have no time to improve and got bugs of ubuntu desktop fixed

---

### Post by slickymaster on 2013-05-21
Yes. I would say so, also. That output shows that your package management system assumes 2018 packages installed, which is the right order of magnitude for an Ubuntu system.

---

### Post by woxuxow on 2013-05-22
> **slickymaster said:**
> Yes. I would say so, also. That output shows that your package management system assumes 2018 packages installed, which is the right order of magnitude for an Ubuntu system.

Thanks for your help

So there is nothing wrong and my system is ok

---

### Post by slickymaster on 2013-05-22
> **woxuxow said:**
> Thanks for your help

So there is nothing wrong and my system is ok

If you look at [https://launchpad.net/ubuntu/raring/+queue?queue_state=3](https://launchpad.net/ubuntu/raring/+queue?queue_state=3) you can see that there were a few package updates done since the begin of May, but I guess most of them currently are just in the 'proposed' bucket only, until they have been adequately been tested. I guess as soon as they are transferred to the 'updates' bucket, your system will install them.

My advice: just wait another few days, and keep an eye on **tail /var/log/apt/history.log** to see whether there are updates happening.

---

### Post by woxuxow on 2013-05-23
> **slickymaster said:**
> If you look at [https://launchpad.net/ubuntu/raring/+queue?queue_state=3](https://launchpad.net/ubuntu/raring/+queue?queue_state=3) you can see that there were a few package updates done since the begin of May, but I guess most of them currently are just in the 'proposed' bucket only, until they have been adequately been tested. I guess as soon as they are transferred to the 'updates' bucket, your system will install them.

My advice: just wait another few days, and keep an eye on **tail /var/log/apt/history.log** to see whether there are updates happening.

Sure

Thanks again

---

### Post by woxuxow on 2013-05-26
Finally yesterday i got some systemic updates (about 80 MB)
But problems are still there (Like nautilus problem or black line on full screen movie playing)
But having update prove that my system is still alive

---

