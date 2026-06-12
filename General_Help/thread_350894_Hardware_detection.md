---
title: "Hardware detection"
date: 2007-02-01
forum: General Help
---

### Post by Dubstar_04 on 2007-02-01
How come Ubuntu 6.10 doesn't recognise my hardware properly? 

I have tried ubuntu on 4 of my pcs and the video drivers are normally wrong. One of them was ok, eg when i scrolled in firefox it actually scrolled instead of labouring to redraw every roll of the mouse scroller!! However when I Install mythtv the video is terible and really jerky. I know the hardware is upto the job because when i installed mythdora it worked fine and the tv quality was excellent!! 

You are probably wondering why I don't just stick with mythdora? 

The truth is I'm not every keen on it and i much prefer ubuntu, Probably because i've spent the last few months using ubuntu and learning how to use things like the command line, and i feel quite comfortable, so much that I have managed to get mythtv installed and almost fully functional. 

I just could do with some dircetion and advise to help me sort this problem, so please could anyone help me with this??

Regards,

Dubstar_04

---

### Post by pseudonym on 2007-02-01
What sort of video card do you have? Xorg can still have problems with hardware detection, unfortunately. You usually have to run 'sudo dpkg-reconfigure xserver-xorg' and choose the appropriate driver.

Also, if you have an nvidia card, you should probably use the binary driver from nvidia.com if you aren't already. Video performance in mythtv will be a lot better with it. The 'offical' guide on it is [here]("http://albertomilone.com/latest_nvidia_udsf_edgy.html").

---

### Post by Dubstar_04 on 2007-02-01
Hey pseudonym,

 Thanks for the reply. The card is an on board grahpics 'savage by s3' I have already reconfigured x and tried both the s3 and savage driver. This is what I don't understand!!

Could it be a problem with rights? Because when you install mythtv it creates a mythtv user but I can't find this user anywhere. What i mean by this is that when i go to the log in screen to try and try to make the mythtv user auto login there is no mythtv user availible, but if i try and add a mythtv user it tells me that there is already a user by that name??

The effect that I get is kind of what I would expect to see from a low powered processor, like the video lumpy and speeds up and down, but like i say it works with mythdora so its obviously a config problem!!  Really annoying all the same!!

Whats more annoying is that I bought a nvidea fx 5200 graphics card but the agp slot on the motherboard is goosed, along with the ps2 plugs so, i will have to buy a new motherboard before I start using mythtv properly!!

I have also tried altering the decoders in mythtv along with the deinterlace settings but non of that made any difference!!!

Why do problems always have to be something so small you can't find it???

If anyone can offer any advice i would be grateful!!

---

