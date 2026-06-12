---
title: "Post-upgrade login woes"
date: 2018-02-19
forum: General Help
---

### Post by charlie_bravo2 on 2018-02-19
I'm running Xubuntu, and as of this morning had decided to resolve an issue I was having.  For a while now, I've noticed a good number of errors when attempting to upgrade my distro on my Dell laptop.  Today I gave the messages a good look and noticed that the errors occurred when attempting to retrieve files from the Zesty repositories.  When I manually checked the locations I noticed most of them were no longer available.  I edited my sources.list, replacing Zesty with Bionic, and saved.

I then ran sudo apt-get update.  I got an error suggesting I run sudo apt-get -f install.  This ran, and I re-ran update, with more errors.  The helpful error message instructed me to run the commands in the sources.list to re-obtain the keys.  Did this, no errors, re-ran the update, no errors this time, and then ran sudo apt-get dist-upgrade.

When it finished, I rebooted my machine, and have been non-functional since.  The system brings me to my DM (XFCE), shows my account, I can enter my password, and after a few seconds, I am returned to the login screen.  I was able to CTRL-ALT-F4 and login there at the command prompt, so the machine is still recognizing my credentials.  It appears the only issues lies in accessing the system through the DM.  

I have read some other similar problems, and have tried each suggested solution: 

I've re-named my ~/.profile, ~/.bash_profile and ~/.bash_login, no fix.

I've tried installing KDE with
sudo apt-get install kubuntu-desktop

I've tried reinstalling XFCE with
sudo apt-get install xubuntu-desktop

Neither of the last two worked.

That's all the details I can recall at this time.  If you have a fix, please let me know.

Thanks in advance.  Huscarl91

---

### Post by wildmanne39 on 2018-02-19
*Thread moved to **General Help, a more appropriate forum**.*

---

### Post by cruzer001 on 2018-02-19
Jumping from Zesty to Bionic is not a recommended way to upgrade.  Of course you have found this out.

I think I would try reverting back to Zesty, if you can.  Then do an eol upgrade.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

IMO your better off doing a fresh install.

---

### Post by Impavidus on 2018-02-20
Zesty is an old release. It has been dead for over a month and that's why you couldn't install anything.

Bionic is the development version. It's unfinished and not released yet. Problems are to be expected, in particular after a dirty upgrade.

You should have upgraded to 17.10 Artful, the currently supported non-LTS release. But as it stands now, I suggest a fresh install of Artful. Download the 17.10.1 image, make a live disk and boot it, make backups if you need and install.

---

### Post by charlie_bravo2 on 2018-02-25
Attempted the fix as described in the article you linked.  Got to the Update stage, and the sudo apt-get update failed for the inability to resolve old-releases.ub7ntu.com.

Any suggestions of what the correct domain I'm supposed to be looking in for the updates?

Thanks in advance.

---

### Post by monkeybrain20122 on 2018-02-25
Just save your data and do a fresh install to a current supported version of Ubuntu, save you a lot of time and troubles than "upgrade". Also Bionic is currently under development so unless you intend to use your OS for testing, stay away from it.

---

