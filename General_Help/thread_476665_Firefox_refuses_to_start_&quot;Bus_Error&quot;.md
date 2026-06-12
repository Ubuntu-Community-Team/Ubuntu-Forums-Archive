---
title: "Firefox refuses to start: &quot;Bus Error&quot;"
date: 2007-06-17
forum: General Help
---

### Post by Area51mafia on 2007-06-17
Last night a website with a Flash application caused Firefox and X to crash, making me reboot. After I rebooted, Firefox reports the error **Bus error (core dumped)**. I rebooted again to try and fix it, and I get the same deal.

I've reinstalled Firefox: did nothing.
I've removed my profiles and had it create a fresh one: did nothing.
I removed Flash: did nothing.

I did force the removal of Firefox, then reinstalled. That SEEMED to work for about a minute or so, until it crashed and wouldn't start up again.
Only thing that seems to work is running Firefox as sudo.

Anybody know what could be the cause of this and how to fix it? I really don't like using Opera and Konq.

---

### Post by linfidel on 2007-06-17
Sorry I don't know offhand how to fix it, but I'd bet it's something in your firefox profile, and the solution will be to delete and recreate it.  Since it works with sudo, it's probably using a different profile, and that's the reason it works.  I would guess it's in your home directory, probably in the folder .mozilla.  You could try deleting the folder, or uninstalling firefox and then deleting the folder.  Or, you could check firefox site or forum for help.

Rebooting should never be necessary for something like Firefox; restarting it should be all that's required.

---

