---
title: "Invited to partial upgrade, yet no errors or warnings when sudo apt-get update"
date: 2013-03-04
forum: General Help
---

### Post by samsom63 on 2013-03-04
Hi all,

Since 3 or 4 days, I am invited to undergo a partial upgrade (i run ubuntu 12.10). The dialog box is horribly confusing as I cannot fathom the difference between "continue" and "partial upgrade". Anyway, I did some research and found that it was usually a bad idea so I opted to not do a partial upgrade. I ran sudo apt-get update without any warnings or errors whatsoever, and went on by upgrading the packages, again without any issue.

Yet, each time I turn on the computer, I get this same message about the partial upgrade. Where does that come from? Should I continue to ignore it?

---

### Post by plucky on 2013-03-04
> **samsom63 said:**
> Hi all,

Since 3 or 4 days, I am invited to undergo a partial upgrade (i run ubuntu 12.10). The dialog box is horribly confusing as I cannot fathom the difference between "continue" and "partial upgrade". Anyway, I did some research and found that it was usually a bad idea so I opted to not do a partial upgrade. I ran sudo apt-get update without any warnings or errors whatsoever, and went on by upgrading the packages, again without any issue.

Yet, each time I turn on the computer, I get this same message about the partial upgrade. Where does that come from? Should I continue to ignore it?

Try running ```
sudo apt-get dist-upgrade
``` as that will install new kernel upgrades when "sudo apt-get upgrade" will not.

See what it wants to install or remove before allowing it to continue. If in doubt,post to output of the command to the forum before continuing.

Dist-upgrade will not install a new distribution upgrade.


Good Luck

---

### Post by samsom63 on 2013-03-04
> **plucky said:**
> Try running ```
sudo apt-get dist-upgrade
``` as that will install new kernel upgrades when "sudo apt-get upgrade" will not.

See what it wants to install or remove before allowing it to continue. If in doubt,post to output of the command to the forum before continuing.

Dist-upgrade will not install a new distribution upgrade.


Good Luck

Many thanks, that was a good idea. In fact, it is a steam related issue:
```

The following packages will be REMOVED
  steam64
The following NEW packages will be installed
  steam-launcher
The following packages will be upgraded:
  steam:i386

```

My steam works well, so I am not sure I want to go ahead with this upgrade.

---

### Post by samsom63 on 2013-03-05
Well, I did dist-upgrade and steam works perfectly! Problem solved.

---

