---
title: "xubuntu 21.10 Can't Update"
date: 2022-08-15
forum: General Help
---

### Post by wmichaelb2 on 2022-08-15
Hi, when I try to update xubuntu with 

sudo apt update
sudo apt dist-upgrade

I get the error message:

Ign:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish InRelease
Ign:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish-updates InRelease      
Ign:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish-backports InRelease           
Err:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish Release                       
  404  Not Found [IP: 91.189.91.39 80]
Err:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish-updates Release               
  404  Not Found [IP: 91.189.91.39 80]
Err:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) impish-backports Release             
  404  Not Found [IP: 91.189.91.39 80]
Ign:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-security InRelease              
Hit:8 [http://ppa.launchpad.net/kelebek333/kablosuz/ubuntu](http://ppa.launchpad.net/kelebek333/kablosuz/ubuntu) impish InRelease     
Err:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-security Release
  404  Not Found [IP: 185.125.190.36 80]
Hit:10 [http://ppa.launchpad.net/teejee2008/ppa/ubuntu](http://ppa.launchpad.net/teejee2008/ppa/ubuntu) impish InRelease
Reading package lists... Done
E: The repository 'http://us.archive.ubuntu.com/ubuntu impish Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu impish-updates Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu impish-backports Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://security.ubuntu.com/ubuntu impish-security Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
mikeb@E6410A:~$ 

 I've tried cleaning up my repository list, but the key ones I need don't seem to be available. 
And I can't install Telegram for support because I can't..get..access..to..the..repository.
Has anyone else seen this problem? Thanks in advance.

---

### Post by tea for one on 2022-08-15
Xubuntu 21.10 reached End of Life on June 14 2022.
[https://xubuntu.org/release/21-10/](https://xubuntu.org/release/21-10/)

I suggest that you backup your personal data and clean install Xubuntu 22.04 (or your current favourite flavour).

---

### Post by QIII on 2022-08-15
Impish (21.10) was an interim release and as such enjoyed only a 9 month period of support.  That has ended.  The repos have likely been moved.  While you can still upgrade via the "Old Releases" method, that often results in failure and a significant emotional event that is probably not worth it for an interim release.

I suggest a fresh installation of Focal (20.04.x) or Jammy (22.04) as they are Long Term Support (LTS) versions, which have 3 years of support for the flavor releases of Ubuntu.

---

### Post by Impavidus on 2022-08-15
In addition to a completely clean install and an end-of-life upgrade, you can also try upgrading by installing the new release over the older. Start the installation, tell it to use the same partition as used for your current system and don't format it. The installer will note the packages currently installed and upgrade those.

---

### Post by guiverc on 2022-08-15
Notices of the EOL of 21.10 went out ~six weeks before EOL, and again at EOL. Your system would have also told you about it, and offered upgrade to 22.04 months ago, though its very easy to tell that notification to '*go away and don't bother me again*' which it does, and you're not told again.

I'll provide the EOLUpgrades link which if changed, can ensure you have applied all upgrades to your *EOL* system, which should also then allow you to *release-upgrade* to 22.04.

- [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

I'll also provide a link to a EOL notice [https://fridge.ubuntu.com/2022/07/19/ubuntu-21-10-impish-indri-end-of-life-reached-on-july-14-2022/](https://fridge.ubuntu.com/2022/07/19/ubuntu-21-10-impish-indri-end-of-life-reached-on-july-14-2022/) as it contains a link to the *JammyUpgrades* or how to upgrade your system to 22.04 .  (Note: *you must do EOLUpgrades first* given 21.10 is now EOL)

You can re-install a Ubuntu desktop system (*including flavors like Xubuntu*) without losing any data files, and having your *manually installed* (ie. apps you've added post-install) packages auto-reinstalled (*where they're from Ubuntu repositories*) which is far faster, and doesn't require the EOLUpgrades changes etc. I keep a system for support purposes of all *supported* releases, and when 21.10 reached EOL and I didn't need that system any more, I just re-installed to have it move to *kinetic* (22.10) as I already had a 22.04 system. Post-reinstall, my music was still there, along with my non-standard music player along with all my other stuff.

21.10 meant the 2021-October release; so just using quick math lets you know its 9 months of support ended in July 2022.  Even if you don't know which day; you can guess it's the 2nd-3rd Thursday of the month (*inc. 4th if there are 5 Thursdays in the month*) & you'll generally be at most a week out without needing to look up the release date (*found on notices*) or EOL warnings/notices.  As July 2022 is gone, the EOL should have been easy to guess.  Repositories get *archived* after EOL which is what the EOLUpgrades links helps you deal with (*and it's all manual, with no country mirrors*)

---

