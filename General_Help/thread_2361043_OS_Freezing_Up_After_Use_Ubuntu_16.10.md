---
title: "OS Freezing Up After Use Ubuntu 16.10"
date: 2017-05-11
forum: General Help
---

### Post by abdusamed on 2017-05-11
[COLOR=#000000]I think really think Nvidia additional hardware is to be blamed but I was getting the same issue on Open Source Driver for Nvidia GTX 960. The logs here are pasted and don't know what more to share.[/COLOR]

[COLOR=#000000]Just want to put it into the open web incase someone feels like figuring out what might be going on. It no longer is happening but when it did, it was very frustrating to use Ubuntu[/COLOR]

**Problem:**


After the time stamp [big time different], my entire Ubuntu distribution would freeze and could be kernel panic. Nothing worked. Only solution to get out of it was ALT+PRTSCRN+ R.E.I.S.U.B

Logs of 'auth.log' and 'syslong' are attached below:

```
Apr 29 18:24:06 Desky-Ubuntu gcr-prompter[23259]: Gcr: stopping prompting for operation /org/gnome/keyring/Prompt/p3@:1.88Apr 29 18:24:06 Desky-Ubuntu gcr-prompter[23259]: Gcr: couldn't find the callback for prompting operation /org/gnome/keyring/Prompt/p3@:1.88[/FONT][/COLOR][COLOR=#000000]Apr 29 18:24:06 Desky-Ubuntu gcr-prompter[23259]: Gcr: stopping prompting for operation /org/gnome/keyring/Prompt/p3@:1.88
Apr 29 18:24:06 Desky-Ubuntu gcr-prompter[23259]: Gcr: couldn't find the callback for prompting operation /org/gnome/keyring/Prompt/p3@:1.88
Apr 29 18:24:06 Desky-Ubuntu gcr-prompter[23259]: Gcr: stopping prompting for operation /org/gnome/keyring/Prompt/p3@:1.88
Apr 29 18:24:06 Desky-Ubuntu gcr-prompter[23259]: Gcr: couldn't find the callback for prompting operation /org/gnome/keyring/Prompt/p3@:1.88
Apr 29 18:24:06 Desky-Ubuntu gcr-prompter[23259]: Gcr: calling the PromptDone method on /org/gnome/keyring/Prompt/p3@:1.88, and ignoring reply
Apr 29 18:24:06 Desky-Ubuntu gcr-prompter[23259]: Gcr: returned from the PromptReady method on /org/gnome/keyring/Prompt/p3@:1.88
Apr 29 18:24:06 Desky-Ubuntu gcr-prompter[23259]: Gcr: received PerformPrompt call from callback /org/gnome/keyring/Prompt/p3@:1.88
Apr 29 18:24:06 Desky-Ubuntu gcr-prompter[23259]: Gcr: stopping prompting for operation /org/gnome/keyring/Prompt/p3@:1.88
Apr 29 18:24:06 Desky-Ubuntu gcr-prompter[23259]: Gcr: couldn't find the callback for prompting operation /org/gnome/keyring/Prompt/p3@:1.88
Apr 29 18:24:16 Desky-Ubuntu gcr-prompter[23259]: 10 second inactivity timeout, quitting
Apr 29 18:24:16 Desky-Ubuntu gcr-prompter[23259]: Gcr: unregistering prompter
Apr 29 18:24:16 Desky-Ubuntu gcr-prompter[23259]: Gcr: disposing prompter
Apr 29 18:24:16 Desky-Ubuntu gcr-prompter[23259]: Gcr: finalizing prompter
Apr 29 18:24:24 Desky-Ubuntu gcr-prompter[23494]: bus acquired: org.gnome.keyring.SystemPrompter
Apr 29 18:24:24 Desky-Ubuntu gcr-prompter[23494]: Gcr: registering prompter
Apr 29 18:24:24 Desky-Ubuntu gcr-prompter[23494]: bus acquired: org.gnome.keyring.PrivatePrompter
Apr 29 18:24:24 Desky-Ubuntu gcr-prompter[23494]: Gcr: received BeginPrompting call from callback /org/gnome/keyring/Prompt/p5@:1.88
Apr 29 18:24:24 Desky-Ubuntu gcr-prompter[23494]: Gcr: preparing a prompt for callback /org/gnome/keyring/Prompt/p5@:1.88
Apr 29 18:24:24 Desky-Ubuntu gcr-prompter[23494]: Gcr: creating new GcrPromptDialog prompt
Apr 29 18:24:24 Desky-Ubuntu gcr-prompter[23494]: Gcr: automatically selecting secret exchange protocol
Apr 29 18:24:24 Desky-Ubuntu gcr-prompter[23494]: Gcr: generating public key
Apr 29 18:24:24 Desky-Ubuntu gcr-prompter[23494]: Gcr: beginning the secret exchange: [sx-aes-1]\npublic=cGRg41HIgPlCgH5vOvOsplcRTTVVY3BdhTaqenQQcMQHVYpR6+G1e2rTc7M08KMwI86iBLp20PJXdvJiPfS9IQhvfBUDt6Y9mSAx+triNc7rSK4uM5q8WO1++41ddjkuhwqq927P4DWMRf47+bCWH5P8aspX4eiR8XljUBj+t4mK0aFYMIB10z0W/BitSXzkOwW6f8AWeGqJt8ttUFTukYepq1ol7xnqD6l04TEcL/oKWFyFGTUXxfrcoRPT+Eow\n
Apr 29 18:24:24 Desky-Ubuntu gcr-prompter[23494]: Gcr: calling the PromptReady method on /org/gnome/keyring/Prompt/p5@:1.88
Apr 29 18:24:24 Desky-Ubuntu gcr-prompter[23494]: acquired name: org.gnome.keyring.SystemPrompter
Apr 29 18:24:24 Desky-Ubuntu gcr-prompter[23494]: acquired name: org.gnome.keyring.PrivatePrompter
Apr 29 18:24:24 Desky-Ubuntu gcr-prompter[23494]: Gcr: returned from the PromptReady method on /org/gnome/keyring/Prompt/p5@:1.88
Apr 29 18:24:24 Desky-Ubuntu gcr-prompter[23494]: Gcr: received PerformPrompt call from callback /org/gnome/keyring/Prompt/p5@:1.88
Apr 29 18:24:24 Desky-Ubuntu gcr-prompter[23494]: Gcr: receiving secret exchange: [sx-aes-1]\npublic=1FiLwd8oGU20oBsTIMBXWiZnjIB6nVdvNcvXlQk43ZOZlUBLn/3RuIUFmNHah0IMrd9Ekctaf3xtVFx6MC0kLxGQ/F6bWr/fCltuqZ7grUjwXqXet8INEWcde103474oZglMv4f+lh8LHYfPchxw2/GKp1bB4o0Ec6M1RAbvYG4gYHWFydQuUg74B1PuZp6hQsNt6dBuM+aNVao1v7Zjv5cVJkp+9laHYJh6navz4HqheApipa5DJ7XYzuvOEBy3\n
Apr 29 18:24:24 Desky-Ubuntu gcr-prompter[23494]: Gcr: deriving shared transport key
Apr 29 18:24:24 Desky-Ubuntu gcr-prompter[23494]: Gcr: deriving transport key
Apr 29 18:24:24 Desky-Ubuntu gcr-prompter[23494]: Gcr: starting password prompt for callback /org/gnome/keyring/Prompt/p5@:1.88
Apr 29 18:24:24 Desky-Ubuntu gcr-prompter[23494]: Gtk: GtkDialog mapped without a transient parent. This is discouraged.
Apr 29 18:24:27 Desky-Ubuntu gcr-prompter[23494]: Gcr: completed password prompt for callback :1.88@/org/gnome/keyring/Prompt/p5
Apr 29 18:24:27 Desky-Ubuntu gcr-prompter[23494]: Gcr: encrypting data
Apr 29 18:24:27 Desky-Ubuntu gcr-prompter[23494]: Gcr: sending the secret exchange: [sx-aes-1]\npublic=cGRg41HIgPlCgH5vOvOsplcRTTVVY3BdhTaqenQQcMQHVYpR6+G1e2rTc7M08KMwI86iBLp20PJXdvJiPfS9IQhvfBUDt6Y9mSAx+triNc7rSK4uM5q8WO1++41ddjkuhwqq927P4DWMRf47+bCWH5P8aspX4eiR8XljUBj+t4mK0aFYMIB10z0W/BitSXzkOwW6f8AWeGqJt8ttUFTukYepq1ol7xnqD6l04TEcL/oKWFyFGTUXxfrcoRPT+Eow\nsecret=nsLVrbO39UHPatOKrnhDEQ==\niv=MGAJL8paYxLrKQgOCbzQEQ==\n
Apr 29 18:24:27 Desky-Ubuntu gcr-prompter[23494]: Gcr: calling the PromptReady method on /org/gnome/keyring/Prompt/p5@:1.88
Apr 29 18:24:27 Desky-Ubuntu gcr-prompter[23494]: Gcr: returned from the PromptReady method on /org/gnome/keyring/Prompt/p5@:1.88
Apr 29 18:24:27 Desky-Ubuntu gnome-keyring-daemon[2148]: couldn't allocate secure memory to keep passwords and or keys from being written to the disk
Apr 29 18:24:27 Desky-Ubuntu gcr-prompter[23494]: Gcr: received PerformPrompt call from callback /org/gnome/keyring/Prompt/p5@:1.88
Apr 29 18:24:27 Desky-Ubuntu gcr-prompter[23494]: Gcr: stopping prompting for operation /org/gnome/keyring/Prompt/p5@:1.88
Apr 29 18:24:27 Desky-Ubuntu gcr-prompter[23494]: Gcr: closing the prompt
Apr 29 18:24:27 Desky-Ubuntu gcr-prompter[23494]: Gcr: stopping prompting for operation /org/gnome/keyring/Prompt/p5@:1.88
Apr 29 18:24:27 Desky-Ubuntu gcr-prompter[23494]: Gcr: couldn't find the callback for prompting operation /org/gnome/keyring/Prompt/p5@:1.88
Apr 29 18:24:27 Desky-Ubuntu gcr-prompter[23494]: Gcr: stopping prompting for operation /org/gnome/keyring/Prompt/p5@:1.88
Apr 29 18:24:27 Desky-Ubuntu gcr-prompter[23494]: Gcr: couldn't find the callback for prompting operation /org/gnome/keyring/Prompt/p5@:1.88
Apr 29 18:24:27 Desky-Ubuntu gcr-prompter[23494]: Gcr: stopping prompting for operation /org/gnome/keyring/Prompt/p5@:1.88
Apr 29 18:24:27 Desky-Ubuntu gcr-prompter[23494]: Gcr: couldn't find the callback for prompting operation /org/gnome/keyring/Prompt/p5@:1.88
Apr 29 18:24:27 Desky-Ubuntu gcr-prompter[23494]: Gcr: calling the PromptDone method on /org/gnome/keyring/Prompt/p5@:1.88, and ignoring reply
Apr 29 18:24:37 Desky-Ubuntu gcr-prompter[23494]: 10 second inactivity timeout, quitting
Apr 29 18:24:37 Desky-Ubuntu gcr-prompter[23494]: Gcr: unregistering prompter
Apr 29 18:24:37 Desky-Ubuntu gcr-prompter[23494]: Gcr: disposing prompter
Apr 29 18:24:37 Desky-Ubuntu gcr-prompter[23494]: Gcr: finalizing prompter
Apr 29 19:17:01 Desky-Ubuntu CRON[4935]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 29 19:17:01 Desky-Ubuntu CRON[4935]: pam_unix(cron:session): session closed for user root
Apr 29 19:29:32 Desky-Ubuntu unix_chkpwd[8011]: password check failed for user (biggycomputer)
Apr 29 19:29:32 Desky-Ubuntu compiz: pam_unix(unity:auth): authentication failure; logname= uid=1000 euid=1000 tty= ruser= rhost=  user=biggycomputer
Apr 29 19:29:36 Desky-Ubuntu unix_chkpwd[8026]: password check failed for user (biggycomputer)
Apr 29 19:29:36 Desky-Ubuntu compiz: pam_unix(unity:auth): authentication failure; logname= uid=1000 euid=1000 tty= ruser= rhost=  user=biggycomputer
Apr 29 19:29:39 Desky-Ubuntu compiz: gkr-pam: unlocked login keyring
Apr 29 19:31:05 Desky-Ubuntu gnome-keyring-daemon[2148]: asked to register item /org/freedesktop/secrets/collection/login/29, but it's already registered
Apr 29 19:31:06 Desky-Ubuntu gnome-keyring-daemon[2148]: asked to register item /org/freedesktop/secrets/collection/login/29, but it's already registered
Apr 30 00:02:44 Desky-Ubuntu systemd-logind[1005]: New seat seat0.
Apr 30 00:02:44 Desky-Ubuntu systemd-logind[1005]: Watching system buttons on /dev/input/event2 (Power Button)
Apr 30 00:02:44 Desky-Ubuntu systemd-logind[1005]: Watching system buttons on /dev/input/event1 (Power Button)
Apr 30 00:02:44 Desky-Ubuntu systemd-logind[1005]: Watching system buttons on /dev/input/event0 (Sleep Button)/Prompt/p&#65533;ing/Prompt/p
```

**syslog**

Code:
```
 Apr 29 19:43:45 Desky-Ubuntu compiz[1994]:   Stack:Apr 29 19:43:45 Desky-Ubuntu compiz[1994]:     [email]dispatch@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/method/core.js:116:24
Apr 29 19:43:45 Desky-Ubuntu compiz[1994]: foldp/output<@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/event/utils.js:212:32
Apr 29 19:43:45 Desky-Ubuntu compiz[1994]: map/<@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/event/utils.js:61:65
Apr 29 19:43:45 Desky-Ubuntu compiz[1994]: transform/<@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/event/utils.js:44:29
Apr 29 19:43:45 Desky-Ubuntu compiz[1994]: [email]emitOnObject@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/event/core.js:112:9
Apr 29 19:43:45 Desky-Ubuntu compiz[1994]: [email]emit@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/event/core.js:89:38
Apr 29 19:43:45 Desky-Ubuntu compiz[1994]: [email]receive@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/event/utils.js:115:5
Apr 29 19:43:45 Desky-Ubuntu compiz[1994]: merges/</<@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/event/utils.js:194:31
Apr 29 19:43:45 Desky-Ubuntu compiz[1994]: [email]emitOnObject@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/event/core.js:112:9
Apr 29 19:43:45 Desky-Ubuntu compiz[1994]: [email]emit@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/event/core.js:89:38
Apr 29 19:43:45 Desky-Ubuntu compiz[1994]: [email]receive@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/event/utils.js:115:5
Apr 29 19:43:45 Desky-Ubuntu compiz[1994]: lift/</<@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/event/utils.js:169:7
Apr 29 19:43:45 Desky-Ubuntu compiz[1994]: [email]emitOnObject@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/event/core.js:112:9
Apr 29 19:43:45 Desky-Ubuntu compiz[1994]: [email]emit@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/event/core.js:89:38
Apr 29 19:43:45 Desky-Ubuntu compiz[1994]: [email]receive@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/event/utils.js:115:5
Apr 29 19:43:45 Desky-Ubuntu compiz[1994]: [email]next@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/event/utils.js:37:24
Apr 29 19:43:45 Desky-Ubuntu compiz[1994]: filter/<@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/event/utils.js:54:7
Apr 29 19:43:45 Desky-Ubuntu compiz[1994]: transform/<@resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/event/utils.js:44:29
Apr 29 19:43:45 Desky-Ubuntu compiz[1994]: [email]emitOnObject@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/event/core.js:112:9
Apr 29 19:43:45 Desky-Ubuntu compiz[1994]: [email]emit@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/event/core.js:89:38
Apr 29 19:43:45 Desky-Ubuntu compiz[1994]: [email]receive@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/event/utils.js:115:5
Apr 29 19:43:45 Desky-Ubuntu compiz[1994]: [email]InputPort.prototype.observe@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/input/system.js:104:5
Apr 29 19:43:47 Desky-Ubuntu unity-panel-ser[2008]: Already have a menu for window ID 83899495 with path /com/canonical/menu/5003467 from :1.151, unregistering that one
Apr 29 19:43:52 Desky-Ubuntu unity-panel-ser[2008]: Already have a menu for window ID 83899495 with path /com/canonical/menu/5003467 from :1.151, unregistering that one
Apr 29 19:43:54 Desky-Ubuntu compiz[1994]: GOT STATUS: 404
Apr 29 19:43:54 Desky-Ubuntu compiz[1994]: Got invalid status (404) from server, ignoring response.
Apr 29 19:47:31 Desky-Ubuntu compiz[1994]: console.error: reddit-enhancement-suite:
Apr 29 19:47:31 Desky-Ubuntu compiz[1994]:   Message: Error: Worker not found for tab with id: -3-16, url: [https://www.reddit.com/r/bostonhousing/comments/67ryjd/one_bedroom_in_back_bay_1000_w_utilities/](https://www.reddit.com/r/bostonhousing/comments/67ryjd/one_bedroom_in_back_bay_1000_w_utilities/)
Apr 29 19:47:31 Desky-Ubuntu compiz[1994]:   Stack:
Apr 29 19:47:31 Desky-Ubuntu compiz[1994]:     [email]workerFor@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://jid1-xufzosoflzsoxg-at-jetpack/background.entry.js:166:10
Apr 29 19:47:31 Desky-Ubuntu compiz[1994]: @resource://gre/modules/commonjs/toolkit/loader.js -> resource://jid1-xufzosoflzsoxg-at-jetpack/background.entry.js:395:107
Apr 29 19:47:31 Desky-Ubuntu compiz[1994]: [email]emitOnObject@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/event/core.js:112:9
Apr 29 19:47:31 Desky-Ubuntu compiz[1994]: [email]emit@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/event/core.js:89:38
Apr 29 19:47:31 Desky-Ubuntu compiz[1994]: [email]emitOnObject@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/event/core.js:112:9
Apr 29 19:47:31 Desky-Ubuntu compiz[1994]: [email]emit@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/event/core.js:89:38
Apr 29 19:47:31 Desky-Ubuntu compiz[1994]: [email]emitOnObject@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/event/core.js:123:45
Apr 29 19:47:31 Desky-Ubuntu compiz[1994]: [email]emit@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/event/core.js:89:38
Apr 29 19:47:31 Desky-Ubuntu compiz[1994]: [email]tabEmit@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/tabs/tab-firefox.js:263:31
Apr 29 19:47:31 Desky-Ubuntu compiz[1994]: [email]tabEventListener@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/tabs/tab-firefox.js:328:23
Apr 29 19:47:31 Desky-Ubuntu compiz[1994]: @resource://gre/modules/commonjs/toolkit/loader.js -> resource://gre/modules/commonjs/sdk/tabs/tab-firefox.js:347:39
Apr 29 19:47:31 Desky-Ubuntu compiz[1994]: [email]emitOnObject@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/event/core.js:112:9
Apr 29 19:47:31 Desky-Ubuntu compiz[1994]: [email]emit@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/event/core.js:89:38
Apr 29 19:47:31 Desky-Ubuntu compiz[1994]: [email]emitOnObject@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/event/core.js:112:9
Apr 29 19:47:31 Desky-Ubuntu compiz[1994]: [email]emit@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/event/core.js:89:38
Apr 29 19:47:31 Desky-Ubuntu compiz[1994]: [email]emitOnObject@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/event/core.js:123:45
Apr 29 19:47:31 Desky-Ubuntu compiz[1994]: [email]emit@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/event/core.js:89:38
Apr 29 19:47:31 Desky-Ubuntu compiz[1994]: [email]messageReceived@resource://gre/modules/commonjs/toolkit/loader.js[/email] -> resource://gre/modules/commonjs/sdk/remote/parent.js:96:37
Apr 30 00:02:42 Desky-Ubuntu rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="993" x-info="http://www.rsyslog.com"] start
Apr 30 00:02:42 Desky-Ubuntu rsyslogd: rsyslogd's groupid changed to 108
Apr 30 00:02:42 Desky-Ubuntu rsyslogd: rsyslogd's userid changed to 104
Apr 30 00:02:42 Desky-Ubuntu systemd-modules-load[305]: Failed to insert 'ashmem_linux': Exec format error
Apr 30 00:02:42 Desky-Ubuntu systemd-modules-load[305]: Failed to insert 'binder_linux': Exec format error
Apr 30 00:02:42 Desky-Ubuntu systemd-modules-load[305]: Inserted module 'lp'
Apr 30 00:02:42 Desky-Ubuntu systemd-modules-load[305]: Inserted module 'ppdev'
Apr 30 00:02:42 Desky-Ubuntu systemd-modules-load[305]: Inserted module 'parport_pc'
```

---

