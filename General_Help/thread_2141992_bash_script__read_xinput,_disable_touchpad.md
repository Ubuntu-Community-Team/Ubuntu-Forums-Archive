---
title: "bash script : read xinput, disable touchpad"
date: 2013-05-04
forum: General Help
---

### Post by sochin on 2013-05-04
I would like to have a script (mapped to a key) to enable/disable the
touchpad on a Vaio SVS13. 

This will get the appropriate id:
```

~> xinput list | grep "SynPS/2 Synaptics TouchPad"
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]

```

Now i need to parse out the id (13) and execute:
```

~> xinput set-prop 13 "Device Enabled" 0

```

Among other things, i don't know how to redirect the output of the
xinput list command to a buffer/array, then pass that to the xinput set-prop.

Here's what i started with:

```

#!/bin/bash
line = $(xinput list) | grep "SynPS/2 Synaptics TouchPad"

IFS='= ' read -a line_array <<< "$line"

xinput set-prop $line_array[4] "Device Enabled" 0

```

Thanks.

---

### Post by pqwoerituytrueiwoq on 2013-05-04
i made a script a while back to toggle that
content of my [FONT=courier new]/usr/local/bin/toggleTouchPad[/FONT] script
```
#!/bin/sh
status=$(synclient -l | grep TouchpadOff | awk '{print $3}')
if [ $status -eq 1 ];then
          status=0
else
          status=1
fi
synclient TouchpadOff=$status
exit
```

---

### Post by sochin on 2013-05-04
Hmm... Seems like a good solution, i added an echo:

```

#!/bin/bash
status=$(synclient -l | grep TouchpadOff | awk '{print $3}')
if [ $status -eq 1 ];then
    status=0
else
    status=1
fi
synclient TouchpadOff=$status
echo "tpad set synclient TouchpadOff=$status"
exit

```

and it seems to toggle the state

```

temp> ./tpad
tpad set synclient TouchpadOff=1
temp> synclient | grep Touchpad
    TouchpadOff             = 1
temp> ./tpad
tpad set synclient TouchpadOff=0
temp> synclient | grep Touchpad
    TouchpadOff             = 0

```

But there is no effect on the touchpad. 

However, these commands work:

```

temp> xinput list | grep "SynPS/2 Synaptics TouchPad"
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
temp> xinput set-prop 13 "Device Enabled" 1
temp> xinput set-prop 13 "Device Enabled" 0

```

---

### Post by pqwoerituytrueiwoq on 2013-05-04
This is a dirty patch but it it keeps track of the status, well then this should work
```
#!/bin/bash
status=$(synclient -l | grep TouchpadOff | awk '{print $3}')
if [ $status -eq 1 ];then
    status=0
else
    status=1
fi
synclient TouchpadOff=$status
xinput set-prop 13 "Device Enabled" $status
notify-send --icon mouse "Touchpad" "TouchpadOff = $status"
exit
```
What does [FONT=Courier New]synclient -l[/FONT] give you

---

### Post by sochin on 2013-05-04
Thanks.

However, the id of the device is not static, thus my desire
to parse the id= from the xinput list and pass that to xinput set-prop...

---

### Post by schragge on 2013-05-04
Try (works in Ubuntu releases starting from 12.04)
```
id=$(xinput --list --id-only 'SynPS/2 Synaptics TouchPad')
``` or directly
```
xinput --set-prop 'SynPS/2 Synaptics TouchPad' 'Device Enabled' 0
``` or even (on quantal/raring)
```
xinput --disable 'SynPS/2 Synaptics TouchPad'
```

---

### Post by sochin on 2013-05-04
Thanks for the help!

Here's what I ended up with to toggle the state of the touchpad:

```

#!/bin/bash
# Get the device id of the Synaptics TouchPad
id=$(xinput list --id-only 'SynPS/2 Synaptics TouchPad')

# Get the current state of the Device Enabled property
# The devString will look like: "Device Enabled (132): 0"
devString=$(xinput --list-props $id | grep "Device Enabled")

# Parse the devString into an array
read -a devString_array <<< "$devString"

# Save the current state of the Device Enabled property
# from the 4th element of devString_array
devEnabled=${devString_array[3]}

# Flip the state of the Device Enabled property
if [ $devEnabled -eq 1 ]; then
    devEnabled=0
else
    devEnabled=1
fi

# Set the "Device Enabled" property with the new value
xinput set-prop $id "Device Enabled" $devEnabled

# Push out a desktop notification of the new value
notify-send --icon computer "Synaptics TouchPad" "Device Enabled = $devEnabled"
exit

```

---

