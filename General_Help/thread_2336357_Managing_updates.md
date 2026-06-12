---
title: "Managing updates"
date: 2016-09-07
forum: General Help
---

### Post by amtrakuk on 2016-09-07
Hi there

I'm a little confused when it comes to keeping your machine up to date.  If up open the App Store sometimes it says there are updates on there.  If I don't manually check by running Update Manager from the search it says there are updates there.  

A couple, ok 3 questions

I'm sure I have got ubuntu update manager setup to check for updates daily but it doesn't appear to be notifying me of new updates available.  Shouldn't the Update Manager icon appear informing me of updates?  At the moment I'm manually having to run the update manager every two or 3 weeks.

Kind of related but I'm not being informed of updates in the App Store Updates tab, should that also inform me?

Why are there now two update utilities (App Store and Update Manager)?  Is there going to be a transition to the Apps store to handle all updates - would be good IMHO ;)

---

### Post by TheFu on 2016-09-07
Wrote an article about this a few years ago. [http://blog.jdpfu.com/linsysmaint](http://blog.jdpfu.com/linsysmaint)
It was republished by Lifehacker.
Hope it helps.

In short, daily patching makes any system issues too hard to figure out. Once a week.  IMHO.
Patch weekly.
Backup daily.
There's some cleanup that you can do quarterly, but it might not be needed on releases after 14.04. I dunno.

---

### Post by irv on 2016-09-07
Every install of Ubuntu I install the Synaptic Package Manager.
```
sudo apt install synaptic
```
Run it and go to the Settings menu and select "Repositories", select the "Updates" tab and chose the setting you want. Here is what mine look like:
[ATTACH=CONFIG]271021[/ATTACH]

I also have a server I update from my laptop, so when I do this I will sometimes check and install updates on my laptop at the same time.
I open a terminal and login to my server will an ssh connection and then type the following commands in the terminal:
```
sudo apt-get update
sudo apt-get upgrade
```
Then I log off the server and do the same two commands in the terminal on the laptop. This makes sure everything is up to date.

---

### Post by Impavidus on 2016-09-07
Ubuntu software, update manager, synaptic and others tools you can use to install, update and uninstall software are all nothing more than front-ends to the same package manager: apt. Apt itself calls dpkg to do the actual installation and uninstallation of packages. It doesn't matter which one you use as they all access the same databases of available and installed software packages. You can also use apt, the back-end, or even dpkg, directly by using the terminal, which is what we often do when we have to fix a problem. The less components we put between the human and the back-end, the more powerful the tool becomes. But also harder to use. So different front-ends are available, just pick the one that fits best with your level of expertise and the difficulty of your problem.

In your settings for software and updates, you can set how often it should check for updates and how often it should show you a pop-up to tell you about updates. You can even set it to install security updates automatically. Note that update manager doesn't always inform you immediately about every update, even when it tells you about some: [https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)

---

