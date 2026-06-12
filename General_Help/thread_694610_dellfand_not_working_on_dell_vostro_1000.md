---
title: "dellfand not working on dell vostro 1000?"
date: 2008-02-12
forum: General Help
---

### Post by himynameiskevin on 2008-02-12
i have a vostro 1000 running gutsy with dellfand installed. i followed instructions from a thread i found on here, they had a vostro 1500. anyway.. the output from dellfand is this:

> v0.9: Fan 0 Status -1 Speed -1 CPU Temp -1C

i guess it's not even recognizing anything, which is no good. the processor temp gets over 50C occasionally (sometimes to 60C), but the fans usually kick in eventually and cool it down.

anyone have similar problems? any way to make dellfand function properly? i would like to continue using ubuntu, but i don't want to fry my laptop.

---

### Post by Blue Sassley on 2008-02-13
I'm having those same problems but mine will register the CPU temp just not the fan speed at all... I have a Vostro 1500 and I had to follow this to get them to work:

```
++++++++++++++++++++++++++++++++
Get fans to work
++++++++++++++++++++++++++++++++

Some people has complained that the fans don't work after the Ubuntu install. I have found that they do work however they seem to cut on way too late. I understand that you have to find a happy medium between battery life and cooling but sometimes the laptop seems unusually hot. So better safe than sorry. This fix will allow you to control the fans and set temperature based cut ons. This fix will sense 2 fans but apparently only one is controllable but thats enough to get your temps down

Hophead wrote:

Fan and temp control (install gkrellm)
1. sudo apt-get install i8kutils gkrellm gkrellm-i8k
2. sudo modprobe i8k force=1
3. sudo gedit /etc/modules
4. add the following line to the end of the file: i8k force=1
5. go to System > Preferences > Sessions > Startup Programs
6. Click ADD and put the command: gkrellm
Now you will see the GKrellm utility load at startup and you can then configure your fan thresholds in settings - plugins - Dell i8k

After installing gkrellm, I opened it and under Plugins, found Dell I8K Plugin. After enabling it, I saw that only the left fan was on. I changed the Temperature Units from Celsius to Fahrenheit, then the right fan came on. I thought this was a coincidence at first, but everytime I change it to Celsius, the right fan goes back off.

```

I got that from this thread:

[http://ubuntuforums.org/showthread.php?t=533073&highlight=fan+vostro+1500](http://ubuntuforums.org/showthread.php?t=533073&highlight=fan+vostro+1500)

But I too want to get dellfand working.

Blue

---

### Post by himynameiskevin on 2008-02-13
yeah i've also tried installing that, i can get the CPU temperature (occasionally, doesn't always work).. the fan control comes up, and it reads the fan speed at -22. if i click the fans to turn them on manually nothing happens.

i also did a little research and found that my processor, amd turion x2 tl-56, has a max temperature of 95C, the highest i've seen mine is around 62-65C, which i guess is in a "safe" zone but it still kind of worries me..

i suppose i could boot up windows and monitor the temperatures for a while, to see if i should even be worrying in the first place.

---

