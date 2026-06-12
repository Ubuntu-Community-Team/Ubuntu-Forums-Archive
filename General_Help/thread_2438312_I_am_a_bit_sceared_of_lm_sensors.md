---
title: "I am a bit sceared of lm_sensors"
date: 2020-03-09
forum: General Help
---

### Post by yayeterusernaminisenin on 2020-03-09
Hello guys ! , I'm new to Ubuntu, I build it dual-boot way so I have windows 10 and Ubuntu together in my pc. I wanted to see my cpu temperature and search for it and I see that I must use lm_sensors. I downloaded lm_sensors and I type "sudo sensors-detect" like I see on internet. While setup there was questions that asks do you want to scan this etc. This was the last question that I choose default reply;

```
Do you want to probe the I2C/SMBus adapters now? (YES/no):
```

and than these questions are appered;

```
Next adapter: nvkm-0000:01:00.0-bus-0000 (i2c-0)
Do you want to scan it? (yes/NO/selectively): 
Next adapter: nvkm-0000:01:00.0-bus-0001 (i2c-1)
Do you want to scan it? (yes/NO/selectively):
```

...(it is going up to the (i2c-12).

I answered all of  them to yes :(. Then I see in internet it is very dangerous to answer other than defaults and default answers for these questions are NO, I was not know how to choose default (I have learned it later that I must press enter to choose defaults). Now everything seems good with my pc there is no problems but may i have screwed some things?. is my computer damaged?.

---

### Post by CatKiller on 2020-03-10
It's fine.

*Potentially* communicating on the wrong bus could cause your computer to get confused and crash. If that had happened, restarting it would make it good as new again. I've never heard of that actually happening, though.

---

### Post by speartip on 2020-03-10
Just re-run "sudo sensors-detect" & go through it again.

---

