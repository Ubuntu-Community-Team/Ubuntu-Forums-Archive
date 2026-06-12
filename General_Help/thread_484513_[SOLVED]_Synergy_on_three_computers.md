---
title: "[SOLVED] Synergy on three computers"
date: 2007-06-25
forum: General Help
---

### Post by letubenaiah on 2007-06-25
I'm having problems running synergy between three computers.  I'm running the server on Ubuntu and I have a Windows XP client and I'm trying to add a Xubuntu client.  When I was running just the Ubuntu and XP machines everything worked fine, but when I add the Xubuntu maching it all breaks.  The windows machine says it is connected but as soon as the mouse gets a couple of inches onto its screen it freezes.  The Xubuntu machine will not connect at all.   The Xubuntu machines debugger gives the following error:

```

ERROR: CServerProxy.cpp,187: server refused client with name "benaiah-server"

```

Here is a copy of my synergy.conf file:

```

section: screens
	benhenry:
	benhenry2:
	benaiah-server:
end
section: links
	benhenry:
		left = benhenry2
	benhenry2:
		right = benhenry
	benhenry:
		right = benaiah-server
	benaiah-server:
		left = benhenry
end

section: options
	screenSaverSync = true
end

```

benhenry is the Ubuntu server, benhenry2 is the XP, and benaiah-server is the Xubuntu machine.
If I remove all benaiah-server info it works fine.  

Any help would be great!

Benaiah

---

