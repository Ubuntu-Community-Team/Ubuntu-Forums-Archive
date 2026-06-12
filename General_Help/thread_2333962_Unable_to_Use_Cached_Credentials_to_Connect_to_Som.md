---
title: "Unable to Use Cached Credentials to Connect to Some Ubuntu Machines"
date: 2016-08-14
forum: General Help
---

### Post by Sambo_ on 2016-08-14
I have 2 Ubuntu Desktop 12.04 LTS machines, which are both fully updated as of today.  UbuntuB is a clone of UbuntuA

While they are generally running fine, I have a strange issue with some of them where I don't seem to be able to use the cached credentials from a Windows 10 machine to connect to some of them.

When I save the credentials for UbuntuB, I can reconnect to that machine after logging off and on to my Win10 machine no problem.  However, when I repeat the same actions for UbuntuA, when I log off and on again, I am prompted for the credentials, and even manually selecting the cached credentials for this machine does not work.

This does not appear to be an issue with any particular Win10 machine as I can replicate this issue on multiple different Win10 machines and it consistently works with UbuntuB, but not UbuntuA.

Anyone got any ideas what may be causing this?

---

### Post by Sambo_ on 2016-08-16
To answer my own question... :)

While I still don't know why there was a difference in behaviour between my 2 'identical' Ubuntu machines, I have discovered why the issue occurs and how to work around it.

It appears that Windows is to blame after all (why do you not look surprised!? :P).  The issue was that when saving credentials I was not using the fully qualified DNS name for the server.  Despite this working perfectly with the hostname only in the session in which I originally entered the username and password, and subsequent sessions when the login credentials were entered manually, it seems that when it comes to cached credentials, Windows is a bit more fussy about what it applies the cached credentials to (which I guess in all fairness is probably a prudent approach).

In other words:

Does not work:
[FONT=lucida console]net use \\UbuntuA /savecred

Does work:
[FONT=lucida console]net use \\UbuntuA.FQDN /savecred[/FONT]
[/FONT]
Once you save credentials for the FQDN you are then free to refer to the machine by hostname or FQDN and the cached credentials will function as expected.

Hopefully this saves someone else from wasting a few hours of their lives sometime in future! :)

---

