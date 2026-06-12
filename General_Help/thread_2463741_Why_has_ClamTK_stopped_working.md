---
title: "Why has ClamTK stopped working?"
date: 2021-06-17
forum: General Help
---

### Post by robert48 on 2021-06-17
I cannot do virus checks anymore because ClamTK has stopped working. I have removed and added but no joy. Is anybody else having the same issue? ClamAV won't run in a terminal either.
Ubuntu 21.04 AMD64

---

### Post by guiverc on 2021-06-17
Also asked at [https://askubuntu.com/questions/1346457/why-has-clamtk-stopped-working](https://askubuntu.com/questions/1346457/why-has-clamtk-stopped-working)

---

### Post by monkeybrain20122 on 2021-06-17
Does anyone still use clam? On Linux you don't need antivirus, clam is bloated garbage and it is supposed to detect Windows virus anyway, there are very few use cases I can think of for clamAV.

---

### Post by dddman on 2021-06-17
Looked it up in the software store, a lot of negative reviews.

I use AVG and let windows take care of windows.
[https://addons.mozilla.org/en-US/firefox/addon/avg-online-security/](https://addons.mozilla.org/en-US/firefox/addon/avg-online-security/)

with antitrack
[https://addons.mozilla.org/en-US/firefox/addon/avg-antitrack/](https://addons.mozilla.org/en-US/firefox/addon/avg-antitrack/)

---

### Post by guiverc on 2021-06-17
I don't have *Clam AV* installed on my desktops, but I usually do on servers.

I don't use windows, thus have no direct need for it, but I do transfer files to windows users on occasion (*via thumb-drive and not the usual web*) so it's a tool that lets me check for virus/malware on files that won't impact me, but may impact people I give them too.

(FYI: *the last malware I detected was in a GNOME theme file in additional files added that my boxes can't use... a bad payload ready to impact windows users should it reach their boxes*)

*Sorry I can't help or give opinion on question, I didn't run it at all during the hirsute cycle (as I'm on development, my current release is impish) so it's been >6 months since I last had need to run clamav; due covid lockdowns I suspect all transfers these days are online.*

---

### Post by klasse on 2021-07-15
> **robert48 said:**
> I cannot do virus checks anymore because ClamTK has stopped working. I have removed and added but no joy. Is anybody else having the same issue? ClamAV won't run in a terminal either.
Ubuntu 21.04 AMD64

 It's possibly due to the following bug: [https://bugs.launchpad.net/bugs/1927065](https://bugs.launchpad.net/bugs/1927065) .
 ClamAV in Terminal should not be affected, though. (Note that the  signatures manually updated with ClamTk and the ones updated  automatically with freshclam could be in different directories. The  directory can be passed as an option to ClamAV.)

---

