---
title: "Synergy errors with connecting after 7.10 upgrade (Vista as server, Ubuntu as client)"
date: 2007-10-26
forum: General Help
---

### Post by elcman on 2007-10-26
Disclaimer: As obnoxious as this sounds, I'll slap in a disclaimer... I'm only a windows user for the games and not much else.

That being said, I've been running Synergy between my Windows XP machine (Server) and Ubuntu (Client, starting with Edgy).

This has been working just fine. I've put all the configuration pieces in place to make sure that logging in to Ubuntu would maintain the Synergy client at all times. I recently "upgraded" to Vista to see what it was all about. I was able to use Synergy without an issue still.

Then I upgraded from Fiesty to Gutsy. My wife pushed the "replace" button several times since we needed to get the server running again with Apache and her forums. In doing that, I swear, something happened that I can't figure out.

Synergy is dead simple to run. I've already got it configured on my Vista machine. I was even able to repeatedly kill it and launch it through PuTTY and have it connect and allow me to use it on both machines. I was still working out what remaining gdm config files to modify for it to start on boot when it stopped working and started giving me the following error:

```

****@****:/etc$ synergyc -f 192.168.0.5
INFO: synergyc.cpp,716: Synergy client 1.3.1 on Linux 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
DEBUG: CXWindowsScreen.cpp,840: XOpenDisplay(":0.0")
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
WARNING: synergyc.cpp,337: cannot open secondary screen: unable to open screen
DEBUG: synergyc.cpp,237: retry in 60 seconds

```

Everything is configured *exactly* as it had been. It should be working! It was working just yesterday, but the Windows Vista machine seems to no longer allow it to connect. All firewall options are turned off and I've made sure that there is nothing blocking the port. I've even made sure to put both aliases and ip addresses in to synergy and into each host file on both computers.

I'm completely baffled by this, I uninstalled and reinstalled both versions with the same results. I'm curious if I've messed up a config file somewhere, but there is nothing for synergy in /etc/ and ... since it is operating as a client, it just doesn't have much to do other than know *where* to connect.

If any gurus here know the answer, I'd sure appreciate it.

---

### Post by elcman on 2007-10-26
Gotta bump it.

A little more research: I've been trying to determine if it can't connect to the server or if the server is actively refusing the connection. I'm finding that the server doesn't even recognize when something is trying to connect to it, but the client is saying it is trying and being refused.

None of these ports are blocked, so I'm not sure what's up with this.

Any help would be marvelous!

---

### Post by elcman on 2007-11-16
I changed my setup around, but I'm finding that this error seems to only reside on the side of my Ubuntu box.

I've got this feeling that it has something to do with it not being able to open the LOCAL display... which is something I hadn't considered yet.

So, how do I fix that? What does this all mean?

```
INFO: synergyc.cpp,716: Synergy client 1.3.1 on Linux 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
DEBUG: CXWindowsScreen.cpp,840: XOpenDisplay(":0.0")
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
WARNING: synergyc.cpp,337: cannot open secondary screen: unable to open screen

```

---

### Post by DouglasAWh on 2008-02-01
Have you tried any other OSes with ubuntu?  I had a friend that got it working on ubuntu a while back, but I don't know if it was Gutsy.  He said it was kinda flaky though.  I know he works in an area with flaky wireless, but I don't know if synergies' flakiness was on wired too.  I'd love to get this working too!

---

### Post by DouglasAWh on 2008-02-05
I can connect to the server from the ubuntu client, but it doesn't seem to actually work.  Ubuntu says "connected to server" but Vista says "waiting for clients."  I've restarted ubuntu to see if that's a problem since I did ubuntu-ubuntu earlier.

So, I can now do Vista-XP (client) and ubuntu-ubuntu, but not Vista-ubuntu.  Grr.

---

### Post by primlantah on 2008-02-19
synergy doesnt support vista.  vista is not listed on the sourceforge.  Vistas security policy prevents synergy from working periodically.  It *can* work... but why would you use vista anyway?

on a side note..dont know why you cant get it to work on ubuntu... its fine when installed from the repository

---

