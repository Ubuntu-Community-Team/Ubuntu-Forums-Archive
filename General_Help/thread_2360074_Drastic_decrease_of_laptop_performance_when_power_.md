---
title: "Drastic decrease of laptop performance when power plug is connected"
date: 2017-05-01
forum: General Help
---

### Post by entropika2 on 2017-05-01
Hi, this is my first message, but am not totally new to the Ubuntu forum.
So far, I have always found my solution somewhere in the discussions, but this time I am having a hard time.

It's been weeks that my laptop becomes practically unusable as soon as I plug in the power plug. With unusable I mean that browsing the Internet becomes very slow, window panning and moving staggers and lags and VLC does not play movies anymore (only the audio goes, the image is stuck at the first frame).

I have one Lenovo u41-70 and am using an universal power adaptor (19V, 3.4A). The original adaptor is in fact 20V and 2.25A so of course I first thought the problem was related to a wrong/not-recognised adaptor (even though the problem did not start immediately when I bought the adaptor, but after one week or so). Hence, I checked the CPU frequency and noticed the scaling governor would change to ```
powersave
``` when plugged in and ```
cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq
``` would tell 500 MHz. Searched around about how to fix this and added the kernel parameter ```
intel_pstate=disable
```. Now the governor is ```
ondemand
``` all the time and  ```
cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq
``` says 1200 MHz. However, no change in the laptop behaviour, still same issues.

Lately, I have noticed the same problem arises when battery goes below the critical level (no power plug). Hence, I thought the problem was somehow related to how ACPI handles events.I added ```
acpi=off
``` to the kernel parameters, but no change.

I am using Ubuntu 16.04.2 (HWE stack enabled) with kernel 4.8, but have also tried with kernel 4.4 and did not notice any difference.

When booting up kernel gives these error messages:

```
[    1.652306] ACPI Error: [\_SB_.PCI0.LPCB.H_EC.ECWT] Namespace lookup failure, AE_NOT_FOUND (20160422/psargs-359)
[    1.652311] ACPI Error: Method parse/execution failed [\_TZ.FN00._ON] (Node ffff8d528e0f70a0), AE_NOT_FOUND (20160422/psparse-542)
[    1.652318] acpi PNP0C0B:00: Failed to change power state to D0
[    1.652339] ACPI Error: [\_SB_.PCI0.LPCB.H_EC.ECWT] Namespace lookup failure, AE_NOT_FOUND (20160422/psargs-359)
[    1.652342] ACPI Error: Method parse/execution failed [\_TZ.FN00._ON] (Node ffff8d528e0f70a0), AE_NOT_FOUND (20160422/psparse-542)
[    1.652346] acpi PNP0C0B:00: Failed to set initial power state
[    1.676051] acpi PNP0C0B:00: Cannot transition from (unknown) to D3hot
[    1.677286] thermal LNXTHERM:00: registered as thermal_zone0
[    1.677288] ACPI: Thermal Zone [TZS0] (32 C)
[    1.677467] thermal LNXTHERM:01: registered as thermal_zone1
[    1.677468] ACPI: Thermal Zone [TZS1] (23 C)
[    1.677582] ACPI Error: [\_SB_.PCI0.LPCB.H_EC.ECRD] Namespace lookup failure, AE_NOT_FOUND (20160422/psargs-359)
[    1.677586] ACPI Error: Method parse/execution failed [\_TZ.TZ00._TMP] (Node ffff8d528e0f7078), AE_NOT_FOUND (20160422/psparse-542)
[    1.677698] ACPI Error: [\_SB_.PCI0.LPCB.H_EC.ECRD] Namespace lookup failure, AE_NOT_FOUND (20160422/psargs-359)
[    1.677701] ACPI Error: Method parse/execution failed [\_TZ.TZ00._TMP] (Node ffff8d528e0f7078), AE_NOT_FOUND (20160422/psparse-542)
[    1.677753] ACPI Error: [\_SB_.PCI0.LPCB.H_EC.ECRD] Namespace lookup failure, AE_NOT_FOUND (20160422/psargs-359)
[    1.677755] ACPI Error: Method parse/execution failed [\_TZ.TZ01._TMP] (Node ffff8d528e0f7118), AE_NOT_FOUND (20160422/psparse-542)
[    1.677838] ACPI Error: [\_SB_.PCI0.LPCB.H_EC.ECRD] Namespace lookup failure, AE_NOT_FOUND (20160422/psargs-359)
[    1.677841] ACPI Error: Method parse/execution failed [\_TZ.TZ01._TMP] (Node ffff8d528e0f7118), AE_NOT_FOUND (20160422/psparse-542)

```

