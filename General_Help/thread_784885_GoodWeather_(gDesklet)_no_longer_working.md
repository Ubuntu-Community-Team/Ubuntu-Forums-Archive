---
title: "GoodWeather (gDesklet) no longer working"
date: 2008-05-06
forum: General Help
---

### Post by clyde9999 on 2008-05-06
The gDesklet, "GoodWeather" is no longer working, the url it uses is a listed in "__init__.py" 

""http://xoap.weather.com/weather/local/" \
"%(weather_code)s?cc=*&dayf=5&prod=xoap&" \
"par=1003832479&key=bb12936706a2d601"

I have noticed that the "screenlet" whether widget had changed also, and it too uses the weather.com http. It was solved. I already tried the same source, but must not know enough about it because I had no result. 

:popcorn:Hope someone can give some advice, and thanks in advance for it..

Jack

---

### Post by jordon on 2008-05-07
I found the answer in [this thread]("http://ubuntuforums.org/showthread.php?t=784053").

In short, just add "link=xoap&" after "prod=xoap&" in the URL. Save the file, restart gDesklets, and it should work.

---

### Post by Pelo1968 on 2008-05-07
fixed it for me,  but I only get a 4day forcast now. can't get more ( 5 if you count "today")
Anyone else getting that ?

---

### Post by Dagahk on 2008-05-07
Mine is fine, it worked what Jordon told.
Thanks :)

---

### Post by clyde9999 on 2008-05-07
Weeeeeee, it worked. Thanks so much!!!!

---

