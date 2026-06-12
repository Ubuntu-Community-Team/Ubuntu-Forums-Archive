---
title: "Ethernet settings, help me kill my windows partition!"
date: 2007-09-22
forum: General Help
---

### Post by Kisame on 2007-09-22
When I enter the Device Manager in the Windows OS and double click my ethernet controller and then click the advanced tab,then i change the value in the scroll menu from auto mode to "10 half mode" if i don't do this the internet just doesnt work at all. When I installed linux on the same machine, I had no idea how to set the internet to 10 half mode or a corresponding setting,
my question is, how?


plz hlep!1:P

---

### Post by Kisame on 2007-09-22
Bump

---

### Post by sonofusion82 on 2007-09-22
try to search for mii-tool or have a look at [http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/](http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/)

i have done is once for a temporary solution when i was using a simple network cable splitter

---

### Post by dcstar on 2007-09-22
> **Kisame said:**
> When I enter the Device Manager in the Windows OS and double click my ethernet controller and then click the advanced tab,then i change the value in the scroll menu from auto mode to "10 half mode" if i don't do this the internet just doesnt work at all. When I installed linux on the same machine, I had no idea how to set the internet to 10 half mode or a corresponding setting,
my question is, how?


Install the ethtool package, and then you put the setting into a small script and you can have that run on startup.

---

### Post by Michl on 2007-10-12
> **dcstar said:**
> Install the ethtool package, and then you put the setting into a small script and you can have that run on startup.

"Wow.  Definitely a reason not to kill the windows partion.  For starters, you need it to
connect to the internet so that you can download something because without changing
the ethernet controller, I can't connect.  I have the same problem ... and changing
the Media Type to 10Base in windows solves all problems, but such a simple change
in ubuntu is a major migraine."

Ok, that was my first pissy reply, but this did help because ethtools is the answer.
But it is part of the Edgy distribution and doesn't need to be downloaded.  So that's
a HUGE relief.  Ethtools is not super transparent, but like all things linux, it is
not as easy and transparent as the configure panels in MS, but it let's
you do a whole lot more.

I;ll stand by this:  ubuntu is a struggle but right as you are on the verge of giving
up, it comes through.  Love/hate.

Michl

P.S>  well, I thought I had it licked but now I'm not able to configure the
ethernet conroller in ubuntu.  it worked once but now it doesn't again
and I don't know what is giong on.

---

