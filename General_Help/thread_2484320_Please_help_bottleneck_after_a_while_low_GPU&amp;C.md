---
title: "Please help bottleneck after a while low GPU&amp;CPU utilize | No memleak or throttle"
date: 2023-02-22
forum: General Help
---

### Post by stormblitzinc on 2023-02-22
What happened?
i5-10400F | RTX 3070 | RAM 16 GB | Ubuntu 22.04.1| Python 3.10.6 (main, Nov 14 2022, 16:10:14) [GCC 11.3.0]

Using stable diffusion on the machine. After 2-6 hour it will slow down and not fully utilize GPU and CPU

Restart is needed to back to normal.

At first I though there is a bottleneck or leaks in the system, So I check and test multiple time to make sure that there are no bottleneck or leak.

I have changed PSU to higher watt (700) and install Ubuntu on SSD instead of HDD doesn't fix the issue.

Normal speed (first 1000-2000 generation)
Normally GPU utilize should be at 95-100% when image is generating
CPU should have at least 1 core running at 100%. (idle 15-20%)
GPU temperature never exceed 70c & fan not running at 100%
CPU temperature always under 60c
RAM utilize at 60% (6GB left) with swap space of 63GB left

Slowdown happens
When it slowed down (this apply until webui.sh is restarted) GPU utilize only at 20-50%
No CPU core running at 100% over all utilize was at 25%
RAM utilize at 60% (6GB left) with swap space of 63GB left (just in case)
Both temperature is under 50c

For photo of collected log while the bottleneck happen.
Please see in this link
[https://github.com/AUTOMATIC1111/stable-diffusion-webui/issues/8015](https://github.com/AUTOMATIC1111/stable-diffusion-webui/issues/8015)

I can't figure out what is causing this. If you have any command that you would like to get an output from.
Please let me know.

---

### Post by TheFu on 2023-02-23
Setup proper system monitoring, the type that will capture 50 different elements of data constantly and let that run for a few days, then look at all the data involved.  There are lots of performance monitoring tools. You probably want one that runs in the background, collecting data, and generating graphs 2x daily, but not more often.

Note the exact times when you notice the slow downs, so you can look at the captured performance numbers for those periods.  What's memory use look like? Is the system thrashing storage?  Is some huge java application performing garbage collection?  What programs are using all the CPU and RAM and networking?  A performance monitoring tool will provide these answers.  Here's an example: [http://demo.munin-monitoring.org/munin-monitoring.org/demo.munin-monitoring.org/](http://demo.munin-monitoring.org/munin-monitoring.org/demo.munin-monitoring.org/)

BTW, there is such a thing as too much swap.  4G is the most I'd use, ever.  Too much and the system has to manage it.

---

### Post by stormblitzinc on 2023-02-23
@TheFu Thankyou for your response I've setup a NewRelic monitor and change the swap size to 8GB. I'll clean run the service again and see if the problem occur and what data is showing in the monitor. I'll update again soon. Thank you for helping.

---

