---
title: "Issue with Ubuntu Software Manager and updates"
date: 2016-11-03
forum: General Help
---

### Post by lanaro on 2016-11-03
Hi guys! I'm having a really annoying issue,the software manager is not letting me install or updating any software at all...when i click on install it just says installing for a few seconds and then it goes back...it says i got upgrades to do (even os related) but i can't do any of em.I also have a red icon on the too saying "A problem occurred when checking for updates"...And i know few ppl had this issue but reading on forums i didn't really found anything useful...and yes i do know that i can install .deb files from the terminal,but that's not just about .deb packages...
Thank you guys in advance for your help!!you're the best!

ps: I'm learning programming and i don't really know what text editor i should use...sublime text seems awesome but i don't know if is worth it.

---

### Post by jeremy31 on 2016-11-03
You should be able to update using terminal ```
sudo apt-get update && sudo apt-get upgrade
```
You should close the Software Manager before running the commands or they will likely fail

---

### Post by howefield on 2016-11-03
> **lanaro said:**
> ...and yes i do know that i can install .deb files from the terminal,but that's not just about .deb packages...

You'll probably get more of a clue as to what is the problem by updating from the terminal..

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

The output of..

```
cat /etc/*-release
```
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

might be useful if you get errors.

Edit : ninja'ed :)

---

### Post by lanaro on 2016-11-03
Thanks for the help guys... the update on terminal seems fine but is not really updating stuff,and the upgrade is saying "Reading package lists... Done
```
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 ubuntu-release-upgrader-core : Depends: python3-distupgrade (= 1:16.04.17) but 1:16.04.12 is installed"
 ubuntu-release-upgrader-gtk : Depends: python3-distupgrade (= 1:16.04.17) but 1:16.04.12 is installed
 update-manager : Depends: update-manager-core (= 1:16.04.3) but 1:16.04.4 is installed
 update-manager-core : Depends: python3-update-manager (= 1:16.04.4) but 1:16.04.3 is installed
E: Unmet dependencies. Try using -f.
```

---

### Post by ian-weisser on 2016-11-03
Please show us the complete output of:
```
apt-cache policy python3-distupgrade
```

---

### Post by lanaro on 2016-11-03
That's what it says
```
 Installed: 1:16.04.12
  Candidate: 1:16.04.17
  Version table:
     1:16.04.17 500
        500 http://au.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://au.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
 *** 1:16.04.12 500
        500 http://au.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://au.archive.ubuntu.com/ubuntu xenial/main i386 Packages
        100 /var/lib/dpkg/status

```

---

### Post by ian-weisser on 2016-11-03
Let's try the easy solution first:
```
sudo apt full-upgrade
```

---

### Post by lanaro on 2016-11-05
> **ian-weisser said:**
> Let's try the easy solution first:
```
sudo apt full-upgrade
```
Is giving me the same response as the normal upgrade :(

---

### Post by lanaro on 2016-11-07
ps: that happened after i installed python 3.5

---

### Post by ian-weisser on 2016-11-07
Are you saying that you replaced the default version of Python3 with a different version of your choice before your problems began?
Or are you saying that the normal system upgrade process just happened to incrementally upgrade Python3 before your problems began?

---

### Post by lanaro on 2016-11-08
I replaced the default version of Python,which was 2.7,with 3.5,and then my issue came,i also have a red circle with a white line on the top of my screen that says "A problem occurred while checking for updates"

---

### Post by ian-weisser on 2016-11-08
Hmmm.


A default install of Ubuntu 14.04 and 16.04 and 16.10 Ubuntu includes *both* Python 2.7 *and* Python 3.5.
Never change them. Elements of your system, including python-apt, still rely upon Python 2.7 in some versions of Ubuntu. Changing the version of Python wrecks your system.
You can always add new versions of Python in addition to the system-provided versions.

Which version of Ubuntu are you running?
How exactly did you make this change to your system? Please be as detailed as possible.

---

### Post by lanaro on 2016-11-09
> **ian-weisser said:**
> Hmmm.


A default install of Ubuntu 14.04 and 16.04 and 16.10 Ubuntu includes *both* Python 2.7 *and* Python 3.5.
Never change them. Elements of your system, including python-apt, still rely upon Python 2.7 in some versions of Ubuntu. Changing the version of Python wrecks your system.
You can always add new versions of Python in addition to the system-provided versions.

Which version of Ubuntu are you running?
How exactly did you make this change to your system? Please be as detailed as possible.

Well,if i remember right i just downloaded,unzipped and installed python3.5 >.<

---

### Post by ian-weisser on 2016-11-10
Does the command 'python' launch py2 or py3?

---

### Post by lanaro on 2016-11-11
It does launch Python 2.7.1.2

---

### Post by ian-weisser on 2016-11-11
Then you can probably just uninstall the foreign Python 3.5 you installed over the Ubuntu version, then use apt to reinstall the Ubuntu Py3 packages.
Backup your data first - success is not certain.

You might still need to reinstall Ubuntu. Had you deleted Py2, you would certainly need to reinstall.

---

### Post by shellback84 on 2016-11-11
I had this very issue with 16.04 almost a year ago. For me there was a trap and that was I could not update anything including any updates that might have fixed and addressed this very problem. I could not download packages nothing. The ubuntu software center would only show my installed packages and no potential new packages, none. Even using the terminal did not work. My fix? Going back to 14.04 fixed everything. The problem with that is, 14.04 is old and I want to update. But your post has convinced me the problem is still there and I must wait once again before I upgrade. If you fix this could you please let me know what you did. The people on here are very nice and tried to help me but going back to 14.04 was the only way I could use ubuntu again.

---

### Post by ian-weisser on 2016-11-12
Overwriting the system-provided version of Python3 is not a some-version-of-Ubuntu-is-broken issue. It's a classic new-power-user mistake, we get a few every cycle.
That's what happens to a small outlier of clever users when they have real control over their system. Real power is also the power to break it.

---

### Post by lanaro on 2016-11-12
> **ian-weisser said:**
> Then you can probably just uninstall the foreign Python 3.5 you installed over the Ubuntu version, then use apt to reinstall the Ubuntu Py3 packages.
Backup your data first - success is not certain.

You might still need to reinstall Ubuntu. Had you deleted Py2, you would certainly need to reinstall.

is not even letting me uninstall Ubuntu, is saying "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. " and when i do that command and try again it says "E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).",then i do apt-get -f install and it says "E: Sub-process /usr/bin/dpkg exited unexpectedly" i guess i will need to reinstall Ubuntu...Would you advice me to install Ubuntu rather than xubuntu this time?and would you advice 16.04 again or 14.04? and is there any way to keep al my files?Thanks very much!

---

### Post by lanaro on 2016-11-12
> **ian-weisser said:**
> Overwriting the system-provided version of Python3 is not a some-version-of-Ubuntu-is-broken issue. It's a classic new-power-user mistake, we get a few every cycle.
That's what happens to a small outlier of clever users when they have real control over their system. Real power is also the power to break it.
i Agree :D

---

### Post by lanaro on 2016-11-12
I think i'll try with lubuntu now,since its lighter and the pc im running now is pretty crap ahah

---

