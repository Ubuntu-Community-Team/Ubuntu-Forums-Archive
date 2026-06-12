---
title: "Question about nvidia-173"
date: 2013-10-13
forum: General Help
---

### Post by jesus-freak on 2013-10-13
My parents have an old computer, probably from the XP era and a guy at my Dads work who is an IT suggested to install Linux on it and I was all for it because I got tired of telling him how to clean viruses off his computer lol. The guy installed Mint 14 Cinnamon and now they can't get the resolution right. There are only two options for resolution and they are both 4x3 and they have a widescreen monitor and the image is so big that they can't see the bar at the bottom however they can access the menu by just guessing and clicking around down in that area lol. Since Mint is Ubuntu based I'm assuming that switching to Ubuntu would''t help a lot. In the Driver Manager there are two options, the first one that it's set to by default only allows one resolution which is 4x3 and is so huge that you can't really use it at all. The second option says "Recommended" and it is nvidia-173. I told him to select that one and it gives him 2 resolutions now. Both 4x3 but the second one at least allows him to see the bar at the bottom with the menu. I did a lot of reading about nvidia-173 and I see a lot of people online saying that if you want to use this driver on newer OS's that you have to downgrade xorg-xserver. While I might be up for trying something like that I wouldn't ask my Dad to get close to that stuff. My question is this, Instead of downgrading xorg-xserver can we simply install an older operating system that the nvidia 173 would work better on? I also read someone saying that the Gnome classic worked better for his old video card running that nvidia 173. Should we try an older version of Ubuntu that has the Gnome classic? Would older systems be okay to use these days? All they use it for is email, instant messenger and youtube. They are not power users by any stretch. Any advice would be appreciated. It's really hard to trouble shoot from a distance, especially when I've only been using Ubuntu for a year now myself.

---

### Post by carl4926 on 2013-10-13
If it's old, you'll almost certainly be better with Mint Mate, not Cinnamon. 
Older CPU's can't handle the latest flash as it requires sse2 (I mention this as you yourself mention youtube)

You can list your hardware here by posting the result of
```
lspci -nnk
```

---

### Post by jesus-freak on 2013-10-13
I'll try to see if we can get that info for you. My parents and I are in different parts of the world so it can take some time. Actually we have tried several different modern versions of Mint including Mate and have the exact same problem on all. That is why I'd like to know if an older version of Ubuntu would be a viable option. One of the versions that runs Gnome or a version that has a gnome option. Can these older versions actually work effectively?

---

### Post by carl4926 on 2013-10-14
The 173 drivers are for GeForceFX GPU's
The info I asked for will just confirm exactly what GPU the machine has.

The driver that loads when you run the live DVD and immediately post install will be nouveau - I know some prefer to stick with that in certain situations. But the proprietary nvidia driver should work better. Older hardware though is more troublesome these days.

Older versions of linux may work better, but support and security updates will be an issue.

---

### Post by CatKiller on 2013-10-14
Not detecting the resolution is normally a monitor issue rather than a graphics driver issue.

Also, walls of text are hard to read.

---

### Post by jesus-freak on 2013-10-14
The IT guy that installed Mint did it at his house hooked up to his monitor and I'm almost positive he had the same problem because he told my Dad that he didn't know what was wrong and why it was acting like this. I'm not 100% sure so I will ask but if it was the same for him then that makes two monitors that display it without the proper resolution. Also, there is the problem of the OS itself not even being able to provide the correct resolution. The correct resolution would be 1280x768 and the only two the OS provides is 1024x768 and 800x600, both 4x3. So I think it is not sending the correct resolution to the monitor.

---

### Post by CatKiller on 2013-10-14
The way that the resolution is determined automatically is through a mechanism called EDID. It was formalised a very long time ago, so the only monitors that don't support it tend to be of the cheap & crappy variety - although using a KVM or a cable without sufficient cabling (essentially, also of the cheap & crappy variety) will also break the communication method, and I used to have a monitor that was distinctly neither cheap nor crappy that lied in the EDID information it provided.

If you select timings that your monitor can't handle you'll break the monitor, so resolutions that aren't categorically known to be supported by the monitor are suppressed. That's why you're only getting the option for 1024×768 and 800×600; those are pretty safe.

It is possible to manually specify the timings that should be used. In Windows this is with a "monitor driver" that's simply a text file that contains the timings that should be provided by EDID. Under Linux, the old method (the one that I'm familiar with from my afore-mentioned lying monitor) is to specify these values through xorg.conf. The new method uses XRandR (X Resize, Rotate and Reflect), although I don't have any experience of that since I got a well-behaved monitor before the switch. There are many posts that describe both processes.

If you get stuck, provide more details about the monitor and where you've got to and I'm sure someone can walk you through it.

---

