---
title: "Lubuntu 12.04 pictures, videos, dvd, etc in negative colors."
date: 2016-01-11
forum: General Help
---

### Post by antonymous2 on 2016-01-11
Hello, I've installed lubuntu 12.04 in my old Toshiba Satellite M30 . It works rather well, but the you tube videos, pictures and dvd show negative colors.I'm a beginner in ubuntu, can anybody help me please?
 Thanks a lot.

---

### Post by ajgreeny on 2016-01-11
Your attached pics are too small to be certain, but neither of them appear to be negative colours.

You also seem to have shown us thumbnails only rather than full images, and the small square one does not even open when clicked.

Add images by clicking on the paperclip in the toolbar of the advanced reply box (it is not available in quick reply) browse to the image on your hard drive, double click it to add it, then click Upload button.

---

### Post by antonymous2 on 2016-01-11
Here two, thanks.

---

### Post by mörgæs on 2016-01-12
I think that the pictures look fine. 
More important is that 12.04 is out of support. Better to do a fresh install of 15.10.

---

### Post by ajgreeny on 2016-01-12
> **mörgæs said:**
> I think that the pictures look fine. 
More important is that 12.04 is out of support. Better to do a fresh install of 15.10.
^^^+1
No negative pictures shown here either; they look good to me.  Could this be a local display problem of your monitor or something similar?

Whilst 15.10 is a good version, it is an intermediate version only and will run out of support again in 6 months; if you prefer to stick with the 5 year support of LTS versions, try 14.04 instead.

---

### Post by mörgæs on 2016-01-12
Three years in this case. The very reason that people should abandon Lubuntu 12.04 :-)

---

### Post by antonymous2 on 2016-01-12
My PC has 512mb and 40gb, do you think it will work?

---

### Post by antonymous2 on 2016-01-12
Anyway I'll try it. Thank you.

---

### Post by XBNCPRk on 2016-01-12
I think its a bit of a stretch to hope that ~12 year old hardware will run 14.04 but best of luck to you. A cursory search though indicates that 2gb RAM (the max for that laptop) has a cost of about $25 USD from amazon or newegg, so if you are able to boot from a live cd or usb and are firm in your decision to stick with that laptop, it may be a very worthwhile upgrade for you.

Before doing anything else though, you might want to try plugging in an external montior to see if the problem is caused by dying hardware. IIRC Toshiba didnt have the greatest of luck with the caps on their lcd power inverters back in the day.

---

### Post by mörgæs on 2016-01-12
> **XBNCPRk said:**
> I think its a bit of a stretch to hope that ~12 year old hardware will run 14.04

No, within the Lubuntu family 12.* , 14.* and 15.* are more or less equally heavy.

---

### Post by antonymous2 on 2016-01-13
The 15.10 installation returns a code error:
[  205.616028] i2c i2c-1: sendbytes: error -110

---

### Post by mörgæs on 2016-01-13
You have to post much more information.

What happened before the error?
Were you able to run a live boot? (probably not)
Have you tried the [alternate installer]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")?

---

### Post by antonymous2 on 2016-01-13
I'm sorry, you're right. It's an alternate installation using forcepae and the error is shown at the boot. It doesn't work of course. I'm trying the minimal installation right now.

---

### Post by mörgæs on 2016-01-14
Good, let's see if it's able to run a command-line only system based upon the minimal installer. 
When that works we can take a look at the GUI.

---

### Post by antonymous2 on 2016-01-17
Hello again, I"ve read your old hardware thread and tried to install 15.10 with forcepae, nomodeset, vga, etc... without success with the graphics. After that I was uncapable of install it again, always started in tty mode. I supose I did something wrong because I tried 14.04 and always boot in the tty mode. Some advise please.

---

### Post by mörgæs on 2016-01-18
> **antonymous2 said:**
> without success with the graphics. 

As you can see above my recommendation was to forget about graphics for now. The first task is to install a command-line only system. 

> **antonymous2 said:**
> Some advise please.

You've already got.

---

