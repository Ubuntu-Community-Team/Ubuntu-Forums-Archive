---
title: "How to set up bidirectional audio communiction over network"
date: 2024-08-17
forum: General Help
---

### Post by tc2020 on 2024-08-17
I have Raspberry Pi 4B running Ubuntu (22.04LTS headless server) with a USB audio adapter attached to RPi4 USB port for both microphone and speaker connection. 

I would like to be able to communicate with someone at a remote location from my Windows PC over an Ethernet LAN, i.e., listening via microphone and talking via speaker.

I am looking for some simple and light set up. What software components do I use on the RPi4 and something common on the PC.?. 

I have read about IceCast2 and DarkIce, but not sure those are the right ones for this use. 

Any comment/direction would be greatly appreciated. Thank you.

---

### Post by HermanAB on 2024-08-18
Here is my way: [https://www.aeronetworks.ca/2015/09/audio-networking-with-sox-and-netcat.html?m=1](https://www.aeronetworks.ca/2015/09/audio-networking-with-sox-and-netcat.html?m=1)

Gstreamer may be better, but figuring it out may take days/weeks/months…

---

### Post by him610 on 2024-08-18
> listening via microphone and talking via speaker
I think you have that backwards, it should be 
> listening via speaker and talking via microphone ;)

---

### Post by currentshaft on 2024-08-18
.

---

### Post by tc2020 on 2024-08-18
Thanks HermanAB for the link. What I try to do is very similar to your blog, i.e.,VoIP intercom.
 I have come across blogs on SOX and gstreamer.

---

### Post by tc2020 on 2024-08-18
> **currentshaft said:**
> Is the person on the other end aware you're "communicating" with them?

Yes and no, depending on the situation. No is when you have to get their attention first.

---

### Post by tc2020 on 2024-08-18
> **him610 said:**
> I think you have that backwards, it should be 
 ;)

It may appear twisted but it's from my PC reference point

---

