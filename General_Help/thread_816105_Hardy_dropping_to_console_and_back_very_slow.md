---
title: "Hardy: dropping to console and back very slow"
date: 2008-06-02
forum: General Help
---

### Post by svaens on 2008-06-02
Hi all, 

I am running Ubuntu Hardy (fresh install) on an old toshiba satellite with a nvidia graphics card. 

I noticed this 'problem' on Hardy only because, before I was running Hardy, I was running Gutsy, and I hadn't noticed this on Gutsy. 

dropping to console (ctrl+f1) is not instant, but nothing to complain about. 
However, getting back X (ctrl+f7) takes a real long time (relatively) compared to how fast it was in gutsy (and other earlier versions). 
It now takes a good 5 seconds at least, during which you can see different shades of black blink across the screen, as if X was attempting to start, fail, retry, fail then finally succeed. 

This causes problems for other applications as well, for instance, when I go 'full screen' on my vmware (running another OS as a guest system). The change to full screen takes a real long time. Annoying. 

This problem, while not so drastically bad in itself, is bad because it shows a degradation in the performance of the system, when it should be getting better. 

I don't know if this is a graphics card issue, or what. Has anyone else noticed this? Anyone not using NVIDIA noticed this? 
I guess what I could do to further test the my theory about the driver is to test the free nv driver... which I haven't done yet. But I will do in the near future and post my results here. However, I would really like to hear of people who've noticed the same thing. Or is it just my luck, and my computer?

Kind regards, 

svaens

---

### Post by Joeb454 on 2008-06-02
It's not that slow on my laptop (Intel graphics). I'm guessing it probably has something to do with loading the restricted driver or something, though I don't know for sure.

What are the spec's of the machine in question?

---

### Post by svaens on 2008-06-02
Hi, and thanks for the reply!

I've got a toshiba satellite 2410, 

1.7GHz pentium 4, 14.1" XGA TFT Display, 2GIG Ram (not original) 
nVidia GeForce4 420Go 3D graphics controller with 16MB Video memory, 
Hardware 3D Graphics accelerator.

for complete specifications sheet, see the link:

[http://www.bmstech.com.au/Brochures/toshiba/s1410.pdf](http://www.bmstech.com.au/Brochures/toshiba/s1410.pdf)

Kind Regards,

svaens

---

### Post by Thanoulis on 2008-06-02
Hi svaens...i've got GeForce 6150, and my switching works fine...i'm using the restriced nvidia driver, installed with [i]envyng[i].

---

### Post by svaens on 2008-06-02
Thanks also for your reply. 
I remember I was using envy to install my nvidia restricted drivers on Gutsy (but that caused me other problems). 
This time, I installed Hardy fresh, and have not made any changes to the default installation except to install the nvidia drivers via the restricted drivers manager ubuntu provides, and use a custom edid file so that my notebooks LCD screen would be used correctly. However, this is the same edid I was using in gutsy. I wonder though if there is a difference in the driver one gets using envy (it compiles it for you on your own system doesn't it?) and the drivers installed via the official ubuntu restricted drivers manager.....   I hope this is not the cause.

---