### Post by schragge on 2013-05-04
I'd probably do it like this
```

id=$(xinput --list --id-only 'SynPS/2 Synaptics TouchPad')
devEnabled=$(xinput --list-props $id | awk '/Device Enabled/{print !$NF}')
xinput --set-prop $id 'Device Enabled' $devEnabled
notify-send --icon computer 'Synaptics TouchPad' "Device Enabled = $devEnabled"

```

---

### Post by BCHLLi on 2013-06-10
> **schragge said:**
> I'd probably do it like this
```

id=$(xinput --list --id-only 'SynPS/2 Synaptics TouchPad')
devEnabled=$(xinput --list-props $id | awk '/Device Enabled/{print !$NF}')
xinput --set-prop $id 'Device Enabled' $devEnabled
notify-send --icon computer 'Synaptics TouchPad' "Device Enabled = $devEnabled"

```


Excelent! Works perfectly...

---

### Post by tuxiano on 2014-01-05
Hello,

just adatped your script, so it auto-disables my touchscreen when I use the wacom pen:

```
#!/bin/bash

#Parameter
interval=0.1
off=3
DevNameTouch="eGalax_eMPIA Technology Inc. PCAP MultiTouch Controller"
DevNamePen="Wacom ISDv4 90 Pen stylus"
DevNameErasor="Wacom ISDv4 90 Pen eraser"

#Initialize Variables
id_touch=$(xinput --list --id-only "$DevNameTouch")
id_pen=$(xinput --list --id-only "$DevNamePen")
id_erasor=$(xinput --list --id-only "$DevNameErasor")

xPosPen=$(xinput --query-state $id_pen | grep valuator | cut -d= -f2 | head -n1)
xPosErasor=$(xinput --query-state $id_erasor | grep valuator | cut -d= -f2 | head -n1)
xPosPenOld=$xPosPen
xPosErasorOld=$xPosErasor

#Recognize movement of Wacom Pen or Erasor
while true
do
    devEnabled=$(xinput --list-props $id_touch | awk '/Device Enabled/{print $NF}')
    xPosPen=$(xinput --query-state $id_pen | grep valuator | cut -d= -f2 | head -n1)
    xPosErasor=$(xinput --query-state $id_erasor | grep valuator | cut -d= -f2 | head -n1)    
    
    if [ $devEnabled == 1 ]; then
        #echo "Touchscreen on"
        if [ $xPosPen != $xPosPenOld ] || [ $xPosErasor != $xPosErasorOld ]; then     
            #echo "Recognized movment"            
            xinput disable $id_touch
            notify-send --icon mouse 'Touch Device has been disabled'
        fi
    else
        #echo "Touchscreen off"        
        if [ $xPosPen == $xPosPenOld ] && [ $xPosErasor == $xPosErasorOld ]; then     
            #echo "No movment has beem recognized, so wait"
            sleep $off

            xPosPen=$(xinput --query-state $id_pen | grep valuator | cut -d= -f2 | head -n1)
            xPosErasor=$(xinput --query-state $id_erasor | grep valuator | cut -d= -f2 | head -n1)    

            if [ $xPosPen == $xPosPenOld ] && [ $xPosErasor == $xPosErasorOld ]; then
                xinput enable $id_touch
                notify-send --icon mouse 'Touch Device has been enabled'
            fi                
        fi
    fi
    
    xPosPenOld=$xPosPen
    xPosErasorOld=$xPosErasor    
    
    sleep $interval
done
```

---

### Post by freudsfeud on 2014-04-24
> **schragge said:**
> I'd probably do it like this
```

id=$(xinput --list --id-only 'SynPS/2 Synaptics TouchPad')
devEnabled=$(xinput --list-props $id | awk '/Device Enabled/{print !$NF}')
xinput --set-prop $id 'Device Enabled' $devEnabled
notify-send --icon computer 'Synaptics TouchPad' "Device Enabled = $devEnabled"

```


This thread helped me a lot! Thanks for all of the input and for the code!!

---

### Post by kumoshk on 2014-09-23
Yes, schragge, thank you for the code. It works. I don't use the last line, though.

---

### Post by sderaco on 2015-03-27
Hi there!
Thank you guys! Just to add a modified version of a script you posted, in my case for any touchpad as I have FocalTech instead of Synaptics, to toggle on/off the touchpad.

```
#!/bin/bash


device=$(xinput | grep Touchpad | awk 'match($0,"=") {print substr($0,RSTART+1,2)}')
status=$(xinput list-props $device | grep Enabled | awk '{print $4}')
if [ $status -eq 1 ];then
    xinput disable $device
else
    xinput enable $device
fi
echo "tpad set Touchpad status = $(xinput list-props $device | grep Enabled | awk '{print $4}')"
exit



```

---

