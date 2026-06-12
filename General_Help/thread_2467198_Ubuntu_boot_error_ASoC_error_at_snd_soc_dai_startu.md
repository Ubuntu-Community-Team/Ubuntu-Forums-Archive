---
title: "Ubuntu boot error: ASoC: error at snd_soc_dai_startup on fef05700.hdmi: -19"
date: 2021-09-18
forum: General Help
---

### Post by fredrum on 2021-09-18
Hello!!
[COLOR=#232629][FONT=-apple-system]I recently installed 'Ubuntu Desktop 21.04' on a sd card for my Raspberry Pi4b and while it seemed fine to start with after one or two reboots I get errors and wasn't able to boot back in again.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I tried again to flash the card with that same image and same thing happened. It was fine in the very first session but then I got this boot error that I haven't been able to solve.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]The error message I kept getting was:
```
[FONT=var(--ff-mono)]ASoC: error at snd_soc_dai_startup on fef05700.hdmi: -19[/FONT][/FONT][/COLOR]
```

[COLOR=#232629][FONT=-apple-system]I read some comment saying it might be because of non-existing audio on the monitor but Iv'e successfully passed audio from HDMI->3.5mmjack out from the monitor under Raspbian OS.

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Iv'e also seen some recent and some threads a few months old with people mentioning the same error messages.
Often it leads to discussions involving Kodi. Seems to be some audio+hdmi related kernel thing?[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Here's a recent and similar chat, [https://github.com/raspberrypi/linux/issues/4575](https://github.com/raspberrypi/linux/issues/4575)[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]
I also saw another user who reported a 'spontaneous reboot' which I suspect happened to me on my first try. (I wasn't in the room)
[https://www.raspberrypi.org/forums/viewtopic.php?f=63&t=316295](https://www.raspberrypi.org/forums/viewtopic.php?f=63&t=316295)

So last night I tried to find an older Ubuntu image and got a Ubuntu Mate 20.04.3. This has worked fine and I didn't get that error even after several reboots. It's using Kernel 5.4.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]
[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I can't use the older Ubuntu as I need the newer 'dma-buf' kernel updates that seem to be post 5.4.

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Is there anyone who knows what this issue might be?

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Cheers.[/FONT][/COLOR]

---

