---
title: "ubuntu sound through hdmi any source"
date: 2018-11-09
forum: General Help
---

### Post by mixtutor on 2018-11-09
I am trying to use severas ubuntu versions for make it works.
I want to have sound through hdmi, and when i set it mannualy its working, but i have many pcs and can you advice me how to make this right.
If my source hdmi input is 1 maybe it is gonna to work, but on some locations input is hdmi2 or hdmi3 and only when I mannualy set then sound came to life.
I am using linux newest version, i tried several version, lubuntu, kubuntu etc

Can I somehow make this?

I did with this 

```
pacmd set-card-profile 0 output:hdmi-stereo &&
sudo chmod 777 /etc/pulse/default.pa &&
echo -e "set-card-profile 0 output:hdmi-stereo \nset-default-sink 0" >> /etc/pulse/default.pa

```
but when output is another, this is not working.

---

