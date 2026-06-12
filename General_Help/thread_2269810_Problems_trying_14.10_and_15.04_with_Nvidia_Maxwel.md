---
title: "Problems trying 14.10 and 15.04 with Nvidia Maxwell card"
date: 2015-03-18
forum: General Help
---

### Post by ubunt72 on 2015-03-18
I tried the live media on usb - Lubuntu, Xubutu, Kubuntu and Ubuntu MATE @ 14.10 and 15.04.   None are usable.

I have a Nvidia Maxwell card, a 750, and the nouveau driver messes up the screen - res, text/fonts are blurry/small... the screen is unreadable.   

I don't know if I should try to install.   If it is still like that, then what?

Is this the typical experience for Nvidia Maxwell card owners?

---

### Post by Yellow Pasque on 2015-03-18
Try booting with nomodeset and that should give you a usable picture (though it may not be the correct resolution). At least then, you can install the proprietary driver, which is what most Maxwell owners want right now anyway. The open-source nouveau driver may eventually be in good shape for your card (I use it on my 8400GS), but it takes some time for the devs to support newer cards.

> Is this the typical experience for Nvidia Maxwell card owners? 
Theoretically, you should get the correct resolution (though no 3D acceleration). [http://www.phoronix.com/scan.php?page=news_item&px=MTY2NDI](http://www.phoronix.com/scan.php?page=news_item&px=MTY2NDI)
I'm personally not surprised that it's buggy though..

---

### Post by dino99 on 2015-03-18
i have the same card and nvidia-346 installed on vivid: everything works well. Even jockey works  :lolflag:
all installed from the vivid i386 archive

---

### Post by grahammechanical on 2015-03-18
The issue for open source developers is that they do not have the hardware to test their work on. They, personally, do not have the funds to buy new video adapters when they are released. It takes open source developers a bit of time to catch up with new hardware. 

I have learned that the first Maxwell cards were put on the market in February 2014 with the second generation being released in September 2014 and a new group released January 2015.

So, I am not surprised that Nouveau in Ubuntu 14.10 is not doing very well on the early versions of Maxwell cards. And I would be very surprised if Nouveau in 15.04 did well on the newest Maxwell cards. This is why proprietary video drivers are important when we have the latest hardware.

Do not forget that the live session in Ubuntu uses the open source video driver. When we install we get a proprietary video driver when we tick the box "Install third party software." 

Ubuntu 15.04 is still under development. So, improvements are being made to the kernel, and Xorg all the time. You might find 15.04 more useful once it has been released. The user experience on 15.04 today is not necessarily a true reflection of what the user experience on 15.04 will be by the release date.

Regards.

---

### Post by ubunt72 on 2015-03-18
> **Temüjin said:**
> Try booting with nomodeset and that should give you a usable picture (though it may not be the correct resolution). At least then, you can install the proprietary driver, which is what most Maxwell owners want right now anyway. The open-source nouveau driver may eventually be in good shape for your card (I use it on my 8400GS), but it takes some time for the devs to support newer cards.

Theoretically, you should get the correct resolution (though no 3D acceleration). [http://www.phoronix.com/scan.php?page=news_item&px=MTY2NDI](http://www.phoronix.com/scan.php?page=news_item&px=MTY2NDI)
I'm personally not surprised that it's buggy though..That's one of the first things I tried and it didn't do anything.   I also tried adding vga=771, too.   Neither made any difference from what I could tell.  

> **9d9 said:**
> i have the same card and nvidia-346 installed on vivid: everything works well. Even jockey works 
all installed from the vivid i386 archiveYou must have been drinking?    I guess if I was drunk, then the blurry, tiny text would be what I'd expect to see.   

Actually, I did try to install 346 by starting Ubuntu Software Center and typing nvidia 346 in the search field.   But, there must be a bug since it would claim there's no internet/network connection.   Yet, I could connect to the internet.  I tried to install via CLI, too.   But, it was too slow so I think it froze up.   Not sure what happened.   Perhaps, it would work with a real install, I don't know.   I just think it's pretty pathetic.

grahammechanical, are you trying to get a job as the nouveau spokesperson? :)   I know they have a hard time but why send it the customer's way?   If it doesn't work properly, then someone (the distro dev or both of them?) should disable it and let the user install it after it's installed.   That's what Nvidia does - it's just not installed at all.   That way, any potential conflicts or problems with the kernel or x-server is avoided, at least, for the live edition and install.   As long as you can see the screen (it might not be the optimal resolution and maybe certain features don't work), you can decide to install either the nouveau or nvidia driver after you have a working install.  

Btw, just telling me how difficult their situation is, doesn't help the user who can't use the driver nor the OS.  Regards.

---

### Post by ubunt72 on 2015-03-18
'Ubuntu 15.04 is still under development. So, improvements are being made  to the kernel, and Xorg all the time. You might find 15.04 more useful  once it has been released. The user experience on 15.04 today is not  necessarily a true reflection of what the user experience on 15.04 will  be by the release date.'

P.S.  My response to this, is that I couldn't use 14.10, either.   I tried 14.10 on live media and the screen problem was replicated.  So, I assume that when 15.04 is released, nothing will change regarding the video drivers and user experience.   Is that a reasonable thing to assume?

---

