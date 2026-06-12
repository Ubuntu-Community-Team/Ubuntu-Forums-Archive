---
title: "Patching Ubuntu"
date: 2017-10-24
forum: General Help
---

### Post by 1jarwolf on 2017-10-24
Dumb question but how would I patch Ubuntu for possible flaws in the system? Would simply doing and apt-get upgrade and apt-get upgrade suffice? Also, would I be more secure by using a wireless wifi adapter then just using wifi?

---

### Post by ian-weisser on 2017-10-24
Usually 'patch' means making a change to source code in one of several trackable, revertable formats. I'm not sure that's what you mean.

Are you simply asking how to install security fixes or bugfixes? Or are you asking something else?

What kind of difference are you concerned about between internal wi-fi vs. external wi-fi adapter? I don't understand where you are going on this.

---

### Post by Impavidus on 2017-10-24
Take a look at the settings in Software & Upgrades. Different flavours put those settings in a slightly different place, but it should be easy to find. Also take a look at unattended upgrades.

If you want to do things manually, you can run```
sudo apt update
sudo apt upgrade
```which will first refresh the list of available packages from the repositories, detecting any available upgrades and security patches, and will then download and install them. But it's easier to automate this a bit. I configured it to check for updates automatically every day and immediately notify me of both security and other updates. I get a pop-up, review the list and hit install (after kernel upgrades I use the terminal to autoremove some old stuff). You can even do it all fully automatic, but I like to keep in control.

If you manually install stuff, you have to install the upgrades manually to. Which is one reason why we don't recommend to install stuff manually.

---

### Post by 1jarwolf on 2017-10-24
Yes, I meant bugfixes and security fixes. Sorry for the misunderstanding. I have an external wifi adapter. It is a PAUO5 wifi USB dongle. I was unsure whether to install updates that are not already checked but I will have a look at them.

---

### Post by mastablasta on 2017-10-25
you can also set automatic updates: [https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

you shouldn't update using wifi as wifi can cause lost packages which can lead to botched update.

---

### Post by ian-weisser on 2017-10-25
> **1jarwolf said:**
> Yes, I meant bugfixes and security fixes. [...] I was unsure whether to install updates that are not already checked [...].

On a single release of Ubuntu, the ONLY updates you will get from the Ubuntu repositories are important bugfixes and security updates. You should install ALL of them.

Software you install from non-Ubuntu sources (like PPAs) are different, and may well include new versions, testing versions, and other non-critical changes.

---

### Post by 1jarwolf on 2017-10-25
Okay. I tried went to the other tab and I am kind of confused now. It still has the 17.04 zesty sources. Should I check all of those as well?

---

### Post by jeremy31 on 2017-10-25
Most users have no need for the source code but it won't result in any extra updates as source code has to be manually downloaded using terminal

---

### Post by ian-weisser on 2017-10-25
> **1jarwolf said:**
> Okay. I tried went to the other tab and I am kind of confused now. It still has the 17.04 zesty sources. Should I check all of those as well?

It's simple:
If you are running 17.04 (zesty), then you should use 17.04 sources *and no others.*
If you are running 17.10 (artful), then you should use 17.10 sources [I]and no others.

[/I]Old, obsolete package sources (like your CD-ROM and previous release of Ubuntu) can be safely deleted or disabled - you will never use them again.

---

