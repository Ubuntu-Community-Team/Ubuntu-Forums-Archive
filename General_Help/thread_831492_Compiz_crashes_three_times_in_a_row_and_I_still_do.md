---
title: "Compiz crashes three times in a row and I still don't know why"
date: 2008-06-16
forum: General Help
---

### Post by nstgc379 on 2008-06-16
Since the end of the Spring 2008 semester I've been pretty much forcing my way over to Linux for use as my main OS. Since this time, early May, I have been using Compiz quite a bit for its improved usablity as much as for its eye candy. I have also, since then, been plagued with two problems. One of these involves being Compiz crashing.

A few minutes I booted, everything was started and I started killing my widgets. When deskbar closed after selecting "emerald --replace" it crashed. I then reloaded Compiz. I then closed out of the terminal after mounting a fake-RAID partition. I can't remember what the third, just that I was very angry. While not a new problem, this is the first time I'd had triple failure (I'm the lucky sort who has a double drive failure on a RAID 5...I blame it on the card though...HighPoint sucks). Excluding the past thirty minutes, I hadn't had a single crash all day, and I was trying to make it crash. I was trying to figure out why it wasn't crashing, when it started with a "run away crashing" fest where every other application I closed crashed. Even tool tips made it crash. I restarted, leading to the beginning of this paragraph.

I realize that Emerald is a window decorator closely tied to Compiz, however that was the first time that action, to my knowledge, caused a crash. MPlayer/GMPlayer aside (I don't always use the front end), there are no apparent causes. As mentioned before, Deskbar automatically closing out or moving the curser as viewing a hint crash Compiz. Those do seem less likely to cause a failure then a normal application though. Its somewhat of a lie to say that I've never had three crashes in a row. MPlayer has been shown itself to be far worse then any other program. Closing and opening GMPlayer has caused more then three crashes in a row. That was when I found that some videos, without reason, will cause MPlayer/GMPlayer to crash almost 100% of the time. Others behave like normal applications. On average, MPlayer and GMPlayer crash more then other applications, however two videos which should be pretty much same thing (different video same encoding) may crash at different rates. No video will reduce the crash rate, which mostly is obtained subjectively, to less then the average, but some will dramaticly increase it.

As for my hardware I meant to to use Everest Ultimate to make a report, but didn't and now I'm angry thus reducing my desire to make such a report to next to nothing. I can give some information.

Monitor: SyncMaster 206BW
GPU: 8600 GT
GFX card maker: MSI
CPU: 13x Windsor (1 MB cache varient)
HTT: 210
RAM: 2 1 GB sticks of G.Skill DRR2 800 RAM stock latancy of 5-5-5-15 (2:1 divider @4-4-4-4-12 not sure about the RAS)
MOther board: GIGABYTE GA-M57SLI-S4
OS: Currently Hardy Haron 32b, however I have also had this problem with Hardy 64b, as well as the 64 bit versions of Gutsy and Feisty.
compiz --version :

Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:0402 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
compiz 0.7.4

Do know this is not the first version of compiz to cause this problem.

Another thread on this message board on the subject may be found [here](http://ubuntuforums.org/showthread.php?t=829045). It isn't as well written nor as thorough.

I have also used different plug-ins for Compiz. Originally, I didn't use Emerald, yet it still crashed. I tried reducing the settings down to "normal" as defined by Ubuntu's appearance dialog, and again, same out come.

---

### Post by dirtydaman on 2008-06-16
reinstall ubuntu or if u dont have hardy heron then upgrade to that and install the service pack and it will check all drives and stuff for incorrect codes etc. which will hopefully correct the problem or uninstall compiz and then reinstall

---

### Post by nstgc379 on 2008-06-16
I specifically said that I've used multiple version of both Ubuntu and Compiz. Furthermore, I would not tag this as "all variants" unless I had tried at least one of the other flavors of Ubuntu (in my case Kubuntu). Thank you for you for trying, it indicates that people care (which provides hope and comfort), however its a bad habit to suggest the obvious without first seeing if they haven't already done that.

---

