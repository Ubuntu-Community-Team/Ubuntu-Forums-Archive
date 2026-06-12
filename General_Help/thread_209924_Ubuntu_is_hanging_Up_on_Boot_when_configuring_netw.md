---
title: "Ubuntu is hanging Up on Boot when configuring network interface"
date: 2006-07-05
forum: General Help
---

### Post by mikeymike1 on 2006-07-05
Hi,

When I try to load Ubuntu, on the boot screen, when I reach "loading network interfaces" it hangs there for about 2-3 minutes followed by what seems to be an error message. I'm assuming it has something to do with installing my network card with ndiswrapper.

However, when I load in recovery mode, I get in just fine; the internet works fine, as well.

Please help.

Thanks,
Mike

---

### Post by jimmygoon on 2006-07-06
You probably just have it configured improperly, hence why it doesn't work when booting but does when using the recovery.

Two things: First off when it "hangs" hit "Control+C" and it will just stop trying to configure that network device and then you can go a step further and disable that network device in the "Administrative Networking" so that during boot it won't even try to configure it :)

Good Luck! I've never been unfortunate enough to have to use ndiswrapper so... :P

---

