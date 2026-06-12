---
title: "Format Junkie Won't Convert"
date: 2014-05-31
forum: General Help
---

### Post by computer3 on 2014-05-31
I just installed Format Junkie on Ubuntu 14.04 and I'm trying to convert a .mp4 file to .avi and it just stays on 0% and doesn't convert. Has anyone else had this problem and is there a way to fix it? 

BTW, I'm a new Linux user (just over a month now) and besides this little glitch I'm actually loving it. It took a week to get over the new OS shock, but I don't see myself going back to Windows ever again.

---

### Post by bapoumba on 2014-05-31
From here : [https://launchpad.net/~format-junkie-team/+archive/release](https://launchpad.net/~format-junkie-team/+archive/release)
> This is the official PPA for the Format Junkie.

This PPA currently has support for Precise, Quantal, and Raring. It does not have support for any other releases.

So that may be why it is not working..

---

### Post by computer3 on 2014-05-31
> **computer3 said:**
> I just installed Format Junkie on Ubuntu 14.04 and I'm trying to convert a .mp4 file to .avi and it just stays on 0% and doesn't convert. Has anyone else had this problem and is there a way to fix it? 

BTW, I'm a new Linux user (just over a month now) and besides this little glitch I'm actually loving it. It took a week to get over the new OS shock, but I don't see myself going back to Windows ever again.

LOL. Problem solved.

---

### Post by bapoumba on 2014-05-31
> **computer3 said:**
> LOL. Problem solved.

Ah, good, but a little more info for others who might run into the same question would be useful :)

---

### Post by computer3 on 2014-05-31
I just meant by problem solved is that the whole problem was that I was using a program that doesn't work on 14.04. I'm still trying to find a way to convert the video.

---

### Post by bapoumba on 2014-05-31
Ah, I guess mencoder is what you need then : [https://help.ubuntu.com/community/MEncoder](https://help.ubuntu.com/community/MEncoder)
mencoder is in universe, and you will need the ubuntu-restricted-extras.

---

### Post by computer3 on 2014-05-31
> **bapoumba said:**
> Ah, I guess mencoder is what you need then : [https://help.ubuntu.com/community/MEncoder](https://help.ubuntu.com/community/MEncoder)
mencoder is in universe, and you will need the ubuntu-restricted-extras.

Thanks. I'll give it a try.

---

