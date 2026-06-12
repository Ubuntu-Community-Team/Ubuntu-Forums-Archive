---
title: "NR Chain in iptables"
date: 2005-09-22
forum: General Help
---

### Post by gmccreight on 2005-09-22
I use firestarter to setup/modify my iptables.  Recently, after certain people were unable to connect to my webserver, I noticed that in the NR Chain (in the iptables)there were all sorts of IP specific rules which blocked huge swaths of addresses completely.

For example, one of the lines read...

LS         all  --  71.0.0.0/8           adsl-fooip-.dsl.snfc21.pacbell.net/29

I replaced the real IP with fooip, but the part that's interesting is the 71.0.0.0/8, which effectively blocks everyone with an IP address which starts with 71.  This included one of the people who was trying to look at my site.

Anyhow, does anyone have any idea why these rules are part of the iptables set up by firestarter, and whether I need to worry about them being put back in or added to automatically?

I flushed the with NR Chain with the following command, and I'm back in businness:

iptables -F NR

I just want to make sure I stay in business.

Cheers - Gordon

---

### Post by gmccreight on 2005-09-22
[QUOTE=gmccreight]I use firestarter to setup/modify my iptables.  Recently, after certain people were unable to connect to my webserver, I noticed that in the NR Chain (in the iptables)there were all sorts of IP specific rules which blocked huge swaths of addresses completely.

For example, one of the lines read...

LS         all  --  71.0.0.0/8           adsl-fooip-.dsl.snfc21.pacbell.net/29

I replaced the real IP with fooip, but the part that's interesting is the 71.0.0.0/8, which effectively blocks everyone with an IP address which starts with 71.  This included one of the people who was trying to look at my site.

Anyhow, does anyone have any idea why these rules are part of the iptables set up by firestarter, and whether I need to worry about them being put back in or added to automatically?

I flushed the with NR Chain with the following command, and I'm back in businness:

iptables -F NR

I just want to make sure I stay in business.

Cheers - Gordon[/QUOTE]
 Whoops... sorry about posting this to the wrong topic area.  I didn't see networking until just now.

---

### Post by gmccreight on 2005-09-22
I've learned some stuff, and wanted to add it here for the next guy.  NR means non-routables.  There is a file which is part of /etc/firestarter which contains these non-routables.  The ones from version 1.0.1 are no longer actually completely true (if ever they were).  Search wikipedia for "IANA reserved netblocks" for the actual list of non-routables.

Also, firestarter has disabled blocking the non-routables as its default behavior as of version 1.0.2

Anyhow, in my case, IP addresses starting with 71 were getting blocked because they were in firestarters list of non-routables, but SBC is actually using them, and they are not really non-routable.

---

