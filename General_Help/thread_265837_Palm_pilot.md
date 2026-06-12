---
title: "Palm pilot"
date: 2006-09-26
forum: General Help
---

### Post by mikaelu on 2006-09-26
I've have struggled with dapper and my Palm TX since the release of dapper and never got it to work (worked in Breezy). I've tried jpilot, kpilot and gpilot. I've also read and tried everything in the forum with no luck.
Today I installed a 2.6.17 kernel from edgy and jpilot worked right away. The only problem is that the Palm reboots after sync but I can live with that.
Is this a known problem? If so, there must be another solution considering that this is a LTS release, or.. ?

---

### Post by knowmad on 2006-09-26
This is a known issue (at least on the forums)-- [http://ubuntuforums.org/showthread.php?t=189400](http://ubuntuforums.org/showthread.php?t=189400). I don't know if it's a reported bug. I was successfully booting into 2.6.12-10 until today when I updated Dapper :(. Guess I'll be jumping to Edgy real soon now unless I find a 2.6.17 package for Dapper.

William

---

### Post by mikaelu on 2006-09-26
Well, it was a stupid question from me. I know it is a known problem....
What I really would like to know is if there is ANYBODY with a working sync or if a fix is to be expected. I find it hard to believe that this problem, if known and affecting all palm users, will stay the entire lifespan of Dapper.

---

### Post by uberg on 2006-09-29
i am able to do some simple sync with pilot-link (a collection of command-line palm utilitis) over my wireless network.  One of the options is -p for port.  Having the port look for the wireless connection allows me to use these utilities and not use the cradle.  Was not able to get cradle to work even with pilot-link.  For example, suppose i want the the file test.txt to be uploaded to the palm from my computer (command line):

install-memo -p net:192.168.1.4 -t test.txt

Will upload the file test.txt to your memo.  There are a TON of other utilities included.  Crude (read 'basic') and not pretty but it allows some syncing.  i just recieved a palm TX and am just finding out the problems with dapper now.  This is what i was able to come up with last night.  Still can't get kpilot (which is what i want) to work.  Nor can i get jpilot or gpilot to work either.  

Have you had any more success?

---

### Post by mikaelu on 2006-10-01
With a kernel from "Edgy Eft" (2.6.17-10-generic) I have been able to get jpilot to work. I still get reboots of the palm after every sync but except from the extra time it does not do any harm I can see. 

I can live with this until Edgy Eft is stable. As this is my main work computer (haven't done windows in 10 years) I was hoping to run Dapper for a longer time as it is almost perfect for everything else. But as it looks now I'm in for an upgrade. Hopefully it doesn't bring other problems...

---

### Post by Monkus on 2006-10-01
Hi,
Palm m130 here. So, if I update my kernel to say 2.6.17, will that take care of the sync issue, or no? I have the Edgy disc, I suppose I could use it to get a newer kernel. I am trying to sync with Gpilot and Evolution. Thanks for your help.

---

### Post by mikaelu on 2006-10-02
For me gpilot didn't work. Only jpilot. But it is worth a try. If you install the edgy kernel you will have it as a new boot option in grub. If it breaks something you only need to boot the old (2.6.15) kernel and remove 2.6.17.

---

### Post by Monkus on 2006-10-02
Well I put the Edgy disc in, but it doesn't show 2.6.17, only 2.6.15.Am I missing something?

---

### Post by mikaelu on 2006-10-02
I didn't use the CD. I've got it from:
[http://packages.ubuntu.com/edgy/base/](http://packages.ubuntu.com/edgy/base/)

---

### Post by Monkus on 2006-10-02
Well, I tried that but it didn't work either. I think it may be this laptop. I cannot seem to get the screen res working properly either. Even when I do everything others have done and been sucessful at. Oh well.

---

