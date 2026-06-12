---
title: "hdmi showing disconnected and not reconnecting when television powered off"
date: 2017-04-28
forum: General Help
---

### Post by JasonKretzer on 2017-04-28
Using :
16.04 64bit
Official Intel Display Drivers (also occurs with default)
Intel ComputeStick

I am using an Intel stick connected to an LG television via HDMI.  
If I do any of the following:
1) Change input to a different source and reboot while changed
2) Unplug the television and reboot while off
3) Turn off the television and reboot while off
4) Disconnect the stick HDMI from the television and reboot and then plug back in to television

When I turn the television back on or return to the proper input source, the television indicates there is no signal.  (Note that the above is how I guarantee to reproduce the problem, sometimes the loss of signal occurs even if I don't reboot in those scenarios)

To get a better idea of what was going on, I installed TeamViewer.  I replicated the above and then remotely accessed via TeamViewer.  I then opened a terminal and used
```

$ xrandr
HDM1 disconnected

```

When I ran this command, the television was turned on and was at the correct input and the stick was connected via hdmi.

I use this for digital signage and the television is mounted to the point where I must use a ladder to physically reach the stick to manually reboot (all wires go into the wall behind the television).  As such, I would like very much to be able to just turn the television off and on and change input, etc. without having to worry about it.  Thoughts?

---

