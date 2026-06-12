---
title: "How to speed up my Ubuntu 14.4"
date: 2015-12-17
forum: General Help
---

### Post by kolswadet on 2015-12-17
How can I speed up my Ubuntu 14.4  more besides installing a SSD which I already have done!
Hope for some useful advise!
Greetings and stay friendly.
kolswadet

---

### Post by pfeiffep on 2015-12-17
Without any specifics about your machine or what aspect you wish to speed up here are 3 links you might find helpful.
[http://www.howtogeek.com/115797/6-ways-to-speed-up-ubuntu/](http://www.howtogeek.com/115797/6-ways-to-speed-up-ubuntu/)
[https://sites.google.com/site/easylinuxtipsproject/Home](https://sites.google.com/site/easylinuxtipsproject/Home)
[http://itsfoss.com/speed-up-ubuntu-1310/](http://itsfoss.com/speed-up-ubuntu-1310/)

---

### Post by XBNCPRk on 2015-12-17
After installing the ssd there are a number of things you can do to improve it, such as enabling trim, picking a better io scheduler, adjusting swappiness (provided you have sufficient ram) and moving your /tmp cache to run in the ram rather than from the ssd.
[http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/)

As a side note, I prefer to avoid applications like preload since the minimal gains from it are far outweighed by the computers inability to guess what I want to do.

---

