---
title: "Ubuntu not as fast as XP???"
date: 2008-06-24
forum: General Help
---

### Post by Predtech on 2008-06-24
Please help me on these few strange issues guys. I have noticed that even after i have tweaked Firefox to run faster it still seems to take substantially longer to launch my homepage, [www.360-hq.com](www.360-hq.com) , than it does on a windows partition running Firefox in the same PC. I think that I'm going crazy but it does run faster in XP than in Hardy, can someone please tell me what I'm doing wrong or if I'm missing something.

The second thing i have a problem with is when i run Firefox and view a flash video, if i have Amarok running in the background i have to close Amarok COMPLETELY before viewing the flash video or it just crashes and i have to use the system monitor to kill the amarok app so i can run it again.

I also have a third issue. My system monitor reports that i only have 3.2GB of ram, i have in fact got 4GB of DDR2 800MHz ram running in dual channel. Can anyone tell me how to fix this. I did read a guide that showed how to install the server kernel but i lost all Nvidia hardware support and my enhanced graphics like wobbly windows was ll gone.

Can anyone help me with these issues????

Thanks

---

### Post by deathsshadow77 on 2008-06-24
well the answer to the third question is quite simple
you are running a 32-bit OS which will only see up to 4 GB of ram (this includes video memory). The same thing also happens in windows. The only way around this is to use a 64-bit OS.

Edit: Pulseaudio may be the issue in your second problem. I can't run both amarok and any flash video at the same time because flash will not put out any sound. Hopefully someone will come clear this up.

---

### Post by WRDN on 2008-06-24
deathshadow77, a 32 bit OS can be forced to see more than 4Gb if needed.
Also, remember that some memory will be reserved by hardware. For example, if you have a GPU with 512Mb GDDR2 memory, you will only have 3.5Gb RAM.

Predtech, the server kernel will allow you to use more than 4Gb RAM (I think you can use up to 64Gb RAM). After installing this, try installing the official nVidia driver for the GPU, rather than the restricted drivers.

Regarding the Firefox issue, are you using a wireless or wired connection?

---

### Post by Predtech on 2008-06-24
> **deathsshadow77 said:**
> 
Edit: Pulseaudio may be the issue in your second problem. I can't run both amarok and any flash video at the same time because flash will not put out any sound. Hopefully someone will come clear this up.

Yeah i have exactly the same problem, i can't get audio from the flash if Amarok is running. I hope someone can help on this one, because i have Pulseaudio installed also.

---

### Post by bodhi.zazen on 2008-06-24
> **deathsshadow77 said:**
> you are running a 32-bit OS which will only see up to 4 GB of ram (this includes video memory). The same thing also happens in windows. The only way around this is to use a 64-bit OS.

That is not true.


