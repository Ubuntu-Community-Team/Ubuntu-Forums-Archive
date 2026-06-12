---
title: "Stoppping non-essential services to achieve faster startup"
date: 2012-12-26
forum: General Help
---

### Post by Holmes.Sherlock on 2012-12-26
I am using Ubuntu 12.04. Below is the attached screenshot of **rcconf** tool. Can anyone please identify which are the non-essential services which I can safely disable to achieve faster startup?

---

### Post by ibjsb4 on 2012-12-26
I do not use rcconf, but "system monitor" will give a description of running processes and you can kill them from there and a reboot will restore killed processes.  Just a good place to play with processes.

---

### Post by Cheesehead on 2012-12-26
It depends upon how you use your system. If, for example, you never use any kind of audio, then you probably don't need pulseaudio upon startup.

Most of those services look essential to me.
Developers did a LOT of work a couple cycles ago to reduce/remove/restructure startup processes and daemons precisely to speed up boot time. And they made a lot of improvements and are still making improvements.

Many of the improvements these days involve changing always-on-but-sleeping daemons into upstart- or dbus-triggered single-shot scripts. The incremental improvement of each is minor at this point....

---

### Post by Holmes.Sherlock on 2012-12-26
> **ibjsb4 said:**
> I do not use rcconf, but "system monitor" will give a description of running processes and you can kill them from there and a reboot will restore killed processes.  Just a good place to play with processes.
It gives you process view, much like task manager in Windows.

---

### Post by offgridguy on 2012-12-26
> **ibjsb4 said:**
> I do not use rcconf, but "system monitor" will give a description of running processes and you can kill them from there and a reboot will restore killed processes.  Just a good place to play with processes.
Thanks, i will try this.

---

### Post by stinkeye on 2012-12-26
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=12321108&postcount=5") for disabling services.
Don't know much about particular services and just disabled a couple I don't use.
Can't say it affected boot time but I did notice a drop in memory use.

---

### Post by oldos2er on 2012-12-26
Since Ubuntu uses upstart for most (?) services now, I think you should follow the advice given by stinkeye rather than using rcconf.

---

### Post by dcstar on 2012-12-27
> **Cheesehead said:**
> 
............
Many of the improvements these days involve changing always-on-but-sleeping daemons into upstart- or dbus-triggered single-shot scripts. The incremental improvement of each is minor at this point....

Yep, basically a waste of time that will end up breaking a system and then having more posts in this forum of the "wah wah - my system doesn't work properly any more" type.

---

### Post by Holmes.Sherlock on 2012-12-27
> **dcstar said:**
> Yep, basically a waste of time that will end up breaking a system and then having more posts in this forum of the "wah wah - my system doesn't work properly any more" type.
Basically what you people are trying to point out is, not much visible performance improvement can be achieved by tuning those services.

BTW, playing around with a system and breaking and reconstructing it is the best way to learn an OS. Isn't it?

---

### Post by ibjsb4 on 2012-12-27
> **dcstar said:**
> Yep, basically a waste of time that will end up breaking a system and then having more posts in this forum of the "wah wah - my system doesn't work properly any more" type.

Did you get a piece of coal for Christmas?

---

