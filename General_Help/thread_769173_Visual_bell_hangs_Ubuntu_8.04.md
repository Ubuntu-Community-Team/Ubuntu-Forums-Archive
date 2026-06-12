---
title: "Visual bell hangs Ubuntu 8.04"
date: 2008-04-26
forum: General Help
---

### Post by toni-meireles on 2008-04-26
Hi.

I've just installed Ubuntu 8.04 and I have the most strange problem. Whenever the system's visual bell goes off my system completely hangs. No response from anything! The only way to get out is pressing the power button long enough for the laptop to shutdown.

It took me quite some time to narrow it down to the visual bell as it seemed completely random. It happens whether I boot normally into X or even in console mode when I boot in recovery mode.

I'm pretty certain that the problem is the visual bell because the system kept hanging when I opened a terminal and hit the Tab key. I then added:

```
set bell-style none
```

to my *~/.inputrc* and the problem where gone on the terminal. The system still hangs every now and then when some other application sends a visual bell signal.

It even happened to me during the install process when trying out my keyboard layout.

Does anyone have any idea what could be causing this? Alternatively, I'd also settle for disabling the visual bell altogether in the meantime.

Thanks in advance.

---

