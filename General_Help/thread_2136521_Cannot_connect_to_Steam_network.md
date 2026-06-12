---
title: "Cannot connect to Steam network"
date: 2013-04-17
forum: General Help
---

### Post by methargica on 2013-04-17
Hello,

I have recently installed Ubuntu 12.04 x64 where my friend is helping get started with this OS. We tend to communicate through Steam. I've installed Ubuntu about 3 days ago and installed Steam using the Ubuntu Software Centre. Only just yesterday, I've been having these really weird connection issues with Steam. Where it cannot connect to the Steam network. I did some research and found that this deals with the problem. But this is not the case for me. 
```
sudo dpkg -r steam:i386
sudo dpkg -P steam:i386
rm -r /home/username/.steam
rm -r /home/username/.local/share/Steam
sudo dpkg -i /home/username/Downloads/steam_latest.deb
```
I've tried these multiple times, but no difference was made. I've reinstalled steam about 5 times using the terminal aswell.
```
methargica@mixolydian:~$ sudo dpkg -r steam:i386
(Reading database ... 198774 files and directories currently installed.)
Removing steam:i386 ...
```

I should mention that there is still a /home/.steam directory. And I'm not sure how I can remove this. 

Cheers

---

