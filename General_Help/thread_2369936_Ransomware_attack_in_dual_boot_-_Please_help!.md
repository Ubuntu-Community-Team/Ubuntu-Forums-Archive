---
title: "Ransomware attack in dual boot - Please help!"
date: 2017-08-28
forum: General Help
---

### Post by misasoup on 2017-08-28
Hi There,
I may have become a victim of a ransomware attack. It blocked my PC while working in Vista and I panicked and forced it close. 
I managed to boot into Windows safe mode, but my daughter had to fiddle and booted into Ubuntu, which appears to work ok.
I should be most grateful if you would advise me on what to do next.
 Is Ubuntu affected by this? How about the files created in Windows to which I have access in Ubuntu?
PC is an HP All-In-One TouchSmart IQ830be with a dual boot Vista/Ubuntu. 
Many thanks in Advance,
M

---

### Post by su:bhatta on 2017-08-28
Check these out for starters

[https://ubuntuforums.org/showthread.php?t=2364841](https://ubuntuforums.org/showthread.php?t=2364841)




[COLOR=#000000][INDENT][https://ubuntuforums.org/showthread.php?t=510812](https://ubuntuforums.org/showthread.php?t=510812)[/INDENT]

[/COLOR]
[COLOR=#000000][/COLOR]

---

### Post by misasoup on 2017-08-29
Thank you

---

### Post by gordintoronto on 2017-08-29
It's my understanding that there is a Windows driver which gives access to some Linux filesystems, but very few people have installed it, so Windows has no access to the files in your Ubuntu, and Windows ransomeware has no access.

On the Windows side, how's your backup? If you back up to an external drive which is normally not connected, it might be OK. To get rid of ransomeware is a "nuke and pave" operation: delete the Windows partition(s), recreate them, install Windows from scratch, install applications, restore your data from backup.

---

