---
title: "Lignting &amp; Sunbird can't read Evolution web calendars"
date: 2007-03-12
forum: General Help
---

### Post by mat_london on 2007-03-12
This one is a real pain for me as I want to share calendars from my Evolution calendar on Ubuntu with work colleagues using Thunderbird on XP.

It appears that calendars published to the web from Evolution using the command "Publish Calendar Information" cannot be read properly by either the Lightning calendar extension for Thunderbird or the Sunbird. 

My calendars are published to [www.icalx.com](www.icalx.com). Google calendars has no problem with using them and neither does the php calendar that comes with icalx, they both display all the info without complaint.

However I get the following with Lightning & Sunbird (I get multiple pop up windows with this message for every diary entry I have with the current versions of Lightning & Sunbird )


Error Number: 0x80004005

[Exception... "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [calIIcalComponent.startTime]"  nsresult: "0x80004005 (NS_ERROR_FAILURE)"  location: "JS frame :: file:///home/mat/.thunderbird/r9jw6u15.default/extensions/%7Be2fda1a4-762b-4020-b5ad-a41df1933103%7D/js/calItemBase.js :: anonymous :: line 522"  data: no]

I have a suspicion it has something to with the way Evolution does Time Zone information, but am not sure.

Anyone got any ideas ?

Mat

---

