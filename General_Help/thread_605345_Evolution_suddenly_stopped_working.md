---
title: "Evolution suddenly stopped working"
date: 2007-11-06
forum: General Help
---

### Post by shiftingsands on 2007-11-06
Running Gutsy, evolution worked great for a day, then overnight decided to stop fetching or sending mail. Get error  "Could not connect to smtp.telus.net: Connection refused"
 Deluge, firefox, thunderbird (with identical configuration settings) all work fine...
Is there a log file or something I can examine to find out what went wrong?
Thanks for any assistance

---

### Post by shiftingsands on 2007-11-07
I found the problem. Somehow, the "use encryption" setting was enabled. I think the username and password were encrypted before being sent to the server. I have no idea how that setting was enabled. Anyway, its working now. Maybe my wife was fiddling with the settings!

---

