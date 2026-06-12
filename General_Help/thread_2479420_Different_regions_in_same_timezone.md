---
title: "Different regions in same timezone"
date: 2022-09-23
forum: General Help
---

### Post by gravik2 on 2022-09-23
Whole Ukraine territory located in one timezone.
I have 4 regions for Ukraine in Ubuntu.
If I choose Kyiv then Discord application shows incorrect timestamps in chat.
If I choose Zaporozhye and Uzhgorod it shows correct timestamps in chat.
System time is correct using any region.
Also there is no difference if I set RTC to local time or universal time, both cases Kyiv region is problematic for Discord.

Is it Ubuntu or Discord issue?

Ubuntu 22.4 
KDE Plasma 5.24.6

---

### Post by QIII on 2022-09-24
Are you speaking of discord.com?

---

### Post by gravik2 on 2022-09-24
Yes.

---

### Post by TheFu on 2022-09-24
There are bugs in javascript date() processing with some timezones.  Often, the original site will need to code special handling for the specific issue on a per-browser basis.

I've reported a similar issue with TZ in TV schedule data.  Was able to trace it back to a specific browser and specific javascript used.  Other browsers had the problem too. Other machines had the problem.  I also see it in different webapp libraries - DotNet programs and C++ programs.

BTW, if the TZ is showing UTC always, that is usually caused by specific browser privacy settings.  Some programs use a wrapper around a browser to hide they are just a webapp.  I think this is common for all "electron apps'.  I understand that discord is an electron app.

---

### Post by gravik2 on 2022-09-24
I'm talking about app not site, idk if it's same for browser version of discord.

---

### Post by TheFu on 2022-09-24
> **gravik2 said:**
> I'm talking about app not site, idk if it's same for browser version of discord.

The discord app is an Electron app, which is basically a version of Chromium browser that contacts the webapp for display.  Javascript is the likely issue, if you don't have a better explanation.

[https://support.discord.com/hc/en-us/community/posts/360056415072-Wrong-time-SOLVED-](https://support.discord.com/hc/en-us/community/posts/360056415072-Wrong-time-SOLVED-) shows that some people are helped and others are not.

---

### Post by gravik2 on 2022-09-24
> **TheFu said:**
> The discord app is an Electron app, which is basically a version of Chromium browser that contacts the webapp for display.
Interesting, did not know that, thx.

> **TheFu said:**
> [https://support.discord.com/hc/en-us/community/posts/360056415072-Wrong-time-SOLVED-](https://support.discord.com/hc/en-us/community/posts/360056415072-Wrong-time-SOLVED-) shows that some people are helped and others are not.

Yeah, I saw this thread yesterday.

Well I guess I'll report to Discord then.

Ty everyone.

---

