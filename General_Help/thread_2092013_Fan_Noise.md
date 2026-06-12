---
title: "Fan Noise"
date: 2012-12-06
forum: General Help
---

### Post by Pbethe on 2012-12-06
It is driving me crazy.  For long periods of time it will make noise like it is trying to start up, then suddenly go silent.  This is a Compaq Presario F572US notebook.  Currently, the Quanta 30D3 motherboard is running 50 degrees C, and the AMD Turion 64 processors are 55 and 54.  The hard drive is a cool 35 degrees C.
Is there some way I can diagnose what is going on without opening up the case?  I hope there is some software way to find out what fans this machine has and why one of them is complaining so loudly.

---

### Post by Pbethe on 2012-12-07
OK, I have looked into /proc/acpi and can see this:  cat /proc/acpi/thermal_zone/THRM/t*
temperature:             43 C
critical (S5):           95 C
passive:                 88 C: tc1=2 tc2=3 tsp=100 devices=CPU0 

There is a /proc/acpi/fan directory with nothing in it.  The Compaq is on a cooling pad whose fan is whirring quite nicely, but this internal fan is making evil noises.  I have tried cleaning the Compaq by spraying air into the vents, but I don't see any dust coming out.  Help!

---

### Post by Kirk Schnable on 2012-12-07
Without hearing the noise, it's hard to tell. It could be a fan bearing going bad or something, and when the fan has run for a certain length of time it either seizes up and stops spinning, or the bearing gets enough oomph to turn the fan silently again.  Unfortunately, if a fan is going bad, you're not going to get around opening up the case to fix it. 

I've never seen this on a laptop, but maybe you'll get lucky... If your motherboard has a nice BIOS, there may be a section called PC Health where you can look at your thermal sensor readings, or possibly even manually adjust the speed of PWM fans or the voltage of older fans.

---

### Post by Pbethe on 2012-12-12
Yes, I may just have to open it up and have a look inside.  I have upgraded the memory in it; I am not a total hardware noob.  I have been reading about software that you can use to control the fans, but if the fan is dying, there is not much point in doing that.

---

### Post by Kirk Schnable on 2012-12-13
> **Pbethe said:**
> Yes, I may just have to open it up and have a look inside.  I have upgraded the memory in it; I am not a total hardware noob.  I have been reading about software that you can use to control the fans, but if the fan is dying, there is not much point in doing that.

Did your case come with any fans?  I've had a few cases come with fans and within 12 months they were making horrible noises when the computer was booting.  After a few minutes of running, they'd become silent.

On the most recent case, my media center case came with two cheap rear exhaust fans.  I opened it up during boot, and used my finger on the flat section of the middle of the fan to stop the fan momentarily.  This was how I figured out which case fan was at fault.  Since case fans are more of a luxury than a necessity, I simply unplugged the noisy one.  If you think it's your CPU or power supply fan, I definitely don't recommend stopping them for any length of time, and they will need to be replaced.

---

### Post by Pbethe on 2012-12-16
That is the thing:  I don't know how many fans are in there.  I infer the presence of this one by the noise.  It is right by the power button.  I can attach a pic I got off the Web.  Yes, that noise comes from the upper left corner.

---

### Post by Rockstarever on 2012-12-16
well there, every pc and even latops make up the start up noise. so its is quite normal. its kind of a normal fan check and test run procedure.

---

### Post by Pbethe on 2012-12-16
> **Rockstarever said:**
> well there, every pc and even latops make up the start up noise. so its is quite normal. its kind of a normal fan check and test run procedure.

This is not normal.  I have had this machine for five years, and recently it started making these awful noises for hours at a time.

---

### Post by hawthornso23 on 2012-12-16
My guess would be that it is a hardware issue. Software issues seldom cause the machine to suddenly start making unusual noises. And if that is the case then seeking a software solution is probably going to teach you a lot about ACPI and interesting kernel stuff, but I really doubt it will fix the problem.

If you are lucky then opening the back and simply cleaning out the dust will fix it. If not you might be looking at replacing a fan.

---

### Post by Pbethe on 2013-01-06
> **hawthornso23 said:**
> My guess would be that it is a hardware issue. Software issues seldom cause the machine to suddenly start making unusual noises. And if that is the case then seeking a software solution is probably going to teach you a lot about ACPI and interesting kernel stuff, but I really doubt it will fix the problem.

If you are lucky then opening the back and simply cleaning out the dust will fix it. If not you might be looking at replacing a fan.

It look like I or somebody else will have to open it up.  It has been pretty quiet for a while, but it is acting up again.  It is really weird how the noise will sometimes suddenly stop.  Now it is making a surging noise, as if a fan is trying to start up.  The good news it that the temperature never gets above 72 degrees C in the core, and now it is 55.  Still, the Whaa, Whaa, Whaa . . . can be really annoying.

---

### Post by Chogan on 2013-01-06
in some cases, installing "Jupiter" solve such a problems.

---

