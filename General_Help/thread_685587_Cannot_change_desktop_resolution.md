---
title: "Cannot change desktop resolution"
date: 2008-02-02
forum: General Help
---

### Post by Coralin on 2008-02-02
Hello;
I recently did a fresh install of Gutsy, and am loving it, except for one problem-
I can't get my resolution to change. I open the System>Preferences>Screen Resolution window, change the resolution in the dropdown from 1600x1200 (my monitor's maximum resolution, and the one that Ubuntu has decided is the one it likes best...) to 1280x1024... and nothing happens. I click OK, the desktop does a really fast little flicker... and nothing has happened. Go back into the window, and the resolution SAYS 1280x1024, but nothing has changed. Restarting still brings me into 1600x1200. 
I'm running an NVidia GeForce 7600; I believe I'm using the proprietary drivers. Switching doesn't seem to change anything.

---

### Post by dexter on 2008-02-02
Try removing all references to the 1600x1200 resolution in xorg.conf, so that 1280x1024 is the maximum resolution. 

Keep in mind it would be wise to create a backup first.

---

### Post by earobinson on 2008-02-02
```
sudo nvidia-settings
``` should let u edit your settings.

---

### Post by Coralin on 2008-02-02
Dexter- I'm not quite sure how to do that; I'm still really new at Linux in general.

earobinson- I just tried that; whenever I change to another setting and hit apply, I get an error message similar to this one: 

```
Failed to set MetaMode (5) 'CRT-0: 1024x768 @1024x768 +0+0' (Mode 1024x768, id: 54) on X screen 0

Would you like to remove this MetaMode?
```

---

### Post by myland on 2008-05-31
Hello,
I very new to Ubundo and I have upgrade to the 8.04. It was running very good until I went to setup the e-mail and then I notice that the resolution was to big and I could not do anything. I found your Post. I printed something it but it was cut off. I login and I'm not sure what to when I did what I was too. I see the xorg.conf below in the post. after you login in dos are suppose to type xorg.conf and then what do I do next? Sorry but real new at this. My co-worker told me that I would have figure this out myself. 
This a computer that I'm testing and it is at work. So I hope someone will post something back by Monday.
Thanks,
Tom

---

### Post by Victormd on 2008-05-31
I'm not sure what you're trying to do but, if you go to SYSTEM>PREFERENCES>SCREEN RESOLUTION and can't change to the resolution you want, here are a few things you can try...
go to SYSTEM>ADMINISTRATOR>HARDWARE DRIVERS and see if the proper graphics card driver is installed. BTW, what's your graphics card?
If it's not marked, then mark it and reboot... If it's marked and you want to edit your xorg.conf, open the terminal window and type (or copy and paste)
```
sudo gedit /etc/X11/xorg.conf
```
and your xorg.conf file will open and you'll be able to edit the lines you want to. I'm assuming you've gone through this post and found what you need... if not, just post back and we'll be happy to help. Some information you might want to post back:
1. graphics card make and model
2. copy and paste your xorg.conf file here...

good luck

---

### Post by myland on 2008-05-31
Thank you,
The other thing I might have compounded my problem to but you know where you have so many letters in a inch. I think I might have mess that up too. I was looking for late this afternoon and I could not find it and also what is the default setting for that. when I first went into it was set 97 but I don't know what is correct. 

I will keep this and try it on Monday. I think you have help me. I want know until Monday but I think this might no it. Again thanks,
I will let you know on Monday. 
Tom

---

