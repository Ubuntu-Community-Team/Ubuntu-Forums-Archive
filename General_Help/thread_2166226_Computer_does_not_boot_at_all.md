---
title: "Computer does not boot at all"
date: 2013-08-08
forum: General Help
---

### Post by patrik2 on 2013-08-08
Hi all!

I'm running Ubuntu on my computer. My problem is that the computer does not boot at all, it does not even go to the BIOS I guess. When I try to start the computer, I get the following message:

"reboot and select proper boot device or insert boot media in selected boot device and press a key"

There is nothing happening on the screen before this. The message reappears if I press a key...

I guess it could be a hardware problem (?) but the computer is brand new, been running for a few months only. Everything was running smoothly until this, I had no problems whatsoever when i shut the computer down the last time.
All help would be appreciated!

---

### Post by Mark Phelps on 2013-08-08
You're most likely NOT seeing messages because you have your BIOS default set to suppress POST (Power On Self Test) messages.  In that case, you won't see anything until you boot into a working OS and it puts up a screen.

To fix this, you need to go into your BIOS settings (key used varies by machine, often the "del" key), and once there, go into the Boot settings and change it to see messages.

Then, when you reboot, you will see the BIOS messages scrolling by on the screen.

IF it wasn't even going into the BIOS, you would get no display or possibly just a flashing cursor in the upper-left corner.

---

### Post by patrik2 on 2013-08-12
Thanks for your help Mark!

I do get to the BIOS but after trying all of the different boot options I still can't start the system, but receive the same messsage. Should I try to boot through a USB or something else to get the system going?

---

### Post by Mark Phelps on 2013-08-12
You're telling me what does NOT happen -- but to help you, I need to know what DOES happen.  

Did you make the BIOS changes I suggested?

If so, are you able to see messages scrolling by on the screen?

If so, what are the last couple of messages you see?

---

