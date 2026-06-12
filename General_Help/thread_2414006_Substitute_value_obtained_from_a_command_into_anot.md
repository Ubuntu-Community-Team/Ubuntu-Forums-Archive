---
title: "Substitute value obtained from a command into another command"
date: 2019-03-04
forum: General Help
---

### Post by raleigh3 on 2019-03-04
The window id for the particular popup window is different each time, so this scripts often does not work
 ```
 .#!/bin/bash   
    # xdotool selectwindow This determines the window id 
    # 2nd method of determining window id
    # xdotool search --name "Error"
    #
    # Does not work because for some reason, the window id is different every time ?
    xdotool key --window 16777491 alt+F4
    # 
    #16777782
    #16777491
    #16778087
``` 
This gives me the correct window id.

```
xdotool search --name "Error" > Window_IDs.txt

```
I just need it to substitute the value it gets for the 16777491 in this

  ```
xdotool key --window 16777491 alt+F4


```

---

### Post by HermanAB on 2019-03-04
I would try something like:
export VAL
VAL=$(xdotool yadda yadda)
$(xdotool yadda "$VAL")

---

