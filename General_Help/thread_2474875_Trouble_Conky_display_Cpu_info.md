---
title: "Trouble Conky display Cpu info"
date: 2022-05-10
forum: General Help
---

### Post by megamister2 on 2022-05-10
Couldn't find what I needed searching so maybe someone knows where/how I can monitor CPU temp with conky and display it in Fahrenheit?
I'm on an Atomic Pi with a Atom Z83504 core processor



I'm using a base file from RPi, that uses vcgencmd...and my RaspberryPi correctly displays in Celsius and Fahrenheit but clearly that doesn't work with the AtomicPI

With Sensors-detect I get Intel digital thermal sensor...(driver 'coretemp')  Success!
from sensors I get coretemp-isa-0000
Adapter:ISA adapter then what appears to be temps which are usually really close in the 4 cores


${cpu cputemp0} seems to be cpu load

${cpu coretemp2} seems to be same cpu load

${cpu cpu0} Seems to be same cpu load- which are usually different from cpu 1,2,3,4

I appear to be able to read the temp with sensors -- get a display for core 1-4 of 35 C approx




So anyone have a line that works ideally in F and C?

Why do I get a CPU load for cpu 0,1,2,3,4 I know there's only 4?

---

### Post by megamister2 on 2022-05-11
Update: Made a little headway playing around with some strings. Found a string that reads the CPU temp on the Atomic Pi and appears accurate.

 


```
CPU Temp: ${exec sensors | grep 'Core 0' | awk '{print $3}' | cut -c2-3} C
```
 


 One can change the core No if a specific is desired. Now the problem is that's ONLY in Celsius...ideally I'd like Fahrenheit displayed also.
On my RPi, I got it to work if I added this string to the end and it calculates what the F would be. But can't get it to work with this string 


```
| awk {print (($1 * 9 / 5))+32}'} F
```

---

### Post by megamister2 on 2022-05-11
FIXED:
I went back character by character comparing the working RPI line and the Atomic Pi line. I think the problem was the end apostrophe and parenthesis. I think the copying and pasting got mixed up a bit. The line formats are very similar so I copied 
  [COLOR=#030303][FONT=Roboto][SIZE=2]| awk '{print (($1 * 9 / 5))+32}'} F to the end of the working Atomic Pi line after the cut -c2-3 and deleting the } there

So the working cpu temp string in F for the[SIZE=4] Atomic Pi[/SIZE] should be 
[/SIZE][/FONT][/COLOR]```


[COLOR=#030303][FONT=Roboto][SIZE=2]${exec sensors | grep 'Core 0' | awk '{print $3}'| cut -c2-3 | awk '{print (($1 * 9 / 5))+32}'} F
[/SIZE][/FONT][/COLOR]
OR

[COLOR=#030303][FONT=Roboto][SIZE=2]${exec sensors -f | grep 'Core 0' | awk '{print $3}'| cut -c2-3} F[/SIZE][/FONT][/COLOR]

 [COLOR=#030303][FONT=Roboto][SIZE=2]
If you want both displayed like I do it's something like 
CPU Temp:  ${exec sensors | grep 'Core 0' | awk '{print $3}'| cut -c2-3 | awk '{print (($1 * 9 / 5))+32}'} F $alignc ${exec sensors | grep 'Core 0' | awk '{print $3}'| cut -c2-3} C
OR
[/SIZE][/FONT][/COLOR]
[COLOR=#030303][FONT=Roboto][SIZE=2][COLOR=#030303][FONT=Roboto][SIZE=2]CPU  Temp:  [/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][COLOR=#030303][FONT=Roboto][SIZE=2][COLOR=#030303][FONT=Roboto][SIZE=2][COLOR=#030303][FONT=Roboto][SIZE=2][COLOR=#030303][FONT=Roboto][SIZE=2]${exec sensors -f  | grep 'Core  0' | awk '{print $3}'| cut -c2-3}[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR] F $alignc ${exec sensors | grep 'Core  0' | awk '{print $3}'| cut -c2-3} C[/SIZE][/FONT][/COLOR]
[/SIZE][/FONT][/COLOR]
```[COLOR=#030303][FONT=Roboto][SIZE=2]
:([/SIZE][/FONT][/COLOR]

---

### Post by deadflowr on 2022-05-11
Does sensors -f  option for fahrenheit output not work on  Atomic PI? (or any PIs for that matter)
like
```
${exec sensors -f | grep 'Core 0' | awk '{print $3}' | cut -c2-3} F
```

---

### Post by megamister2 on 2022-05-11
> **deadflowr said:**
> Does sensors -f  option for Fahrenheit output not work on  Atomic PI? (or any PIs for that matter)
like
```
${exec sensors -f | grep 'Core 0' | awk '{print $3}' | cut -c2-3} F
```

Oh sure NOW your reply after I spend hours to find a working solution...Yes I just tried it and it does work to display in F. Every reference I found seemed to be in Celsius and I wasn't sure where that -f went, I now remember seeing it in a random reply somewhere a few hrs back. But now there's 2 working solutions EVEN BETTER. I'll edit the previous reply and add it. That's ok I have my notes and I'm making references a couple places for others to find in the future hopefully just a copy and paste to make it quick and easy.

The Raspberry Pi reads[COLOR=#030303][FONT=Roboto][SIZE=2]{exec /opt/vc/bin/vcgencmd measure_temp

Not sure if there's a -f that works or not. Mines not broke so I'm not gonna try and fix it haha I like seeing them both side by side so it gives me a better association for Celsius which I'm not as familiar with but used a lot.
[/SIZE][/FONT][/COLOR]

 
It's not easy to find info on displaying in F

---

### Post by megamister2 on 2022-05-11
Here's my final layout view

---

