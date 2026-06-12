---
title: "How do i control the CPU-fanspeed?"
date: 2008-03-24
forum: General Help
---

### Post by mikkel13 on 2008-03-24
I'm new at Ubuntu (7.10)... and I like it, in some way it is easier :P
But my CPU-fan is running at full speed all the time.... noisy! In windows I used Cool'n'Quiet, to control the speed, and the overclock of the CPU...
Isn't the any thing like that for Ubuntu?
Thanks... sorry for my bad English:(

---

### Post by chewearn on 2008-03-25
What CPU and mobo you have?

Install lm-sensors to monitor the temperature and fan speed:
```
sudo aptitude install lm-sensors
sudo sensors-detect
```

Check the sensor readings:
```
sensors
```

---

### Post by mikkel13 on 2008-03-25
... Now I can read the temp. by the code: sensors... but should it also change the cpu-fanspeed?, it is still running at full speed.
My cpu is an AMD x2 64 2600+
Motherboard: MSI Platinum K9N

---

### Post by fjgaude on 2008-03-25
Likely there is a setting in the BIOS of your motherboard that has a function as to how the CPU fan is handled. At bootup, usually you can get into the BIOS using something like Del key, or F2. Your motherboard manual has it all.

---

### Post by chewearn on 2008-03-25
> **mikkel13 said:**
> ... Now I can read the temp. by the code: sensors... but should it also change the cpu-fanspeed?, it is still running at full speed.
My cpu is an AMD x2 64 2600+
Motherboard: MSI Platinum K9N

It's not for controlling the fan speed, but to let you check the temperatures, so you are sure the full fan speed is not due to overheating, or anything like that.


> **fjgaude said:**
> Likely there is a setting in the BIOS of your motherboard that has a function as to how the CPU fan is handled. At bootup, usually you can get into the BIOS using something like Del key, or F2. Your motherboard manual has it all.

Yeah, I'm now using BIOS to control my fan speed as well.  Previously, I have tried using the ubuntu howto below, but it doesn't work so well.
[http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)

---

### Post by mikkel13 on 2008-03-26
Thanks...
Now my fan is running at 2220 rpm instead of 2766 rpm, took some of the noise :D
But in windows I used cool'n'quiet, and I could get it down to about 700 rpm - nearly soundless :P
Can't I do this by using the BIOS?, or do I have to go all through the link you gave me, and hope it works?

---

### Post by chewearn on 2008-03-26
> **mikkel13 said:**
> 
Can't I do this by using the BIOS?,

Depends on how many adjustment you can make in the BIOS.

In my PC, I can set three temperature-vs-fan speed combinations.  That means I can have four fan speed zones, in theory.  In practice, it take a lot of tweaking to get the settings right.  Plus, the settings are unscaled numbers, so you have to do trial-and-errors.

>  or do I have to go all through the link you gave me, and hope it works?I tried the links; it worked quite well for a few weeks.

But once in a while (randomly), the fan will get out of calibration.  My PC is on 24-7; it got a bit dangerous when the temperature hit the roof, without the fan turning on.  And I was away sleeping, or at work.

You can try the link, if you think it's worth the risk.  Or if you don't leave your PC unattended for hours on end.

---

### Post by fragos on 2008-03-27
A noisey fan can be quieted down by slowing it down but the noise is a function of cheap bearings in the fan.  Better quality fans aren't expensive.  Good fans have DB noise rattings which you can compare.

---

### Post by mikkel13 on 2008-03-30
I don't want to buy a new fan, I'm really happy with my Zalman-fan, it keeps my PC cool on 35 C with 700 rpm :D

Is it possible to run Cool'n'Quiet with Wine?

---

### Post by fragos on 2008-03-30
I don't know about Cool'n'Quiet with Wine. There are some things you can do to reduce the noise of things vibrating against each other. For one you can place something soft under your PC. I trimed down a piece of no skid matterial used in tool boxes. You can also insulate things you mount to your case like fans and PS with fiber or nylon washers. Antec has a kit you couls consider. Even the metal panels in your case can vibrate. You can test this by pressing against each panel with your hand and listen to any changes in sound. I used a Zalman fan mate to slow down a noisy fan. Many boxes have multiple fans -- CPU, PS and case for example. Perhaps one of the other fans is the culprit. I would think your slowed down Zalman isn't the source of fan noise. You may be able to test the other fans by pressing down on the center of each fan -- of course avoiding the blades.

---

### Post by mikkel13 on 2008-03-31
My cabinet is an Antec, a model with low noise level fans and silicone between the cabinet and the PSU, HDs, flour, etc. My graphic card fan is running at lowest level, and there isn't any other fans than the CPU-fan. I am really sure that it is my CPU-fan.

In windows I was able to set the cpu-fan to 700 rpm, and there was no sound... Isn't there no way to do this in Ubuntu???

---

### Post by bill516 on 2008-03-31
I did a quick Google search using the phrase "CPU Fan Speed Ubuntu" and turned up a list of possibilities.  The first was at

[http://wiki.archlinux.org/index.php/Fan_speed_control](http://wiki.archlinux.org/index.php/Fan_speed_control)

and it appears to fit advice being given by others here.   Not quite so simple as the app you have referenced, but it looks like it will do what you want it to do for you.

By all means watch your temps.  Your Zalman/Antec combination is quite good.  You should run quietly.

I have a CoolerMaster case with aftermarket power supply and CPU fan installed.  Under Linux the machine is virtually silent.  (At the moment it is entirely silent and has been for the last two hours.)    Running XP/Adobe Photo Elements the same maachine spins its little heart out and sounds off accordingly.

---

### Post by mikkel13 on 2008-04-02
I tried the link, but didn't get longer than to the pwmconfig.
When I run "sudo pwmconfig", it says:
[I]
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

Found the following devices:
   hwmon0/device is k8temp
   hwmon1/device is w83627ehf

Found the following PWM controls:
   hwmon1/device/pwm1
hwmon1/device/pwm1_enable stuck to 1
Failed to set pwmhwmon1/device/pwm1 to full speed
Something's wrong, check your fans![/I]

Does it mean that my motherboard doesn't suport pwm?

---

