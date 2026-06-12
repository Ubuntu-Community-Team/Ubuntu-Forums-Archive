---
title: "Thunderbird won't start"
date: 2020-10-28
forum: General Help
---

### Post by Onesimus on 2020-10-28
I am on Ubuntu 20.10 having upgraded from 20.04.
And have just done the latest updates this included Kernel 5.8.0-26-generic 

However, on re-starting the machine, thunderbird won't start.  I get the following error message 
```

XML Parsing Error: undefined entity
Location: chrome://messenger/content/messenger.xhtml
Line Number 905, Column 3:
  <key id="openLightningKey"
--^
```

Any ideas ?

---

### Post by Onesimus on 2020-10-28
Further to the above post, if I start Thunderbird from the command line I get

```
[calBackendLoader] Using Thunderbird's libical backend
Extension error: Error while loading 'jar:file:///usr/lib/thunderbird/extensions/messagingmenu@mozilla.com.xpi!/manifest.json' (NS_ERROR_FILE_NOT_FOUND) resource://gre/modules/Extension.jsm:570 :: readJSON/</<@resource://gre/modules/Extension.jsm:570:20
onStopRequest@resource://gre/modules/NetUtil.jsm:128:18

Extension error: Error while loading 'jar:file:///usr/lib/thunderbird/omni.ja!/chrome/messenger/search-extensions/twitter/manifest.json' (NS_ERROR_FILE_NOT_FOUND) resource://gre/modules/Extension.jsm:570 :: readJSON/</<@resource://gre/modules/Extension.jsm:570:20
onStopRequest@resource://gre/modules/NetUtil.jsm:128:18

Extension error: statusPrivacy is null resource://gdata-provider/legacy/modules/ui/gdata-event-dialog.jsm:56 :: gdataInitUI/<@resource://gdata-provider/legacy/modules/ui/gdata-event-dialog.jsm:56:5
gdataInitUI@resource://gdata-provider/legacy/modules/ui/gdata-event-dialog.jsm:60:5
onLoadWindow@resource://gdata-provider/legacy/modules/gdataUI.jsm:30:18
checkAndRunExtensionCode@resource:///modules/ExtensionSupport.jsm:220:28
_checkAndRunMatchingExtensions@resource:///modules/ExtensionSupport.jsm:192:31
registerWindowListener/<@resource:///modules/ExtensionSupport.jsm:71:26
registerWindowListener@resource:///modules/ExtensionSupport.jsm:70:22
registerWindowListener@resource://gdata-provider/legacy/modules/gdataUI.jsm:24:20
register@resource://gdata-provider/legacy/modules/gdataUI.jsm:49:25
onStartup@jar:file:///home/drjoe/.thunderbird/u9r2t7tj.default/extensions/%7Ba62ef8ec-5fdc-40c2-873c-223b8a6925cc%7D.xpi!/api/gdata.js:48:13
onStartup/<@resource://gre/modules/ExtensionCommon.jsm:1406:17

JavaScript error: resource://gre/modules/ExtensionParent.jsm, line 1533: Error: Message manager was disconnected before receiving Extension:ExtensionViewLoaded
```

---

### Post by walts48 on 2020-10-29
> **Onesimus said:**
> I am on Ubuntu 20.10 having upgraded from 20.04.
And have just done the latest updates this included Kernel 5.8.0-26-generic 

However, on re-starting the machine, thunderbird won't start.  I get the following error message 
```

XML Parsing Error: undefined entity
Location: chrome://messenger/content/messenger.xhtml
Line Number 905, Column 3:
  <key id="openLightningKey"
--^
```

Any ideas ?

There is a Thunderbird bug report about that with version 68.0 with language packs installed.

[URL="https://bugzilla.mozilla.org/show_bug.cgi?id=1655225"]https://bugzilla.mozilla.org/show_bug.cgi?id=1655225
[/URL]
Do you have any language packs installed?

I'll try a Live 20.10 later and see what happens. However it probably won't have that updated kernel. :-k

---

### Post by Onesimus on 2020-10-29
Hi Walts48

I have the current language packs installed:
   thunderbird-locale-en
   thunderbird-locale-en-us
   thunderbird-locale-en-gb

I can start thunderbird in safe-mode from the command line.  But that certainly isn't ideal.

---

