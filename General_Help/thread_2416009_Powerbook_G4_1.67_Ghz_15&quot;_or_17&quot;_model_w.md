---
title: "Powerbook G4 1.67 Ghz 15&quot; or 17&quot; model won't sleep and doesn't wake from suspend"
date: 2019-04-03
forum: General Help
---

### Post by mrcobalt124 on 2019-04-03
I have a Powerbook G4 1.67 Ghz (That i'm writing this on) running Lubuntu 16.04 PPC port. It doesn't sleep when I shut the lid, but it says it can't lock when I open it again.

When I run ```
sudo pm-suspend
```
Nothing happens. No output, no suspending, nothing.

 When I run ```
sudo systemctl suspend
```

The screen turns off, the fans stop, and most things just stop, but the light doesn't blink.

This is the only problem I have running Lubuntu, other than sometimes having to fight with the brightness controls.

How can I make it sleep?
I was thinking maybe there was some tool that could help. Although if I was handed a guide with a bit of info on sleep APIs or something I could probably whip up my own custom sleep driver, as I did with my fans.

---

