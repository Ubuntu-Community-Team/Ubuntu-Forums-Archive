---
title: "problem after installing google chrome &amp; with firefox"
date: 2019-10-09
forum: General Help
---

### Post by danieldama on 2019-10-09
Hey,

I installed lubuntu 19.04 today and started using it, while i watched youtube videos and videos from other site on **firefox** i notice some glitching when there were a lot of movement. the video didnt stuck, just some parts of the screen where there were a lot of movment looked "[COLOR=#333333][FONT=Assistant]flickery[/FONT][/COLOR]". Im using integrated intel graphic so if someone know what the cause I would love to go back to firefox.

and after I download chrom and started it from terminal im getting the following message: 

```
[5554:5554:1009/183925.057354:ERROR:sandbox_linux.cc(369)] InitializeSandbox() called with multiple threads in process gpu-process.
Opening in existing browser session.
```

and if im closing the terminal the browser closing too.

---

### Post by CatKiller on 2019-10-09
Both Chrome and Firefox disable hardware acceleration for video decoding on Linux. There's [a build of Chromium](https://www.linuxuprising.com/2018/08/how-to-enable-hardware-accelerated.html) that has it enabled.

---

### Post by danieldama on 2019-10-09
thats weird because I tried chromium too, and still it worked only on chrome.

and do you have any clue about the error? Im getting it when im openning spotify too:

```
[1009/192502.422617:ERROR:buffer_manager.cc(488)] [.DisplayCompositor]GL ERROR :GL_INVALID_OPERATION : glBufferData: <- error from previous GL command


```

---

### Post by deadflowr on 2019-10-09
> and if im closing the terminal the browser closing too.
How it should be, if you want to keep it running you need to disown it.

---

### Post by danieldama on 2019-10-09
> **deadflowr said:**
> How it should be, if you want to keep it running you need to disown it.

thank you,


and I just notice that it doesnt matter what the program im trying to open from the terminal after it opens im getting the error I posted.

this time with chromium:

```
aniel@daniel-pc:~$ chromium-browser[24839:24839:1009/193229.264799:ERROR:sandbox_linux.cc(369)] InitializeSandbox() called with multiple threads in process gpu-process.
[24839:24839:1009/193229.398617:ERROR:buffer_manager.cc(488)] [.DisplayCompositor]GL ERROR :GL_INVALID_OPERATION : glBufferData: <- error from previous GL command


(chromium-browser:24809): GLib-GIO-CRITICAL **: 19:32:45.231: g_dbus_proxy_new: assertion 'G_IS_DBUS_CONNECTION (connection)' failed
Icon theme "breeze" not found.



```

is that normal?

---

