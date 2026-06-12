---
title: "[Feisty] Everything freezes when attempting to show home directory"
date: 2008-03-26
forum: General Help
---

### Post by Randomskk on 2008-03-26
Hi all,
I've run into a bit of a sudden problem and I've no idea where to even begin looking for a solution here.

I was on my dual-boot windows earlier today when I needed to get a file on my home directory. I use a windows ext3 driver to access my music collection which is on another partition, so I just told it to make my home partition available to windows.
This worked fine, I accessed the file and later rebooted into Linux.

Everyting booted fine, however whenever I tried to view my home directory, the program freezes. That's literally about as much as I can offer.
Konqueror and Dolphin both freeze right away, Kate won't even load. Firefox freezes when I go "Save Page As".
`ls` works for my home directory, but not the Pictures subdirectory (interestingly it does work for other subdirectories). The first time, I got a segmentation fault, and after that it just hangs.
I've tried `gdb /bin/ls` and that freezes too, and I've tried `truss /bin/ls` and that also freezes.

I've loaded windows and removed the home partition from showing up, but the problem persists on Linux.
It seems like it is only certain files that are causing the problem, since programs are able to load their configuration files fine.

The file I accessed in Windows was in /home/adam/Pictures, which is the directory that ls hangs on.

Addendum: I told bash to run ls for each directory in my home folder, and it got to Pictures and froze. I tried again in reverse order and again it got to Pictures and froze, so that certainly seems to be the culprit.
However, every other program still freezes just showing the Home folder (possibly because they calculate total disk space, perhaps by accessing the Pictures folder?)

I'm open to any suggestions!

Thanks,
Randomskk

---

### Post by Randomskk on 2008-03-26
Aha! Got it.
I did "sudo touch /home/forcefsck" and rebooted, causing fsck to be run, and it fixed the problem. Gotta love fsck.

---

