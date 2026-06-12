---
title: "Thunderbird Problems"
date: 2021-04-20
forum: General Help
---

### Post by electrosteam on 2021-04-20
My TB was working a few days ago, now will not send because TB claims the ISP server security is not acceptable.
No change in the ISP settings that I can see.

Also, ALL my address books are gone !

Checking the Mozilla/Thunderbird support forum shows several messages over the last few days with a litany of problems.

There was an upgrade to Lubuntu offered a few days ago, and I always simply accept and move on with life.
This could have included TB upgrades that damaged the install.

1. Can anybody confirm that a recent TB upgrade creates problems ?

2. If so, is there any plan for correction ? 

3. Should I give up on TB and use something else ?

Keep well,
John.

---

### Post by guiverc on 2021-04-20
You haven't provided release details.  We don't even know your desktop (a legacy Lubuntu or modern Lubuntu?) though I doubt it's desktop specific (ISP certificate that expired would be what I'd check)

 I recall (*some time ago*) a notice that for one release (an LTS) a major change was being implemented that caused a later version to replace the earlier version which had the potential for problems (*usually security fixes are backported to the older stable version; the warning was this wasn't being done instead the LTS release would get a later version*), but that was weeks ago I think, and I don't know your release so may not impact you.  (*I maybe thinking of what's here* - [https://ubuntuforums.org/showthread.php?t=2458076](https://ubuntuforums.org/showthread.php?t=2458076))

---

### Post by electrosteam on 2021-04-20
The release is current Lubuntu 20.04.2 LTS with Kernel 5.8.0-50-generic running on a HP Laptop 2 years old.
TB is 78.7.1.

All as per standard install with all offered upgrades to date.

John.

---

### Post by walts48 on 2021-04-20
This might help with the ISP failure to update their certificates issue.

[https://support.mozilla.org/en-US/kb/thunderbird-78-faq#w_after-upgrading-to-thunderbird-78-i-cannot-receive-or-send-email-messages](https://support.mozilla.org/en-US/kb/thunderbird-78-faq#w_after-upgrading-to-thunderbird-78-i-cannot-receive-or-send-email-messages)

More FAQ [https://support.mozilla.org/en-US/kb/thunderbird-78-faq](https://support.mozilla.org/en-US/kb/thunderbird-78-faq)

---

### Post by ajgreeny on 2021-04-20
Run command ```
zgrep -i " upgrade " /var/log/dpkg.log* | grep thunderbird
```which will list all the upgrades of thunderbird carried out in the period for which the dpkg logs still exist; in my case they go back to May 2020, more than enough for your problem, but it will show when the change from 68 to 78 occurred which may help your deliberations.

MKore than that I can't help; thunderbird is still working exactly as it has done for me over very many years (decades?) and the move to TB 78 was no problem for me either.

---

### Post by TheFu on 2021-04-20
Seems you need to **contact the ISP** and have them renew their cert if they haven't already handled it. It isn't an issue on your system or one that you can do anything about.  If some other mail software works, that software probably has a security failure.

I'm running TB v78.7.1  and connecting fine to both my email servers and to gmail without any cert complaints.  My email server cert expires in about 3 more years. Let me check for the exact date:  Fri, 26 Apr 2024 02:41:51 GMT

---

