---
title: "IrfanView: How do I make this the default viewer"
date: 2007-04-16
forum: General Help
---

### Post by Killimor on 2007-04-16
Running Ubuntu 6.10.   I have installed Wine  and I have installed IrfanView.

But how do I configure my system so that, when I click on an image file, it will automatically open in Irfanview?


At the moment, I have to go through the convoluted process of opening IrfanView first , and then File>Open and navigate to the folder where the image is stored.

I simply want to click on the image itself and have it open in IrfanView.

I have searched and found nothing that will give me a step by step guide on what I need to do.

Thanks,
Killimor

---

### Post by Magnes on 2007-04-16
Maybe set the image to open with command in Nautilus (right click on image, open with):

wine /path-to-infran-view/InfranView.exe

I don't know if it'll work (I don't have Ubuntu at work) but it's worth a try.

---

### Post by Killimor on 2007-04-17
I done exactly as you described. 

After right-clicking an image file, I worked my way through the Open With option and set up a custom command:

wine '/home/killimor/.wine/drive_c/Program Files/IrfanView/i_view32.exe'

Now, when I click on an image, IrfanView starts up but the image itself is not loaded.  I still have to go through the process of File>Open... etc.

So, I am a bit further forward, but how do I go the extra step and get IrfanView to automatically load the image?

---

### Post by aussiedini on 2007-04-17
Try putting %f after the command. In Nautilus that opens the file your are clicking.

---

### Post by Killimor on 2007-04-17
OK,  I tried the following custom command:

wine '/home/killimor/.wine/drive_c/Program Files/IrfanView/i_view32.exe' %f

But now, after clicking on an image file, nothing at all appears to happen.  IrfanView doesn't even fire up!!

So, what to do next??

---

### Post by david_kt on 2007-04-17
Follow below step:

```
gedit ~/.wine/IrfanView
```

Copy and paste below code:

```
#!/bin/sh 

QUICKPARLOCATION="c:\\Program Files\\IrfanView\\i_view32.exe"
PARAM=`winepath -w "$*"`
wine "$QUICKPARLOCATION" "$PARAM"
exit 0
```

and save the file.

Make sure it is it is executable:

```
chmod +x ~/.wine/IrfanView
```

After you completed this go to an image file right click it, properties, go to the &#8220;open with&#8221; pane, click add, paste '/home/killimor/.wine/IrfanView' in the command line and select the radio bullet.

After that try to double click any image file.

DK

---

### Post by Killimor on 2007-04-17
Wow!!!  That's brilliant mate.  Works just like I want it to!!  

Can't say that I understand a word of the coding in the IrfanView executable, but it does the business :) 

Thanks tremendously for your help.

Killimor

---

