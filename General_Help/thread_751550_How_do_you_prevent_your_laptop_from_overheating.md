---
title: "How do *you* prevent your laptop from overheating?"
date: 2008-04-10
forum: General Help
---

### Post by Th3Professor on 2008-04-10
Do you use an external fan or cooling device? Which one?

Do you occasionally "open her up" (the laptop!) and clean out the dust/dirt/etc.? How do you do it?

Do you set up a mini-fridge and stick you laptop inside the freezer anytime you use it?

;)

Basically, I'm curious to know what methods of madness people out there use to accomplish a "cool laptop".

It'll be really helpful to know what devices to *not* use.

For example, I recommend *not* using the "Targus" external fans device:
1. The cable shorted out only a few weeks into using it.
2. The fans are not nearly powerful enough to provide effective cooling.

I'm presently running an old Dell laptop that is big, heavy, clunky, and it **seriously** overheats.

Are you cool? Enlighten us hotties!
8-)

---

### Post by Bliepo32 on 2008-04-10
I am just using fans, but some computers use phase change cooling. Effectively, that means your computer is a fridge. And of course, there are always some who go extreme, and use liquid nitrogen (-146.9°C). And you could go even further than that, but that would be totally mental.

I do clean dirt sometimes though. I does make a difference. But my computer is cool enough. CPU is about 35 degrees celsius (95F). I did have a viedoecard once though, which reached 130 degrees celsius, and the crashed.

---

### Post by pointone on 2008-04-10
I learned long ago to stay away from "desktop replacement" laptops. They're hardly portable and are almost guaranteed to overheat. A properly designed laptop shouldn't overheat unless you throw it in the oven.

As far as your situation, though, you can try the following:

```
echo -n "powersave" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

This will forcibly scale down your CPU to its low(est?) setting.

Also, disable Compiz or any effects on your system, since they only increase your video card's load.

---

### Post by niteshifter on 2008-04-10
Hi,

Some tricks I've used:

Elevate the laptop (at the rear) when it's sitting on a hard surface. Those seemingly useless blocks that Dell ships with cases do have a use ;)

My wife uses a gadget by the name of Lapguard, basically a semi-rigid sheet of material with rubber bumpers that raise the laptop up a bit for better airflow and it keeps the heat off of you.

A couple of times a year, I have at our laptops with a some air-in-a-can along with a small brush and get the dust and debris out of the cooling path.

You mentioned "big, heavy, clunky, and it seriously overheats" - and the first thing that popped into my mind was it's a Dell 5100. If it is, clean it and get (or make) a Lapguard for it. Those machines just plain run hot, and with a P4 CPU cannot scale the clock down.

---

### Post by sm4n666 on 2008-04-10
i use [URL="http://www.buy.com/prod/antec-notebook-cooler-usb-power-2-x-70mm-dbb-fan-w-aluminum-surface/q/loc/101/10353046.html"]click me
[/URL]

everyonce and awhile it will be for $8 after rebate or -$2 after google checkout.....but i is worth the $35....it keeps my laptop cool (even if i game for hours with games like cod4/UT3)

if you dont have $$ to spend just elevate your laptop.  ive heard that using 4 bottle lids work wonders

---

### Post by jcwmoore on 2008-04-10
i use a targus usb cooling pad, it was 15 or 20 dollars at wal-mart, works wonders!

---

### Post by Whiffle on 2008-04-10
I use tp-fancontrol on my thinkpad, thats about it...it doesn't really get hot.  But if it did, I'd probably just elevate it and call it good.

---

### Post by hardyn on 2008-04-10
Attack it with compressed air every now and again.

---

### Post by Zack McCool on 2008-04-10
> **sm4n666 said:**
> i use [URL="http://www.buy.com/prod/antec-notebook-cooler-usb-power-2-x-70mm-dbb-fan-w-aluminum-surface/q/loc/101/10353046.html"]click me
[/URL]

everyonce and awhile it will be for $8 after rebate or -$2 after google checkout.....but i is worth the $35....it keeps my laptop cool (even if i game for hours with games like cod4/UT3)

if you dont have $$ to spend just elevate your laptop.  ive heard that using 4 bottle lids work wonders

I use this same one when the laptop is being used as a Media center on my Plasma TV.  I have the cooler permanently stationed in my home entertainment system.  The laptop stays nice and cool, even after hours of video playback...

---

### Post by jaya28inside on 2008-04-10
meanwhile i didnt use any cooler at all...
coz i'm using PC 
and it's all opened case... :D

---

### Post by Th3Professor on 2008-04-11
> **Whiffle said:**
> I use tp-fancontrol on my thinkpad, thats about it...it doesn't really get hot.  But if it did, I'd probably just elevate it and call it good.

Is there a program/application like that that works on non-Thinkpads?

(AKA: Dell Inspiron 8500... it gets so hot that one could burn themselves, pretty bad, and the computer also crashes when the temperature goes too high... after booting back up the computer beeps me out and says something about the temperature getting too high, offering to look into it, which only takes me to the BIOS, which actually doesn't seem to help (nothing in there that seems to fix the overheating.))

I'm halfway tempted to try to get some kind of super-cooling system, willing to go to the extreme if it means extending the life of that particular laptop.

---

### Post by Whiffle on 2008-04-11
> **Th3Professor said:**
> Is there a program/application like that that works on non-Thinkpads?

(AKA: Dell Inspiron 8500... it gets so hot that one could burn themselves, pretty bad, and the computer also crashes when the temperature goes too high... after booting back up the computer beeps me out and says something about the temperature getting too high, offering to look into it, which only takes me to the BIOS, which actually doesn't seem to help (nothing in there that seems to fix the overheating.))

I'm halfway tempted to try to get some kind of super-cooling system, willing to go to the extreme if it means extending the life of that particular laptop.

It depends entirely on the laptop; but...

I googled a bit and apparently the i8k module does this functionality on the inspirion 8xxx's.
> 
As noted above there is no fan control interface through ACPI for this laptop. The i8k kernel module for Inspiron 8000 laptops allows, however, to directly control the fan. The i8k module does not load as it does not recognize the laptop model. That can be solved by providing the force=1 option. I added the following to my /etc/modules.conf file: 
 # Interface to BIOS fan control?
 options i8k force=1 restricted=1 
The functionality provided by the module is accessible through the i8kutils package. It is not included in Red Hat 9 but can be downloaded from the FreshRPMS site. Included in the package is the i8kmon utility that monitors the temperature and turns on the fans accordingly.
[http://dsanta.users.ch/resources/dell-i8500-linux.html](http://dsanta.users.ch/resources/dell-i8500-linux.html)

---

### Post by Th3Professor on 2008-04-12
> **Whiffle said:**
> It depends entirely on the laptop; but...

I googled a bit and apparently the i8k module does this functionality on the inspirion 8xxx's.

[http://dsanta.users.ch/resources/dell-i8500-linux.html](http://dsanta.users.ch/resources/dell-i8500-linux.html)

Thank you for that info.

Regarding this part:
```
 # Interface to BIOS fan control?
