---
title: "My Weather Indicator shows wrong temperature"
date: 2016-01-11
forum: General Help
---

### Post by tominto on 2016-01-11
Maybe I didn't set things up properly, but my weather indicator is showing it's 27c here in Toronto, ON, Canada.  How do I fix this? (I'm using Ubuntu 15.10 btw)

---

### Post by HermanAB on 2016-01-11
Prolly showing Fahrenheit.  27F = -3C

---

### Post by tominto on 2016-01-11
That sounds like it would make sense, except it is celcius.  If I change it, it shows 80.  It's annoying because I really like the app

---

### Post by ian-weisser on 2016-01-11
There are a couple 'weather app' out there. Exactly which one are you using? What's the package name?

---

### Post by tominto on 2016-01-12
Exactly that.  My-Weather-Indicator

---

### Post by HermanAB on 2016-01-12
80C would be a little bit hot yes.  Even here in the UAE, I have not seen 80C.
;)

---

### Post by ian-weisser on 2016-01-12
My-weather-indicator is not from the Ubuntu Repositories. It's PPA/Non-Ubuntu software.
That means that our experience with it is limited. It's not Ubuntu software. It other software that happens to run on Ubuntu.

You may get better support by going to the upstream project team directly: [https://launchpad.net/my-weather-indicator](https://launchpad.net/my-weather-indicator)
...or perhaps not. No changes since August 2014, and a long list of untriaged bugs.
One of those bugs seems to include your issue: [https://bugs.launchpad.net/my-weather-indicator/+bug/1517395](https://bugs.launchpad.net/my-weather-indicator/+bug/1517395)

Many 'weather apps' merely pull data from an online service. Those online services come and go, and sometimes change their API, breaking your client.
The app itself seems dormant and unmaintained. A new maintainer to fork the code, restart the project, fix those bugs, and package the software for Ubuntu is welcome.

Howerver, the app is written in reasonably-easy-to-understand Python, so can probably be fixed by anyone willing to invest a bit of time.
If you are skilled in (or wish to learn) Python, it should be a fun afternoon to figure out which service changed their API, research the new format, and fix the Python parsing of the online data.

---

### Post by Saruk_Maktao on 2016-01-12
Weather apps have to pull data from a server source, so it's possible the weather server it's pulling data from is incorrect. Depending on your weather applet, you might be able to change which service it pulls from. It may just need to be refreshed, but, if, under settings, there are other sources, my first instinct would be to try one of them and see what happens.

---

