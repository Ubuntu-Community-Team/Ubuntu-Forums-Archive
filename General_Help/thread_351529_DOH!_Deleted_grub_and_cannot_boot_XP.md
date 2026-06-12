---
title: "DOH! Deleted grub and cannot boot XP"
date: 2007-02-02
forum: General Help
---

### Post by gunst on 2007-02-02
Hi All
I running Ubuntu and XP in dualboot, and wanted to make a fresh install of Ubuntu. Me - not doing my research - deleted the ubuntu drives from Partition Magic in Windows and now i cannot boot windows. I tried fixing the error 22 with "fixmbr" and "fixboot" in the WIndows Recovery Console. 
But now it seems like i totaly messed up my Windows install. Now a boot menu appears and I can choose "safe boot" and "normal boot" and so on, but no matter what, Windows boots for 1-2 seconds and then restarts the computer - I can see the "blue screen of death" for a split second. What do I do :confused: 

Somebody help, please? :( 

/Gunst

---

### Post by g8m on 2007-02-02
Get your live install cd and install grub again...

---

### Post by g8m on 2007-02-02
boot live cd
mount the drive where ubuntu is installed
chroot into the mounted ubuntu install
apt-get install grub

or something like that

---

### Post by gunst on 2007-02-02
Could you please tell me howto or link?

---

### Post by Malac on 2007-02-02
pummel the F8 key until you see an option to :
[Disable Automatic Reboot on System Failure]
and try that. This should mean the BSOD will stay on the screen long enough to read the error. Google for solutions using the error name or number.

AND/OR

Same process but choose 
[Last Known Good Configuration(.....)]
See if that works.

---

### Post by g8m on 2007-02-02
hmm, it;s too early for me, forget about my entries, I didn't read the post correctly, the ubuntu drives are gone, so you can't get into ubuntu anymore. Don't know how to correct this with windows.

---

### Post by Malac on 2007-02-02
If my previous suggestions don't help you could try a "repair install" of XP.
[SIZE=1]I can't remember the exact wording of the prompts but they are close.[/SIZE] :)

Boot the Windows CD and choose Install Windows (NOT Repair Using Recovery Console option), then choose Repair Existing Install.
This preserves your data on the XP install and most of your settings.

There is an MS KB article on how to do this in more detail here. : [http://support.microsoft.com/kb/315341](http://support.microsoft.com/kb/315341)

---

### Post by gunst on 2007-02-02
Hi all
Thanks for the replies, I got help from a mate, I used Recovery Console and "chkdsk /r" which solved it.
Thanks anyways :)
/gunst

---

