---
title: "ntpdate delays bootup - bug?"
date: 2005-09-30
forum: General Help
---

### Post by kadissie on 2005-09-30
Does anyone else think the following should be submitted to bugzilla?  I realise it is an upstream issue, but something should be done.

I have experienced on numerous occasions having a boot process hang for two minutes while trying to sync time with ntp.ubuntulinux.com - and if you do a search on the forums for "ntpdate", you will find that there are dozens of queries from people asking how they can avoid this delay.  Sometimes they don't know what it is until someone points it out; all they see is "*ror: Temporary failure in name resolution", which seems to a newbie like a fairly scary thing.

This is unacceptable.  There are thousands of Ubuntu users who do not have reliable, always-on internet connections.  Yes, they can "update-rc.d ntpdate remove" or they can hit Ctrl+C during the delay, but I hope no-one is satisfied that this is the ideal solution....  And the neat solution of adding "-t [timeout]" to the command line options in /etc/default/ntpdate doesn't work, because that is an NTP protocol timeout rather than a DNS timeout, which is the problem here.

The Fedora ntpdate manpage says that ntpdate is being retired in favour of ntpd in that distro, but I note that the former is [still in the Breezy package list]("http://packages.ubuntu.com/breezy/net/ntpdate").

My (naive) suggestion would be to daemon the ntpdate process.

Are there any other annoying startup processes that require an internet connection but are too daft to figure out that one isn't present?

Robert.

---

### Post by mlomker on 2005-09-30
Hey! Stop right there.  You're making way too much sense.  ;)

---

### Post by Zotova on 2005-09-30
Well I don't personally see the need for having a time sync when you boot. Like you say it simply slows things down too much.

If you do turn the feature off you can still have your clock sync within ubuntu periodically - so with that feature in place what is the actual point of a boot-time sync for desktop users?

---

