---
title: "Mouse speed - Can't decrease it enough"
date: 2017-03-14
forum: General Help
---

### Post by dunya on 2017-03-14
I tried to do it from Mouse and Touchpad options and xset m from terminal does not help much as well. How can I change these settings?

---

### Post by efflandt on 2017-03-15
Ubuntu 16.04 and 16.10 increased default mouse acceleration from something like 2 to 5 that may work fine for a mousepad, but is way to fast for a regular mouse. The cursor would fly across a 1080p screen when I barely moved my mouse and flew around the screen so fast that I could not even tell where the cursor was. If you have a wireless mouse or keyboard with mousepad, there are no gui settings for mouse speed and acceleration.

The xset command sets the same settings for all similar devices. But in my case I wanted to leave the mousepad on any wireless keyboard at default settings, but slow it down for my real mouse. For that **xinput** is more selective than **xset**, see **man xinput**. The xinput command alone gives you a short list to get the device id, and you can use that id to test different settings for the specific device.```
$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® SiderWinderTM X4 Keyboard    id=9    [slave  pointer  (2)]
&#9116;   &#8627; Logitech K400                               id=10    [slave  pointer  (2)]
&#9116;   &#8627; Logitech MX Master                          id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Microsoft Microsoft® SiderWinderTM X4 Keyboard    id=8    [slave  keyboard (3)]

$ xinput --set-ptr-feedback 11 5 2 1
```In this case it sets device 11 to threshold 5, acceleration 2, times the normal 1. A larger threshold would not accelerate until you move the mouse farther quickly or setting acceleration to 1 would disable acceleration.

Once you find settings you like, you can open Dash ("Search your computer" icon at top of Unity bar), begin typing "start", open "Startup Applications", and add your desired xset or xinput command to run automatically when X starts.

---

### Post by dunya on 2017-03-18
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; A4TECH USB Device                           id=12    [slave  pointer  (2)]
&#9116;   &#8627; A4TECH USB Device                           id=13    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_HD                 id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=16    [slave  keyboard (3)]

Thanks for the reply. I am pretty new to Ubuntu (Actually I use Xubuntu). Above you can find the devices I have, but I do not know why my Wireless A4 mouse is listed twice. I wrote: xinput --set-ptr-feedback 13 1/4 1 1 also tried it for 12 1/4 1 1 but both does not seem to help. Is there any other thing I should try?

---