Sorry if I did not write the post in the right way, but as I said this was my first one. If you need more details, please ask.
I'm starting to think to some hardware damage due to the power adaptor. 
I was also trying to update the BIOS, but Lenovo only provides an EXE file for this laptop. I don't have Windows installed and no CD drive, so was trying to figure out how to put WinPE on an USB and maybe use it to flash the BIOS, but I didn't manage yet...

Any idea or advice? 
Thank you in advance for your help!

---

### Post by Autodave on 2017-05-01
Are you plugging it in before or after you have it running?  I have a Dell that will not allow me to plug the adapter in once running. However, if I power it up with the AC connected, it is fine. Even more, once powered up with the AC connected, I can disconnect and reconnect it at will. I just have to have it connected before powering up. Why? No clue.

---

### Post by entropika2 on 2017-05-02
It doesn't matter. 
If I start it with the AC connected, it lags immediately.
If I start it on battery it's ok, but it starts lagging as soon as I connect the AC. I can also repeat this behaviour several times. On battery it's ok, when I plug the AC it starts lagging, I remove the AC and it's ok, I plug it back and it lags...and so on.

Funny thing, it is the same with VLC. If I start the movie with AC connected, image is stuck and audio plays. As soon as I unplug the cable, the movie plays smoothly, but it stops again if I plug back the cable. Starting VLC from Terminal it shows an error related to the vdpau codec and complains about CPU being too slow...

---

### Post by Bucky Ball on 2017-05-02
Sounds to me like this may be a dying power pack and may not be supplying adequate power to the computer. Is there another compatible device you can check this power pack on or are you handy with a multimeter and know what to look for?

Failing that, you can check the specs on the one you're using and pick up a replacement power pack that will match it and give that a try. Some have adjustable voltages so you can choose what matches your machine. I'm trying to imagine how anything software-related could cause this. :-k

What I'm curious about is does it supply enough juice to charge the battery or does charging to full take forever to achieve? If it's not charging the battery, guess you're screwed when the battery goes flat and will need to replace the power supply anyhow. :(

One last thought, and this may sound strange but please try: switch off the machine and take the battery out. Plug in the power supply and boot up. Slow or fast? If things are normal, strange as this may sound, it is probably a battery. They do strange things when they are dying.

---

### Post by dragonfly41 on 2017-05-02
A quick search finds other threads reporting same symptoms ...

Here is just one thread .. [https://forums.lenovo.com/t5/ThinkPad-T400-T500-and-newer-T/Slower-with-AC-Power-than-with-Battery/td-p/1049349](https://forums.lenovo.com/t5/ThinkPad-T400-T500-and-newer-T/Slower-with-AC-Power-than-with-Battery/td-p/1049349)

Some discussion about tweaking "Power Options"???   More than that I don't know.

---

### Post by entropika2 on 2017-05-02
I have already tried another adaptor, also universal, with voltage selector set to 20V, but did not notice any difference.
I did not try to remove the battery, though. It is not removable and I do not have proper tools to open the laptop, right now.

I do not know what you exactly mean with "Power Options", but I have installed ```
indicator-cpufreq
``` The applet can be used to set the power state of the computer. I can set it to "Performance".  The CPU freq is updated, I checked it with ```
watch grep \"cpu MHz\" /proc/cpuinfo
``` but the behaviour of the laptop doesn't change.

Ah, just to add one detail, when the laptop starts lagging I checked both CPU ```
top
``` and GPU ```
sudo intel_gpu_usage
``` and none of them seems having problems. RAM is also fine, basically not used at all...

---

### Post by entropika2 on 2017-05-03
[UPDATE] 
I've noticed something weird.
```
cat /sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_max_freq
2201000
```
while
```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_max_freq
2200000
```

which is probably due to 
```
/sys/devices/system/cpu/cpu*/cpufreq/bios_limit = 2200000
```
Could that cause any trouble?

---

### Post by entropika2 on 2017-05-15
The original charger solved the issue.

---

### Post by Bucky Ball on 2017-05-15
Thanks for marking as solved and telling us what fixed it. Could help others. Enjoy. ;)

---

