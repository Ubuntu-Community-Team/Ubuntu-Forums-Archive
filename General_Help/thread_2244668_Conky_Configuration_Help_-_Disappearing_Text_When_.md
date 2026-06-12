---
title: "Conky Configuration Help - Disappearing Text When I Have No Network"
date: 2014-09-18
forum: General Help
---

### Post by e30ernest on 2014-09-18
I got one of the templates from the Conky Manager to work on my desktop.  With a few tweaks, I got it to look great: 

[img]http://s25.postimg.org/k707tpq7j/working.png[/img]

However, if I don't have a network connection, I lose my time and battery text:

[img]http://s25.postimg.org/lngbplii7/notworking.png[/img]

I'm a newbie with almost zero knowledge (just getting by what I read from various online sources) so I don't know why that is happening.  Here is my configuration file:

[https://docs.google.com/a/fruitful.io/file/d/0B9McqY8nm4LFeDhRVHVMWkktcmc/edit](https://docs.google.com/a/fruitful.io/file/d/0B9McqY8nm4LFeDhRVHVMWkktcmc/edit)

Thank you for your help! :)&#65279;

---

### Post by CantankRus on 2014-09-18
Your [COLOR="#FF8C00"]time[/COLOR] and [COLOR="#EE82EE"]battery[/COLOR] code is within **[COLOR="#FF0000"]$if_existing[/COLOR]** network sections

```
# EDITION FINIR WLAN
[COLOR="#FF0000"]**${if_existing /proc/net/route wlan0}**[/COLOR]${font Play:normal:size=7}${color1}${alignr 54}${voffset -8}WiFi  ${color1}${wireless_essid wlan0}
${font Play:normal:size=7}${color1}${goto 298}${voffset 2}Up${goto 370}${color1}${totalup wlan0} / ${color1}${upspeed wlan0}
${font Play:normal:size=7}${goto 298}${color1}Down${goto 370}${color1}${totaldown wlan0} / ${color1}${downspeed wlan0}
${font Play:normal:size=8}${goto 300}${voffset 2}Local IP${goto 370}${addr wlan0}
${font Play:normal:size=8}${goto 300}${voffset 1}Public IP${goto 370}${execi 3600 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
[COLOR="#FF8C00"]${font Michroma:size=9}${goto 90}${voffset -42}${color0}${time %a} ${color0}${time %D}
${font Michroma:size=18}${goto 118}${color1}${voffset -4}${time %H}:${time %M}[/COLOR]
[COLOR="#EE82EE"]${font Michroma:size=8}${color0}${goto 296}${voffset 18}BATTERY
${font Play:size=8}${color0}${goto 278}${voffset 5}${color1}${battery_percent BAT0}%[/COLOR]
# |--ETH0
[COLOR="#FF0000"]${else}[/COLOR][COLOR="#FF0000"]**${if_existing /proc/net/route eth0}**[/COLOR]${font Play:normal:size=7}${color1}${goto 298}${voffset 6}Up${goto 370}${color1}${totalup wlan0} / ${color1}${upspeed wlan0}
${font Play:normal:size=7}${goto 298}${color1}Down${goto 370}${color1}${totaldown wlan0} / ${color1}${downspeed wlan0}
${font Play:normal:size=8}${goto 300}${voffset 2}Local IP${goto 370}${addr eth0}
${font Play:normal:size=8}${goto 300}${voffset 1}Public IP${goto 370}${execi 3600 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
[COLOR="#FF8C00"]${font Michroma:size=9}${alignr 298}${voffset -42}${color0}${time %a} ${color0}${time %D}
${font Michroma:size=18}${goto 118}${color1}${voffset -4}${time %H}:${time %M}[/COLOR]
[COLOR="#EE82EE"]${font Michroma:size=8}${color0}${goto 296}${voffset 18}BATTERY
${font Play:size=8}${color0}${goto 278}${voffset 4}${color1}${battery_percent BAT1}%[/COLOR][COLOR="#FF0000"]**${endif}${endif}**[/COLOR]
```

So what happens is...
> if_existing wlan0 shows wlan0, battery and time data
else
if_existing eth0 shows eth0, battery and time data
endif
endif
Nothing will show from within that code section when both wlan0 and eth0 don't exist.

You need to remove the time and battery code to outside of the **$if_existing** arguments.
You will probably need to adjust the $voffset values.

---

### Post by e30ernest on 2014-09-18
Thank you!  I'll play around with that.  I'm guessing if I move the time, date and battery indicators out of the "if" argument, it'll shift up when there is no network?  If that's the case, how do I create a new "if" argument to display time, date and battery at x voffset when there is no network?  

Sorry if these seem like dumb questions. :)

---

### Post by CantankRus on 2014-09-18
Pehaps leave as is and add another $else and adjust voffsets in last section.

