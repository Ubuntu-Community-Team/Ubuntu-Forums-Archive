---
title: "Changing the dollar sign $ to rupee sign &#8377; in the keyboard layout"
date: 2012-11-29
forum: General Help
---

### Post by igodspeed on 2012-11-29
Hello All,

Here is my question. I am using a dell laptop with US keyboard layout. I was wondering if it would be possible if i could change just the dollar sign $ to &#8377;. This is an indian rupee, more information could be found here: [http://font.ubuntu.com/rupee/](http://font.ubuntu.com/rupee/)

What i would like is a permanent solution, so every time i press shift and 4 the rupee sign should appear instead of the dollar sign however i would like the other keys to remain unchanged. I have tried with the keyboard layout and under ADDING A CURRENCY SIGN selecting RUPEE ON 4 but that does not seem to work. Please advise. Any help would be very appreciated.

---

### Post by pkadeel on 2012-11-29
> **igodspeed said:**
> Hello All,

Here is my question. I am using a dell laptop with US keyboard layout. I was wondering if it would be possible if i could change just the dollar sign $ to &#8377;. This is an indian rupee, more information could be found here: [http://font.ubuntu.com/rupee/](http://font.ubuntu.com/rupee/)

What i would like is a permanent solution, so every time i press shift and 4 the rupee sign should appear instead of the dollar sign however i would like the other keys to remain unchanged. I have tried with the keyboard layout and under ADDING A CURRENCY SIGN selecting RUPEE ON 4 but that does not seem to work. Please advise. Any help would be very appreciated.
Other than the solution you have already tried, permanent solution is to modify the xkb symbols file and replacing dollar sign with rupee sign. If you are willing to do that, post the image of you keyboard layout dialog or post the exact Layout name you want to change which is visible in the dialog like the one in attached image.

---

### Post by igodspeed on 2012-12-03
> **pkadeel said:**
> Other than the solution you have already tried, permanent solution is to modify the xkb symbols file and replacing dollar sign with rupee sign. If you are willing to do that, post the image of you keyboard layout dialog or post the exact Layout name you want to change which is visible in the dialog like the one in attached image.

Thanks for the reply. As requested i have attached screenshot of my keyboard layout. I would like to permanently change my keyboard. i am running windows also, i hope this does not change the key behaviour in my windows partition. Thanks for your help

---

### Post by pkadeel on 2012-12-03
> **igodspeed said:**
> Thanks for the reply. As requested i have attached screenshot of my keyboard layout. I would like to permanently change my keyboard. i am running windows also, i hope this does not change the key behaviour in my windows partition. Thanks for your help
The image size you posted is quite small and I could not see the keys in the layout image however the layout you are currently using appears to be "English (US)"

Now open the terminal and enter (gedit is default text editor on ubuntu but you can change it with other text editior if you like.)
```

gksu gedit /usr/share/X11/xkb/symbols/us

```A file will open and you will change the "dollar" with "0x10020b9" as shown in the attached images. Then save the file. Change will be effective after you reboot the system. This change will only affect your current ubuntu installation and will no affect windows.

---

### Post by Vaphell on 2012-12-03
i don't think getting rid of $ is a smart idea. It's rather important character in terminal, regexes and scripts require it.

---

### Post by Peter Maunder on 2012-12-03
I was able to add a Rupee sign to go along with the € (EURO) which is already configured on my keyboards. Euro U+20AC as opposed to the new Rupee U+20B9

I just gave a small test with my Acer netbook running Linux Mint Mate 13, which has an American Keyboard. Normally I use a € sign on Alt Gr 5 below the the % sign. I added a Rupee sign on Alt Gr 4(below the $) using the keyboard settings. 

  Keyboard Settings > Preferences > Choose the Keyboard  > Options
  Adding currency signs to certain keys > Rupee on 4
  Logoff, Logon again to activate the keyboard.

I have the similar options on this system except that it is a full English (British) keyboard and I thought it was better to try a genuine American keyboard.

I agree that you should not change the $ (dollar sign) to something else. 

This assumes that you have an At Gr or its equivalent.   

Good luck

---

### Post by igodspeed on 2012-12-03
Thanks a lot for your help. It worked!!!&#8377;&#8377;&#8377; I can always change it back if there is a need for the dollar sign.

---

### Post by igodspeed on 2013-05-01
Hi,

I have bought another laptop and this time it is a Gateway  NE56R. There are bunch of keys which work in windows with gateway  sotware installed but does not work when i have ubuntu running. For  example there are there euro and Dollar sign under shift key and next to  above key. Is there a way i can get the dollar key to change here to  rupee key. I am not able to find the code such as 0x10020b9 not do i know where to paste it in  gksu gedit /usr/share/X11/xkb/symbols/us. Kindly please let me know how i can go ahead and modify the functions of these keys so i can use them with Ubuntu.
Please see the link for how the keyboard looks like. [https://www.google.co.in/search?q=Acer+Gateway+NE56R&client=ubuntu&hs=zjD&channel=fs&tbm=isch&tbo=u&source=univ&sa=X&ei=yBaBUd62HcmJrQfRxYCwBA&ved=0CDAQsAQ&biw=1366&bih=643#imgrc=c8YdYIOjf-yT6M%3A%3BWp-FugFPqHJ3GM%3Bhttp%253A%252F%252Fwww.gogi.in%252Fwp-content%252Fuploads%252F2012%252F08%252FGateway-NE56R02I-NE56R14I.jpg%3Bhttp%253A%252F%252Fwww.gogi.in%252Fgateway-ne56r02i-ne56r14i-ne-series-laptop-features-price.html%3B500%3B350](https://www.google.co.in/search?q=Acer+Gateway+NE56R&client=ubuntu&hs=zjD&channel=fs&tbm=isch&tbo=u&source=univ&sa=X&ei=yBaBUd62HcmJrQfRxYCwBA&ved=0CDAQsAQ&biw=1366&bih=643#imgrc=c8YdYIOjf-yT6M%3A%3BWp-FugFPqHJ3GM%3Bhttp%253A%252F%252Fwww.gogi.in%252Fwp-content%252Fuploads%252F2012%252F08%252FGateway-NE56R02I-NE56R14I.jpg%3Bhttp%253A%252F%252Fwww.gogi.in%252Fgateway-ne56r02i-ne56r14i-ne-series-laptop-features-price.html%3B500%3B350)

Warm Regards

---

### Post by pkadeel on 2013-05-01
The keys you are asking about are special keys specific to Gateway meaning it is their propietry layout. I think your best bet will be to look for a linux driver for this keyboard. I guess ubuntu will be using a generic keyboard layout which does not contain these special keys unless ubuntu has a builtin capability to identify these two keys you are asking for.

---

