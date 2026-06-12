---
title: "Error Message"
date: 2016-12-30
forum: General Help
---

### Post by randym-axcess on 2016-12-30
When I run, "apt-get update", I get this message at the end of the string:

> W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release)  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.


This happened after a failed attempt to install Google Chrome on my 14.04 OS.

> 

wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -


sudo sh -c 'echo "deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main" >> /etc/apt/sources.list.d/google-chrome.list'


sudo apt-get update
sudo apt-get install google-chrome



So, how do I remove that from my sources.list and get rid of the message?

.

---

### Post by cariboo on 2016-12-30
> **randym-axcess said:**
> When I run, "apt-get update", I get this message at the end of the string:



This happened after a failed attempt to install Google Chrome on my 14.04 OS.



So, how do I remove that from my sources.list and get rid of the message?

.

Go to System Settings->Software & Settings->Other Software to remove the repositories you want.

---

### Post by randym-axcess on 2016-12-30
Thank you!

.

---

