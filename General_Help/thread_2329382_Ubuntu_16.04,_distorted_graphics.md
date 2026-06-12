---
title: "Ubuntu 16.04, distorted graphics"
date: 2016-06-30
forum: General Help
---

### Post by john568 on 2016-06-30
If I let my laptop suspend and then wake it up, the graphics are all the wrong colors. I can't take a screenshot of it because the screenshot comes out in the correct colors. If I change the display resolution and change it back, the problem is fixed. What's going on here?

[COLOR=#000000]System details:[/COLOR]
[COLOR=#000000]Ubuntu 16.04 LTS[/COLOR]
[COLOR=#000000]Memory: 7.7 GiB[/COLOR]
[COLOR=#000000]Processor: Intel® Core™ i7-3520M CPU @ 2.90GHz × 4 [/COLOR]
[COLOR=#000000]Graphics: Gallium 0.4 on AMD TURKS (DRM 2.43.0, LLVM 3.8.0) (Different from when I was using Ubuntu 14 I think?)[/COLOR]
[COLOR=#000000]OS Type: 64-bit[/COLOR]
[COLOR=#000000]Disk: 483.7 GB[/COLOR]

---

### Post by X-RED_Tech on 2016-07-01
Already explained here: [http://ubuntuforums.org/showthread.php?t=2329212](http://ubuntuforums.org/showthread.php?t=2329212)

---

### Post by john568 on 2016-07-01
No, this is a completely different issue. I also had this issue in Ubuntu 14 with different graphics drivers.

---

### Post by sudodus on 2016-07-01
Will the following workaround work for you?

***ctrl + alt + F1*** (to get to a text screen)

***ctrl + alt + F7*** (to get back to the graphical screen, let us hope this time with correct graphics)

It works for me in a somewhat [similar case](http://ubuntuforums.org/showthread.php?t=1958073&page=19&p=13511417#post13511417), and it works to get back the cursor in other cases.

If it does, you can write a comment in the following bug report, which might target the wrong program package, but definitely describes a real bug.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604)

---

