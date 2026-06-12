---
title: "Ubuntu bootup and BIOS display on 'disabled' tv output"
date: 2008-06-10
forum: General Help
---

### Post by GammaPoint on 2008-06-10
I've got a monitor and a TV that I occasionally set up which separate X sessions to watch movies on the TV (though nvidia-settings).  After watching the movie, I disable the TV out, resave the X configuration file, and then restart X.  

However, since I started doing this I noticed that when I start my computer in the morning the BIOS screen and all Ubuntu bootup graphics that occur before the login screen only show up on my TV (even though it's disabled).  After I login on my computer monitor the output on the TV immediately goes to 'no input found' as I would have expected it to do in the first place.  

This is an annoying thing for various reasons. One of which is the fact that when Ubuntu periodically does disk checks on startup I don't have any knowledge as to why it's taking my computer so long to boot up unless I turn on the TV. Another is that if I want to configure the BIOS I have to turn on the TV, which again is supposed to be disabled.

Does anyone know why this would happen? Where is the boot up display set? Is it in xorg.conf somewhere?

Thanks.

---

### Post by cdenley on 2008-06-10
I doubt your xorg.conf configuration would make any difference, since it displays on your tv long before the file can be read. I think I had an ATI card once that the default output had to be changed by flashing the BIOS on the video card. The default output was used when more than one monitors were connected. When you disconnect your TV, is your computer monitor used?

---

### Post by Ocxic on 2008-06-10
unplug the TV from the video card, it defaults to the TV output whenever anything is connected to it, upon boot, I had the dame thing, no way around it

---

### Post by GammaPoint on 2008-06-10
You guys are right. If I disconnect my TV it shows up on my monitor instead. If there's nothing I can do about then I'll get used to it :)

Thanks.

---

