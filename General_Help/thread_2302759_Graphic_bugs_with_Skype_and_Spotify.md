---
title: "Graphic bugs with Skype and Spotify"
date: 2015-11-13
forum: General Help
---

### Post by Jedit Ojanen on 2015-11-13
Hi,

I've installed Ubuntu 14.04 on my laptop. When I use Skype and/or Spotify for long enough time (few hours) the graphics start to fail and I'm unable to use the programs. I have NVidia graphic card and I've tried both graphic drivers propieatry NVIDIA and Nouveu X.Org but I got the same problem with both of the drivers. I don't know much more about the grapchic card I'm using but the laptop is about 3 years old. I've tried to find solution to my problem by Googling without luck. It would be very nice to get a solution for this problem because I need Skype in daily basis at my work and all I can use now is web Skype but I can't receive files and it has it's faults like not all the group chats are visible etc.

Edit: I was thinking of adding a screenshot but it seems not to be possible. Anyway, I'm trying to describe the graphic bugs. Sometimes the contact list of Skype goes all messy. Like all the contact names are stacked on top of each other and you can try to imagine what it looks like when dozens of names are written on top of each other, Sometimes the contact list looks just fine but the chat window is almost fully grey and there is just small spot at the middle of the window where the graphics are fine and you can see little bit of the chat text there. Hope this helps.

---

### Post by Jedit Ojanen on 2015-11-17
Thank you for all the help :(

---

### Post by Jedit Ojanen on 2015-11-18
Okay, could someone give me info where to get support or help?

---

### Post by mcparty2 on 2015-11-18
I have not had any issues with either programs on my laptop using Ubuntu 14.04.
Spotify is a bit buggy I have found but nothing I haven't been able to work around. It might be worth checking out their forums.
To me it sounds like a graphics card issue if its occurring in two different pieces of software (funnily both bits of software are designed primarily for Windows users so it may be a translation issue)

In the meantime have you checked an lspci and see if the Graphics card is loaded correctly (i am assuming so) also is it possible you check /var/log/syslog and see if you are getting any errors at the time the problems occur... this might tell you where the problem is.

Thanks

---

### Post by Jedit Ojanen on 2015-11-19
Hey, thanks for the reply. I can't tell if my graphic card is loaded correctly but here is all the info for the graphic card I can find with lspci command:

VGA compatible controller: NVIDIA Corporation GF108GLM [NVS 5200M] (rev a1)

I checked /var/log/syslog when I opened Skype but my system didn't write anything new in the log. I think it's not possible but could desktop environment have something to do with the problem? I'm using default Unity at the moment and I installed brand new installation of Ubuntu 14.04 just couple of weeks ago. I've not done any drastic changes to my OS since the installation. All I have done is install couple of basic software like Skype, Chrome, Spotify etc. I have updated all the software and I'm using the newest tested proprietary drivers from NVidia. If changing desktrop environment could help I would definitely do so because I would need Skype at my work very badly.

---

