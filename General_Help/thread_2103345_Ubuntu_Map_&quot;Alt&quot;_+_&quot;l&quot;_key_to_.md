---
title: "Ubuntu Map &quot;Alt&quot; + &quot;l&quot; key to &quot;Left&quot; arrow key"
date: 2013-01-09
forum: General Help
---

### Post by trankhanh89 on 2013-01-09
Hi all,

In my Ubuntu 12.10, I want to map the "Alt" and "l" keys to the "Left" key (Which is when I type "Alt" and "l" together It will function like I press "Left" key).
I use this command: 
```
 xmodmap -e "keycode 46 mod1 = l Left"
```
(I checked "l" keycode with ```
xev
``` command and it tells me that 46 is l's keycode).

But it doesn't work :(. Can you suggest me a more accurate way?

Here is the result after I run "xmodmap -pm" in terminal:

```
shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Alt_R (0x6c),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x85),  Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)
```

Thank you.

---

### Post by trankhanh89 on 2013-01-10
Any idea or suggestion are welcome.

---

