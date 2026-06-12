---
title: "Computer Keeps Shutting Off Under Heavy CPU Load"
date: 2017-01-28
forum: General Help
---

### Post by eldavar on 2017-01-28
Hello friends! I've been having a problem with my computer unexpectedly shutting off when the CPU is under a relatively heavy load. I've got what I think is a decent machine here, and I don't think the stuff I'm doing should be taxing enough to cause the machine to crash. 

Here's the setup (pasted from SysInfo): 
Release Ubuntu 16.04 (xenial)
GNOME 3.18.2 (Ubuntu)
Kernel 4.4.0-59-generic (#80-Ubuntu SMP Fri Jan 6 17:47:47 UTC 2017)
AMD FX(tm)-8320 Eight-Core Processor
Memory total 15946 MiB
Swap total 8088 MiB
NVIDIA GeForce GTX 650

I'm not sure how much of that is relevant, or if there's other info needed, so just tell me if it is. 

So, here's what's happening: Whenever I'm video chatting with Skype or Hangouts, or streaming a movie via Plex, the CPU usage spikes way up and so does the temp. After a short time, usually between 5-10 minutes, the computer suddenly shuts off without warning. I'm thinking this must be a temperature issue that's causing the crash, which I find a little unusual since I've got seven fans inside the case (2 on the door pointing in, 2 on the front pointing in/back, 2 on the back pointing out, and 1 on the top pointing down). I actually thought 7 fans was overkill, but apparently not? 

I installed Psensor, which seems to validate my guess that the problem is a temp issue, because when I'm video chatting or using Plex the AMD CPU temp jumps way up from it's usual 30-40 degrees C (is that a normal temp?) to over 80 degrees C. The fan speeds also spike and I can hear them too. 

But, I don't know what some of the generic items in Psensor actually are. I read that Asus boards normally use the asus_atk0110 driver for temp monitoring, so maybe I'd get more specific info from that? But I'd have to add that driver as a module. That's getting a little over my head, though. 

I found a [man page for "aibs"]("http://manpages.ubuntu.com/manpages/precise/man4/aibs.4freebsd.html") which looks like (I think) the atk0110 driver. I also found another [page talking about ATK0110 and "HWMON"]("http://cateee.net/lkddb/web-lkddb/SENSORS_ATK0110.html") but I don't know what that is or how I would use it (or if it's even for Ubuntu).

Basically, I'm trying to fix this temp crashing problem, and I thought starting with more accurate sensor data from the Asus driver might be useful. But the man page says this:
```

To compile this driver into the kernel, place the following lines in your kernel configuration file:

           device acpi
           device aibs

Alternatively, to load the driver as a module at boot time, place the following lines in loader.conf(5):

           acpi_load="YES"
           aibs_load="YES"
```
I don't know how to do that and I'm afraid of screwing up my system. I'd appreciate it if somebody can tell me how to do this properly. If anybody can help me figure out why my machine keeps shutting off, I'd really appreciate that too. I'm not sure where to find crash logs, and looking through the syslog doesn't tell me anything I can understand. Sorry for the long post!

---

### Post by QIII on 2017-01-28
Don't bother with adding more sensors.  You are clearly experiencing thermal shutdowns.  You need to determine what is wrong with your cooling solution.

Did you assemble the machine?

---

### Post by yetimon_64 on 2017-01-28
> **eldavar said:**
> ...way up from it's usual 30-40 degrees C (is that a normal temp?) to over 80 degrees C. The fan speeds also spike and I can hear them too. ...

Normal temp sounds about right, but that load temp is dangerously high, I'd stop using it; with that shutting down behaviour it sounds like the machine is trying to protect the CPU from damage, most probably done by the motherboard itself.
 
