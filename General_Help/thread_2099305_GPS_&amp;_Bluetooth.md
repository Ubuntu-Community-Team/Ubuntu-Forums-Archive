---
title: "GPS &amp; Bluetooth"
date: 2012-12-29
forum: General Help
---

### Post by suomalainen on 2012-12-29
Happy Holidays Ubunteros!


I have a Samsung Nexus S and I would like to transmit the NMEA data it receives via it's onboard GPS receiver by exporting it over bluetooth to Ubuntu 12.04.

Has anyone done this before? I'm looking for some real good instructions how this is done but haven't found anything just yet.

Thank you!

---

### Post by kreggz on 2012-12-29
Maybe try posting this on Reddit in either the Linux or Android section if you don't get a response.

---

### Post by suomalainen on 2012-12-29
I found this post online and followed the setup instructions accordingly:

[http://gaygeekramblings.wordpress.com/2011/09/27/how-to-connect-ubuntu-laptop-to-gps-on-android-phone/](http://gaygeekramblings.wordpress.com/2011/09/27/how-to-connect-ubuntu-laptop-to-gps-on-android-phone/)

During setup I get the same screens as the OP illustrates in his instructions and am even lead to believe that I have setup my BT GPS correctly in Ubuntu 12.04 using a Samsung Nexus S.

Although the green BT light burns indicating I'm connected, I get the message:

 "GPS over BT isn't responding.Do you want to close it?"

and so I do....

Anyone have any idea what I can try next?

Thank you and Happy New Year!

---

### Post by suomalainen on 2012-12-30
Still stuck in the mud. I did however, remove Blueman and GPSD and it's client.

Thought this would be a good idea when starting over again.

Anyone have any positive experiences in getting their Android GPS to work using bluetooth?

Thanks

---

### Post by suomalainen on 2012-12-31
Bump...

---

### Post by Cheesehead on 2012-12-31
Have you tried [the (old) tutorial]("http://ubuntuforums.org/showthread.php?t=200142") on the subject?

On the GPS side, little has changed.

---

### Post by suomalainen on 2012-12-31
Thanks Cheesehead... This look good but is there different rules to follow when your using a bluetooth GPS receiver as compared with GPS in the smartphone`???

Thank you!

P.s. Is your avatar from the civil war?

---

### Post by Cheesehead on 2012-12-31
Different rules? No.
Different device descriptions? Yes. It depends upon your device.

The avatar is [http://en.wikipedia.org/wiki/Lew_Wallace](http://en.wikipedia.org/wiki/Lew_Wallace)

---

### Post by suomalainen on 2013-01-06
I still haven't got this to work and want to attempt a step by step approach.

Firstly, I'd like the terminal code "hcitool scan" to see the GPS in my Nexus s. Currently, this code only sees my nexus s and not the GPS inside it.

I have an Android app installed called "GPS over BT" and it indicates that the apps BT is discoverable but still isn't seen.

Any ideas how to get hcitool scan to see my GPS?

Thanks.

---

