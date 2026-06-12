---
title: "nVidia problem and Wine"
date: 2006-08-30
forum: General Help
---

### Post by Thanatios on 2006-08-30
Well I recently tried to install the nVidia driver, and so now I dont know if its installed or not. Since when I installed it on Ubuntu before, it showed me a nVidia logo when I started up my Ubuntu desktop. Now I dont see that. How to check if its installed or not?

Also, when I try to run a game in Wine, I first get these errors:
```
Xlib:  extension "GLX" missing on display ":0.0".
err:opengl:process_attach Could not create default context.
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```
And then when the game starts up I get this error:

> Video surface allocation failed (Error code 13)

Please choose another video graphics mode (I have no idea how to do this)

Can anyone tell me what to do, and what is wrong? I am so confused.

Thanks in advance.

---

### Post by zxee on 2006-08-30
How did you install the propritary nvidia driver? There are some excellant guides in the forums check the top of this page: [http://www.ubuntuforums.org/forumdisplay.php?f=138](http://www.ubuntuforums.org/forumdisplay.php?f=138)
If the nvidia driver is correctly installed typing (in the terminal) > glxgears --printfps should provide you with a graphic and fps output.

---

### Post by Thanatios on 2006-08-31
well, when I type that, I get:
> thanatios@thanatios-desktop:~$ glxgears --printfps
Warrning: unknown parameter: --printfps
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

So I guess it doesnt work. =/

---

