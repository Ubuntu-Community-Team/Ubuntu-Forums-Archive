---
title: "Need help with battery information"
date: 2022-07-29
forum: General Help
---

### Post by la.khan on 2022-07-29
To get more information on how my laptop battery is doing, I run the command ```
upower -i $(upower -e | grep BAT0)
``` I see the following output:
```

  native-path:          BAT0
  vendor:               SMP-SDI2.8
  model:                DELL FW1MN31
  serial:               1358
  power supply:         yes
  updated:              Friday 29 July 2022 07:23:03 PM (107 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               fully-charged
    warning-level:       none
    energy:              19.1512 Wh
    energy-empty:        0 Wh
    energy-full:         19.1512 Wh
    energy-full-design:  41.44 Wh
    energy-rate:         0.0148 W
    voltage:             16.899 V
    charge-cycles:       N/A
    percentage:          100%
    capacity:            46.2143%
    icon-name:          'battery-full-charged-symbolic'

```
Here is my interpretation of the output. It is a Dell battery and it is fully charged at 100%. It is designed to provide 41.44 Wh of output, but currently it provides only 19.15 Wh. And, it's capacity is only 46.2143%. Is this correct? Am I reading this right?

Truth be told, my laptop battery is 3+ years old and I know that all batteries deteriorate over time (mobiles, laptops, cars etc). But, it looks like this piece has served me well. Or, do I have this all wrong? Is there a better/accurate way/tool to monitor how my battery is performing?

Thanks for any insights I may have missed :)

---

### Post by TheFu on 2022-07-29
Looks like the battery holds only 46% of the designed amount. It is dying.  Whether 46% is sufficient is a question that only you can answer.  If it were me and I used the battery more than 2 hrs at a time, I'd get a replacement.  
Or if the battery is "bulging", it is a safety hazard and needs to be disposed quickly, then replaced.  Bulging is bad and is a sign of possible overheating, leaking, and worse.

OTOH, I have a Dell laptop with a basically a dead battery. It hasn't moved in over a decade and is never used without plugged in power. The battery isn't bulging.  When the system finally dies ...  is has GPU issues already, but a hard reboot seems to get the GPU working again ... anyway, when it finally dies, I'll have to figure out a different solution.  I haven't booted that laptop since April. It isn't even plugged in now.  For years, it was powered on 24/7/365. I definitely got a fantastic value from it.

BTW, I wouldn't trust those battery measurements much.  They are prbably only accurate within ±2%, if that much.  Ignore all those decimal points.  Software people often confuse accuracy and "close enough".  Just because something can be calculated to 50 decimal points, that doesn't make any difference in the true accuracy.  That's part of the difference in training for an engineer vs a theoretical scientists.  Engineers work with "close enough", not exact answers.  Batteries are definitely about engineering.

---

### Post by la.khan on 2022-07-30
Thanks for the reply.

As of now, my battery gives < 2 hrs of back up. And, it takes < 2 hrs to charge to full 100%. When the battery was new, it would last 4 hrs without power and took 4 hrs to recharge to 100%. That is how I know it is deteriorating. And, the readings/measurements (capacity 46%) match with my experience. As of now, it looks like my laptop battery still has some juice left and I can squeeze a few more months out of it, before I order a replacement.

Good point about battery bulging. Now that you mention it, I did notice  it with some mobile phone batteries. Had them replaced pronto. Will keep  an eye out for any bulge in my laptop battery.

Usually, my laptop is plugged into an electrical socket for most of the time. Though it is a laptop, I use it more as a desktop. I barely move it unless I have to. Once a week, I unplug the laptop and let it run on battery till it goes down to 9-10%. Then, I charge it all the way back to 100%. This seems to have stood me in good stead. Either that or I have recd an exceptionally good battery or both \\:D/

Yeah, agreed, them decimal points are kinda excessive :tongue:

---

