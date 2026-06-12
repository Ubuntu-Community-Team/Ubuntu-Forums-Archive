---
title: "Record with rtl_fm"
date: 2018-02-09
forum: General Help
---

### Post by francistransitron2 on 2018-02-09
Hi,

I am trying to figure out the best way to record audio with rtl_fm. How  do you guys do it? Do you simply replace the "play" after the pipe with a  record command, do you add another pipe after the play to record?

Here is what my current command looks like, to play: ```
[COLOR=#000000][FONT=Arial]rtl_fm  -f 95.1M -M fm -s 200k -E deemp |[/FONT][/COLOR][COLOR=#000000][FONT=Arial] [/FONT][/COLOR][COLOR=#000000][FONT=Arial]redsea | play -r 200k -t raw -e s -b 16 -c 1 -V1 - lowpass 16k[/FONT][/COLOR]
```

I would like to use arecord to record on sound detection, but I really don't know where to start.

Any help would be greatly appreciated.

Regards,

---

### Post by HermanAB on 2018-02-09
This will record the NOAA number 15 weather Fax satellite:
rtl_fm -M usb -f 137.6181M -s 24k  -l 0 | sox -r 24k -t raw -e s -b 16 -c 1 - noaa15.wav

---

### Post by francistransitron2 on 2018-02-09
Thank you Herman, I will try this.

---

### Post by francistransitron2 on 2018-02-09
Herman, do you know how arecord with sound detection would be implemented for this?

---

### Post by HermanAB on 2018-02-09
Well, arecord and aplay are the ALSA utilities, while sound exchange (sox) is a generic swiss knife.  They can achieve the same thing, but one has to read the man page to figure it out.

You want to automatically start/stop using VOX?  I don't know of a utility that can easily do that.

rtl_fm can scan based on squelch settings, but the audio will all go into the same file.


The other way to do things, is to start and stop a little script using the at daemon.

Get the satellite orbital time with gpredict.

For example, if you have  script called n15:
#! /bin/bash
/opt/local/bin/rtl_fm -d 0 -M usb -f 137.618100M -s 24k -l 0 | /usr/local/bin/sox -r 24k -t raw -e s -b 16 -c 1 - wxdata.wav

Then you can start it with at:
$ at -f ./n15 now + 168 minutes
job 6 at Fri Feb  9 13:45:00 2018

The recording will run forever, unless you stop it with a scheduled kill command.

So you can make a simple killall script like this one called n15stop:
#! /bin/bash
killall n15

and schedule it like this:
$ at -f ./n15stop now + 178 minutes

To capture 10 minutes of data. 

There are several blog posts here: 
[http://www.aeronetworks.ca/2017/12/satellite-weather-maps-on-macbook.html](http://www.aeronetworks.ca/2017/12/satellite-weather-maps-on-macbook.html)

---

