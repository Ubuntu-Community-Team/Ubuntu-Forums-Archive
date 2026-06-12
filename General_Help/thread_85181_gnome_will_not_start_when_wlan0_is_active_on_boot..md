---
title: "gnome will not start when wlan0 is active on boot."
date: 2005-11-01
forum: General Help
---

### Post by lasermike026 on 2005-11-01
When my wireless lan (wlan0) is configured to start on boot, gnome desktop will not start when I try to log in.

My wireless card is lynksys WMP54GS running via ndiswrapper.  This is incidental.

Is it possible that gnome will not start because the ip issued to wlan0 by dhcp is not resolvable?  Any idea's?

Thanks in advance,
Mike

---

### Post by lasermike026 on 2005-11-02
Update.

Tried to ping localhost and I realized it was down.  Interesting.  I have a small script in /etc/rc2.d that performs the dhclient call.  (I did that instead of having ubuntu up the wlan0 interface while testing a theory.)  In any case, I put an 'ifup  lo' before the 'dhclient wlan0' call and it resolve the issue.  I didn't change anything because it was all working fine and I had been hacking on the users workstation for 4 hours trying get the wireless card working then fixing the gnome startup issue.

My hunch is that when the ndiswrapper module loads up, the lo interface goes down.  I have no proof to support this hunch.  All I know is when the system boots, lo interface was down so I up'ed in a startup script.

Personally, I wish there was a linux driver so I didn't have to use ndiswrapper.

---

