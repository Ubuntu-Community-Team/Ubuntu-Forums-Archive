---
title: "Set timezone from GPS latlong and timezone maps"
date: 2014-12-07
forum: General Help
---

### Post by cpdondo on 2014-12-07
I travel a lot, and I have a laptop with a built-in GPS.  I would really, really like for the laptop to set itself to the current timezone from the GPS.  I'm not talking about keeping accurate time; I am talking about setting the timezone based on mapped timezone boundaries.

There are a few projects around that have the timezone maps (like this one: [http://efele.net/maps/tz/](http://efele.net/maps/tz/) ) but I have not been able to find a package that can read latlong, look up the timezone using the coordinates, and then set the system timezone.

Is anyone aware of any such thing?

---

### Post by bapoumba on 2014-12-07
Not here, but I found the question interesting :)
Here are a few links. Could not find any application that would do it, I may have not searched well enough.
[http://stackoverflow.com/questions/5584602/determine-timezone-from-latitude-longitude-without-using-web-services-like-geona](http://stackoverflow.com/questions/5584602/determine-timezone-from-latitude-longitude-without-using-web-services-like-geona)
[http://stackoverflow.com/questions/8327280/gps-position-to-timezone](http://stackoverflow.com/questions/8327280/gps-position-to-timezone)
[http://stackoverflow.com/questions/16086962/how-to-get-a-time-zone-from-a-location-using-latitude-and-longitude-coordinates](http://stackoverflow.com/questions/16086962/how-to-get-a-time-zone-from-a-location-using-latitude-and-longitude-coordinates)

---

### Post by JKyleOKC on 2014-12-07
> **cpdondo said:**
> I have not been able to find a package that can read latlong, look up the timezone using the coordinates, and then set the system timezone.

Is anyone aware of any such thing?I don't think such a package exists, for the simple reason that timezone boundaries are not straight lines marked off by latlong coordinates. They are intensely political in nature and usually (but not always) follow political boundaries.

You could, however, approximate what you are looking for by applying the fact that each 15 degrees of longitude is another hour's displacement from GMT/UTC, subtracting if moving west or adding if moving east. You could calculate the displacement using just the longitude value from GPS, and apply it to calculate a timezone value, keeping in mind that UTC is based at 0 degrees longitude. 

You might still be an hour off in those cases where the actual zone boundary isn't at a multiple of 15 degrees (the enormous width of the USA's Central zone comes to mind immediately), and at one time the zone for South Korea was displaced by only 30 minutes because Syngmann Rhee refused to keep the same time as neighboring Japan. However this might be close enough for most purposes...

---

### Post by cpdondo on 2014-12-07
The database I refered to [http://efele.net/maps/tz/](http://efele.net/maps/tz/)  has the correct boundaries in polygons.  It's a matter of reading it and then setting the time.  If I could get it into sqlite and then write something to read the latlong from gpsd it would be fairly simple....  I'm hoping someone else has done the work.  :)

There are a few libraries around, but no single app that does what I'm looking for.  Android packages exist; my tablet sets the time based on GPS and it has not failed me yet.

---

### Post by steeldriver on 2014-12-07
Quick bit of googling throws up this on StackOverflow  --> [How to get a time zone from a location using latitude and longitude coordinates?]("http://stackoverflow.com/q/16086962")

---

### Post by cpdondo on 2014-12-08
I've been through all of those; none are a standalone app.  Looks like I'll roll my own using spatialite.  :)

---

### Post by ian-weisser on 2014-12-08
Here is someone else's solution: [http://davidegironi.blogspot.it/2014/03/finding-timezone-by-latitude-longitude.html](http://davidegironi.blogspot.it/2014/03/finding-timezone-by-latitude-longitude.html)

---

