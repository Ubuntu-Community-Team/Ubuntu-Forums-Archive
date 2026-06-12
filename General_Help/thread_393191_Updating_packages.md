---
title: "Updating packages"
date: 2007-03-25
forum: General Help
---

### Post by fmcdee on 2007-03-25
When I click on the update triangle, it starts to come up but then the following message appears. "Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one."

  I'm not using any other packaging, apt-get or anything else that I am aware of. How do I find out what is active or what is causing this problem? 
tks :confused:

---

### Post by Dr. Nick on 2007-03-25
if your on kde then from a terminal run

sudo killall adept
sudo killall apt-get

or open the resource manager (forget where its at in kde) and look for any of them processes running.

Or simply restart the computer and see if it works then

---

### Post by fmcdee on 2007-03-26
I tried "sudo killall adept and sudo killall apt-get" and I checked out resourses and don't see anything running except "apt-index-watcher", which I stopped running, but still get the message as stated above. Any suggestions.  I do have Automatix installed if that means anything. Even when I try add/remove programs and sign in, I get the same message.

I tried to uninstall automatix2, using konsole terminal "sudo apt-get remove automatix2" per instructions at Automatix website. This returns the following:  "the package virtualbox needs to be reinstalled, but I can't find an archive for it". So I guess I first need to know how to reinstall the package virtualbox. Any help appreciated. (you too Nick)

---

