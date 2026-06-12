---
title: "Drag and Drop with Virtual Box"
date: 2012-12-18
forum: General Help
---

### Post by alphaamanitin on 2012-12-18
Hello Forum,

I have Xubuntu 12.04 LTS and winows 7 in virtual box with 8 gigs ram and dynamic storage limit to 150 gb.  Despite having a shared clipboard and bidirection clipboard and drag and drop enabled, I cannot get the copy and paste or drag and drop to work.  Does anyone else have this issue?

---

### Post by Cheesemill on 2012-12-18
Have you installed the VirtualBox Guest Additions in your Xubuntu?

---

### Post by alphaamanitin on 2012-12-18
I had not heard of that before.  I'll give it a shot and report back. Unfortunately I am WAY too swamped at work right now to deal with it. 

AlphaA

---

### Post by haqking on 2012-12-18
> **alphaamanitin said:**
> I had not heard of that before.  I'll give it a shot and report back. Unfortunately I am WAY too swamped at work right now to deal with it. 

AlphaA

install the Guest Additions (from within VM go to Devices menu and then choose Install Guest Additions) also add the Extensions pack available from [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

---

### Post by alphaamanitin on 2012-12-19
[s]I messed up and installed the guest additions before the DKMS.  So I rebuild the kernal with the appropriate command but still am not getting the drag and drop or clipboard features to work.  Can't figure out how to reinstall the Guest Additions.  Thought that might help.  Suggestions?

AlphaA


So tired and stressed from work, just now realized I completely f-up and was trying to follow the directions for a linux guest, thinking it was for linux host.  I am way too tired and stressed for this BS.  Thanks for the help guys.

AlphaA[/s]


Update, still doesn't work.  Not sure why, I have the guest additions install but no drag and drop, no clipboard.  I do have them both enabled.

---

