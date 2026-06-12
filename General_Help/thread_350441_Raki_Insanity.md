---
title: "Raki Insanity"
date: 2007-01-31
forum: General Help
---

### Post by blackfire on 2007-01-31
Hello everyone,
 I'm getting mad here.
I'm trying to sync my i-mate pda2k (pocket pc) but seems like an old troll is tampering with my pc.
I managed to sync everything ok for about a week. Then I got the insane idea of connecting the pda to windows... I won't go into details: I ended up reverting the PDA to factory default.
Then, let the madness begin: raki wasn't syncink my pocket pc anymore.
My situation:

synce up & running
kontact [kubuntu edgy, kde 3.5.6] up & running
raki up and (SIGH) almost running.

I can sync my contacts without any trouble (well, almost. HINT FOR EVERYONE: If you have got pictures into your contacts raki won't be able to sync and you will lose some contacts, not just the ones with the pictures) BUT... BUT...
I am not able to sync my calendar NOR my todo list. I can see raki trying to and suddenly crashing.
The last messages I can see in the console is:

raki: Subscribing Todos ...
kresources: ERROR: ManagerImpl::readResourceConfig: mFactory is 0. Did the app forget to call readConfig?
raki: ERROR: Received DCOP: resource added for unknown resource qjgHux2PgV
raki: SynCEDeviceKonnector::readSyncees()...
raki: SynCELocalKonnector::readSyncee()...
KCrash: Application 'raki' crashing...


That's it. Looks like the local konnector isn't working. I'm using an ICS file as a base: if I don't have an event in the pda AND in the korganizer I can sync (well, it won't do nothing but it will not crash).


Please, let an angel answer me, I've lost the day already :(

---

### Post by 0cool on 2007-08-07
Hey,

has this issue ever been resolved?

I ran into the same issue when trying to sync my PDA with kontact.

> ws01:~$ raki: ... init
raki:  Creating PairEditorDialog
raki: PocketPCConnectorConfig::loadSettings
raki: Subscribing Events ...
kresources: ERROR: ManagerImpl::readResourceConfig: mFactory is 0. Did the app forget to call readConfig?
raki: ERROR: Received DCOP: resource added for unknown resource dq9qTEbuSl


KDE: 3.5.6
Kontact: 1.2.4
Raki: 0.9.1

---

### Post by eudemus on 2007-09-06
Totally infuriating.
Looks like this could be related to this bug:
[https://bugs.launchpad.net/ubuntu/+source/synce-kde/+bug/82455](https://bugs.launchpad.net/ubuntu/+source/synce-kde/+bug/82455)
which is "resolved", but not to the benefit of all but the most techie!

Another problem (RAKI only detecting your PDA as "anonymous"!
[http://osdir.com/ml/handhelds.ipaq.synce.general/2006-05/msg00007.html](http://osdir.com/ml/handhelds.ipaq.synce.general/2006-05/msg00007.html)

How do we get the powers that be in Ubuntu to recompile and make available via Synaptic (i.e. via the standard repositories) the 2 programs that seem to be needed for synce-kde and synce-konnector to perform their basic function? I would have thought that "closing" a bug report would have involved this .... evidently not. (or else this didn't quite fix the bug as cheerily as was thought).

Eudemus

---

