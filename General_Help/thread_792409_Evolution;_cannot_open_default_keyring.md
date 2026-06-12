---
title: "Evolution; cannot open default keyring"
date: 2008-05-12
forum: General Help
---

### Post by slambrick on 2008-05-12
Hi, Every time I open Evolution I am asked to put in my password to unlock the keyring as Ev cannot access it. This only started happening after an Ev patch recently installed.

---

### Post by darco on 2008-05-13
> **slambrick said:**
> Hi, Every time I open Evolution I am asked to put in my password to unlock the keyring as Ev cannot access it. This only started happening after an Ev patch recently installed.

Ya I posted this a couple weeks back and still no reply. My pop up is for the alarm-notify which I disabled in Evo and under System/Preferences/Session but they keyring keeps popping up...
good luck
darco

---

### Post by darco on 2008-05-13
ok, killed two birds w/one stone....

[http://ubuntuforums.org/showthread.php?t=776176](http://ubuntuforums.org/showthread.php?t=776176)

I was able to unlock my network keyring for my laptop :grin:

and was able to unlock the Evolution alarm on my PC :guitar:

[http://ubuntuforums.org/showthread.php?t=776176](http://ubuntuforums.org/showthread.php?t=776176)

good luck 

darco

---

### Post by zhkent on 2008-09-01
This worked for me to get the keyring from popping up in evolution (hardy).
System - Preferences - Password and Encryption 
This opens the password and encryption window.
Click on the PGP Passphrases  Tab
Uncheck the box beside - Ask me before using a cached passphrase

I [COLOR="DarkOrange"]was wrong, horribly wrong![/COLOR]
When I rebooted the keyring was back.

I read in a post that if you login without a password then evolution will ask for it.
If you login with a password evolution won't ask for a password.

---

### Post by zhkent on 2008-09-07
After changing the "Ask me before using a cached passphrase".
Evolution will only ask for the password the first time you open it after booting up, not each time.

---

