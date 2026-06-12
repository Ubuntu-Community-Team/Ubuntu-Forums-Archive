---
title: "Ati 9250 and OpenGl"
date: 2006-10-02
forum: General Help
---

### Post by divineleft on 2006-10-02
I have an Ati Radeon 9250, and installed it using [this]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") guide. Everything works, except I noticed that it's kind of slow. I have 3d acceleration but the windows lag when I minimize or move them. I checked my drivers and found that my opengl version is 1.3.

> justin@linux:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 Series DDR Generic
OpenGL version string: **1.3.1091** (X4.3.0-8.28.8 )

All of the drivers are new, I got them right off of the ati site and there were no problems in the installation, so I was wondering: Is there any way to fix this so my opengl version is 2.0?


Also - I think it would be worth mentioning that I installed it using 8.28 because ati removed 9250 support in their latest driver (8.29), but I'm almost positive that they had opengl 2 in their drivers before.

---

### Post by divineleft on 2006-10-02
Looks as though the problem is fixed with the generic drivers on edgy, but it would still be nice to know so that I don't have to deal with this for the next 20 days.

---

