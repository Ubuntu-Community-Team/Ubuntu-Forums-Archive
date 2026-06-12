---
title: "URGENT completley broken system, help!"
date: 2008-03-20
forum: General Help
---

### Post by corvettecraz92 on 2008-03-20
okay...i tried installing kubuntu 8.04 with KDE 4 using wubi 8.04. Now, i can't boot into windows OR ubuntu.

I booted into the kubuntu 7.10 livecd to try to look at my harddrive....only it's not mounting. it gives me "hal-storage-all-options refused uid 999"

WIll somebody PLEASE help me?? why is it that nobody ever replys to my posts?? I need help here, PLEASE!!! Is there any way possible i can get wubi Uninstalled, and windows working perfectly again????

---

### Post by ago on 2008-03-20
run chkdsk /r from a windows CD or a rescue CD (recovery console)
the above is usually due to hard-reboots or power losses

---

### Post by corvettecraz92 on 2008-03-20
YES!! YES! 

I found my windows cd!!!
will update...

---

### Post by fela on 2008-03-20
I heard wubi was really buggy...well, my friend (Mal1024 on the forums i think) used it with feisty and it corrupted his whole disk...might of been fixed in newer versions, but that's what I heard.

---

### Post by corvettecraz92 on 2008-03-20
hmmf. actually, it was the exact opposite for me: old version installed feisty just fine, but it was the newer version installing hardy that messed me up...

after I get this fixed, i'm done with ubuntu...

---

### Post by corvettecraz92 on 2008-03-20
Faaaantastic. now whenever i run chkdsk  /r it says 
"system has one or more unrecoverable problems"

trying to boot into windows: "Disk read error. Press ctrl+alt+delete to reboot."

NOW what?

Thanks Wubi, you just broke my entire HD! How's about you buy me a new one??

---

### Post by ago on 2008-03-20
All system corruptions reported so far were because of people hard rebooting...

And as you can see here [http://www.google.it/search?q=system+has+one+or+more+unrecoverable+problems&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.it/search?q=system+has+one+or+more+unrecoverable+problems&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a) 
 you can experience windows fs corruption independently of wubi (particularly when hard rebooting...) 

The link above by the way provides a few hints of things to try.

---

### Post by corvettecraz92 on 2008-03-20
well, that's great....so I guess the only thing to do is to format, and reinstall windows?

:(

---

### Post by ago on 2008-03-20
Try first to boot off a linux live CD and to mount the windows drive, if you can mount you should be able to recover most of it.They also suggest a few recovery tools, but I have never used any of those.

---

### Post by Vinnie_Fits on 2008-03-22
Some have had this problem with Wubi. Some have fixed it with Spinrite. Unfortunately, this nice proggie from Gibson Research is not free.

I understand your frustration. Good luck with the recovery.

As a note to others contemplating Wubi or anytime you take a drastic step of putting more than one OS on a single physical drive: Always make an image of your HDD before running anything like Wubi. I recommend Acronis True Image since that is what I use. Very stable and comes with a recovery CD (CD runs on Linux natch!) with which you can boot and then restore a pristine image of your Windows install. Saved my bacon more than once!

---

