---
title: "Messed up Graphics Driver"
date: 2013-12-28
forum: General Help
---

### Post by jpr654 on 2013-12-28
Hi,

I recently dual booted Ubuntu on my Windows 8.1 machine. It was working perfectly, until I decided to mess with the graphics drivers. I changed it from the default open source to a closed source driver, and (naively) restarted the machine. Now I load in to a black screen--no GUI, but I do have a mouse. I want to reset the graphics drivers to the open source ones I had selected originally, but have no clue how to do so from the command prompt. Can anyone help me? Thanks!

---

### Post by QIII on 2013-12-28
Hello!

What is your model of graphics card and what driver did you install?  Is this a laptop with hybrid Intel/ATI or Intel/Nvidia graphics?

---

### Post by egeezer on 2013-12-28
It would also be good to know which version of Ubuntu you're running: 12.04? 13.04? 13.10? Some graphics handling is different in these.

---

### Post by jpr654 on 2013-12-28
Is there a way to tell from the Ubuntu command line what driver I installed (I didn't think that it would be a problem, so I didn't think to write the driver down)? I remember the name included "fglrx"--I think that was the type of driver I installed. I am running Ubuntu 13.10. The display adapters I have are (according to the windows partition): AMD Radeon HD 7700M series and Intel(R) HD Graphics 4000. I'm guessing that fits in the lines of hybrid ATI/Intel?

---

### Post by egeezer on 2013-12-28
fglrx is indeed the open source driver for ATI (Radeon) chips, and that is probably the one you were using before you installed.  There is a lot more information in the link below than I could possibly give you.  Best advice: keep searching in help.ubuntu.

[https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=fglrx&sa=Search](https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=fglrx&sa=Search)

---

### Post by QIII on 2013-12-28
fglrx is the closed source binary driver from ATI. 

Your troubles have to do with your hybrid setup.  Ubuntu 13.10 has a package available to make this work.  Unfortunately I'm on my cell phone right now.  I'll try to get back to this a little later.

---

### Post by QIII on 2013-12-29
Have a look [here]("https://wiki.ubuntu.com/X/Config/HybridGraphics").

Before you install the packages, make sure your current fglrx is uninstalled and you have renamed xorg.conf.  I wouldn't remove it, just in case, so

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Then install the packages as described in the link.  Also install fglrx-amdcccle so that you can use the Catalyst Control Center to control which card is used.

Let us know if that helps.

---

### Post by jpr654 on 2013-12-31
Purging all the files containing flgrx did the trick. I am now able to log into unity, which was the problem. Thanks everyone for the help!

---

