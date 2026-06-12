---
title: "Users Periodically Lose Ability To Print, Except From Google Chrome"
date: 2013-09-06
forum: General Help
---

### Post by Kirk Schnable on 2013-09-06
I've got a strange issue plaguing some of our systems here.  Periodically, users will report that they lose the ability to print from LibreOffice.  They report that restarting the computer fixes the problem.  

We've been passing it off as a LibreOffice glitch, until today when I saw the same thing happen to a WINE program someone was printing out of.  I decided to investigate further.  When the issue occurs **nothing is logged** in any CUPS log, including access_log, error_log, and page_log.  Chrome prints normally, and Chrome print jobs immediately appear in page_log, but jobs from LibreOffice and WINE are totally ignored and don't show up in CUPS logs.

So, I decided to start looking at other logs, and I found this in my kern.log...

```
[...]
Sep  5 14:17:01 hostname kernel: [1736471.530964] type=1400 audit(1378408621.486:5291): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 14:17:02 hostname kernel: [1736472.531653] type=1400 audit(1378408622.486:5292): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 14:17:03 hostname kernel: [1736473.531651] type=1400 audit(1378408623.486:5293): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 14:17:04 hostname kernel: [1736474.531836] type=1400 audit(1378408624.486:5294): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 14:17:05 hostname kernel: [1736475.531658] type=1400 audit(1378408625.486:5295): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 14:17:06 hostname kernel: [1736476.532571] type=1400 audit(1378408626.486:5296): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 14:17:07 hostname kernel: [1736477.532872] type=1400 audit(1378408627.486:5297): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 14:17:08 hostname kernel: [1736478.532128] type=1400 audit(1378408628.486:5298): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 16:20:19 hostname kernel: [1743869.695596] type=1400 audit(1378416019.646:5299): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 16:20:19 hostname kernel: [1743869.698588] type=1400 audit(1378416019.650:5300): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 16:20:19 hostname kernel: [1743869.700664] type=1400 audit(1378416019.654:5301): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 16:20:19 hostname kernel: [1743869.726214] type=1400 audit(1378416019.678:5302): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 16:20:19 hostname kernel: [1743869.728150] type=1400 audit(1378416019.682:5303): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 16:20:19 hostname kernel: [1743869.750892] type=1400 audit(1378416019.702:5304): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 16:20:19 hostname kernel: [1743869.752825] type=1400 audit(1378416019.706:5305): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 16:20:19 hostname kernel: [1743869.757511] type=1400 audit(1378416019.710:5306): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 16:20:19 hostname kernel: [1743869.759386] type=1400 audit(1378416019.710:5307): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 16:20:19 hostname kernel: [1743869.767313] type=1400 audit(1378416019.718:5308): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 16:20:34 hostname kernel: [1743884.840388] type=1400 audit(1378416034.794:5315): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 16:20:34 hostname kernel: [1743884.861810] type=1400 audit(1378416034.814:5316): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 16:20:34 hostname kernel: [1743884.863565] type=1400 audit(1378416034.814:5317): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 16:20:35 hostname kernel: [1743885.050419] type=1400 audit(1378416035.002:5318): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 16:20:35 hostname kernel: [1743885.053092] type=1400 audit(1378416035.006:5319): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 16:20:35 hostname kernel: [1743885.055373] type=1400 audit(1378416035.006:5320): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 16:20:35 hostname kernel: [1743885.061361] type=1400 audit(1378416035.014:5321): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 16:20:35 hostname kernel: [1743885.063170] type=1400 audit(1378416035.014:5322): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 16:20:35 hostname kernel: [1743885.069418] type=1400 audit(1378416035.022:5323): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  5 16:20:35 hostname kernel: [1743885.071194] type=1400 audit(1378416035.022:5324): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  6 07:36:56 hostname kernel: [1798866.969330] type=1400 audit(1378471016.923:5325): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  6 07:36:56 hostname kernel: [1798867.003390] type=1400 audit(1378471016.955:5326): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  6 07:36:56 hostname kernel: [1798867.006051] type=1400 audit(1378471016.959:5327): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  6 07:36:56 hostname kernel: [1798867.011454] type=1400 audit(1378471016.963:5328): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  6 07:36:56 hostname kernel: [1798867.013446] type=1400 audit(1378471016.967:5329): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  6 07:36:57 hostname kernel: [1798867.050089] type=1400 audit(1378471017.003:5330): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  6 07:36:57 hostname kernel: [1798867.053975] type=1400 audit(1378471017.007:5331): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  6 07:36:57 hostname kernel: [1798867.059132] type=1400 audit(1378471017.011:5332): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  6 07:36:57 hostname kernel: [1798867.061167] type=1400 audit(1378471017.015:5333): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  6 07:36:57 hostname kernel: [1798867.065279] type=1400 audit(1378471017.019:5334): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  6 07:38:03 hostname kernel: [1798933.800603] type=1400 audit(1378471083.755:5355): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  6 07:38:03 hostname kernel: [1798933.806686] type=1400 audit(1378471083.759:5356): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  6 07:38:03 hostname kernel: [1798933.810533] type=1400 audit(1378471083.763:5357): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  6 07:38:03 hostname kernel: [1798933.815434] type=1400 audit(1378471083.767:5358): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  6 07:38:03 hostname kernel: [1798933.818024] type=1400 audit(1378471083.771:5359): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  6 07:38:03 hostname kernel: [1798933.827892] type=1400 audit(1378471083.779:5360): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  6 07:38:03 hostname kernel: [1798933.831123] type=1400 audit(1378471083.783:5361): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  6 07:38:03 hostname kernel: [1798933.834897] type=1400 audit(1378471083.787:5362): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  6 07:38:03 hostname kernel: [1798933.836551] type=1400 audit(1378471083.791:5363): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep  6 07:38:03 hostname kernel: [1798933.840726] type=1400 audit(1378471083.795:5364): apparmor="DENIED" operation="open" parent=1 profile="/usr/sbin/cupsd" name="/etc/pbis/user-ignore" pid=596 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
```

