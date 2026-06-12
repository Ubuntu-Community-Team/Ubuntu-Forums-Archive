---
title: "What's Upgrading Like?"
date: 2006-10-12
forum: General Help
---

### Post by dpaint4 on 2006-10-12
I've used Ubuntu, and liked it a lot since 5.10. I currently use 6.06 and my install is lovely. In fact, it's so lovely that I'm scared that when 6.10 comes out officially, I'll mess something up when I try to upgrade.

Will the upgrade be offered via the regular automatic update system, or will it be like I've heard before, where you do it by changing your repositories and then typing something or other like 'dist upgrade' (I know that's not it) in the terminal?

What kind of failure rate is there for that? I'm looking forward to 6.10 a lot. 

Anyone have tips for a successful upgrade or stories?

---

### Post by matt_risi on 2006-10-12
I'm in the same boat, pretty nervous. I'm probably gonna wait a week after release and watch the forums for installation issues, etc.

---

### Post by PriceChild on 2006-10-12
The update notifier will inform you that a new version of ubuntu is out.

You can press no, and will never hear about it again :)

Press yes, and it will attempt to prepare your system, check for problem, then upgrade.

Please remember that Dapper is an LTS release and I do not see the need for anyone wanting a stable workstation to upgrade.

Edgy doesn't have its name for nothing...

Btw check [here]("https://help.ubuntu.com/community/EdgyUpgrades") for more info on upgrading.

---

### Post by dpaint4 on 2006-10-13
> **PriceChild said:**
> The update notifier will inform you that a new version of ubuntu is out.

You can press no, and will never hear about it again :)

Press yes, and it will attempt to prepare your system, check for problem, then upgrade.

Please remember that Dapper is an LTS release and I do not see the need for anyone wanting a stable workstation to upgrade.

Edgy doesn't have its name for nothing...

Btw check [here]("https://help.ubuntu.com/community/EdgyUpgrades") for more info on upgrading.

Thanks a lot; that's exactly the information I was looking for, and even better, the scenario is exactly as I'd hoped.

---

### Post by aysiu on 2006-10-13
I don't think you should be nervous. Upgrades can be painless or painful. They're usually painless.

If you have a separate /home partition or data partition and a script like Automatix or Easy Ubuntu, it shouldn't be too hard to do a reinstall, should it come to that.

---

### Post by matt_risi on 2006-10-13
Right now for me the cons outweigh the pros, I don't wanna give up what little stability I have now for Edgy. We'll see I guess.

---

### Post by fragos on 2006-10-14
From a use perspective they may not be a need to update if your needs are already being met.  I on the other hand am a change addict.  I will update because I love new and enjoy the learning curve sometimes associated with a new release.  Its a personal thing, not a Linux community mandate.  The best tool for you is always one you want to and can use.

---

### Post by Cronjob on 2006-10-14
I've never done an "ubuntu" upgrade before, but every Debian upgrade I've done in the last however many years has been as difficult as this:

#>  apt-get update; apt-get dist-upgrade;

---

### Post by matt_risi on 2006-10-14
Yeahhh I think I'm just gonna stay with Dapper.. I don't want my laptop to be any more "edgy" than it already is. ;)

---

### Post by aysiu on 2006-10-14
> **Cronjob said:**
> I've never done an "ubuntu" upgrade before, but every Debian upgrade I've done in the last however many years has been as difficult as this:

#>  apt-get update; apt-get dist-upgrade;
If you decide not to use the built-in update manager, it's actually a three-part process in Ubuntu.

1. Make sure you have the appropriate desktop package installed (*ubuntu-desktop* for Gnome, for example)

2. Change your /etc/apt/sources.list (replace all instances of *dapper* with *edgy*)

3. ```
sudo aptitude update && sudo aptitude dist-upgrade
``` I wrote [a script for it](http://ubuntuforums.org/showthread.php?t=275890) that most people probably won't use.

---

### Post by slibuntu on 2006-10-14
Edgy is going to be a proper release right? bearing in mind i started with 6.06,i'd like to know, are most new Ubuntu releases unstable? I sorta thought upgrading to Edgy would be a no brainer, why wouldn't you want the latest one? Similar to upgrading from 2000 to Xp, its a natural progression, now i'm doubtful if i should or not

---

### Post by matt_risi on 2006-10-14
I guess Edgy's gonna be sorta a "bleeding edge" type thing, where it's mostly for people who wanna test the new OS and run the latest and greatest (and crashiest) software.

---

