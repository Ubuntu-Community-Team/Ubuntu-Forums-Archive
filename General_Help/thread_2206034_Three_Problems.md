---
title: "Three Problems"
date: 2014-02-17
forum: General Help
---

### Post by lava2 on 2014-02-17
Using 12.04.

After updating the other day, I suddenly have three problems:

- Screen mirroring to my TV over HDMI is screwed up now. As soon as I plug the HDMI cable in, the laptop screen resizes such that the edges are off-screen, and similarly are also off-screen on the TV. 

- My GTK+/Window themes, specifically the min/max/close buttons in the upper left corner, are screwed up. In dark themes they are totally gone (even though they still work if you click in the area), and in light themes you can see them but the close/min buttons are in duplicate and it's slightly offset and overlapping the other set of close/min buttons. Like the graphic is screwed up.

- Last, my Unity dash icons went from being small back to big again. 

- I notice now that I have no third party drivers listed. I haven't looked in that area for probably a year now, but I'm pretty sure I was using an NVIDIA proprietary driver before. When I look in System Details, it says my graphics card and drivers are "unknown". I'd have told you what my video card is by now but that's the only place I know to look for that info. From memory it's a GeForce 4 or 5xx-something.

- I installed nvidia-current in the terminal, but I still don't see any third-party drivers when I pull up the Additional Drivers pane.

What on earth happened here, and how can I fix it?

---

### Post by TheFu on 2014-02-17
I don't have an answer.
I think older nvidia cards are under legacy support now, so nvidia-current won't work for you.
It was smart to reinstall the nvidia drivers post-kernel, just need to find the legacy-nvidia driver somewhere.

So ... I'd look for the nvidia legacy drivers in synaptic or through a PPA to try an solve this.

I'm guessing that software-center won't be able to help at all. Synaptic might, but I'd bet you'll need to find and add a PPA. Honestly, I've never found **any** use for software center.

---

### Post by lava2 on 2014-02-17
I see version 96 and 173 of the Nvidia driver in the Ubuntu Software Center. Do you think either of those would work?

EDIT: Just installed 173 using the Software Center, and it still doesn't show up in my Additional Drivers pane. Any idea why?

---

