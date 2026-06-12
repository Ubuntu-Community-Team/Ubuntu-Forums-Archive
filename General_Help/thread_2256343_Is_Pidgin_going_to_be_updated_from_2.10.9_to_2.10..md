---
title: "Is Pidgin going to be updated from 2.10.9 to 2.10.11 in repositories soon?"
date: 2014-12-11
forum: General Help
---

### Post by Rooster2000 on 2014-12-11
Do you have plans to update Pidgin from version 2.10.9 to 2.10.11 in Ubuntu repositories? At the moment it seems that it is impossible to contact MSN from v2.10.9 although it worked for a while when I changed the protocol to WLM by using msn-pecan. According to Pidgin website, some login issue with MSN is fixed in v2.10.11 and there seems to be also some important security updates in v2.10.10. 

> Pidgin 2.10.11 contains login fixes for MSN and some XMPP servers, and Pidgin 2.10.10 contains [important security updates]("http://www.pidgin.im/news/security/"). Please upgrade!

[http://www.pidgin.im/](http://www.pidgin.im/)

I have understood that if some software that is in repositories releases security updates, it ought to be updated in repositories too?

---

### Post by Rooster2000 on 2014-12-15
Does anyone have any information on this one, or am I missing something too obvious?

If there is a workaround to get 2.10.9 to connect MSN network?

At the moment connecting by using MSN -protocol says:

```
(16:19:12) account: Connecting to account <my_account>.
(16:19:12) connection: Connecting. gc = 0xb94eb488
(16:19:12) msn: new httpconn (0xb9818bf8)
(16:19:12) dnsquery: Performing DNS lookup for messenger.hotmail.com
(16:19:12) dns: Successfully sent DNS request to child 1751
(16:19:12) dns: Got response for 'messenger.hotmail.com'
(16:19:12) dnsquery: IP resolved for messenger.hotmail.com
(16:19:12) proxy: Attempting connection to 64.4.45.62
(16:19:12) proxy: Connecting to messenger.hotmail.com:1863 with no proxy
(16:19:12) proxy: Connection in progress
(16:19:12) proxy: Connecting to messenger.hotmail.com:1863.
(16:19:12) proxy: Error connecting to messenger.hotmail.com:1863 (Connection refused).
(16:19:12) proxy: Connection attempt failed: Connection refused
(16:19:12) msn: Connection error: Connection refused
(16:19:12) msn: Connection error from Notification server (messenger.hotmail.com): Connection refused
(16:19:12) connection: Connection error on 0xb94eb488 (reason: 0 description: Connection error from Notification server: Connection refused)
(16:19:12) account: Disconnecting account <my_account> (0xb94e6220)
(16:19:12) connection: Disconnecting connection 0xb94eb488
(16:19:12) msn: destroy the OIM 0xb9836d28
(16:19:12) msn: destroy httpconn (0xb9818bf8)
(16:19:12) connection: Destroying connection 0xb94eb488
```

and for WLM protocol:

```
(16:14:47) account: Connecting to account <my_username>.
(16:14:47) connection: Connecting. gc = 0xb8f0a1d0
(16:14:47) msn-pecan: connection error: (NS):reason=[Unable to connect]
(16:14:47) msn-pecan: closing 'ns'
(16:14:47) msn-pecan: not connected: conn=0xb8ecb418
(16:14:47) connection: Connection error on 0xb8f0a1d0 (reason: 0 description: Error on notification server: Unable to connect)
(16:14:47) msn-pecan: C: 000: ns: VER 1 MSNP12
(16:14:47) g_log: pn_stream_write_full: assertion 'stream' failed
(16:14:47) msn-pecan: not normal: status=0 (ERROR)
(16:14:47) msn-pecan: connection error: (NS)
(16:14:47) g_log: msn_session_disconnect: assertion 'session->connected' failed
(16:14:47) account: Disconnecting account <my_username> (0xb8bb0dd0)
(16:14:47) connection: Disconnecting connection 0xb8f0a1d0
(16:14:47) connection: Destroying connection 0xb8f0a1d0
```

---

### Post by ian-weisser on 2014-12-15
> **Rooster2000 said:**
> Do you have plans to update Pidgin from version 2.10.9 to 2.10.11 in Ubuntu repositories?

Perhaps.
According to [https://tracker.debian.org/pkg/pidgin](https://tracker.debian.org/pkg/pidgin) , Pidgin 2.11 is currently in Debian Testing. However, it has not been imported to Ubuntu yet. Debian Import Freeze isn't until 17 FEB 2015, so seems plenty of time to get it included in Ubuntu 15.04.

Will Pidgin 2.11 be backported to previous releases of Ubuntu? Unlikely. Such backporting has been rare in the past. But PPA developers are always full of surprises, too. Somebody might...but it's not planned.

A *different* question is 'did my connection bug get fixed'. Maybe it got fixed without upgrading to the next version...but the changelogs [http://changelogs.ubuntu.com/changelogs/binary/p/pidgin](http://changelogs.ubuntu.com/changelogs/binary/p/pidgin) does not show a fix.

So keep an eye out for Pidgin 2.11 landing in 15.04 or a PPA.

---

### Post by Rooster2000 on 2014-12-22
For me it sounds bad that Pidgin is not updated in the repositories of older LTS versions if they release some security updates. Isn't that the purpose of installing apps from repositories in the first place that you can trust at some level that you get all the necessary security updates for them?

For that MSN connection issue, looks like Microsoft has shut down that MSN messenger network so it's useless to try to connect it.

---

### Post by mcduck on 2014-12-22
It's more likely that the security fixes would end being patched into the current version rather than updating to latest version.

In general Ubuntu's updates favour stability between tested versions over updates to latest versions, so if it's possible to apply security patches to the version already tested and approved for whatever Ubuntu release you are running, then that's what's going to happen.

Edit:

For example, the Pidgin version in 14.04 right now is *not* 2.10.9, but instead 2.10.9-0ubuntu3.2. The "ubuntu3.2" indicates that there are additional patches applied by Ubuntu's developers and the packages maintainer. Taking a look at the [package's changelog]("http://changelogs.ubuntu.com/changelogs/pool/main/p/pidgin/pidgin_2.10.9-0ubuntu3.2/changelog"), you'll notice that the last security update to that package included patches for the security issues reported on Pidgin's website.

Update from ubuntu3.1 to ubuntu3.2 applied parches for security vulnerabilities  CVE-2014-3694, CVE-2014-3695, CVE-2014-3696 and CVE-2014-3698. Exactly same ones that were fixed in Pidgin 2.10.10. (excluding  CVE-2014-3697, as that's only relevant for Windows version)

Similarly, Ubuntu 12.04 is running even older Pidgin version, 2.10.3-0ubuntu1.6, but the Ubuntu patches are up-to-date with latest Pidgin security patches. The [Ubuntu changelog]("http://changelogs.ubuntu.com/changelogs/pool/main/p/pidgin/pidgin_2.10.3-0ubuntu1.6/changelog") displays the same security updates.

---

### Post by ian-weisser on 2014-12-22
> **Rooster2000 said:**
> For me it sounds bad that Pidgin is not updated in the repositories of older LTS versions if they release some security updates. Isn't that the purpose of installing apps from repositories in the first place that you can trust at some level that you get all the necessary security updates for them?

As McDuck pointed out, *version updates* are different from *security patches*. The Ubuntu Security Team does patch security vulnerabilities in Pidgin, and those patched versions are pushed in the -security repositories.

If you want 'updated' Pidgin, you should be subscribed to the  appropriate PPA, or you should be using the latest regular (non-LTS  release of Ubuntu)...when 2.11 lands, of course.

The purpose of an LTS is to provide five-year group of software that has predictable behavior; that does not change, except for security and important bugfixes. That software-not-changing form of stability is what the 'S' in LTS refers to (not the prevent-crashing kind of stability). Updating software in LTS repositories is *precisely the opposite* of the intent of an LTS release. The original target audience of LTS users is commercial/institutional operations with a defined workflow and low tolerance for change.

---

### Post by mc4man on 2014-12-22
Non security related fixes can get into Ubuntu supported releases thru a SRU but they have to qualify & the process can be a bit of a chore
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)
You may wish to use the pidgin developers ppa - main page,
[https://launchpad.net/~pidgin-developers/+archive/ubuntu/ppa](https://launchpad.net/~pidgin-developers/+archive/ubuntu/ppa)

referring page - 
[https://www.pidgin.im/download/ubuntu/](https://www.pidgin.im/download/ubuntu/)

---

### Post by kevdog on 2014-12-22
To address the original post -- I would say know is the time to actually learn how to compile and install a package from source.  There a guides how to do this and it's not very difficult.  I would turn this into a wonderful learning opportunity.

---

### Post by Rooster2000 on 2014-12-26
Thanks for your thorough responses. As security fixes are patched in repositories for 2.10.9 and it seems that MSN service has been dropped by Microsoft, there is no need for me to update to 2.10.11 anymore. So I'll spare the learning opportunity to build from sources for some other software instead.

In general, I like the ideology behind LTS releases (predictability, stability, aimed for users with low tolerance of change). At this point I just thought for a moment that it is maintained by the expense of security.

---

