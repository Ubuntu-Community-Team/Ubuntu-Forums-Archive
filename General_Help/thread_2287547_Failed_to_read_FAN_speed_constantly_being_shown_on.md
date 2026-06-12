---
title: "Failed to read FAN speed constantly being shown on screen"
date: 2015-07-20
forum: General Help
---

### Post by mrJTparadise on 2015-07-20
Hi all,

After bootup, I get the error : Failed to read FAN speed every 3 seconds.  Just a snippet below, but my entire screen is flooded with these.
 
```
[  353.317317] Failed to read FAN speed
[  356.049939] Failed to read FAN speed
[  356.059858] Failed to read FAN speed
[  358.777936] Failed to read FAN speed
[  358.788055] Failed to read FAN speed
[  361.545800] Failed to read FAN speed
[  361.555714] Failed to read FAN speed
[  364.274213] Failed to read FAN speed
[  364.284139] Failed to read FAN speed
[  366.998069] Failed to read FAN speed
[  367.008192] Failed to read FAN speed
[  369.752486] Failed to read FAN speed
[  369.762418] Failed to read FAN speed
[  372.506622] Failed to read FAN speed
[  372.516754] Failed to read FAN speed
[  375.289893] Failed to read FAN speed
[  375.300014] Failed to read FAN speed
[  378.028185] Failed to read FAN speed
[  378.037899] Failed to read FAN speed
[  380.811135] Failed to read FAN speed
[  380.821054] Failed to read FAN speed
[  383.538937] Failed to read FAN speed
[  383.548865] Failed to read FAN speed
[  386.267621] Failed to read FAN speed
[  386.277539] Failed to read FAN speed
[  388.995763] Failed to read FAN speed
[  389.005693] Failed to read FAN speed

```

I’ve edited /etc/sensor3.conf and made sure ignore fan1/2/3 is uncommented under each module listing.  Furthermore, I’ve went into the BIOS and disabled the Embedded Controller Fan/Temp specified monitoring to also see if this makes a difference.
 
Both changes haven’t given me any luck in making this message go away.
 
Does anyone know what may be the culprit in this or how to get rid of the message?  We have no fans in our system.

---

### Post by dino99 on 2015-07-20
which ubuntu release are you using ?

---

### Post by mrJTparadise on 2015-07-20
I am using Ubuntu 14.04 x64 Server edition.  I have narrowed it down by not loading specific modules at bootup - coretemp and w83627hf.  Doing this removes the errors, however, I need these modules as a requirement.

---

### Post by mrJTparadise on 2015-07-21
Problem is within the driver and not lm-sensors or /etc/sensors3.conf.  Please disregard.

---

