---
title: "Ubuntu 14.04 LTS boot issues after kernel upgrade"
date: 2014-10-10
forum: General Help
---

### Post by sgrutzik on 2014-10-10
Hi,

I'm running Ubuntu 14.04 LTS on a Dell Inspiron 1434. Since the latest kernel upgrade (to 3.13.0.37) the system hangs on booting. I don't even get to the loading screen with the logo and 5 dots, it just freezes on a black screen. I can boot fine if I choose to boot with an older kernel version (3.13.0.36 works) but it still hangs on resuming from hibernate. After the panic, I can't even restart with the SysRq REISUB sequence (SysRq is enabled and works fine with a manually induced crash). I've been having intermittent panics on resuming from hibernate (since about the previous kernel upgrade) but it wasn't every time at least was able to boot fine from a fully shut down state. I don't have any 3rd party drivers and the only proprietary software is ABAQUS (a finite element package, shouldn't have an effect on booting). 

I've been using various flavors of linux since about 2008 but have never had to do much digging below the surface beyond editing config files and the like. I know I should post some logs but having never had to deal with kernel issues I'm not sure what would be useful so just let me know. Also, this is the first time I've had to post on the forums so if I'm violating some etiquette please forgive me.

Any help or suggestions would be appreciated. Thanks.

---

### Post by whitesmith on 2014-10-10
Welcome to the forum; you're in the right spot. These are diagnostic steps that won't solve anything but may give us a starting point:

1 - When you freeze on a black screen can you boot from a tty (Ctrl-Alt-F2, let's say)?

2 - Can you boot into recovery mode?

---

