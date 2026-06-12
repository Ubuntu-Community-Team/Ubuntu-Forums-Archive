---
title: "Recommendation for a system temperature monitoring program for Ubuntu 14.04?"
date: 2016-08-04
forum: General Help
---

### Post by giga+bytes on 2016-08-04
I just built a new Ubuntu-only PC (not dual-boot; no Windows), and am today starting it up and running tests to make sure everything works properly, plus I have a laptop with the same version of Ubuntu that has been problematic so I want to test that one too, so I need to keep an eye on the temperatures of the CPU and RAM and all that. I want a real-time display (have that with my Windows computer so want something similar), but am getting conflicting answers from web searches.

I have seen suggestions for lm-sensors (which I believe is a command-line display, so not what I am looking for unless it shows temperature changes in real-time), system load indicator (not actually sure what this is), and Psensor (which I am not sure is stable or compatible with 14.04).

Are one of these 3 what I am looking for, or is there something else ideal I have not found yet?

---

### Post by pqwoerituytrueiwoq on 2016-08-04
i am using xubuntu, what i did was use the genmon-applet to make myself some panel sensors
[url=http://i.imgur.com/zDhAaV0.png]
  [img]http://imgur.com/zDhAaV0l.png[/img]
[/url]
here is a dump of my scripts i made for it
[https://github.com/GM-Script-Writer-62850/xfce-genmon-scripts](https://github.com/GM-Script-Writer-62850/xfce-genmon-scripts)

---

### Post by CatKiller on 2016-08-04
I use conky. Amongst other things, I've got it displaying CPU, GPU, hard drive, and system temps, as well as the speeds of the CPU fan, GPU fan, front fan, and rear fan. Having the Vcore displayed as the processor clocks up and down can be quite useful too.

---

### Post by giga+bytes on 2016-08-04
I'm quite new to Linux, and don't know what exactly an applet is (I've only known Windows, so a comparison to the Windows equivalent, if there is one, would make better sense to me). I've only done some simpler things with the command line, so if there's more complicated configuring by the command line I may not be able to figure it out myself.

Conky looks like a possibility, I even found a guide (Linux.com) for installing and basic configuring. It was installed on 16.04; is the procedure for 14.04 the same?

---

### Post by CatKiller on 2016-08-04
> **giga+bytes said:**
> Conky looks like a possibility, I even found a guide (Linux.com) for installing and basic configuring. It was installed on 16.04; is the procedure for 14.04 the same?

The install procedure is exactly the same. The syntax for the conky configuration file changed for conky 1.10, I think. Old configurations will be automatically converted to the new format, but not the other way round. I can't remember how that change lines up with Ubuntu releases.

You can do some amazing things with conky; there are sample configurations all over the place, including at least one mammoth thread on this forum.

You'll still need to install lm-sensors; that's what actually reads the data from the chips. The other tools simply display that information in a style of your choosing.

Edit: I should warn you, though, conky can be a total time sink. Lots of tweaking and experimentation to get everything displayed exactly how you want it :)

---

### Post by pqwoerituytrueiwoq on 2016-08-04
> **giga+bytes said:**
> I'm quite new to Linux, and don't know what exactly an applet is (I've only known Windows, so a comparison to the Windows equivalent, if there is one, would make better sense to me). I've only done some simpler things with the command line, so if there's more complicated configuring by the command line I may not be able to figure it out myself.

Conky looks like a possibility, I even found a guide (Linux.com) for installing and basic configuring. It was installed on 16.04; is the procedure for 14.04 the same?
a panel applet/plugin is similar to a tray icon in windows, just depended on the panel (think task bar) you can have far more flexibility involving placement
conky is a lot like the widget stuff that was in windows vista


installing conky on 16.04 should be the same as 14.04, there is the possibility of a custom made script needing changes though

---

### Post by giga+bytes on 2016-08-04
Thanks for the comparison, now I understand. Both options are very appealing, but to decide which is best for me is difficult. Other than configuring, Conky looks easy to install and use. How difficult is it to install and setup those applets? Is is simply a matter of copying & pasting your scripts and it's done?

Just thought of another good question: can either be set to always be on (startup with the computer and always be visible at a moments glance), without being a drag on system resources or speed?

---

### Post by pqwoerituytrueiwoq on 2016-08-04
the scripts are fairly easy, but if you want to use unity they are not what you are looking for
i made then for use with the xfce4-genmon-plugin package that uses the xfce4-panel which is part of the xfce4-desktop/xubuntu-desktop package

this applet just runs a given command periodically and updates it's data

i prefer panel applets to conky since my windows don't cover them up

---

### Post by giga+bytes on 2016-08-04
Yeah, I think I should go with Conky for now, and perhaps later when I have more experience with Linux I'll look into what you use to see which I prefer.

Thanks for the info!

---

### Post by CatKiller on 2016-08-05
> **giga+bytes said:**
> Just thought of another good question: can either be set to always be on (startup with the computer and always be visible at a moments glance), without being a drag on system resources or speed?

Yes, it's easy to make things start when you log in. Conky simply draws on the desktop. As pqwoerituytrueiwoq said, it's possible to cover conky with your other windows unless you have conky on top of everything else, which I don't personally think looks nice.

In my case, I've got conky displayed on the right-hand side so that it's less likely to be covered by open windows. But if you've got lots of windows open, switching to an empty desktop is just a key combo or mouse scroll away. Do you know about workspaces? They can be very handy.

The amount of resources that conky uses depends on what you've set it up to do, although it's pretty lightweight. My conky setup, which calls quite a lot of external programs and scripts, uses at most 2% of processing time. How much processing time is used by processes is another thing that my conky displays ;)

---

### Post by CatKiller on 2016-08-07
OK, I'm near my computer now, so I can show you the kind of information my Conky displays. There are lots of ways to make it prettier if you don't want the minimalistic table look. Lots of people like variations on conky rings that display information like dials.

---

