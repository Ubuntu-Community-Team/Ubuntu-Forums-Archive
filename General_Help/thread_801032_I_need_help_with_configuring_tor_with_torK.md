---
title: "I need help with configuring tor with torK"
date: 2008-05-20
forum: General Help
---

### Post by mamadu bwana on 2008-05-20
I am trying to configure torK on my x386 computer running Ubuntu 8.04 and I am running into some problems.  Could you please point me towards the right solution?

I installed torK, tor and privoxy without any problems.

I used the torK wizard to configure to to run as a client.```


I configured torK to lauch tor when needed (tor is not started at bootup)

When I try to lauch torK from the "press play to get started"  I get this message:

TorK couldn't start your Privacy Proxy!
Message: Nothing.
Reason: This may be because you have configured it to launch at system startup. If that is the case, and you have reason to believe it is configured to listen to Tor, then just click 'No' and take a look at the 'Konqueror' settings in the configuration dialog.
Would you like TorK to try restarting it again?
```

Then I choose 'yes' and I get:

```
Tor Couldn't Bind to One of the Addresses/Ports you configured!
Message: May 19 15:52:14.256 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Reason: Tor is probably already running. If you like, TorK can connect to the already-running instance of Tor and manage that for you instead. (You will have to open the configuration dialog and re-apply any settings you wished to use.)
```
Would you like to do this now?

and when I choose 'yet' I get:
```

TorK has passed an invalid configuration file to Tor!
Message: May 19 15:52:14.256 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
This means: Please report this using 'Help->Report Bug' in the menu. Try to provide as much detail as possible. Thanks!
```

What am I doing wrong?  How do I manually start tor and privoxy and have torK use them?

I know that it is not my hardware or network because I ran torK off a live-CD and everything worked perfectly.

Many thanks in advance for any pointers!

---

### Post by Monicker on 2008-05-20
Why a second thread on the same issue?  You already have this one going:  [http://ubuntuforums.org/showthread.php?t=800115]("http://ubuntuforums.org/showthread.php?t=800115")

If no one answers right away, it may just be that most here are not familiar with the application.  Please be patient.

---

