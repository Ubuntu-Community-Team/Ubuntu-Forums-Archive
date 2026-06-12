---
title: "Is it possible to take a Wubi install and turn it into a real partition?"
date: 2008-05-04
forum: General Help
---

### Post by stevezygote on 2008-05-04
Is it possible to take a Wubi install under Windows XP Home SP2 and turn it into an actual partition? If I delete Wubi/Ubuntu 8.04 I'll loose all my settings. What I'd ideally like to do is take what I currently have in the Wubi install and create an actual partition on my HDD. 

Background: I have a 2.2Ghz Celeron on 512MBs of RAM and a 52 GIG HDD (it's an HP Pavilion 514n so it has a locked FAT partition of 5 GIG which is the restore). I've created a 10 GIG Wubi install virtual drive under Windows XP Home SP2.

---

### Post by the8thstar on 2008-05-04
According to the Wubi website this is possible with 7.04 and 7.10, but NOT with 8.04.

Here is a possible workaround:

1. Assuming you have mounted XP in your current Ubuntu (Wubi) install, copy all the files from your /home in a folder in windows xp. Call it "ubuntu home".

2. Insert a liveCD, partition your disk as you see fit and reboot in Ubuntu. DON'T REMOVE/OVERWRITE XP!!! Use the option "largest contiguous space".

3. Assuming that XP is mounted in the new Ubuntu, move the contents of the folder "ubuntu home" to /home and replace everything. Once you're happy with the result, reboot.

4. Your settings and documents should be there. Reboot in XP and uninstall Wubi Ubuntu.

Let me know how it goes.

---

### Post by ago on 2008-05-04
You can access the files directly from a virtualdisk. See the wubiguide.

---

### Post by stevezygote on 2008-05-04
Thank you. I'll give it a try. Does this mean all my programs will be transferred?

---

### Post by stevezygote on 2008-05-04
> **ago said:**
> You can access the files directly from a virtualdisk. See the wubiguide.

I'm well aware of this. Perhaps you didn't understand my question, which has already been answered. I have a Wubi install. I've been mucking with it and I have it just to my liking. I wanted to take the Wubi install (in the virtual disk under Windoze XP) and make it a permanent, actual partition. Then delete the Wubi install under Windoze.

---

### Post by darco on 2008-05-05
This is what you need....
[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

I am waiting for the Developer to update to 8.04 which he said sometime in the next couple of weeks...

darco

---

### Post by stevezygote on 2008-05-05
> **darco said:**
> This is what you need....
[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

I am waiting for the Developer to update to 8.04 which he said sometime in the next couple of weeks...

darco
Wow. Thanks a lot. This will work on my 8.04? Again, thank you.

---

### Post by ago on 2008-05-05
lvpm does not yet support 8.04

---

### Post by stevezygote on 2008-05-05
I noticed that. However, the work around will? I copied the home directory in kubuntu to my winders xp my docs but as a failsafe (and the experience and a test of some cheap made in Taiwan DVD-RWs) I burned a Linux formatted DVD-RW. Later I tried reading it in winders and to my amazement winders actually could read it. It reads fine in Linux/Kubuntu.

---

