---
title: "Can a linux distrobution be upgraded to the next version with terminal"
date: 2024-01-25
forum: General Help
---

### Post by SUPERFITTER on 2024-01-25
Can a Linux distribution be upgraded to the next version with terminal commands?

---

### Post by deadflowr on 2024-01-25
Depends on the linux distribution, but Ubuntu can with the command
```
do-release-upgrade
```

This command is specific to Ubuntu and Ubuntu derivatives.
It doesn't work for Debian, Red hat-based derivatives and many others.

Those distributions would have their own methods and/or commands to upgrade versions/releases.

---

### Post by guiverc on 2024-01-26
> **SUPERFITTER said:**
> Can a Linux distribution be upgraded to the next version with terminal commands?

This really is just confirmation of what @deadflowr has already said.

I just modified the [Lubuntu *testing checklist* for Lubuntu 22.04.4 LTS]("https://discourse.lubuntu.me/t/testing-checklist/4695"), where we list two commands for the *release-upgrade* that we QA test for.

```

do-release-upgrade -d -m desktop -f DistUpgradeViewKDE
do-release-upgrade -d

```

We're not QA-testing that with this *respin* release (*thus why I put "NA or not applicable*" on those lines. 

The `-d` option is only required before the *release-upgrade* becomes officially available (in QA we're doing it before it's released), but otherwise it's identical to what was already provided.

The EXTRA OPTIONS in the first command I used provide a nicer GUI box for the upgrade; Lubuntu uses LXQt which has no *specific* view so we just use the DistUpgradeViewKDE or KDE view option.

Both of those alternatives are essentially identical, and those are identical to what Kubuntu uses too.

If you're wanting to *releaseupgrade*, I'll suggest you read the upgrade notes for that specific release though; eg. for a [23.04 to 23.10 upgrade]("https://fridge.ubuntu.com/2024/01/26/ubuntu-23-04-lunar-lobster-reached-end-of-life-on-january-25-2024/"), the link goes to [https://help.ubuntu.com/community/ManticUpgrades](https://help.ubuntu.com/community/ManticUpgrades) , but such links exist for all *supported* upgrade paths.

---

### Post by Tadaen_Sylvermane on 2024-01-26
Then there is the fully manual method of editing the sources list, and running the upgrade in turn as straight Debian does. 
This is not the recommended way to do Ubuntu but it does work as long as your system is sound and you haven't polluted it with countless PPA's from various releases. 

I've successfully done a debootstrap Jammy from a Debian live boot then upgraded it one at a time to 23.10. No issues to speak of. 
For what it's worth this was a bare debootstrap that I upgraded. It didn't have a whole package load installed, just the base. That may or may not cause problems.

---

### Post by SUPERFITTER on 2024-01-27
I'm using a duel boot with Ubuntu and Mint. I cannot upgrade to a new version of Mint for some reason. I was looking for a way to repair and update to a newer version of Mint with terminal commands.

---

### Post by guiverc on 2024-01-27
All of Ubuntu and [*flavors* of Ubuntu]("https://ubuntu.com/desktop/flavours") upgrade the same way.

FYI:  You asked this in a Ubuntu and *flavors* section of this forum, Linux Mint isn't a *flavor*.

Linux Mint  however is not Ubuntu, and those procedures don't apply (*they may only upgrade the Ubuntu parts of your system, thus on reboot you've a broken system*).

You should follow Linux Mint procedures, as your system as runtime *adjustments* and other things that differ to Ubuntu systems.  eg. [https://linuxmint-user-guide.readthedocs.io/en/latest/upgrade-to-mint-21.html](https://linuxmint-user-guide.readthedocs.io/en/latest/upgrade-to-mint-21.html) if that's the upgrade you're after.

---

### Post by SUPERFITTER on 2024-01-27
[COLOR=#DD4814]****[/COLOR]**[B]**[/B]**[B]**[/B]guiverc 

Thank you for your reply.  I was looking for a way of fixing this problem. [B][B]
[/B][/B]I tried using the site.**[B] **[/B] [https://linuxmint-user-guide.readthe...o-mint-21.html]("https://linuxmint-user-guide.readthedocs.io/en/latest/upgrade-to-mint-21.html")
That did not work for me, so I will have to format and install the new version.
Thank you

[URL="https://ubuntuforums.org/member.php?u=2074246"][B][COLOR=#DD4814][B]
[/B][/COLOR][/B][/URL]

---

### Post by yancek on 2024-01-27
Did you prefix all the commands with sudo?  Hard to say what didn't work as "Follow the instructions on the screen" doesn't tell one much and I don't use Mint so couldn't help.

---

### Post by SUPERFITTER on 2024-01-27
yancek
I did prefix all the commands with sudo.  
I think the install is so screwed up that I will just format and start over.  
Thank you for your response.

---

### Post by guiverc on 2024-01-27
> **SUPERFITTER said:**
> 
That did not work for me, so I will have to format and install the new version.
Thank you


I'm no expert in Linux Mint, however you do realize that Ubuntu Desktop systems allow a non-destructive re-install, ie. you don't need to format for install, and thus your settings, configurations & data remain... Further if done correctly, you can actually have the *manually installed* packages you added to your old system (*the one you're installing over*) auto-reinstall too.

I do this about weekly with a Lubuntu system, instead of performing normal upgrades... as it accomplishes a QA test of the *unreleased 22.04.4 *product at the same time as updating my packages.

I also used this to switch a 23.04 system (*which is now EOL*) to 24.04 (*technically noble, it' doesn't change to 24.04 until after RC which is still ~18-April-2024*)

I've written about it [here]("https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533") if interested, and whilst I don't know if Linux Mint will do the same, it's for sure what I'd use if I was going the re-install route (*I do it >70 times per year & thus trust it*)

---

### Post by avidandrew on 2024-02-01
I would highly recommend running [FONT=courier new]do-release-upgrade[/FONT] and any other commands related to the upgrade inside a tmux window ([FONT=courier new]sudo apt-get install tmux[/FONT] beforehand). This way, if for some reason you get disconnected from the terminal running [FONT=courier new]do-release-upgrade[/FONT] (e.g. if you are connected to the computer over SSH, you can easily reconnect and run [FONT=courier new]tmux attach[/FONT] to get reattached to the TTY where the upgrade process is running.

---

