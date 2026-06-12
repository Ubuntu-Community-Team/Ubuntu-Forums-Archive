---
title: "Battery design capacity lower than actual"
date: 2013-03-24
forum: General Help
---

### Post by WebRic on 2013-03-24
[COLOR=#333333][FONT=Ubuntu Beta]Hi i have been having some problems with battery. [/FONT][/COLOR]

[COLOR=#333333][FONT=Ubuntu Beta]It is 48 Wh battery for Lenovo Ideapad and ubuntu is still telling me it design capacity is 38 Wh and also i doesnt charge it more than this value. Yesterday i was plaing around and this is what i got, i charged it to 44Wh (its max now i think coz it has about 10 months) but ubuntu now see the battery is charget to 44Wh and its design capacity is 38Wh, i have fear when i discharge it, ubuntu will charge it again only to 38Wh

[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta]This is what i get as info

[/FONT][/COLOR]&#8203;richard@richard-Ideapad:~$ cat /proc/acpi/battery/BAT0/state present:                 yes
capacity state:          ok
charging state:          charged
present rate:            0 mW
remaining capacity:      43820 mWh
present voltage:         12195 mV
richard@richard-Ideapad:~$ acpi
The program 'acpi' is currently not installed.  You can install it by typing:
sudo apt-get install acpi
richard@richard-Ideapad:~$ cat /proc/acpi/battery/BAT0/info 
present:                 yes
**design capacity:         38880 mWh**
**last full capacity:      43950 mWh**
battery technology:      rechargeable
design voltage:          10800 mV
design capacity warning: 3073 mWh
design capacity low:     1536 mWh
cycle count:          0
capacity granularity 1:  1537 mWh
capacity granularity 2:  40877 mWh
model number:            L09S6Y02
serial number:           16177
battery type:            LION
OEM info:                SANYO

I have no idea what should i do, i would appreciate any help. Thanks

---

