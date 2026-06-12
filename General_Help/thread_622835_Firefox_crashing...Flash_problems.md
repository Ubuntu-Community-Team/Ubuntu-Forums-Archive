---
title: "Firefox crashing...Flash problems"
date: 2007-11-25
forum: General Help
---

### Post by PRGUY85 on 2007-11-25
Hey:

I have Flash 9 installed on my computer.  Recently, Firefox, Gran Paradiso and Epiphany (all based on the firefox structure) have been crashing on flash video sites.  This also includes flash sites such as pandora.com.  If I open firefox and watch a youtube video, it works well.  However, if I watch a second video, firefox stops responding and I have to quit the program.  The only way to watch a second video is to close firefox and open it again...
Any ideas?

---

### Post by hailtothethief on 2007-11-25
From a terminal [Applications > Accessories > Terminal]
type in:
```
sudo aptitude reinstall libflash-mozplugin
```


If that doesn't work:

```
sudo aptitude reinstall firefox libflash-mozplugin
```

Hope that helps

---

### Post by aldous on 2007-12-09
I'm having the same problem and the solution posted does not solve anything for me.

---

### Post by faeriedragon on 2008-01-26
I'm having a similar problem, however, I cannot get anything on Youtube or *any* site that uses Flash to work. In fact, Firefox will crash and burn. Or will lock up my entire computer (but that may be a different issue that I'm trying to figure out...We're thinking "hardware"...but anyway....). 

I installed Flash from Adobe's site and did everything according to their instructions. Not sure if FF doesn't recognise that I have Flash installed or if I need to do something I'm overlooking....It's been a while since I've had to config my browser. 

I'm a noob at the whole 'nix/Ubuntu world, so please be gentle. 

Thanks! :)

---

### Post by browndruid on 2008-01-27
If you're using an AMD64 architecture, then you'll need to follow the instructions [on this thread]("http://ubuntuforums.org/showthread.php?t=476924").

That, however, seems to somehow not work completely for me. So I had to install f32-bit Firefox and flash for it, along with some other plug-ins, using [this script]("http://ubuntuforums.org/showthread.php?t=202537"). That didn't work for a while for me, then suddenly worked. I don't know why, and I don't have the know-how to figure out why. If anyone would explain that to me, though, I would be very grateful.

Hope that helps!

---

