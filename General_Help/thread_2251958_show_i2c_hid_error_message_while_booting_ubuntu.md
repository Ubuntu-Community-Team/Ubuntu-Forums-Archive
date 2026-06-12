---
title: "show i2c_hid error message while booting ubuntu"
date: 2014-11-07
forum: General Help
---

### Post by b4456609 on 2014-11-07
I installed ubuntu 14.10 in my new laptop acer E3-112-C31G.
First, I found the bluetooth couldn't find any device.
And the touchpad can't work after suspend.

I google for solutions. I upgrade kernel. and all problems solved.

But I saw this message while booting ubuntu using newer kernel.
[ATTACH=CONFIG]257815[/ATTACH]
And my touchpad works well.
I try to blacklist i2c_hid, but i can't use my touchpad.

```
:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SYN1B7D:01 06CB:2991 UNKNOWN                id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HD WebCam                                   id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                            id=13    [slave  keyboard (3)]


```

```
I: Bus=0018 Vendor=06cb Product=2991 Version=0100
N: Name="SYN1B7D:01 06CB:2991 UNKNOWN"
P: Phys=
S: Sysfs=/devices/platform/80860F41:00/i2c-0/i2c-SYN1B7D:01/0018:06CB:2991.0001/input/input5
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=1
B: EV=b
B: KEY=6420 10000 0 0 0 0
B: ABS=260800000000003


```

output devices.txt
[ATTACH]257816[/ATTACH]

output dmesg.txt
[https://drive.google.com/file/d/0B6dWDK46zEWkUHRTMmxQNFVBQ3M/view?usp=sharing](https://drive.google.com/file/d/0B6dWDK46zEWkUHRTMmxQNFVBQ3M/view?usp=sharing)

please help me. thank you.

---

### Post by baumkuchen2 on 2014-11-09
> **b4456609 said:**
> And the touchpad can't work after suspend.
I google for solutions. I upgrade kernel. and all problems solved.
[…]
I try to blacklist i2c_hid, but i can't use my touchpad.

Same touchpad problem and blacklist behaviour here with a new installed Acer Aspire V3-371-37YM. Couldn't find a solution. However it seems not to be perfectly working (error messages) can you please tell me what you've done with kernel?

---

### Post by raggar on 2015-03-30
Not sure if this helps you. But it did help me a lot on my acer aspire V3-371 I randomly experienced my mousepointer to move up and down and strange behavior. I found this and it helped a lot. Also I don't see the errors anymore. 
[http://www.iq-tm.de/TP%20freeze.htm](http://www.iq-tm.de/TP%20freeze.htm)

---

