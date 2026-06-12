---
title: "Set GPS coordinates/location on PC without GPS device"
date: 2014-07-24
forum: General Help
---

### Post by tcarnell on 2014-07-24
I was wondering how I can setup my Ubuntu 14.04 and manually give it a location with long/lat GPS coords, any ideas?

So that when I load Google Maps etc it immediately centers on my current location (well, the location that I manually set).

---

### Post by AudioFlux on 2014-07-24
That feature already exists on the google.com/maps website. Even on the Maps android app, it centers on your location when you open it. I don't have the maps software on Ubuntu, but I will be surprised if it isn't coded along the same lines (haha, "coded along the same lines").

---

### Post by ian-weisser on 2014-07-24
The EASY way is to tell Google your coordinates in the web browser.
Browser bookmarks are good at this.
[http://www.google.com/maps/@40.05,-88.23,11z](http://www.google.com/maps/@40.05,-88.23,11z)
@latitude,longitude,zoom_level

The HARD way is to manually tell your system's GeoClue service the location.
This requires a working familiarity with both GeoClue and Dbus andDbus introspection tools, since there is _no_ documentation.
- Install the geoclue-manual package
- Use a dbus introspection tool to learn the proper message format 
- Create a dbus message to the Geoclue service with the manual address using shell or Python or C or any other language.

---

### Post by tcarnell on 2014-07-24
Thanks for the quick response - well my PC doesn't have any GPS system and when I open Google Maps it takes me to the middle of the USA (I'm in Spain). Yes, it does work on my mobile, but that has GPS.

---

### Post by tcarnell on 2014-07-24
hmm... that's sounds like a lot more work that I had hoped for - thanks for the answer!

I was hoping there was an option under the Ubuntu settings to simply enter a latitude and longitude, at which point all services that might be interested in my PC location (browsers, maps, chat apps etc) will have a location to use. At the moment, when I open Google Maps it takes me to the USA (I'm in Spain).

---

### Post by ian-weisser on 2014-07-24
GeoClue draws your location from a GPS, if one is installed.
If not, it estimates your location from your IP address. That's less exact, usually city-level resolution, sometimes worse. It depends on the location information keyed in by the admin people at the ISP. Some smaller ISPs simply assign all locations to their head office (after all, that's where they are).

If you are using a Spanish ISP, GeoClue should be resolving your location to be Spain, and Google Maps should open to Spain.

If, however, you are using a different ISP (like a Satellite ISP, or a USMIL ISP), the IP address location will often be wherever the head office of the organization is.

I once used a Norwegian satellite ISP, so Google kept offering me the wrong search language. The workaround was to use an english-language bookmark.

---

