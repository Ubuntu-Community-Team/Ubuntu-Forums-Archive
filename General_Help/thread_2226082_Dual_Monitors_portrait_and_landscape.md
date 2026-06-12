---
title: "Dual Monitors portrait and landscape"
date: 2014-05-25
forum: General Help
---

### Post by Karl_Woods on 2014-05-25
Good Morning all, i'm not sure if this is the correct forum to be posting in, so I hope that no one gets the hump with my first post!

last year I turned an ASUS EEEbox into a 17" digital picture frame picture hopefully below. I would like to add a second monitor to this but in portrait mode, so I guess there are two questions here, the first is, does anyone know if the DVI can split into two VGA ports and display separate images, and the second is it possible to rotate on of the displays, and have the software run on both screens simultaneously? I hope someone can help. Thanks.

Karl

[ATTACH=CONFIG]253431[/ATTACH][ATTACH=CONFIG]253432[/ATTACH]

---

### Post by coffeecat on 2014-05-25
Not a Ubuntu, Linux and Other OS Chat thread.

*Thread moved to **General Help**.*

---

### Post by Karl_Woods on 2014-05-25
> **coffeecat said:**
> Not a Ubuntu, Linux and Other OS Chat thread.

*Thread moved to **General Help**.*

Thanks

---

### Post by gordintoronto on 2014-05-25
DVI can not split into two VGA ports. DVI is digital, VGA is analogue.

Can you add a video card to the box?

---

### Post by zemega on 2014-05-27
Looking at the disassembly video of the B202 (I assume, its the only one with DVI output) Eee Box, the answer is no. It doesn't seems like its possible to add a video card to that box. No PCI slot in the spec either. So you are limited to just one display output.

Edit: Unless you want to go to Wireless Display route. Which can be quite hard to do. Considering it was released before 2010, I'm not sure if the box can support wireless display. And of course, there seems to be no wireless display support in Ubuntu as well, that's your major obstacle.

You can also try USB monitor. [http://blog.laptopmag.com/asus-mb168b-portable-monitor](http://blog.laptopmag.com/asus-mb168b-portable-monitor) . But, I have no idea whether it works in Ubuntu or not.
[http://askubuntu.com/questions/6382/how-can-i-get-a-displaylink-usb-monitor-under-ubuntu-any-recent-version](http://askubuntu.com/questions/6382/how-can-i-get-a-displaylink-usb-monitor-under-ubuntu-any-recent-version) . In this discussion, it says it works out of box for 13.04. So 14.04 should not be a problem.
The best way to test this is to bring your box (hopefully 14.04) to a store that sells this USB monitors.

Edit 2: Checkout the video below. Might help you with your goal. I do suggest you use the latest 14.04. These USB monitors seems to use Display Link technology and it works out of the box for 14.04 (actually kernel 3.9 and higher).
[https://www.youtube.com/watch?v=O2OCKRh-3ko](https://www.youtube.com/watch?v=O2OCKRh-3ko)

---