[http://ubuntuforums.org/showpost.php?p=5222181&postcount=16](http://ubuntuforums.org/showpost.php?p=5222181&postcount=16)

---

### Post by Predtech on 2008-06-24
> **WRDN said:**
> deathshadow77, a 32 bit OS can be forced to see more than 4Gb if needed.
Also, remember that some memory will be reserved by hardware. For example, if you have a GPU with 512Mb GDDR2 memory, you will only have 3.5Gb RAM.

Predtech, the server kernel will allow you to use more than 4Gb RAM (I think you can use up to 64Gb RAM). After installing this, try installing the official nVidia driver for the GPU, rather than the restricted drivers.

Regarding the Firefox issue, are you using a wireless or wired connection?

As far as i can remember i have 256MB in my video card, it's a 7300LE if i remember correctly. I tried the guide that i had found on changing the kernel but as i said i lost all advanced visual effects. When i noticed that had happend i checked the hardware drivers and it was completely blank, not even giving me an option to download drivers automatically like it does on a fresh install. 
If you have a good recommended way for the kernel upgrade i'd love to hear about it man, i'm fairly new to Linux to be honest. Man, i've never used a search engine so much in my life, lol, but Ubuntu is definitely worth the change over. 
When i upgrade the kernel, i'll try going to Nvidia's website and install the official drivers from there, but i think maybe i should uninstall the current video drivers before the kernel upgrade, just in case it messes things up.

Anyways, thanks for the quick replies, this is why i love the Linux scene, hell i'm even starting to convert some others over to Ubuntu from Windows and Mac OS X.

---

### Post by WRDN on 2008-06-24
Not an easy way to do it, but you could try recompiling your current kernel. A word of warning, **DO NOT** do this if you are not comfortable compiling kernels.
You can set an option in the current kernel to allow 64Gb memory. To do this:

- Change directory to the current kernel in use
```
cd /usr/src/[kernel]
```

Now, type

```
make menuconfig
```

Before this will work, you may have to install other dependencies.

Once it opens, a screen with multiple options to configure the kernel will appear. Select "Processor Type and Features" then the "High Memory Support (4Gb)" option. Finally, select the "64Gb" option and save.

You will then need to recompile the kernel. There is a guide [here]("http://www.linuxchix.org/content/courses/kernel_hacking/lesson3") instructing you how to do so.

I will repeat my sentiments that, you MUST be comfortable compiling/ configuring kernels before doing this, as it could potentially go horribly wrong.

Regarding the GPU, you should use [envy]("http://www.albertomilone.com/nvidia_scripts1.html") to ensure the right driver is installed.

EDIT: As a final note, I would suggest you do not bother trying to upgrade/ reconfigure the kernel, unless you believe the benefits will be worth the effort. Check you're system monitor during 'heavy usage' and if you're not using the full 3.2Gb RAM, then I see no reason to bother forcing Ubuntu to see all of it.

---

### Post by Predtech on 2008-06-25
Ok, so i decided to reinstall the os with the 64bit version and i think it runs faster as a whole entire system compared to the 32bit version, so as far as the speed is concerned, i think that's under control. Using the 64bit os also addressed the ram issue, now i see 3.9GB of ram

Now if someone can help regarding the Flash/Amarok issue that'd be great.

Thanks

---

### Post by squashpup on 2008-06-25
"Please help me on these few strange issues guys. I have noticed that even after i have tweaked Firefox to run faster it still seems to take substantially longer to launch my homepage, [www.360-hq.com](www.360-hq.com) , than it does on a windows partition running Firefox in the same PC. I think that I'm going crazy but it does run faster in XP than in Hardy, can someone please tell me what I'm doing wrong or if I'm missing something."

I've noticed several things since installing Ubuntu Hardy on this ancient 433mhz laptop with only 196 mb RAM:

1) Firefox is significantly slower than it should be out-of-the-box.  
2) When I do the tweaks that everyone suggests to speed up the connections, it seems to run even slower.
3) I've given up on Firefox altogether on this computer and now use Opera, which, even with such limited resources, is quite snappy.

I'm not suggesting you give up on Firefox, but if you try Opera and the speed is the same, then you know it's probably not a Firefox problem and you can start looking elsewhere.  On the other hand, if you notice a speedup with Opera, then it's probably a Firefox problem and that's where you can concentrate your attention.

A word of advice:  go to the Opera website and get that version.  The version that's in the Ubuntu repos isn't current and refuses to use the Flash and Java plugins, but the version from the site works perfectly.

Hope you get it sorted out.

---

### Post by Predtech on 2008-06-25
Yeah, i used to use Opera many moons ago before firefox ever came out. I'll give it a spin. 

Thanks

---

### Post by Predtech on 2008-06-25
I downloaded Opera a few minutes ago, and man it is horrible. I have no way of importing my many passwords like i can with the password exporter for firefox, PLUS the back and forward buttons on my mouse don't work in Opera when they do in FF, and that's a HUGE problem for me. I have become so used to using them that i can't bare to use the browser back and forward buttons. Now if there is a work around for both of these problems then it might be worth having another look at but until then, no way.

But i do sincerely appreciate the idea though. Thanks for that.

---

