---
title: "Dual boot: NTLDR missing"
date: 2013-01-25
forum: General Help
---

### Post by kemo71 on 2013-01-25
Hi everybody , I have dual booting in my laptop windows xp pro and ubuntu ,for windows it was broken along time ago but I didn't care but today I tried to do a partition in my hdd it had two partitions I tried to cut from D disk to increas C disk but I just did the cut for D then after I tried to open my laptop the following message occur "ntldr missing press  ctrl+del+alt to restart"

I searched all over the internet but all the problems were just similar  to mine but I don't know what is the proper solution to my issue and if someone want to help please explain in a simple language because i'm not that expert .

thx Ubuntu Great Community

---

### Post by kemo71 on 2013-01-28
Hi everybody , I have dual booting in my laptop windows xp pro and ubuntu ,for windows it was broken along time ago but I didn't care but today I tried to do a partition in my hdd it had two partitions I tried to cut from D disk to increas C disk but I just did the cut for D then after I tried to open my laptop the following message occur "ntldr missing press ctrl+del+alt to restart"

I searched all over the internet but all the problems were just similar to mine but I don't know what is the proper solution to my issue and if someone want to help please explain in a simple language because i'm not that expert .

---

### Post by mörgæs on 2013-01-28
Threads merged.

---

### Post by oldfred on 2013-01-28
First try chkdsk from a Windows XP disk. Ubuntu has no way to run chkdsk.

Windows NTFS partitions have boot & partition information in the PBR or partition boot sector. If you changed partition size it has to run chkdsk to update size in PBR.

If ntldr is still missing then you may have corrupted system? Then additional Windows repairs may be required from XP disk.

       Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)

    
       chkdsk c: /r
     You may need to do this on all NTFS partitions (drives) on your system.

---

