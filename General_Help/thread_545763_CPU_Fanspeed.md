---
title: "CPU Fanspeed"
date: 2007-09-08
forum: General Help
---

### Post by hfw on 2007-09-08
I am having trouble setting my fanspeed.  It runs full speed all the time.  I read the howto: in [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29), which help me set up lm-sensors, but when I try the next step:

 How to control fan speed (lm-sensors)

Install and config lm-sensors first, see section above. Then run pwmconfig to test your fans

pwmconfig

I get:

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

The howto: doesn't say what to do when you can't control fan speed.  Just what to do when you can.  I'm not sure where to go from here.  Any help would be appreciated.

Thanks,
Hal

---

### Post by grendel38 on 2007-09-21
I had the same problem with my Sony VAIO desktop.  I followed the directions at that link, and that fixed it.  In addition to installing lm-sensors you have to create the mkdev.sh and follow through on the rest of the instructions in the "section above" as referred to in the link.

Until I did that, I got the same response you did.  I'd install lm-sensors, and run it, but just get the message that no controllable sensors were found.  After following the steps in the link, lm-sensors could find the sensors and control the fan speed.

---

### Post by Krudtugle on 2007-09-27
I followed these instructions and it works partially. pwmconfig can clearly control the fan speed. When I run it, it tests the speed of the fans (although I only have one, the CPU fan). 

As a step in pwmconfig, it creates some kind of correlation during which the fan speed is obviously controlled (at 992 rpm it's nicely quiet).

Would you like to generate a detailed correlation (y)? y
    PWM 255 FAN 3068
    PWM 240 FAN 2766
    PWM 225 FAN 2445
    PWM 210 FAN 2311
    PWM 195 FAN 2191
    PWM 180 FAN 2083
    PWM 165 FAN 1962
    PWM 150 FAN 1814
    PWM 135 FAN 1687
    PWM 120 FAN 1591
    PWM 105 FAN 1454
    PWM 90 FAN 1339
    PWM 75 FAN 1231
    PWM 60 FAN 998
    PWM 45 FAN 981
    PWM 30 FAN 992
    PWM 15 FAN 981
    PWM 0 FAN 992

But then as a further step, pwmconfig asks if the fanspeed shall be automatically adapted to temperature changes and there is some configuration utility I walked through (see below). After having done this a couple of times the result is:

The fancontrol script can automatically respond to temperature changes
of your system by changing fanspeeds.
Do you want to set up its configuration file now (y)? 
What should be the path to your fancontrol config file (/etc/fancontrol)? 
Loading configuration from /etc/fancontrol ...

Select fan output to configure, or other action:
1) 9191-0290/pwm2      3) Just quit           5) Show configuration
2) Change INTERVAL     4) Save and quit
select (1-n): 5

Common Settings:
INTERVAL=10

Settings of 9191-0290/pwm2:
  Depends on 9191-0290/temp2_input
  Controls 9191-0290/fan2_input
  MINTEMP=0
  MAXTEMP=60
  MINSTART=80
  MINSTOP=80

select (1-n): 4

Saving configuration to /etc/fancontrol...
Configuration saved
laerke@ubuntu:~$ 

The MINSTART and MINSTOP values pertain to pwm, not fan rpm. So, the configuration is saved, but the fan speed is NOT automatically asjusted. Now it runs on full speed all the time (above 3000 rpm).  This is worse than before I installed lm-sensors.

I also followed the rest of the instructions in the link in the post below:

Test it
/etc/init.d/fancontrol start

and
/etc/init.d/fancontrol stop

But when running /etc/init.d/fancontrol start nothing happens, only this:

laerke@ubuntu:~$ sudo /etc/init.d/fancontrol start
 * Starting fancontrol daemon...                                             [ OK ] 
laerke@ubuntu:~$ 

So, how do I really control the fan speed? And how is the configuration file in pwmconfig related to the one I create myself (/etc/init.d/fancontrol) according to the instructions in [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29?](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29?)

---

### Post by grendel38 on 2007-09-27
not sure if I can help, but here's my two cents:

> I followed these instructions and it works partially. pwmconfig can clearly control the fan speed. When I run it, it tests the speed of the fans (although I only have one, the CPU fan).

As a step in pwmconfig, it creates some kind of correlation during which the fan speed is obviously controlled (at 992 rpm it's nicely quiet).

[snip]

> The MINSTART and MINSTOP values pertain to pwm, not fan rpm. So, the configuration is saved, but the fan speed is NOT automatically asjusted. Now it runs on full speed all the time (above 3000 rpm).  This is worse than before I installed lm-sensors.

Settings of 9191-0290/pwm2:
  Depends on 9191-0290/temp2_input
  Controls 9191-0290/fan2_input
  MINTEMP=0
  MAXTEMP=60
  MINSTART=80
  MINSTOP=80

I think the problem is your pwm settings are both the same -- the idea is to set a set a fan start temp at which the fan is running at slow speed with low power, and a maximum temp at which the fan should be running at a fast speed for maximum cooling.  The way you have it set up, the spins at the same speed all the time.  There needs to be a range between MINSTART and MINSTOP.  Go back, and rerun the utility, this time selecting different value for MINSTARTand MINSTOP.


> I also followed the rest of the instructions in the link in the post below:

Test it
/etc/init.d/fancontrol start

and
/etc/init.d/fancontrol stop

But when running /etc/init.d/fancontrol start nothing happens, only this:

laerke@ubuntu:~$ sudo /etc/init.d/fancontrol start
 * Starting fancontrol daemon...                                             [ OK ]

[snip]

that means the script is working -- it will control the fan speed according to the values you input -- but like I said, you have to specify a power range along with a temperature range.  The way you have it set up, the fan receives the same power regardless of the temperature.

---

### Post by Total_Biscuit on 2007-09-27
You have it (I think).  The other item to check is that the correct temperature sensor, i.e. the one for the cpu, is being used as the reference for controlling the fan.  In the meantime, here's my - working perfectly - /etc/fancontrol for example:
```
INTERVAL=10
FCTEMPS= 9191-0290/pwm2=9191-0290/temp2_input
FCFANS= 9191-0290/pwm2=9191-0290/fan2_input
MINTEMP= 9191-0290/pwm2=10
MAXTEMP= 9191-0290/pwm2=60
MINSTART= 9191-0290/pwm2=10
MINSTOP= 9191-0290/pwm2=0
```

---

### Post by Krudtugle on 2007-10-02
OK, thanks! It seems to work fine now (I use the same values as Total_Biscuit).

Anyone knows the logic behind the parameter names MINSTART and MINSTOP? I find them a bit cryptic...

---

### Post by Total_Biscuit on 2007-10-03
Take a look at /usr/share/doc/lm-sensors/doc/fancontrol.txt where everything is explained.

---

### Post by Gumper on 2007-10-04
Does anyone know how to change the fan control settings without having to run pwmconfig command again?

Thanks

---

### Post by Gumper on 2007-10-04
One more question. Is it possible to somehow configure this to work with the temperature coming from your hd? I'm currently using hddtemp to display my hd temps in conky and it would be nice to be able to use this data to control a case fan pulling air over my hd.

---

