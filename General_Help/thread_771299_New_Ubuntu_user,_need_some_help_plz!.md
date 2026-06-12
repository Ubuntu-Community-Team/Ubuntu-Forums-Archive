---
title: "New Ubuntu user, need some help plz!"
date: 2008-04-27
forum: General Help
---

### Post by cullen418 on 2008-04-27
I have 8.04 and I have a couple of questions I need help with:

1.  I have an ATI 3850 and installed the restricted drivers.  When I try to use the enhanced desktop effects, my screen gets cut off.  My resolution is 1024x768 and when I apply them, a lot of the screen gets cut off, even though I can still click down at the bottom of the screen to change windows.

2.  The login screen doesn't fit on my screen.  It's way too big and I can't see everything.

3.  How do I get flash in Mozilla Firefox?

Thanks.

---

### Post by igfud on 2008-04-27
I'm afraid I may not be able to help with 1 and 2, but installing Flash in Linux is easy enough.

Download the tar.gz version of Flash here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

Once the download is complete, open the file up and click on the "Extract" button to extract the contents (if you're familiar with Windows, these "tar ball" files are a lot like zipped folders).  I'll assume you extracted the file to your desktop as a point of reference.

Go ahead and open the terminal (Applications > Accessories > Termainal) and navigate to the folder you just extracted by using the following command:

```
cd Desktop/install_flash_player_9_linux
```

(cd stands for "change directory" ie folder)

Now you need to run the installer file.  Enter:

```
./flashplayer-installer
```

The terminal should tell you to press ENTER to continue etc.  Follow the instructions.  Once the installation is complete, restart Firefox (if it is running) and you should be set.

There is one little known bug with the Linux version of Flash.  If you use a mouse with a scroll wheel, the scrolling will stop if your cursor ends up on a Flash object.  The Flash object is receiving the scrolling instead of the browser.  You just have to move your mouse off the Flash object to continue scrolling (there are no known fixes yet; this is a bug on Adobe's part and since their software is closed source, the open source community can't do much to help).

As far as I know, there is not a version of Shockwave Player available for Linux (this is often used in lieu of Flash for browser games).  You can, however, use the Windows versions of Firefox and Shockwave with Wine to get around this.

igfud

---

### Post by cullen418 on 2008-04-27
thanks, can someone help me with the others?

---

### Post by cybercookie72 on 2008-04-27
hi...im a noob too but

I have an nvidia 7300gs card but I think you might be running in to the same thing i did.  I did all the stuff to start compiz and when i restarted had low rez and that was all i could get.  I had to reinstall the nvidia drivers (I used that envy thing...works great) and once I did that I was able to use high rez and compiz with no problems.  And it seemed that each time I got a new kernel I had to reinstall the video drivers to get out of the low rez bad place :KS.

hope this helps

---

### Post by cullen418 on 2008-04-27
> **cybercookie72 said:**
> hi...im a noob too but

I have an nvidia 7300gs card but I think you might be running in to the same thing i did.  I did all the stuff to start compiz and when i restarted had low rez and that was all i could get.  I had to reinstall the nvidia drivers (I used that envy thing...works great) and once I did that I was able to use high rez and compiz with no problems.  And it seemed that each time I got a new kernel I had to reinstall the video drivers to get out of the low rez bad place :KS.

hope this helps
i did the envy install, but when I tried to enable the desktop effects the screen still got cut off.

---

### Post by cullen418 on 2008-04-27
help please!!!

---

### Post by cullen418 on 2008-04-28
can anyone help me?

---

### Post by cullen418 on 2008-04-29
please, i really want to get all of this sorted out!

---

### Post by loell on 2008-04-29
just a guess maybe its your monitor, what your refresh rate? 

find it in: **system menu**--> **Preferences**-->**Screen resolution**

---

### Post by cullen418 on 2008-04-30
It is 60Hz

---

### Post by TheLions on 2008-04-30
if you wish you can force a resolution:

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

also I would recommend to newest download drivers directly from ati page...

---