### Post by ubunt72 on 2015-03-18
"Theoretically, you should get the correct resolution (though no 3D acceleration). [http://www.phoronix.com/scan.php?pag...tem&px=MTY2NDI]("http://www.phoronix.com/scan.php?page=news_item&px=MTY2NDI")
I'm personally not surprised that it's buggy though.."

I read the article.   They were using:  "In fact, it mode-set correctly for dual-link DVI on a 30-inch Samsung  2560 x 1600 display for these two mid-range graphics cards." - a 2560 x 1600 display.   Perhaps, a monitor with such a resolution works.  Mine is 1650  x 1050.

---

### Post by Yellow Pasque on 2015-03-18
> a 2560 x 1600 display. Perhaps, a monitor with such a resolution works. Mine is 1650 x 1050. 
^That doesn't make any sense to me. Maybe if the article had a smaller resolution and yours was bigger..

---

### Post by ubunt72 on 2015-03-18
> **Temüjin said:**
> ^That doesn't make any sense to me. Maybe if the article had a smaller resolution and yours was bigger..Well, the higher resolutions are now the standard?

Just trying to figure out what the problem is.  I cannot find any similar problem with a fix or solution.   Most of them are after an install - I have always fixed any problem post-install.

---

### Post by efflandt on 2015-03-19
Actually because nouveau did not support the Maxwell chip yet I was surprised that I did not have an issue with live/install iso of 64-bit 14.04.1 (I used nomodeset), but maybe that was using some other video method, because in the installed system I don't even think I could get the login screen (I know that I could not log into X) and when I tried the text console, as soon as I would login, it would flash the motd and immediately return to login prompt. Installing **nvidia-current** by enabling networking and going to root shell in recovery boot got me as far as login window, but still not X (logs showed that nvidia version did not support the card). Purging nvidia* and installing **nvidia-331** worked (**nvidia-331-updates** would be recommended). The main reason I purged that and went to **nvidia-346** from xorg-edgers ppa was to play around with video overclocking (which requires 337 or newer) (default speed is not any faster than nvidia-331).

Note that for hybrid Intel/Nvidia graphics I heard NOT to use nomodeset, so I did not use that when installing 14.04.1 to my laptop (older GTX 765m chip) and it works fine for either graphics with regular nvidia-331-updates.

I have not downloaded 14.10 or 15.04 yet, but if you can get them to install, you might try installing at least nvidia-331-updates from recovery boot, enabling networking (wait for it to return to menu if any errors) then root console.

---

### Post by ubunt72 on 2015-03-19
> **efflandt said:**
> Actually because nouveau did not support the Maxwell chip yet I was surprised that I did not have an issue with live/install iso of 64-bit 14.04.1 (I used nomodeset), but maybe that was using some other video method, because in the installed system I don't even think I could get the login screen (I know that I could not log into X) and when I tried the text console, as soon as I would login, it would flash the motd and immediately return to login prompt. Installing **nvidia-current** by enabling networking and going to root shell in recovery boot got me as far as login window, but still not X (logs showed that nvidia version did not support the card). Purging nvidia* and installing **nvidia-331** worked (**nvidia-331-updates** would be recommended). The main reason I purged that and went to **nvidia-346** from xorg-edgers ppa was to play around with video overclocking (which requires 337 or newer) (default speed is not any faster than nvidia-331).

Note that for hybrid Intel/Nvidia graphics I heard NOT to use nomodeset, so I did not use that when installing 14.04.1 to my laptop (older GTX 765m chip) and it works fine for either graphics with regular nvidia-331-updates.

I have not downloaded 14.10 or 15.04 yet, but if you can get them to install, you might try installing at least nvidia-331-updates from recovery boot, enabling networking (wait for it to return to menu if any errors) then root console.A wild guess, but 14.04 uses a much older kernel, 3.13.   14.10 uses 3.16 but I'm just speculating.  Perhaps, the Nouveau developers were not able to catch up to the latter kernels?   I dunno....

---

### Post by ubunt72 on 2015-03-28
Hi, I just want to follow up - for anyone who cares - that I tried the latest 15.04 beta-2 of Ubuntu MATE and everything on the live media worked - like a charm!  I was pretty happy! :)  I hope nothing changes - negatively, at least.   The only thing I couldn't do is install software - well, I guess that is not too shocking.   It was still live media.   I tried to install the Cinnamon desktop for fun, but it complained about an internet connection.   

I have reason to suspect, a proper install would be good.   I clicked Hardware - Additional Drivers - and it detected I have a gtx 750 and displayed that I was using x.org. -> nouveau driver.   I had the option to choose a few Nvidia driver choices - including the latest 346?   I think that's the latest?   Anyway, it was very encouraging.   The text looked fine - the correct size and resolution.   It would probably be even better with installing the latest nvidia (binary) driver if I wanted all the bells and whistles - 2d and 3d.   

So, something was fixed.   I hope it doesn't regress and that if I install this, I will have at least as good an experience.   I like the look of MATE and wanted to try a more traditional desktop.   I've been using GNOME and while I became used to it, it's still nice to use a typical desktop instead of the more mobile devices-type of DE.   That's why I was looking at either XFCE, MATE, Cinnamon and KDE (although, KDE never works with my android phone.).   I was able to connect no problem with my Android phone and view my pictures with no problem.   So, everything was configured properly - out of the box - which is another +1 for MATE!

---

