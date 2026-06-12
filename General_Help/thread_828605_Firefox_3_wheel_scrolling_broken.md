---
title: "Firefox 3 wheel scrolling broken"
date: 2008-06-13
forum: General Help
---

### Post by anjilslaire on 2008-06-13
I noticed today that something's amiss in Firefox: Whenever I scroll up with the mouse wheel, FF acts like the Back button is pressed, and the previous page is loaded. This is a highly annoying, to say the least.

This appears to be an issue with Firefox 3, not xorg or the mouse. If I load FF 2.0.0.14, it behaves fine, and it also behaves correctly in Konqueror.
I've checked about:config and everything seems in order
```

mousewheel.horizscroll.withnokey.action = 0
mousewheel.withnokey.action = 0

```

and xorg has been tried with both configurations:
```

Section “InputDevice”
Identifier    “Configured Mouse”
Driver        “mouse”
Option        “CorePointer”
Option        “Device”    “/dev/input/mice”
Option        “Protocol”    “ExplorerPS/2&#8243;
Option        “ZAxisMapping”    “4 5&#8243;
Option        “Emulate3Buttons”    “false”
EndSection

```
and
```

Section “InputDevice”
Identifier    “Configured Mouse”
Driver        “mouse”
Option        “CorePointer”
EndSection

```

Any thoughts? It just cropped up, and is driving me nuts.
Kubuntu Hardy 8.04 x86
package version 3.0~rc1+nobinonly-0ubuntu0.8.04.1

Thanks :)

---

### Post by Happy_Man on 2008-06-13
Try deleting your .mozilla folder, and then using a Firefox package downloaded from here: [http://download.mozilla.org/?product=firefox-3.0rc3&os=linux&lang=en-US](http://download.mozilla.org/?product=firefox-3.0rc3&os=linux&lang=en-US) to make sure it's firefox and not something else on your computer.

---

### Post by anjilslaire on 2008-06-13
Nope, its Firefox. It does the same thing with the archive from Mozilla. Of course, going back to 2.0.0.14 resolves the issue, and its not present in other browsers and file managers. Definitely seems to be something in the FF 3 builds...

---

### Post by anjilslaire on 2008-06-14
Update:
Tired of fighting it. Browsing needs to be a hassle-free function, so I went back to 2.0.0.14. I'll try 3 out again in a few weeks, and see how it goes.

---

