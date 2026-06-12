---
title: "Quality of Life Audio issues,(default/fallback sink ignored, switching broken)"
date: 2022-06-19
forum: General Help
---

### Post by nofunever on 2022-06-19
This is in regards to switching between distinct devices, I know switching  profiles on the same device(headphone,speakers, optical/analog etc) is it's own mess, that thankfully I don't need to worry about nearly as often. It's a gripe for sure but for another day.

I have manually set the default sink  in /etc/pulse/default.pa by name rather than index(changing number of devices plugged in)

This is ignored for whatever reason. 


I have 

Soundblaster ZX
FIIO BTR5 USB & Bluethooth DAC/AMP
Focusrite 2i2 USB Recording Interface


My issue is it falls back to the Focusrite whenever I disconnect the FIIO USB rather than to the Soundblaster ZX

When I am at my Desk the FIIO BTR5 functions as a USB DAC/AMP

When I get up from my desk and disconnect it from usb it connects via bluetooth to a dedicated audio transmitter that is fed by optical out coming from the soundblaster.

With my recording interface taken out of the picture this all works seamlessly.

I plug my dac in via usb everything switches over automatically. I unplug it my system switches to the soundblaster that feeds the bluetooth transmitter and the fiio switches to bluetooth mode. Half second blip and all resumes as if nothing happened. The problem arises only when I introduce my recording interface into the equation. I prefer to keep it plugged in but it mucks EVERYTHING up.



What happens with the 2i2 added in, I unplug the Fiio, it switches to the 2i2, If I then manually switch the sink to the soundblaster, i get no audio, I have to select the Soundblaster, then deselect it, then select it one more time, for audio to kick in. Then if plug the Fiio back in via USB, it automatically switches to it in the menu but it doesn't functionally work, it requires the same selecting another device and then re re-selecting the Fiio to make the sound work.  So not only does it select the wrong device every time but I have to fiddle with the audio settings panel every time to correct the issue.

As someone who comes and goes from his computer frequently many times in an hour this is super annoying. 


To reiterate, I have the soundblaster ZX set as the default output sink in the defaults configuration file, since the number of devices changes, I am not using the index but the proper name of the device to identify it. 

I'm currently using Kubuntu but i've had this issue with other ubuntu derivatives.

---

