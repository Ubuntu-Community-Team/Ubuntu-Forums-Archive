---
title: "Strange upgrade dialog"
date: 2014-09-03
forum: General Help
---

### Post by lz1dsb on 2014-09-03
Have you guys come across this. Since a couple of days my update dialog has change a little bit and I do not know why? 
It offers me a partial upgrade - but than it starts the distribution upgrade dialog! How can I fix this?

---

### Post by ThatBum on 2014-09-03
Open a terminal and put in, one at a time:
[FONT=courier new]sudo apt-get update
sudo dpkg --configure -a
sudo apt-get dist-upgrade
[/FONT]
It will update the package lists, attempt to fix any broken/half-installed packages, then run an upgrade with smart dependency resolution. Note that [FONT=courier new]apt-get dist-upgrade[/FONT] doesn't actually upgrade your distribution, as noted [here]("https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands").

Put the output here if it hits a snag anywhere.

---

### Post by coffeecat on 2014-09-03
What exactly do you mean by "distribution upgrade dialog"? As ThatBum points out, the apt-get option dist-upgrade doesn't upgrade you to a newer version but does an in-version update with intelligent dependency resolution. However, if you have accidentally upgraded to the current development version somehow, which is Utopic/14.10, dist-upgrade can be problematic while a version is still in development.

We need to be sure which version you are running, just in case you have accidentally upgraded or partially upgraded to 14.10. When you run the commands ThatBum suggests, post the output. Also, post the output of this command:

```
cat /etc/lsb-release
```

---

### Post by lz1dsb on 2014-09-03
Here's the output:
@NUC-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"

I'll check out the commands which ThatBum pointed out...

---

### Post by lz1dsb on 2014-09-03
> **ThatBum said:**
> Open a terminal and put in, one at a time:
[FONT=courier new]sudo apt-get update
sudo dpkg --configure -a
sudo apt-get dist-upgrade
[/FONT]
It will update the package lists, attempt to fix any broken/half-installed packages, then run an upgrade with smart dependency resolution. Note that [FONT=courier new]apt-get dist-upgrade[/FONT] doesn't actually upgrade your distribution, as noted [here]("https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands").

Put the output here if it hits a snag anywhere.

Thank you ThatBum!
This solved it. Just a quick question on the second command. From the dpkg manual I could see:"Configure  a package which has been unpacked but not yet configured.  If -a or --pending is given instead of package, all unpacked but unconfigured packages are configured."
So in my understanding this will take any package that was unpacked previously, but for some reason not upgraded correctly, and the last command will actually upgrade the pending packages. Correct?

---

### Post by ThatBum on 2014-09-03
Correct.

The first command is also important. It updates the local package database from the repository servers; it is the actual check for updates. [FONT=courier new]apt-get upgrade[/FONT] downloads and installs said updates based on the comparison of the database to what's installed. If the Internet connection was interrupted during [FONT=courier new]apt-get update[/FONT] some repositories would be updated and some would be outdated, which could be problematic, so make sure it completes successfully.

Also note that [FONT=courier new]apt-get[/FONT] is itself a frontend for [FONT=courier new]dpkg[/FONT]. 

Don't forget to mark the thread as solved in thread tools.

---

### Post by grahammechanical on 2014-09-03
To those of us running the development release (Utopic Unicorn - 14.10) that dialog is very familiar. I see that every day when I update. I never accept the offer. I click continue and I get the standard update mechanism. Running a Partial Upgrade when using the development release can cause more problems than it would solve. 

Regards.

---

### Post by lz1dsb on 2014-09-03
Thank you ;)

---

