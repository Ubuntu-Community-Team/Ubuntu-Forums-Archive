---
title: "Laptop Fingerprint Reader Software Desired. Lenovo T400"
date: 2013-05-07
forum: General Help
---

### Post by TomBrooklyn on 2013-05-07
What is the best software to enable the fingerprint reader on a Lenovo T400 laptop computer running Ubuntu 12.10?


How well does it work?


What happens if it fails to work every time?    Will I get locked out of the computer, or does the password access still work? 



I found a couple of other threads about fingerprint software but they were 2 and 4 years old and I don't know if they're still up to date.    I didn't append my question to those threads as most forum moderators seem to prefer new threads be started.

---

### Post by txwooley on 2013-05-07
Do a lsusb to get the ID of your reader.  Then have a look [here]("https://launchpad.net/~fingerprint") to see if it is compatible with fprint.  If your reader isn't listed then google the ID number.  Mine wasn't listed but I managed to find a patch for fprintd.

---

### Post by txwooley on 2013-05-07
Also have a look at [this]("http://askubuntu.com/questions/108835/how-do-i-use-the-fingerprint-scanner-on-a-hp-probook").  Lots of useful info.

---

