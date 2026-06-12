---
title: "Update WARNING"
date: 2007-07-25
forum: General Help
---

### Post by doctorbrowder on 2007-07-25
Yesterday after I finally got my dial up modem set up, I happily connected to the internet and had to let it run about ten hours to download 140mb of updates! (felt just like Win XP again) I applied them and all seemed well.

Today, I connected to the internet and the update manager informed me that there were 40 MORE updates. I chose to take a look at them, and I got this rather dire looking message:

"Apply the following changes?

WARNING

You are about to install software that CAN'T BE AUTHENTICATED! Doing this could allow a malicious individual to damage or take control of your system."

Have I already been hacked into again, now with Linux???????? Shall I just throw the computer in the trash, rip out the telephone line and go hide under my bed?

---

### Post by FuturePilot on 2007-07-25
Try ```
sudo apt-get update
```
That might make it go away. Don't worry, no one has hacked you. It's most likely a 3rd party repo that you added and it doesn't have a gpg key to authenticate it. It might help if you post your sources list.

---

### Post by doctorbrowder on 2007-07-25
The only software I've added is ClamAV and Firestarter, and those directly from the APPLICATIONS --> ADD/REMOVE command. Could it be one of those two that is giving me this warning?

---

### Post by FuturePilot on 2007-07-25
Does it still happen after ```
sudo apt-get update
```? 
Since you haven't added anything to your sources list it's probably a key mis match on the repos end. I've seen it happen before. It might just disappear by itself.

---

### Post by doctorbrowder on 2007-07-25
Thanx! The sudo apt-get update appears to have worked. The warning disappeared and it downloaded the 40 more updates without complaint.

---

### Post by bettlebrox on 2007-07-26
What version of Ubuntu are U using? If your using the last development expect lots and lots of updates.

---

