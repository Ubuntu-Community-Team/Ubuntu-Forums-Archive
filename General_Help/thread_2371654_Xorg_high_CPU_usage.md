---
title: "Xorg high CPU usage?"
date: 2017-09-17
forum: General Help
---

### Post by meta-xx on 2017-09-17
Hi all, 

I recently decided to bite the bullet and install Linux on my PC, and at the recommendation of a friend I decided to go with Ubuntu Gnome. It should be noted at this point that I am admittedly inexperienced with code, commands, etc. I'm picking things up as I go along of course, but it's sometimes overwhelming. 

Anyway, the reason for this post. My PC has been on now for a few hours, and I started to notice things slowing down and getting 'laggy'. After some research I used the 'top' command in the terminal and noticed that something called Xorg was reported as using over 80% CPU usage. It's got to the point now where as I type this message it takes a couple seconds for the text to appear on screen. Can anyone shed some light as to why Xorg is running so heavy? And has anyone got any possible solutions? 

Just for reference, I have an AMD FX-8350, 16gb RAM and Gnome is installed on an SSD. So I can't see why hardware would be the bottleneck here.

If you need more information just ask and I'll be happy to supply it.

Thanks in advance for any replies!

---

### Post by ChuangTzu on 2017-09-17
first
```
sudo apt install inxi 
```
then post the output of

```
inxi -S -x  -M  -r -m -s -I 
```

remember to wrap ouput in code blocks so its easier to read in the forum

---

### Post by meta-xx on 2017-09-18
My apologies for the late reply. 

Unfortunately I can't do what you ask. I decided to simply re-install since posting. I also went with a different distro this time around. Many thanks for the effort though, I apologise for wasting your time.

---

