---
title: "Graphics Drivers Problem? or Resolution?"
date: 2014-09-09
forum: General Help
---

### Post by Alex Eagle on 2014-09-09
I recently installed ubuntu, by reccomendation from a friend. I have downloaded ages ago but there was a problem with the packages, so I **had** to uninstall. I unistalled and reinstalled 3 times, but the problem insisted on coming back. But I tried again last week. The old problem is no longer effective, I don't know why, but it just isn't.

   I really want to get this to work guys, so ***please*** help. I do have experience with terminal, and know basic commands for it. I also know my way round all the little bits of ubuntu pretty well, but don't give me anything too advanced, coz I am still a bit of a newbie to this.

   So, the only problem I have with it now, is the SCREEN!!!!!!!!!!!! It's infuriating. It's unusable, until I get it sorted. Some windows fit, others have anything but the top left corner showing. The windows that are fully visible are way too big and chunky and blown out of preportion. I have enclosed screenshots to help with dianosing the problem. 

       [ATTACH=CONFIG]256293[/ATTACH][ATTACH=CONFIG]256294[/ATTACH]

The friend who put me on to ubuntu suggested that it would be a driver problem. I thought it was the resolution (640x480) but now think it's more likely to be the drivers. My System Settings>Details>Graphics says Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits). No idea what that is! :p XD But I do know that my card is probably intel, not Nvidia. But hey! What do I know?

   (The answer to that BTW is nothing. At least not about the card I've got.)

       I really hope that somebody with the answer finds this post, because this is the only bug with it. (FYI I have ubuntu 14.04 LTS.) I timed my startup this morning, and it took 1min 18sec! Compared with Windows Vista Basic (on the same laptop) which takes about an hour to get up to working standard and another 30mins to open Google Chrome.

Thanks Guys.:)

---

### Post by grahammechanical on 2014-09-09
To start with Galluim is an open source video driver for Nvidia cards.

Second, llvmpipe is a version of Gallium that Ubuntu uses for machines that have a graphic adapter that cannot do hardware accelerated 3D graphics that Ubuntu needs for the Unity user interface.

Third, we may have an appropriate graphic adapter but because of some conflict with graphic drivers Ubuntu will load and run on llvmpipe.

Fourth, If we select Recovery Mode from the Grub boot menu and then select Resume we load Ubuntu using llvmpipe. And as you have discovered llvmpipe does what it is supposed to do but it provides a less than satisfactory  user experience.

Question: Can your machine run Ubuntu Unity 3D? You do not tell us the hardware specification. What graphic adapter does it have? How much of its own memory does the graphic adapter have? Or does it share system memory (RAM) with the OS

Run this command

```
/usr/lib/nux/unity_support_test -p
```

If the answer is no, when you need to try Xubuntu or Lubuntu. Or stick with things as they are now.

If the answer is yes, then go to System Settings>Software and Updates>Additional Drivers tab and change the video driver. Keep also in mind that companies like Nvidia who provide the proprietary video drivers often drop support for older hardware from their drivers. That could also be the reason that you are running on llvmpipe. The open source video driver Nouveau (Gallium without llvmpipe) might be the better choice for you.

Regards.

---

### Post by Alex Eagle on 2014-09-09
This is what it came up with:

OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
OpenGL version string:  2.1 Mesa 10.1.3

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no



If you still need answers to other things you asked, sorry. I'm not sure if this covers it. And please remember, I'm not an advanced computer user. If what I've already said doesn't cover it, tell me where to find the other answers.

FYI my laptop is a Fujitsu Siemens Esprimo Mobile V5535 if that helps. And thanks for the prompt response.

---

