---
title: "upgrade dapper server to edgy"
date: 2006-10-28
forum: General Help
---

### Post by mitjab on 2006-10-28
i want to upgrade dapper server to edgy but do not know how?

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)
this howto is not for server.

Is it smart to upgrade?

---

### Post by meng on 2006-10-28
One probable solution is to change all instances of 'dapper' in your /etc/apt/sources.list to 'edgy', then
sudo apt-get update
sudo apt-get dist-upgrade

I say probable because I think that should work, but I don't have any experience with the server edition.

But to get to your more fundamental question, how many things currently aren't working to your satisfaction with Dapper? And how important is it that your system doesn't break with the upgrade, such that you may need hours/days to fix the breakage? Upgrades have a higher risk of breakage than clean installs.

---

### Post by GSMD on 2006-10-30
Don't try to do this. Chances are high that you'll lose your server due to variou sbugs that  still present  in Edgy. I've tried on 2 servers and Edgy ruined both of them.

---

### Post by mitjab on 2006-10-31
i try and it works for me.

My server still workimg after dist-upgrade.

---

