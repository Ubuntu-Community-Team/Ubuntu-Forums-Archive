---
title: "Where's my pipe?"
date: 2006-10-26
forum: General Help
---

### Post by laurenx on 2006-10-26
I have a problem with my screensaver (crashes when it kicks in - it's another thread) and the last advice I had yesterday was to input a command inlcuding a pipe (to check whether my graphics card was acclerated or not). I have a long vertical line on my keyboard (on the right above he enter key) but it refuses to produce a pipe, even in combination with shift, alt or ctrl. How can I produce a pipe from a standard keyboard?

Laurenx

---

### Post by christhemonkey on 2006-10-26
Mine is <shift>+<\>

(Second function backslash)

or the 3rd function next to 1, but i cant get that to work.

---

### Post by lloyd_b on 2006-10-26
Is your machine configured for a standard US Keyboard?  The pipe symbol is exactly where you were looking - it's "Shift" + "Backslash", which is located right above the enter key.

If that key combination isn't producing the pipe symbol, then what IS it producing (knowing that might help sort things out).

Lloyd B.

---

### Post by laurenx on 2006-10-26
I get tilda "~" from that (shift + \). I live in Thailand, but they have to use linux here don't they?

laurenx

---

### Post by laurenx on 2006-10-26
I have changed my keyboard to an old US Dell; the pipe key (shift + key above the right enter key) still produces a tilder ~. Doesn;t that mean  that it isn't the keyboard that is the problem, but something in the software - say a font or something? Anybody any suggestions how I can produce a pipe character?

laurenx

---

### Post by IYY on 2006-10-27
I highly doubt it's the font. Just out of curiosity, copy and paste the following pipe character into your terminal/wherever you want a pipe: |

I think it should still display as a pipe, meaning the problem is with the way your key press is interpreted. Could you perhaps show a photograph of your keyboard? You might be able to find a picture of a similar one online.

---

### Post by lloyd_b on 2006-10-27
> I have changed my keyboard to an old US Dell; the pipe key (shift + key above the right enter key) still produces a tilder ~. Doesn;t that mean that it isn't the keyboard that is the problem, but something in the software - say a font or something? Anybody any suggestions how I can produce a pipe character?

Could you post a copy of the file "/etc/X11/xorg.conf"?

The problem isn't with the keyboard itself - it's that something in your system has been told to interpret the "scan codes" from the keyboard incorrectly.

What I'm looking for is a section in xorg.conf that looks like this:
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection
```

I suspect that on your system, the "XkbModel" and "XkbLayout" are set to something different, and I'm curious to see what.

Lloyd B.

---

