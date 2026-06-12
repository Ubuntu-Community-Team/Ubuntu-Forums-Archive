---
title: "Frequent freezes after upgrading 18.04 LTS"
date: 2020-01-22
forum: General Help
---

### Post by gregstoll on 2020-01-22
Hi all!  I recently upgraded some packages (including the kernel) on my 18.04 LTS system, and now after I login X freezes within 30-60 seconds.  (it fits the [freeze description perfectly]("https://wiki.ubuntu.com/X/Troubleshooting/Freeze") - mouse can still move sometimes but can't click on anything, but I can ssh into the machine fine and see that Xorg is taking 100% CPU)

I'm currently running linux-image-4.15.0-74-generic, so I tried downgrading all the way back to -64 (and also -72, -70, -66) and still get the same symptoms.  Is there another package I can try downgrading?  I looked at  xserver-xorg-video-nouveau (I'm at 1:1.0.15-2) but it looks like it hasn't been updated in a while...

Here are some outputs the Freeze page indicated might be informative.  Any advice would be appreciated, thanks!

Output of dmesg: [https://pastebin.com/15mK1RG2](https://pastebin.com/15mK1RG2)
Xorg.1.log - this has some suspicious NVIDIA WAIT warnings at the bottom but I'm not sure what they mean: [https://pastebin.com/Umc4D1JG](https://pastebin.com/Umc4D1JG)

---

