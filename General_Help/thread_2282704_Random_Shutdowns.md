---
title: "Random Shutdowns"
date: 2015-06-16
forum: General Help
---

### Post by welefort on 2015-06-16
Recently upgraded to 15.05  and now Im experiencing random shutdowns.   I've checked the hardware sensors and the temperature's all seem to be within range.  After bootup the system stays running,  which I would not expect with overheating issues.   The logs dont seem to point to any issue,  but I could be wrong there.    I was hoping someone could take a look and let me know if they see anything.

The following logs show the shutdown time  Approx 7:25 am,  with bootup at approx 7:27am.  I copied the events for a few seconds before and after.

Syslog

```
un 16 07:25:05 *** kernel: [  211.960408] Valid eCryptfs headers not found in file header region or xattr region, inode 7741023
Jun 16 07:25:06 *** gnome-session[1618]: WARNING: content window passed to PrivateBrowsingUtils.isWindowPrivate. Use isContentWindowPrivate instead (but only for frame scripts).
Jun 16 07:25:06 *** gnome-session[1618]: pbu_isWindowPrivate@resource://gre/modules/PrivateBrowsingUtils.jsm:25:14
Jun 16 07:25:06 *** gnome-session[1618]: pbs<@resource://unity/observer.js:38:71
Jun 16 07:25:06 *** gnome-session[1618]: Observer.prototype.observe@resource://unity/observer.js:77:24
Jun 16 07:25:07 *** gnome-session[1618]: WARNING: content window passed to PrivateBrowsingUtils.isWindowPrivate. Use isContentWindowPrivate instead (but only for frame scripts).
Jun 16 07:25:07 *** gnome-session[1618]: pbu_isWindowPrivate@resource://gre/modules/PrivateBrowsingUtils.jsm:25:14
Jun 16 07:25:07 *** gnome-session[1618]: pbs<@resource://unity/observer.js:38:71
Jun 16 07:25:07 *** gnome-session[1618]: Observer.prototype.observe@resource://unity/observer.js:77:24
Jun 16 07:25:13 *** gnome-session[1618]: WARNING: content window passed to PrivateBrowsingUtils.isWindowPrivate. Use isContentWindowPrivate instead (but only for frame scripts).
Jun 16 07:25:13 *** gnome-session[1618]: pbu_isWindowPrivate@resource://gre/modules/PrivateBrowsingUtils.jsm:25:14
Jun 16 07:25:13 *** gnome-session[1618]: pbs<@resource://unity/observer.js:38:71
Jun 16 07:25:13 *** gnome-session[1618]: Observer.prototype.observe@resource://unity/observer.js:77:24
Jun 16 07:25:18 *** gnome-session[1618]: WARNING: content window passed to PrivateBrowsingUtils.isWindowPrivate. Use isContentWindowPrivate instead (but only for frame scripts).
Jun 16 07:25:18 *** gnome-session[1618]: pbu_isWindowPrivate@resource://gre/modules/PrivateBrowsingUtils.jsm:25:14
Jun 16 07:25:18 *** gnome-session[1618]: pbs<@resource://unity/observer.js:38:71
Jun 16 07:25:18 *** gnome-session[1618]: Observer.prototype.observe@resource://unity/observer.js:77:24
Jun 16 07:27:36 *** anacron[871]: Job `cron.daily' started
Jun 16 07:27:36 *** anacron[2167]: Updated timestamp for job `cron.daily' to 2015-06-16
Jun 16 07:28:16 *** gnome-session[1618]: 1434454096813#011addons.update-checker#011WARN#011Update manifest for {2e1445b0-2682-11e1-bfc2-0800200c9a66} did not contain an updates property
Jun 16 07:28:16 *** gnome-session[1618]: 1434454096903#011addons.update-checker#011WARN#011Update manifest for ubufox@ubuntu.com did not contain an updates property
Jun 16 07:28:17 *** gnome-session[1618]: 1434454097283#011addons.update-checker#011WARN#011Update manifest for webapps-team@lists.launchpad.net did not contain an updates property
Jun 16 07:28:17 *** gnome-session[1618]: 1434454097294#011addons.update-checker#011WARN#011Update manifest for online-accounts@lists.launchpad.net did not contain an updates property
Jun 16 07:28:17 *** gnome-session[1618]: 1434454097301#011addons.update-checker#011WARN#011Update manifest for {972ce4c6-7e08-4474-a285-3208198ce6fd} did not contain an updates property
Jun 16 07:29:25 *** kernel: [  471.252562] Valid eCryptfs headers not found in file header region or xattr region, inode 6557225
Jun 16 07:29:25 *** gnome-session[1618]: console.error: reddit_res:
Jun 16 07:29:25 *** gnome-session[1618]: Message: [Exception... "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsIFileOutputStream.init]"  nsresult: "0x80004005 (NS_ERROR_FAILURE)"  location: "JS frame :: resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/io/file.js :: open :: line 147"  data: no]
Jun 16 07:29:25 *** gnome-session[1618]: Stack:
Jun 16 07:29:25 *** gnome-session[1618]: open@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/io/file.js:147:6
Jun 16 07:29:25 *** gnome-session[1618]: JsonStore__write@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/simple-storage.js:163:17
Jun 16 07:29:25 *** gnome-session[1618]: JsonStore_write@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/simple-storage.js:120:6
Jun 16 07:29:25 *** gnome-session[1618]: notify@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/timers.js:40:8


```

kernlog
```
Jun 16 07:22:37 *** kernel: [   64.873338] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 16 07:22:37 *** kernel: [   64.873340] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 16 07:22:37 *** kernel: [   64.873342] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 16 07:22:38 *** kernel: [   65.499181] r8169 0000:02:00.0 eth0: link down
Jun 16 07:22:38 *** kernel: [   65.499258] r8169 0000:02:00.0 eth0: link down
Jun 16 07:22:39 *** kernel: [   67.094245] r8169 0000:02:00.0 eth0: link up
Jun 16 07:23:46 *** gnome-session[1618]: Entering running state
Jun 16 07:24:25 *** kernel: [  171.653726] Valid eCryptfs headers not found in file header region or xattr region, inode 6557225
Jun 16 07:25:04 *** kernel: [  211.528192] Valid eCryptfs headers not found in file header region or xattr region, inode 7741022
Jun 16 07:25:05 *** kernel: [  211.960408] Valid eCryptfs headers not found in file header region or xattr region, inode 7741023
Jun 16 07:29:25 *** kernel: [  471.252562] Valid eCryptfs headers not found in file header region or xattr region, inode 6557225


```

---

### Post by raja.genupula on 2015-06-16
Hello ,

We really cant blame **eCryptfs headers **for your random shutdown . But that is the only event we can see from the logs you have provided. so this log my not be enough to troubleshoot issue perfectly, we need atleast 5 min log. keep the events to low so we can less events to analysis while looking at the log.

And lets start from above inode errors fixing. 

In terminal type as 

> [COLOR=#333333][FONT=verdana]find ~/ -inum [/FONT][/COLOR] <Inode>

for example 

> [COLOR=#333333][FONT=verdana]find ~/ -inum [/FONT][/COLOR] 6557225

and it will list corresponding file for that inode and then try to access that file , if file exists fine else remove that file with rm <filename> command.

And do same for all other inodes too and then see any progress.

---

