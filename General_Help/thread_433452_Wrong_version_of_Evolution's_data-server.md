---
title: "Wrong version of Evolution's data-server"
date: 2007-05-05
forum: General Help
---

### Post by ctsdownloads on 2007-05-05
I must be missing something, but in a new install of Feisty, we are running evolution-data-server-1.10 instead 2.10? Considering how bugtastic this previous release is with the exchange servers and time zones, I really need to at least try to get the newer version on the off chance this amazingly obvious issue has been fixed.

[https://launchpad.net/ubuntu/+source/evolution/+bug/91637](https://launchpad.net/ubuntu/+source/evolution/+bug/91637)

What kills me is how "the fix is released" and clearly, just from the bug list above, it clearly is not based on comments made still on Launchpad. But to further rub salt into my wounds, I am still seeing that I have the older version of the data-server. Tell me this is something that is fixable?

Help!

---

### Post by ctsdownloads on 2007-05-05
Figured it out:
 
My proper time zone from the clock was set to Pacific/LosAngeles 

But in evolution (calender settings off of preferences), my time zone was Pacific/Pitcairn

So, I changed it to match "America/Los_Angeles" and saved it, restarted evolution and bingo - it's fixed. :guitar:

This worked in Edgy and Feisty for me.

---

