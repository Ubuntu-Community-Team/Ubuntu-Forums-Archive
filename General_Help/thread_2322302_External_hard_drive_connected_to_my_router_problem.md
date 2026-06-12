---
title: "External hard drive connected to my router problem"
date: 2016-04-27
forum: General Help
---

### Post by Lorenzo_ on 2016-04-27
Hey all,

im having trouble connecting to my external drive via wifi. A few weeks ago it just started continuously asking me for my username and password without letting me access any of the files. Any ideas or suggestions would be helpful and appreciated.

thanks.

---

### Post by him610 on 2016-04-27
You can begin by telling us more about the specifications of your router, your network, your external drive, and your system. 

I have never had the need to connect an external drive to my router which does not mean I can't. Most of the folks who hang around these forums thrive on solving problems.

---

### Post by mcduck on 2016-04-27
I ran into the same issue, I understood the problem is that the router I have (Asus RT-AC56U) is using older SMB authentication method that isn't enabled by default in Ubuntu any more. Luckily you can enable it again with a few lines added in /etc/samba/smb.conf

(This is the old bug report I found when looking for solution, seems like it's still haunting us... [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/510059](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/510059))

Anyway, just edit the /etc/samba/smb.conf file, and under the "[global]" section , add these two lines:
```
client ntlm auth = yes
client ntlmv2 auth= no
```

(I'm not sure if you need the second line at all or not, I'll have to test at some point, but this definitely fixed the issue for me. It was pretty odd, connecting to guest shares was fine, and I could mount the share manually from command-line, and Deja Dup was able to mount it for my backups without any problems, so it was just trying to connect to it through Nautilus that resulted in endlessly repeating password dialogue).

---

