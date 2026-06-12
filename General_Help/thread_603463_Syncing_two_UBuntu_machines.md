---
title: "Syncing two UBuntu machines"
date: 2007-11-05
forum: General Help
---

### Post by bogoliubov on 2007-11-05
I have two computers for work, one stationary PC and one laptop; both run Ubuntu 7.10.
I'd like to set them up so that I can sync all my (work) folders, files, mails, calendar tasks etc.

I know I can use rsync to sync folders. But can I somehow sync both machines simultaneously? How will then deleting a file (on purpose) work?
An example: I work a bit at the stationary PC, then (without syncing) work a bit with the laptop. After this, I'd like to sync them to get the result from my work to exist on both machines. 
Can this be done?


If it isn't possible to sync both machines simultaneously, then I can try to keep track of which computer I used last, and so remember which machine to sync. 
But what about mail and calendar things? Can I sync this with rsync (just basic files) or do I need something else? I use evolution.

---

### Post by fjgaude on 2007-11-05
Install unison, it is two way, and will do what you want. It's in the repository.

---

### Post by bogoliubov on 2007-11-05
> **fjgaude said:**
> Install unison, it is two way, and will do what you want. It's in the repository.

I'll have a look at it. Thanks for the help!

---

### Post by mauritzius on 2007-11-08
did you succeed in getting your evolution data between the two machines to sync? I would be very interested in that too..

---

### Post by bogoliubov on 2007-11-08
> **mauritzius said:**
> did you succeed in getting your evolution data between the two machines to sync? I would be very interested in that too..

Well, the thing is that I haven't yet received the stationary computer; I'm still waiting for it to arrive from Dell. I just wanted to think ahead a bit...

---

### Post by bogoliubov on 2007-11-13
Hmm, it seems that Unison is not enough to sync Evolution between two machines. It might work if the machines have identical names, but mine can't have that...

So, how should one go about with this? I'm looking at Opensync, which seems to be able to sync Evolution on two machines. Anyone out there who has tried this?

---

