---
title: "Help needed!!!!"
date: 2007-02-20
forum: General Help
---

### Post by jpe2000 on 2007-02-20
Everytime I try to run Beryl I get this message:

```

Detected xserver : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension : passed (v0.2)
Checking for XDamage extension : passed
Checking for RandR extension : passed
Checking for XSync extension : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig : passed
Checking for GLX_EXT_texture_from_pixmap : failed

No GLX_EXT_texture_from_pixmap
Segmentation fault
```

What the heck is wrong? And everytime I type "beryl-manager" it restarts the xserver. Please help me ASAP because I would REALLY like to get Beryl working.

Thanks.

---

### Post by jpe2000 on 2007-02-20
I'm sorry but I would like to get a reply sometime soon because I'm to excited and I really want this NOW lol...

---

### Post by yabbadabbadont on 2007-02-20
Common forums courtesy is to wait at least a couple of hours before bumping your post.  But since you are new, I'll go ahead and answer your question.  :)  (next time it will be 30 lashes with a wet noodle)

The answer to your question is that the driver you are using for your video card is missing a feature that is required to run XGL/Beryl.  Search the forums for guides on how to get the lastest drivers for your card.

Edit: If you search the forums for "GLX_EXT_texture_from_pixmap", you will find quite a few threads on the topic.

---

### Post by jpe2000 on 2007-02-20
Okay, thank. Just one question.

Why didn't my drivers come with that in the first place?

---

### Post by yabbadabbadont on 2007-02-20
> **jpe2000 said:**
> Okay, thank. Just one question.

Why didn't my drivers come with that in the first place?

Ask the manufacturer...

---

### Post by Tomosaur on 2007-02-20
> **jpe2000 said:**
> Okay, thank. Just one question.

Why didn't my drivers come with that in the first place?

Because the world is not magic :P

Seriously though - it depends on your graphics card. Most manufacturers do not release Linux drivers for whatever reason - and thus open source developers are forced to reverse engineer the hardware. Fear not - because these free drivers are generally of a very high quality (occasionally higher quality than the 'official' drivers!). The reason the drivers did not come pre-installed is normally because of legal issues. Ubuntu is free, so even if there are linux drivers available for your hardware - the manufacturers won't get a penny, so they won't allow the Ubuntu developers to ship the drivers required. There are projects available to help remedy this situation, look into Automatix, for example, which may help you out.

But, in the end, just tell us your graphics card and someone should be able to help you :)

Ah! You seem to have an Nvidia card. You're in luck, because nVidia are great with linux. Just go to the nVidia site and download the linux driver for your card. You may need to kill X server to install it, and install it via the command line, which is a bit of a pain in the backside but the results should be worth it :). If your card is recent enough, then you should be able to start beryl once the driver is properly installed.

There are also free nvidia drivers available, type this into the command line:
```

sudo aptitude install nvidia-glx

```

I have never gotten Beryl to work with the nvidia-glx driver before, so I reccommend the official one from nVidia's website.

---

