---
title: "How remove sound module"
date: 2007-06-23
forum: General Help
---

### Post by longlegs on 2007-06-23
Hi ,
I have a problem with no sound and one of the "solutions" requires removing the module with 
sudo modprobe -r snd_ens1371

then reloading it with 
sudo modprobe snd_1371

However, when I issue the -r command I get a message that the snd module is in use.

How can I determine which program or module is using it? or how can I tell the system to quit arguing and do what it is told?

Thanks
longlegs

---

### Post by handydan918 on 2007-06-23
not certain this will help, but I've used < rmmod modulename>  to remove modules in the past.

---

### Post by longlegs on 2007-06-23
Hi ,

I get same "in use" message with rmmod.

Thanks for reply.
longlegs

---

### Post by Rui Pais on 2007-06-23
Hi,
some modules, after been loaded, cannot be unloaded again.

You may try blacklist that one specificaly and later load it manually or with a script... i don't know if thats enough as a solution.

To blacklist you add to /etc/modprobe.d/blacklist:
```
blacklist snd_ens1371
```

hth

---

### Post by longlegs on 2007-06-23
Hi,
I edited the blacklist then rebooted.
lsmod | grep snd | more still shows snd_ens1371 loaded and
modprobe -r snd_ens1371 still says it's in use.

Any other possibles?

longlegs

---

### Post by nutz on 2007-06-23
What happens if you boot to command line only and then try it?

---

### Post by longlegs on 2007-06-23
Hi,
I'm out of time for now but will try that later. 
Thanks much
longlegs

---

### Post by longlegs on 2007-07-07
Hi ,
Finally removed the snd_ens1371 driver by removing the sound card before booting.
It did not however, help me with getting sound working.
It appears that some app/driver/process is grabbing the sound card and never letting go, so the cd players, etc, cannot play.
Is there any way to determine what is using the snd_1371?
In the /boot file I see several lines with things like speakup, speakupmain, synth(esizer?) and so on. I have found fhat speakup is a program for converting text to sound. Do I need to remove all references to speakup, and if so, how?

TIA
longlegs

---

### Post by longlegs on 2007-07-07
bump?

---

### Post by geraldm on 2007-07-07
As far as which modules are in use, the command lsmod provides the list.
This is for ppp here:
ppp_generic            28180  7 ppp_deflate,bsd_comp,ppp_async
slhc                    7168  1 ppp_generic

The module slhc has 1 other module requiring it, ppp_generic, which is 
listed after it.  To unload slhc, I would have to remove ppp_generic and
then slhc.  Both can be removed in one command line with all the 
dependent modules listed the correct dependency
order.  You can do similar with snd_1371.

An application may be using a module, that would not be shown in this
list.  The command "ps aux" lists all applications running.  Certainly it
will be a  sound application.

Gerald

---

### Post by Rui Pais on 2007-07-08
> **longlegs said:**
>  edited the blacklist then rebooted.
lsmod | grep snd | more still shows snd_ens1371 loaded and
modprobe -r snd_ens1371 still says it's in use.

Thats because some modules/drivers can not be unloaded after they been loaded at boot process... and the hardware makes them be loaded evcen if they are blacklist... sometimes change file /etc/modprobe.d/aliases can be used for that, if you know the alias of snd_ens1371...
> **longlegs said:**
> Hi ,
Finally removed the snd_ens1371 driver by removing the sound card before booting.
It did not however, help me with getting sound working.
It appears that some app/driver/process is grabbing the sound card and never letting go, so the cd players, etc, cannot play.
Is there any way to determine what is using the snd_1371?

Sorry but do you mind to give a little more details...

Do you mean that you boot without the card inserted but it still loaded the snd_1371?
whats the output of:
lsmod | grepsnd_ens1371
did you tried to blacklist too all other modules/drivers that appear in that line (dependencies)?

[QUOTE=longlegs]
In the /boot file I see several lines with things like speakup, speakupmain, synth(esizer?) and so on. I have found fhat speakup is a program for converting text to sound. Do I need to remove all references to speakup, and if so, how?
[/QUOTE]
exactly what file you change in /boot? 
Your configurations files ate in /etc, not in /boot. The file config-2.6.xxxxxxxx is just a copy of the kernel config options that was used for compilation. They don't should be changed (it exist is only for reference), and they do nothing if changed. Kernel don't read it...

---

