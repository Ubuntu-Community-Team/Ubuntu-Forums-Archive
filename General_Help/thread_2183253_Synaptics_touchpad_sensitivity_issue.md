---
title: "Synaptics touchpad sensitivity issue"
date: 2013-10-24
forum: General Help
---

### Post by zeynel2 on 2013-10-24
I have Ubuntu 12.04 and Samsung laptop. The touchpad sensitivity was set too high and was unusable. I adjusted the sensitivity according to instructions on this page: [https://help.ubuntu.com/community/SynapticsTouchpad#Adjust_Touchpad_Sensitivity](https://help.ubuntu.com/community/SynapticsTouchpad#Adjust_Touchpad_Sensitivity). I reset the numbers with this (my device number is 12): ```
$ xinput --set-prop 12 "Synaptics Finger" 55 70 255
``` 

But when I reboot the numbers go back to old values and I have to reset every time I reboot. Is there a way to make the new numbers permanent so that I don't have to reset them with every reboot?

---

### Post by varunendra on 2013-10-25
Welcome to the forums zeynel2 !

> **zeynel2 said:**
> (my device number is 12)
That device number may change with every reboot. It depends upon which of the keyboard or touchpad was probed first. So you should use its name string instead (within double-quotes). For example, my touchpad is listed as (in the output of "xinput") -
```
&#8627; ETPS/2 Elantech Touchpad                	id=13	[slave  pointer  (2)]
```
So I would use "ETPS/2 Elantech Touchpad" instead of 13.

To make it load automatically at startup, you may add the command to your **/etc/rc.local** file, before the last line "exit 0". To make sure it is executed 'After' the touchpad is properly probed and activated, you may add a delay time (say, 6 seconds) before the command is automatically executed. Something like this -
```
sleep 6 && xinput --set-prop "ETPS/2 Elantech Touchpad" "Synaptics Finger" 55 70 255
```
Make sure the last line in the file remains "exit 0" (this is important!).

To be able to edit the file, you must open it with root access -
```
gksu gedit /etc/rc.local
```

To do the same thing directly from terminal, you can use this command -
```
sudo sed -i 's:^exit 0:sleep 6 \&\& xinput --set-prop "ETPS/2 Elantech Touchpad" "Synaptics Finger" 55 70 255\n&:' /etc/rc.local
```
(it is recommended to first use the above command without "sudo" and "-i" option (sed 's:^exit 0......) to see the result of the command in terminal without actually changing the file. If it is as expected, use again exactly as above.)

---

### Post by zeynel2 on 2013-10-26
Thank you very much for this. I ran the command without "sudo" and "-i" options and I got "exit 0" response from the terminal. Is this what is expected? Can now I go ahead with the command with "sudo" and "-i". Sorry, I am really new to Linux and Ubuntu and I don't exactly understand what is going on.

---

### Post by varunendra on 2013-10-27
The entire output you should see should be -
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sleep 6 && xinput --set-prop "ETPS/2 Elantech Touchpad" "Synaptics Finger" 55 70 255
exit 0
```
So the last line is "exit 0", but there are other lines above it as well. If your output is same as above, then go ahead, the command is fine and so would be it's effect. You can check the file later with -
```
cat /etc/rc.local
```
..which does nothing but just displays the file contents on the terminal.

If you are seeing anything different than above, copy-paste here what you see and I may suggest what is wrong.

In any case, what is required is just editing of a file (to add a single line of command in it) which can always be opened normally with your default text editor. It is just that these system files can only be edited with root privileges, which is why you have to use "gksu gedit..." or things like the above command.

You can also use just -
```
gksu gedit
```
which will open the "gedit" program with a blank file. You can then use its "File > Open" menu or Open button to browse to the file /etc/rc.local > open it > edit it (carefully) > Save & close it (the blank file it opened with in this case should be discarded).

The previous "gksu gedit /etc/rc.local" command I suggested in my previous post opens the gedit program with desired file already opened, so you don't start with an unwanted blank file.

---

### Post by zeynel2 on 2013-10-27
Thank you, Varun. But I run into two problems. I changed the /etc/rc.local as instructed but that gave an error message in bootup (I couldn't read the entire message but it says something like "couldn't recognize touchpad device...." and this had the effect of disabling the two finger scrolling. So I removed that line. So the problem remains, in bootup it goes back to default values.

Also, although I am using the device name now, I noticed that last 3 or 4 restart device name did not change and remained 12. So the problem may be related to something else.

---

### Post by varunendra on 2013-10-27
> **zeynel2 said:**
> "couldn't recognize touchpad device...."

That message almost certainly means the name you used was incorrect. Perhaps you used "ETPS/2 Elantech Touchpad" which was just an example. Post back the output of -
```
xinput
```
so that I can advise the exact name to use.

Another possible cause maybe that 6 seconds was probably too soon to attempt modifying it, maybe it takes longer to get ready itself. With that possibility in mind, you can change 6 to a higher value, like maybe 30 seconds. When it works, try lowering the value step by step until you find a value that is neither too soon nor too long.

And it's id (12) is just a matter of which of the touchpad or keyboard was detected and probed first. It may remain always the same if the keyboard always lags behind in the race. In any case, using a 'fixed' id is not reliable since we know it _is likely_ to change.

---

### Post by zeynel2 on 2013-10-27
```
a@b:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; MOSART Semi. 2.4G Wireless Mouse            id=9    [slave  pointer  (2)]
&#9116;   &#8627; **SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]**
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Webcam SC-10HDD12636P                       id=10    [slave  keyboard (3)]
a@b:~$ 

```
This is the command I used:
```

xinput --set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Finger" 55 70 255

```

I'll try the 30 seconds later. Thanks.

---

### Post by varunendra on 2013-10-27
> **zeynel2 said:**
> ```

&#9116;   &#8627; **SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]**

```
This is the command I used:
```

xinput --set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Finger" 55 70 255

```

Looks correct to me.

As a side note, the touchpad in my laptop seems to be detected at 44 seconds. I'm not sure at which stage the /etc/rc.local script is run. So depending upon the relative timing of its execution from the timing of touchpad's detection, you may have to try an even higher value.

In any case, adding the command in that script is a sure-shot way to run 'Any' command at a desired time after booting. :)

To check when the touchpad becomes ready in your lappy, you can use -
```
cat /var/log/Xorg.0.log | grep -i touchpad
```
The number in the brackets at the start of each line *(e.g. **[    44.832]**)* is the time in seconds since the system booted.

---

