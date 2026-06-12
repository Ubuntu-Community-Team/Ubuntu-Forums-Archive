---
title: "Chromium whitelisting"
date: 2017-08-25
forum: General Help
---

### Post by webmiester on 2017-08-25
Hi Everyone,

I am making a company information system using the Raspberry pi running on ubuntu as workstations.  I am now using chromium (I had trouble with firefox not having any sound when playing mp3's - couldnt resolve that issue).  The chromium is beautiful in its kiosk mode.  I was just worried someone can simply press cntr-alt-T and run chromium from the command line and browse however he/she would like.  I tried a few whitelist manager add-ons to prevent people from browsing to places I would not want them to.  However, I found that by visiting "chrome://extensions", one can simply find the setup page of these whitelist programs and disable them.  In firefox, the whitelist add-on which worked perfectly was "Whitelist Ninja".  In whitelist ninja, it would also block entry to the setup pages but would allow entry with the password.  I would like to ask:

1) Is there a way I can put a password to prevent people to open certain applications through the command line?  Better yet, can I put a password to prevent them from opening the command line?
2) How do I block access to the chrome://extensions?  Is there a whitelist manager add-on that can function like this just like in whitelist ninja?
3) I found this resource which describes a way to block access to chrome://extensions, but it seems to be for windows.  Is there a way to make this work in ubuntu? [https://security.stackexchange.com/questions/66239/how-to-prevent-installation-of-google-chrome-extensions](https://security.stackexchange.com/questions/66239/how-to-prevent-installation-of-google-chrome-extensions)

Thanks so much

Thanks so much

---

### Post by webmiester on 2017-08-25
HI, I would like to give an update:

I found this site which describes the force addition of an add-opn which cannot be removed.  It might work.  However I don't understand the thread.  Basically, it says I have to add a string of text somewhese to make it into group policy.  But where do I add it?  I really appreciate you time, thank you.

[https://www.chromium.org/administrators/policy-list-3#ExtensionInstallForcelist](https://www.chromium.org/administrators/policy-list-3#ExtensionInstallForcelist)

---

### Post by webmiester on 2017-08-25
I tried changing the permissions of the extensions directory using: sudo chmod -R 444 .config/chromium/Default/Extensions
All it did though was make the extensions useless instead of protecting access to them.  What do you guys think of this idea?  Will a different set of restrictions work?  Or is this idea just plain crazy?

---

