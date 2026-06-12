---
title: "Software Updater v Ubuntu Software"
date: 2017-01-13
forum: General Help
---

### Post by makouser on 2017-01-13
Hi all,

First time here as a poster, but a Ubuntu user for years and years. Not that that is any indicator of knowledge:confused:

I'm confused by the role of the Software Updater and Ubuntu Software. I can't seem to fine any consistency with what each thinks are updates. Only Updater actually notifies me, not Ubuntu Software.

Can someone explain what each should do, is one more strategic than the other, do I need to run both to keep up-to-date?

Thanks

---

### Post by howefield on 2017-01-13
Which version of Ubuntu are you running ?

I'd suggest Software Updater to be the more accurate, Ubuntu Software at the moment can't even list all Software far less get the updates right ;)

My preference is to let unattended-upgrades run (16.04 onwards) and a periodic update via terminal..

```
sudo apt update
```
```
sudo apt upgrade
```

---

### Post by chris354 on 2017-01-13
By ubuntu software i assume you mean the software centre? If that's the case it won't tell you if there are updates because its basically a place to install and uninstall applications and doesnt include an update process.

Software updater is exactly that, an updater so it runs the checks and notifies/installs per your settings. You do not need to keep either of the applications "open" software updater runs a daemon in the background which does the checks and will periodically popup a dialog for you.

---

### Post by howefield on 2017-01-13
> **chris354 said:**
> By ubuntu software i assume you mean the software centre? If that's the case it won't tell you if there are updates because its basically a place to install and uninstall applications and doesnt include an update process.

The Software Centre became Ubuntu Software in Ubuntu 16.04 and does advise of updates, hence the OPs confusion.

---

### Post by makouser on 2017-01-13
> **howefield said:**
> The Software Centre became Ubuntu Software in Ubuntu 16.04 and does advise of updates, hence the OPs confusion.

How does it advise of updates?

I don't see anything.

Why does it show different things to Software Updater?

Is Ubuntu Software the future? Is it something to do with Snap? That's something else I'm confused by, but for another post probably.

> **howefield said:**
> Which version of Ubuntu are you running ?

I'd suggest Software Updater to be the more accurate, Ubuntu Software at the moment can't even list all Software far less get the updates right ;)

My preference is to let unattended-upgrades run (16.04 onwards) and a periodic update via terminal..

```
sudo apt update
```
```
sudo apt upgrade
```

I've contemplated unattended-upgrades, but still begs the question as to whether it sees the stuff that Ubuntu Software does.

I've wondered if it is just a timing issue that one sees the updates at a different time to the other, and if I was patient either would do.

Just want an idea of what Ubuntu's strategy is on it.

---

### Post by ian-weisser on 2017-01-13
> **barry.merchant said:**
> I've wondered if it is just a timing issue that one sees the updates at a different time to the other, and if I was patient either would do.

Patience is the best idea of all.
Ubuntu Software is intended to be an app store. A place to go to find software packages.
Software Updater is one of several available tools to upgrade already-installed packages.

Software Updater uses *phased updates*, which means that all upgrades are not offered immediately to everyone. There is a good reason for that - it means that a catastrophic upgrade can be identified and reverted before it poisons the entire community. But it also means that it's the wrong tool if you want every upgrade immediately. Use ordinary apt or Synaptic for immediate upgrades.

I don't even have Software Updater or Update Notifier installed anymore. I use Unattended Upgrades and regular backups for everything in the Ubuntu repos. Software Updater dates from a time before the current CI and QA and Testing methods were worked out, and reviewing upgrades was a wise idea.

---

### Post by makouser on 2017-01-13
> **ian-weisser said:**
> Patience is the best idea of all.
Ubuntu Software is intended to be an app store. A place to go to find software packages.
Software Updater is one of several available tools to upgrade already-installed packages.

Software Updater uses *phased updates*, which means that all upgrades are not offered immediately to everyone. There is a good reason for that - it means that a catastrophic upgrade can be identified and reverted before it poisons the entire community. But it also means that it's the wrong tool if you want every upgrade immediately. Use ordinary apt or Synaptic for immediate upgrades.

I don't even have Software Updater or Update Notifier installed anymore. I use Unattended Upgrades and regular backups for everything in the Ubuntu repos. Software Updater dates from a time before the current CI and QA and Testing methods were worked out, and reviewing upgrades was a wise idea.


I appreciate that the old Ubuntu Software Centre was indeed just an app store, but the new one is trying to be more than that isn't it? IIRC it has updated OS components even the recent kernel patches.

---

### Post by ian-weisser on 2017-01-13
> **barry.merchant said:**
> I appreciate that the old Ubuntu Software Centre was indeed just an app store, but the new one is trying to be more than that isn't it? IIRC it has updated OS components even the recent kernel patches.

The old one had those, too. Displayed differently, perhaps, but I recall dbus packages and kernel packages and other components in the old Software Center.

---

### Post by makouser on 2017-01-14
So back to Ubuntu Software and notifications (or lack of in my case), how do I make it tell me when there are updates?

---

