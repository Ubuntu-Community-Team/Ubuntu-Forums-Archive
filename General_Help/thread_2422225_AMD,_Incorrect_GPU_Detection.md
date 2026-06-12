---
title: "AMD, Incorrect GPU Detection"
date: 2019-07-03
forum: General Help
---

### Post by Axxon95 on 2019-07-03
Not entirely sure on where to go to ask this, but I figure General Help should work.

My laptop is running an AMD A8-7410 with AMD R5 (lspci shows Mullins) Graphics. Ubuntu 19.04 x64
I wanted to use Oibaf or Padoka to test the latest Drivers and such, specifically Vulkan. When I add either of those PPAs, before I restart I check OpenGL support, it states Kabini and when I restart I get met with a Black Screen. I've tried using Radeon and AMDGPU drivers(with modprobe blacklisting).

Is there any way for me to correct the GPU detection on my end?

Thanks.

Edit: Oibaf seems to be working now after a week or so,  but it is still incorrectly showing OpenGL Render String, and RADV Vulkan as Kabini.
Edit 2: Padoka is now working with disable Wayland support in GDM3 config file.

I'll mark as solved. I think the name change from Mullins to Kabini was made in MESA or something. No idea.

---

