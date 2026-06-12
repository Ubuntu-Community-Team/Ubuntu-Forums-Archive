---
title: "horrible performance from radeon hd3200 in 12.04"
date: 2013-01-05
forum: General Help
---

### Post by LLCoolJeff on 2013-01-05
ok so I am a bit confused about what is going on here....

1. My machine : gateway nv-52 series (2.1 ghz amd vision, 4gb ram, radeon hd3200 onboard graphics)

Now, I believe I have narrowed a past problem of mine down a little further. Unity runs horrible on this machine, and I have tried all combinations of different drivers, (stock ubuntu, direct from amd, etc) and I cannot get it to work right. even opening the main menu runs slow, youtube streaming? forget it, not happening. I have also tried different DE's and even XFCE runs slow, albeit a little faster than Unity3d. I also tried 12.10 and it is no better (even worse because that graphics card runs into problems with the new kernel, see here : [http://askubuntu.com/questions/202979/ati-radeon-hd-3200-very-slow-performance](http://askubuntu.com/questions/202979/ati-radeon-hd-3200-very-slow-performance))

Now, when I tried installing mint 14 XFCE, everything runs like a dream, the system is snappy, and 1080p video plays wonderful. I would much rather prefer to use Unity, but I cannot figure out why there is such a difference between Ubuntu and Mint. Aren't they both based off of 12.10? Shouldn't XFCE work the same in both of them? Shouldn't the same gpu problem in 12.10 be apparent in mint 14?

I am so confused as to why this is being weird, and I just want to try to get unity running smoothly on this machine. Thanks for your time, I hope I can get this sorted out

---

### Post by BlinkinCat on 2013-01-05
Copy and paste code into a terminal - Will show if Unity should run -

```

/usr/lib/nux/unity_support_test -p

```Cheers

---

### Post by LLCoolJeff on 2013-01-05
> **BlinkinCat said:**
> Copy and paste code into a terminal - Will show if Unity should run -

```

/usr/lib/nux/unity_support_test -p

```Cheers

output:

```
Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

hmm, so are you saying I should install unity inside mint 14? whats the proper command to do this right? I have seen a few different methods around?

I would be very grateful if this ends up working, but I am still a bit puzzled as to why the two distros give such different results..

---

### Post by BlinkinCat on 2013-01-05
> **LLCoolJeff said:**
> output:

```
Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```hmm, so are you saying I should install unity inside mint 14? whats the proper command to do this right? I have seen a few different methods around?

I would be very grateful if this ends up working, but I am still a bit puzzled as to why the two distros give such different results..

Hi, 
No I'm not saying that at all - results show Unity should run on your machine - It may be a driver issue - someone with more experience than I could help you there - I hope you resolve your issue

cheers

---

