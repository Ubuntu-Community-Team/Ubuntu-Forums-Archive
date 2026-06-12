---
title: "Grub Customizer"
date: 2013-07-02
forum: General Help
---

### Post by cuzzo13 on 2013-07-02
I just started using grub customizer on ubuntu 12.04 but when i boot grub the picture i set is messed up i can see it but the colors are messed up and i dont see the os's and i cant start the system. I saw a thread saying to change the .jpg to .png and thats what made me be able to get this far.So how can I get the picture to look right and get the os's up there so I can boot them?

---

### Post by Bucky Ball on 2013-07-02
You may need to set a different resolution on the grub screen. You can do that in GC too from memory.

---

### Post by cuzzo13 on 2013-07-02
what resolution do I need to set?

---

### Post by Bucky Ball on 2013-07-02
Not sure. Suppose that would depend on the picture if I'm right. Can you still see the text? 

I would try a different resolution, setting them in GC, and see if it makes any difference. If so, try a few and experiment. If you can't see the text you know hitting return will launch the first kernel on the list so not too fraught with danger.

---

### Post by cuzzo13 on 2013-07-02
I cant see the text its not there I changed the colors of the text and the highlight color also i changed the font would that cause this problem
the picture is this
 [http://www.google.com/imgres?imgurl=http://www.paqoo.com/gudang/best-3d-hd-wallpaper-2013-aa.jpg&imgrefurl=http://www.paqoo.com/desktopwallpaper/1900x1200/best-3d-hd-wallpaper-2013-aa-12645.html&h=1200&w=1900&sz=697&tbnid=YU177ajS7uVdlM:&tbnh=90&tbnw=143&zoom=1&usg=__FPIOb3nUsY_QBg7gZMBXdOEfSfQ=&docid=w_zggJ9bwvN_1M&sa=X&ei=PjXTUeuOL7Kw4APCwoHYAQ&ved=0CDsQ9QEwBA&dur=296](http://www.google.com/imgres?imgurl=http://www.paqoo.com/gudang/best-3d-hd-wallpaper-2013-aa.jpg&imgrefurl=http://www.paqoo.com/desktopwallpaper/1900x1200/best-3d-hd-wallpaper-2013-aa-12645.html&h=1200&w=1900&sz=697&tbnid=YU177ajS7uVdlM:&tbnh=90&tbnw=143&zoom=1&usg=__FPIOb3nUsY_QBg7gZMBXdOEfSfQ=&docid=w_zggJ9bwvN_1M&sa=X&ei=PjXTUeuOL7Kw4APCwoHYAQ&ved=0CDsQ9QEwBA&dur=296) 

I right clicked it and clicked save image as then I converted it with terminal to png

---

### Post by Bucky Ball on 2013-07-02
Positive it converted? Not sure what format it needs to be in, or what size (that could be your issue in which case you'd need to shrink or resize the pic). As for the resolution, I guess that would depend on the res of the image you're using which could be on the website you link to. I'd say do a search for 'grub background image specifications'. Took me seconds to find this:

> GRUB 2 can use PNG, JPG/JPEG and TGA images for the background. The image must meet the following specifications:

    JPG/JPEG images must be 8-bit (256 color)
    Images should be non-indexed, RGB

By default, if desktop-base package is installed, images conforming to the above specification will be located in /usr/share/images/desktop-base/ directory.****

Photo can be JPG so that has nothing to do with it. But if it has converted and is not 256/8 bit then that's probably the problem. The photo is black and white so if the text is any other colour you would see it somewhere I'd say.

---

### Post by cuzzo13 on 2013-07-02
How would i get desktop-base package i dont think i have it

---

### Post by cuzzo13 on 2013-07-02
Ok I have The picture there but the letters aren't the right font its like a normal font instead of cursive bold italic size 16 looking font

---

### Post by Bucky Ball on 2013-07-02
Make sure the font and size is set correctly in GC. Experiment and see what works best.

---

### Post by fantab on 2013-07-03
> **cuzzo13 said:**
> I just started using grub customizer on ubuntu 12.04 but when i boot grub the picture i set is messed up i can see it but the colors are messed up and i dont see the os's and i cant start the system. I saw a thread saying to change the .jpg to .png and thats what made me be able to get this far.So how can I get the picture to look right and get the os's up there so I can boot them?

Certain pictures don't work with Grub. It is yet to be ascertained why it happens. Possibly, its because of the pictures' graphic properties. Try another picture both .jpg and .png will work with Grub.

A word about Grub-Customizer: though is a nice utility I have always faced problems with it. Almost everything Grub-Customizer can do CAN be done following [https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen).
Its quite simple and you must also encourage yourself to learn how to customize Grub without Grub-customizer.

---

