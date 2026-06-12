---
title: "How to automatically switch WIFI signals without any intervention?"
date: 2019-09-08
forum: General Help
---

### Post by ardouronerous on 2019-09-08
Here's my situation, we have two routers at my home, the main wireless router which is downstairs and a wireless bridge router that I set up upstairs.

Now, due to the doors, walls and floors, the WIFI signal from the downstairs router is weaker upstairs, same with my wireless bridge, it's weaker downstairs.

Here's the problem though, my sister, who's laptop runs Lubuntu, she uses her laptop downstairs and upstairs, but like I said, she experiences weak WIFI signal when she goes up to her bedroom.

Is there a way to configure Lubuntu to switch automatically to my WIFI bridge when she's upstairs and switch automatically to the main router when she goes downstairs?

Thanks.

---

### Post by MoebusNet on 2019-09-09
I don't know if this will help, but Network Manager will start looking for a known WiFi connection when the one it is using is weak enough to drop. You might actually want to *lower* the power level of your wireless routers to the minimum that provides stable coverage. Then when she changes locations, the further router will drop out due to weak signal strength, Network Manager will look for a known WiFi connection and choose the strongest (usually closest) signal. This may not work if you have a neighbor running a really strong, close signal that you can log into; in which case just forget his login info.

---

### Post by ardouronerous on 2019-09-10
Thanks for the info. So, I guess my sister has to wait for the router signal from the downstairs router to drop before it accepts the signal from my wireless bridge, which is already set up on her laptop.

---

### Post by MoebusNet on 2019-09-12
If the downstairs router is strong enough, Network Manager may not drop the connection when she is upstairs. Visa versa for the upstairs router when downstairs. Best practices call for operating your wireless routers at the lowest power levels that will still result in stable connections; otherwise you wind up interfering with yourself and anyone else on the same WiFi channel. Only you can determine what the proper power levels should be set at; it just takes a little experimentation.

---

