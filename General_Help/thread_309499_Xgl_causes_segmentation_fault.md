---
title: "Xgl causes segmentation fault"
date: 2006-11-29
forum: General Help
---

### Post by illfingaz on 2006-11-29
Hi guys,

I used to run Ubuntu (Dapper) with the latest nVidia driver + xgl + beryl without any problems. I recently moved to Xubuntu (Dapper) and tried going through nvidia+xgl install process.

Both the nVidia driver and Xgl installed without any errors but when I try to run:

```
Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer &
```

I get a segmentation fault. Can anyone suggest what the problem might be or maybe a file I can check to get some more details? Thanks in advance guys.

---

### Post by Joe_CoT on 2006-11-29
There are a number of reasons for xgl to segfault. many of them involve a slight breeze going through the room ;)

Have you tried using aiglx or the beta nvidia driver? both are **much** more stable...

---

### Post by illfingaz on 2006-11-29
I haven't tried the beta drivers + aiglx because up to this point Xgl was working great. I guess if no one else has some ideas I might end up trying that. Thanks for the input. Anyone else?

---

### Post by Joe_CoT on 2006-11-29
Well, the thing is that programs **shouldn't** segfault. That means there's a bug on the software's end, and besides a work around, there isn't much you can do about it besides get the error, report it to their dev team, and see where it goes. In the spirit of that, try this:

```
gdb Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer
```
after the debugger is set up, type "run", hit enter. It will give you an error, which you can then google/submit. If you get something akin to "no symbols found", you'll need to install debug symbols for xgl/xorg in order to get a meaningful error.

---

### Post by illfingaz on 2006-11-29
Thanks for the suggestion...how do I install debug symbols for xgl/xorg as gdb is giving me 'no debug symbols found'?

---

### Post by Joe_CoT on 2006-11-29
Depends entirely on where you got xgl from. Assuming you got it from some third party repository or other:

```
sudo apt-cache search xgl
```

(you could also search for it in synaptic)
Try to find an xgl debug package. there *should* be one.

---

