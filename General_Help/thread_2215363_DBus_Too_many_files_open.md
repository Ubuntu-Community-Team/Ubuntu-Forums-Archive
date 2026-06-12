---
title: "DBus: Too many files open"
date: 2014-04-06
forum: General Help
---

### Post by anubeon on 2014-04-06
**Greetings,**

I've recently been experiencing an issue with an as yet unidentified programme causing DBus to exceed some predefined file access limit. Once the number of open files exceeds this limit, starting any programme relying on DBus will invariably result in it crashing with the following error message…

> dbus.exceptions.DBusException: org.freedesktop.DBus.Error.LimitsExceeded: Failed to determine seats of user "1000": Too many open files

…making a system reboot necessary, as many programmes seem to rely on DBus these days (Onboard and GEdit being two such programmes). I have no idea how to diagnose this issue, or how to determine which if any package is responsible. Thus I'd appreciate any assistance in diagnosing the above, so that I can at the very least report the bug to the appropriate developers.

[B]Kind Regards,

Lee Hyde.[/B]
[I][SIZE=2][COLOR=#696969]
**P.S.:** If it helps, I've recently installed [/COLOR][[COLOR=#696969]Copy's[/COLOR]]("https://www.copy.com")[COLOR=#696969] sync clients and I have a suspicion that their CopyAgent client may well be the culprit. CopyAgent's appindicator is certainly rather [/COLOR][[COLOR=#696969]bug ridden[/COLOR]]("https://copy.zendesk.com/entries/28050018-Potential-fix-for-Ubuntu-13-10-indicator-icon-")[COLOR=#696969], and the package is distributed as a pre-compiled .tar which suggests to me that their Linux client is something of an after thought.

**P.P.S.**: I'm sure that there's a way to increase the file access limit, but I'd rather diagnose the underlying issue as I suspect raising that limit will only serve as a stop gap fix and whichever bug is causing the above issues will eventually hit that new limit eventually anyway.[/COLOR][/SIZE][/I]

---

### Post by anubeon on 2014-04-12
I'm 99.99% certain now that it's the [Copy]("http://www.copy.com") client that is the culprit here. I'd appreciate any assistance in characterising the bug so that I can properly report it to the Copy developers (although they don't appear to be the most responsive lot when it comes to their Linux client). However, for now, I don't regard this as critical as I've been able to avoid major annoyance by disabling Copy for the time being (I was only trailing it as an alternative to Ubuntu One).

---

