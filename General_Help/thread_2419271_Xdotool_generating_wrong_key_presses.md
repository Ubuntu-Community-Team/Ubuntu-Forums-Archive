---
title: "Xdotool generating wrong key presses"
date: 2019-05-19
forum: General Help
---

### Post by tigrezno on 2019-05-19
Hi everyone, I'm trying to emulate the numpad since my keyboard doesn't come with it.

At the moment I'm using xdotool to generate keys like **KP_1**, **KP_2**, and so on.
But the problem is it's not generating only **KP_1** but also the alternative for that key, **KP_End**, along with some **Shift_L**.
It seems the problem is xdotool is adding **SHIFT_L** to the key event even with clearmodifiers added.
Here is a capture from _xev_ that shows the problem when **KP_1** is sent via xdotool: 

[IMG]https://i.imgur.com/cptUae2.png[/IMG]

I used this command to generate the key press:

```
xdotool key --clearmodifiers KP_1
```

How can I get a "single" **KP_1** press? 
Thanks

[SOLVED]

Ok, the problem is I tried to directly generate **KP_1**, **KP_2**, **KP_3**, when I should have used the alternative, this is: **KP_End**, **KP_Down**, ..., and change between them with the **Num_Lock**.

This way it works perfectly.

---

