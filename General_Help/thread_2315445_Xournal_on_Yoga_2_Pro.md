---
title: "Xournal on Yoga 2 Pro"
date: 2016-02-28
forum: General Help
---

### Post by sarah26 on 2016-02-28
[FONT=Ubuntu]I am having trouble using Xournal on my Lenovo Yoga 2 Pro capacitive touchscreen without an active digitizer. When using the mouse or the touchpad, I am able to create strokes normally. However, when using my finger on the touchscreen, the following happens:[/FONT]


[FONT=Ubuntu]When X-input is enabled[/FONT]

[LIST]
[*][FONT=Ubuntu]All strokes are registered as dots placed where the stroke started[/FONT]
[*][FONT=Ubuntu]When    the command “xinput --map-to-output "ELAN Touchscreen"    eDP1” is run, the first stroke is registered correctly and can    produce a line, but all subsequent strokes are registered as dots    again[/FONT]
[/LIST]
[FONT=Ubuntu]When X-input is disabled[/FONT]

[LIST]
[*][FONT=Ubuntu]Some    strokes are registered as dots, others are not registered at all.    About 1 out of every 5 presses produces as a dot where the stroke    started[/FONT]
[*][FONT=Ubuntu]When    double tapping, if the first tap produces a dot, the second tap can    correctly produce a line[/FONT]
[*][FONT=Ubuntu]When    the command “xinput --map-to-output "ELAN Touchscreen"    eDP1” is run, the first stroke is registered correctly and can    produce a line, but all subsequent strokes are registered as either    dots or nothing[/FONT]
[/LIST]


[FONT=Ubuntu]Running“xinput” produces the following:[/FONT]


&#9121; [FONT=Ubuntu]Virtualcore pointer                                id=2    [master     pointer      (3)] [/FONT]
&#9116;   &#8627; [FONT=Ubuntu]Virtualcore XTEST pointer                      id=4    [slave      pointer      (2)] [/FONT]
&#9116;   &#8627; [FONT=Ubuntu]ELANTouchscreen                                id=10    [slave          pointer      (2)] [/FONT]
&#9116;   &#8627; [FONT=Ubuntu]SynPS/2Synaptics TouchPad                  id=13    [slave         pointer      (2)] [/FONT]
&#9116;   &#8627; [FONT=Ubuntu]MicrosoftSculpt Comfort Mouse              id=9    [slave      pointer      (2)] [/FONT]
&#9123; [FONT=Ubuntu]Virtualcore keyboard                           id=3    [master     keyboard    (2)] [/FONT]
    &#8627; [FONT=Ubuntu]Virtualcore XTEST keyboard                 id=5    [slave      keyboard     (3)] [/FONT]
    &#8627; [FONT=Ubuntu]PowerButton                                        id=6    [slave      keyboard     (3)] [/FONT]
    &#8627; [FONT=Ubuntu]VideoBus                                           id=7    [slave      keyboard     (3)] [/FONT]
    &#8627; [FONT=Ubuntu]PowerButton                                        id=8    [slave      keyboard     (3)] [/FONT]
    &#8627; [FONT=Ubuntu]LenovoEasyCamera                               id=11    [slave      keyboard     (3)] [/FONT]
    &#8627; [FONT=Ubuntu]ATTranslated Set 2 keyboard                id=12    [slave      keyboard     (3)]

[/FONT][FONT=Ubuntu]Do you have any advice as to what I can do to get Xournal working withmy touchscreen?

[/FONT]
[FONT=Ubuntu]Thanks for your help![/FONT]

---

### Post by sarah26 on 2016-02-29
Hello all,

I have found a fairly simple solution.

After uninstalling and reinstalling Xournal from the Software Center multiple times with no success, I decided to look online. I uninstalled the version from the software center and used the following webpage to install the latest version of Xournal

[http://www.geekssharingspace.org/2014/07/how-to-install-xournal-048-windows.html](http://www.geekssharingspace.org/2014/07/how-to-install-xournal-048-windows.html)

It now works flawlessly.

Thanks for looking!

---

### Post by sudodus on 2016-02-29
Welcome to the Ubuntu Forums, and thanks for sharing your solution :KS

(I'm using xournal, but not with a touchscreen.)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED. It will help people find your solution.

---