For testing, I've gone into /etc/apparmor.d/ on this machine and I've moved usr.sbin.cupsd to the disabled folder and restarted apparmor.  I was immediately able to print from LibreOffice and WINE again...

Is this an apparmor issue?  Is there a better way to fix it than disabling the CUPS profile?  Otherwise, I'll just have Puppet move this file on everybody's machines so that printing is fixed for everyone on Monday.

Thanks,
Kirk

---

### Post by tgalati4 on 2013-09-06
I would suspect a virus possibly.  I don't know how *apparmor* interacts with cupsd, but obviously cupsd tried to perform an operation that *apparmor* said "no" to.  So I would spend some time digging into the *[apparmor]("https://help.ubuntu.com/community/AppArmor")* framework to see why this is happening.

Also look at your change/upgrade history to see if *cupsd* or *apparmor* were changed recently causing a regression.  If that is the case, then a bug should be filed somewhere.

---

### Post by Kirk Schnable on 2013-09-13
The print jobs are lost somewhere between the application and CUPS.  I am still seeing this issue periodically.

I've noticed it happening now with some WINE programs, so I'm going to try to write a launcher that logs WINEDEBUG output to a text file so I can look at the winspool debug log and see if they provide any insights.

---

### Post by Kirk Schnable on 2013-09-25
After disabling AppArmor on a few test computers, I've determined that I may have been wrong to blame AppArmor for my issues.  The printing problems still seem to occur even with AppArmor turned off.

Does anybody have any other ideas?

---

### Post by Kirk Schnable on 2013-09-26
I still have not come up with a fix for this issue... disabling AppArmor is definitely not effective.  I'll have to dig through some CUPS debug logs on several computers.

---

