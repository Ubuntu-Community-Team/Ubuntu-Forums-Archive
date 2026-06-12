---
title: "Firefox Ubuntu displays webpage incorrectly"
date: 2007-10-13
forum: General Help
---

### Post by jerry47 on 2007-10-13
The web page shown below displays correctly in Windows XP and not correctly in Ubuntu 7.04. Both are version 2.0.0.6 when I noticed it.

[http://www.accuweather.com/forecast.asp?partner=forecastfox&traveler=0&zipChg=1&zipcode=48162&metric=0](http://www.accuweather.com/forecast.asp?partner=forecastfox&traveler=0&zipChg=1&zipcode=48162&metric=0)

Noticed it first on my new System76 Laptop. Then checked a desktop with 19" CRT monitor. Screen resolution does not appear to play a role with the problem. Since it displays the same on a 15.4" laptop screen and 19" CRT, do not think it is a driver issue either.

The text between the 1-5 day forecast for the radar, for instance, wraps around to the next line overwriting the day of the week. I am sure there are other websites that have similar problems. But noticed this one because I use the  Forecastfox extension.

Has anyone else noticed this problem? Seems to be specific to Ubuntu, but not sure why it would display differently on two operating systems.

Thanks

---

### Post by rainwalker on 2007-10-13
Some pages don't seem to render/display correctly in the included Firefox install that comes with Ubuntu. I noticed the same sort of thing happening a while back, but it didn't happen with an install of Firefox from the mozilla site rather than the included one.
It's getting better with each update, but I still don't understand why the Ubuntu Firefox would display things differently than the Mozilla one

---

### Post by kellemes on 2007-10-13
Could it be you use different fonts?

---

### Post by jerry47 on 2007-10-14
No, changing the fonts or leaving it set to websites choose their own fonts makes no difference. 

I did however install the latest version of Firefox via SourceForge using their python script. 

This updated Ubuntu Firefox to 2.0.0.7 and corrected the text problem. There is a slight issue that still persists for a drop down box that is partially cut off.

Here is the website address for installing the latest version of Firefox using the script.

Appears to work very well with no other issues so far on two machines.

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

---

### Post by rainwalker on 2007-10-14
> **jerry47 said:**
> No, changing the fonts or leaving it set to websites choose their own fonts makes no difference. 

I did however install the latest version of Firefox via SourceForge using their python script. 

This updated Ubuntu Firefox to 2.0.0.7 and corrected the text problem. There is a slight issue that still persists for a drop down box that is partially cut off.

Here is the website address for installing the latest version of Firefox using the script.

Appears to work very well with no other issues so far on two machines.

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)


Check your about:plugins page in that new install of Firefox. I found that plugins only seem to work with the Firefox packaged with Ubuntu

---

### Post by jerry47 on 2007-10-17
I checked the plugins that I am currently using with the 2.0.0.7 Firefox and they all work fine. This also includes a test version of Gutsy on my desktop. Here is a list of plugins:

Sun JRE 1.6

MPlayer

Adobe PDF reader

Adobe Flashplayer

Now, I have experienced the hanging of Firefox using flashplayer on YouTube for instance. And this was before upgrading the browser using the Sourceforge script.  This problem has been posted all over the internet and from what I gather the consensus is that it is an Adobe issue, not Firefox.

---

