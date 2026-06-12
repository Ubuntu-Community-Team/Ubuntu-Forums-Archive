---
title: "Remmina and .rdp"
date: 2018-06-14
forum: General Help
---

### Post by whaase on 2018-06-14
Hey, 

I'm scratching my head on how to fix this small issue I am having. 

I set up a connection within Remmina. I had to add a pre command of /f in order for it to auto open in full screen. It works great from within Remmina, but, when I export to a .rdp file to place on a desktop, it does not use the /f switch to open it. 

We have many clients that use RDP and want to roll out a generic .rdp icon for their connection, but we need it to open in full screen. I've googled many times and can not come up with an answer.

.rdp files are associated with Remmina, is there a way to have Remmina default to using this /f switch with all connections?

I've tried all the preference settings in Remmina and none seem to do it.

Any help would be great.

Thanks, Walter

---

### Post by tweston1 on 2019-02-08
Bump... from many moons in the future.

I am also having this issue. OP, did you ever figure this out?

Thank you!

---

### Post by dmnur on 2019-02-08
Remmina 1.2.x, available in Ubuntu 18.04 and later, allows you to do this for all connections by default:
Remmina Preferences -> Appearance -> Default view mode -> Viewport fullscreen

---

