---
title: "Disable ps2 ports (block all keyboards)"
date: 2017-02-10
forum: General Help
---

### Post by Dr_Lion on 2017-02-10
I'm trying to block all keyboards on ps2 ports, but im not able to do it.

I've searched some hours on internet and i still cant find anything that acomplishes that.

im able to find my ps2 keyboard:

> 
cat /proc/bus/input/devices

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input2
U: Uniq=
H: Handlers=sysrq kbd event2 
B: PROP=0
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7


I can find files from that keyboard here: /sys/bus/serio/devices/serio0/
but i dont know what to do.


I thought of using some udev rules to block them all, but this is something that i dont know anything. And when i search 98% of topics are about network ports or usb...

Anyone can help?

---

### Post by #&amp;thj^% on 2017-02-10
If by block all keyboards means the same as disable keyboards.
You can use xinput to float the input device under X.
This "may/may not" be the method you really want 
    Execute the command "xinput" list to list your input devices.
```
xinput
```
    Locate "**all ps2 keyboards**" and take note of its id number; this will be used to disable the keyboard. Also, take note of the number at the end, **[slave keyboard (#)]**; this is the id number of the master, which will be used to re-enable your keyboard.
    To disable the keyboard, execute the command:
 ```
xinput float <id#>
```, 
where **<id#>** is your keyboard's id number. For example, if the id was 10, then the command would be **"xinput float 10"**
    To re-enable the keyboard, execute the command:
 ```
xinput reattach <id#> <master#>
```, 
where master is that second number we noted down. So if the number was 3, you would do [B]"xinput reattach 10 3"
[/B]Source: [http://askubuntu.com/questions/160945/is-there-a-way-to-disable-a-laptops-internal-keyboard](http://askubuntu.com/questions/160945/is-there-a-way-to-disable-a-laptops-internal-keyboard)
Hope this is useful to you.;)

---

### Post by Dr_Lion on 2017-02-13
I tried what you sugest and it's true that it works, but...

I have a few buts, i only have one ps2 keyboard here now, but tomorrow i will take another keyboard to try, 

I did a script to get both ids and disable keyboard, but since it doesnt keep state, i added the script to start up config, and it works. My big doubt now is if it works only for this ps2 keyboard, or for all ps2 keyboards!!! I understand that this method work for all, but to automate this task without human interaction to select keyboard to disable, all ps2 keyboards will have to have the same name, because it is what im using to detect both ids and disable keyboard automatically!

Otherwise im back to step 1, where i cant disable all ps2 keyboards, without human interaction.

---

### Post by #&amp;thj^% on 2017-02-13
That is why I said earlier in my post above..."This "may/may not" be the method you really want "
But for a workaround....I found it to be at least satisfactory.(For My case use) 
> Otherwise im back to step 1, where i cant disable all ps2 keyboards without human interaction. 
I'm not trying to sound cheeky here...but in a perfect world...lol.
No OS with "Driver Support" is perfect.
> My big doubt now is if it works only for this ps2 keyboard, or for all ps2 keyboards!!! 
You will need to change or add "ID#'s" for each keyboard added.
This is the best effort that I could come up with.
Regards

---

### Post by Dr_Lion on 2017-02-16
Well, i've tried another ps2 keyboard, and i know its a small set for an experiment but i got just the same "name" and both id's. I dont know if it is always like this, but for now i will take this experiment as a yes, and even if it changes the ids, as long as it keeps the keyboard name "AT Translated Set 2 keyboard" there is no problem for me, cause im parsing this name and using the ids assigned to it.

Now my only doubt is to make the script in bash or pyhton, i tried bash but it didnt work (that weird sed, awk), since i'm better at python, python it was, and it is working without user interaction every single time computer get up.

---

### Post by #&amp;thj^% on 2017-02-16
Good News...You know I did not even think about python.
Good work....and if you would care to share your script here with us, I'm sure future visitors would be grateful;).
Kind Regards

---

### Post by efflandt on 2017-02-18
Just curious "why" you are disabling a ps2 keyboard? for example if it is to prevent someone from plugging in a local keyboard who has physical access to the computer, do you also need to look at disabling USB keyboards?

---

### Post by Dr_Lion on 2017-03-08
Replying to both of you.

Yes i can share, with some problems that i had here, i lost the original file, but i've made a copy of my python script, im not sure if it is completly function, but i think it is. Anyway it's very simple to test, only have to uncomment the print statements to check if the id's are right..
I noticed coments are in portuguese but small blocks are self explanatory, no need to read comments.

Folllowing code will block keyboards that listed in xinput command with name "AT Translated Set"! If you want to block other device listed there, you can change that name to the device name. but remenber, in that case you may have to change also the numbers stating positions of characters to split the strings in order to get the right id...

```

#!/usr/bin/env python

import sys
import os
import subprocess

p1 = subprocess.Popen(["xinput"], stdout=subprocess.PIPE)
p2 = subprocess.Popen(["grep", "AT Translated Set"], stdin=p1.stdout, stdout=subprocess.PIPE, stderr=subprocess.PIPE)

p1.stdout.close()

kids = p2.communicate()
ids2 = str(kids)

'''
ids = ids2.split(" ")
print ids

print ids[21]
print ids[24]
'''


ids = ids2.split("=")
#print ids
#    print ids[1]

ids4 = str(ids[1])
ids3 = ids4.split("(")
#print ids3

idblock = ids3[0][0:2]
iddblock = ids3[1][0]

#estes sao os prints finais
#print idblock
#print iddblock

#xinput float 13
p3 = subprocess.Popen(["xinput", "float", idblock])
#p3.communicate()

```


About usb blocking, the answer is "yes". Usb ports are also blocked, but those were already blocked, using udeve rules... I noticed ps2 port was left open and that's why the need to block them. This was the fastest way to achive that, as i searched and did not found anything about how to block ps2 keyboards through udev rules.

---

