---
title: "PCMCIA Wireless card not showing up in IFCONFIG?"
date: 2012-11-10
forum: General Help
---

### Post by pakopako on 2012-11-10
I'm running Ubuntu 11.04 on a Toshiba M200 and have been using a PCMCIA AR5001X+ Wireless Network Adapter for a year now. Tried using it today and it doesn't show up on IFCONFIG -A

The PCMCIA card shows up with LSPCI and it still blinks so I know it's getting power.
PCCARDCTL STATUS shows that there's a card inserted (though PCCARDCTL IDENT shows nothing).

---

### Post by pakopako on 2012-11-11
Last week I tried installing NDISwrapper to install a Windows SDcard  driver (didn't work) and I uninstalled it today. Could this be causing  issues?

Yes. Yes it is. Searched for my PCMCIA card and found [two](http://ubuntuforums.org/showthread.php?t=1054020) [pages](http://ubuntuforums.org/showthread.php?t=1763414) from Ubuntuforums that detail an additional step needed to remove NDISwrapper.  That seems to have done the trick.

---

