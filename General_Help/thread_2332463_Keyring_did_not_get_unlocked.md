---
title: "Keyring did not get unlocked"
date: 2016-07-31
forum: General Help
---

### Post by Gnusboy on 2016-07-31
Hey all
The strangest thing I've ever seen with Ubuntu just happened when I started the Chromium Web Browser. A box with a message popped up on my screen saying

"Enter Password to unlock your keyring password."
"The login keyring did not get unlocked when you logged into your computer"

Just prior to this message, I had been browsing in Firefox without problems, but I shut it down. Then I started to open Chromium and that's when the message appeared.
Once it appeared, I could not enter text in Chromium. I then opened Firefox and it opened the splash page, but would not accept any input.
I canceled the keyring box and note, then everything was OK. At least so far.

I do have a Ubuntu system password, but it does not need it unless I want to mess with primary Ubuntu. Why did this happen and what can I do about it?? Is it some kind of malware?

---

### Post by mansonfan78 on 2016-08-01
I've had this happen with Chrome web browser myself, it's just an issue with Chromium-based browsers apparently.  Probably caused by a recent update to Chromium.  It's nothing to worry about, just annoying.  For me, it eventually went back to normal all on it's own.

---

### Post by CantankRus on 2016-08-01
Chromium saves passwords to your Login keyring @ **~/.local/share/keyrings/login.keyring**
If you have automatic Login enabled in Ubuntu you will be asked to input your Login password to unlock the Login keyring when chromium opens, to access saved passwords.
Maybe you didn't have any saved passwords before.

Simple solution is to disable automatic Login in **System Settings > Users**
When you manually login the Login keyring will also be unlocked.

---

### Post by Gnusboy on 2016-08-01
Awesome! Thanks.

---

