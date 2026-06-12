---
title: "Ctrl and Fn key transformed to shift key"
date: 2017-03-13
forum: General Help
---

### Post by webbtraverse on 2017-03-13
After having watched a football game on wilmaa.com yesterday, my left Ctrl and Fn keys have transformed into shift keys. I don't know what media player they use, though. I'm using ubuntu 16.04 and Firefox 52.0 64 bit on an Acer Aspire ES 15 laptop. I've found some similar issues with these keys on Gnome in some forums, but don't know yet how to resolve the problem. I'm on Linux for several years now, but basically not really a geek, I just know doing some basic stuff in a terminal. Do you think [this]("https://superuser.com/questions/88835/my-control-key-doesnt-work-how-do-i-fix-it") might be the solution or do you have other suggestions?

The terminal gives the following outputs for  xev | grep -i keyrelease -A5:

For the left Ctrl key:

```
KeyRelease event, serial 37, synthetic NO, window 0x4200001,
    root 0xf7, subw 0x0, time 26607973, (-40,252), root:(757,304),
    state 0x1, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

For the Fn key:

```
KeyRelease event, serial 37, synthetic NO, window 0x4200001,
    root 0xf7, subw 0x0, time 26693629, (-239,195), root:(558,247),
    state 0x1, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

Thanks in advance for your help!

---

### Post by QIII on 2017-03-13
Hello!

Please use code tags around terminal commands and results.  That will preserve formatting and avoid incorrect interpretation of character strings as things like smileys.

To use code tags:

1.  Click the # symbol above the text entry box, place your cursor between the code tags that appear and type or paste your text.

2.  Type or paste your text, highlight it, and click the # button.

3.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after your text.  The square brackets are required.

---

### Post by webbtraverse on 2017-03-13
Of course, I'm sorry, I haven't paid attention!

---

### Post by QIII on 2017-03-13
No problem.  It's just hard to read code sometimes when there are scattered smilies, frownies, evil grins and pink unicorns mixed in.

:)

---

