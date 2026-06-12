---
title: "Audio Output to fifo"
date: 2019-09-08
forum: General Help
---

### Post by nathanhawthorne12 on 2019-09-08
Morning folks.  

Just a quick background.

I enjoy capturing Satellite Images From the Likes of Meteor or NOAA.  I use a basic SDR via usb to my computer.

Meteor Satellites are a little more difficult to capture than NOAA, but the general thing to do is

Use an SDR Application to Record Audio -> Demodulate the Audio File -> Decode the Demodulated file and produce an image.

Now to do this the easy way in Linux I would 

1.  mkfifo /tmp/meteor_iq
2.  meteor_demod -s 140000 /tmp/meteor_iq << Run the Demodulator first.

3.  Run GQRX and keep watching at 137.1M until I see a nice signal

4.  Quit GQRX

5.  rtl_fm -M raw -s 140000 -f 137.9M -E dc -g <gain> -p <ppm> /tmp/meteor_iq

Pretty simple to be honest, BUT whilst I can getting the audio to the pipe, I cannot hear anything or see anything so I am unable to quite it at the correct time.  
What I would like to achieve is to use GQRX exclusively and pipe the audio to the mkfifo at /tmp/meteor_iq.  This way I can watch the waterfall for any changes and to exit the demodulating at an appropriate time.
Since GQRX can output on lan, and looking around I can see I could use  netcat as 

nc -l -u 7355 | something here

but I am unsure what to put after the pipe so It would automatically go to the fifo at /tmp/meteor_iq

OR if their was a way to pipe the audio from an application in general from pulseaudio to the fifo

Any help appreciated

Ubuntu 18.04 clean install

---

### Post by HermanAB on 2019-09-08
You can tee the audio.  That way you can hear what you are doing while processing it.

Maybe you can get some ideas here: [https://www.aeronetworks.ca/2015/09/audio-networking-with-sox-and-netcat.html](https://www.aeronetworks.ca/2015/09/audio-networking-with-sox-and-netcat.html)

---

