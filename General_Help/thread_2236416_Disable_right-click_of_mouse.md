---
title: "Disable right-click of mouse ??"
date: 2014-07-26
forum: General Help
---

### Post by sarahfoxnz on 2014-07-26
Hello.

Is there a way i can disable the right-click (or left) of my mouse & then turn it on agin later ?

Basically, i play an online game & I think its run on FLASH technology.  I use the left button to perform tasks.

The problem is - if i accidentally press the right-button, the game freezes / stops.  I can sometimes get it to start / resume - but usually i need to close down the browser tab & start again.

the game is Bloons.

is there a way to disable ONE button ?

---

### Post by Paulgirardin on 2014-07-26
The following threads describe how to disable various mouse functions:
[http://ubuntuforums.org/showthread.php?t=2065400](http://ubuntuforums.org/showthread.php?t=2065400)

[http://askubuntu.com/questions/59128/how-to-disable-mouse-wheel-scroll-in-ubuntu-11-04-or-10-10](http://askubuntu.com/questions/59128/how-to-disable-mouse-wheel-scroll-in-ubuntu-11-04-or-10-10)

---

### Post by sarahfoxnz on 2014-07-26
thanks.   However I am getting stuck at 

> 
 $ xinput get-button-map 3
device has no buttons


i've tried 1,2,3 etc - But no luck

Here is my full process

> 
sarah@LinuxPC:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft Wireless Optical Desktop® 2.10    id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Microsoft Microsoft Wireless Optical Desktop® 2.10    id=8    [slave  keyboard (3)]
    &#8627;   USB Keyboard                              id=10    [slave  keyboard (3)]
    &#8627;   USB Keyboard                              id=11    [slave  keyboard (3)]




and  (I found my mouse has ID=9 - right ?)
> 


sarah@LinuxPC:~$ xinput list 9
Microsoft Microsoft Wireless Optical Desktop® 2.10    id=9    [slave  pointer  (2)]
    Reporting 13 classes:
        Class originated from: 9. Type: XIButtonClass
        Buttons supported: 13
        Button labels: "Button Left" "Button Middle" "Button Right" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right" "Button Side" "Button Extra" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown"
        Button state:
        Class originated from: 9. Type: XIKeyClass
        Keycodes supported: 248
        Class originated from: 9. Type: XIValuatorClass
        Detail for Valuator 0:
          Label: Rel X
          Range: -1.000000 - -1.000000
          Resolution: 1 units/m
          Mode: relative
        Class originated from: 9. Type: XIValuatorClass
        Detail for Valuator 1:
          Label: Rel Y
          Range: -1.000000 - -1.000000
          Resolution: 1 units/m
          Mode: relative
        Class originated from: 9. Type: XIValuatorClass
        Detail for Valuator 2:
          Label: Rel Horiz Wheel
          Range: -1.000000 - -1.000000
          Resolution: 1 units/m
          Mode: relative
        Class originated from: 9. Type: XIValuatorClass
        Detail for Valuator 3:
          Label: Rel Dial
          Range: -1.000000 - -1.000000
          Resolution: 1 units/m
          Mode: relative
        Class originated from: 9. Type: XIValuatorClass
        Detail for Valuator 4:
          Label: Rel Vert Wheel
          Range: -1.000000 - -1.000000
          Resolution: 1 units/m
          Mode: relative
        Class originated from: 9. Type: XIValuatorClass
        Detail for Valuator 5:
          Label: Rel Misc
          Range: -1.000000 - -1.000000
          Resolution: 1 units/m
          Mode: relative
        Class originated from: 9. Type: XIValuatorClass
        Detail for Valuator 6:
          Label: None
          Range: -1.000000 - -1.000000
          Resolution: 1 units/m
          Mode: relative
        Class originated from: 9. Type: XIValuatorClass
        Detail for Valuator 7:
          Label: None
          Range: -1.000000 - -1.000000
          Resolution: 1 units/m
          Mode: relative
        Class originated from: 9. Type: XIScrollClass
        Scroll info for Valuator 2
          type: 2 (horizontal)
          increment: 1.000000
          flags: 0x0
        Class originated from: 9. Type: XIScrollClass
        Scroll info for Valuator 3
          type: 1 (vertical)
          increment: -1.000000
          flags: 0x0
        Class originated from: 9. Type: XIScrollClass
        Scroll info for Valuator 4
          type: 1 (vertical)
          increment: -1.000000
          flags: 0x2 ( preferred )

sarah@LinuxPC:~$ 



the right button is the 3rd button right ? but (as above) I got no results.

basically, i want to turn the right-button off (& turn it on again later)

---

