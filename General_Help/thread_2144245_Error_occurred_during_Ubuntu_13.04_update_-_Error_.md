---
title: "Error occurred during Ubuntu 13.04 update - Error Mounting Filesystems"
date: 2013-05-11
forum: General Help
---

### Post by anchapin on 2013-05-11
I started the update process for Ubuntu 13.04 from 12.10.  Then the power cord was accidentally pulled out and the computer battery died. Now I get the following message when I turn it on "General error mounting filesystems. A maintenance shell will now be started. CONTROL-D will terminate this shell and reboot the system." Then it has "root@[username]-HP-G60-NOTEBOOK-PC:~#"

I am a beginner Ubuntu user and prefer step by step instructions. Also, I am sorry if this has been posted before, but I searched and couldn't find anything that seemed to match.

---

### Post by ibjsb4 on 2013-05-12
While in the maintenance shell enter

```
sudo apt-get -f install
```

And post the output using code tags.

[ATTACH=CONFIG]242504[/ATTACH]

---

### Post by anchapin on 2013-05-17
[FONT=arial]Thanks for the help. This is what I get.[/FONT]
```
[FONT=arial]
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: dpkg was interrupted, you must manually run 'sudo dpkg -- configure -a' to correct the problem.[/FONT]

```[FONT=arial]
Then after doing what it said, I got this.

[/FONT]
```
[FONT=arial]dpkg: error: unable to access dpkg status area: Read-only file system
[/FONT]
```
> **ibjsb4 said:**
> While in the maintenance shell enter

```
sudo apt-get -f install
```

And post the output using code tags.

[ATTACH=CONFIG]242504[/ATTACH]

---

### Post by debrota on 2013-05-18
I have essentially the exact same problem, with the exact same responses from the maintenance shell.  I had a working 12.04 system.  I authorized the upgrade to 13.04.  When I got back to the PC, there had been a power failure.  I am unsure if the upgrade succeeded or not, but now all I get is the maintenance shell.  I can see a linux partition on /dev/sda1, an extended partition on /dev/sda2, and a linux swap partition on /dev/sda5.

---

### Post by bandrew02 on 2013-05-19
try doing


sudo do-release-upgrade

That should work

---

### Post by wildmanne39 on 2013-05-19
*Thread moved to **General Help**.*

---

### Post by anchapin on 2013-06-08
When I try what you said below, I get the following.

```
Checking for a new Ubuntu release
```

Then it doesn't do anything else.


> **bandrew02 said:**
> try doing


 sudo do-release-upgrade

That should work

---

### Post by sbarron on 2013-06-11
> **anchapin said:**
> When I try what you said below, I get the following.

```
Checking for a new Ubuntu release
```

Then it doesn't do anything else.

same for me doesn't do anything adfter that, same issue i think with the power being cut on the upgrade.

---

### Post by nkg on 2013-10-18
I had similar problem in Kubuntu after upgrade from 13.04 to 13.10. I solve it and descriebe sollution in [Kubuntu forum]("http://www.kubuntuforums.net/showthread.php?62233-Kubuntu-won-t-start-after-tried-to-upgrade-it-to-12-10&p=337186&viewfull=1#post337186").

---

