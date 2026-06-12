---
title: "CPU thread management &amp; BOINC"
date: 2008-02-02
forum: General Help
---

### Post by PfromD on 2008-02-02
I have a problem when running the BOINC client ... My cooler isn't efficient enough, så the CPU runs (too) hot and triggers the BIOS-set restart due to core-temp.
Back in windoze I used 'Thread master', *really* easy-to-use service for limiting processor-usage by individual threads/apps. What's an Ubuntu-equivalent for doing the same thing?

---

### Post by dcstar on 2008-02-03
> **PfromD said:**
> I have a problem when running the BOINC client ... My cooler isn't efficient enough, så the CPU runs (too) hot and triggers the BIOS-set restart due to core-temp.
Back in windoze I used 'Thread master', *really* easy-to-use service for limiting processor-usage by individual threads/apps. What's an Ubuntu-equivalent for doing the same thing?

Irrelevant, just change your BOINC settings to use "x%" of CPU rather than the default 100%.

Scale it back until it no longer overheats your system.

---

### Post by hardyn on 2008-02-03
have they put an x-windows screen saver together for BOINC yet?  I like this approach a little better that what they are currently using, but yes it does work.

Thanks for any help.

---

### Post by PfromD on 2008-02-03
> **dcstar said:**
> Irrelevant, just change your BOINC settings to use "x%" of CPU rather than the default 100%.

Scale it back until it no longer overheats your system.
argh! totally forgot that you can set this on the account page. But I seem to recall that the account-set CPU limitations work like cr*p on windows, so I hope it works better on Linux.
But when following the process in the system monitor, it doesn't seem to be a setting for *scaling* CPU-usage as much as *scheduling*. By that I mean that the process gets continually stopped and restarted to attain the equivalent of running a period at only eg. 20% capacity. The end result is pretty much the same, but the service mentioned previously (ThreadMaster) has the process run continuously at the set limitations,

---

