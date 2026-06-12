---
title: "Fstab Info"
date: 2017-04-22
forum: General Help
---

### Post by bookie2 on 2017-04-22
Hi guys!
When doing a reinstall you have basically two choices...

Choice1 disconnect all drives but the main one for the installation and add your other drives afterwards...

choice 2 have all drives connected and depending on the distro you can add mount info,as you install....even mount info for raid arrays..

I have disconnected all my drives but one for the installation...
I have my main drive, raid array with 3x3 tb drvies and a 2tb drive for other stuff...

Adding them to fstab I usually run blkid to find out the uuid numbers and add them to fstab...

What I am not sure about is the variables you can add...

Example:

uuid=...... /Mine  ext4  defaults  0  0 (it is the last variables I am not sure about sometimes you see 0 2 or 0 0? Can someone explain these variables to me...

Thank you!

bookie

---

### Post by TheFu on 2017-04-22
For the level of detail you are asking, there is only 1 place to get it.  We aren't allowed to say this, but it is THE ONLY VALID ANSWER.  **man fstab**.  I've seen many explanations, but many of them are incorrect, inaccurate.  The manpage is really the best source of information.

---

### Post by bookie2 on 2017-04-22
Thank you!
I will have a read....;)

Have a nice weekend!

bookie

---

