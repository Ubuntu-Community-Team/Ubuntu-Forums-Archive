---
title: "Canonical-livepatch error Apparmor"
date: 2021-05-18
forum: General Help
---

### Post by ffallateufps on 2021-05-18
Running Ubuntu 16.04 and trying to enable livepatch results in an error due to apparmor:

> root@server01:/etc/apparmor.d# ua enable livepatchOne moment, checking your subscription first
Unable to configure Livepatch: Failed running command '/snap/bin/canonical-livepatch config remote-server=https://livepatch.canonical.com' [exit(127)]. Message: /snap/core/11081/usr/lib/snapd/snap-confine: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory


ERROR: Unable to configure Livepatch: Failed running command '/snap/bin/canonical-livepatch config remote-server=https://livepatch.canonical.com' [exit(127)]. Message: /snap/core/11081/usr/lib/snapd/snap-confine: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory


root@server01:/etc/apparmor.d# canonical-livepatch 
/snap/core/11081/usr/lib/snapd/snap-confine: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory

Here is the event in syslog:
> 2021-05-18T20:51:09.154617+00:00 ps-dev-util01 kernel: [ 1198.196648] audit: type=1400 audit(1621371069.149:64): apparmor="DENIED" operation="open" profile="/snap/core/11081/usr/lib/snapd/snap-confine" name="/lib/x86_64-linux-gnu/libm-2.23.so" pid=12461 comm="snap-confine" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
2021-05-18T20:51:09.154618+00:00 ps-dev-util01 kernel: [ 1198.196661] audit: type=1400 audit(1621371069.149:65): apparmor="DENIED" operation="open" profile="/snap/core/11081/usr/lib/snapd/snap-confine" name="/lib/x86_64-linux-gnu/libm-2.23.so" pid=12461 comm="snap-confine" requested_mask="r" denied_mask="r" fsuid=0 ouid=0

I've tried adding the following rule into "/etc/apparmor.d/usr.lib.snapd.snap-confine.real":
```
/{,usr/}lib{,32,64,x32}/{,@{multiarch}/}libcap.so* mr,
``` 

I reloaded the profile but still won't allow me to run livepatch.

Any suggestions or help would be welcome.

---

### Post by grahammechanical on 2021-05-18
I do not know the correct answer. I am just guessing.

Livepatch is part of Ubuntu Advantage. It is free for personal use on up to 3 machines. Also part of Ubuntu Advantage is Ubuntu Extended Security Maintenance (ESM). This ESM is not necessary on Ubuntu that is still in standard support. It is my guess that you are getting this error because 16.04 has reached end of standard support life. I think that you need to register to get Extended Security Maintenance for 16.04. I do believe that it is also free for personal use. You may have already registered. If that is the case then I am guessing wrong. Sorry.

[https://ubuntu.com/advantage](https://ubuntu.com/advantage)

Regards

---

