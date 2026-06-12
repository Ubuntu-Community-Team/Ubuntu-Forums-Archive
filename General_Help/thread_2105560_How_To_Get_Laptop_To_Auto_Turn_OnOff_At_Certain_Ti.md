---
title: "How To Get Laptop To Auto Turn On/Off At Certain Times Of The Day"
date: 2013-01-16
forum: General Help
---

### Post by Ngative0 on 2013-01-16
Hi, I'm new to this forum, but not that new to Ubutnu.
I'm running my Lenovo Thinkpad laptop, with an Intel Core 2 Duo CPU, (Originally Windows 7 OS), with Ubuntu 12.10(only Ubuntu 12.10, no Windows, don't ask me how, I'd rather not say how, mainly cuz my memories of how I did it are foggy, all I know is I tried to remove Ubuntu and re-install a newer version, and when I THOUGHT I did that, I rebooted my laptop, and it showed an error saying there was no something... and I just booted Ubuntu 12.04 onto my computer with a cd, & upgraded it's OS, & now it runs ONLY Ubuntu12.10).
And I need some help because I'm in the middle of my special Martial Arts Training, and Workouts, and these Workouts and Special Training takes a lot out of my body, and there are some friends with good intentions, but with very little understanding and patience, and if I show them what my training did to me, they'd freak, & I don't need more stress in my life.
SOOOOOOOOOO... I need a way for my laptop to automatically turn on at a certain time in the morning, and shut off at a certain time at night.
If anyone has any idea how to help me achieve this state on my laptop, that would be appreciated. I don't really care if I'm able to turn it back on between it shutting off, and turning on. If I can: great. If not: I don't really care.
Just need laptop to auto turn off at night, and auto turn on in the morning.
Thanks for anyone who gives advice on a program to download off of the software centre, or any other advice, I just need it to work, and it needs to be free, and not a trial. Thanks.

Mess with the Elite, Prepare for Defeat.(-0)

---

### Post by ljmhk on 2013-01-16
This thread should help with the automatic start up:

[http://ubuntuforums.org/showthread.php?t=858838](http://ubuntuforums.org/showthread.php?t=858838)

As for the shutdown you should be able to use cron to shedule a shutdown.

The command you will likely need is: "sudo shutdown now"

Here is some additional information on using the cron:

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

Good luck!

---

### Post by Toz on 2013-01-16
Hello and welcome to the forums.

**rtcwake** will do this for you. Have a look here for more information: [http://askubuntu.com/questions/61708/automatically-sleep-and-wake-up-at-specific-times]("http://askubuntu.com/questions/61708/automatically-sleep-and-wake-up-at-specific-times")

---

### Post by tgalati4 on 2013-01-16
Most laptops will sleep under Ubuntu.  So you don't have to turn it on and off.  Just close the lid and see what happens.  Then lift the lid and see what happens.  As long as you keep some power to it, the most batteries will last several hours in sleep.

Also, in BIOS, there is usually a tab that allows you to put in a time for wake and/or shutdown.

I would see a doctor before you REALLY freak your friends out.

---

