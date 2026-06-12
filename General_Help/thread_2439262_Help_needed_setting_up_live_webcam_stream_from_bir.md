---
title: "Help needed setting up live webcam stream from birdbox!"
date: 2020-03-25
forum: General Help
---

### Post by Paul_Hey on 2020-03-25
I did post a similar question in the server section yesterday, but I've made some progress now, and it's really a more general question...


I am running 16.04 server, for the purposes of Emby and TVheadend.


My wife has just purchased a bird box with a camera installed, but she's bought one which has analogue output instead of an IP camera, so needs to connect directly to a display via composite and audio plugs. I've connected it up and it's working.

I would like to be able to access the live stream from a web browser over my LAN, so that it can be seen anywhere in the house or on a device other than the TV.  In fact it doesn't have to be a web browser, VLC would also be fine, anything which can be easily run from an Android device.

I appear to have almost achieved this, by using an EasyCap DC60 USB capture card plugged into my server, and then with the motion webcam software, making it available to view on port 8081.

I say almost because the camera in the box has audio, and motion does not appear to cater for this.  What I'm looking for is a steer in the right direction, not a bespoke solution, just somewhere to start researching how to do this.  A lot of similar questions I've found point to FFmpeg, but I could do with a little advice on where to begin!
[COLOR=#000000]

[/COLOR]

---

### Post by HermanAB on 2020-03-25
This should get you going, since there are many tips on testing and debugging video streaming issues.:
[https://www.aeronetworks.ca/2018/04/raspberry-pi-video-streaming.html](https://www.aeronetworks.ca/2018/04/raspberry-pi-video-streaming.html)

---

