---
title: "BandWidth Monitor"
date: 2013-08-08
forum: General Help
---

### Post by nachinew on 2013-08-08
Hi,

New to Ubuntu, I want a application which monitor my Bandwidth usage in GUI for Particular time. Is any application is available for my requirement?
For ex: If I need to monitor for a month at a specific time 10 to 6. 

Please share your views.

---

### Post by ajgreeny on 2013-08-08
Have a look at vnstat.

I am not sure about the level of detail you want from the utility, or whether vnstat can do that for you, but it is pretty flexible so there may be a way to get exactly what you want from its output.

---

### Post by maggotbrain on 2013-08-08
For bandwidth monitoring(and much more), I am partial to using [Cacti]("http://www.cacti.net/") in my environments as it is relatively easy to install, greatly customizable, and has a healthy plug-in community for this such as custom reports, scheduling, etc.

To get a newer version that is not in the common repositories, you will need to install a PPA:
```
sudo add-apt-repository ppa:micahg/ppa
sudo apt-get install cacti
```

---

### Post by nachinew on 2013-08-08
> **maggotbrain said:**
> For bandwidth monitoring(and much more), I am partial to using [Cacti]("http://www.cacti.net/") in my environments as it is relatively easy to install, greatly customizable, and has a healthy plug-in community for this such as custom reports, scheduling, etc.

To get a newer version that is not in the common repositories, you will need to install a PPA:
```
sudo add-apt-repository ppa:micahg/ppa
sudo apt-get install cacti
```

Thanks for your reply.
Can this support to monitor for a specific or scheduled period.

---

### Post by maggotbrain on 2013-08-08
Yes, it can produce data based upon specified time criteria. While Cacti is an 'always on' service, there are custom filters that allow you to specify desired time period. Here is an example, on one of my machines based upon your time period:

[http://i.imgur.com/ppJvk5J.png]("http://i.imgur.com/ppJvk5J.png")

There are also plugins for generating reports which can be set up to be emailed out to you if you desire based upon your data filters.

---

### Post by nachinew on 2013-08-09
> **maggotbrain said:**
> Yes, it can produce data based upon specified time criteria. While Cacti is an 'always on' service, there are custom filters that allow you to specify desired time period. Here is an example, on one of my machines based upon your time period:

[http://i.imgur.com/ppJvk5J.png](http://i.imgur.com/ppJvk5J.png)

There are also plugins for generating reports which can be set up to be emailed out to you if you desire based upon your data filters.

I installed friend, how to start and monitor the bandwidth.
I installed using synaptic manager

---

