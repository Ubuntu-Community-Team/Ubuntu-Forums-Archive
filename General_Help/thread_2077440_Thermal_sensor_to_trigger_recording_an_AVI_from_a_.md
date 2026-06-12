---
title: "Thermal sensor to trigger recording an AVI from a network camera?"
date: 2012-10-28
forum: General Help
---

### Post by Roasted on 2012-10-28
I'm a huge fan of Motion, which is a piece of software that basically records video in the event it detects motion. It works by comparing frames to determine the number of pixels that have changed, at which point it triggers the recording process. This is all well and good, until fall hits and blowing leaves are continually triggering the software to record. No big deal, because I'd rather have too many feeds than not enough in the event somebody decides to take the package Mr. UPS man left on my porch, but in an effort to figure out a more accurate way of recording motion detection, I began to throw a few ideas around.

I'm curious if anybody knows of a way (or a product, since I have no idea if this sensor I'm about to speak of even exists) to take a thermal sensor which is network based (wireless, even?) and to send a signal to the computer to trigger a recording process into AVI format of what the network camera is seeing. Make sense?

192.168.1.150 = Ubuntu 12.04 Server (downstairs in basement)
192.168.1.160 = Vivotek IP8332 network camera (mounted outside in ceiling of deck area)
192.168.1.170 = Wired (or wireless?) thermal sensor which gets "tripped" when it sees bodies of heat (aka humans, or even small dogs etc.) moving. Signal is sent to server @ 192.168.1.150, which then begins recording the mjpg stream that 192.168.1.160 is seeing.

Any thoughts?

---

### Post by gordintoronto on 2012-10-28
Nice idea, but I have no useful suggestions.

Something along the lines of this infrared camera:
[http://www.amazon.co.uk/Y-Cam-YCB004-Black-Wi-Fi-Camera/dp/B004993AO6/ref=dp_ob_title_ce/280-2161830-7015913](http://www.amazon.co.uk/Y-Cam-YCB004-Black-Wi-Fi-Camera/dp/B004993AO6/ref=dp_ob_title_ce/280-2161830-7015913)

might be a starting point.

---

### Post by sandyd on 2012-10-28
> **Roasted said:**
> I'm a huge fan of Motion, which is a piece of software that basically records video in the event it detects motion. It works by comparing frames to determine the number of pixels that have changed, at which point it triggers the recording process. This is all well and good, until fall hits and blowing leaves are continually triggering the software to record. No big deal, because I'd rather have too many feeds than not enough in the event somebody decides to take the package Mr. UPS man left on my porch, but in an effort to figure out a more accurate way of recording motion detection, I began to throw a few ideas around.

I'm curious if anybody knows of a way (or a product, since I have no idea if this sensor I'm about to speak of even exists) to take a thermal sensor which is network based (wireless, even?) and to send a signal to the computer to trigger a recording process into AVI format of what the network camera is seeing. Make sense?

192.168.1.150 = Ubuntu 12.04 Server (downstairs in basement)
192.168.1.160 = Vivotek IP8332 network camera (mounted outside in ceiling of deck area)
192.168.1.170 = Wired (or wireless?) thermal sensor which gets "tripped" when it sees bodies of heat (aka humans, or even small dogs etc.) moving. Signal is sent to server @ 192.168.1.150, which then begins recording the mjpg stream that 192.168.1.160 is seeing.

Any thoughts?

Get a infrared sensor. You will have to tune it to detect people, or else the odd squirrel/raccoon will trip it.

If you have bears, thats just too bad ;)

---

### Post by coldraven on 2012-10-29
I have one of these which switches on a couple of outside lights. (240V)
[http://www.screwfix.com/p/140-standalone-pir/11291](http://www.screwfix.com/p/140-standalone-pir/11291)
You could wire it to a relay and switch the pins of a serial port to go up or down.
Possibly just connect the RTS and CTS pins together (pins 7 and 8 on a 9 pin plug)
[http://en.wikipedia.org/wiki/Serial_port](http://en.wikipedia.org/wiki/Serial_port) 
Then you would need a script to monitor the port. It's probably easy but don't ask me how that part would work :)

Important! Keep the mains voltage away from the low voltage serial port. Use a relay!!

---

### Post by Roasted on 2012-10-30
> **gordintoronto said:**
> Nice idea, but I have no useful suggestions.

Something along the lines of this infrared camera:
[http://www.amazon.co.uk/Y-Cam-YCB004-Black-Wi-Fi-Camera/dp/B004993AO6/ref=dp_ob_title_ce/280-2161830-7015913](http://www.amazon.co.uk/Y-Cam-YCB004-Black-Wi-Fi-Camera/dp/B004993AO6/ref=dp_ob_title_ce/280-2161830-7015913)

might be a starting point.

I don't understand how an infrared camera will help. All the infrared does is it makes "invisible" light so people show up in b/w mode much easier on the camera. I currently have this camera:

[http://www.amazon.co.uk/Vivotek-IP8332-Bullet-Network-Camera/dp/B003UBJRCI/ref=sr_1_1?s=computers&ie=UTF8&qid=1351645877&sr=1-1](http://www.amazon.co.uk/Vivotek-IP8332-Bullet-Network-Camera/dp/B003UBJRCI/ref=sr_1_1?s=computers&ie=UTF8&qid=1351645877&sr=1-1)

...which has a built in IR panel within the lens, much like the other one linked above.

What I need is some sort of sensor, a network based sensor, something that has an IP address on my network and can notify my server to begin recording the mjpg stream of the camera.

Using the info from the first post as a further example:

192.168.1.170 (sensor) detects moving bodies of heat - signal is sent to 192.168.1.150 (server) which says, yo! dude! start recording the mjpg feed from 192.168.1.160!

Any further ideas? I'm just not entirely sure how this would work. It's involving several network pieces, some of which (the network based sensor) I'm not even sure if they exist. The way "Motion" detects motion is an interesting integrated way, as it simply scans the pixels continuously - if a certain number of them change, it flags that as motion and begins recording. Hmm.

---

### Post by sandyd on 2012-10-30
I think he/she means a thermographic imaging camera. Those detect heat, which is emitted in the form of infrared.

---

### Post by Statia on 2012-10-31
I was browsing a second hand store yesterday when I saw a network camera and remembered your post.
Panasonic BL-C210
According to the box, it "detects motion, heat and sound".
According to the website, it has a pyroelectric infrared sensor.

[http://panasonic.net/pss/security/products/bbbl/lineup/bl-c210/spec.html](http://panasonic.net/pss/security/products/bbbl/lineup/bl-c210/spec.html)

Hope this helps.

---

