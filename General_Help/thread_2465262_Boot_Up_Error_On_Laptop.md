---
title: "Boot Up Error On Laptop"
date: 2021-07-27
forum: General Help
---

### Post by koollaydtac on 2021-07-27
My wife got this error on her laptop. I have no idea how she got it. What I should do and how do I fix this? Thanks in advance. :)

[https://cdn.discordapp.com/attachments/558632421608783891/869686735804698714/Photo0034.jpg](https://cdn.discordapp.com/attachments/558632421608783891/869686735804698714/Photo0034.jpg)

---

### Post by tea for one on 2021-07-27
You boot into a [COLOR="#0000FF"]live[/COLOR] session using your installation media (Ubuntu/Xubuntu etc).
Open a terminal and run:-

```
sudo fsck /dev/mmcblk0p2
```

---

### Post by koollaydtac on 2021-07-27
Thanks mate. Ok I did what you said and this is what happened. It failed because it says it's mounted. Is there something else I need to do? Thanks again. :)

[https://cdn.discordapp.com/attachments/558632421608783891/869714222450372698/Photo0060.jpg](https://cdn.discordapp.com/attachments/558632421608783891/869714222450372698/Photo0060.jpg)

---

### Post by koollaydtac on 2021-07-27
Ok I actually got it sorted out mate. I went in to GParted and was able to unmount the disk from there. Thanks again for the help mate. I appreciate it. :)

---

