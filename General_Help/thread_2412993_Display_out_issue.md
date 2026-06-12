---
title: "Display out issue"
date: 2019-02-19
forum: General Help
---

### Post by ProDigit on 2019-02-19
Hey guys,

I'm having an Asus motherboard with Intel Core i5 7400, 
The motherboard has VGA and DVI out for the onboard graphics.
I use my computer for folding and mining, and it has 2x GTX 1060 cards installed.
Lubuntu doesn't want to boot via integrated graphics.
What I get is the boot screen, and then blank.
From the responses my PC gives me, I can see Lubunu is started, in GUI mode, but there just isn't anything but a black screen on the display out.

Even setting nvidia-server to the intel IGP, causes Lubuntu to give a black screen on the IGP display out; while the DGPUs are having no signal.

The only way I can make Lubuntu work, is by setting the graphics drivers to the NVidia card in the first PCIE slot, and connect my monitor there and reboot.

Same goes for trying to make it work via Bios.
If I have no DGPUs, Lubuntu runs fine from the IGP.
But once a DGPU is installed, Lubuntu expects it to run from the DGPU.

This is not a biggie, however, I would prefer to use the IGP for display out, as it's only displaying either the terminal or X11.
Running my monitor on the DGPU uses about 2-5% of it's processing power, which I'd rather keep for folding/mining.

Is there any solution to this?

---

