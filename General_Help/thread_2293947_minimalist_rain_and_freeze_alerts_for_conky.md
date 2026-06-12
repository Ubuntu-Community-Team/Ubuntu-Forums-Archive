---
title: "minimalist rain and freeze alerts for conky"
date: 2015-09-08
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2015-09-08
I want to put something in conky that will not show anything unless the probability of a rain or freeze in the next 24 hours reaches some threshold, let's say 40% - and then when that condition is fulfilled to show the time at which the event becomes likely. Or something approximately like that.

I am looking for a way that makes minimal demands on system resources and internet bandwidth, maybe a script that runs once every 3 hours until it finds a probability of rain or freeze and then checks more frequently as the predicted time draws nigh.

Everything I've found either can't be made to do this or does it very wastefully, downloading and discarding a great deal of information that I'll then have to filter somehow.

Any suggestions would be appreciated. Thanks for reading.

---

### Post by CantankRus on 2015-09-08
Above my level of expertise but you would probably need to use a free weather api
and be able program for it.
[**_[COLOR="#B22222"]top-10-weather-apis[/COLOR]_**]("http://www.programmableweb.com/news/top-10-weather-apis/analysis/2014/11/13")

---

### Post by Dreamer Fithp Apprentice on 2015-09-09
Thank you, CantankRus. That's quite an article. Despite having included "API" and "machine readable" in various searches I had only found a couple of those listed. So that is both interesting and potentially helpful.

 I've made a little progress. To avoid having to download a bunch of images, flash videos, and sound files, even when accessing a web page intended for humans to read, I'm trying "lynx -dump http://joesweatherforcasting.com/mybackyard" (url is a fictional example) or the same command with  w3m instead of lynx. That seems to work. But if I can find a real API that's free and that I can figure out how to parse, that should be a lot more reliable.  A lot of these kind of things seem to be xmls, which is probably better for somebody who knows xml magic, but are hard to manipulate with the tools I halfway understand, like grep, sed, and cut.

---

### Post by Habitual on 2015-09-09
Isn't  wunderground a free-ish (need to reg, get 'key') API?

---

### Post by CantankRus on 2015-09-09
> **Dreamer Fithp Apprentice said:**
> Thank you, CantankRus. That's quite an article. Despite having included "API" and "machine readable" in various searches I had only found a couple of those listed. So that is both interesting and potentially helpful.

 I've made a little progress. To avoid having to download a bunch of images, flash videos, and sound files, even when accessing a web page intended for humans to read, I'm trying "lynx -dump http://joesweatherforcasting.com/mybackyard" (url is a fictional example) or the same command with  w3m instead of lynx. That seems to work. But if I can find a real API that's free and that I can figure out how to parse, that should be a lot more reliable.  A lot of these kind of things seem to be xmls, which is probably better for somebody who knows xml magic, but are hard to manipulate with the tools I halfway understand, like grep, sed, and cut.

Isn't the usual method to download the web page html source to a text file using wget or curl
and then sed grep awk the info you want.
No flash, images etc are downloaded.
All you get is the same as what you see when you view the page source in firefox.
eg
```
curl --retry 3 "http://joesweatherforcasting.com/mybackyard" > joesweather.txt
```

---

### Post by Dreamer Fithp Apprentice on 2015-09-25
Thank you, gentlesapients. Sorry I'm tardy. I wasn't expecting more replies. 

I got something halfway working with the approach I mentioned. Wunderground I tried once and abandoned that approach for reasons I forget. Somewhere in the process I managed to add myself to their mailing list. I'll look at it again. About curl, I didn't realize it could do that.  I'll try that next.

---

### Post by CantankRus on 2015-09-25
I create my own weather conky by downloading local sites using curl.
I prefer to do this because conditions are more accurate than the common weather sites used by most.
eg this is a script which downloads various local sites and is run periodically through conky.
```
#!/bin/bash

curl --retry 3 "ftp://ftp2.bom.gov.au/anon/gen/fwo/IDW12300.txt" > ~/conky/curl/bomforecast.txt

curl --retry 3 "http://www.bom.gov.au/wa/observations/perth.shtml" | sed s'/[<>]/ /g' > ~/conky/curl/bomtemp # []brackets in sed mean "any one of". Replaces < or >  with a space

curl --retry 3 "http://www.srosurf.com" | sed -e :a -e 's/<[^>]*>//g;/</N;//ba' | sed 's/&nbsp;/ /g' | sed 's/Support your local shaper, support your local surf shop.//g' > ~/conky/curl/surfreport.txt

curl --retry 3 'http://www.transport.wa.gov.au/imarine/coastaldata/tidesandwaves/stampgif_dg.asp?gfx=RDW_POLD' > ~/conky/curl/rottoswell.gif

curl --retry 3 "ftp://ftp2.bom.gov.au/anon/gen/fwo/IDW11400.txt" | tr "\r" " " | sed -e :a -e 's/<[^>]*>//g;/</N;//ba' > /home/glen/conky/curl/swell.txt
```

As you can see in most of the curl commands I strip out html tags using sed before sending it to a text file.

Then I try various awk sed grep etc commands in terminal to get the info I want from the text file.
Once I find a command that works I ceate a conky line.
eg To show my forecast max temp.
```
Max: ${execi 3600 cat ~/conky/curl/bomforecast.txt | grep "City Centre" | awk '/City Centre/ && /Max/{print $(NF)}' | head -1}°C
```

I know very little coding and just google sed/awk commands.
You can also strip html tags using the application **html2text**.
eg
```
curl --retry 3 "http://www.bom.gov.au/wa/observations/perth.shtml" |  html2text -o ~/weather.txt
```
Use whatever is easiest to get the info you want.

---

### Post by Dreamer Fithp Apprentice on 2015-10-24
Thanks, CantankRus. I'm still tinkering with this, but I think y'all have given me the tools I'll need. So I'll mark it solved.

For what it is worth to anybody doing something similar:

This search string also found a lot of good links:
latitude longitude weather

And this site is promising:
[https://developer.forecast.io/docs/v2](https://developer.forecast.io/docs/v2)

---

