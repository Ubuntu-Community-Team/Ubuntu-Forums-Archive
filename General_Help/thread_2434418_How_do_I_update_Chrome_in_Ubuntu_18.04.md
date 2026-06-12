---
title: "How do I update Chrome in Ubuntu 18.04?"
date: 2020-01-05
forum: General Help
---

### Post by ubububub on 2020-01-05
Hi,

I got a message from a chrome browser extension that I was not using the latest version of Chrome so I went to terminal and did sudo apt-get update && apt-get upgrade. It was running fine until I got the message (in the middle of it):

Ign:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease

I tried doing:

sudo apt-get --only-upgrade install google-chrome-stable

which told me I had the latest version....which is confusing.
Do I have the latest version or do I not? Is this the correct way to update Chrome and will the Ign(ored) line affect the update?
What do I do?

I am 64bit, Ubuntu 18.04 on an Asus laptop.

---

### Post by crip720 on 2020-01-05
Most programs are updated automatically in linux.  Most recent stable chrome version is [COLOR=#5F6368][FONT=Roboto]79.0.3945.88, which should match [/FONT][/COLOR]if you go to about chrome in browser settings.  Extension might be wacky or worst.  Never trust extensions without proof.[COLOR=#5F6368][FONT=Roboto][/FONT][/COLOR]

---

### Post by deadflowr on 2020-01-06
What says
```
apt policy google-chrome-stable
```

---

