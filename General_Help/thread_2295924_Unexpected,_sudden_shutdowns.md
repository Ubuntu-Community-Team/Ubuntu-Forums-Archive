---
title: "Unexpected, sudden shutdowns"
date: 2015-09-22
forum: General Help
---

### Post by texpat on 2015-09-22
Lately my machine has been unexpectedly shutting down. Shutdowns are sudden and complete.

After looking around on the 'Net a bit, I thought I might have a thermal problem, but I've ruled that out.

There are two ways I can produce such a sudden shutdown, although not with a lot of precision:

Running Windows 10 in Virtualbox will at some point produce this error. Its happened while playing around with various apps and on closing Windows down.

The second way is to run *[FONT=Trebuchet MS]darktable[/FONT]* and convert a series of RAW images to JPG or PNG.

As I said, in the beginning I thought it had something to do with running the computer under heavy loads and hence overheating, but that doesn't seem to be the case. I run boinc that'll consume 100% CPU power and make the hardware heat up quite a bit, but it can do so for days without issues.

Does anyone here have an idea as to what I should be looking for to solve this problem?

This is on Xubuntu 14.04 by the way. What other info can I provide to aid problem solving?

---

### Post by texpat on 2015-09-23
bump

---

### Post by Bashing-om on 2015-09-23
texpat; Hello;

Do not know, but as a thought, are you pounding /swap and running out of memory ?

Any good indications of what is going on if you run:
```

free -m

```
in an alternate terminal and updating frequently, what do you observe happening ?

What does 
```

top

```
relate about resource usage ?

Maybe tail the syslog and look for abnormalities ?

These things do not happen for no reason
[INDENT][INDENT]so we start look'n
[/INDENT][/INDENT]

---

### Post by pqwoerituytrueiwoq on 2015-09-23
while reading that the only thing i could think of was overheating as that is CPU intensive but they are also memory intensive
then i read bashing-om's post then it hit me, you may have a failing ram stick
run memtest86+ and see if it finds any errors ([error count]>0 means bad ram)
a bad ram stick will cause BSODs on windows and linux to suddenly shutdown or lockup

---

### Post by texpat on 2015-09-24
Hi Bashing-om,

I've been observing memory quite closely, but that doesn't seem to be the problem. I'll use quite a lot, upwards of 7GB of the 8GB available, but swap usage is 0. Could that indicate a problem? Is swap really only used when RAM is 100% full?

[FONT=Courier New]**top**[/FONT] doesn't throw any unusual metrics, either.

Since testing entails having the machine crash on me, this is a slow and tedious process. I'll run some ore tests (provoke another shutdown) and report back. Perhaps syslog reveals something...

---

### Post by texpat on 2015-09-24
pqwoerituytrueiwoq, Hi

How would I go about running memtest86+? Is that a program? Typing it into the console brings up nothing, not even the "...isn't installed, use apt-get..." message.

Thanks
tx

---

### Post by ian-weisser on 2015-09-24
> **texpat said:**
> Shutdowns are sudden and complete.

By shutdown, I assume you mean 'unexpected instantaneous poweroff, with loss of all unsaved work'

I haven't seen a motherboard that detects and powers off for faulty RAM, but seen plenty that shut down for thermal or due to failing power supply.
Don't use CPU to estimate temperatures - install lm-sensors and know for sure.
Thermal causes may be wider than CPU alone. GPU activity, failing sensors, blocked air passages, and other causes may contribute.

Since you can duplicate the shutoff event, monitoring reported temps before a poweroff should be fairly easy to confirm or disprove.
If you disprove thermal, then replace the power supply. Perhaps your PSU can do full CPU + fans, but not quite full GPU also.

---

### Post by pqwoerituytrueiwoq on 2015-09-24
memtest86+ is accessible from the boot menu (grub)
a bad psu is hard to identify can can cause other parts to fail, they are no fun at all

---

### Post by texpat on 2015-09-25
> **ian-weisser said:**
> By shutdown, I assume you mean 'unexpected instantaneous poweroff, with loss of all unsaved work'
Yep
> **ian-weisser said:**
> I haven't seen a motherboard that detects and powers off for faulty RAM, but seen plenty that shut down for thermal or due to failing power supply.
Don't use CPU to estimate temperatures - install lm-sensors and know for sure.
Thermal causes may be wider than CPU alone. GPU activity, failing sensors, blocked air passages, and other causes may contribute.
I use [FONT=Courier New]**psensor**[/FONT] which is a graphical frontend to [FONT=Courier New]**lm-sensors**[/FONT] and while the system heats up quite a bit, its all within acceptable limits.
CPU ~ 85ºC; Motherboard ~ 35ºC; GPU ~ 56ºC
Physically cleaning the box and checking the fans was one of the first things I did.
> **ian-weisser said:**
> Since you can duplicate the shutoff event, monitoring reported temps before a poweroff should be fairly easy to confirm or disprove.
If you disprove thermal, then replace the power supply. Perhaps your PSU can do full CPU + fans, but not quite full GPU also.
I actually built the machine, so I took power consumption into account. Still, could be PSU is defective...

---

### Post by texpat on 2015-09-25
> **pqwoerituytrueiwoq said:**
> memtest86+ is accessible from the boot menu (grub)
a bad psu is hard to identify can can cause other parts to fail, they are no fun at all

Now GRUB won't load. It *says* its loading but boots straight through to the OS. That's just effing great :frown: I'll try and sort things out. I'll be back with any news after the weekend.

So far thanks to all for reading and helping :D

---

### Post by pqwoerituytrueiwoq on 2015-09-25
try holding shift and hitting up/down arrow keys
you can edit the [FONT=courier new]/etc/default/grub[/FONT] file to show the menu and not hide it then run update grub
but what i usually end up doing is editing[FONT=courier new] /boot/grub/grub.cfg[/FONT]
and change any [FONT=courier new]set timeout=0[/FONT] to [FONT=courier new]set timeout=10[/FONT]

---

### Post by texpat on 2015-10-03
Finally came around to running memtest86+
Comes back clean. So RAM is OK.

---

### Post by pqwoerituytrueiwoq on 2015-10-03
then i would guess the PSU is failing, how old is it? if it is out of warranty id open it up and see if the caps are leaking
my old PSU was close to failing [http://i.imgur.com/G9CDK.jpg](http://i.imgur.com/G9CDK.jpg)/[http://i.imgur.com/BsK8N.jpg](http://i.imgur.com/BsK8N.jpg) it was not causing problems yet, but it was not going to last much longer
if this is a basic system (no power hungry GPU) id suggest a [Corsair CX430 or a 300W SeaSonic]("http://tinyurl.com/pvjb7by")
unless you have a PCI GPU you would probally need under 250w, but anything below 300w that is quality is very hard to find, for best efficiency it is best not to get too many watts the 80+ rating only is for certain load percentages (20-80% IIRC)

the main sign is it is under load and not overheating

---

