---
title: "USB Login key?"
date: 2007-03-13
forum: General Help
---

### Post by ew16301 on 2007-03-13
Are there any USB login keys for Ubuntu like Rohos? I want something where you can plug in your USB key and it logs you in, and locks when you pull it out. Thanks in advance.

---

### Post by Desummoner on 2007-10-31
Such solution for Ubuntu is "The PAM_USB Project" ( [http://www.pamusb.org/](http://www.pamusb.org/) )

Supported: Two-factor authentication, Non-intrusive (USB Serial number, model and vendor verification used), One Time Pads, Support for all kind of removable devices (SD, MMC, etc).

Included in Ubuntu repository (universe) so could be installed via apt/Synaptic:
```
sudo apt-get install libpam-usb pamusb-tools
```

BUT! Current version of repository package **pamusb-tools** is incompatible with current version of Ubuntu (7.10 Gutsy), so it need to be manually patched: simply get file **pamusb-agent** from CVS ( [https://pamusb.svn.sourceforge.net/svnroot/pamusb/trunk/pam_usb/tools/pamusb-agent](https://pamusb.svn.sourceforge.net/svnroot/pamusb/trunk/pam_usb/tools/pamusb-agent) ) and replace with it same file from package located at **/usr/bin/pamusb-agent**

Make initial configuration from QuickStart:Setting up ( [http://www.pamusb.org/doc/quickstart#setting_up](http://www.pamusb.org/doc/quickstart#setting_up) ) and you're done.

Some notes (IMHO, of course):
[LIST]
[*]An only way to get station locked with plugging out USB flash drive and not get treated by "unsafe device removal" notifications is to disable one_time_pad and don't have any partitions on USB flash drive, which can be automounted.
[*]USB flash drives with empty Vendor field (eg. Apacer HT203) are not supported by software (will be fixed AFAIK)
[/LIST]

Project still need some fixes and IMHO some improvements, but it is great!
:)

---

### Post by Jinx-Wolf on 2008-01-19
I'm still having some issues. I managed to get it to authenticate my sudo password, however, removing it does not lock the computer.

When I disable one_time_pad, it makes me enter my password when I login or launch a program, which beats the purpose of even having the USB key.

When formating to a unmountable format, it no longer recognizes the USB drive, because it needs the UUID.

(after messing around for a couple hours, I've managed to make it not work at all, so I'm going to attempt a reinstall... and sorry for reviving a dead thread)

Edit:
I purged then reinstalled fresh, reconfiguring everything. Now it works fine, but still won't lock.

Edit2:
Well, now it doesn't work again. All I did was add the commands to lock, and changed the device name in both the device's field, and my user's field. Now I get:

```
* Authentication request for user "wolf" (pamusb-check)
* Device "LEXAR" is connected (good).
* Performing one time pad verification...
* Pad checking failed !
* Access denied.

```

---

### Post by fb2007 on 2008-04-07
Does anybody know how to do anything like this with Compact Flash card?

---

