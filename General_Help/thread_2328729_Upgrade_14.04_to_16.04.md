---
title: "Upgrade 14.04 to 16.04"
date: 2016-06-23
forum: General Help
---

### Post by Jason_Hunter on 2016-06-23
I'm on a totally fresh 14.04, installed today and I've done update and upgrade

I do: 

 sudo do-release-upgrade -d

..and I get: 

Leser mellomlager






Det oppstod en kritisk feil 


Error in sys.excepthook:
Traceback (most recent call last):
  File "/tmp/ubuntu-release-upgrader-004nn0tc/DistUpgrade/DistUpgradeViewText.py", line 145, in _handleException
    "\n".join(lines))
  File "/tmp/ubuntu-release-upgrader-004nn0tc/DistUpgrade/DistUpgradeViewText.py", line 180, in error
    print(twrap(msg))
UnicodeEncodeError: 'ascii' codec can't encode character '\xab' in position 170: ordinal not in range(128)


Original exception was:
Traceback (most recent call last):
  File "/tmp/ubuntu-release-upgrader-004nn0tc/xenial", line 8, in <module>
    sys.exit(main())
  File "/tmp/ubuntu-release-upgrader-004nn0tc/DistUpgrade/DistUpgradeMain.py", line 242, in main
    if app.run():
  File "/tmp/ubuntu-release-upgrader-004nn0tc/DistUpgrade/DistUpgradeController.py", line 1876, in run
    return self.fullUpgrade()
  File "/tmp/ubuntu-release-upgrader-004nn0tc/DistUpgrade/DistUpgradeController.py", line 1691, in fullUpgrade
    self._view.updateStatus(_("Checking package manager"))
  File "/tmp/ubuntu-release-upgrader-004nn0tc/DistUpgrade/DistUpgradeViewText.py", line 159, in updateStatus
    print(msg)
UnicodeEncodeError: 'ascii' codec can't encode character '\xe5' in position 14: ordinal not in range(128)
=== Command terminated with exit status 1 (Thu Jun 23 20:29:20 2016) ===

---

### Post by Jason_Hunter on 2016-06-23
Ok, just did: 

```
LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8 LANGUAGE=en_US.UTF-8 sudo do-release-upgrade -d
```

..and seems to be working now.

---

### Post by grahammechanical on 2016-06-23
Do not be surprised if you end up not with 16.04 (xenial xerus) but with yakkety yak, the development version of 16.10. The -d switch in the command do-release-upgrade -d = development version.

See the section Upgrading to development releases in this wiki page.

[https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

If the upgrade is successful you will need to do regular updates over the coming months to get to 16.10 released version .

Regards

---

### Post by Bucky Ball on 2016-06-24
Couple of things: if you did a fresh install of 14.04 LTS, why didn't you install 16.04 LTS instead if that's where you wanted to be and could you mark the thread as solved if you require no further support. Thanks. (See green link in my signature.)

---

### Post by vasa1 on 2016-06-24
> **grahammechanical said:**
> Do not be surprised if you end up not with 16.04 (xenial xerus) but with yakkety yak, the development version of 16.10. The -d switch in the command do-release-upgrade -d = development version.

See the section Upgrading to development releases in this wiki page.

[https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

If the upgrade is successful you will need to do regular updates over the coming months to get to 16.10 released version .

Regards

If OP wants to stay with 16.04 LTS, maybe choosing the appropriate settings in "Software Sources and Updates" would help?

---

### Post by oldos2er on 2016-06-24
> **Jason_Hunter said:**
> Ok, just did: 

```
LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8 LANGUAGE=en_US.UTF-8 sudo do-release-upgrade -d
```

..and seems to be working now.

In addition to what grahammechanical said, if you're not interested in testing Yakkety you should do a clean install of 16.04. 

What does ```
lsb_release -a
``` say?

---

### Post by grahammechanical on 2016-06-24
The official method for upgrading 14.04 to 16.04 will not be active until 16.04.1 is ready for release.

> 14.04 LTS to LTS upgrades will be enabled with the 16.04.1 LTS point release, in approximately 3 months time.

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

This is why it is difficult to upgrade from 14.04 to 16.04. In fact it is easier to upgrade from 14.04 to 16.10 development version because 16.10 development version is available. Whereas, the LTS to LTS upgrade channel is not yet enabled.

And yes, I agree, if 14.04 is a new install and the OP wants 16.04, then freshing installing 16.04 is the way to do it.

---

### Post by Jason_Hunter on 2016-06-25
Well, this is the reason. I'm on a hosted ubuntu with sol VPS

It offers 14.04 as an image and not 16.04. It does however also offer 15.04, but I thought I would have to go through 2 iterations to 15.10 and then to 16.04, instead of from 14.04 to 16.04

It did however install 16.04 and not 16.10 with the -d switch

I also found out that 16.04 is not supported on sol vps, so I'm just going to install 15.04 and be done with it. Ticket closed.

---

### Post by Bucky Ball on 2016-06-25
15.04 is well out of support. I wouldn't go there. Surprised they'd be offering such an obsolete release for install.

Please mark the thread as 'solved' if you're done here. See green link in my signature. Thanks.

---

