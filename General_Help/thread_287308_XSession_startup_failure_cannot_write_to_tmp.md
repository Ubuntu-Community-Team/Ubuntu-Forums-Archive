---
title: "XSession startup failure: cannot write to /tmp"
date: 2006-10-28
forum: General Help
---

### Post by thesnowysoviet on 2006-10-28
This is the second time I've seen this error, unsolicited by any major system changes, across two Ubuntu distributions (Breezy and my current, Dapper).

On startup, everything goes well up until the kdm prompt for username and password.  After entering my password, I see the splash screen for a half-second, then an X window pops up:

"Xsession: warning: unable to write to /tmp; X session may exit with an error"

I click the only button - Okay - and I'm given another error, but this time with the window decorations of KDE:

"There was an error setting up inter-process communications for KDE. The message returned by the system was: Could not read network connection list: /home/me/.DCOPserver_computername__0.  Please check that the "dcopserver" program is running!"

I click Okay in that window, and I'm given a terminal.  After the error about dcopserver not running, I type "dcopserver":

"DCOPClient::attachInternal. Attach failed Authentication Rejected, reason: Non of the authentication protocols specified are supported and host-based authenticaion failed ICE Connection rejected!"

Odd.  "man dcopserver":

"gzip: stdout: No space left on device. man: command '/bin/gzip -dc /usr/share/manman1/dcopserver.1.gz' failed with exit status 256."

Curiouser and curiouser.  "sudo man dcopserver" works, as does any command prefixed by sudo except for cd, which does not work for reasons completely unknown to me.  My root, swap, and home partitions are 2.5GB, 1.5GB, and 20GB, respectively.  I tried making myself owner of /tmp and it didn't work.

Anybody know what is going on, before I make the mother of all bug reports to the Kubuntu crew?  Apologies for the incoherent error reports; this is the way they appear on my screen.

---

### Post by vibestriton on 2006-10-28
Is your root filesystem okay?

You can run fsck from the LiveCD.

sudo fsck /dev/<root partition identifier>


Note: Doing this when root is mounted is NOT a good idea.

---

### Post by thesnowysoviet on 2006-10-28
> **vibestriton said:**
> Is your root filesystem okay?

You can run fsck from the LiveCD.

sudo fsck /dev/<root partition identifier>


Note: Doing this when root is mounted is NOT a good idea.

What would my root partition identifier be?  "root"?  "/"?  And how would I know whether root was mounted or not?  Would it be safe to run from a console window within the KDE instance the LiveCD starts up?

---

### Post by vibestriton on 2006-10-28
Open a terminal window and type...

```
vim /etc/fstab
```

Your root device is listed left of "/".

Shutdown and reboot from the liveCD. Open a terminal and run...

```
sudo umount /dev/<root device name>
```

...just to be safe.  Then...

```
sudo fsck /dev/<root device name>
```

I hope this helps.

---

