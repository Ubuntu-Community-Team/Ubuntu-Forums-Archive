---
title: "CPU usage and temperature"
date: 2007-05-16
forum: General Help
---

### Post by NaCl on 2007-05-16
I am experiencing high CPU usage when playing certain video files. I compiled my mplayer following this [howto]("http://ubuntuforums.org/showthread.php?t=336706&highlight=codec"). My laptop is a PM 1.6 with 1GB of ram and using the intel chipset (xorg tells me it's 810). I have a rmvb file (640x480) that lags on my computer. My CPU usage goes up to 100%. I also notice lags when I play h264 mkv files and watching flash on firefox. On the same laptop, Windows XP could play them fine without lags. My laptop is capable of playing these file fine without lags. All I want is to watch them without interruption and anger. What could be causing all of these usually high cpu usage? How can I check my system?

Also, even when my system's on idle, it gets quite hot. (I can feel it) I tried installing lmsensor, but it wouldn't let me complete after saying something about the kernel. So I can only say it is higher than usual. Could this be hardware failure or high voltage consumption? I can hear the fan working though. At one point it got so hot it turned off by itself saying it reached the critical temperature (82 degree celcius).

Thanks in advance

---

### Post by Tenicus on 2007-05-16
First of all, if it reached 82 degrees there is probably something wrong with your heatsink.  Maybe not enough thermal paste or too much, check it out
Try using VLC and see if you get the same CPU usage

---

### Post by NaCl on 2007-05-16
same CPU usage in VLC, and VLC couldn't even decode the video file well

should i open up the laptop to check the thermal paste?

---

### Post by Tenicus on 2007-05-16
Yes, if you know what you are doing

---

### Post by bunyip on 2007-05-16
does it get hot if run at 100% in windows? if not then the paste would appear to be working.

when it's in windows running at 100% is the fan louder than in linux?

have you searched the web to see if other people have issues with this model?

---

### Post by NaCl on 2007-05-17
okay, it's really weird. sometimes it gets hot even on idle
last night it was using 100% cpu resource when playing a file
the problem is not occurring anymore, at least not when i tried it one hour ago
*okay, it's taking 100% overall again

when the problem was occurring, the system monitor doesn't show any other process (except gmplayer and gnome system monitor) consuming cpu resources

could it be a problem of my xorg configuration but then xorg is not even using more than 10% of the cpu

okay, i think i can play divx and xvid file fine

---

### Post by Denn1s on 2007-05-19
i hav been experiencing a similar problem with a Celeron M, cpu seems to heat fast and after some time it turns very slow, i hav never taken it to the point of turning off, i cant play MP4 at normal speed and ePSXe lasts about 30 minutes and then becomes too slow to continue playing

i hav an acer 2420 travelmate (laptop), it had never happedned untill recently, 
currently using ubuntu feisty upgraded from edgy (it began happening in edgy)

---

### Post by NaCl on 2007-05-21
I think it really might be a problem related to heat. Right after I turn on the laptop, playing the same files I've been having trouble with is fine. There's noway I can monitor the temperature. I tried installing it by following the guide, but it ended because it wasn't present in the kernel or something like that.

My laptop was fine when I was using edgy. Since I have nothing to lose by time, I am gonna reinstall feisty to see if the problem persists.

---

### Post by hardyn on 2007-05-21
Its a really common problem with the P-M based notebooks... use the 386 kernel and all will be well, i have the exact poor performance, high idle cpu useage problems with the generic kernel

contrary to popular belief... the 386 is now (since egdy) is a generic kernel but without SMP support.

---

### Post by NaCl on 2007-05-21
to hardyn:
what do you think i should do?
install the 386 kernel?
i don't know how to compile my own kernel. i tried, but i have clue on most of the things it was displaying


okay, i discover this

this is after 3 minutes of h264 playback (the same type file it was giving me trouble from the very beginning)

> cat /proc/acpi/thermal_zone/THR0/temperature 
temperature:             91 C

cat /proc/acpi/thermal_zone/THR1/temperature 
temperature:             49 C

idle is
> acpi -V
     Battery 1: charged, 100%
     Thermal 1: ok, 72.0 degrees C
     Thermal 2: ok, 47.0 degrees C
  AC Adapter 1: on-line

this is hotter than my desktop at home

i am not sure which one is my CPU's. but could it be that my cpu's getting too hot and is affecting performance

---

### Post by hardyn on 2007-05-21
its in the repositories, very very easy.

just remember to install the headers as well... 

sudo apt-get install linux-386
or use synaptic.

---

### Post by ghell on 2007-05-21
Even if using the 386 kernel works, that is very high for the cpu temperature. My old Toshiba Tecra S1 managed to get above that after its only fan stopped working and my fiancé's old twinhead got pretty high when the fan started spinning a lot slower than normal (it eventually started grinding against the grill, though it had 2 fans so it wasn't as bad as my Toshiba)

Make sure the fan is spinning and spinning at the correct speed if possible. If it is not, try putting some oil on it (after I bought a £34 replacement heat sink and fan for that Toshiba, I found that the old one worked again after oiling it)

---

### Post by NaCl on 2007-05-21
could it also have something to do with the way acpi's power management?
my cooling mode is currently set to passive, and i can't set it to active
i notice how my fan only spins faster only after 75 degree celcius or so

