---
title: "Turn off touch screen at bootup."
date: 2016-09-06
forum: General Help
---

### Post by irv on 2016-09-06
I have a touch screen on my laptop that I never use so when I first power on my laptop I run the command:
```
xinput set-prop 12 'Device Enabled' 0
```
12 is the id for my touch screen. This works just fine. Now if someone walks by when I am on my laptop my mouse pointer is not moving around because of the wind hitting the screen. (That's why I don't like touchscreens on a laptop). Give me a keyboard and mouse.
I was wondering what the easiest way is to just have the above command run at bootup?
I know there are different ways to do this but was wondering what the easiest way would be?

---

### Post by irv on 2016-09-06
I thought this to be the easiest route.
I open up startup Applacations and added the command 
```
xinput set-prop 12 'Device Enabled' 0
```
to a process I called "turn off touchscreen".
I will makr this thread soloved.

---

