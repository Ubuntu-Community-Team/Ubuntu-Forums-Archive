---
title: "Not seeing some directories in windows partition"
date: 2014-05-30
forum: General Help
---

### Post by zitelli-pablo on 2014-05-30
Hi Guys!

I installed Xubuntu 14.04 in dual boot with Windows 7 in a Lenovo G480 laptop. I'm having the following issue:

I can't see (literally) a couple of directories which are in the Win partition. To be more precise, I mount the NTFS partition and need to read/write the C:/Users/my_win_user/Documents and another folder with data (C:/Data), but I can't find them even from terminal doing ls or from the file manager. I don't know what I'm missing...

I tried mounting the partition with: 

```
sudo mount -t ntfs-3g -o -rw /dev/sda2 /media/win
```

```
sudo mount -t ntfs-3g /dev/sda2 /media/win -o "umask=022"
```

Both with the same issue.

As a test, I copied the data folder from windows to an external HDD (NTFS), then mounted in Xubuntu and I can see and read/write the directories without any problem.

I can't realize what I'm doing wrong... I searched in the forum but couldn't find the same problem posted.

Thanks to everyone!

---

### Post by steeldriver on 2014-05-30
Hello and welcome to the forums

AFAIK, the Windows 7 default C:/Users/my_win_user/Documents is a "library" (virtual folder) not a real folder - you should be able to navigate to C:/Users/my_win_user/My\ Documents though

For the C:\Data folder I have no idea, sorry

---

### Post by zitelli-pablo on 2014-05-30
I tried that, same issue...

Could it be something related to Windows permissions to users or groups for those folders?

---

