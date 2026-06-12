---
title: "Second monitor sometimes won't come on or goes off and doesn't come back on"
date: 2024-04-09
forum: General Help
---

### Post by mrgrhayward on 2024-04-09
OS: Ubuntu 22.04.4; kernel: 6.5.0-27-generic.

Sometimes I boot up my PC into Ubuntu but my second monitor does not come on; just a black screen, or it does and stays on for a time while I'm using my OS but then goes to a black screen. In both cases its power light is blinking, indicating the monitor is in stand-by mode[COLOR=#202122][FONT=sans-serif]—n[/FONT][/COLOR]o "check signal cable", meaning no signal detected, warning appears on its screen. The attached pic shows how things are set up. Weirdly, if I pull out the HDMI plug of the HDMI-to-VGA unit from the HDMI splitter unit, no "signal lost" warning appears; the warning does appear if I pull out the VGA plug from the HDMI-to-VGA adaptor unit. I've tried various things but the only one that works is to power off then on the PC; sometimes I have to do this multiple times to get the monitor to come on. The monitor itself is not faulty as I've plugged it in directly to my PC. What could be wrong, and how to solve? Thanks.

[IMG]https://photos.app.goo.gl/cFw9Ko7aSw35Wj3U7[/IMG]
[IMG]https://drive.google.com/file/d/1RCPsHScrKg52jUiFMTg7f9ciuDVukm6H/view?usp=drive_link[/IMG]
[IMG]https://drive.google.com/file/d/1RCPsHScrKg52jUiFMTg7f9ciuDVukm6H/view?usp=sharing[/IMG]
[IMG]https://i.ibb.co/vDGx0v1/my-computer-and-audio-video-equipment-and-their-connectedness-dia-forhelpforum-dia-svg-xcf.png[/IMG]

---

### Post by him610 on 2024-04-11
@mrgrhayward, a couple of suggestions:

Since both primary and secondary monitors are using VGA, recommend you obtain a VGA A/B switch for those two monitors. 
On the HDMI (right) side, you could remove the HDMI splitter cable and connect both remote TV secondary monitors to the Active HDMI Splitter.
Try not to make it more complicated than necessary. KISS principle.

I like your block diagram. We don't see enough of them in these forums. One picture := 1000

---

### Post by mrgrhayward on 2024-04-17
Thanks for your response. :)

Just to clarify: the desktop on my primary monitor is extended across the local secondary monitor so that I can have something displayed on one monitor and something different displayed on the other monitor at the same time, so an A/B switch can't be used. Additionally, what is displayed on the local secondary monitor is also displayed on both remote TV secondary monitors. The reason for what might seem a little over-complicated is as follows: a friend of mine often visits me and I like to show him things on the Internet, such as an interesting Web page or YouTube video, while he is sitting comfortably on my couch in front of the remote TV secondary monitor, which is the lower one in my diagram and is a nice, big (forty-inch screen) TV. Because of where in the room my PC workstation is located, without the local secondary monitor, which is next to me, I wouldn't be able to see what he was seeing on the remote TV secondary monitor he's sitting in front of without me having to get up and look, or, if I want to use my mouse pointer to point something on his screen out to him, twist my body round, look at his screen while trying to manipulate my mouse with my outstretched arm, either of which is awkward and uncomfortable for me. The reason for the remote TV secondary monitor that is the upper one in my diagram, which I also can't easily see when sitting at my workstation, is to provide redundancy if the former TV stops working (properly).

The HDMI splitter cable is necessary to connect both remote TV secondary monitors to the active HDMI splitter. (The splitter cable, shaped like a 'Y', is used in reverse; normally, the end, 'leg' of the 'Y', connected to the HDMI-to-YPbPr adapter would be the input, and the arms of the 'Y' would be the outputs, but my arrangement does work to send one output of the active HDMI splitter to the two remote TV secondary monitors.)

I think I may have actually now fixed the problem of the secondary monitors going black and not being able to get them back on, or, at least, if they do go black, I can get them back up again without having to recycle my PC's power: something to do with the active HDMI splitter. I'm still trying to remember what I did but it involved unplugging the cable to the VGA adapter from it then plugging it back in followed by recycling the adapter's power.

(Glad you like my diagram; you'd love the 3D models I often do to explain things. :))

---

### Post by him610 on 2024-04-18
@mrgrhayward
Glad you seem to have found a solution to your issue.
Dealing with two monitors simultaneously is about my limit. Anything more than that tends to overwhelm the soft tissue between my ears. :)

---

