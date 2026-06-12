---
title: "How to disable apparmor for Chromium snap? (Ubuntu 20.04)"
date: 2020-08-18
forum: General Help
---

### Post by fluffy20470-50233 on 2020-08-18
Solved by running chromium with this command:
```
/snap/chromium/current/usr/lib/chromium-browser/chrome
```


////////////////////////////////////////////////////////////////////////////////////////////////////////


When I type:

```
sudo apparmor_status
```

these 2 profiles are shown as enforce:
```
snap.chromium.chromedriver
snap.chromium.chromium
```

When I type:

```
sudo aa-complain /var/lib/snapd/apparmor/profiles/snap.chromium.chromium
```

I get this message:

```
Profile for /var/lib/snapd/apparmor/profiles/snap.chromium.chromium not found, skipping
```

I want to remove the Chromium apparmor profiles from [enforce] because I'm pretty sure it's interfering with u2f (my USB device is usable in it's desktop app, but not in Chromium). I'm using the default Chromium version that gets installed in Ubuntu 20.04 (installed using Synaptic).

---

### Post by CelticWarrior on 2020-08-18
I'm not sure it has anything to do with apparmor. It may have something to do with snap limitations (app confinement). Chromium is actually a snap, installed by the .deb file in the repositories.

Please wait for other posts.

---

### Post by deadflowr on 2020-08-18
uf2 devices is a plug/slot in chromium which can be set in The Chromium's home page Permissions tab in Software.
(or check it with the snap connections command)

---

### Post by TheFu on 2020-08-18
# See the available options for a snap package
$ snap connections <application-name> 

Looks like chromium has 
```
u2f-devices               chromium:u2f-devices               :u2f-devices
```
as connections. There are a bunch.

```
snap connect chromium:u2f-devices
```
should allow the u2f connection. I didn't test it.

You can run chromium from the snap, but without the snap constraints. Just point directly at the application and run it.
**/snap/chromium/current/usr/lib/chromium-browser/chrome & **
May want to use constraints that you control, like firejail, however.

---

### Post by fluffy20470-50233 on 2020-08-19
> **deadflowr said:**
> uf2 devices is a plug/slot in chromium which  can be set in The Chromium's home page Permissions tab in Software.
(or check it with the snap connections command)
> **TheFu said:**
> # See the available options for a snap package
$ snap connections <application-name> 

Looks like chromium has 
```
u2f-devices               chromium:u2f-devices               :u2f-devices
```
as connections. There are a bunch.

```
snap connect chromium:u2f-devices
```
should allow the u2f connection. I didn't test it.

Thank you for your reply. I typed [snap connect chromium:u2f-devices] into my terminal but unfortunately it didn't let me use my usb device (ledger nano s) with chromium

I was however able to get it working in Firefox by completely disabling apparmor [sudo systemctl stop apparmor > sudo systemctl disable apparmor]


> **TheFu said:**
> 
You can run chromium from the snap, but without the snap constraints. Just point directly at the application and run it.
**/snap/chromium/current/usr/lib/chromium-browser/chrome & **


Sorry what do you mean by this? what would be the exact command to type into the terminal to do this?

---

### Post by TheFu on 2020-08-19
> **fluffy20470-50233 said:**
> Sorry what do you mean by this? what would be the exact command to type into the terminal to do this?

```
$  /snap/chromium/current/usr/lib/chromium-browser/chrome & 
```

Leave off the beginning "$" - that just shows that a normal userid is being used.

---

### Post by deadflowr on 2020-08-19
It might just be that the snap doesn't have support for this particular device.
What you might do is try asking about the device's support and how to help get it fixed over in this thread:
[https://discourse.ubuntu.com/t/call-for-testing-chromium-browser-deb-to-snap-transition/11179]("https://discourse.ubuntu.com/t/call-for-testing-chromium-browser-deb-to-snap-transition/11179")
Here's a similar issue (different device): [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1851211]("https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1851211")
You'll most likely be asked to file a bug so see: [https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")

---

### Post by fluffy20470-50233 on 2020-08-19
> **TheFu said:**
> ```
$  /snap/chromium/current/usr/lib/chromium-browser/chrome & 
```

Leave off the beginning "$" - that just shows that a normal userid is being used.

Thank you. This allowed me to use my usb device (Ledger Nano S) with Chromium.

> **deadflowr said:**
> It might just be that the snap doesn't have support for this particular device.
What you might do is try asking about the device's support and how to help get it fixed over in this thread:
[https://discourse.ubuntu.com/t/call-for-testing-chromium-browser-deb-to-snap-transition/11179](https://discourse.ubuntu.com/t/call-for-testing-chromium-browser-deb-to-snap-transition/11179)
Here's a similar issue (different device): [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1851211](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1851211)
You'll most likely be asked to file a bug so see: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)


Thank you. I got it working with Chromium thanks to TheFu's command, and I also got it working with Firefox after disabling apparmor completely (using: sudo systemctl stop apparmor > sudo systemctl disable apparmor).

I prefer Firefox so I'm going to try to get it working in Firefox without completely disabling apparmor.

---

