---
title: "Wine not recognizing Drives"
date: 2008-04-19
forum: General Help
---

### Post by DesolationUSA on 2008-04-19
Firstly, I'm very new to both linux and wine so please bear with me.  I'm trying to use DVD43 and 1 Click DVD Copy Pro.  Neither of which seem to be able to auto detect either of my dvd drives (one internal, one external) I tried adding drives into the wine config and so forth but to no avail.  My internal is an option under with the drives section within Wine config but for what ever reason it's not making the connection to the programs.  Any help will be greatly appreciated! Thanks for reading.

---

### Post by ibuclaw on 2008-04-19
The mount points should be
```
/media/cdrom0
```
and
```
/media/cdrom1
```
Respectively.

On a word about the WINE apps.

DVD43 is dubbed as being [garbage]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9020").
ie: Does not function in WINE. (be it uses a special windows driver to use the CD-Rom drives that isn't supported, etc,etc.). My general understanding is that WINE does not support Windows Driver Emulations (It lets Linux handle the hardware), so apps looking to run a Windows Driver will not work indefinately.

And 1 Click COPY appears to be working for me.
At, least, the app has extracted the image and saved it to my ~/.wine/drive_c folder.

Check the attachment for proof.

Also, have you tried any Native Linux apps?
As there are plenty out there then can do just as well or better than Windows based apps.

Regards
Iain

---

### Post by ibuclaw on 2008-04-19
I don't have any DVDs with me, so I don't know whether or not it will burn the image.

But here is a screenshot of the app and my DVD drive is displayed in the dropdown box as shown.

My DVD drive even ejected once the rip process was process was complete!
Gave me a shock :)

My version of WINE is 0.9.60 by the way.

You can get it from their [website.]("http://www.winehq.org/site/download-deb")

Regards
Iain

---

### Post by DesolationUSA on 2008-04-21
I'm not sure what to do with the codes you provided, but I've included a screen shot of the error message from 1 Click DVD Copy and a screen shot of the drives tab in my wine config.

---

