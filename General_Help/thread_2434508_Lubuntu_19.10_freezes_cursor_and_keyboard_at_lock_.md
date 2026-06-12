---
title: "Lubuntu 19.10 freezes cursor and keyboard at lock screen"
date: 2020-01-07
forum: General Help
---

### Post by semper-solus on 2020-01-07
Hello, all.

I recently had to delete and reinstall my OS, and--bearing the spotty knowledge that I do--I decided to accomplish this with a series of bash scripts that printed out all of my attached packages, and then automatically reinstalled them. (So it's possible I'm missing an incredibly important dependency and do not know what it is.) While I was at it, I also decided to install 19.10 instead of the original 19.04, because 04 lost support or something, according to the timeline on the Lubuntu website (which I may have misread).

Ever since I did this, and tried to awaken my computer from "Suspend" state or a lengthy lock (which I do on instinct whenever I get up from the chair), I reach a lock screen (the one affiliated with XScreenSaver, if that helps), but I cannot move my cursor or keyboard. I have to do a forced shutdown and reboot. I would like to change this.

As far as identifying and fixing the problem, I am still at the "diagnosis" stage, so could someone help me figure out how to run the pertinent tests?

As always, any suggestions--as long as they are constructive or helpful in some way--are appreciated.

---

### Post by guiverc on 2020-01-07
i'm not a fan of the idea of using a script to work out what packages were installed, and then re-installing them. My concern is they were probably installed as part of `lubuntu-desktop` for example and thus when you release-upgrade to 20.04 in the future, the normal packaging rules for the release-upgrade will occur.  However if you `install -reinstall` packages individually, you'll have those packages recorded as being manually (user) installed so if they are removed in 20.04, they won't be for your system as you installed them (instead of them being part of `lubuntu-desktop`.

Lubuntu 19.04 & all 19.04 releases are still supported; they were released 2019-April-18 ([https://fridge.ubuntu.com/2019/04/19/ubuntu-19-04-disco-dingo-released/](https://fridge.ubuntu.com/2019/04/19/ubuntu-19-04-disco-dingo-released/)) so will be supported until at least 2020-Jan-18.  I see nothing on [https://lubuntu.me/disco-released/](https://lubuntu.me/disco-released/) that contradicts that.

I wonder what method you used to install 19.10; I'm assuming you *Manual Partitioning*, selected your existing partitions and did **not** format those partitions, but without specifics I'm unsure.  (this would allow user configs to survive re-install; format wouldn't)

For "*shutdown and reboot*" do you mean using **Sysrq** keys to cause the kernel to shutdown/reboot? or using the power button  (I would avoid using power button unless absolutely necessary; but this information is really useful as if the sysrq keys no longer work - it means the linux kernel is possibly dead, or your keyboard has become dead etc which is a huge clue). If however you're using power-button instead of keyboard, please test using sysrq keys to reboot or shutdown  (for info I'll refer you to [https://ubuntuforums.org/showthread.php?t=617349](https://ubuntuforums.org/showthread.php?t=617349) though if I forgot the keys I'd probably do a "*magic sysrq*" keys on a phone & look at wikipedia to jog my memory)

---

### Post by semper-solus on 2020-01-07
> **guiverc said:**
> i'm not a fan of the idea of using a script to work out what packages were installed, and then re-installing them. My concern is they were probably installed as part of `lubuntu-desktop` for example and thus when you release-upgrade to 20.04 in the future, the normal packaging rules for the release-upgrade will occur.  However if you `install -reinstall` packages individually, you'll have those packages recorded as being manually (user) installed so if they are removed in 20.04, they won't be for your system as you installed them (instead of them being part of `lubuntu-desktop`.

Lubuntu 19.04 & all 19.04 releases are still supported; they were released 2019-April-18 ([https://fridge.ubuntu.com/2019/04/19/ubuntu-19-04-disco-dingo-released/](https://fridge.ubuntu.com/2019/04/19/ubuntu-19-04-disco-dingo-released/)) so will be supported until at least 2020-Jan-18.  I see nothing on [https://lubuntu.me/disco-released/](https://lubuntu.me/disco-released/) that contradicts that.

I wonder what method you used to install 19.10; I'm assuming you *Manual Partitioning*, selected your existing partitions and did **not** format those partitions, but without specifics I'm unsure.  (this would allow user configs to survive re-install; format wouldn't)

For "*shutdown and reboot*" do you mean using **Sysrq** keys to cause the kernel to shutdown/reboot? or using the power button  (I would avoid using power button unless absolutely necessary; but this information is really useful as if the sysrq keys no longer work - it means the linux kernel is possibly dead, or your keyboard has become dead etc which is a huge clue). If however you're using power-button instead of keyboard, please test using sysrq keys to reboot or shutdown  (for info I'll refer you to [https://ubuntuforums.org/showthread.php?t=617349](https://ubuntuforums.org/showthread.php?t=617349) though if I forgot the keys I'd probably do a "*magic sysrq*" keys on a phone & look at wikipedia to jog my memory)

(answering paragraph by paragraph)

I only installed the packages labeled "installed" but not "automatic". I figured "automatic" meant "came either with the OS or with a package download". This may be wrong.

I guess I misread that. That is a lot of extra work for me.

I did use manual partitioning, but I wanted the partition to take up more space on the hard drive, and the efi and swap partitions were in the way. My configurations did not survive.

I just looked up what a SysRq key is, and my laptop definitely does not have one. I've been using the power button. I know it's bad for linux; I just know no other options.

Does that help determine what the problem is in any way?

---

