---
title: "Screen Resolution"
date: 2006-12-16
forum: General Help
---

### Post by Ted D. on 2006-12-16
Since today's update I have a screen resolution problem. (I don't have a nvidia card.)
I am not able to get any higher resolution than 832x624(highest setting available - lower settings are available I need higher settings).
Does anyone else have this problem? How can I get higher setting? Assistance please.
I have posted this in the  update threads regarding nvidia drivers but since I don't have the card, I thought this issue should be posted here.
Thanks in advance.
Ted D.

---

### Post by taurus on 2006-12-16
What graphic card do you have anyway?  See if you can reconfigure your X by booting into recovery mode from GRUB menu and at the prompt, do

```
cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.bak
dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by Ted D. on 2006-12-17
On board S3 Graphics Pro savage DDS.

Will it be obvious what the next step is after I follow your recommendation in the terminal?

Thanks, Ted D.

---

### Post by Littleweseth on 2006-12-17
From memory, that command gives you a text-based wizardlike thing to reconfigure xorg.

---

### Post by Ted D. on 2006-12-17
Thanks all. It worked and I got the chance to go to X config which was a new experience.

---

