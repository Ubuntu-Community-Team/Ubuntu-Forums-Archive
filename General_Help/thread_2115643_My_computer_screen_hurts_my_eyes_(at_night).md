---
title: "My computer screen hurts my eyes (at night)"
date: 2013-02-13
forum: General Help
---

### Post by timbuck on 2013-02-13
If this needs to be moved, please do so.
I wasn't sure where to put this, but this  only happens at night, I look at my computer screen and it HURTS my eyes, like.... it's hard to explain, and I probably sound crazy, but I have the brightness on the lowest setting and that helps //*slightly*// but the colors them selves don't look correct

Also something strange I have noticed is if I look at my computer screen through a camera at night, everything else gets really orange, is this normal?

If anyone can PLEASE help me, my eyes burn, and I don't know what to do!!! :confused:

Edit  I was messin with my camera and found this thing called white balance and starting changing the settings, I made my room and all look about the same, and now when I look at my computer screen it's a light baby blue color.... um.... is there a way to fix this or is it okay to look at this blue screen at night?

---

### Post by oscillator on 2013-02-13
Try using flux or redshift as computer screens emit slightly blue light, but at night we usually have yellow lights (unless like me you have a daylight bulb) which apparently strains your eyes, so it's likely just that. 

Download either (whichever works) and it will change the colour output of your screen to match the light in your room depending on your longitude and latitude. 

Flux >>> [http://stereopsis.com/flux/](http://stereopsis.com/flux/)

Redshift >>> [http://jonls.dk/redshift/](http://jonls.dk/redshift/)

hope that helps.

---

### Post by timbuck on 2013-02-13
Thank you so much,
I think i'll try f.lux tonight, but which one do you recommend/ which one is easier / better in your opinion?

I'll bump this at night time to share my experience, thank you again, i've got redshift running now

---

### Post by timbuck on 2013-02-13
OMG!!! REDSHIFT IS AMAZING!!!!!!!!!!

Why is this not installed by DEFAULT????

THANK YOU SO MUCH !!!!!!!

:D

I use 
redshift -l -80:25 -t 6000:4700 -g 0.8 -m vidmode -v
it's AMAZING
after a while I will disable it and see what it's like for everyone else who doesn't use this, get ready for some big capital letters!!!

---

### Post by Stonecold1995 on 2013-02-13
I also installed this, but it makes the screen *too* red for my eyes to adjust well.  Is there any program like this which uses the webcam to more accurately adjust the screen color so it can compensate for room's lighting, instead of guessing the ambient light based on location?

Or should I make a separate thread?

---

### Post by timbuck on 2013-02-13
Please use the command in my post above and I don't think it will be near as red
or '''redshift -o 4800 '''' w/o the quotes

Yeah this (webcam detect lighting) has been suggested for a program called f.lux -- the program that inspired redshift
and the developers of f.lux say it's hard to do and requires a lot of work

You may like f.lux better
If you have i386 or ia32 libraries installed then check out f.lux
[http://stereopsis.com/flux/linux.html](http://stereopsis.com/flux/linux.html)
When you do the commands, open f.lux and fill in ALL information
Select flourecent and press closu

Please.wait 2 minutes at least

If your screen does not change in 3 minutes do the following
Open a terminal
Type
fluxgui 
Hopefully this will return 'fluxgui already running, exiting'
If so type

**[COLOR="red"]EDIT [/COLOR]**
xflux -h
You will need to enter location either by US zipcode or lat : lon
for US zipcode
xflux -z 01234 -k 3700
For lat lon 
 xflux -l latitude -g longitude -k temperature (eg. 2700)
xflux -l 30 -g -80 -k 3400 or try 3700 b/c 2700 will be way too orange for most

xflux is much more accurate than redshift, but redshift is open source and has more features

If you need any help I'd be glad to assist you

---

### Post by offgridguy on 2013-02-13
Very interesting thread, Thank you.

---

### Post by timbuck on 2013-02-13
That's the FIRST time I've read a response like this to a thread of this topic haha
Your welcome

If you need help as well all you gotta do is click / tap that reply button and ask:popcorn:

---

### Post by timbuck on 2013-02-14
OUCH OMG I JUST DISABLED F.LUX ON MY iPad yes you can get it on jailbroken idevices
It's not terrible but it just looks COMPLETELY un natural!!!

Enabled again ahhhh SO much better, very relaxing as well
I mean who ( excluding pc coders ) uses a computer late at night haha

I feel terrible for anyone that doesn't at least TRY f.lux / redshift
 at least a few times if you don't like it the first time 

Alright I'll answer any replies in the morning, you all enjoy!

---

### Post by SeanBlader on 2013-02-14
I don't want to rain on your parade, and I'm glad you found something that helps, but did you think about maybe getting away from the screen a bit? Everything in moderation you know?

---

### Post by timbuck on 2013-02-14
Yeah I do
I take short breaks every now and then, thanks for the suggestion!

Does anyone else use redshift?

---

