---
title: "Package not found?"
date: 2008-03-17
forum: General Help
---

### Post by Replicon on 2008-03-17
Hi,

I just got my Serval Performance. This thing is sweet! Can't wait to set it all up and everything.

Quick question: I ran the software update, and it is failing on a package. It's getting a 404 on us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_7.10+20080205_all.deb

Is this something that needs to be reported to the repository owners, or is it a config issue on my side? I assume it's the repository, which is why I didn't just shove this into the system76 forum.

cheers

EDIT: ack! I just realize this seems to be blocking the install of build-essential, which is a problem hehe...

---

### Post by Rocket2DMn on 2008-03-18
Do you still have this problem?  It's possible that the file was just down for a bit while it was updated or something, the repos aren't perfect.  Try
```
sudo apt-get update
sudo apt-get upgrade
```
Post all the ouput here if it doesn't work.

---

### Post by Replicon on 2008-03-18
Thank you. Yeah, that fixed it. I'm not sure why it didn't work in the GUI. I didn't think to run it manually, as I thought the package manager gui is basically an APT wrapper, and hence, hitting "check for updates" should basically be exactly the same thing as running apt-get update.

Come to think of it, I updated with Aptitude, so maybe it was smarter and checked more than one place to pull the package from... or something. :)

cheers

---

