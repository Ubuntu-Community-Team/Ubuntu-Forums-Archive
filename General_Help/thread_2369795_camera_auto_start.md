---
title: "camera auto start"
date: 2017-08-26
forum: General Help
---

### Post by unityforever on 2017-08-26
happened just now.
i saw indicator light running.

i need answer. 				

i didn't running any program which will trigger camera 				

i installed veracrypt winshark and ettercap before.
winshark and ettercap is downloaded from official source. veracrypt i download it from its official website via https
anti-virus detected malware in ettercap in early day.
i heard there are backdoor in vearcrypt before

and i installed update 1 days ago. 				

					i can't remove veracrypt.
i can use veracrypt but apt cannot find it in list.
i checked dpkg list also find nothing.

---

### Post by TheFu on 2017-08-28
The camera is just a device.  That means there is a file in /dev/ for it.  You can ask the kernel which programs are accessing which files. **lsof**, **fuser**, and there are other tools for it. So, first see which program is accessing the camera device.

Well - that isn't really true - the first thing you should to is cover the camera with some tape.
BTW, that doesn't prevent the microphone from being used too.

If you have flash or webRTC enabled in any browser, those are likely to be the issue. Remove/disable those things.

Or you could have been hacked. If you are paranoid, there is probably a reason, usually caused by visiting not-so-nice parts of the internet.

I've never used any of the programs you mentioned.  For encryption, I use dm-crypt/luks.

---