From what I had with an AMD Phenom 9750 quad core the critical temp for them is 62 deg C. I just went [[COLOR=#0000ff]--here--[/COLOR]]("http://www.tomshardware.com/answers/id-1921786/max-8320-temperature.html")
and your model is the same critical temperature. When I first ran my AMD (Phenom 9750) the temps were hitting critical at about 55-70% loading on all four cores no matter what I tried with fans and Arctic Silver thermal paste etc.

My quad core machine now processes all four cores at 100 % while video encoding with ffmpeg etc and never gets more than about 55 to 58 degrees C, nicely "sub critical" at "full load". The answer for my desktop unit, even with multiple fans including a 200 mm top case fan, was a fully enclosed water system cooling unit from Corsair. The unit I bought was the H50 unit (I don't think they produce that particular model nowadays) and it still works well after 7 to 8 years later.

From my experience building my own tower with an AMD processor, two things helped me greatly; the Corsair water cooling unit for the CPU and Artic Silver thermal paste. Still using the tower, whenever I'm around where it is, to this day at full loading :).

---

### Post by ian-weisser on 2017-01-28
QIII and yetimon_64 are right. You know the problem and you have the data you need. Time to start budgeting for a bigger, better cooler.

---

### Post by thehipho on 2017-01-28
> I installed Psensor, which seems to validate my guess that the problem is a temp issue, because when I'm video chatting or using Plex the AMD CPU temp jumps way up from it's usual 30-40 degrees C (is that a normal temp?) to over 80 degrees C. The fan speeds also spike and I can hear them too. 

If the thermal paste is applied correctly it shouldn't over-heat, or it could just be that you have a bad cpu?

---

### Post by HereInOz on 2017-01-28
Just a question:  When the temperature spikes up and the fans go hard at it, what happens to the actual temperature of the CPU heatsink?  It is OK to touch the heatsink while the computer is running, but maybe make sure you are earthed to the PC case at the time, just in case you have generated some static voltage.  

If the CPU heatsink heats up, and is noticeably warmer to the touch, then you have a cooling problem as outlined above, but if the heatsink does not get appreciably warmer, it may be that you have a heat transfer issue, or a heatsink mounted incorrectly, and not properly contacting the CPU.

Either way, a good quality water cooling kit is a good solution.

---

### Post by Keith_Helms on 2017-01-29
> **thehipho said:**
> If the thermal paste is applied correctly it shouldn't over-heat, or it could just be that you have a bad cpu?

Thermal paste helps transfer heat more efficiently to the cpu heatsink and fan.  If the heatsink and fan do not themselves provide sufficient cooling, the paste won't fix that problem.  The problem may be due to needing a better cpu fan, needing better case airflow/fans, or it could possibly be aggravated by the case being placed in a poor airflow location such as stuck in the back of a shelf.

---

### Post by eldavar on 2017-01-29
Thank you all for your insight and suggestions. 

The case is not stuck in a cabinet or wedged in between anything. It sits quite comfortably on the desk and there is unobstructed air flow on all sides. 

We assembled this machine ourselves about 6 months ago. I have a friend who works in a computer shop and builds custom gaming rigs regularly, and I trust that he knew what he was doing. And yes, Arctic Silver paste was used, and all of the components including the CPU heat sink are fitted and situated properly. All of the major components were brand new at the time as well, so wouldn't it be unlikely that the CPU or another part is faulty? 

Would it make sense to remove the CPU and re-apply a fresh coat of the Arctic Silver? Maybe it didn't get completely covered the first time. 

I have no experience with liquid cooling. When I was buying the components last year, I remember reading on the AMD website that this particular CPU, the FX8000 series, was the most powerful processor line that they offered that did not require a liquid cooling rig. I will have to start all over and learn about liquid cooling setups. 

Could the problem be that I need better fans? The fans are the only thing that wasn't brand new when we assembled this machine.

---

### Post by yetimon_64 on 2017-01-29
> **eldavar said:**
> ...We assembled this machine ourselves about 6 months ago...
Would it make sense to remove the CPU and re-apply a fresh coat of the Arctic Silver? ...
I tend to like to redo the thermal paste about every 6 to 8 months when the desktop is getting regular heavy use. Thermal paste can tend to degrade in quality over time especially if you regularly give the CPU a good loading workout.

> **eldavar said:**
> I have no experience with liquid cooling. When I was buying the components last year, I remember reading on the AMD website that this particular CPU, the FX8000 series, was the most powerful processor line that they offered that did not require a liquid cooling rig. I will have to start all over and learn about liquid cooling setups....

If you can repaste your own CPU and can read a set of instructions fully and carefully before attempting the job, installing a water cooler unit is a breeze. I was reluctant to do it myself until told the hardest part of the job is pasting the CPU/heatsink which I'd already done a few times. My first build of the water cooled set up took about an hour, most of that being carefully reading the instructions multiple times to ensure I fully understood before doing anything. Someone used to the task would likely complete it in 5 to 10 minutes. The water pump head that mounts on the CPU does require a special socket bracket that replaces the existing socket heatsink mounting bracket; this requires the motherboard to be completely removed from its backing mounts for the installation of the new unit.

> **eldavar said:**
> Could the problem be that I need better fans? The fans are the only thing that wasn't brand new when we assembled this machine. I suspect changing only the fans will have minimal if any impact on the overheating problem. If they are actually running currently, replacing them with new fans will likely give very little change to the current level of airflow. Getting the heat away from the CPU as quickly as possible is the key to reducing the temperature, water cooling with a water pump in the head mounted on the CPU and a heat exchange radiator and fan on the back of the case is a very effective means of removing heat quickly away from the CPU to outside the case altogether.

---

