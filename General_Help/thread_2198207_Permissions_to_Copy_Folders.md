---
title: "Permissions to Copy Folders"
date: 2014-01-07
forum: General Help
---

### Post by wrichtmyer2 on 2014-01-07
I decided to dig out my old Mac HDD and plugged it in via USB. I tried to access it by live booting the latest version of Ubuntu, but I got the error 'You do not have the permissions necessary to view the contents of "Pictures". I am running Windows 8 on the drive I'm copying to.

I looked at an old thread, and tried to chmod and then cd, but my knowledge isn't the best, as I haven't used Ubuntu recently. 

The location in grabbing from is: /media/ubuntu/Macintosh HD/Users/wrichtmyer/Pictures

The location in copying to is: /media/ubuntu/CC88FA3C88FA249C/Users/William/Desktop/From_Mac

There may be an issue with the space in the grabbing from location, as there is a space between Macintosh HD, and Ubuntu messes up with that. 

Thanks!

---

### Post by jeanjd63 on 2014-01-07
Hello 
The good command seems to be :
**sudo  cp  "[COLOR=#000000]/media/ubuntu/Macintosh HD/Users/wrichtmyer/Pictures"   [/COLOR][COLOR=#000000]/media/ubuntu/CC88FA3C88FA249C/Users/William/Desktop/From_Mac[/COLOR]**

---

