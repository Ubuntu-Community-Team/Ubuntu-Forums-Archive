---
title: "Can't sync Keepass2's database through SMB after updating to 20.04"
date: 2020-05-22
forum: General Help
---

### Post by scoffdon on 2020-05-22
Hi,

I have an issue with Keepass2 - Password Manager (I use this one instead of a native compatible application because I need the sync feature, which native app don't really do. Native app overwrite change when you sync from two different devices): since the update to 20.04, I can't sync anymore to my NAS through SMB.

No issue on 19.10 (I reinstalled a laptop for testing purpose). First, I thought it was because of Keepass2, maybe a bad update? The reason to think that is that the 19.10 ship with Keepass2 version 2.41 and when you update to the 20.04, Keepass2 is on version 2.44. So what I did is: download the 2.41 and try to launch it (with mono Keepass.exe) and then try to sync it: unfortunately, I have still the error "Synchronization failed" (and after the sync failed, the file on the NAS weight 0 byte).

So since it seem to not be because of Keepass2 itself, what seem to be the cause? Mono? I don't know what exactly changed between the 19.10 and the 20.04 (quick guessing: a lot of things!), but sadly it broke the sync function and I use a lot (I make change in computer1, then in computer2, I sync computer1 with the NAS and then computer2 with the NAS, with Keepass2 I have the change sync to the two devices while when I used a native compatible app, the change from computer1 was overwritten by computer2).


Any idea how to fix it? Or if you have a native app with a "real" sync function that I can use with SMB (I have no problem to switch)?

For info, it's not because of the old SMB1, my NAS run on FreeNAS on it's disabled since I installed it.



Thanks in advance for your help!



Best Regards,

---

### Post by ActionParsnip on 2020-05-22
If you mount the storage using SFTP is it better? Worth a try

---

### Post by scoffdon on 2020-05-22
Yep, it's seem to work with SFTP (I had to enable SSH because I usually don't run services I don't need on my NAS, so SSH was disabled and I usually prefer to keep it that way where I can).

It was a little easier with SMB because I could use the GUI to mount the share. Here I had to run the command to mount it where I wanted. I saw on the internet that you can setup the whole thing to auto-mount at startup with a key, so I may try that.


The funny thing is: I couldn't sync with Keepass2 the database, but I could create a folder with the Keepass interface on the NAS, so it was not a writing issue with SMB.


So, that doesn't fix the original problem, but at least it work again, thank you!

---

