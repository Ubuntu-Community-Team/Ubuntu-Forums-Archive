---
title: "System Becomes Unbearably Slow!!"
date: 2018-01-22
forum: General Help
---

### Post by wewantutopia on 2018-01-22
Hello,

My laptop will slow to an unbearable level making work very hard.

I am running Ubuntu 16.04 on a Intel i7-2675QM @ 2.20GHz with 8gb ram.

It is using intel_pstate as the driver.

I've recently learn that I can use: ```
 watch -n1 "lscpu | grep MHz | awk '{print $1}'";
``` to view realtime CPU usage.

It occasionally will run at ~2000mhz as I would expect.  It most often runs between 650-1100 mhz even though it displays 3100mhz max - 800mhz min.  When the system gets unbearable it will be running @ 300mhz all the way down to 110mhz!!! This is crazy!!  It will stay that slow for ~ 20 seconds.  It seems to do this every couple of minutes or so.

Does anyone have any ideas??

Thank you!

---

### Post by TheFu on 2018-01-22
cooling problem?

---

### Post by cruzer001 on 2018-01-22
Disable cpu throttling?

an example

[https://askubuntu.com/questions/971142/cannot-disable-cpu-throttling-on-ubuntu-16-04-lts](https://askubuntu.com/questions/971142/cannot-disable-cpu-throttling-on-ubuntu-16-04-lts)

---

### Post by QIII on 2018-01-22
Disabling CPU throttling is a good way to allow the blue smoke to escape if the throttling is thermal.

OP:  Monitor your temps to see if they are rising quickly at the time the machine slows down.

Install something like lm-sensors, detect your sensors then watch.  You'll have to take a look at the output of sensors to determine which line is the CPU temp and grep for that line in your watch command.

---

### Post by wewantutopia on 2018-01-24
Thanks for all the replies.  I think I've mostly got it sorted.

I have the sensor indicator installed; temps seemed within range.

I turned off CPU power saving in the BIOS and the minimum freq. immediately increased to 799.99 (no more 100/300 mhz) but stayed pegged there.

I then noticed turbo was turned off.  Turned it back on and it stayed pegged at 1199 (a 50% increase!).

I noticed I couldn't adjust and save /sys/devices/system/cpu/intel_pstate/min_perf_pct and max_perf_pct.  Both were set to 40 and I could not change the values.

After much searching, I uninstalled Thermald.  

Everything seems to be in order now.  The system is running hotter but at the max of an acceptable range; the fan is doing it's job.  Seems like Thermald was hard-coding those values.

Figured I'd report back in case anyone else runs into something like this.

Thanks for your assistance

---

