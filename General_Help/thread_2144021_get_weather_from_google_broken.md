---
title: "get_weather_from_google broken?"
date: 2013-05-10
forum: General Help
---

### Post by defaria on 2013-05-10
For quite some time now the indicator-weather applet in Ubuntu has been unable to do a Forecast. When I do it I get: "Forecast information cannot be fetched. Connection cannot be established".

I noticed that indicator-weather was written in Python and I decided to see what all the fuss was about Python (I'm a huge Perl guy but never saw a good reason to learn Python). I wanted to specifically learn the debugger so I said "Hey indicator-weather has this bug - let's see if I can debug it).

At around line 472 of indicator-weather.py it makes the following call:

    self.forecast = pywapi.get_weather_from_google (location_name, hl = self.locale)

And I see in pywapi.py that it's using the GOOGLE_WEATHER_URL of [http://www.google.com/ig/api?weather=%s&hl=%s](http://www.google.com/ig/api?weather=%s&hl=%s). The %s's are filled in with ",,,32847270,-117274204" and "en". This call fails. If I use a browser to go to that URL with the %s's filled in I get:

    We're sorry...

    ... but your computer or network may be sending automated queries. To protect our users, we can't process your request right now.
    Google Help for more information

And going to the Google Help page talks about captcha's and the like. Is this just plain broken now?

---

### Post by tgalati4 on 2013-05-11
Sending automated queries violates Google's terms of service.  The weather query is picked up by their robot filters.

[http://blog.programmableweb.com/2012/08/28/google-weather-api-never-supported-finally-disconnected/](http://blog.programmableweb.com/2012/08/28/google-weather-api-never-supported-finally-disconnected/)

---

### Post by defaria on 2013-05-11
OK, it says it can use Yahoo too and in fact I'm set to use Yahoo but that doesn't seem to be working either. In any event, how do we get this fixed?

---

### Post by tgalati4 on 2013-05-11
Check [http://bugs.launchpad.net](http://bugs.launchpad.net).  I found 168 hits for* indicator-weather*.  And the API's constantly change for such services:  [https://bugs.launchpad.net/ubuntu/+source/indicator-weather/+bug/1048193](https://bugs.launchpad.net/ubuntu/+source/indicator-weather/+bug/1048193)

When the service dies, there is not much you can do about it:  [https://bugs.launchpad.net/ubuntu/+source/indicator-weather/+bug/1047898](https://bugs.launchpad.net/ubuntu/+source/indicator-weather/+bug/1047898)

---

### Post by Linuxisfast on 2013-05-12
Add atareo ppa and install my-weather-indicator which is far more feature filled and bug free and it has several options of weather service including weather world weather and wunderground.

---

### Post by defaria on 2013-05-12
The fact that there's been 168 hits for bugs and at least a year and nothing's been fixed is very telling... From what I can tell both the Google and the Yahoo services are not working.

---

### Post by defaria on 2013-05-12
Care to tell me how to "add atareo ppa"?

---

### Post by defaria on 2013-05-12
So I go to [http://www.noobslab.com/2013/01/install-my-weather-indicator-in-ubuntu.html](http://www.noobslab.com/2013/01/install-my-weather-indicator-in-ubuntu.html) and install my-weather-indicator and nothing happens. How do you run the thing? I look at the list of installed files and I assume it's something like:

$ /opt/extras.ubuntu.com/my-weather-indicator/bin/my-weather-indicator
Traceback (most recent call last):
  File "/opt/extras.ubuntu.com/my-weather-indicator/bin/my-weather-indicator", line 38, in <module>
    import comun
  File "/opt/extras.ubuntu.com/my-weather-indicator/share/my-weather-indicator/comun.py", line 121, in <module>
    line = f.readline()
  File "/usr/lib/python3.3/encodings/ascii.py", line 26, in decode
    return codecs.ascii_decode(input, self.errors)[0]
UnicodeDecodeError: 'ascii' codec can't decode byte 0xef in position 512: ordinal not in range(128)

Bug free? Really?

---

