---
title: "Gutsy Gibbon &amp; Western Australia Daylight Saving"
date: 2007-10-28
forum: General Help
---

### Post by zoetrope666 on 2007-10-28
Hi, 

I live in Western Australia and we switched over to Daylight Saving time today. It's part of a 3 year trial. There are other posts on these forums on the topic, but they deal with when the trial first came in to being, and so they only provide fixes for dapper and edgy at best. I wonder if there's a solution out there to make Gutsy clocks recognize Daylight Saving time?

Thanks for any help!
Ashlee

---

### Post by zoetrope666 on 2007-10-28
Ah, I think I've sorted it out...

I right clicked on the date & time and selected 'Adjust Date &Time'. 

Under 'configuration' I clicked to select 'Keep synchronized with Internet Servers'. This required me to download a package. 

After it had downloaded and installed, I clicked 'Select Servers' under the 'Time Servers' option in the 'adjust date & time' window. I selected the 'ntp.per.nml.csiro.au (Perth, Australia)' option, then clicked close.

I then checked that the time zone was correct - it should be set on 'Australia/Perth'. 

I then clicked close. 

I just restarted my system and the correct time appears to have stay put, so - good so far!

Cheers!

---

### Post by por100pre1 on 2007-10-28
Not useful in the short term, but [filing a bug]("https://bugs.launchpad.net/bugs/+filebug") against **tzdata** can be part of a definitive solution.

EDIT: Glad you sorted it out with NTP. However it must be fixed in manual time as well. :-k

---

### Post by Caffeine_Junky on 2007-10-28
> **zoetrope666 said:**
> Ah, I think I've sorted it out...

I right clicked on the date & time and selected 'Adjust Date &Time'. 

Under 'configuration' I clicked to select 'Keep synchronized with Internet Servers'. This required me to download a package. 

After it had downloaded and installed, I clicked 'Select Servers' under the 'Time Servers' option in the 'adjust date & time' window. I selected the 'ntp.per.nml.csiro.au (Perth, Australia)' option, then clicked close.

I then checked that the time zone was correct - it should be set on 'Australia/Perth'. 

I then clicked close. 

I just restarted my system and the correct time appears to have stay put, so - good so far!

Cheers!

Cool!  ...welcome to Day Light Savings :)

---

