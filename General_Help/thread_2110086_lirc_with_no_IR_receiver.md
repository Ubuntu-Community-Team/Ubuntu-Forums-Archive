---
title: "lirc with no IR receiver"
date: 2013-01-29
forum: General Help
---

### Post by el_Paraguayo on 2013-01-29
This may sound a bit odd, but I want to run lirc without a physical IR receiver attached. 
 
The reason being is that I use [amote]("http://www.google.co.uk/url?sa=t&rct=j&q=raspberry%20pi%20amote&source=web&cd=1&cad=rja&ved=0CDIQFjAA&url=http%3A%2F%2Fwww.raspberrypi.org%2FphpBB3%2Fviewtopic.php%3Ff%3D35%26t%3D15258&ei=SMwHUeDxDoeS0QXd9YHoDg&usg=AFQjCNGgdK9JcvZS89n5KoxtrSX-qI9Ang&bvm=bv.41524429,d.d2k") to control an ir receiver and blaster on my raspberry pi. But I'd like to add some control functionality for my pc which doesn't have a receiver.
 
Amote works by connecting to a lirc daemon running with the "--listen" option.
 
The pc is running mythbuntu 10.10.
 
If I set the lircd parameters in the hardware.conf file and try to restart lircd it fails to start.
 
What I'd really like to know is whether this is an achievable result, or whether I'm wasting my time.
 
Assuming the former, any tips to get it running would be greatly appreciated.
 
Thanks,
 
el_P

---

