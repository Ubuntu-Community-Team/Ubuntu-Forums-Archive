---
title: "System locks up when accessing shares from Windows machine"
date: 2014-12-23
forum: General Help
---

### Post by mike248 on 2014-12-23
I'm running 14.04 and have cifs installed.  I have a NAS with many shares mounted with no problem except when I don't access for a little while it may take 5-10 seconds to be able to browse the folder.  

If I had a Dolphin window open with a windows share opened or a terminal which was accessing a windows share, and the Windows machine shutdown or rebooted, I would not be able to use those programs at all.  I had mounted a windows share in my home folder like /home/user/winshare and if I accessed my home directory, it would lock the window up as well, in Dolpin as well as terminal.  If I ran the "df" command in terminal, it would lock up that tab of terminal.  

I thought I would have to reboot the system but I tracked down any app that was accessing the home folder or a windows share and closed it.  That cleared everything up.  

I decided that mounting in the home folder wasn't a good idea if it was locking up just by accessing my home folder so I created a /mnt/windows folder and put the shares there.  

I just now ran a command that was accessing a file list for a wget command and I mistyped the file location of the list, to /mnt/windows//drive/filename.txt and this caused the same problem as I had when the Windows system rebooted.  

Can anyone give meany insight into how to fix this or how to make this less of an issue?

---