### Post by raif on 2020-11-02
Same bug, same upgrade path and same workaround.

Have tried removing all language packs other than en-gb (previously had de, fr & es) then reinstalling Thunderbird but the problem persists. I'm wondering if it has anything to do with the changes to calendar support in v78, as the old Lightning extensions no longer work.

Yes it's annoying and I hope someone can suggest a fix soon!

---

### Post by walts48 on 2020-11-02
> **raif said:**
> Same bug, same upgrade path and same workaround.

Have tried removing all language packs other than en-gb (previously had de, fr & es) then reinstalling Thunderbird but the problem persists. I'm wondering if it has anything to do with the changes to calendar support in v78, as the old Lightning extensions no longer work.

Yes it's annoying and I hope someone can suggest a fix soon!

Have you removed all the old no longer functioning extensions?

---

### Post by Onesimus on 2020-11-03
I have 'solved' my issue by re-installing Ubuntu 20.04.
If the issue hadn't occurred on a key application (ie. Thunderbird, though could have been FireFox, LibreOffice), I would have found (or waited) for a solution.
As it was, it took about 1hr to re-install 20.04

The only snag is that Thunderbird won't download the missing emails (they're still on the Gmail server), and Thunderbird in 20.04 won't accept a profile from a later version

---

### Post by walts48 on 2020-11-03
> **Onesimus said:**
> I have 'solved' my issue by re-installing Ubuntu 20.04.
If the issue hadn't occurred on a key application (ie. Thunderbird, though could have been FireFox, LibreOffice), I would have found (or waited) for a solution.
As it was, it took about 1hr to re-install 20.04

The only snag is that Thunderbird won't download the missing emails (they're still on the Gmail server), and Thunderbird in 20.04 won't accept a profile from a later version

See [Dedicated profile per Thunderbird installation | Thunderbird Help]("https://support.mozilla.org/en-US/kb/dedicated-profile-thunderbird-installation").

The bug report I mentioned in another post has also been resolved.

---

### Post by raif on 2020-11-11
Yes, have removed all extensions, reinstalled Thunderbird but the problem remains.

Is anyone else still having this issue or have suggestions how to fix (other than downgrading to 20.04)?
many thanks

---

### Post by ajgreeny on 2020-11-11
My suspicion is a conflict between the calendar config files in Tbird 68 and the now incorporated calendar in Tbird 78.
I am running  Xubuntu 20.10 as a VM in kvm and have created a new configuration and profile for it which is working well.

The problem I do have is getting all the various calendars from the old lightning to the new version, though so far I have not spent much time on it.

---

### Post by walts48 on 2020-11-11
> **ajgreeny said:**
> My suspicion is a conflict between the calendar config files in Tbird 68 and the now incorporated calendar in Tbird 78.
I am running  Xubuntu 20.10 as a VM in kvm and have created a new configuration and profile for it which is working well.

The problem I do have is getting all the various calendars from the old lightning to the new version, though so far I have not spent much time on it.

See [https://bugzilla.mozilla.org/show_bug.cgi?id=1655225#c12](https://bugzilla.mozilla.org/show_bug.cgi?id=1655225#c12)

Just how would you get the various calendars?

Did you select the Calendar tab and use Events and Tasks > Export to back each calendar up in the old version of Thunderbird? All you would have to do then is created the calendar in Thunderbird and use Event and Tasks > Import for each calendar.

Data for any network calendar should be there when you add the network calendar.

---

### Post by walts48 on 2020-11-11
> **raif said:**
> Yes, have removed all extensions, reinstalled Thunderbird but the problem remains.

Is anyone else still having this issue or have suggestions how to fix (other than downgrading to 20.04)?
many thanks

Installing version 78.4.x from Thunderbird was what fixed the issue for this bug report. [https://bugzilla.mozilla.org/show_bug.cgi?id=1655225](https://bugzilla.mozilla.org/show_bug.cgi?id=1655225).

My Thunderbird just updated to 78.4.3 this morning.

[Download Thunderbird in your language — Thunderbird]("https://www.thunderbird.net/en-US/thunderbird/all/")

---

### Post by raif on 2020-11-11
That conflict was what I was thinking too.

Have deleted calendar-data in my Thunderbird profile folder (and a few other files that looked related to extensions no longer supported in T78), then reinstalled. Thunderbird now seems to start fine.

---

