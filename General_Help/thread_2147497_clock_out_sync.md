---
title: "clock out sync"
date: 2013-05-22
forum: General Help
---

### Post by johntd on 2013-05-22
Recently the clock on my Ubuntu 12.04 keeps on losing the time and date by years, the only way that I can get it back to the right time is by going into my Win 7 and doing a time update from there, this is not a daily thing, it may go allright for some time before losing it again.

---

### Post by sudodus on 2013-05-22
The standard behaviour is that date and time are synced via the internet in Ubuntu. How are your settings? There is a small GUI program, that can do it for you in settings.

Click on the cog wheel at the top right corner,

select System Settings -- Time & Date

If the problem appears after the computer has been shut down, your CMOS or 'clock' battery might need to be replaced. It is usually a CR2032 battery. 

> *CR2032 battery* is a button cell lithium *battery* rated at 3.0 volts. It is commonly used in computers as a CMOS *battery*

---

### Post by johntd on 2013-10-08
I have replaced the battery but still having to reset the time and date when booting up

---

### Post by sudodus on 2013-10-08
This is what I think: Either the new battery is also bad, or there is something wrong with your hardware. But I am not sure. What about Windows? Are you running Windows often enough to know if you have the same problem when booting into Windows? And what about the clock, that you see in the BIOS menus?

Or could it be a problem, that Windows is using one time system and Ubuntu another? In that case the offset would be exact hours (and the minutes would stay correct) for most time zones. You can set Ubuntu to assume that the hardware clock is set in universal time UTC (see more details in ```
info date
``` or browse the internet), while Windows might be set to use the local time.

---

### Post by johntd on 2013-10-10
I have now tried leaving the power on to the computer, that is I shut down the computer but leave the mains power on, this seems to have the desired affect, ie the clock and callender keep time, this looks like it may be the new battery that not working.

---

