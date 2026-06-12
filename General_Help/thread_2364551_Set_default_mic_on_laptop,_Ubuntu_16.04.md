---
title: "Set default mic on laptop, Ubuntu 16.04"
date: 2017-06-24
forum: General Help
---

### Post by uyohn on 2017-06-24
Hey there,

I'm trying to connect output from my electric guitar to my laptop. Laptop has Headset jack (which means combined mic and headphones). I'm using dongle to separate those two jacks. Into one I'm connecting my headphones, into second the output from guitar (I'm sure I'm connecting it right). Then running command ```
pactl load-module module-loopback latency_msec=1
```. 

Problem is: Sometimes it works, sometimes is used the internal laptop mic. When I run ```
pacmd list-sources
```, thie output says: 
```
ports:        
     analog-input-internal-mic: Internal Microphone (priority 8900, latency offset 0 usec, available: unknown)
           properties: device.icon_name = "audio-input-microphone"
     analog-input-mic: Microphone (priority 8700, latency offset 0 usec, available: no)
           properties: device.icon_name = "audio-input-microphone"
    
active port: <analog-input-internal-mic>

```

The pulse audio GUI shows only one mic in both cases.

It seems to me that the dongle is perhaps not working right, because when I connect my headset right into laptop jack, the headset mic is recognized and working by default.

Question: Is it possible to somehow disable the internal mic and set the external as default?

Thanks for any response.

---

