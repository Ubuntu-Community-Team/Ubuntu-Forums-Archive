---
title: "Problem with sound at startup"
date: 2020-05-22
forum: General Help
---

### Post by lesliek2 on 2020-05-22
I'm using Ubuntu 16.04.

I have headphones plugged into my computer all the time and listen to sound only through them. Some recent update of one or more things has affected my ability to do that.

Before, I'd get sound from my headphones automatically after starting up my computer.

Now, I have to open "Volume Control" and go to the tab "Output Devices". Below the words "Built-in Audio Analog Stereo" is the word "Port" with two options, "Speakers" and "Headphones (Unplugged)". "Speakers" is automatically selected when I start up. I switch my selection to "Headphones (Unplugged)" and then I get sound through my headphones again.

What can I do to make sure that "Headphones (Unplugged)" is automatically selected on start up instead of "Speakers"?

Thanks,

Leslie

---

### Post by lesliek2 on 2020-05-22
Solved this problem by adding "set-sink-port 0 analog-output-headphones" to the end of etc/pulse/default.pa. Some update had replaced my existing default.pa, omitting that line.

---

