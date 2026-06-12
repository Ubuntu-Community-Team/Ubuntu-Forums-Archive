---
title: "ubuntu alarms everyday"
date: 2016-07-22
forum: General Help
---

### Post by roya2 on 2016-07-22
I have a ubuntu  system that I brought home from work. It alarms every day at 5 AM. I installed a fresh 16.04 recently and it does the same thing again every day. How can I stop this ?
Thank you.

---

### Post by plip123 on 2016-07-22
Hi!

Does your computer turn on everyday at 5AM to beep? What do you mean by alarm? Could you give more info?

If you installed a fresh 16.04 and it still happens, I think it's probably a setting in your BIOS or something similar. It's definitely not part of the default install.

---

### Post by roya2 on 2016-07-22
It is similar to the alarms that we set to wake up in our phone. It is not very loud. it lasts for maybe 1 or 2 minutes. I looked in the BIOS but did not find anything similar to alarm clock.

---

### Post by grahammechanical on 2016-07-22
Do you have a motherboard user guide? See if you can download a version from the manufacturer's web site. Then you can read up on the BIOS/UEFI settings utility. When I enter my BIOS settings utility and go to APM configuration I get an option to enable/disable Power On by RTC Alarm. The guide book says this:

"Allows you to enable or disable RTC to generate a wake event. When this item is set Enabled, the items RTC Alarm Date/RTC Alarm Hour/RTC Alarm Minute/RTC Alarm Second will be come user-configurable with set values."

I give this information as an example of the sort of alarm settings that could cause this alarm activation. If this was a company machine connected to a company network it was most probably set up to wake up at 5 AM every day to connect to the company servers for some reason or another.

[https://en.wikipedia.org/wiki/Real-time_clock](https://en.wikipedia.org/wiki/Real-time_clock)

[https://en.wikipedia.org/wiki/Advanced_Power_Management](https://en.wikipedia.org/wiki/Advanced_Power_Management)

Regards.

---