options i8k force=1 restricted=1
```
...since this is Ubuntu and not RH, I'm guessing the modules config file is different. On Ubuntu, is it this file? :

/etc/modules

Before I add that "options"... line, should I download and install the package "i8kmon"?

I don't see that specific name in the package manager. I do see these from an "i8k" search:

gkrellm-i8k
i8kutils
sensors-applet

Before I do any of this I'd like to make sure it's safe (no exploding laptops).
...or, uhm, imploding. or something.

Anyway, looks like it's a step in the right direction though! Very cool.

EDIT:
Update... I see this line along with the gkrellm-i8k & i8kutils in the package manager:
"The programs require the kernel module i8k.o which can be compiled from the package sources or found in Linux kernel 2.4.14 and later versions."
Will it automatically take care of that if/when I install those 3 apps? Or should I manually take care of it?

---

### Post by Whiffle on 2008-04-12
Actually the 
options i8k force=1 restricted=1

line would go in /etc/modprobe.d/options  if i remember correctly. I think i8kutils is the package you want.  I'm guessing you've got the i8k module already, you can check by doing:

sudo modprobe i8k 

in a terminal.  If no errors, then you've got it.

---

### Post by Th3Professor on 2008-04-13
> **Whiffle said:**
> Actually the 
options i8k force=1 restricted=1

line would go in /etc/modprobe.d/options  if i remember correctly. I think i8kutils is the package you want.  I'm guessing you've got the i8k module already, you can check by doing:

sudo modprobe i8k 

in a terminal.  If no errors, then you've got it.

What does "force=1" and "restricted=1" mean?

Will adding that "options" line to /etc/modprobe.d/options make i8k run at boot?
Or should I make it do the "modprobe i8k" thing every time it boots?

I went ahead and installed those 3 apps I listed before, including good o'l "gkrellm", which I have used on previous Linux set-ups. However, gkrellm isn't showing up when I load it, although the process seems to be running. Should I use something else like torsmo?

As far as the fans in the laptop, if it's okay to do it, I'd actually rather the fans be on max 100% of the time, no matter what (unless that's a bad idea).

Also, is it really only 1 fan or actually 2?

I only hear & see 1 fan going (there's only 1 external fan vent on the laptop).

---