any way to change that? i read a howto on changing the setting of acpi, but it didn't work for me (maybe i was using the wrong command? it told me to use echo)

i followed this howto
[http://www.columbia.edu/~ariel/acpi/acpi_howto.txt](http://www.columbia.edu/~ariel/acpi/acpi_howto.txt)

---

### Post by NaCl on 2007-05-21
sorry for asking this noob question
is 386 equivalent to x86?
i know pentium M is a type of x86 processor
but would linux-386 work for Pentium M

---

### Post by ghell on 2007-05-21
i386 is an old but compatible x86 instruction set. newer 32bit machines use i686 and most applications will get a performance benefit from this. I use x64 (AMD64 or in my case EM64T) because my Core 2 Duo supports 64bit :)

You really need to find a way to enable active cooling or you will get a lot of problems (or just do what I used to do and buy a desk fan to point at the bottom of your laptop hehe)

---

### Post by hardyn on 2007-05-22
what you say is no longer accurate in ubuntu land... the two are both generic kernels now, but the 386 does not have SMP support

---

### Post by NaCl on 2007-05-24
okay, using this program call mobmeter on windows, i've confirmed that it is also experiencing overheating on windows. i am going to open up the laptop this weekend

---

### Post by kiddo on 2007-06-10
NaCL, I have an Acer Travelmate 2428WXCI (so it's in the 2420 series), and I experience no such issues. Except that the cpu goes up to 52°C MAXIMUM, because the cpu fan always kicks in and brings it down to 48°C. Which is still too high for my tastes.

My problem is that the fan spins up and down and up and down and... even when the machine is doing nothing. Even without any OS at all, displaying the BIOS page, the temperature rises to 51°C for no reason and then starts cooling down with the fan.

So what I am saying is:
[LIST]
[*]**you have a huge problem**. I'm using the generic kernel, the cpu is a pentium M, and you should NOT get to 80°C, that is insane. **Check your hardware cooling**, quick!
[*]did you already **open up your laptop**? if yes/no, **could you take pictures** to show me how to do that? I can't figure out how to dismantle this travelmate laptop (I'm a bit scared of breaking the plastic covers), photos would help me a long way.
[/LIST]

---

### Post by ghell on 2007-06-10
Most laptops break apart in a similar but complicated way. First turn it over and unscrew everything you see, remove everything you can (fan, hdd, dvd, battery etc). Pop off the panel between your keyboard and your screen and take the screen off. Pull the keyboard off and pull the ribbon out (where it is held in push the clip, dont just pull it. It can look like an ide cable but infact the end is part of the board not the ribbon) then pretty much just turn it over and take the back off.

Make sure you keep all screws handy and know where everything goes.

---

### Post by kiddo on 2007-06-10
> First turn it over and unscrew everything you see, remove everything you can (fan, hdd, dvd, battery etc). Pop off the panel between your keyboard and your screen and take the screen off. Pull the keyboard off and pull the ribbon out (where it is held in push the clip, dont just pull it. It can look like an ide cable but infact the end is part of the board not the ribbon) then pretty much just turn it over and take the back off.

Well, you can start laughing, because what stops me is exactly the "panel between the keyboard and the screen". It scares the hell out of me, I hate "clipped" stuff that you need to pop out. It feels like the plastic will break :| Some pictures attached to show you how mine looks like.

---

### Post by CRuno91 on 2007-07-19
Hi, I also have an Acer TravelMate 2420 and experience heating problems that bring me to temperatures near 97C...I'm afraid to open up the laptop because the hinge on the left side of the screen cracked and came off so now it's on one hinge with wires hanging from the screen.  

I've noticed while searching the internet that the cracked hinges and overheating are very common in the 2420 series, probably why they don't sell it anymore.

---

### Post by kiddo on 2007-07-19
A friend of mine actually dismantled my laptop - completely - a few days ago, and we put some Artic Silver 5 thermal paste to replace the factory's compound.

I think that the temperature is slightly better, but maybe it is due to having cleaned up the cpu fan grid. Kind of depressing knowing that even Artic Silver cannot solve the problem!

Not a big overheating problem though, I would just like the laptop to be entirely silent.

---

### Post by DaiLaughing on 2007-07-19
I would really recommend that you do NOT take any laptop apart if it still works.  Practise on an old dog a few times first because you will break something.  You should be able to find a maintenance guide (technicians manual) for all the big brands but even with those instructions don't do it.](*,)

I'm guessing with the Pentium M that it is clocking itself down to avoid overheating and that's why it can't handle the video.  It's not like those Dell's from a few years back where if you sit it on a desk that blocks the fan air intake?

---

### Post by kiddo on 2007-07-19
the air intake for those acer travelmates is indeed very dumb. It expels the hot hair to the right side (yeah, right near the microphone and right on your hand/leg). The fresh air intake is taken from the bottom of the laptop. I assume they are not completely brain dead as the laptop has "legs" to lift it about 5mm from the table surface.

This is obviously insufficient, especially if you are not on a flat surface.

---

### Post by prakar on 2007-09-10
Very true, very easy. Upgrading my kernel and voila!
The fan works, thanks very much

---

