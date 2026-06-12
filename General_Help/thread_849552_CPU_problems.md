---
title: "CPU problems"
date: 2008-07-04
forum: General Help
---

### Post by riksweeney on 2008-07-04
Hi,

Sometimes when I'm watching a movie or playing a game in MAME, my CPU fan will come on and the game / movie will slow down, almost as if something else is stealing all of the CPU time.

If I pause the game for a few seconds then its performance will be OK again for about a minute or so and then it'll do it again.

Perhaps there's something wrong with my XOrg configuration because I can't understand why I can't run something for an extended period of time without it grinding to a halt.

Has anyone encountered this problem before?

Toshiba Satellite M70 Gutsy Kubuntu

Thanks

Richard

---

### Post by lavinog on 2008-07-04
maybe the trackerd indexer is running.
there is another process that can do this. I forgot the name but i think it was for compiling all of the man pages...I remember it causing the same problem...I just let it do its thing (to about 30 mins) and it hasn't come back since then.

---

### Post by |{urse on 2008-07-04
sometimes programs go into indefinite postponement, it just happens. It's a problem with your software not your hardware. Try killing the tracker daemon as described above.

sudo killall trackerd

and run it again. perhaps you need a different version of the software or just need to recompile it.

---

### Post by Vivaldi Gloria on 2008-07-04
Open a terminal and start

```
top
```

or

```
htop
```

to find out which app uses the cpu most.

---

### Post by jsprz8382 on 2008-07-04
now that you guys mention it it might be some updates available that are taking some much cpu. Ill try killing them

---

### Post by riksweeney on 2008-07-04
OK, I'll give this a go and see what might suddenly be sucking up the CPU time.

Thanks

Richard

---

### Post by cariboo on 2008-07-04
Check you cpu temperature, if the fan comes on and things slow down, you might be having heat issues.

You can put an icon on the panel that show cpu temp as well as other temps. to install the sensors. Open Synaptic and search for lm-sensors, mark it for installation as well as sensors-applet. Once they are installed open up a terminal and enter:

```
sudo sensors-detect
```

Answer yes to all the questions. Reboot when it is done. Right click on the top panel, then add to panel, scroll down and select Harware Sensor Monitor. You should now have a sensor monitor on your panel. To change what sensors are monitored, right click on a sensor, then click preferences and then click the sensors tab and pick what you want. I personal have both cpu core temps, fan speed and all four of my hard drives monitored.

**Note:** this may not work on a laptop, but you can try it.

Jim

---

