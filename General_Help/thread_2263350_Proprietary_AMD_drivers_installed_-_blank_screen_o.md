---
title: "Proprietary AMD drivers installed - blank screen on boot"
date: 2015-01-31
forum: General Help
---

### Post by craig-hall-worcester on 2015-01-31
Hi all, first time poster.

I'm running an R9 285, in a dual-boot setup with Windows 7 and Ubuntu 14.

I opted to use the AMD proprietary graphics drivers in place of the standard open-source ones to try to improve general performance (this was done through the Ubuntu system settings).

Now when I try to boot Ubuntu, it gets to a blank screen and does nothing.

I'd like to revert back to open source drivers firstly so I can use Ubuntu again. I tried using the purge -fglrx method but got error messages;

"W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to var/cache/apt
E: The package lists or status file could not be parsed or opened".

Secondly, is there any working AMD drivers I could use with my card so I can fully utilise my card?

Any help or advice would be really appreciated.

Thanks and regards.

---

### Post by phidia on 2015-01-31
Did you try using the [latest beta driver]("http://support.amd.com/en-us/download/catalyst-hotfixes") for that card?

---

### Post by QIII on 2015-01-31
Hello!

The message you got indicates that you have another package manager instance (either via the command line, synaptic or the Software Center) open simultaneously.  Make sure you close them all and open only one.

Which release of Ubuntu are you using?  14.04 or 14.10?

Did you install the driver via the Ubuntu repo or by downloading directly from the AMD website?  If directly from AMD, you will have to use a different method to remove the driver.

Because this new generation of AMD video cards is such a struggle for many Ubuntu users, Canonical has graciously agreed to provide me an R9 to conduct testing with and sort out all the problems (both with currently supported releases of Ubuntu and the development version) so I can provide better support here on the Forums and update the wiki in my signature.  Hopefully I will be able to give some definitive advice about how to use the proprietary driver in a couple of weeks.

Cheers!

---

