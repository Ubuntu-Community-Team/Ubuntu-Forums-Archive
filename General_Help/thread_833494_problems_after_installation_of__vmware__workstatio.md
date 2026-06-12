---
title: "problems after installation of  vmware  workstation 6 on  Hardy"
date: 2008-06-18
forum: General Help
---

### Post by balki2005 on 2008-06-18
Hello,

After  installation  of  VMWare  Workstation 6.0.3 build-80004 on Ubuntu Hardy. and when  I installed  my first  image (windows xp) I recieve this  error  on my syslog:

```

Jun 18 21:35:05 thunderdragon kernel: [   90.458354] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 18 21:35:05 thunderdragon kernel: [   90.458384] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 18 21:35:17 thunderdragon kernel: [  102.740402] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 18 21:35:17 thunderdragon kernel: [  102.740440] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 18 21:35:17 thunderdragon kernel: [  102.764942] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 18 21:35:17 thunderdragon kernel: [  102.765002] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 18 21:48:19 thunderdragon kernel: [  884.134787] rezound[6660]: segfault at fffffffc eip b75de578 esp bf8f4420 error 6
Jun 18 22:06:40 thunderdragon kernel: [ 1984.020512] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 18 22:06:40 thunderdragon kernel: [ 1984.020560] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 18 22:34:17 thunderdragon -- MARK --
Jun 18 22:36:48 thunderdragon kernel: [ 3789.984601] UDF-fs: No VRS found
Jun 18 22:36:49 thunderdragon kernel: [ 3791.083476] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 18 22:36:49 thunderdragon kernel: [ 3791.083520] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 18 22:36:49 thunderdragon kernel: [ 3791.087861] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 18 22:36:49 thunderdragon kernel: [ 3791.088336] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 18 22:36:54 thunderdragon kernel: [ 3796.268366] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 18 22:36:54 thunderdragon kernel: [ 3796.268434] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 18 22:36:54 thunderdragon kernel: [ 3796.272092] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 18 22:36:54 thunderdragon kernel: [ 3796.272162] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 18 22:37:36 thunderdragon kernel: [ 3837.806236] cdrom: This disc doesn't have any tracks I recognize!
Jun 18 22:38:30 thunderdragon kernel: [ 3892.369964] /usr/bin/serpen[7343]: segfault at 736e6157 eip b7c31ded esp bfd07cd0 error 4
Jun 18 22:38:39 thunderdragon kernel: [ 3900.454343] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 18 22:38:39 thunderdragon kernel: [ 3900.454392] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 18 22:38:39 thunderdragon kernel: [ 3900.461007] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 18 22:38:39 thunderdragon kernel: [ 3900.461061] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 18 22:38:40 thunderdragon kernel: [ 3901.476392] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 18 22:38:40 thunderdragon kernel: [ 3901.476439] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 18 22:38:40 thunderdragon kernel: [ 3901.479427] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 18 22:38:40 thunderdragon kernel: [ 3901.479471] VMBlock warning: DentryOpRevalidate: invalid args from kernel
Jun 18 22:54:17 thunderdragon -- MARK --

```

do  somebody what the  problem is, and what I can do to resolve  it ?

thanks  in advance,

Balki2005

---

### Post by flammon on 2008-07-02
I see the same errors. I don't have any VM started when errors occur. I'm running VMware Player 2.0.3 on a Hardy AMD64 system with 4 Gb of RAM.

---

