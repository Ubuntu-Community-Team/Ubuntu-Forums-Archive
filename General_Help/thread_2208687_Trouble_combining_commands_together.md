---
title: "Trouble combining commands together"
date: 2014-03-01
forum: General Help
---

### Post by aruth on 2014-03-01
Hello, I am running ubuntu on tablet pc and would like to get screen rotation functionality working correctly. I have found that in addition to rotating the screen the stylus also has to be rotated. So there are two commands that must be ran at the same time. I would like to run these commands via Easystroke so I can make gestures to rotate the screen any which way. The two commands used together work correctly when I set the screen in normal or inverted position, but not in left or right position.

I have found to rotate the screen I should use xrandr as in:

xrandr --output eDS1 --rotate left

And to rotate the stylus I need to use xinput as in:

:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ASUS ASUS Wireless Input Receiver           id=9    [slave  pointer  (2)]
&#9116;   &#8627; ASUS ASUS Wireless Input Receiver           id=10    [slave  pointer  (2)]
&#9116;   &#8627; Atmel Atmel maXTouch Digitizer              id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Asus 2.0 USB Webcam                         id=11    [slave  keyboard (3)]
    &#8627; Asus 2.0 USB Webcam                         id=12    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=14    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=15    [slave  keyboard (3)]


xinput set-prop 13 "Coordinate Transformation Matrix" 0 -1 1 1 0 0 0 0 1

If I perform each of these commands individually my screen is rotated and when I press the touch screen the cursor acts in the right place. However, when I try to combine them together an error shows up that wasn't there before

 :~$ xrandr --output eDP1 --rotate left ; xinput set-prop 13 "Coordinate Transformation Matrix" 0 -1 1 1 0 0 0 0 1unable to find device 13

The screen gets rotated, but the touch input does not

I have also tried using && instead of ; and using the full device name instead of the id 13. I also tried putting the commands in a file and running them that way, but the results is the same. Its strange that it only happens when I rotate left or right but normal and inverted work just fine. Does anyone know why this could be happening or a simple solution?

---

### Post by TheFu on 2014-03-01
Don't have a clue, but .... perhaps a 1 second sleep between the commands will help?  Maybe not , but it is worth a try.
[B]
sleep 1;[/B]

---

### Post by aruth on 2014-03-03
Yay, it worked. Thanks a lot. I guess it must take a second to recover after rotating the screen.

For the record anyone trying to get this screen rotation and stylus rotation to work simultaneously can use the following 4 commands. You will have to replace your screen with the eDP1(type xrandr with no arguments to see device list) and your touch device id with the 13.(You can get this from ```
xinput list
```)

Normal
```
xrandr --output eDP1 --rotate normal ;  sleep 1; xinput set-prop 13 "Coordinate Transformation Matrix" 1 0 0 0 1 0 0 0 1
```

Right
```
xrandr --output eDP1 --rotate right ;  sleep 1; xinput set-prop 13 "Coordinate Transformation Matrix" 0 1 0 -1 0 1 0 0 1
```

Left
```
xrandr --output eDP1 --rotate left ;  sleep 1; xinput set-prop 13 "Coordinate Transformation Matrix" 0 -1 1 1 0 0 0 0 1
```

Inverted
```
xrandr --output eDP1 --rotate inverted ; sleep 1;  xinput set-prop 13 "Coordinate Transformation Matrix" -1 0 1 0 -1 1 0 0 1
```

---

### Post by TheFu on 2014-03-03
Really?  That worked?  Who knew?

Anyway, please mark the thread as SOLVED to help others.

---

