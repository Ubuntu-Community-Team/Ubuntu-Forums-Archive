---
title: "Photoshop CS2"
date: 2007-05-10
forum: General Help
---

### Post by Bubula on 2007-05-10
I looked in the forums to find whether someone has successfully run PS CS2 in 7.04, but couldn't find a positive answer.  Can this be really accomplished, with or without Whine(?), or should I not bother?

---

### Post by ironfistchamp on 2007-05-10
CS2 won't run without some compatibility layer like Wine. I am not sure how well CS2 works with Wine but it would be a good idea to check out the appdb.

[http://appdb.winehq.org/](http://appdb.winehq.org/)

HTH

Ironfistchamp

---

### Post by electricshoes on 2007-05-10
I heard that there is a Portable version of Photoshop around that will work in wine, but I have not tried this myself.

---

### Post by obviouslyshane on 2007-05-10
I tried to install CS2 in wine... Didnt work... It may just be my noobish skillz though...

---

### Post by Xeor on 2007-05-10
I installed Photoshop CS2 on Kubuntu with Wine. Managed to edit a picture and save it but as soon as I closed it it didn't want to start again.

To come that close to make it work (and yet so far...) I installed it on Windows XP, copied the directories in "Program Files" and somewhere else for the "Common Files" or something like that and put them respectively back in the Wine directories.

You also have to copy the "Registry" changes and put them in the Wine files.

A lot of work for not much, really :confused:

---

### Post by strabes on 2007-05-10
Another option is to to virtualize windows using something like virtualbox. I never use it but I have a working virtual windows with photoshop installed.

---

### Post by Bubula on 2007-05-10
Not sure how to send this to strabes, so this is probably "public."

I'm not sure what you're describing since I am very new to ubuntu, so could you please expand on your suggestion?  Running photoshop more quickly than I can get it to run in windows is my primary reason for looking into Ubuntu.  If I can't do that, then I'll stay with XP.  Thanks for your reply.  Same to everyone else.

---

### Post by k|d&lt;FuNkY&gt;FrY on 2007-05-12
> **Xeor said:**
> I installed Photoshop CS2 on Kubuntu with Wine. Managed to edit a picture and save it but as soon as I closed it it didn't want to start again.

To come that close to make it work (and yet so far...) I installed it on Windows XP, copied the directories in "Program Files" and somewhere else for the "Common Files" or something like that and put them respectively back in the Wine directories.

You also have to copy the "Registry" changes and put them in the Wine files.

A lot of work for not much, really :confused:

Delete ALL the .PSP files created here --> 

/home/YOU/.wine/drive_c/windows/profiles/YOU/Application Data/Adobe/Photoshop/9.0/Adobe Photoshop CS2 Settings

Yes, CS2 will install under Feisty, however, its functionality is very limited beyond that point.

---

