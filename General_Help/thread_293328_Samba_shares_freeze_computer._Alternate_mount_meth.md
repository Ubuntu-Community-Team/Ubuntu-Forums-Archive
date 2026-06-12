---
title: "Samba shares freeze computer. Alternate mount method?"
date: 2006-11-05
forum: General Help
---

### Post by reldruH on 2006-11-05
I have a samba server on my local network with two shares that I mount onto my kubuntu laptop using fstab. Within two hours of turning on my computer amarok freezes, katapult goes next, followed by konqueror and then the rest of the computer. If I disable the shares I have no problems. Does anybody know why this happens or alternate ways of mounting the shares at startup I could try? My two entries in fstab are: ```
//my-server/Music /home/me/Media/Music smbfs username=me,password=passwd,fmask=777 0 0
//my-server/Pictures /home/me/Media/Pictures smbfs username=me,password=passwd,fmask=777 0 0
```Any advice I can get would be greatly appreciated.

---

### Post by zek725 on 2006-11-05
Nearly similar thing here. However, it only happens when the network server is disconnected. 

I've removed shortcuts to those unsuccessful mounts (meaning, network is disconnected thus, mount failure) to speed up launching of Thunar. 

Sometimes, I just edit **/etc/fstab** with the network mounts commented (**#**) as default. Whenever I need to mount the network, I just uncomment those lines then ```
sudo mount -a
```

---

### Post by reldruH on 2006-11-05
> **zek725 said:**
> 
Sometimes, I just edit **/etc/fstab** with the network mounts commented (**#**) as default.
That's what I've got now but I shouldn't have to manually edit fstab everytime I want to listen to my music, right? Isn't there an easier (automatic) way to do this? Also, what do your fstab entries look like? I had a lot of problems getting them writeable. They're owned by the user I pass to fstab, but always get mounted by root. Did you find a way around that (without using fmask?)

---

### Post by der_joachim on 2006-11-05
If you mount your smb shares as smbfs, you will probably have some speed issues, which may give you problems (I have speed issues, but apart from speed, no real problems. Guess I'm lucky). You may want to mount your shares as cifs, which is way faster and more stable than smbfs apparently. 

Hope this helps. Good luck.

---

