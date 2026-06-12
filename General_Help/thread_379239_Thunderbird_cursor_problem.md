---
title: "Thunderbird cursor problem"
date: 2007-03-08
forum: General Help
---

### Post by svenster on 2007-03-08
Hello,

I have a cursor issue with Mozilla Thunderbird: when I write messages and use the cursor keys to navigate around the text, the cursor leaves traces (pixels) wherever it went. This makes it really hard to read the words and also to find the current cursor position.

I am running the most up-to-date version of Thunderbird on Edgy Eft. The machine is an Acer laptop with a widescreen display and fairly low resolution (~1280x800). The fonts look as if they're anti-aliased (smooth edges).

I have tried changing fonts, sizes and encoding but the problem remains. Do you know if this can be fixed?

Thanks!
Sven

---

### Post by svenster on 2007-03-09
Found a solution and can now answer my own question:

The problem is due to the driver for my graphics card. The card is a Geforce Go 7300 and I was using the default driver that comes with Edgy. The cursor ghosting actually happened is all sorts of applications including Firefox and OpenOffice Writer (esp in tables) but was most pronounced in Thunderbird.

The following thread describes the issue and details a solution (this did not work for me but for plenty of other users): [http://www.ubuntuforums.org/showthread.php?t=168090&highlight=cursor+ghosting](http://www.ubuntuforums.org/showthread.php?t=168090&highlight=cursor+ghosting)
My issue with this was that the driver kernel module (once compiled) failed to load.

I then followed the instructions here: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)
(up to the point saying: and replacing "nv" with "nvidia")

This has resolved the cursor issue in all applications and works fine.

Hope this helps!
Sven

---