```
# EDITION FINIR WLAN
[COLOR="#FF0000"]**${if_existing /proc/net/route wlan0}**[/COLOR]${font Play:normal:size=7}${color1}${alignr 54}${voffset -8}WiFi  ${color1}${wireless_essid wlan0}
${font Play:normal:size=7}${color1}${goto 298}${voffset 2}Up${goto 370}${color1}${totalup wlan0} / ${color1}${upspeed wlan0}
${font Play:normal:size=7}${goto 298}${color1}Down${goto 370}${color1}${totaldown wlan0} / ${color1}${downspeed wlan0}
${font Play:normal:size=8}${goto 300}${voffset 2}Local IP${goto 370}${addr wlan0}
${font Play:normal:size=8}${goto 300}${voffset 1}Public IP${goto 370}${execi 3600 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
[COLOR="#FF8C00"]${font Michroma:size=9}${goto 90}${voffset -42}${color0}${time %a} ${color0}${time %D}
${font Michroma:size=18}${goto 118}${color1}${voffset -4}${time %H}:${time %M}[/COLOR]
[COLOR="#EE82EE"]${font Michroma:size=8}${color0}${goto 296}${voffset 18}BATTERY
${font Play:size=8}${color0}${goto 278}${voffset 5}${color1}${battery_percent BAT0}%[/COLOR]
# |--ETH0
[COLOR="#FF0000"]**${else}**[/COLOR][COLOR="#FF0000"]**${if_existing /proc/net/route eth0}**[/COLOR]${font Play:normal:size=7}${color1}${goto 298}${voffset 6}Up${goto 370}${color1}${totalup wlan0} / ${color1}${upspeed wlan0}
${font Play:normal:size=7}${goto 298}${color1}Down${goto 370}${color1}${totaldown wlan0} / ${color1}${downspeed wlan0}
${font Play:normal:size=8}${goto 300}${voffset 2}Local IP${goto 370}${addr eth0}
${font Play:normal:size=8}${goto 300}${voffset 1}Public IP${goto 370}${execi 3600 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
[COLOR="#FF8C00"]${font Michroma:size=9}${goto 90}${voffset -42}${color0}${time %a} ${color0}${time %D}
${font Michroma:size=18}${goto 118}${color1}${voffset -4}${time %H}:${time %M}[/COLOR]
[COLOR="#EE82EE"]${font Michroma:size=8}${color0}${goto 296}${voffset 18}BATTERY
${font Play:size=8}${color0}${goto 278}${voffset 5}${color1}${battery_percent BAT1}%[/COLOR]
[COLOR="#FF0000"]**${else}**[/COLOR][COLOR="#FF8C00"]${font Michroma:size=9}${goto 90}${voffset -42}${color0}${time %a} ${color0}${time %D}
${font Michroma:size=18}${goto 118}${color1}${voffset -4}${time %H}:${time %M}[/COLOR]
[COLOR="#EE82EE"]${font Michroma:size=8}${color0}${goto 296}${voffset 18}BATTERY
${font Play:size=8}${color0}${goto 278}${voffset 5}${color1}${battery_percent BAT0}%[/COLOR][COLOR="#FF0000"]**${endif}${endif}**[/COLOR]

```

or leave the voffsets and just use some line spaces after the last else.
eg
```
# EDITION FINIR WLAN
${if_existing /proc/net/route wlan0}${font Play:normal:size=7}${color1}${alignr 54}${voffset -8}WiFi  ${color1}${wireless_essid wlan0}
${font Play:normal:size=7}${color1}${goto 298}${voffset 2}Up${goto 370}${color1}${totalup wlan0} / ${color1}${upspeed wlan0}
${font Play:normal:size=7}${goto 298}${color1}Down${goto 370}${color1}${totaldown wlan0} / ${color1}${downspeed wlan0}
${font Play:normal:size=8}${goto 300}${voffset 2}Local IP${goto 370}${addr wlan0}
${font Play:normal:size=8}${goto 300}${voffset 1}Public IP${goto 370}${execi 3600 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
${font Michroma:size=9}${goto 90}${voffset -42}${color0}${time %a} ${color0}${time %D}
${font Michroma:size=18}${goto 118}${color1}${voffset -4}${time %H}:${time %M}
${font Michroma:size=8}${color0}${goto 296}${voffset 18}BATTERY
${font Play:size=8}${color0}${goto 278}${voffset 5}${color1}${battery_percent BAT0}%
# |--ETH0
${else}${if_existing /proc/net/route eth0}${font Play:normal:size=7}${color1}${goto 298}${voffset 6}Up${goto 370}${color1}${totalup wlan0} / ${color1}${upspeed wlan0}
${font Play:normal:size=7}${goto 298}${color1}Down${goto 370}${color1}${totaldown wlan0} / ${color1}${downspeed wlan0}
${font Play:normal:size=8}${goto 300}${voffset 2}Local IP${goto 370}${addr eth0}
${font Play:normal:size=8}${goto 300}${voffset 1}Public IP${goto 370}${execi 3600 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
${font Michroma:size=9}${goto 90}${voffset -42}${color0}${time %a} ${color0}${time %D}
${font Michroma:size=18}${goto 118}${color1}${voffset -4}${time %H}:${time %M}
${font Michroma:size=8}${color0}${goto 296}${voffset 18}BATTERY
${font Play:size=8}${color0}${goto 278}${voffset 5}${color1}${battery_percent BAT1}%
${else}


${font Michroma:size=9}${goto 90}${voffset -42}${color0}${time %a} ${color0}${time %D}
${font Michroma:size=18}${goto 118}${color1}${voffset -4}${time %H}:${time %M}
${font Michroma:size=8}${color0}${goto 296}${voffset 18}BATTERY
${font Play:size=8}${color0}${goto 278}${voffset 5}${color1}${battery_percent BAT0}%${endif}${endif}
```

---

### Post by e30ernest on 2014-09-18
Awesome!  Thank you!  I used the 2nd option you gave and it worked perfectly. :)

---

