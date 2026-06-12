---
title: "Remap buttons on a secondary device"
date: 2014-10-27
forum: General Help
---

### Post by sixtimes on 2014-10-27
I've seen a number of discussions that are similar to this issue but I haven't yet been able to get this working.

I recently broke my left pinky finger pretty badly. I got the [Fragpedal Quad]("http://www.gamingmouse.com/gaming/fragpedal/quad/") and am trying to remap the pedals to things like control and alt and tab.

The device behaves like a mouse - by default, the pedals are mapped to scroll wheel up, scroll wheel down, right click and left click. When I run xinput, I get the following:

```

&#9121; Virtual core pointer                      id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Good Work Systems, Inc. GWS IDI Device    id=9    [slave  pointer  (2)]
&#9116;   &#8627; PixArt USB Optical Mouse                  id=11   [slave  pointer  (2)]
&#9123; Virtual core keyboard                     id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; Good Work Systems, Inc. GWS IDI Device    id=10   [slave  keyboard (3)]
    &#8627; Lenovo Lenovo Black Silk USB Keyboard     id=12   [slave  keyboard (3)]
    &#8627; Lenovo Lenovo Black Silk USB Keyboard     id=13   [slave  keyboard (3)]

```

The pedals are the "Good Work Systems" device.

The closest I've gotten to getting this to behave how I want was creating and editing an .xbindkeys configuration as such:

```

# Copy
"xte 'keydown Control_L' 'key C' 'keyup Control_L'"
  b:5

# Cut
"xte 'keydown Control_L' 'key X' 'keyup Control_L"
  b:4

# Paste
"xte 'keydown Control_L' 'key V' 'keyup Control_L'"
  b:3

# Select All
"xte 'keydown Control_L' 'key A' 'keyup Control_L'"
  b:1

```

But this affects my regular mouse buttons too. How do I specify a per-device keymapping?

---

