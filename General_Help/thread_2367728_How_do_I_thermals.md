---
title: "How do I thermals?"
date: 2017-08-02
forum: General Help
---

### Post by The musmula on 2017-08-02
So I've noticed that Windows manages to keep my laptop under 30 degrees (C) while I'm just browsing and dealing with documentation. During that time my laptops fans are either completely off or they're spinning super slowly. However, my Ubuntu gnome installation heats up within a minute to 50 degrees and keeps the fans spinning pretty quickly although not at max. One more thing I noticed with Windows is that task manager reports my CPU clock to be under 1GHz most of the time but I don't really know where I could get a reading of that on Ubuntu, is that even a relevant piece of information? I dunno. Battery life isn't that important to me but Ubuntu eats up my 97Wh battery in like 2 hours so... sounds like something I might wanna be concerned about.

My question then is: how is Windows doing this and how do I get close to that performance on Ubuntu?

I've tried following this guide: [https://www.reddit.com/r/Dell/comments/5y3rii/xps_9560_battery_life_optimization_and_fan/](https://www.reddit.com/r/Dell/comments/5y3rii/xps_9560_battery_life_optimization_and_fan/)

But I've found it hard to follow some advice like turning off the Nvidia GPU... "[FONT=Arial]As for the moment I don't really need the Nvidia card on Linux[/FONT]"... well... I do. Not always, but quite often. There is a thing where I can disable the 1050 in Nvidias settings manager with a "performance profile" but that then crashes my session and I have to revert those changes back through tty.

Then there's "UNDERVOLT WITH INTEL XTU" which I don't really understand the point of... Sometimes I do need all of the GHz, it's why I bought this thing in the first place. Is that permanent? 

And then there's the i8kutils thing which I can't get to work. I get an error when trying to run the "make smm" command and none of the fixes in the comments seem to help.

At the end of the day... I don't get why I have to follow a guide like this anyway. It works out of the box on Windows, surely things can't get complicated to the point of "compile i8kutils so you have access to a feature that is so risky to use that it wasn't included in the binaries"

Thanks in advance

---

### Post by Autodave on 2017-08-02
To answer one of you questions, *psensor *is a program that will gibe you temps, fan speeds, etc. Software center as well as Synaptic have it.

---

### Post by The musmula on 2017-08-02
Yeah, psensor is how I know that my thermals are at 50 on Linux. It won't give me fan speeds tho unless I have i8kutils installed

---

### Post by The musmula on 2017-08-02
So I just restarted my machine to get some work done on Ubuntu and I fired up psensor right away to get an idea of how quickly things heat up and most of the temps were between 50-60 degrees which doesn't make much sense since I was watching a movie on Windows literally 20 seconds before that with speedfan on which reported temperatures of 25-30 degrees. And the reason I can't make heads or tails of that is because if my fan speeds are controlled by the BIOS as mentioned in the reddit post linked in my initial post on this thread, then the BIOS should always have correct temperature readings - regardless of the operating system in use. Does anybody have an idea as to what's going on? Is it possible for my laptop to heat up like that within the bootup time?
Also, I can't feel a temperature difference on the deck

---

