---
title: "Update Manager    - Not updating!"
date: 2008-05-16
forum: General Help
---

### Post by opm595 on 2008-05-16
Hi,
I've recently ran up Hardy on an old system (bios circa 1999) that was running Win98 and everything has been running fine. However, when I  booted it up this morning I was alerted to the auto updates, and as normal clicked on the update icon on the panel etc. The mouse pointer then turns into the circle/timer type icon and all seems normal but then update manager does nothing. I've attempted to download updates several times and at one stage left it for an hour and not a single update was downloaded or installed. I'm properly connected to the Net, browser works, email, pings etc, just update manager will not update. Strangely though, it was working fine a yesterday.

The only thing I've installed since yesterday is LAMP (which seems to be running Ok) - could this cause any problems with Update Manager?

Can anyone shine some light on this one?

Thanks in advance

---

### Post by Gunman1982 on 2008-05-16
Open a console and execute 'sudo apt-get update' and then look what it says.

---

### Post by Bubba64 on 2008-05-16
> **opm595 said:**
> Hi,
I've recently ran up Hardy on an old system (bios circa 1999) that was running Win98 and everything has been running fine. However, when I  booted it up this morning I was alerted to the auto updates, and as normal clicked on the update icon on the panel etc. The mouse pointer then turns into the circle/timer type icon and all seems normal but then update manager does nothing. I've attempted to download updates several times and at one stage left it for an hour and not a single update was downloaded or installed. I'm properly connected to the Net, browser works, email, pings etc, just update manager will not update. Strangely though, it was working fine a yesterday.

The only thing I've installed since yesterday is LAMP (which seems to be running Ok) - could this cause any problems with Update Manager?

Can anyone shine some light on this one?
Thanks in advance

Have you opened software resources in administrative or synaptic and made sure the repositories are ticked and the download section is ticked and if you installed with CD is ticked off.

---

### Post by forrestcupp on 2008-05-16
You could also try going to System->Administration->Software Sources and try a different server.

---

