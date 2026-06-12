---
title: "lm-sensors labels"
date: 2008-02-10
forum: General Help
---

### Post by damp sneaker on 2008-02-10
Can anybody give me some feedback on what the fan and temp sensor labels are referring to in the following sensors output? I'm concerned about that temp3 which looks to be hot but "temp3" doesn't tell me much about what it is. :confused: Also fan2 which shows a zero. All fans (CPU, case, power supply and video card) *are* happily spinning away. And what's up with the 'ALARM' after 'in6' and 'in7'? That's making me nervous too but I don't even know what 'in6' or 'in7' *are*. :redface: It's a new box that I just built up and would hate to see it melt down. :eek:

TIA for any help.

Here's what 'sensors' reports:

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +17°C
Core0 Temp:
              -2°C
Core1 Temp:
              -2°C
Core1 Temp:
              -9°C

it8718-isa-0228
Adapter: ISA adapter
in0:       +1.12 V  (min =  +0.00 V, max =  +4.08 V)   
in1:       +2.26 V  (min =  +0.00 V, max =  +4.08 V)   
in2:       +3.26 V  (min =  +0.00 V, max =  +4.08 V)   
in3:       +2.98 V  (min =  +0.00 V, max =  +4.08 V)   
in4:       +3.09 V  (min =  +0.00 V, max =  +4.08 V)   
in5:       +3.14 V  (min =  +0.00 V, max =  +4.08 V)   
in6:       +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in7:       +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in8:       +3.10 V
fan1:     1032 RPM  (min =    0 RPM)                   
fan2:        0 RPM  (min =    0 RPM)                   
fan3:     1211 RPM  (min =    0 RPM)                   
temp1:       +33°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor   
temp2:       +22°C  (low  =  +127°C, high =  +127°C)   sensor = diode   
temp3:       +84°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor   
vid:      +1.550 V

FWIW:
motherboard=Gigabyte MA790X-DS4

---

### Post by kidders on 2008-02-11
Hi there,

Sensor configurations are chipset-specific, so the only people who can answer your questions with any accuracy are others with the same hardware as you. Places like [http://www.lm-sensors.org/wiki/Configurations](http://www.lm-sensors.org/wiki/Configurations) are a good place to start, but I recommend liberal use of Google.

I can answer *some* of your questions though...

> I'm concerned about that temp3 which looks to be hot but "temp3" doesn't tell me muchOne of three things is probably happening there:[LIST]
[*]Someone is frying eggs on your motherboard. [Not terribly likely ... but at least worth checking]
[*]Temp3 isn't actually connected to a sensor, or is not properly implemented by your motherboard's chipset. In either case, the values it spits out will be spurious, and lmsensors should be configured to disregard them. [Reasonably likely]
[*]Your multipliers/offsets are wrong. [More likely][/LIST]Sensors apps use basic algorithms to transform resistance/voltage information into meaningful numbers like temperatures & speeds. I suspect yours may be wrong.

> Also fan2 which shows a zero.The "fan2" sensor probably isn't connected, or perhaps isn't supported by your motherboard.

> And what's up with the 'ALARM' after 'in6' and 'in7'?My guess is that they are meaningless reference values ... a pair of voltages that are permanently high & permanently low. The thing to do with those is configure lmsensors to ignore them, I'd say.

Anyhow, until you find sensor configuration details that match your motherboard, the only useful information you can get from them is *changes* in the values reported, not the sizes of the values themselves. For example, a CPU temperature that goes from -35C to 45C might be cause for concern, even though 45C is not an unreasonable CPU temperature. For all you know, you see, what is being represented as 45C may in reality be 110C ... there's just no way to know until you nail down the correct sensor multipliers & offsets.

As a first step, I suggest making a backup of your lmsensors configuration, and deleting all the crud out of it. Typically, sensor configuration files contain thousands of lines of real & sample setups for a huge variety of chips, only one or two of which you actually have. Paring it down to the absolute minimum should make it far less confusing to read, so it'll be much easier to see which bits of it need to be changed.

---

### Post by apetresc on 2008-02-11
When I worked in hardware last work term, I noticed an interesting "bug": If the fan speed was held in two registers (a low-order byte, and a high-order byte) and the high-order byte was read BEFORE the low-order byte (this is wrong, it should be the other way around), the resulting number after the appropriate shifting always came out to 84.17 RPM. Always, regardless of whether the fan was running fast, slow, or at all. It was sort of the "error code" for the system. Obviously 84RPM is a ridiculous value for a fan speed.

Similarly, it's a ridiculous temperature, and the number is the same which strikes me as quite a coincidence, so chances are that the reading is not accurate, it is simply the result of an improperly-accessed sensor register. Maybe it's a register that does not even exist (lm-sensors is trying to look for a sensor that is not physically present on your system).

I'd ignore it; if any part of your system actually WAS running at 84 degrees, you'll find out soon enough anyway when your house burns down :)

---

### Post by damp sneaker on 2008-02-11
> **kidders said:**
> Hi there,
Hello, and thanks for responding!
> 

I can answer *some* of your questions though...

One of three things is probably happening there:[LIST]
[*]Someone is frying eggs on your motherboard. [Not terribly likely ... but at least worth checking]
[*]Temp3 isn't actually connected to a sensor, or is not properly implemented by your motherboard's chipset. In either case, the values it spits out will be spurious, and lmsensors should be configured to disregard them. [Reasonably likely]
[*]Your multipliers/offsets are wrong. [More likely][/LIST]Sensors apps use basic algorithms to transform resistance/voltage information into meaningful numbers like temperatures & speeds. I suspect yours may be wrong.



All that is kinda what I was speculating but not knowing for sure it was filling me with fear. 

> 

The "fan2" sensor probably isn't connected, or perhaps isn't supported by your motherboard.

That one I think that I found. There's a power supply fan connector on the motherboard but the PS I put in the box (Antec Neo HE 550) doesn't have a connector for that. 

> 
My guess is that they are meaningless reference values ... a pair of voltages that are permanently high & permanently low. The thing to do with those is configure lmsensors to ignore them, I'd say.

OK, will do. 

> 
Anyhow, until you find sensor configuration details that match your motherboard, the only useful information you can get from them is *changes* in the values reported, not the sizes of the values themselves. For example, a CPU temperature that goes from -35C to 45C might be cause for concern, even though 45C is not an unreasonable CPU temperature. For all you know, you see, what is being represented as 45C may in reality be 110C ... there's just no way to know until you nail down the correct sensor multipliers & offsets.

As a first step, I suggest making a backup of your lmsensors configuration, and deleting all the crud out of it. Typically, sensor configuration files contain thousands of lines of real & sample setups for a huge variety of chips, only one or two of which you actually have. Paring it down to the absolute minimum should make it far less confusing to read, so it'll be much easier to see which bits of it need to be changed.

That's all great advice and I'm grateful for it.  Thank you very much.

---

### Post by damp sneaker on 2008-02-11
> **AdrianP said:**
> [Interesting related anecdotal stuff snipped for brevity.]

Similarly, it's a ridiculous temperature, and the number is the same which strikes me as quite a coincidence, so chances are that the reading is not accurate, it is simply the result of an improperly-accessed sensor register. Maybe it's a register that does not even exist (lm-sensors is trying to look for a sensor that is not physically present on your system).

I'd ignore it; if any part of your system actually WAS running at 84 degrees, you'll find out soon enough anyway when your house burns down :)

Thanks Adrian. It didn't make much sense to me either but I really needed other opinions to calm my fears. The house is still standing and I can't feel any excess  heat in the box with the cover off so I guess all is cool (so to speak).  Thanks very much for your input!

---

